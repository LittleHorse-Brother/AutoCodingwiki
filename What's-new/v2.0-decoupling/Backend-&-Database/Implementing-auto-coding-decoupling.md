
## Upgrade the auto coding framework to decoupling version

1. Update the framework version to the latest version through nuget. The decoupling package version should be 2.x or higher.

2. Modify the code as follows:
![image.png](/.attachments/image-4d4cedd3-4884-480c-991b-326b29ca4323.png)
3. Fixes other issues that cannot be compiled because the API changes.


## Update the auto coding database configuration

- Create tables
Different service uses different schema to isolate the configuration in the database. Each Schema has a complete auto coding configuration tables.

  e.g. For kb, the following tables should be created: 
  - `kb.t_AutoCoding_Entity`
  - `kb.t_AutoCoding_Field`
  - `kb.t_AutoCoding_API`
  - `kb.t_AutoCoding_UI....`
  - `...`

- Deprecation of ViewEntity across namespace

  Cross-namespace viewEntity is no longer supported, it should be deleted directly. Please pay attention to the `Default` and `SourceDataForAutoCreating` of the `t_AutoCoding_Field` table. If there is a reference to the viewEntity, you need to modify the sourceEntity referenced to the viewEntity. 

  e.g. kb’s `designTemplate`, its baseEntity is `systemDesignTemplate`, SourceNameSpace is partner, it is a cross-namespace viewEntity, and should be deleted.

- Merge the partner & system entities into the specified schema.

  The entity in partner & system is migrated to the related autocoding table under the schema corresponding to the service. For partner, the data moved to the past, TenancyType is partner. For system, TenancyType is none. 

  e.g. kb's `systemDesignTemplate`, it is under the partner's schema, it should be migrated to the kb's schema.

- Remove all extenral service entities and related configurations.

  First delete the data in the entity table, and then use this as a benchmark to delete data in other tables. Note that the data in the field, like the agent under kb, should only part of the filed be retained.

  1. Find out all the entities that need to be retained by the service (including the entities belonging to this service and the entities it references), and delete all the entities that are not needed in `t_AutoCoding_Entity`.

  2. For tables directly associated with `t_AutoCoding_Entity`, such as `t_AutoCoding_API`, root EntityUniqueName, delete unnecessary data.

  3. For tables that are indirectly associated with `t_AutoCoding_Entity`, such as `t_AutoCoding_APIGetAdditionalField`, first delete unnecessary data in `t_AutoCoding_API`, and then associate according to id, delete data in `t_AutoCoding_APIGetAdditionalField`.

- Define how to reference the external entities and fix the structure of referenced external entities

    - **External Reference**：It is an entirely external entity and all access to that entity under the current service will switch to use API call. For this type of entity, you only need to configure the entity and primary key.

    - **Entity Copy**: For frequently used entities such as Agent and Department, to avoid frequent access to Global API, it is allowed to configure a copy of the entity, but only need to configure their own fields, do not need to configure useless fields. In a micro-service architecture, entities need to be synchronized between different services and the same table is used before the database is split.

## Handle possible data inconsistency issues, including the custom code on back-end & front-end.
  - The referenced entity has been deleted.

    e.g. `campaignOfflineMessage.taskbot` the referencing taskbot may be deleted.

  - The extension entity may not exist.

    e.g. `agentDistribution` and `agentPreference` managed in livechat service, but the primary entity `agent` managed in global service. The project team needs to work on scenarios where there is a `agent` but no `agentDistribution` and `agentPreference`.

## Ensure that the upstream and downstream service handle data inconsistency scenarios

The `shift` of livechat depends on the `agent` of gloal, and the `chatbotSmartTriggerAction` of bot depends on the `segment` of livechat. When livechat is released, ensure that upstream and downstream are aware of these changes and have made these changes. 