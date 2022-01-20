Describe an icon. Include general info of an icon, such as `name` `svg`, etc.

## Fields
- [Name](#Name)
- [Svg](#Svg)
- [IconStyle](#IconStyle)

<br>

## Name

`string`

Default: `""`. Unique.

Icon name.

[Example](#example)

<br>

## Svg

`string`

Default: `""`. Required.

SVG content.

<details>
<summary id="example">Example</summary>

Below is a svg icon.

Configurations of the icon are:
- `name`: `svg`
- `svg`: `<svg viewBox="0 0 24 24"><circle cx="12" cy="12" r="8"></circle></svg>`

</details>

<br/>

## IconStyle
`string`

The default value is `common`, it is used to filter the icon list. eg:
- `/api/entities/icons` or `/api/entities/icons?iconStyle=common` get all icons whose `IconStyle` equals to `common`.
- `/api/entities/icons?iconStyle=amy` get all icons whose `iconStyle` equals to `amy`.