Each field option group represents an select field that can be either a bool (true, false) or an enumeration such as knowledge base status (open, closed).

In general, there will be multiple Field Option per field option group.

Field option group will be referenced by Field.

# [N] Field Option

Indicate a specific option corresponding to the `t_AutoCoding_FieldOption` table in auto coding database.

## Name

`string`

Required.

Case sensitive. When type is bool, name will be “true” or “false”. This field is used in HTTP APIs. Value and Label are not used in HTTP APIs except they appear in HTTP Get API of the entity definition.

For example: The status of the article returns `draft` and `published` in the api response.

![image.png](/.attachments/image-ae5d10b7-7d0a-40d4-a78c-589d142159ad.png)

## Value

`int` 

Required.

Value is used on database storage. Of course, if you need to define enumerations in the custom code, you need to correspond to this value.

For example: The status of the article needs to be store `0(draft)` and `1(published)` in database.

![image.png](/.attachments/image-ef3ffb33-4ad5-44db-ad7e-1e07db9bf04e.png)

 ## Label

`string`

Default: `""`

The label is usually used in UI presentation. Support [variable](/References/UI/Variables).

For example: The status of article needs to be displayed as `Draft` and `Published` on the UI.

![image.png](/.attachments/image-ae235dd3-a9ec-42a7-bbdd-7c6f2cf24900.png)

## HelperText

`string`

Default: `""`

Then the front-end is displayed as Radio. The helperText is displated after the option with a question mark icon. Support [variable](/References/UI/Variables).

Example:

![image.png](/.attachments/image-d89c979f-0dab-4fd6-9e19-29b17fdecfba.png)

## Icon

`string`

Default: `""`

Name of the Icon. The icon will eventually be displayed in a dropdown list or table.

For example: 

![image.png](/.attachments/image-69219ea6-3d53-4917-a320-86dc85ed58af.png)