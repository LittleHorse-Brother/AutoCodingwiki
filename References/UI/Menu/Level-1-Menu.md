Describe the modules of the product. When the selected level1Menu has no `level2Menu`, the `icon` and corresponding label will be displayed. When the selected menu has level2Menu, only the icon will be displayed, hover on the icon the `label` will be displayed in the tooltip.

![livechat.png](/.attachments/livechat-880bc2c2-2802-459b-8f22-64c30834e9b3.png)

## Fields
- [Label](#Label)
- [Icon](#Icon)
- [Path](#Path)
- [Application](#Application)
- [Order](#Order)
- [ConditionForShowing](#ConditionForShowing)
- [ScopingEntityUniqueName](#ScopingEntityUniqueName)
- [Position](#position)
- [CustomLevel1MenuName](#ScopingEntityUniqueName)
- [MenuStyle](#menuStyle)
- [IsOpenPageInNewTab](#isOpenPageInNewTab)

<details>
<summary>Example</summary>

Below is the [Dashboard](https://dash11.comm100.io/ui/10100000/livechat/dashboard/) menu.

The configrations as following:
- Level1Menu
  - `label` is `Live Chat`
  - `icon` is `lc`
  - `path` is `/livechat/dashboard/`
  - `application` is `livechat`

![menu-level1.png](/.attachments/menu-level1-f72ed799-c425-48a3-8dd4-af594ba6f8c0.png)

</details>

<br/>
<br />

## Label
`string`

Required.

Display `Label` in three positions. Support [variable](/References/UI/Variables).
- Display it in tooltip when hover on [`Icon`](#icon) when it has submenus.
- Display it as label in the right of the [`Icon`](#icon) when it no submenus.
- Display it on the top of [Level2Menu](/References/UI/Menu/Level-2-Menu).

![level1m.png](/.attachments/level1m-8db7aa19-1a1e-47fa-b4cd-fdac8a339fc1.png)

<br />

## Icon
`string`

Required.

The unique name of [Icon](/References/UI/Icon).

<br />

## Path
`string`

Required. 

`Path` is the url of default page of `module` or `product`, view [detail](/References/UI/Page#path). 

<br />

## Application
`string`

Required.

Hide this menu when the application is not enabled. Also known as `module` or `product`.
Menu selected cases:
- Match according to the value of [`Application`](#application). If multiple `Level1Menu` are found, select the corresponding `LevelMenu` according to the path.
- Match according to the value of [`Application`](#application), if only one `Level1Menu` is found, select the matching `Level1menu`.
- Match according to the value of [`Application`](#application), if `Level1Menu` is not found, there is no selected `Level1Menu` in the menu.

<br />

## Order
`int`

Required.

The order of the menu list. Display in ascending order.

## ConditionForShowing
`string`

Config the condition to control whether the menu is visible. eg: `@site.product.livechat == true`

## ScopingEntityUniqueName
`string`

It is optional. Here is the uniqueName of the scoping entity. When the query parameters do not have a ID of scoping entity, the ID of the first data in the scoring entity list will be taken as the default value.

## Position
`enum`: `top(default)(0)` `bottom(1)`

The default value is `top`. Determines whether the menu is displayed at the top or bottom of level1Menu bar.

## CustomLevel1MenuName
`string`

It is optional. the name of custom menu.

## MenuStyle
`string`

The default value is common, it is used to filter the menu list. eg:
- `/api/entities/menus` or `/api/entities/menus?menuStyle=common` get all menus whose `MenuStyle` equals to `common`.
- `/api/entities/menus?menuStyle=amy` get all menus whose `MenuStyle` equals to `amy`.

##IsOpenPageInNewTab
`bool` default value is false.

It only supports the menu with no submenus. If it configured to `true`, open the page in the new tab when clicking the menu.
