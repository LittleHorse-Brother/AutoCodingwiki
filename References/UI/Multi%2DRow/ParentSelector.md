Describe a parent selector which when its selected value changed, the current entity component (such as a `table`) will update by this value. The current entity's relationship to the parent selector entity which is determined by `FieldName` must be `oneToMany`. Include presentation type, associated field name, and the `tree` configurations of the parent selector. Below is the [Articles ParentSelector](https://dash11.comm100.io/ui/10100000/kb/knowledgebases/articles/).
![ParentSelector.png](/.attachments/ParentSelector-29525f4b-1b95-41c8-adbf-0c746be8d68d.png)

## Fields
- [EntityUniqueName](#EntityUniqueName)
- [ComponentType](#ComponentType)
- [FieldName](#FieldName)
- [TreeAllItemsLabel](#TreeAllItemsLabel)
- [TreeAllItemsIcon](#TreeAllItemsIcon)

<br>
<br>

## EntityUniqueName

`string`

Default: `""`. Required.

The [`UniqueName`](/References/Entity#UniqueName) of the associated entity.

<br>
<br>

## ComponentType

`enum`

`tree (default) 1`

The presentation type of the parent selector. Only support `tree` for now.

<br>
<br>

## FieldName

`string`

Default: `""`. Required.

The associated field [`Name`](/References/Field#Name) to the current entity.

[Example](#example)

<br>
<br>

## TreeAllItemsLabel

`string`

Default: `""`. Optional.

If not empty, show a button under the tree title. When clicking this button, show all items in the list. Support [variable](/References/UI/Variables).

[Example](#example)

<br>
<br>

## TreeAllItemsIcon

`string`

Default: `""`. Optional.

The icon name beside [`TreeAllItemsLabel`](#TreeAllItemsLabel).

<details>
<summary id="example">Example</summary>

Below is part of the [Articles](https://dash11.comm100.io/ui/10100000/kb/knowledgebases/articles/) page.

Configurations of the parent selector are:
- `entityUniqueName`: `article`
- `componentType`: `tree`
- `fieldName`: `category`
- `treeAllItemsLabel`: `All Categories`
- `treeAllItemsIcon`: `categories`

![TreeAllItems.png](/.attachments/TreeAllItems-5e0beb0b-6575-4609-9b10-9f8b939ac90f.png)

Configurations of the tree are:
- `entityUniqueName`: `category`
- `isAllowNew`: `true`
- `isAllowEdit`: `true`
- `isAllowDelete`: `true`
- `isAllowReorder`: `true`

![Tree.png](/.attachments/Tree-b96c029b-ab7c-48c5-b9f8-f2007a507164.png)
</details>