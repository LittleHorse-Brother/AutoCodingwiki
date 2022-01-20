Describes tab object, Includes some general info of tab, such as [`Title`](#title), [`Path`](#path) etc. The tab is selected when [`Path`](#path) is matched. Below is [ban list](https://dash11.comm100.io/ui/10100000/livechat/settings/banlist/bannedvisitor/) page.

![banlist.png](/.attachments/banlist-1afe4852-3908-4129-ac90-85a349a3dbe0.png)

## Fields
- [EntityUniqueName](#EntityUniqueName)
- [Title](#Title)
- [Description](#Description)
- [Path](#Path)
- [Order](#Order)
- [ConditionForShowing](#ConditionForShowing)

<details>
<summary>Example</summary>

Below is part of the [Ban List](https://dash11.comm100.io/ui/10100000/livechat/settings/banlist/bannedvisitor/) page. Ready for `entity` for each tab, config difference [`path`](#path) of tab.

The configurations are:
- Page
  - `title` is `Ban List`
  - `type` is `pageWithTabs`
  - `path` is `/livechat/settings/banlist/bannedvisitor/`
  - Banned Visitors tab
    - `title` is `Banned Visitors`
    - `entityUniqueName` is `bannedVisitor`
    - `path` is `/livechat/settings/banlist/bannedvisitor/`
    - `order` is 0
  - Banned IPs tab
    - `title` is `Banned IPs`
    - `entityUniqueName` is `bannedIp`
    - `path` is `/livechat/settings/banlist/bannedip/`
    - `order` is 1

![banlist.png](/.attachments/banlist-1afe4852-3908-4129-ac90-85a349a3dbe0.png)

</details>

<br /><br />

## EntityUniqueName
`string`

Required.

<br /><br />

## Title
`string`

Required.

Display text in tab. Support [variable](/References/UI/Variables).

<br /><br />

## Description
`string`

Optional.

Use for the introduction of the current tab. Support [variable](/References/UI/Variables).

<br /><br />

## Path

`string`

Required. Globally Unique.

Tab is selected when path is matched.
- [Page](/References/UI/Page)'s [`PageType`](/References/UI/Page#pageType) is `pageWithTabs`, check the path in tabs of [Page](/References/UI/Page)

View [detail](/References/UI/Page#path)

<br /><br />

## Order

`int`

Required.

Order of the tab. From left to right.

<br /><br />

## ConditionForShowing

`string`

Optional.

Show current tab when condition result is true, support [variable](/References/UI/Variables).