`DataFilter` is used to filter data. It is only available when [`Multi-Row PresentationType`](/References/UI/Multi%2DRow#PresentationType) is [`table`](/References/UI/Multi%2DRow#table). Get entity list with conditions. If there are multiple configured conditions, all conditions must meet.

## Fields
- [EntityUniqueName](#EntityUniqueName)
- [FieldName](#FieldName)
- [Value](#Value)

<br>
<br>

## EntityUniqueName

`string`

Default: `""`. Required.

The [`UniqueName`](/References/Entity#UniqueName) of the associated entity.

<br>
<br>

## FieldName

`string`

Default: `""`. Required.

The name of the [condition](/References/Entity-API) belongs to the associated entity.

<br>
<br>

## Value

`string`

Default: `""`. Required.

Generate a condition as '[`Name`](#Name)=`Value`'.
eg: `engineType=dialogflow`