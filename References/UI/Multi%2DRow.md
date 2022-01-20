Describe a multi-row which is used when the entity's [`IsMultiRecord`](/References/Entity#IsMultiRecord) is `yes` or `controlledByFeaturePoint` (Its result is true). The multi-row determine the presentation of multi-record, it can display in the form of a table, a tree, or an image list. Below is the [Campaign Auto Invitation Multi-Row](https://dash11.comm100.io/ui/10100000/livechat/campaign/invitation/autoinvitation/).
![Multi-Row.png](/.attachments/Multi-Row-46215921-bf08-4747-abb4-b09bc1ca4a8d.png)

## Fields
- [EntityUniqueName](#EntityUniqueName)
- [PresentationType](#PresentationType)
- [Title](#Title)
- [Description](#Description)
- [DescriptionPosition](#DescriptionPosition)
- [SizeForDisplayInDrawer](#SizeForDisplayInDrawer)
- [IsShowEnableSwitch](#IsShowEnableSwitch)
- [EnableSwitchConfigEntityName](#EnableSwitchConfigEntityName)
- [EnableSwitchConfigEntityFieldName](#EnableSwitchConfigEntityFieldName)
- [CustomComponentNameBelowTitle](#CustomComponentNameBelowTitle)
- [CustomComponentNameBelowList](#CustomComponentNameBelowList)
- [CustomComponentNameBesideTitle](#CustomComponentNameBesideTitle) `v0.5.x`

<br>
<br>

## EntityUniqueName

`string`

Default: `""`. Required.

The [`UniqueName`](/References/Entity#UniqueName) of the associated entity.

<br>
<br>

## PresentationType

`enum`

[`table (default) 0`](#table) [`tree 1`](#tree) [`imageList 2`](#imageList)

### table

`value`: `0`

This multi-row object must have [`Table`](/References/UI/Multi%2DRow/Table) property which describes how to render the table.

<details>
<summary>Example</summary>

Below is part of the [Custom Pages](https://dash11.comm100.io/ui/10100000/kb/knowledgebases/custompages/) page.

Configurations of the Multi-Row are:
- `entityUniqueName`: `customPage`
- `presentationType`: `table`

![Table.png](/.attachments/Table-17af384e-0a35-473b-807a-31409da3ad81.png)
</details>

<br>

### tree

`value`: `1`

This multi-row object must have [`Tree`](/References/UI/Multi%2DRow/Tree) property which describes how to render the tree.

<details>
<summary>Example</summary>

Below is part of the [Articles](https://dash11.comm100.io/ui/10100000/kb/knowledgebases/articles/) page.

Configurations of the Multi-Row are:
- `entityUniqueName`: `category`
- `presentationType`: `tree`

![Tree.png](/.attachments/Tree-33c5e1eb-99b0-40a1-a06b-1643c13d85f9.png)
</details>

<br>

### imageList

`value`: `2`

This multi-row object must have `ImageList` property which describes how to render the image list.

<details>
<summary>Example</summary>

Below is part of the [Images](https://dash11.comm100.io/ui/10100000/kb/knowledgebases/images/) page.

Configurations of the Multi-Row are:
- `entityUniqueName`: `image`
- `presentationType`: `imageList`

![ImageList.png](/.attachments/ImageList-9f65c397-949c-4205-a637-92378435183e.png)
</details>

<br>
<br>

## Title

`string`

Default: `""`. Optional.

Priority is higher than [Page Title](/References/UI/Page#Title). Support [variable](/References/UI/Variables).

[Example1](/References/UI/Page#tooltipexample) [Example2](/References/UI/Page#belowtitleexample)

<br>
<br>

## Description

`string`

Default: `""`. Optional.

Priority is higher than [Page Description](/References/UI/Page#Description). Support [variable](/References/UI/Variables).

[Example1](/References/UI/Page#tooltipexample) [Example2](/References/UI/Page#belowtitleexample)

<br>
<br>

## DescriptionPosition

`enum`

[`tooltip (default) 0`](#tooltip) [`belowTitle 1`](#belowTitle)

Priority is higher than [Page DescriptionPosition](/References/UI/Page#DescriptionPosition).

### tooltip

`value`: `0`

Display description in a question mark icon beside the page title.

[Example](/References/UI/Page#tooltipexample)

<br>

### belowTitle

`value`: `1`

Display description below the page title.

[Example](/References/UI/Page#belowtitleexample)

<br>
<br>

## SizeForDisplayInDrawer

`enum`

[`small (default) 0`](#small) [`large 1`](#large)

### small

`value`: `0`

The drawer's size is `small` when display multi-row in a drawer.

<details>
<summary>Example</summary>

Below is part of the [New Article](https://dash11.comm100.io/ui/10100000/kb/knowledgebases/articles/new) page (Manage tag drawer).

Configurations of the Multi-Row are:
- `entityUniqueName`: `tag`
- `sizeForDisplayInDrawer`: `small`

![Small.png](/.attachments/Small-d786e137-df4f-4ad1-9712-fb5fb15ac856.png)
</details>

<br>

### large

`value`: `1`

The drawer's size is `large` when display multi-row in a drawer.

<details>
<summary>Example</summary>

Below is part of the [Articles](https://dash11.comm100.io/ui/10100000/kb/knowledgebases/articles/) page (Manage knowledge base drawer).

Configurations of the Multi-Row are:
- `entityUniqueName`: `knowledgeBase`
- `sizeForDisplayInDrawer`: `large`

![Large.png](/.attachments/Large-1adbe1ff-68b9-4df2-9aa4-b8541989600d.png)
</details>

<br>
<br>

## IsShowEnableSwitch

`bool`

Default: `false`.

- If true, show a switch to enable/disable the function.

<details style="margin-left: 1em;">
<summary id="enableswitchexample">Example</summary>

Below is part of the [Departments](https://dash11.comm100.io/ui/10100000/global/people/departments/) page.

Configurations of the Multi-Row are:
- `entityUniqueName`: `department`
- `isShowEnableSwitch`: `true`
- `enableSwitchConfigEntityName`: `departmentConfig`
- `enableSwitchConfigEntityFieldName`: `isEnabled`

![Enable Switch.png](/.attachments/Enable%20Switch-bb90e828-4c09-4d90-9b77-61f411c12e90.png)
</details>

<br>

- If false, hide the switch.

<details style="margin-left: 1em;">
<summary>Example</summary>

Below is part of the [Agents](https://dash11.comm100.io/ui/10100000/global/people/agents/) page.

Configurations of the Multi-Row are:
- `entityUniqueName`: `agent`
- `isShowEnableSwitch`: `false`

![Disable Switch.png](/.attachments/Disable%20Switch-2a40b0d7-5db3-4aee-87e3-e463fc7521ea.png)
</details>

<br>
<br>

## EnableSwitchConfigEntityName

`string`

Default: `""`. Required when [`IsShowEnableSwitch`](#IsShowEnableSwitch) is true.

The entity [`UniqueName`](/References/Entity#UniqueName) which associated with the switch.

[Example](#enableswitchexample)

<br>
<br>

## EnableSwitchConfigEntityFieldName

`string`

Default: `""`. Required when [`IsShowEnableSwitch`](#IsShowEnableSwitch) is true.

The field [`Name`](/References/Field#Name) which associated with the switch. It belongs to the entity which is determined by [`EnableSwitchConfigEntityName`](#EnableSwitchConfigEntityName).

[Example](#enableswitchexample)

<br>
<br>

## CustomComponentNameBelowTitle

`string`

Default: `""`. Optional.

The custom component name which displays below the page title.

<details>
<summary>Example</summary>

Below is part of the [Learning](https://dash11.comm100.io/ui/10100000/bot/agentassist/agentassistlearning/) page.

Configurations of the Multi-Row are:
- `entityUniqueName`: `agentAssistLearningQuestion`
- `customComponentNameBelowTitle`: `CBotAgentAssistHighScoreReminder`

#### The position of the custom component can be controlled by CSS.
![CustomComponentNameBelowTitle.png](/.attachments/CustomComponentNameBelowTitle-afa648e0-8213-4b74-9216-a84316b84299.png)
</details>

<br>
<br>

## CustomComponentNameBelowList

`string`

Default: `""`. Optional.

The custom component name which displays below the list.

<details>
<summary>Example</summary>

Below is part of the [Installation](https://dash11.comm100.io/ui/10100000/livechat/campaign/installation/) page (Manage campaign drawer).

Configurations of the Multi-Row are:
- `entityUniqueName`: `campaign`
- `customComponentNameBelowList`: `CDynamicCampaignLink`

![CustomComponentNameBelowList.png](/.attachments/CustomComponentNameBelowList-0c5bca90-a307-49ab-a0ea-458cd0dea8bc.png)
</details>

<br/>
<br/>

## CustomComponentNameBesideTitle

`string`
`version`: `v0.5.x`

Default: `""`. Optional.
The custom component name which displays beside the list.