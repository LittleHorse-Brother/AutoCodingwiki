Describes a data source used to parse the data requested from the data source field interface. The `Name` property is a unique identifier, just like id. The `EntityName` property is the unique name of the entity which is associated with the current data. The `FieldNameForDataType` property is used to find the [Data Source Data Type](/References/UI/Data-Source-Data-Type) of each data item.

## Fields
- [Name](#Name)
- [Label](#Label)
- [EntityName](#EntityName)
- [FieldNameForDataType](#FieldNameForDataType)
- [ConditionForShowing](#ConditionForShowing)

<br>
<br>

## Name

`string`

Default: `""`. Unique.

Name of the data source. When using data source as macro, the macro displays as {!{name}}.{{fieldname}}.

<details>
<summary id="example">Example</summary>

Configurations of custom variable data source are:
- `name`: `customVariable`
- `label`: `Custom Variable`
- `entityName`: `customVariable`
- `fieldNameForDataType`: `type`
- `conditionForShowing`: `@customVariableConfig.isEnabled == true`

</details>

<br>
<br>

## Label

`string`

Default: `""`. Required.

Display as the group title. Support [variable](/References/UI/Variables).

[Example](#example)

<br>
<br>

## EntityName

`string`

Default: `""`. Required.

The [`UniqueName`](/References/Entity#UniqueName) of the associated entity. Each data source field group must have a corresponding requirement entity.

[Example](#example)

<br>
<br>

## FieldNameForDataType

`string`

Default: `""`. Required.

When using data source on rule condition the corresponding requirement entity must have a field that indicates the name of the data type of the field.

[Example](#example)

<br>
<br>

## ConditionForShowing

`string`

Default: `""`. Optional.

Show current data source when condition result is true, support [variable](/References/UI/Variables).

[Example](#example)