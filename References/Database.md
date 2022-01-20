The database configuration describes the properties of a specific entity in the database. This is a definition of how to isolate data for difference tenants. If you do not set a database record for an entity, the auto coding framework will not operate from the database automatically. If your entity data source is an external system, you do not need to configure the database for that entity.


## UniqueEntityName

`string`

Required

Indicates which [entity](/References/Entity) belongs to.

## SiteIdLocation

`enum`

Required

Allows: `none` `tableName` `tableField`

### None

The value in database is `0`.

This type means there is no siteId field in this entity.

### tableName

The value in database is `1`.

This type means siteId is stored in the database table name. For example, chat table's name is `t_livechat_chat1000`, siteId is `1000`.

### tableField

The value in database is `2`.

This type means there is a database table column named `SiteId` in the corresponding database table.

## NameSpace
In Startup.cs, when installing WebAPIModule, you will need to pass in the corresponding Application and Namespace, where Namespace will be used as the schema, which will affect the final table name generation, and will eventually generate `[{NameSpace}].[t_{Application}_{Name }(siteId?)]`