Entity represents a real-world thing that is determined by the ER design process in the software design process.

- [UniqueName](#UniqueName)
- [Name](#Name)
- [NameForPlural](#NameForPlural)
- [IsMultiRecord](#IsMultiRecord)
- [DynamicFieldEntity](#DynamicFieldEntity)
- [FeatureNameForMultiRecord](#FeatureNameForMultiRecord)
- [FeatureNameForAvailability](#FeatureNameForAvailability)
- [AuditLogActionType](#AuditLogActionType)
- [IfRecordChangeLog](#IfRecordChangeLog)
- [PermissionForGet](#PermissionForGet)
- [PermissionForInsert](#PermissionForInsert)
- [PermissionForUpdate](#PermissionForUpdate)
- [PermissionForDelete](#PermissionForDelete)
- [DeletionPolicy](#DeletionPolicy)
- [FieldToBeDisplayedWhenReferenced](#FieldToBeDisplayedWhenReferenced)
- [TenancyType](#TenancyType)
- [Fields](#Fields)

## UniqueName

`String`

The **primary key** of the entity. The value of this field is used where the entity is referenced in all auto coding ER.

## Name
`string`

Name of the entity. The name will be used in:
- API path
- Database table name
- Field name
- Include

Because we need to provide a friendly API, the name of the entity can be the same in a different application. For example AutoDistribution entity, which will be available in live chat and ticket products. They use the same path in API like `livechat/autoDistribution` and `ticketing/autoDistribution`. So they all use the same entity name `autoDistribution`, but use a different unique name like `livechatAutoDistribution` and `ticketingAutoDistribution`.

## NameForPlural

`string`

This is for API paths, e.g. /livechat/campaigns.

## IsMultiRecord

`enum`

- `yes` current entity is a multiple records entity. Multiple record means there are multiple records in a site, like there can be multiple Campaigns in Live Chat, and multiple Bot in Bot.
- `no` current entity is a single record entity. 
- `controlledByFeaturePoint` whether multiple records or not depends on FeatureNameForMultiRecord. For example, we have a feature point to control if a site can have multiple knowledgebases or not.


## DynamicFieldEntity

`string`

Represents the entity corresponding to the current entity‘s custom field and dynamically generates the entity at the specific runtime. Auto Coding will provide an IDynamicFieldMapper interface. The project team needs to implement this interface and register it in the IOC.

## FeatureNameForMultiRecord

`string`

Applicable when <b>IsMultiRecord</b> is `controlledByFeaturePoint`. When this feature is enabled, the current entity is a multiple records entity. When this feature is not enabled, the current entity is a single record entity. 

## FeatureNameForAvailability

`string`

An entity is not available if the feature is disabled

## AuditLogActionType

`int`

reference to Audit log type entity. 

## IfRecordChangeLog

`bool`

When this feature is enabled, all create/update/delete operations for the current entity will be record as a changelog.

## PermissionForGet

`int`

Id of Permission Entity.

## PermissionForInsert

`int`

Id of Permission Entity.

## PermissionForUpdate

`int`

Id of Permission Entity. HTTPPostAction has the same permission as Update.

## PermissionForDelete

`int`

Id of Permission Entity.

## DeletionPolicy

`enum`

- `Soft` Indicates that a soft deletion will be applied and the references to the entity from historical data can still be included. For this entity, you can load the deleted entity at the same time by passing an “isIncludeDeleted” parameter. 
- `TemporarySoft` Represents a temporary soft deletion. Hard deletion will be performed when data synchronization is complete or migration is complete. Depending on the implementation of the data cleaner. Deleted data can never be loaded and included.
- `Hard` Indicates that the data will be deleted directly from the database.


## FieldToBeDisplayedWhenReferenced

`string`

The name of the field. When the entity is referenced, this field in the entity is displayed on the UI. Such as the `title` of the article, or the `name` of the agent.

## TenancyType
`enum`, allows `none`, `site` and `partner`.

Specifies the type of tenant, because some entities belong to the partner and some entities belong to site, which makes some distinction between the default behavior of the framework and therefore needs to be specified.
- `none`: Indicates that the current entity does not have tenant type and is shared by all users, such as some system entities.
- `site`: Indicates that the entity is site-level and determines whether there is `SiteId` filter default of dynamic table name based on the t_AutoCoding_Database's configuration.
- `partner`: Indicates that the entity is partner-level and determines whether there is `PartnerId` filter default of dynamic table name based on the t_AutoCoding_Database's configuration.

## Fields 

`array` of [Field](/References/Field).


