Describe a batch operation. Include general info of a batch operation, such as `type` `iconName`, etc. Below is the [Learning BatchOperations](https://dash11.comm100.io/ui/10100000/bot/agentassist/agentassistlearning/).
![BatchOperations.png](/.attachments/BatchOperations-12bcc27d-d486-475f-b991-b535bf077b3b.png)

## Fields
- [EntityUniqueName](#EntityUniqueName)
- [Type](#Type)
- [Order](#Order)
- [IconName](#IconName)
- [Label](#Label)
- [CustomBatchOperationName](#CustomBatchOperationName)
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

[`delete (default) 0`](#delete) [`customBatchOperation 1`](#customBatchOperation)

### delete

`value`: `0`

Show [`DeleteConfirmDialog`](/References/UI/Multi%2DRow/DeleteConfirmDialog) when clicking. If confirmed then delete the selected rows.

<details>
<summary>Example</summary>

Below is part of the [Learning](https://dash11.comm100.io/ui/10100000/bot/agentassist/agentassistlearning/) page.

Configurations of the batch operation are:
- `entityUniqueName`: `agentAssistLearningQuestion`
- `type`: `delete`

![Delete.png](/.attachments/Delete-998c4930-e01d-4764-93c0-c2f3d6a1b1b2.png)
</details>

<br>

### customBatchOperation

`value`: `1`

Find component by [`CustomBatchOperationName`](#CustomBatchOperationName) and execute.

<details>
<summary id="custombatchoperationexample">Example</summary>

Below is part of the [Learning](https://dash11.comm100.io/ui/10100000/bot/agentassist/agentassistlearning/) page.

Configurations of the batch operation are:
- `entityUniqueName`: `agentAssistLearningQuestion`
- `type`: `customBatchOperation`
- `label`: `Add as Similar Question to...`
- `customBatchOperationName`: `CBotAgentAssistBatchLinkOperation`

![CustomBatchOperation.png](/.attachments/CustomBatchOperation-2b4d9114-6339-47b1-a729-86be1c0cc325.png)
</details>

<br>
<br>

## Order

`int`

Default: `0`.

The order of the batch operation.

<br>
<br>

## IconName

`string`

Default: `""`. Optional.

The icon name of the batch operation.

<br>
<br>

## Label

`string`

Default: `""`. Optional.

The label of the batch operation. Support [variable](/References/UI/Variables).

[Example](#custombatchoperationexample)

<br>
<br>

## CustomBatchOperationName

`string`

Default: `""`. Required when [`Type`](#Type) is [`customBatchOperation`](#customBatchOperation).

Only available for [`customBatchOperation`](#customBatchOperation).

[Example](#custombatchoperationexample)

<br>
<br>

## ConditionForShowing

`string`

Default: `""`. Optional.

Show current batch operation when condition result is true, support [variable](/References/UI/Variables).

<details>
<summary>Example</summary>

Below is part of the [Chats](https://dash11.comm100.io/ui/10100000/livechat/history/chats/) page.

Configurations of the batch operation are:
- `entityUniqueName`: `chat`
- `type`: `customBatchOperation`
- `customComponentName`: `CChatExportSelectedOperation`
- `conditionForShowing`: `@site.feature.exportHistory==true`

When the export history feature is enabled.
![ConditionForShowing-True.png](/.attachments/ConditionForShowing-True-6f26a01b-5e31-4934-9608-7f476a8f7def.png)

When the export history feature is disabled.
![ConditionForShowing-False.png](/.attachments/ConditionForShowing-False-ac0b7e1c-2a4e-4071-a29e-e0a085bce7d4.png)
</details>