Describes a Single-Row object. If the [entity](/References/Entity) need to be modified from UI, [Page](/References/UI/Page) has to config Single-Row. For new entity page, config a [form](/References/UI/Single-Row/Form) and put form's name to [`NewFormName`](#NewFormName), if the UI is the same between new and edit page, config the same form's name to [`NewFormName`](#NewFormName) and [`EditFormName`](#EditFormName). Below is the ['New Banned Visitor'](https://dash11.comm100.io/ui/10100000/livechat/settings/banlist/bannedvisitor/new) page.

![banlist.png](/.attachments/banlist-240c560d-403f-4324-91db-c25372e46c3d.png)

## Fields
- [EntityUniqueName](#EntityUniqueName)
- [IsShowEnableSwitch](#IsShowEnableSwitch)
- [EnableSwitchConfigEntityName](#EnableSwitchConfigEntityName)
- [EnableSwitchConfigEntityFieldName](#EnableSwitchConfigEntityFieldName)
- [EditFormName](#EditFormName)
- [NewFormName](#NewFormName)
- [CustomComponentNameBesideTitle](#CustomComponentNameBesideTitle) `v0.5.x`
- [CustomComponentNameBelowTitle](#CustomComponentNameBelowTitle-v0.5.x) `v0.5.x`

<br/>

## EntityUniqueName
`string`

Required.

The unique name of the [Entity](/References/Entity) which is going to modified.

<br />

## IsShowEnableSwitch
`bool`

Default: `false`

If true, show a switch beside of page's title.

![feature switch.png](/.attachments/feature%20switch-d818fc43-fe1a-4c0a-bba2-36aa4d7fa4b1.png)

[Example](#featureswitch)

<br />

## EnableSwitchConfigEntityName
`string`

Optional. Available for [`IsShowEnableSwitch`](#IsShowEnableSwitch) is `true`

The unique name of entity, the entity's [`IsMultiRecord`](/References/Entity#IsMultiRecord) is `no`.

[Example](#featureswitch)

<br />

## EnableSwitchConfigEntityFieldName
`string`

Optional. Available for [`IsShowEnableSwitch`](#IsShowEnableSwitch) is `true`

The name of the field of [`EnableSwitchConfigEntityName`](#EnableSwitchConfigEntityName) which need to be modified.

<details id="featureswitch">
<summary>Example for enable switch </summary>

Below screenshot is a part of livechat's [prechat](https://dash11.comm100.io/ui/10100000/livechat/campaign/prechat/) page.

The configurations as following:
- entity
  - `singleRowUI`
    - `isShowEnableSwitch` is `true`
    - `enableSwitchConfigEntityName` is `campaignPreChat`
    - `enableSwitchConfigEntityFieldName` is `isEnabled`

![feature switch.png](/.attachments/feature%20switch-d818fc43-fe1a-4c0a-bba2-36aa4d7fa4b1.png)
</details>

<br />
<br />

## EditFormName
`string`

Default: `""`

Name of the corresponding [Form](/References/UI/Single-Row/Form#name). 

<br />

## NewFormName
`string`

Default: `""`

Name of the corresponding [Form](/References/UI/Single-Row/Form#name). If an entity’s new form is the same as the edit form, you can set [`EditFormName`](#EditFormName) and [`NewFormName`](#NewFormName) to the same.

<br/>

## CustomComponentNameBesideTitle

`string`
`version`: `v0.5.x`

Default: `""`. Optional.
The custom component name which displays beside the list.

<br/>

## CustomComponentNameBelowTitle`v0.5x`
`string`
`version`: `v0.5.x`

Default: `""`. Optional.
The custom component name which displays below the list.