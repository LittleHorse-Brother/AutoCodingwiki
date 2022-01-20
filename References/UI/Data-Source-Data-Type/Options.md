Describe an option. Only available when [`Type`](/References/UI/Data-Source-Data-Type#Type) is [`enum`](/References/UI/Data-Source-Data-Type#enum) or [`entity`](/References/UI/Data-Source-Data-Type#entity). If [`Type`](/References/UI/Data-Source-Data-Type#Type) is [`enum`](/References/UI/Data-Source-Data-Type#enum), these are all the enum options. If [`Type`](/References/UI/Data-Source-Data-Type#Type) is [`entity`](/References/UI/Data-Source-Data-Type#entity), the data from [`EntityName`](/References/UI/Data-Source-Data-Type#EntityName) will be used and there are extra options like "@Assignee" (Always display extra options at the top).

## Fields
- [Label](#Label)
- [Value](#Value)
- [Order](#Order)

<br>
<br>

## Label

`string`

Default: `""`. Required.

The label of the option. Use to display. Support [variable](/References/UI/Variables).

<br>
<br>

## Value

`string`

Default: `""`. Required.

The value of the option. Use to determine.

<br>
<br>

## Order

`int`

Default: `0`.

The order of the option.