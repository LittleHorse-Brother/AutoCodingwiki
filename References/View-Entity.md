A view entity is a subset of a Requirement Entity. A ViewEntity can only have HTTP Get operations and no other HTTP operations. When a field references to a ViewEntity, the referenced is automatically transferred to the Base Entity. View Entity corresponding to the table `t_AutoCoding_ViewEntity` table in auto coding database. Contains the following fields: 

- [UniqueName](#UniqueName)
- [Name](#Name)
- [NameForPlural](#NameForPlural)
- [Application](#Application)
- [SourceNamespace](#SourceNamespace)
- [BaseEntity](#BaseEntity)
- [Conditions](#Conditions)

# UniqueName
`string`

Required: Yes

Unique name of the entity. Duplicates with the requirement entity’s unique name are not allowed. The value of this field is used where the entity is referenced in all auto coding ER.

# Name
`string`

Required: Yes

The name of the View Entity. The name will be used in:
- API path
- Field name
- Include

Because we need to provide a friendly API, the name of the entity can be the same in a different application. For example AutoDistribution entity, which will be available in live chat and ticket products. They use the same path in API like `livechat/autoDistribution` and `ticketing/autoDistribution`. So they all use the same entity name `autoDistribution`, but use a different unique name like `livechatAutoDistribution` and `ticketingAutoDistribution`.

# NameForPlural
`string`

Required: Yes

For restful API URL, e.g. /livechat/campaigns.

# Application
`string`

Required: Yes

Specify the current view entity’s Application. Only this Application’s app is allowed to access this entity’s API. 

# SourceNamespace
`string`

Required: Yes

Specify the current view entity’s namespace. Only this namespace’s app is allowed to access this entity’s API. Access from partner namespace to site namespace is automatically filtered with partnerId.

# BaseEntity
`string`

Required: Yes

RequirementEntity. When a field references to a ViewEntity, the referenced is automatically transferred to the Base Entity.

# [N]Conditions
`Reference`

Required: No

Default: []

when there are multiple conditions, “and” will be used

reference to: [View Entity Condition](/References/View-Entity/View-Entity-Condition)