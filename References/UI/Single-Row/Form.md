Describes form's information, one entity includes multiple forms, eg: the new/edit page with different UI. Below is [new agent](https://dash11.comm100.io/ui/10100000/global/people/agents/new) page.

![f-full.png](/.attachments/f-full-44f85333-7b58-4329-9f0d-f7acce7c4716.png)

## Fields
- [EntityUniqueName](#EntityUniqueName)
- [Name](#Name)
- [Title](#title)
- [Description](#Description)
- [DescriptionPosition](#DescriptionPosition)
- [SizeForDisplayInDrawer](#SizeForDisplayInDrawer)

## Combined Components
- [Components](/References/UI/Single-Row/Form/Component)
- [Buttons](/References/UI/Single-Row/Form/Button)

<br/>

## EntityUniqueName
`string`

Required.

The unique name of the [Entity](/References/Entity) needs a form to modify some fields.

<br/>

## Name
`string`

Required. Unique in forms of the entity.

Fetch the form's configurations by `Name`. 
eg: `NewFormName` and `EditFormName` of [Single-Row](/References/UI/Single-Row)

<br/>

## Title
`string`

Default: `""`

Support [variable](/References/UI/Variables).

The form show on the drawer:
- Set the title of the drawer to edit the bound entity. If it is empty, the title is not displayed.
- When creating or editing entity in the drawer, such as the scoping entity.
  - If it is empty, the default value when creating a new entity is "New {[Entity](/References/Entity#label).label}"
  - If it is empty, the default value when editing the entity is "Edit {[Entity](/References/Entity#label).label}"

The form show on the Page:
The current entity is the one-to-one relationship with the scoping entity, or it is Single-Record, the title use the configuration of [page](/References/UI/Page#title). other as following:
- If it is empty, the default value when creating a new entity is "New {[Entity](/References/Entity#label).label}"
- If it is empty, the default value when editing the entity is "Edit {[Entity](/References/Entity#label).label}"

<details>
<summary>Example</summary>

The below screenshot is a part of livechat's [pre-chat](https://dash11.comm100.io/ui/10100000/livechat/campaign/prechat/) page.

The configurations as following:
- entity
  - singleRowUI
    - forms
      - `title` is `Pre-chat`

![formtitle.png](/.attachments/formtitle-3eb8bace-0b3e-468b-b87e-8a26a3fc9e87.png)

</details>

<br/>
<br/>

## Description
`string`

Default: `""`

Html supported. like the `title`, it will be configured on the drawer or page. If the value is empty, the description is not displayed. Support [variable](/References/UI/Variables).

<details>
<summary>Example</summary>

The below screenshot is a part of [new department](https://dash11.comm100.io/ui/10100000/global/people/departments/new) page.

The configurations:
- page
  - `description` is `A department ...`
- form
  - `description` is `""`
  
![new-d.png](/.attachments/new-d-a2ecbeab-6d2c-4df4-a376-84b17d1df71c.png)
</details>
<br/>

[Example](#descriptionBelow)

<br/>

## DescriptionPosition
`enum`

[`tooltip(default) 0`](#tooltip) [`belowTitle 1`](#belowTitle)

### tooltip
`value`: `0`
Show [`Description`](#Description) in tooltip. the marked place in the right of [`Title`](#title).

<details>
<summary>Example for tooltip enum</summary>

The below screenshot is a part of ticket's [Operating Hours & Holidays](https://dash11.comm100.io/ui/10100000/ticketing/settings/workingtimeholidays/workinghoursconfig/) page, hover on the question mark.

The configurations as following:
- entity
  - singleRowUI
    - forms
      - `description` is `Defined operating days ...`
      - `descriptionPosition` is `tooltip`

![form-description.png](/.attachments/form-description-99650380-72bf-43b9-823a-023cb72b9c37.png)

</details>

### belowTitle
`value`: `1`
Show [`Description`](#Description) below [`Title`](#title).

<details>
<summary id="descriptionBelow">Example for belowTitle enum</summary>

The below screenshot is a part of livechat's [auto translation](https://dash11.comm100.io/ui/10100000/livechat/settings/autotranslation/) page.

The configurations as following:
- entity
  - singleRowUI
    - forms
      - `description` is `Automatically translate ...`
      - `descriptionPosition` is `belowTitle`

![form-below.png](/.attachments/form-below-d5f29028-af1b-41b4-b68c-4abcd3ac59ae.png)

</details>

<br/>
<br/>

## SizeForDisplayInDrawer
`enum`

[`small(default) 0`](#small) [`large 1`](#large)

If the form used in the drawer, it determines the size of the drawer. such as [`DrawerLink`](/References/UI/Single-Row/Form/Component#drawerLink).

### small
`value`: `0`
<details>
<summary>Example for small enum</summary>

The below screenshot is a part of livechat's [Pre-chat](https://dash11.comm100.io/ui/10100000/livechat/campaign/prechat/) page, click the edit icon in the form table.

The configurations as following:
- entity
  - singleRowUI
    - forms
      - `sizeForDisplayInDrawer` is `small`

![size-small.png](/.attachments/size-small-1b00b765-c61f-4cec-881c-74f434818627.png)

</details>

### large
`value`: `1`
<details>
<summary>Example for large enum</summary>

The below screenshot is a part of livechat's [chat button](https://dash11.comm100.io/ui/10100000/livechat/campaign/chatbutton/) page, switch to image in the type section, then click select image link in desktop section.

The configurations as following:
- entity
  - singleRowUI
    - forms
      - chatButtonFromGalleryImage
        - `sizeForDisplayInDrawer` is `large`

![size-large.png](/.attachments/size-large-9f34b237-34fc-41f8-9f3c-de53271c6c2a.png)

</details>


