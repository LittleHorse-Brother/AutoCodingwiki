Describe a tree. Includes general operation configuration of the tree, like add, edit, delete, reorder. Below is the [Category Tree](https://dash11.comm100.io/ui/10100000/kb/knowledgebases/articles/).
![Tree.png](/.attachments/Tree-33bdf650-e8cd-4a2f-ba91-98ad7655eb8b.png)

## Fields
- [EntityUniqueName](#EntityUniqueName)
- [IsAllowNew](#IsAllowNew)
- [IsAllowEdit](#IsAllowEdit)
- [IsAllowDelete](#IsAllowDelete)
- [IsAllowReorder](#IsAllowReorder)

<br>
<br>

## EntityUniqueName

`string`

Default: `""`. Required.

The [`UniqueName`](/References/Entity#UniqueName) of the associated entity.

<br>
<br>

## IsAllowNew

`bool`

Default: `false`.

- If true, the user can add a tree item as a child to another tree item.
- If false, the user can not add a tree item.

[Example](/References/UI/Multi%2DRow/ParentSelector#example)

<br>
<br>

## IsAllowEdit

`bool`

Default: `false`.

The root item can not edit.

- If true, the user can edit a tree item. Include changing its name and parent tree item.
- If false, the user can not edit any tree item.

[Example](/References/UI/Multi%2DRow/ParentSelector#example)

<br>
<br>

## IsAllowDelete

`bool`

Default: `false`.

The root item can not delete.

- If true, the user can delete a tree item. The children of the tree item will delete also.
- If false, the user can not delete any tree item.

[Example](/References/UI/Multi%2DRow/ParentSelector#example)

<br>
<br>

## IsAllowReorder

`bool`

Default: `false`.

The root item can not reorder. Only available for the entity with the `order` field.

- If true, the user can change the order of a tree item by dragging it. Include becoming a child or a sibling of another tree item (except the children of its own).
- If false, the user can not change the order of any tree item.

[Example](/References/UI/Multi%2DRow/ParentSelector#example)