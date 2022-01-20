Describe a component above the table. Includes general info of a component above table, such as `type` `text`, etc. Below is the [Campaign Auto Invitation ComponentsAboveTable](https://dash11.comm100.io/ui/10100000/livechat/campaign/invitation/autoinvitation/). If the table is in a form, this component usually renders under the table and opens a drawer, and then handle something in the drawer when you click it.
![ComponentsAboveTable.png](/.attachments/ComponentsAboveTable-549581f0-8fba-4272-871e-a07ebf1fa754.png)

## Fields
- [EntityUniqueName](#EntityUniqueName)
- [Type](#Type)
- [Order](#Order)
- [Text](#Text)
- [IsPrimaryButton](#IsPrimaryButton)
- [ButtonActionId](#ButtonActionId)
- [CustomComponentName](#CustomComponentName)
- [ConditionForShowing](#ConditionForShowing)

<br>
<br>

## EntityUniqueName

`string`

Default: `""`. Required.

The [`UniqueName`](/References/Entity#UniqueName) of the associated entity.

<br>
<br>

## Type

`enum`

[`newButton (default) 0`](#newButton) [`customButton 1`](#customButton) [`customComponent 2`](#customComponent)

### newButton

`value`: `0`

It is used to add a row to the table. If the table inside a form, open the new entity drawer when clicking. Otherwise, open the new entity page when clicking.

<details>
<summary>Example</summary>

Below is part of the [Articles](https://dash11.comm100.io/ui/10100000/kb/knowledgebases/articles/) page.

Configurations of the component above table are:
- `entityUniqueName`: `article`
- `type`: `newButton`

![NewButton.png](/.attachments/NewButton-90f668c9-b698-47cd-9ad2-dd35e5a3bbcc.png)
</details>

<br>

### customButton

`value`: `1`

Display as a normal button. The behavior of the button is determined by the [button action](/References/UI/Button-Action).

<details>
<summary id="custombuttonexample">Example</summary>

Below is part of the [Learning](https://dash11.comm100.io/ui/10100000/bot/aichatbot/learning/) page.

Configurations of the component above table are:
- `entityUniqueName`: `chatbotLearningQuestion`
- `type`: `customButton`
- `text`: `Add Multiple Visitor Questions`
- `isPrimaryButton`: `false`
- `buttonAction`:
  - `type`: `entityInDrawer`
  - `targetEntityName`: `addMultipleVisitorQuestions`

![CustomButton.png](/.attachments/CustomButton-7ef3ac94-b22c-4be8-9c7b-df5482b41447.png)
</details>

<br>

### customComponent

`value`: `2`

Find component by [`CustomComponentName`](#CustomComponentName) and execute.

<details>
<summary id="customcomponentexample">Example</summary>

Below is part of the [Agents](https://dash11.comm100.io/ui/10100000/global/people/agents/) page.

Configurations of the component above table are:
- `entityUniqueName`: `agent`
- `type`: `customComponent`
- `customComponentName`: `CGlobalNewAgentButton`

![CustomComponent.png](/.attachments/CustomComponent-61a49b60-1b4b-45dd-bb5f-610360f42b6d.png)
</details>

<br>
<br>

## Order

`int`

Default: `0`.

The order of the component.

<br>
<br>

## Text

`string`

Default: `""`. Optional.

Button text. Only available when [`Type`](#Type) is not [`customComponent`](#customComponent). Support [variable](/References/UI/Variables).

[Example](#custombuttonexample)

<br>
<br>

## IsPrimaryButton

`bool`

Default: `false`.

Only available for [`customButton`](#customButton).

- If true, the button has a primary style (with the blue background and white text).
- If false, the button does not have a primary style.

[Example](#custombuttonexample)

<br>
<br>

## ButtonActionId

`string`

Default: `""`. Required when [`Type`](#Type) is [`customButton`](#customButton).

The button action [`Id`](/References/UI/Button-Action#`Id`). Only available for [`customButton`](#customButton).

[Example](#custombuttonexample)

<br>
<br>

## CustomComponentName

`string`

Default: `""`. Required when [`Type`](#Type) is [`customComponent`](#customComponent).

Only available for [`customComponent`](#customComponent).

[Example](#customcomponentexample)

<br>
<br>

## ConditionForShowing

`string`

Default: `""`. Optional.

Show current component above table when condition result is true, support [variable](/References/UI/Variables).

<details>
<summary>Example</summary>

Below is part of the [Chats](https://dash11.comm100.io/ui/10100000/livechat/history/chats/) page.

Configurations of the component above table are:
- `entityUniqueName`: `chat`
- `type`: `customComponent`
- `text`: `Export All`
- `customComponentName`: `CChatExportAllOperation`
- `conditionForShowing`: `@site.feature.exportHistory==true`

When the export history feature is enabled.
![ConditionForShowing-True.png](/.attachments/ConditionForShowing-True-7ea314c9-f36f-434c-9719-81d260000cb5.png)

When the export history feature is disabled.
![ConditionForShowing-False.png](/.attachments/ConditionForShowing-False-637616a7-e078-40c0-ad5d-ce438227a8c9.png)
</details>