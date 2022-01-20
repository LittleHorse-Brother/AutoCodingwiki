Describes AdditionalField object. In some case, a component work with multiple fields. Config one field in [component](/References/UI/Single-Row/Form/Component), others as additional fields.
## fields
- [fieldName](#fieldName)
- [UIElementType](#UIElementType)
- [ComponentId](#ComponentId)

<br/>

## FieldName
`string`

Required.

The name of the additional field. The component need to fetch value from multiple fields of current entity. eg: [Avatar Input](#avatarInput)

<br/>

## UIElementType
`string`

Required.

The property's name of the component which receive the value of configured in `FieldName`.

<br/>

## ComponentId
`string`

Required.

The Id of the component which need a additional field.