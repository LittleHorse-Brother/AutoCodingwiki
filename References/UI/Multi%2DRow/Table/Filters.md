Describe a filter. Include general info of a filter, such as `conditionName` `componentType`, etc. Below is the [Learning Filters](https://dash11.comm100.io/ui/10100000/bot/agentassist/agentassistlearning/). If the table is in a form, it usually filters the data locally without the network request.
![Filters.png](/.attachments/Filters-8a4da507-4f0e-4ce2-b3e1-e21d8651cdc5.png)

## Fields
- [EntityUniqueName](#EntityUniqueName)
- [ConditionName](#ConditionName)
- [ComponentType](#ComponentType)
- [Order](#Order)
- [Default](#Default)
- [IsClearable](#IsClearable)
- [Placeholder](#Placeholder)
- [CustomFilterName](#CustomFilterName)
- [IconName](#IconName)
- [ConditionForShowing](#ConditionForShowing)

<br>
<br>

## EntityUniqueName

`string`

Default: `""`. Required.

The [`UniqueName`](/References/Entity#UniqueName) of the associated entity.

<br>
<br>

## ConditionName

`string`

Default: `""`. Optional when the table filter is [advanced](/References/UI/Multi%2DRow/Table#IsAdvanceFilter) and [`componentType`](#componentType) is [`custom`](#custom).

The name of the [HTTPGetCondition](/References/Entity-API#[N]-HTTPGetCondition).Name in Server API Entity.

<br>
<br>

## ComponentType

`enum`

When the component value changed, the table data will reload.

[`keywordSearch (default) 0`](#keywordSearch) [`select 1`](#select) [`dateRangePicker 2`](#dateRangePicker) [`custom 4`](#custom)

### keywordSearch

`value`: `0`

Display as an input component.

<details>
<summary id="keywordsearchexample">Example</summary>

Below is part of the [Intents](https://dash11.comm100.io/ui/10100000/bot/aichatbot/intents/) page.

Configurations of the filter are:
- `entityUniqueName`: `chatbotIntent`
- `conditionName`: `keywords`
- `componentType`: `keywordSearch`
- `Placeholder`: `Search intent`

![KeywordSearch.png](/.attachments/KeywordSearch-ea193f9f-d8d4-4107-8264-ecf6bbbbffd2.png)
</details>

<br>

### select

`value`: `1`

The data of the select comes from:
1. The [`Entity`](/References/Entity) API, if [`ConditionName`](#ConditionName) is associated with an entity.
2. [`Field Option Group`](/References/Field-Option-Group) which associated with the field, if [`ConditionName`](#ConditionName) is associated with a field.

<details style="margin-left: 1em;">
<summary>Example</summary>

Below is part of the [Articles](https://dash11.comm100.io/ui/10100000/kb/knowledgebases/articles/) page.

Configurations of the filter are:
- `entityUniqueName`: `article`
- `conditionName`: `tagId`
- `componentType`: `select`

![Select.png](/.attachments/Select-03f6034d-bbf8-483b-ab36-c34ca9c63d35.png)
</details>

<br>

### dateRangePicker

`value`: `2`

The default value:
1. Last 30 days not include today, if the table filter is not [advanced](/References/UI/Multi%2DRow/Table#IsAdvanceFilter).
2. Today, if the table filter is [advanced](/References/UI/Multi%2DRow/Table#IsAdvanceFilter).

The value format:
1. `YYYY-MM-DD HH:mm:ss`, the type of the associated field is [`datetime`](/References/Field#datetime).
2. `YYYY-MM-DD`, the type of the associated field is date is [`date`](/References/Field#date).

<details style="margin-left: 1em;">
<summary>Example</summary>

Below is part of the [Learning](https://dash11.comm100.io/ui/10100000/bot/agentassist/agentassistlearning/) page.

Configurations of the filter are:
- `entityUniqueName`: `agentAssistLearningQuestion`
- `conditionName`: `dateRange`
- `componentType`: `dateRangePicker`

![DateRangerPicker.png](/.attachments/DateRangerPicker-01d70479-e66d-4c19-86c4-361b504ec919.png)
</details>

<br>

### custom

`value`: `4`

Find component by [`CustomFilterName`](#CustomFilterName) and execute.

<details>
<summary id="customexample">Example</summary>

Below is part of the [Audit Log](https://dash11.comm100.io/ui/10100000/global/security/auditlogmanage/) page.

Configurations of the filter are:
- `entityUniqueName`: `auditLog`
- `conditionName`: `module`
- `componentType`: `custom`
- `customFilterName`: `CGlobalLogFilter`

![Custom.png](/.attachments/Custom-2509e8fa-2594-4c26-89a8-1446b0b56d25.png)
</details>

<br>
<br>

## Order

`int`

Default: `0`.

The order of the filter.

<br>
<br>

## Default

`stringarray`

Default: `[]`. Optional.

The default value of the filter component.
- When [`ComponentType`](#ComponentType) is [`dateRangePicker`](#dateRangePicker).
  - Only the first and second (if exists) values in this will pass to the filter component.
  - Support `@today-n` format. It means how many days (n) before today.
- When [`ComponentType`](#ComponentType) is **not** [`dateRangePicker`](#dateRangePicker).
  - When the table filter is [advanced](/References/UI/Multi%2DRow/Table#IsAdvanceFilter). All the values in this will pass to the filter component.
  - When the table filter is **not** [advanced](/References/UI/Multi%2DRow/Table#IsAdvanceFilter). Only the first value in this will pass to the filter component.

[Example](#isclearablefalseexample)

<br>
<br>

## IsClearable

`bool`

Default: `true`. Only available for [`select`](#select) and the table filter is **not** [advanced](/References/UI/Multi%2DRow/Table#IsAdvanceFilter).

- If true, display the clear icon in the filter component when focused.

<details style="margin-left: 1em;">
<summary>Example</summary>

Below is part of the [Articles](https://dash11.comm100.io/ui/10100000/kb/knowledgebases/articles/) page.

Configurations of the filter are:
- `entityUniqueName`: `article`
- `conditionName`: `tagId`
- `componentType`: `select`
- `isClearable`: `true`

![IsClearable-True.png](/.attachments/IsClearable-True-f77caac1-6278-48d3-a6ca-58e6aa044f6a.png)
</details>

<br>

- If false, do not display the clear icon.

<details style="margin-left: 1em;">
<summary id="isclearablefalseexample">Example</summary>

Below is part of the [Dynamics 365](https://dash11.comm100.io/ui/10100000/integration/dynamics365/) page.

Configurations of the filter are:
- `entityUniqueName`: `integrationDynamics365FieldMapping`
- `conditionName`: `dynamics365Entity`
- `componentType`: `select`
- `default`: `["contact"]`
- `isClearable`: `false`

![IsClearable-False.png](/.attachments/IsClearable-False-6b3deee9-a22d-47c5-b662-0c2624b17755.png)
</details>

<br>
<br>

## Placeholder

`string`

Default: `""`. Optional.

Display placeholder in the filter component. Only available for [`select`](#select) and [`keywordSearch`](#keywordSearch). Support [variable](/References/UI/Variables).

[Example](#keywordsearchexample)

<br>
<br>

## CustomFilterName

`string`

Default: `""`. Required when [`ComponentType`](#ComponentType) is [`custom`](#custom).

Only available for [`custom`](#custom).

[Example](#customexample)

<br>
<br>
 
## IconName

`string`

Default: `""`. Optional.

Display icon beside filter. Only available when the table filter is [advanced](/References/UI/Multi%2DRow/Table#IsAdvanceFilter).

<br>
<br>

## ConditionForShowing

`string`

Default: `""`. Optional.

Show current filter when condition result is true, support [variable](/References/UI/Variables).

<details>
<summary>Example</summary>

Below is part of the [Chats](https://dash11.comm100.io/ui/10100000/livechat/history/chats/) page.

Configurations of the filter are:
- `entityUniqueName`: `chat`
- `conditionName`: `departmentId`
- `componentType`: `custom`
- `customFilterName`: `CFilterDepartmentSelect`
- `conditionForShowing`: `@departmentConfig.isEnabled == true and @site.feature.department == true`

When the department is enabled.
![ConditionForShowing-true.png](/.attachments/ConditionForShowing-true-e6d13193-07e2-44a6-9163-556b9e7c4f4c.png)

When the department is disabled.
![ConditionForShowing-false.png](/.attachments/ConditionForShowing-false-f552ff3f-c5bd-4ea9-a335-1e07a73c1d7a.png)
</details>