Describe a delete confirm dialog. Include general info of a delete confirm dialog, such as `type` `message`, etc. Below is the [Category DeleteConfirmDialog](https://dash11.comm100.io/ui/10100000/kb/knowledgebases/articles/).
![DeleteConfirmDialog.png](/.attachments/DeleteConfirmDialog-973d5d78-f44d-4431-892d-00ea5095d1fc.png)

## Fields
- [EntityUniqueName](#EntityUniqueName)
- [Type](#Type)
- [Message](#Message)
- [MessageForBatchDelete](#MessageForBatchDelete)
- [CheckboxMessage](#CheckboxMessage)
- [Title](#Title) `v0.5.x`
- [OkText](#OkText) `v0.5.x`
- [CancelText](#CancelText) `v0.5.x`

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

[`basic (default) 0`](#basic) [`checkbox 1`](#checkbox)

### basic

`value`: `0`

No extra option, just DELETE button and CANCEL button.

<details>
<summary id="basicdeleteexample">Example For Delete</summary>

Below is part of the [Learning](https://dash11.comm100.io/ui/10100000/bot/agentassist/agentassistlearning/) page.

Configurations of the delete confirm dialog are:
- `entityUniqueName`: `agentAssistLearningQuestion`
- `message`: `Are you sure you want to delete the visitor question "$question"?`
- `type`: `basic`

![BasicDelete.png](/.attachments/BasicDelete-13641d39-b1bb-4290-a2ad-5e07e529eea2.png)
</details>

<details>
<summary id="basicbatchdeleteexample">Example For Batch Delete</summary>

Below is part of the [Learning](https://dash11.comm100.io/ui/10100000/bot/agentassist/agentassistlearning/) page.

Configurations of the delete confirm dialog are:
- `entityUniqueName`: `agentAssistLearningQuestion`
- `messageForBatchDelete`: `Are you sure you want to delete the $count visitor questions?`
- `type`: `basic`

![BasicBatchDelete.png](/.attachments/BasicBatchDelete-e23837b7-a909-43c0-9b03-60f5b6ed24ce.png)
</details>

<br>

### checkbox

`value`: `1`

Show a checkbox and require a check before delete.

<details>
<summary id="checkboxdeleteexample">Example For Delete</summary>

Below is part of the [Learning](https://dash11.comm100.io/ui/10100000/bot/aichatbot/learning/) page.

Configurations of the delete confirm dialog are:
- `entityUniqueName`: `chatbotLearningQuestion`
- `message`: `Are you sure you want to delete the visitor question "$question"?`
- `type`: `checkbox`
- `checkboxMessage`: `"I understand all questions will be deleted and it can not be undone."`

![CheckboxDelete.png](/.attachments/CheckboxDelete-d64e5991-0268-4c59-b59f-4e65b3583325.png)
</details>

<details>
<summary id="checkboxbatchdeleteexample">Example For Batch Delete</summary>

Below is part of the [Learning](https://dash11.comm100.io/ui/10100000/bot/aichatbot/learning/) page.

Configurations of the delete confirm dialog are:
- `entityUniqueName`: `chatbotLearningQuestion`
- `messageForBatchDelete`: `Are you sure you want to delete the $count visitor questions?`
- `type`: `checkbox`
- `checkboxMessage`: `"I understand all questions will be deleted and it can not be undone."`

![CheckboxBatchDelete.png](/.attachments/CheckboxBatchDelete-245e6384-116b-4e9e-852b-baae77a51fa3.png)
</details>

<br>
<br>

## Message

`string`

Default: `""`. Required when the multi-row can delete.

Prompt information for the user to delete. Support [variable](/References/UI/Variables). Support [current entity field as variable](/References/UI/Variables).

[Example1](#basicdeleteexample), [Example2](#checkboxdeleteexample)


<br>
<br>

## MessageForBatchDelete

`string`

Default: `""`. Required when the multi-row can batch delete. 

Prompt information for the user to batch delete. Support [variable](/References/UI/Variables). Support ["$count" variable](/References/UI/Variables).

[Example1](#basicbatchdeleteexample), [Example2](#checkboxbatchdeleteexample)

<br>
<br>

## CheckboxMessage

`string`

Default: `""`. Required when [`Type`](#Type) is [`checkbox`](#checkbox).

Show this message beside checkbox. Only available for [`checkbox`](#checkbox). Support [variable](/References/UI/Variables).

[Example1](#checkboxdeleteexample), [Example2](#checkboxbatchdeleteexample)

<br/>
<br/>

## Title
`string`
`version`: `v0.5.x`

Default: `Confirm Delete`, optional.
If configure it, replaces the default title of confirm dialog.

<br/>
<br/>

## OkText
`string`
`version`: `v0.5.x`

Default: `Delete`, optional.
If configure it, replaces the default label of delete button.

![image.png](/.attachments/image-b0b49541-bdf8-42ae-b3ae-b3b57fba21d3.png)

<br/>
<br/>

## CancelText
`string`
`version`: `v0.5.x`

Default: `Cancel`, optional.
If configure it, replaces the default label of cancel button.
![image.png](/.attachments/image-d6aab7b2-5265-4f0c-940f-cae79d38cfb8.png)