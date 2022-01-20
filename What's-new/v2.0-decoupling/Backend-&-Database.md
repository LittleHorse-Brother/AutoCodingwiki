
# Goal

  - Separate the unified Auto Coding database so that each project team can run with a separate Auto Coding configuration to solve the coupling of the entities of different teams.
  - Each project can use its own specific version of the Auto Coding framework so that changes of the framework can be implemented separately
  - Avoid reworking all the tools and other things that have been done around the database with auto coding and to reduce the amount of time the project decouple, we also use the database to save the auto coding configuration, but separate by different schema in production environment.
  - Ensure that each project team can implement decoupling independently and all modules can run properly in the unified Auto Coding database before decoupling.

## Overall Design

Different service uses different schema to isolate the configuration in the database. Each Schema has a complete auto coding configuration tables like the followings:

- livechat
  - `livechat.t_AutoCoding_Entity`
  - `livechat.t_AutoCoding_Field`
  - `livechat.t_AutoCoding_API`
  - `livechat.t_AutoCoding_UI....`
  - `...`
- ticketing
  - `ticketing.t_AutoCoding_Entity`
  - `ticketing.t_AutoCoding_Field`
  - `ticketing.t_AutoCoding_API`
  - `ticketing.t_AutoCoding_UI...`
  - `...`

## Changes of the Auto Coding Configuration

- Table `t_AutoCoding_Entity` add the following fields
  - **Service**: string. Specify which service the entity belongs to. All the entities should have a service. The Auto Coding framework will only handle the entities api under current service. 
    - You do not need to configure fields and UIs for entiteis out of the current service.

  - **TenancyType**: enum. Allows `none`, `site` and `partner`. Specifies the type of tenant, because some entities belong to the partner and some entities belong to site, which makes some distinction between the default behavior of the framework and therefore needs to be specified.
    - `none`: Indicates that the current entity does not have tenant type and is shared by all users, such as some system entities.
    - `site`: Indicates that the entity is site-level and determines whether there is `SiteId` filter default of dynamic table name based on the t_AutoCoding_Database's configuration.
    - `partner`: Indicates that the entity is partner-level and determines whether there is `PartnerId` filter default of dynamic table name based on the t_AutoCoding_Database's configuration.

- `t_AutoCoding_Database` add the following fields.
  - **Schema**: string. Indicates which schema is used when the current entity maps to the database table name.
  - **TenancyIsolationPolicy**: enum. Allows `none`, `table` and `field`. The `SiteIdLocation` field will be deprecated.

- Use service name as the schema name.
  - When auto coding decoupling is applied, the app only loads the Auto Coding table configuration under the currently specified schema.
  - Remove the partner and system schemas' related tables.
    - Deprecation of ViewEntity across namespace.
    - The project team needs to migrate its own partner or system entities to its own service.

## Changes when using the Auto Coding Framework 

- When you enable the auto coding framework in the app startup you need to specify the following configuration
  - `Service`
  - `API Domain`

- When you enable the auto coding framework, the following api will be automatically provided
  - `GET /autocoding/entities`. This api returns all entities of the current service for front-end render the UI part.

- When you enable the auto coding framework and run the applicaction the database schema will upgrade to current version automatically

- When you enable the auto coding framework the `HEAD` method will be provided for all entities automatically
  - This api is used to check whether an entity record is real exists or not. e.g. `HEAD /livechat/campaigns/{id}` returns 404 indicates not exists and 200 is exists.

## Changes of the Auto Coding Framework behavior when the referenced entity is out of current service

### Validation
  - When an api is called to set a value on a reference entity (out of current service), the framework will make a api request to verify.
    - The project team doesn't have to deal with anything


### API Include
  - Entities referenced across services cannot be included by framework
    - The external entities configured in `HttpGetIncludeEntities` and `AutoIncludeReferencingEntities` should be removed.
    - For specific entities such as agent & department that can be configured as their own service. But you only need to configure the fields used. This configuration requires architect team confirm.
    - External entities used in the front-end or backend custom code need to be pull through the API.

### Stop Deletion
  - If there is a reference to an external service entity there is no way to prevent the referencing entity being deleted.
    - The external service entity should be handled referencing entity deleted.
      - e.g. `campaignOfflineMessage.taskbot` the referencing taskbot may be deleted.

### Auto Creation
  - In some cases, we may need to extend an entity to add new features. We call this entity as an extension entity. If the extension entity and the primary entity is not in the same service, the extension entity will not be created automatically When the primary entity created.
    - e.g. `agentDistribution` and `agentPreference` managed in livechat service, but the primary entity `agent` managed in global service. The project team needs to work on scenarios where there is a `agent` but no `agentDistribution` and `agentPreference`.

### Cascade Deletion
  - Cascading deletions across services cannot be implemented. In fact, there are two cases of cross service enttiy cascading deletion.
    - Extension entity
      - The project team needs to handle the deletion of the primary entity. This means that the extension entity still exists, but the primary entity may have been deleted.
        - e.g. `agentDistribution`
    - Many To Many
      - The project team needs to handle the deletetion of the referencing entity. This means that the relation still exists, but the entity may have been deleted.
        - e.g. `shift.agentIds`

### Inboundary 
  - The inboundary configuration across service is not supported.


## What does the project team need to do when implementing auto coding decoupling?

### Using backend auto coding decoupling

1. Upgrade the auto coding framework to decoupling version. 

2. Update the auto coding database configuration
  - Merge the partner & system entities into the specified schema.
  - Remove all extenral service entities and related configurations.
  - Define how to reference the external entities and fix the structure of referenced external entities
    - **External Reference**：It is an entirely external entity and all access to that entity under the current service will switch to use API call. For this type of entity, you only need to configure the entity and primary key.
    - **Entity Copy**: For frequently used entities such as Agent and Department, to avoid frequent access to Global API, it is allowed to configure a copy of the entity, but only need to configure their own fields, do not need to configure useless fields. In a micro-service architecture, entities need to be synchronized between different services and the same table is used before the database is split.

3. Handle possible data inconsistency issues, including the custom code on back-end & front-end.
  - The referenced entity has been deleted.
  - The extension entity may not exist.

4. Ensure that the upstream and downstream service handle data inconsistency scenarios







