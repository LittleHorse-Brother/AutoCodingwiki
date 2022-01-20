Describe the children's menus of level2Menu. eg: [History](https://dash11.comm100.io/ui/10100000/livechat/history/chats/) menu

![submenu.png](/.attachments/submenu-9c829f31-5919-44b3-af31-adf5a485ff7b.png)

## Fields
- [Level2MenuId](#Level2MenuId)
- [Label](#label)
- [Path](#Path)
- [ConditionForShowing](#conditionForShowing)
- [Order](#Order)
- [IsOpenPageInNewTab](#isOpenPageInNewTab)

<details>
<summary>Example</summary>

Below screenshot is a part of livechat's [menu](https://dash11.comm100.io/ui/10100000/livechat/settings/autodistribution/).

The configurations as following:
- leve2menu
  - `label` is `History`
  - `path` is `''`
  - `type` is `static`
  - level2SubMenus
    - Chats menu
      - `label` is  `Chats`
      - `path` is  `/livechat/history/chats/`
    - Messages menu
      - `label` is  `Messages`
      - `path` is  `/livechat/history/messages/`
    - Missed & Refused menu
      - `label` is  `Missed & Refused`
      - `path` is  `/livechat/history/missedandrefusedchats/`
    - Agent Chats menu
      - `label` is  `Agent Chats`
      - `path` is  `/livechat/history/agentchats/`

![submenu.png](/.attachments/submenu-9c829f31-5919-44b3-af31-adf5a485ff7b.png)
</details>

<br />
<br />

## Label
`string`

Required.

Display text. Support [variable](/References/UI/Variables).

<br />

## Path
`string`

Required.

The format is '/{[application](/References/UI/Menu/Level-1-Menu#application)}/{level2MenuName}/{level2SubmenuName}', it is selected when `level2SubmenuName` is matched.
- The [`Path`](/References/UI/Menu/Level-2-Menu#path) of [`level2Menu`](/References/UI/Menu/Level-2-Menu) is empty, `level2MenuName` equal [`Name`](/References/UI/Menu/Level-2-Menu#name) of [`level2Menu`](/References/UI/Menu/Level-2-Menu).

<br />


## Level2MenuId
`string`

Required.

The Id of the Leve2Menu

<br />

## ConditionForShowing
`string`

Config the condition to control whether the menu is visible. eg: `@site.product.livechat == true`

<br/>

## Order
`int`

Required.

It is ascending.

<br/>

##IsOpenPageInNewTab
`bool` default value is false.

If it is configured to `true`, open the page in the new tab when clicking the menu.
