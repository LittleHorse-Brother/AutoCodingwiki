Describes a data source data type used to identify the current data item. The `Name` property is a unique identifier, just like id. The `Type` property is the actual type of the current data item which determined how to use it in an operation.

## Fields
- [Name](#Name)
- [Type](#Type)
- [EntityName](#EntityName)
- [CustomTypeName](#CustomTypeName)
- [ConditionForShowing](#ConditionForShowing)

<br>
<br>

## Name

`string`

Default: `""`. Unique.

Name of current type. Link to the value of the [`FieldNameForDataType`](/References/UI/Data-Source#FieldNameForDataType) field.

<br>
<br>

## Type

`enum`

[`string (default) 0`](#string) [`int 1`](#int) [`bool 2`](#bool) [`enum 3`](#enum) [`dateTime 4`](#dateTime) [`timezone 5`](#timezone) [`entity 6`](#entity) [`custom 7`](#custom) [`stringArray 8`](#stringArray) [`float 9`](#float) [`simpleString 10`](#simpleString)

The actual type which the operator depends on this.

### string

`value`: `0`

The component right beside the operator will display as text input. Operator support `is` `isNot` `contains` `notContains` `regularExpression`. Bellow is the input component:
![String.png](/.attachments/String-299a85d0-7e58-46a1-bcd6-c74b7119d2ba.png)

<br>

### int

`value`: `1`

The component right beside the operator will display as a number input. Operator support `is` `isNot` `isMoreThan` `isLessThan`. Bellow is the input component:
![Int.png](/.attachments/Int-615cbb1b-2c90-4fda-9440-2beb63bb7704.png)

<br>

### bool

`value`: `2`

The component right beside the operator will display as a select which can only select true or false. Operator support `is` `isNot`. Bellow is the input component:
![Bool.png](/.attachments/Bool-c7e932c1-84b9-4eb2-a2bd-d80c7beb1608.png)

<br>

### enum

`value`: `3`

The component right beside the operator will display as a select. Operator support `is` `isNot`. Bellow is the input component:
![Enum.png](/.attachments/Enum-245e5435-f3fa-4017-9d8c-b2668b2b7b2b.png)

<br>

### dateTime

`value`: `4`

The component right beside the operator will display as a date-time picker. Operator support `is` `isNot` `before` `after`. Bellow is the input component:
![DateTime.png](/.attachments/DateTime-940eaa49-91c4-4cec-9c59-b9f2a37a4a02.png)

<br>

### timezone

`value`: `5`

The component right beside the operator will display as a select which can only select a timezone. Operator support `isOneOf` `isNotIn`. Bellow is the input component:
![Timezone.png](/.attachments/Timezone-81ab2620-e537-4323-a40a-633a6b7b4453.png)

<br>

### entity

`value`: `6`

The component right beside the operator will display as a select, and the data of the select will request by the [`EntityName`](#EntityName). Operator support `isOneOf` `isNotIn`. Bellow is the input component:
![Entity.png](/.attachments/Entity-a089a775-5ca1-41d9-9e8a-046f6d0acd8f.png)

<br>

### custom

`value`: `7`

The component right beside the operator will display a custom component determined by [`CustomTypeName`](#CustomTypeName). Operator support `is` `isNot`. Bellow is the input component:
![Custom.png](/.attachments/Custom-2a084c9b-0595-4c9d-b23c-c923778b3d44.png)

<br>

### stringArray

`value`: `8`

The component right beside the operator will display as a select. Operator support `isOneOf` `isNotIn` `contains` `notContains`. Bellow is the input component:
![StringArray.png](/.attachments/StringArray-dc568524-f0d0-4445-a321-7d5d2c81950d.png)

<br>

### float

`value`: `9`

The component right beside the operator will display as text input. Operator support `is` `isNot` `isMoreThan` `isLessThan`. Bellow is the input component:
![Float.png](/.attachments/Float-3a204955-032b-47bb-abeb-14eef205ba3e.png)

<br>

### simpleString

`value`: `10`

The component right beside the operator will display as text input. Operator support `is` `isNot` `contains` `notContains`. Bellow is the input component:
![SimpleString.png](/.attachments/SimpleString-fed768b8-013b-4c5d-ac98-7abf1d4a300c.png)

<br>
<br>

## EntityName

`string`

Default: `""`. Required when [`Type`](#Type) is [`entity`](#entity).

The entity [`UniqueName`](/References/Entity#UniqueName) which associated. Only available for [`entity`](#entity).

<br>
<br>

## CustomTypeName

`string`

Default: `""`. Required when [`Type`](#Type) is [`custom`](#custom).

Only available for [`custom`](#custom).

<br>
<br>

## ConditionForShowing

`string`

Default: `""`. Optional.

Show current data source data type when condition result is true, support [variable](/References/UI/Variables).