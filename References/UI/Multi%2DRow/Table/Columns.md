Describe a column. Include general info of a column, such as `fieldName` `cellComponentType`, etc. Below is the [Learning Columns](https://dash11.comm100.io/ui/10100000/bot/agentassist/agentassistlearning/).
![Columns.png](/.attachments/Columns-0a573159-9bda-48bd-bcc8-ef1abd907fa6.png)

## Fields
- [EntityUniqueName](#EntityUniqueName)
- [FieldName](#FieldName)
- [CellComponentType](#CellComponentType)
- [Order](#Order)
- [Width](#Width)
- [HeaderIcon](#HeaderIcon)
- [HeaderLabel](#HeaderLabel)
- [HeaderHelperText](#HeaderHelperText)
- [IsAllowSort](#IsAllowSort)
- [IsShowContentInTooltip](#IsShowContentInTooltip)
- [Url](#Url)
- [CustomComponentName](#CustomComponentName)
- [SelectDataSource](#SelectDataSource)
- [ConditionForShowing](#ConditionForShowing)
- [ConditionForDisableCell](#ConditionForDisableCell)
- [IsOpenPageInNewTab](#IsOpenPageInNewTab) `v0.5.x`

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

The name of the HTTPGetResultField. For the field in the included entity, the corresponding data list will be shown e.g. article.tags.

<br>
<br>

## CellComponentType

The table cell component's [`Field`](/References/Field) is controlled by [`FieldName`](#FieldName).

`enum`

[`avatar (default) 0`](#avatar) [`avatarList 1`](#avatarList) [`chipInput 2`](#chipInput) [`color 3`](#color) [`editEntityLink 4`](#editEntityLink) [`icon 5`](#icon) [`input 6`](#input) [`link 7`](#link) [`list 8`](#list) [`numberInput 9`](#numberInput) [`routeTo 10`](#routeTo) [`ruleCondition 11`](#ruleCondition) [`select 12`](#select) [`switch 13`](#switch) [`text 14`](#text) [`customComponent 15`](#customComponent)

### avatar

`value`: `0`

The avatar's icon is determined by [`AdditionalFields`](/References/UI/Multi%2DRow/Table/Columns/AdditionalFields), the avatar's text is determined by the field.
![AvatarCell.png](/.attachments/AvatarCell-01297222-6b44-489b-9893-95f71cbe66b7.png)

<details>
<summary id="avatarexample">Example</summary>

Below is part of the [Agents](https://dash11.comm100.io/ui/10100000/global/people/agents/) page.

Configurations of the column are:
- `entityUniqueName`: `agent`
- `fieldName`: `displayName`
- `cellComponentType`: `avatar`
- `headerLabel`: `Display Name`
- `additionalFields`:
  - For avatar
    - `uiElementType`: `avatar`
    - `fieldName`: `avatar`

![Avatar.png](/.attachments/Avatar-b192035d-70dc-4db5-8051-a01448039e2f.png)
</details>

<br>

### avatarList

`value`: `1`

The data corresponding to the field should be multi-record. The avatar's icon is determined by [`AdditionalFields`](/References/UI/Multi%2DRow/Table/Columns/AdditionalFields).

<details>
<summary id="avatarlistexample">Example</summary>

Below is part of the [Departments](https://dash11.comm100.io/ui/10100000/global/people/departments/) page.

Configurations of the column are:
- `entityUniqueName`: `department`
- `fieldName`: `agents`
- `cellComponentType`: `avatarList`
- `headerLabel`: `Members`
- `additionalFields`:
  - For avatar
    - `uiElementType`: `avatar`
    - `fieldName`: `avatar`

![AvatarList.png](/.attachments/AvatarList-2a657563-f415-4c40-a04e-19bf4e73b45a.png)
</details>

<br>

### chipInput

`value`: `2`

Display as an input. When you press enter, the inputted data will be changed into a chip. Only available when table inside a form. There are no examples because it is not used currently.

<br>

### color

`value`: `3`

Display a colored circle based on the field.

<details>
<summary>Example</summary>

Below is part of the [Segmentation](https://dash11.comm100.io/ui/10100000/livechat/settings/segmentation/) page.

Configurations of the column are:
- `entityUniqueName`: `segment`
- `fieldName`: `color`
- `cellComponentType`: `color`
- `headerLabel`: `Color`

![Color.png](/.attachments/Color-34155ea7-e2b4-443c-ab51-efa0d737542e.png)
</details>

<br>

### editEntityLink

`value`: `4`

Use to edit a row to the table. If the table inside a form, open a drawer when clicking. Otherwise, open a page when clicking.

<details>
<summary>Example</summary>

Below is part of the [Articles](https://dash11.comm100.io/ui/10100000/kb/knowledgebases/articles/) page.

Configurations of the column are:
- `entityUniqueName`: `article`
- `fieldName`: `title`
- `cellComponentType`: `editEntityLink`

![EditEntityLink.png](/.attachments/EditEntityLink-ea6f5856-d285-4336-a81d-60ef73da40b6.png)
</details>

<br>

### icon

`value`: `5`

The icon name is determined by the associated field's [`Field Option Group`](/References/Field-Option-Group).

<details>
<summary>Example</summary>

Below is part of the [Articles](https://dash11.comm100.io/ui/10100000/kb/knowledgebases/articles/) page.

Configurations of the column are:
- `entityUniqueName`: `article`
- `fieldName`: `status`
- `cellComponentType`: `icon`

![Icon.png](/.attachments/Icon-77ade5b6-a38b-4445-83b8-e99fe5bd5420.png)
</details>

<br>

### input

`value`: `6`

Display as text input. Only available when table inside a form. There are no examples because it is not used currently.

<br>

### link

`value`: `7`

Open a page when clicking. The URL of the page is determined by [`Url`](#Url).

<details>
<summary id="linkexample">Example</summary>

Below is part of the [Articles](https://dash11.comm100.io/ui/10100000/kb/knowledgebases/articles/) page (Manage knowledge base drawer).

Configurations of the column are:
- `entityUniqueName`: `knowledgeBase`
- `fieldName`: `articles`
- `cellComponentType`: `link`
- `url`: `../articles?scopingknowledgebaseid=$id`

![Link.png](/.attachments/Link-6e7b6f4d-a744-4afe-a13d-72aa5836b8e3.png)
</details>

<br>

### list

`value`: `8`

Display as a chip item list. The data corresponding to the field should be multi-record.

<details>
<summary>Example</summary>

Below is part of the [Agents](https://dash11.comm100.io/ui/10100000/global/people/agents/) page.

Configurations of the column are:
- `entityUniqueName`: `agent`
- `fieldName`: `departments`
- `cellComponentType`: `list`

![List.png](/.attachments/List-01314e5e-4fa9-484e-9c46-ef16adc20acb.png)
</details>

<br>

### numberInput

`value`: `9`

Display as an input that can only input numbers. Only available when table inside a form.

<details>
<summary>Example</summary>

Below is part of the [Auto Distribution](https://dash11.comm100.io/ui/10100000/livechat/settings/autodistribution/) page.

Configurations of the column are:
- `entityUniqueName`: `agentAutoDistributionConfig`
- `fieldName`: `maxConcurrentChats`
- `cellComponentType`: `numberInput`
- `headerLabel`: `Maximum Chat Number`

![NumberInput.png](/.attachments/NumberInput-2850cdfd-fdd8-4684-8dfc-a89a5646d488.png)
</details>

<br>

### routeTo

`value`: `10`

Describe where to route when this row is triggered. The `routeToType` are determined by the field, the `routeToAgent` and `routeToDepartment` is determined by [`AdditionalFields`](/References/UI/Multi%2DRow/Table/Columns/AdditionalFields).

<details>
<summary id="routetoexample">Example</summary>

Below is part of the [Routing Rules](https://dash11.comm100.io/ui/10100000/ticketing/settings/routingrules/) page.

Configurations of the column are:
- `entityUniqueName`: `ticketingRoutingRule`
- `fieldName`: `routeToType`
- `cellComponentType`: `routeTo`
- `headerLabel`: `Route to`
- `additionalFields`:
  - For routeToAgent
    - `uiElementType`: `routeToAgent`
    - `fieldName`: `routeToAgent.displayName`
  - For routeToDepartment
    - `uiElementType`: `routeToDepartment`
    - `fieldName`: `routeToDepartment.name`

![RouteTo.png](/.attachments/RouteTo-476c0f79-d643-4b8c-95a6-ec5a8ce09da1.png)
</details>

<br>

### ruleCondition

`value`: `11`

Describe the conditions under which this row will be triggered. The `conditions` are determined by the field, the `logicalExpression` and `when` is determined by [`AdditionalFields`](/References/UI/Multi%2DRow/Table/Columns/AdditionalFields).

<details>
<summary id="ruleconditionexample">Example</summary>

Below is part of the [Smart Triggers](https://dash11.comm100.io/ui/10100000/bot/aichatbot/smarttriggers/) page.

Configurations of the column are:
- `entityUniqueName`: `chatbotSmartTrigger`
- `fieldName`: `chatbotSmartTriggerConditions`
- `cellComponentType`: `ruleCondition`
- `headerLabel`: `Conditions`
- `additionalFields`:
  - For logicalExpression
    - `uiElementType`: `logicalExpression`
    - `fieldName`: `logicalExpression`
  - For when
    - `uiElementType`: `when`
    - `fieldName`: `conditionExpressionType`

![RuleCondition.png](/.attachments/RuleCondition-b25279d8-5bbd-4e00-8d75-8d02a07a7ab4.png)
</details>

<br>

### select

`value`: `12`

The data of the select comes from:
1. The [`DataSource`](#DataSource) API, if [`SelectDataSource`](#SelectDataSource) is available.
2. The time zone API, if the associated field type is [`timezone`](/References/Field#timezone).
3. The [`Entity`](/References/Entity) API, if the associated field is associated with an entity.
4. The field's [`Field Option Group`](/References/Field-Option-Group).
Only available when table inside a form.

<details>
<summary id="selectexample">Example</summary>

Below is part of the [Salesforce](https://dash11.comm100.io/ui/10100000/livechat/integrationsapi/salesforce/) page.

Configurations of the column are:
- `entityUniqueName`: `integrationSalesforceFieldMapping`
- `fieldName`: `comm100Field`
- `cellComponentType`: `select`
- `headerLabel`: `Comm100 Field`
- `selectDataSource`: `["salesforceMappingVisitorDynamicField", "customVariable", "salesforceMappingPreChatFormField", "salesforceMappingChatField"]`

![Select.png](/.attachments/Select-e49f7c73-d017-4ce0-9f74-2639ffef809a.png)
</details>

<br>

### switch

`value`: `13`

The field type should be [`bool`](/References/Field#bool). If the table inside a form, change local data when clicking. Otherwise, change remote data when clicking.

<details>
<summary id="switchexample">Example</summary>

Below is part of the [Agent Wrap-up](https://dash11.comm100.io/ui/10100000/livechat/campaign/agentwrapup/) page.

Configurations of the column are:
- `entityUniqueName`: `wrapupFormField`
- `fieldName`: `isRequired`
- `cellComponentType`: `switch`
- `headerLabel`: `Required`
- `headerHelperText`: `Agents need to complete the required fields before they can remove chat entries from the Agent Console.`

![Switch.png](/.attachments/Switch-f8f3155c-56dd-48f3-a575-f826533ecb88.png)
</details>

<br>

### text

`value`: `14`

Support HTML.

<details>
<summary id="textexample">Example</summary>

Below is part of the [Articles](https://dash11.comm100.io/ui/10100000/kb/knowledgebases/articles/) page.

Configurations of the column are:
- `entityUniqueName`: `article`
- `fieldName`: `helpful`
- `cellComponentType`: `text`
- `headerIcon`: `thumbUp`

![Text.png](/.attachments/Text-e3d9cbb4-70e9-4169-a3e5-69d9657ebb19.png)
</details>

<br>

### customComponent

`value`: `15`

Find component by [`CustomComponentName`](#CustomComponentName) and execute.

<details>
<summary id="customcomponentexample">Example</summary>

Below is part of the [Agents](https://dash11.comm100.io/ui/10100000/global/people/agents/) page.

Configurations of the column are:
- `entityUniqueName`: `agent`
- `fieldName`: `permissions`
- `cellComponentType`: `customComponent`
- `headerLabel`: `Permissions`
- `customComponentName`: `CGlobalAgentPermissionEditor`

![CustomComponent.png](/.attachments/CustomComponent-621e64ed-c068-442a-9a36-21c267973475.png)
</details>

<br>
<br>

## Order

`int`

Default: `0`.

The order of the column.

<br>
<br>

## Width

`string`

Default: `auto`. Optional. `auto` `{int}px` `{int}%`

The width of the column.

<br>
<br>

## HeaderIcon

`string`

Default: `""`. Optional.

- If present, use this as header content.
- If not present, use [`HeaderLabel`](#HeaderLabel) or [`Field Label`](/References/Field#Label) instead.

  [Example](#textexample)

<br>
<br>

## HeaderLabel

`string`

Default: `""`. Optional.

Support [variable](/References/UI/Variables).

- If present, use this as header content.
- If not present, use [`Field Label`](/References/Field#Label) instead.

  [Example](#avatarexample)

<br>
<br>

## HeaderHelperText

`string`

Default: `""`. Optional.

Show a question mark icon beside header text with a tooltip. Support [variable](/References/UI/Variables).

[Example](#switchexample)

<br>
<br>

## IsAllowSort

`bool`

Default: `false`.

- If true, the user can sort by the [`FieldName`](#FieldName) of this column.
- If false, the user can not sort by the [`FieldName`](#FieldName) of this column.

<br>
<br>

## IsShowContentInTooltip

`bool`

Default: `false`.

User can view whole content when content exceeds max lines.

- If true, show content in a tooltip.
- If false, hide the tooltip.

<br>
<br>

## Url

`string`

Default: `""`. Required when [`CellComponentType`](#CellComponentType) is [`link`](#link). Optional when [`CellComponentType`](#CellComponentType) is [`avatar`](#avatar).

Page URL to open. Only available for [`avatar`](#avatar) or [`link`](#link), support [variable](/References/UI/Variables).

[Example](#linkexample)

<br>
<br>

## CustomComponentName

`string`

Default: `""`. Required when [`CellComponentType`](#CellComponentType) is [`customComponent`](#customComponent).

Only available for [`customComponent`](#customComponent).

[Example](#customcomponentexample)

<br>
<br>

## SelectDataSource

`stringarray`

Default: `[]`. Optional.

The name list of the data source. Only available for [`select`](#select).

[Example](#selectexample)

<br>
<br>

## ConditionForShowing

`string`

Default: `""`. Optional.

Show current column when condition result is true, support [variable](/References/UI/Variables).

<details>
<summary>Example</summary>

Below is part of the [Chats](https://dash11.comm100.io/ui/10100000/livechat/history/chats/) page.

Configurations of the filter are:
- `entityUniqueName`: `chat`
- `fieldName`: `department`
- `cellComponentType`: `text`
- `headerLabel`: `Department`
- `conditionForShowing`: `@departmentConfig.isEnabled == true and @site.feature.department == true`

When the department is enabled.
![ConditionForShowing-true.png](/.attachments/ConditionForShowing-true-29619851-dce1-4362-9dad-3df02ff1b405.png)

When the department is disabled.
![ConditionForShowing-false.png](/.attachments/ConditionForShowing-false-e4953977-92fa-48ac-a40f-668159129876.png)
</details>

<br>
<br>

## ConditionForDisableCell

`string`

Default: `""`. Optional.

Disable current cell when condition result is true, support [variable](/References/UI/Variables).

<details>
<summary>Example</summary>

Below is part of the [Pre-chat](https://dash11.comm100.io/ui/10100000/livechat/campaign/prechat/) page.

Configurations of the filter are:
- `entityUniqueName`: `preChatFormField`
- `fieldName`: `isRequired`
- `cellComponentType`: `switch`
- `headerLabel`: `Required`
- `ConditionForDisableCell`: `$isVisible==false`

Required is enabled when visible is enabled. Otherwise, required is disabled when visible is disabled.
![ConditionForDisableCell.png](/.attachments/ConditionForDisableCell-4db8effc-9c60-4352-8f83-edbf61478dc7.png)
</details>

## IsOpenPageInNewTab 
`bool`
`version`: `v0.5.x`

Default: `false` Optional.
It only supports `Link` component.
- If `true`,  open the page in new tab.
- If `false`, open the page in the current tab.