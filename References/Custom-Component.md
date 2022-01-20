The extension is used to describe a custom component commonly. It is also used to describe something else, such as level 2 submenu provider, yup schema, and so on.

## Form Component

1. The component should implement the specific interface to render in a form. It usually implements `id`, `value`, `label`, `disabled`, `onChange`(change event), `onBlur`(blur event).
1. Import the component in a specific extension definition file. The `extension.type` should be `formComponent` and `extension.name` should be the component name.
1. Assign the component name to [`UIFormComponent.CustomComponentName`](/References/UI/Single-Row/Form/Component#CustomComponentName) in the database.

### Example

#### GIT Address
http://192.168.3.200:8080/tfs/defaultcollection/frontend/_git/Onboarding
(only accessible from LAN environment.)

#### Code Location
- Extension Definition: .\FrontEnd\src\Extension\index.ts
- Component Definition: .\FrontEnd\src\Extension\UI\CKBUrlInput.tsx

### Extension
![Extension.png](/.attachments/Extension-b00d9187-7cee-477b-ac6d-ff59e8e36c18.png)
- `name`
Property `name` should be the component name.
- `component`
Property `component` is the component itself.
- `wrapper`
Property `wrapper` defines the component's wrapper.
  - `none`
    - The component will wrap with nothing and render itself.
  - `CFormField`
    - The component will wrap with `CFormField`. `CFormField` only does some logic, such as validation, handle change event, and so on.
  - `CFormControl`
    - The component will wrap with `CFormControl`. `CFormControl` not only does some logic, such as validation, handle change event, and so on. But also renders something, such as component label, tooltip, error message, helper text, and so on.
- `labelShrink`
Property `labelShrink` defines which component should the component label display.
  - `true`: `InputLabel`
  - `false`: `CFormLabelStyled`
- `validator`
  - Property `validator.name` defines the prop name when passing the schema to the component.
  - Property `validator.params` defines the params passed to the schema.
  - Property `validator.schema` is the validator schema itself.
- properties
  - Property `properties.name` defines the prop name when passing the value to the component.
  - Property `properties.value` defines the prop value path to the current entity.
- `valueMapping`
  - The key of the `valueMapping` defines the prop value name to the current entity.
  - The value of the `valueMapping` defines the prop name when passing the value to the component.
- `domainServiceProps`
  - Property `domainServiceProps.name` defines the prop name when passing the domain service to the component.
  - Property `domainServiceProps.entityUniqueName` defines which entity used to generate the domain service.
  - Property `domainServiceProps.scopingEntityUniqueName` defines the domain service's scoping entity.
- `dataSourceDomainServiceProps`
  - The key of the `dataSourceDomainServiceProps.name` defines the prop name when passing the data source domain service to the component.
  - The value of the `dataSourceDomainServiceProps.dataSources` defines the data sources used to generate the data source domain service.