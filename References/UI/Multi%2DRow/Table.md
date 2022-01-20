Describe a table. Include general info of a table, such as `maxLinesOfRow` `messageForNoRecords`, etc. Below is the [Campaign Auto Invitation Table](https://dash11.comm100.io/ui/10100000/livechat/campaign/invitation/autoinvitation/).
![Table.png](/.attachments/Table-4cb84247-ccf1-4cbc-88fc-6db9fa2e3563.png)

## Fields
- [EntityUniqueName](#EntityUniqueName)
- [MaxLinesOfRow](#MaxLinesOfRow)
- [DefaultSortFieldName](#DefaultSortFieldName)
- [DefaultSortOrder](#DefaultSortOrder)
- [IsAdvanceFilter](#IsAdvanceFilter)
- [IsEnableBatchOperation](#IsEnableBatchOperation)
- [IsTableRowSelectable](#IsTableRowSelectable)
- [IsAllowReorder](#IsAllowReorder)
- [IsPagination](#IsPagination)
- [IfShowAllRows](#IfShowAllRows)
- [MessageForNoRecords](#MessageForNoRecords)

<br>
<br>

## EntityUniqueName

`string`

Default: `""`. Required.

The [`UniqueName`](/References/Entity#UniqueName) of the associated entity.

<br>
<br>

## MaxLinesOfRow

`int`

Default: `1`.

Show `…` if table cell content exceeds max lines. Can only be an int from 1 and 10.

<br>
<br>

## DefaultSortFieldName

`string`

Default: `""`. Optional.

The field [`Name`](/References/Field#Name) to the current entity. When the table is first loaded, it is used to sort.

[Example1](#ascexample), [Example2](#descexample)

<br>
<br>

## DefaultSortOrder

`enum`

[`asc (default)`](#asc) [`desc`](#desc)

When the table is first loaded, it is used to determine how to sort.

### asc

Sort in ascending order.

<details>
<summary id="ascexample">Example</summary>

Below is part of the [Agents](https://dash11.comm100.io/ui/10100000/global/people/agents/) page.

Configurations of the table are:
- `entityUniqueName`: `agent`
- `defaultSortFieldName`: `displayName`
- `defaultSortOrder`: `asc`

![DefaultSortOrder-Asc.png](/.attachments/DefaultSortOrder-Asc-d2e91fe4-b969-44f6-94c8-04fc498d37f8.png)
</details>

<br>

### desc

Sort in descending order.

<details>
<summary id="descexample">Example</summary>

Below is part of the [Articles](https://dash11.comm100.io/ui/10100000/kb/knowledgebases/articles/) page.

Configurations of the table are:
- `entityUniqueName`: `article`
- `defaultSortFieldName`: `modifiedTime`
- `defaultSortOrder`: `desc`

![DefaultSortOrder-Desc.png](/.attachments/DefaultSortOrder-Desc-34f3d00e-be9e-4650-8469-21fb58ae90cd.png)
</details>

<br>
<br>

## IsAdvanceFilter

`bool`

Default: `false`.

When the table filter is advanced, the [`ComponentsAboveTable`](/References/UI/Multi%2DRow/Table/ComponentsAboveTable) and [`Filters`](/References/UI/Multi%2DRow/Table/Filters) are rendered in different styles.

- If true, the table filter is advanced.

<details style="margin-left: 1em;">
<summary>Example</summary>

Below is part of the [Chats](https://dash11.comm100.io/ui/10100000/livechat/history/chats/) page.

Configurations of the table are:
- `entityUniqueName`: `chat`
- `isAdvanceFilter`: `true`

![IsAdvanceFilter-True.png](/.attachments/IsAdvanceFilter-True-f2c26562-7397-4a28-8589-35201ebc5a2b.png)
</details>

<br>

- If false, the table filter is not advanced.

<details style="margin-left: 1em;">
<summary>Example</summary>

Below is part of the [Articles](https://dash11.comm100.io/ui/10100000/kb/knowledgebases/articles/) page.

Configurations of the table are:
- `entityUniqueName`: `article`
- `isAdvanceFilter`: `false`

![IsAdvanceFilter-False.png](/.attachments/IsAdvanceFilter-False-2edbd427-8ae1-4b93-a972-ee9018b7a24a.png)
</details>

<br>
<br>

## IsEnableBatchOperation

`bool`

Default: `false`.

- If true, table batch operation is enabled.

<details style="margin-left: 1em;">
<summary>Example</summary>

Below is part of the [Learning](https://dash11.comm100.io/ui/10100000/bot/agentassist/agentassistlearning/) page.

Configurations of the table are:
- `entityUniqueName`: `agentAssistLearningQuestion`
- `isEnableBatchOperation`: `true`

![IsEnableBatchOperation-True.png](/.attachments/IsEnableBatchOperation-True-8c87d81e-0cf9-42fa-b204-f4832892209c.png)
</details>

<br>

- If false, table batch operation is disabled.

<details style="margin-left: 1em;">
<summary>Example</summary>

Below is part of the [Articles](https://dash11.comm100.io/ui/10100000/kb/knowledgebases/articles/) page.

Configurations of the table are:
- `entityUniqueName`: `article`
- `isEnableBatchOperation`: `false`

![IsEnableBatchOperation-False.png](/.attachments/IsEnableBatchOperation-False-697a46a3-303b-47ec-8065-e139712eb814.png)
</details>

<br>
<br>

## IsTableRowSelectable

`bool`

Default: `false`.

The selected table row will add a style class that adds a background color to this table row.

- If true, the user can select the table row when clicking.

<details style="margin-left: 1em;">
<summary>Example</summary>

Below is part of the [Chats](https://dash11.comm100.io/ui/10100000/livechat/history/chats/) page.

Configurations of the table are:
- `entityUniqueName`: `chat`
- `isTableRowSelectable`: `true`

![IsTableRowSelectable-True.png](/.attachments/IsTableRowSelectable-True-9be28f0b-c875-4ab2-9785-d38ffe61e841.png)
</details>

<br>

- If false, the user can not select the table row when clicking.

<details style="margin-left: 1em;">
<summary>Example</summary>

Below is part of the [Articles](https://dash11.comm100.io/ui/10100000/kb/knowledgebases/articles/) page.

Configurations of the table are:
- `entityUniqueName`: `article`
- `isTableRowSelectable`: `false`

![IsTableRowSelectable-False.png](/.attachments/IsTableRowSelectable-False-553a90b5-a01a-427e-9d82-a8ce2903cdb8.png)
</details>

<br>
<br>

## IsAllowReorder

`bool`

Default: `false`.

Only available for the entity with the `order` field.

- If true, the user can change the order of the table row.

<details style="margin-left: 1em;">
<summary>Example</summary>

Below is part of the [Custom Away Status](https://dash11.comm100.io/ui/10100000/global/people/customawaystatus/) page.

Configurations of the table are:
- `entityUniqueName`: `agentAwayStatus`
- `isAllowReorder`: `true`

![IsAllowReorder-True.png](/.attachments/IsAllowReorder-True-201989a9-ebc8-46ed-96bf-c55866bb4b23.png)
</details>

<br>

- If false, the user can not change the order of the table row.

<details style="margin-left: 1em;">
<summary>Example</summary>

Below is part of the [Articles](https://dash11.comm100.io/ui/10100000/kb/knowledgebases/articles/) page.

Configurations of the table are:
- `entityUniqueName`: `article`
- `isAllowReorder`: `false`

![IsAllowReorder-False.png](/.attachments/IsAllowReorder-False-d1ea5f38-250a-44f2-b215-8a7201bd70e6.png)
</details>

<br>
<br>

## IsPagination

`bool`

Default: `false`.

Table inside form is not supported.

- If true, show pagination under table rows.

<details style="margin-left: 1em;">
<summary>Example</summary>

Below is part of the [Articles](https://dash11.comm100.io/ui/10100000/kb/knowledgebases/articles/) page.

Configurations of the table are:
- `entityUniqueName`: `article`
- `isPagination`: `true`

![IsPagination-True.png](/.attachments/IsPagination-True-26113613-4532-47a4-9169-08905ef989e6.png)
</details>

<br>

- If false, hide pagination under table rows.

<details style="margin-left: 1em;">
<summary>Example</summary>

Below is part of the [Custom Away Status](https://dash11.comm100.io/ui/10100000/global/people/customawaystatus/) page.

Configurations of the table are:
- `entityUniqueName`: `agentAwayStatus`
- `isPagination`: `false`

![IfShowAllRows-false.png](/.attachments/IfShowAllRows-false-3da9cde5-fde6-40a5-8f03-c26e37b78f92.png)
</details>

<br>
<br>

## IfShowAllRows

`bool`

Default: `false`.

The server API [`isPagination`](#isPagination) must be false. Only available when table inside a form.

- If true, show all rows.

<details style="margin-left: 1em;">
<summary>Example</summary>

Below is part of the [Pre-chat](https://dash11.comm100.io/ui/10100000/livechat/campaign/prechat/) page.

Configurations of the table are:
- `entityUniqueName`: `preChatFormField`
- `ifShowAllRows`: `true`

![IfShowAllRows-true.png](/.attachments/IfShowAllRows-true-8126c054-3d31-41ee-b102-befc99511a47.png)
</details>

<br>

- If false, show 5 rows by default with a More button under the table, click to show all rows. Hide the more button when less than 5 rows.

<details style="margin-left: 1em;">
<summary>Example</summary>

Below is part of the [Auto Distribution](https://dash11.comm100.io/ui/10100000/livechat/settings/autodistribution/) page.

Configurations of the table are:
- `entityUniqueName`: `agentAutoDistributionConfig`
- `ifShowAllRows`: `false`

![IfShowAllRows-false.png](/.attachments/IfShowAllRows-false-00ec1011-7033-4826-b20c-2a2225362888.png)
</details>

<br>
<br>

## MessageForNoRecords

`string`

Default: `No records found.`.

Display message when there are no records in the table. Support [variable](/References/UI/Variables).

<details>
<summary>Example</summary>

Below is part of the [IP Allowlist](https://dash11.comm100.io/ui/10100000/global/security/ipallowlist/loginipallowlist/) page.

Configurations of the table are:
- `entityUniqueName`: `loginIpAllowlist`
- `messageForNoRecords`: `Access to your Comm100 account is accepted from any IP address`

![MessageForNoRecords.png](/.attachments/MessageForNoRecords-27e71cc6-6505-4c96-b62d-23ec545333be.png)
</details>