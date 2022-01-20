Describes EditorFeature object, the Feature is a tool of HtmlEditor/CodeEditor.

## Fields
- [Type](#Type)
- [IconName](#IconName)
- [Tooltip](#Tooltip)
- [RestoreDefaultConfirmMessage](#RestoreDefaultConfirmMessage)
- [ComponentId](#ComponentId)
- [CustomButtonActionId](#CustomButtonActionId)
- [Order](#Order)

<br/>

The configuration here is for **HtmlEditor** and **CodeEditor**. Some configuration items do not support both of them, so describe separately as follows:
1. [HtmlEditor](#htmleditor)
2. [CodeEditor](#codeeditor)

<br/>


<a id="htmleditor"></a>
## 1. HtmlEditor
Used to enter rich-text.

<details>
<summary>Example for Html Editor</summary>

Below screenshot is part of [new article](https://dash11.comm100.io/ui/10100000/kb/knowledgebases/articles/new) page. Html editor doesn't support `restoreDefault` and `copyAll`.

The configurations:
- editorFeatures
  - fontSize tool
    - `type` is `fontSize`
  - italic tool
    - `type` is `italic`
  - link tool
    - `type` is `link`
  - textHighlightColor tool
    - `type` is `textHighlightColor`
  - bold tool
    - `type` is `bold`
  - underline tool
    - `type` is `underline`
  - bulletList tool
    - `type` is `bulletList`
  - numberedList tool
    - `type` is `numberedList`
  - increaseIndent tool
    - `type` is `increaseIndent`
  - decreaseIndent tool
    - `type` is `decreaseIndent`
  - strikethrough tool
    - `type` is `strikethrough`
  - alignLeft tool
    - `type` is `alignLeft`
  - alignCenter tool
    - `type` is `alignCenter`
  - alignRight tool
    - `type` is `alignRight`
  - insertTable tool
    - `type` is `insertTable`
  - viewSourceCode tool
    - `type` is `viewSourceCode`
  - fullscreen tool
    - `type` is `fullscreen`
  - customButton tool
    - `type` is `customButton`
    - `tooltip` is `Insert Image`
    - `icon` is `insertImage`
    - customButtonAction
      - `name` is `insertKBImage`
      - `targetEntityName` is `image`
      - `type` is `custom`
   - `type` is `justify`
   - `fontColor` is `fontColor`

![f-c-html editor.png](/.attachments/f-c-html%20editor-8b38ab47-8f92-4929-95c1-0db61fa229e5.png)

</details>

<br/>

### Type
The `Type` here refers to the features supported by HtmlEditor. It will be displayed in the editor's toolbar.

`enum`

`bold 0` `italic 1` `link 2` `fontFamily 3` `fontSize 4` `fontColor 5` `textHighlightColor 6` `underline 7` `bulletList 8` `numberedList 9` `seperator 10` `alignLeft 11` `alignCenter 12` `alignRight 13` `undo 14` `redo 15` `increaseIndent 16` `decreaseIndent 17` `strikethrough 18` `insertTable 19` `fullscreen 20` `viewSourceCode 23` [`customButton 24`](#customButton) `justify 26`

### customButton
`value`: `24`
It provides the ability to custom function for the editor. 

<br/>

## IconName
`string`

Optional. Available for [`customButton`](#customButton)

The name of [SVG](/References/UI/Icon).

<br/>

## Tooltip
`string`

Optional. Available for  [`customButton`](#customButton)

Display in the tooltip when hovering on the icon. Support [variable](/References/UI/Variables).

![tooltip.png](/.attachments/tooltip-e9b064d4-a89c-4613-9564-9751f04920fe.png)

<br/>

## ComponentId
`string`

Required.

The Id of the component which needs to add tool.

<br/>

## CustomButtonActionId
`string`

Optional.

The Id of [Custom Button Action](/References/UI/Button-Action). If there is a value, the `type` must be `customButton`.

<br/>

## Order
`int`

Required.

Determines the display order of features in the toolbar, ascending from left to right.

<br/>

<a id="codeeditor"></a>
## 2. CodeEditor
It is used to edit code. It supports multiple languages. Click [here](/References/UI/Single-Row/Form/Component#codeeditorsyntaxlanguage) to configure the languages it supports.

Example for [Code Editor](/References/UI/Single-Row/Form/Component#codeEditor)

## Type
The `Type` here refers to the features supported by CodeEditor. It will be displayed in the editor's toolbar.

`enum`

[`copyAll 21`](#copyAll) [`restoreDefault 22`](#restoreDefault) [`customButton 24`](#customButton)

### copyAll
`value`: `21`
It isn't shown in the toolbar. If it configured, it appears when the mouse hover on the editor.

<details>
<summary>Example for copyAll</summary>

Below the screenshot is part of livechat's [installation](https://dash11.comm100.io/ui/10100000/livechat/campaign/installation/) page.

The configurations:
- component
  - `componentType` is `codeEditor`
  - `columnSpan` is `12`
  - editorFeatures
    - copyAll tool
      - `type` is `copyAll`

![f-c-copyall.png](/.attachments/f-c-copyall-87816bf0-5db1-487d-9645-6b19dc59d324.png)

</details>

### restoreDefault
`value`: `22`
Click it to return to the default value。

[Example](/References/UI/Single-Row/Form/Component#codeEditor)

### customButton
`value`: `24`
It provides the ability to custom function for the editor. 

<br/>

## IconName
`string`

Optional. Available for [`restoreDefault`](#restoreDefault) and [`customButton`](#customButton)

The name of [SVG](/References/UI/Icon).

<br/>

## Tooltip
`string`

Optional. Available for [`restoreDefault`](#restoreDefault) and [`customButton`](#customButton)

Display in the tooltip when hovering on the icon. Support [variable](/References/UI/Variables).

![tooltip.png](/.attachments/tooltip-e9b064d4-a89c-4613-9564-9751f04920fe.png)

<br/>

## RestoreDefaultConfirmMessage
`string`

Optional. Available for [`restoreDefault`](#restoreDefault)

The confirm message when click `restore default` button on the above of [Code Editor](/References/UI/Single-Row/Form/Component#codeEditor). Support [variable](/References/UI/Variables).

![restoredefault.png](/.attachments/restoredefault-5865bac3-95e7-499b-8e8f-36dd54f1ce24.png)

<br/>

## ComponentId
`string`

Required.

The Id of the component which needs to add tool.

<br/>

## CustomButtonActionId
`string`

Optional.

The Id of [Custom Button Action](/References/UI/Button-Action). If there is a value, the `type` must be `customButton`.

<br/>

## Order
`int`

Required.

Determines the display order of features in the toolbar, ascending from left to right.