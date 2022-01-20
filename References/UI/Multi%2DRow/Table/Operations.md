Describe an operation. Include general info of an operation, such as `type` `iconName`, etc. Below is the [Learning Operations](https://dash11.comm100.io/ui/10100000/bot/agentassist/agentassistlearning/).
![Operations.png](/.attachments/Operations-ed6e2cf7-6ece-4e86-bd1d-365ec447cde9.png)

## Fields
- [EntityUniqueName](#EntityUniqueName)
- [Type](#Type)
- [Order](#Order)
- [IconName](#IconName)
- [Tooltip](#Tooltip)
- [Url](#Url)
- [IsOpenLinkInNewTab](#IsOpenLinkInNewTab)
- [FormNameForDrawerEdit](#FormNameForDrawerEdit)
- [CustomOperationName](#CustomOperationName)
- [ConditionForShowing](#ConditionForShowing)
- [ConditionForDisabled](#ConditionForDisabled)

<br>
<br>

## EntityUniqueName

`string`

Default: `""`. Required.

The [`UniqueName`](/References/Entity#UniqueName) of the associated entity.

<br>
<br>

## Type

[`customOperation (default) 0`](#customOperation) [`edit 1`](#edit) [`delete 2`](#delete) [`link 3`](#link) [`copy 4`](#copy) [`drawerEdit 5`](#drawerEdit)

### customOperation

`value`: `0`

Find component by [`CustomOperationName`](#CustomOperationName) and execute.

<details>
<summary id="customoperationexample">Example</summary>

Below is part of the [Learning](https://dash11.comm100.io/ui/10100000/bot/agentassist/agentassistlearning/) page.

Configurations of the operation are:
- `entityUniqueName`: `agentAssistLearningQuestion`
- `type`: `customOperation`
- `iconName`: `design`
- `tooltip`: `Add as similar questions to...`
- `customOperationName`: `CBotAgentAssistLinkOperation`

![CustomOperation.png](/.attachments/CustomOperation-42cc75c6-8d68-46b7-8c18-ecad311ce8cd.png)
</details>

<br>

### edit

`value`: `1`

It is used to edit a table row. If the table inside a form, open the edit entity drawer when clicking. Otherwise, open the edit entity page when clicking.

<details>
<summary id="editexample">Example</summary>

Below is part of the [Articles](https://dash11.comm100.io/ui/10100000/kb/knowledgebases/articles/) page.

Configurations of the operation are:
- `entityUniqueName`: `article`
- `type`: `edit`
- `iconName`: `edit`
- `tooltip`: `Edit`

![Edit.png](/.attachments/Edit-5385aa36-d433-48c1-b444-5212bbd03756.png)
</details>

<br>

### delete

`value`: `2`

Show [`DeleteConfirmDialog`](/References/UI/Multi%2DRow/DeleteConfirmDialog) when clicking. If confirmed then delete the current row.

<details>
<summary>Example</summary>

Below is part of the [Articles](https://dash11.comm100.io/ui/10100000/kb/knowledgebases/articles/) page.

Configurations of the operation are:
- `entityUniqueName`: `article`
- `type`: `delete`
- `iconName`: `delete`
- `tooltip`: `Delete`

![Delete.png](/.attachments/Delete-135c2b66-7180-425d-ad8b-bd0d4ca9fb19.png)
</details>

<br>

### link

`value`: `3`

Open a page when clicking. The URL of the page is determined by [`Url`](#Url).

<details>
<summary id="linkexample">Example</summary>

Below is part of the [Articles](https://dash11.comm100.io/ui/10100000/kb/knowledgebases/articles/) page.

Configurations of the operation are:
- `entityUniqueName`: `article`
- `type`: `link`
- `iconName`: `preview`
- `tooltip`: `Preview`
- `url`: `https://@config.kbFrontEndDomain/kb/@siteId/@query.scopingknowledgebaseid/a/$id?preview=true`
- `isOpenLinkInNewTab`: `true`

![Link.png](/.attachments/Link-34f4e27d-e524-4b76-ae4e-901ebfad2b0a.png)
</details>

<br>

### copy

`value`: `4`

Open a drawer with a form when clicking, and the form has a name input. Clone this row by the inputted name if the form submits successfully.

<details>
<summary>Example</summary>

Below is part of the [Invitation](https://dash11.comm100.io/ui/10100000/livechat/campaign/invitation/autoinvitation/) page.

Configurations of the operation are:
- `entityUniqueName`: `campaignAutoInvitation`
- `type`: `copy`
- `iconName`: `copy`
- `tooltip`: `Copy`

![Copy.png](/.attachments/Copy-2b47b86d-4a42-4f1d-afaf-47774bd58f86.png)
</details>

<br>

### drawerEdit

`value`: `5`

Open a drawer when clicking, display the form in the drawer. The form is determined by [`FormNameForDrawerEdit`](#FormNameForDrawerEdit).

<details>
<summary id="drawereditexample">Example</summary>

Below is part of the [Agents](https://dash11.comm100.io/ui/10100000/global/people/agents/) page.

Configurations of the operation are:
- `entityUniqueName`: `agent`
- `type`: `drawerEdit`
- `iconName`: `password`
- `tooltip`: `Reset password`
- `formNameForDrawerEdit`: `agentResetPassword`

![DrawerEdit.png](/.attachments/DrawerEdit-01aa80ad-a3a5-42e1-90d6-83294f923364.png)
</details>

<br>
<br>

## Order

`int`

Default: `0`.

The order of the operation.

<br>
<br>

## IconName

`string`

Default: `""`. Required.

The icon name of the operation.

[Example](#editexample)

<br>
<br>

## Tooltip

`string`

Default: `""`. Optional.

The tooltip of the operation. Support [variable](/References/UI/Variables).

[Example](#editexample)

<br>
<br>

## Url

`string`

Default: `""`. Required when [`Type`](#Type) is [`link`](#link).

The url to open when clicking. Support [field name as variable](/References/UI/Variables), only available for [`link`](#link).

[Example](#linkexample)

<br>
<br>

## IsOpenLinkInNewTab

`bool`

Only available for [`link`](#link).

- If true, open the link in a new browser tab.
- If false, open the link in the current browser tab.

[Example](#linkexample)

<br>
<br>

## FormNameForDrawerEdit

`string`

Default: `""`. Required when [`Type`](#Type) is [`drawerEdit`](#drawerEdit).

The form name for the drawer. Only available for [`drawerEdit`](#drawerEdit).

[Example](#drawereditexample)

<br>
<br>

## CustomOperationName

`string`

Default: `""`. Required when [`Type`](#Type) is [`customOperation`](#customOperation).

Only available for [`customOperation`](#customOperation).

[Example](#customoperationexample)

<br>
<br>

## ConditionForShowing

`string`

Default: `""`. Optional.

Show current operation when condition result is true, support [variable](/References/UI/Variables).

<details>
<summary>Example</summary>

Below is part of the [Chats](https://dash11.comm100.io/ui/10100000/livechat/history/chats/) page.

Configurations of the filter are:
- `entityUniqueName`: `article`
- `type`: `link`
- `iconName`: `preview`
- `tooltip`: `Preview`
- `url`: `https://@config.kbFrontEndDomain/kb/@siteId/@query.scopingknowledgebaseid/a/$id?preview=true`
- `isOpenLinkInNewTab`: `true`
- `conditionForShowing`: `$status=="draft`

When the status is draft.
![ConditionForShowing-true.png](/.attachments/ConditionForShowing-true-fb77d273-6166-4407-9680-f7f65ea59fad.png)

When the status is not draft.
![ConditionForShowing-false.png](/.attachments/ConditionForShowing-false-3e02c7cd-c70e-4cc6-a251-4cf5cb9f121b.png)
</details>

<br>
<br>

## ConditionForDisabled

`string`

Default: `""`. Optional.

Disable current operation when condition result is true, support [variable](/References/UI/Variables).

<details>
<summary>Example</summary>

Below is part of the [Pre-chat](https://dash11.comm100.io/ui/10100000/livechat/campaign/prechat/) page.

Configurations of the filter are:
- `entityUniqueName`: `preChatFormField`
- `type`: `delete`
- `iconName`: `delete`
- `tooltip`: `Delete`
- `conditionForDisabled`: `$field.isSystem==true`

The operation is enabled when field.isSystem is true. Otherwise, the operation is disabled when field.isSystem is false.
![ConditionForDisabled.png](/.attachments/ConditionForDisabled-ece4fd9f-77dd-4084-9be2-54fd75b3b2e4.png)
</details>