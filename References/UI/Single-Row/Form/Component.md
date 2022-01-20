[Form](/References/UI/Single-Row/Form) is made of a component. Use layout components to group others, such as [`groupBegin`](#groupBegin), [`groupEnd`](#groupEnd), The layout components are configured in pair. Below is ['chat button'](https://dash11.comm100.io/ui/10100000/livechat/campaign/chatbutton/) page.

![chat button.png](/.attachments/chat%20button-6c758ffe-3bea-4a8e-8659-a28c8cd6e992.png)

## Fields
- [ComponentType](#ComponentType)
- [Label](#Label)
- [LabelDisplayStyle](#LabelDisplayStyle)
- [MessageForRequiredFieldNotFilled](#MessageForRequiredFieldNotFilled)
- [MessageForInvalidFormat](#MessageForInvalidFormat)
- [CustomComponentName](#CustomComponentName)
- [FieldNameForCopyValueWhenChangedFirstTime](#FieldNameForCopyValueWhenChangedFirstTime)
- [Order](#Order)
- [EditorHeight](#EditorHeight)
- [FieldOrEntityName](#FieldOrEntityName)
- [InputComponentPrefix](#InputComponentPrefix)
- [InputComponentSuffix](#InputComponentSuffix)
- [ComponentText](#ComponentText)
- [ButtonActionId](#ButtonActionId)
- [SelectDataSource](#SelectDataSource)
- [FormNameForDrawerLinkOrSubFormLink](#FormNameForDrawerLinkOrSubFormLink)
- [GroupTitle](#GroupTitle)
- [Name](#Name)
- [IsGroupExpandable](#IsGroupExpandable)
- [GroupTitleSize](#GroupTitleSize)
- [SizeForImageRadioGroup](#SizeForImageRadioGroup)
- [IframeUrl](#IframeUrl)
- [IconName](#IconName)
- [IsInline](#IsInline)
- [InlineComponentWidth](#InlineComponentWidth)
- [IsIndent](#IsIndent)
- [ColumnSpan](#ColumnSpan)
- [ConditionForShowing](#ConditionForShowing)
- [HelperText](#HelperText)
- [HelperTextPosition](#HelperTextPosition)
- [ParentFieldName](#ParentFieldName)
- [InvisibleVariableValue](#InvisibleVariableValue)
- [ConditionForDisabled](#ConditionForDisabled)
- [CodeEditorSyntaxLanguage](#CodeEditorSyntaxLanguage)

<br />

## ComponentType
`enum`

[`checkbox 0`](#checkbox) [`chipInput 1`](#chipInput) [`groupBegin 2`](#groupBegin) [`groupEnd 3`](#groupEnd) [`input 4`](#input) [`htmlEditor 6`](#htmlEditor) [`codeEditor 7`](#codeEditor) [`radioGroup 8`](#radioGroup) [`select 9`](#select) [`selectTree 10`](#selectTree) [`textarea 11`](#textarea) [`text 12`](#text) [`imageRadioGroup 13`](#imageRadioGroup) [`segmentGroup 14`](#segmentGroup) [`newLine 19`](#newLine) [`placeHolder 20`](#placeHolder) [`password 22`](#password) [`passwordWithRetype 23`](#passwordWithRetype) [`avatarInput 24`](#avatarInput) [`transferList 25`](#transferList) [`drawerLink 26`](#drawerLink) [`table 29`](#table) [`multiSelect 30`](#multiSelect) [`numberInput 31`](#numberInput) [`datePicker 33`](#datePicker) [`iframe 34`](#iframe) [`colorPicker 35`](#colorPicker) [`fileInput 36`](#fileInput) [`galleryImagePicker 37`](#galleryImagePicker) [`ruleConditionEditor 39`](#ruleConditionEditor) [`customComponent 40`](#customComponent) [`button 41`](#button) [`linkButton 42`](#linkButton) [`icon 43`](#icon) [`switch 44`](#switch) [`invisibleVariable 45`](#invisibleVariable) [`timeRangePicker 46`](#timeRangePicker) [`subGroupTitleText 47`](#subGroupTitleText) [`dateTimePicker 48(v0.5.x)`](#dateTimePicker)

### checkbox
`value`: `0`
The `Type` Of the [Field](/References/Field) only supports `bool`.

![f-c-checkbox.png](/.attachments/f-c-checkbox-03b5003b-f1df-4b70-b7a9-6234a5a1e744.png)

<details>
<summary>Example for checkbox</summary>

Below the screenshot is a part of kb's [new article](https://dash11.comm100.io/ui/10100000/kb/knowledgebases/articles/new) page. create a bool field with the name 'isFeatured', add two options for it, the checkbox will take the helperText/label of the option as the label which value is 'true'.

The configurations:
- isFeatured field
  - `name` is `isFeatured`
  - `default` is `''`
  - `type` is `bool`
  - `label` is `''`
  - field options
    - true option
      - `helperText` is `Mark this article as Featured to make it appear above the Non-Featured articles`
      - `key` is `true`
      - `icon` is `star`
      - `label` is `''`
    - false option
      - `key` is `false`
      - `icon` is `blank`
      - `label` is ``

- component
  - `componentType` is `checkbox`
  - `isInline` is `false`
  - `isIndent` is `false`
  - `columnSpan` is `12`
  - `fieldOrEntityName` is `isFeatured`

![f-c-checkbox.png](/.attachments/f-c-checkbox-03b5003b-f1df-4b70-b7a9-6234a5a1e744.png)

</details>

### chipInput
`value`: `1`
Supports [Field](/References/Field)'s type is `reference`, the relationship is `oneToMany` or `manyToMany`, it doesn't support data source, but it supports filter the list base on the scoping value.

![f-c-chip.png](/.attachments/f-c-chip-427e497a-a73d-4f6f-b904-24444745959b.png)

<details>
<summary>Example for chipInput</summary>

Below the screenshot is a part of kb's [edit article](https://dash11.comm100.io/ui/10100000/kb/knowledgebases/articles/edit) page. The tag entity must be in the boundary of the article, the relationship between tag and article is many-to-many.

The configurations:
- entitiesInBoundary
  - `entityName` is `tag`
  - `primaryEntityUniqueName` is `article`
- component
  - `componentType` is `chipInput`
  - `isInline` is `false`
  - `isIndent` is `false`
  - `columnSpan` is `12`
  - `fieldOrEntityName` is `tags`

![f-c-chip.png](/.attachments/f-c-chip-427e497a-a73d-4f6f-b904-24444745959b.png)

</details>

### groupBegin
`value`: `2`
It is layout component, places in the front of group, supports properties are [`GroupTitle`](#GroupTitle), [`GroupTitleSize`](#GroupTitleSize) and [`IsGroupExpandable`](#IsGroupExpandable).

[Example](#GroupTitleSize)

### groupEnd
`value`: `3`
It is a layout component, places at the end of the group, it just an end mark for the group.

[Example](#GroupTitleSize)

### input
`value`: `4`
The `Type` Of the [Field](/References/Field) supports `string` and `email`. Following configurations only configure one for each component:
- Configure [`InputComponentPrefix`](#InputComponentPrefix), then display readonly text before input area.
- Configure [`InputComponentSuffix`](#InputComponentSuffix), then display readonly text after input area.
- Configure [editor feature](/References/UI/Single-Row/Form/Component/EditorFeature), it only supports `customButton` feature with `insertVariable`.

![re-input.png](/.attachments/re-input-54924cb4-6d83-4c52-ab0d-bde0c2ffa55b.png)

<details>
<summary>Example</summary>

Below the screenshot is a part of [new agent](https://dash11.comm100.io/ui/10100000/global/people/agents/new) page. At first, create a [form](/References/UI/Single-Row/Form), then adding a component with input type to it. 

The configurations of input component:
- component
  - `componentType` is `input`
  - `isInline` is `false`
  - `isIndent` is `false`
  - `columnSpan` is `6`
  - `fieldOrEntityName` is `email`

![re-input.png](/.attachments/re-input-54924cb4-6d83-4c52-ab0d-bde0c2ffa55b.png)

</details>

<details>
<summary>Example for inputComponentPrefix</summary>

Below screenshot is a part of kb's [new article](https://dash11.comm100.io/ui/10100000/kb/knowledgebases/articles/new) page. The example is a custom component which inherit input,

The configurations of input component:
- component
  - `componentType` is `customComponent`
  - `customComponentName` is `CKBUrlInput`
  - `isInline` is `false`
  - `isIndent` is `false`
  - `columnSpan` is `6`
  - `fieldOrEntityName` is `email`
  - `inputComponentPrefix` is `https://@config.kbFrontEndDomain/kb/@siteId/.../`

![f-c-input-prefix.png](/.attachments/f-c-input-prefix-a062c4e6-c3fa-4f6c-b2e8-d5d5970e304d.png)

</details>

<details>
<summary>Example for editor feature</summary>

Below the screenshot is a part of kb's [chat window](https://dash11.comm100.io/ui/10100000/livechat/campaign/chatwindow/) page. Expands advanced section, selected 'Automatically email chat transcripts for archiving or followup'.

The configurations of input component:
- component
  - `componentType` is `input`
  - `fieldOrEntityName` is `emailSubjectForArchivingTranscripts`
  - editorFeatures
    - `type` is `customButton`
    - `icon` is `insertdynamicinfo`
    - customButtonAction
      - `type` is `insertVariable`

![custom-input.png](/.attachments/custom-input-7b176940-1ced-4a6e-baf2-641ce7ac22f3.png)

</details>

### htmlEditor
`value`: `6`
The `Type` Of the [Field](/References/Field) supports `string` and `encodedHtml`. Configure tool bar via [editor feature](/References/UI/Single-Row/Form/Component/EditorFeature). Its height is controled by [`EditorHeight`](#EditorHeight), the default value is `300px`.

![f-c-html.png](/.attachments/f-c-html-a78d4808-81b8-42b5-9ca8-fb6b44d22fae.png)

<details>
<summary>Example for htmlEditor</summary>

Below the screenshot is part of livechat's [chat window](https://dash11.comm100.io/ui/10100000/livechat/campaign/chatwindow/) page. The editor is a third-party component named [Froala](https://froala.com/wysiwyg-editor/docs/options/). Take the greeting message as an example which places in the advanced section on the current page. it needs to add a string field named 'greetingMessage' and config editor features for it. Editor feature control what tools will show on above of HTML editor. 

The configurations:
- greeting message field
  - `name` is `greetingMessage`
  - `type` is `string`
  - `default` is `''`

- component
  - `componentType` is `htmlEditor`
  - `isInline` is `false`
  - `isIndent` is `true`
  - `columnSpan` is `12`
  - `fieldOrEntityName` is `greetingMessage`
  - editor features
    - bold tool
      - `type` is `bold`
    - italic tool
      - `type` is `italic`
    - link tool
      - `type` is `link`

![f-c-html.png](/.attachments/f-c-html-a78d4808-81b8-42b5-9ca8-fb6b44d22fae.png)

</details>

### codeEditor
`value`: `7`
The `Type` Of the [Field](/References/Field) supports `string` and `encodedHtml`. Configure tool bar via [editor feature](/References/UI/Single-Row/Form/Component/EditorFeature). Its height is controled by [`EditorHeight`](#EditorHeight), the default value is `300px`. Configure [`CodeEditorSyntaxLanguage`](#CodeEditorSyntaxLanguage) to control the supported language of codeEditor.

![f-c-codemirror.png](/.attachments/f-c-codemirror-3e19bd89-d435-4cfe-af41-3112ef8d9e01.png)

<details>
<summary>Example for codeEditor</summary>

Below screenshot is a part of kb's [edit design](https://dash11.comm100.io/ui/10100000/kb/knowledgebases/designs/edit) page. Code editor is a third party component named [code mirror](https://codemirror.net/). Like HtmlEditor, its tooltar via config editor feature, the language of CodeMirror is via config the [CodeEditorSyntaxLanguage](#CodeEditorSyntaxLanguage) of component. the request have to encode HTML mark, so create a field with type encodedHtml.

The configurations:
- body field
  - `name` is `body`
  - `type` is `encodedHtml`
  - `default` is `@designTemplate?pageType=$pageType`
  - `label` is `$pageType`
- component
  - `componentType` is `htmlEditor`
  - `codeEditorSyntaxLanguage` is `css`
  - `isInline` is `false`
  - `isIndent` is `false`
  - `columnSpan` is `12`
  - `fieldOrEntityName` is `body`
  - editor features
    - Restore Default tool
      - `icon` is `restoreDefault`
      - `tooltip` is `Restore Default`
      - `type` is `restoreDefault`
    - Insert Image tool
      - `icon` is `insertImage`
      - `tooltip` is `Insert Image`
      - `type` is `customButton`
      - custom button action
        - `name` is `insertKBImage`
        - `targetEntityName` is `image`
        - `type` is `custom`
    - Insert Category tool
      - `icon` is `insertCategory`
      - `tooltip` is `Insert Category`
      - `type` is `customButton`
      - custom button action
        - `name` is `insertKBCategory`
        - `targetEntityName` is `category`
        - `type` is `custom`
    - Insert Article tool
      - `icon` is `insertArticle`
      - `tooltip` is `Insert Article`
      - `type` is `customButton`
      - custom button action
        - `name` is `insertKBArticle`
        - `targetEntityName` is `article`
        - `type` is `custom`

![f-c-codemirror.png](/.attachments/f-c-codemirror-3e19bd89-d435-4cfe-af41-3112ef8d9e01.png)

</details>

### radioGroup
`value`: `8`
Supports field's type, such as `enum`, `bool`, `guid` and `string`. If the type is `enum`, render a radio for each [field option](/References/Field-Option-Group) below the label. supports the fields of [field option](/References/Field-Option-Group) are `label`, `value` and `helperText`.
![f-c-radiogroup.png](/.attachments/f-c-radiogroup-93a11702-40ce-4fdc-a472-1a4309138e26.png)

<details>
<summary>Example for radioGroup</summary>

Below the screenshot is a part of ticket's [edit blocked sender](https://dash11.comm100.io/ui/10100000/ticketing/settings/blockedsenders/edit?blockedsenderid=a088fd8a-c467-4ebe-8c16-bc27a60dfe09) page. Take Block level as an example, it needs to create a field named 'blockLevel', then add two options as following.

The configurations:
- block level field
  - `name` is `blockLevel`
  - `default` is `ejectAllFutureMessages`
  - `type` is `enum`
  - `label` is `Block Level`
  - field options
    - Mark future messages as junk option
      - `key` is `markFutureMessagesAsJunk`
      - `label` is `Mark future messages as junk`
    - Reject all future messages option
      - `key` is `ejectAllFutureMessages`
      - `label` is `Reject all future messages`
- component
  - `componentType` is `radioGroup`
  - `isInline` is `false`
  - `isIndent` is `true`
  - `columnSpan` is `12`
  - `fieldOrEntityName` is `blockLevel`

![f-c-radiogroup.png](/.attachments/f-c-radiogroup-93a11702-40ce-4fdc-a472-1a4309138e26.png)

</details>

### select
`value`: `9`
The `Type` Of the [Field](/References/Field) supports `enum`, `bool`, `timeZone` and `reference`, the relationship of `reference` is oneToMany. If the type is `timeZone`, fetch all timeZones as the options. Supports [dataSource](/References/UI/Data-Source) also, put dataSource's name to [`SelectDataSource`](#SelectDataSource), [`SelectDataSource`](#SelectDataSource) is array, so it can configure multiple dataSource. It supports filter the options base on the scoping value.

![f-c-select.png](/.attachments/f-c-select-9236ec12-6fb1-4c54-bc07-474e48049e65.png)
<details>
<summary>Example</summary>

Below the screenshot is a part of kb's [new Article](https://dash11.comm100.io/ui/10100000/kb/knowledgebases/articles/new/) page. take article's status as an example, at first it has to config a field named 'status' with data type is an enum and add two options for it.

The configurations of select component:
  - status field
    - `default` is `draft`
    - `label` is `Status`
    - `name` is `status`
    - field options
      - draft option
        - `label` is `Draft`
        - `key` is `draft`
        - `icon` is `reddot`
      - published option
        - `label` is `Published`
        - `key` is `published`
        - `icon` is `dot`

  - component
    - `componentType` is `select`
    - `isInline` is `false`
    - `isIndent` is `false`
    - `columnSpan` is `12`
    - `fieldOrEntityName` is `similarQuestions`
 
![f-c-select.png](/.attachments/f-c-select-9236ec12-6fb1-4c54-bc07-474e48049e65.png)

</details>

### selectTree
`value`: `10`
The `Type` Of the [Field](/References/Field) only supports `reference`, configure [tree](/References/UI/Multi%2DRow/Tree) for reference entity.
![f-c-selectTree.png](/.attachments/f-c-selectTree-a61f51f8-2a42-4c1f-a8b3-8172013db554.png)

<details>
<summary>Example for selectTree</summary>

Below the screenshot is a part of kb's [new Article](https://dash11.comm100.io/ui/10100000/kb/knowledgebases/articles/new/) page. take article's category as an example, config a reference field with relationship one-to-many.

The configurations as following:
- category field
  - `name` is `category`
  - `type` is `reference`
  - `referenceEntityName` is `category`
  - `referenceType` is `oneToMany`
- component
  - `componentType` is `selectTree`
  - `isInline` is `false`
  - `isIndent` is `false`
  - `columnSpan` is `6`
  - `fieldOrEntityName` is `category`

![f-c-selectTree.png](/.attachments/f-c-selectTree-a61f51f8-2a42-4c1f-a8b3-8172013db554.png)

</details>

### textarea
`value`: `11`
The `Type` Of the [Field](/References/Field) supports `string`, `stringArray` and `reference`, the relationship of `reference` is oneToMany or manyToMany. If configure regex to validate the value of the textarea which's type is `stringArray`, use the regex to validate the value of each line.
![textarea.PNG](/.attachments/textarea-6b899795-93bc-4c95-80c9-a9b7c44453ee.PNG)

<details>
<summary>Example for textarea</summary>

Below the screenshot is a part of kb's [new Article](https://dash11.comm100.io/ui/10100000/kb/knowledgebases/articles/new) page. At first, create a [form](/References/UI/Single-Row/Form), then adding a component with `textarea` type to it.  

The configurations of textarea component:
- component
  - `componentType` is `textarea`
  - `isInline` is `false`
  - `isIndent` is `false`
  - `columnSpan` is `12`
  - `fieldOrEntityName` is `similarQuestions`
  - `helperText` is `Adding variations of the same question here can help your Agent Assist better understand and recognize the same question asked in different ways. Make sure that you enter one question per line.`

![textarea.PNG](/.attachments/textarea-6b899795-93bc-4c95-80c9-a9b7c44453ee.PNG)

</details>

### text
`value`: `12`
Config the content of text component with [`componentText`](#componentText).
![re-text.png](/.attachments/re-text-74be7199-cae3-4009-b67d-0da9b6cf3030.png)

<details>
<summary>Example</summary>

Below the screenshot is a part of bot's [general settings](https://dash11.comm100.io/ui/10100000/bot/agentassist/agentassist/) page. At first, create a [form](/References/UI/Single-Row/Form), then adding a component with text type to it.

The configurations of text component:
- component
  - `componentType` is `text`
  - `componentText` is `Display suggestions only when the score is higher than `
  - `isInline` is `true`
  - `isIndent` is `true`

![re-text.png](/.attachments/re-text-74be7199-cae3-4009-b67d-0da9b6cf3030.png)

</details>

### imageRadioGroup
`value`: `13`
The Type Of the Field only supports `enum`, supports the fields of [field option](/References/Field-Option-Group) are `label`, `value`, `icon` and `helperText`. Control the size of `icon` via [`SizeForImageRadioGroup`](#SizeForImageRadioGroup).

![f-c-imagegroup.png](/.attachments/f-c-imagegroup-1d73d946-1b11-4a08-90a5-d6ac04ece5f7.png)

<details>
<summary>Example for imageRadioGroup</summary>

Below the screenshot is a part of livechat's [chat window](https://dash11.comm100.io/ui/10100000/livechat/campaign/chatwindow/) page. Take 'Type' as an example, it need to create a field named 'Type', then add two options as following.

The configurations:
- type field
  - `name` is `Type`
  - `type` is `enum`
  - `label` is `''`
  - field options
    - Embedded option
      - `helperText` is `An embedded chat window opens right on the page where the chat button has been clicked. This will not prevent your visitors from seeing existing website content.`
      - `icon` is `embedded`
      - `key` is `embeddedChatWindow`
      - `label` is `Embedded`
    - Popup option
      - `helperText` is `A pop-up chat window opens in a separate window which means each time a visitor wants to return to the chat they need to switch to that chat window. You can also add the link of such chat windows to your email signature or any other places and people can chat with you directly by clicking on the link.`
      - `icon` is `popup`
      - `key` is `popupChatWindow`
      - `label` is `Popup`

- component
  - `componentType` is `imageRadioGroup`
  - `isInline` is `false`
  - `isIndent` is `false`
  - `columnSpan` is `12`
  - `fieldOrEntityName` is `type`
  - `sizeForImageRadioGroup` is `8.75`

![f-c-imagegroup.png](/.attachments/f-c-imagegroup-1d73d946-1b11-4a08-90a5-d6ac04ece5f7.png)

</details>

### segmentGroup
`value`: `14`
The Type Of the Field only supports `enum`, supports the fields of [field option](/References/Field-Option-Group) are `label`, `value` and `helperText`.

![f-c-segmentGroup.png](/.attachments/f-c-segmentGroup-052346fd-a9e0-45d0-9f35-dd33629e7919.png)

<details>
<summary>Example for segmentGroup</summary>

Below screenshot is a part of ticket's [auto distribution](https://dash11.comm100.io/ui/10100000/ticketing/settings/autodistribution/) page. create a field named 'ifLimitMaxTicketsForAllAgents' and add two options.

The configurations:
- ifLimitMaxTicketsForAllAgents field
  - `name` is `ifLimitMaxTicketsForAllAgents`
  - `default` is `true`
  - `type` is `bool`
  - `label` is `''`
  - field options
    - For all agents option
      - `key` is `true`
      - `label` is `For all agents`
    - For each agent option
      - `key` is `false`
      - `label` is `For each agent`

- component
  - `componentType` is `segmentGroup`
  - `isInline` is `false`
  - `isIndent` is `false`
  - `columnSpan` is `12`
  - `fieldOrEntityName` is `ifLimitMaxTicketsForAllAgents`

![f-c-segmentGroup.png](/.attachments/f-c-segmentGroup-052346fd-a9e0-45d0-9f35-dd33629e7919.png)

</details>

### newLine
`value`: `19`
It is a layout component, the value of `IsInline` is `false`, the value of `ColumnSpan` is `12`. the components after it will render in new line.

For example,
[Input, ColumnSpan 4 ] [NewLine]
[Input, ColumnSpan 6 ] [NewLine]

### placeHolder
`value`: `20`
It is layout component with no content. the width of the component is configured via [`InlineComponentWidth`](#InlineComponentWidth).

![placeholder.png](/.attachments/placeholder-3cc9f44e-4ae2-47d2-a991-ec3267935b74.png)

### password
`value`: `22`
Supports [Field](/References/Field)'s type is `string`.

![f-c-pwd.png](/.attachments/f-c-pwd-f70f28f9-8cfc-4f25-9444-ccd369e16b7f.png)

<details>
<summary>Example for password</summary>

Below the screenshot is a part of [new agent](https://dash11.comm100.io/ui/10100000/global/people/agents/new) page. Create a field named 'Password' with string type.

The configurations:
- password field
  - `name` is `password`
  - `type` is `string`
  - `label` is `Password`
- component
  - `componentType` is `password`
  - `isInline` is `false`
  - `isIndent` is `false`
  - `columnSpan` is `6`
  - `fieldOrEntityName` is `password`

![f-c-pwd.png](/.attachments/f-c-pwd-f70f28f9-8cfc-4f25-9444-ccd369e16b7f.png)

</details>

### passwordWithRetype
`value`: `23`
Supports [Field](/References/Field)'s type is `string`.

![f-c-resetpwd.png](/.attachments/f-c-resetpwd-70e459ca-eb3f-4b9f-a25c-d5721abc5182.png)

<details>
<summary>Example for passwordWithRetype</summary>

Below the screenshot is a part of [agents](https://dash11.comm100.io/ui/10100000/global/people/agents/) page. Click reset password mark

The configurations:
- password field
  - `name` is `password`
  - `type` is `string`
  - `label` is `Password`
- component
  - `componentType` is `passwordWithRetype`
  - `isInline` is `false`
  - `isIndent` is `false`
  - `columnSpan` is `12`
  - `fieldOrEntityName` is `password`

![f-c-resetpwd.png](/.attachments/f-c-resetpwd-70e459ca-eb3f-4b9f-a25c-d5721abc5182.png)

</details>

### avatarInput
`value`: `24`
Supports [Field](/References/Field)'s type is `reference`, the relationship is `oneToOne`. It provides the ability to upload a local image or pick the system image as an avatar, it needs to modify multiple fields, so configures [additional field](/References/UI/Single-Row/Form/Component/AdditionalField).

Related `uiElementType` as following:
- `customImage` it is used when upload image.
- `systemImage` it is the field's name of the reference entity which is the URL of the avatar.
- `avatar` it is the field's name of the current entity which is the URL of the avatar.
- `isCustomImage` it is the field's name of the current entity which judges the avatar is from a local or system.

![f-c-avatarinput.png](/.attachments/f-c-avatarinput-0a45c0c5-be24-4191-a0a4-c7e9ad354202.png)

<details>
<summary id="avatarExample">Example for avatarInput</summary>

Below the screenshot is a part of [new agent](https://dash11.comm100.io/ui/10100000/global/people/agents/new) page. it can pick a system avatar or upload an avatar from local for a new agent, so this component relates to five fields:

1, systemAvatar field is reference, the corresponding entity is systemAvatar, the relationship is one-to-one.
2, customizeAvatar is configured as an additional field, the field is used to upload local avatar when new/edit agent. 
3, avatarImage is configured as an additional field, it is a field of systemAvatar entity.
4, avatar is configured as an additional field, this field is generated by custom code, its value is the path of current agent's avatar.
5, ifCustomizeAvatar is configured as an additional field, check the value of avatar is from the system or custom.

The configurations:
- systemAvatar field
  - `name` is `systemAvatar`
  - `type` is `reference`
  - `referenceEntityName` is `systemAvatar`
  - `referenceType` is `oneToOne`
- component
  - `componentType` is `avatarInput`
  - `isInline` is `false`
  - `isIndent` is `false`
  - `columnSpan` is `6`
  - `fieldOrEntityName` is `systemAvatar`
  - additionalFields
    - ifCustomizeAvatar field
      - `fieldName` is `ifCustomizeAvatar`
      - `uiElementType` is `isCustomImage`
    - customizeAvatar field
      - `fieldName` is `customizeAvatar`
      - `uiElementType` is `customImage`
    - avatarImage field
      - `fieldName` is `avatarImage`
      - `uiElementType` is `systemImage`
    - avatar field
      - `fieldName` is `avatar`
      - `uiElementType` is `avatar`

![f-c-avatarinput.png](/.attachments/f-c-avatarinput-0a45c0c5-be24-4191-a0a4-c7e9ad354202.png)

</details>

### transferList
`value`: `25`
Supports [Field](/References/Field)'s type is `reference`, the relationship is `oneToMany` or `manyToMany`. Configure [additional field](/References/UI/Single-Row/Form/Component/AdditionalField) to support display, it supports filter the list base on the scoping value.
Related `uiElementType` as following:
- `avatar` the URL of an avatar.
- `subttle` the text display in subtile.

![f-c-transfer.png](/.attachments/f-c-transfer-f8e3a2f0-6c95-4df4-94ee-a82882a98907.png)

<details>
<summary>Example for transferList</summary>

Below the screenshot is a part of [edit department](https://dash11.comm100.io/ui/10100000/global/people/departments/edit) page. Take members as an example. display avatar and email of the agent in this component, so add two additional fields for this component, the relationship between agent and department is many-to-many.

The configurations:
- component
  - `componentType` is `transferList`
  - `isInline` is `false`
  - `isIndent` is `false`
  - `columnSpan` is `12`
  - `fieldOrEntityName` is `agents`
  - additionalFields
    - avatar field
      - `fieldName` is `avatar`
      - `uiElementType` is `avatar`
    - email field
      - `fieldName` is `email`
      - `uiElementType` is `subtitle`

![f-c-transfer.png](/.attachments/f-c-transfer-f8e3a2f0-6c95-4df4-94ee-a82882a98907.png)

</details>

### drawerLink
`value`: `26`
Configure a [Form](/References/UI/Single-Row/Form) for it, and put the form's name to [`FormNameForDrawerLinkOrSubFormLink`](#FormNameForDrawerLinkOrSubFormLink).

![f-c-drawerlink.png](/.attachments/f-c-drawerlink-c34e0706-c2a0-4b9c-87f7-c77e551ec71f.png)

<details>
<summary>Example for drawerLink</summary>

Below screenshot is a part of [agentassit](https://dash11.comm100.io/ui/10100000/bot/agentassist/agentassist/) page. Show a form in drawer when clicking the drawer link, so create a [form](/References/UI/Single-Row/Form), put the name of form to [FormNameForDrawerLinkOrSubFormLink](#FormNameForDrawerLinkOrSubFormLink).

The configurations:
- component
  - `componentType` is `drawerLink`
  - `isInline` is `false`
  - `isIndent` is `true`
  - `formNameForDrawerLinkOrSubFormLink` is `AgentAssistTextBeforeArticle`
  - `componentText` is `Default text before the Knowledge Base article link`

![f-c-drawerlink.png](/.attachments/f-c-drawerlink-c34e0706-c2a0-4b9c-87f7-c77e551ec71f.png)

</details>

<!--### subFormLink
`value`: `28`
Configure a [Form](/References/UI/Single-Row/Form) for it, and put the form's name to [`FormNameForDrawerLinkOrSubFormLink`](#FormNameForDrawerLinkOrSubFormLink).-->

### table
`value`: `29`
The document is [here](/References/UI/Multi%2DRow/Table)

### multiSelect
`value`: `30`
Supports [Field](/References/Field)'s type is `reference`, the relationship is `manyToMany`.  It supports disable the option which configured in [`HTTPDeleteCondition`](/References/Entity-API), also it supports filter the options base on the scoping value.

![f-c-ms.png](/.attachments/f-c-ms-15f790a4-bd3a-43b3-8cae-cc87a1e853fb.png)

<details>
<summary>Example for multiSelect</summary>

Below the screenshot is a part of [new agent](https://dash11.comm100.io/ui/10100000/global/people/agents/new) page. Take departments as an example, the relationship between department and agent is many-to-many.

The configurations:
- component
  - `componentType` is `multiSelect`
  - `isInline` is `false`
  - `isIndent` is `false`
  - `fieldOrEntityName` is `departments`

![f-c-ms.png](/.attachments/f-c-ms-15f790a4-bd3a-43b3-8cae-cc87a1e853fb.png)

</details>

### numberInput
`value`: `31`
Only supports [Field](/References/Field)'s type is `number`. Configure number range via `min` and `max` properties of [Field](/References/Field).

![f-c-number.png](/.attachments/f-c-number-7d7c7380-e6a1-402d-a812-05db533cf5a6.png)

<details>
<summary>Example for numberInput</summary>

Below the screenshot is a part of [general](https://dash11.comm100.io/ui/10100000/bot/agentassist/agentassist/) settings page. create a field named 'highConfidenceScore' with integer type.

The configurations:
- highConfidenceScore field
  - `name` is `highConfidenceScore`
  - `default` is `40`
  - `type` is `integer`
  - `label` is `''`
- component
  - `componentType` is `numberInput`
  - `isInline` is `true`
  - `isIndent` is `false`
  - `inlineComponentWidth` is `82`
  - `fieldOrEntityName` is `highConfidenceScore`

![f-c-number.png](/.attachments/f-c-number-7d7c7380-e6a1-402d-a812-05db533cf5a6.png)

</details>

### datePicker
`value`: `33`
Only supports [Field](/References/Field)'s type is `date`. the date format is fetched from the current agent, eg: `MM-DD-YYYY`.

![f-c-datepicker.png](/.attachments/f-c-datepicker-69ce58b6-a756-4c74-814e-aee08c645afc.png)

<details>
<summary>Example for datePicker</summary>

Below the screenshot is part of the edit ticket's [holiday](https://dash11.comm100.io/ui/10100000/ticketing/settings/workingtimeholidays/holiday/) page. Clicking the edit icon in the operations column creates a data type field named 'Date'.

The configurations:
- date field
  - `name` is `date`
  - `default` is `''`
  - `type` is `date`
  - `label` is `Date`
- component
  - `componentType` is `datePicker`
  - `isInline` is `false`
  - `isIndent` is `false`
  - `columnSpan` is `6`
  - `fieldOrEntityName` is `date`

![f-c-datepicker.png](/.attachments/f-c-datepicker-69ce58b6-a756-4c74-814e-aee08c645afc.png)

</details>

### iframe
`value`: `34`
Display a frame, the frame and parent window has the same domain. they connection with the postMessage function.  Configure the url via [`IframeUrl`](#iframeUrl).

### colorPicker
`value`: `35`
Only supports [Field](/References/Field)'s type is `string`.

![f-c-colorpicker.png](/.attachments/f-c-colorpicker-56ae8ac2-0c0b-4a97-826c-e95d80c306d3.png)

<details>
<summary>Example for colorPicker</summary>

Below screenshot is a part of [chat button](https://dash11.comm100.io/ui/10100000/livechat/campaign/chatbutton/) page, switch to adaptive type.

The configurations:
- adaptiveButtonColor field
  - `name` is `adaptiveButtonColor`
  - `default` is `#329FD9`
  - `type` is `string`
  - `label` is `Color`
- component
  - `componentType` is `colorPicker`
  - `isInline` is `false`
  - `isIndent` is `false`
  - `columnSpan` is `4`
  - `fieldOrEntityName` is `adaptiveButtonColor`

![f-c-colorpicker.png](/.attachments/f-c-colorpicker-56ae8ac2-0c0b-4a97-826c-e95d80c306d3.png)

</details>

### fileInput
`value`: `36`
The `Type` Of the [Field](/References/Field) supports `file` and `image`. It can configure a [additional field](/References/UI/Single-Row/Form/Component/AdditionalField) where getting the file's name.

Related `uiElementType` as following:
- `fileNameField` config the field which stores file name.

![f-c-upload.png](/.attachments/f-c-upload-2f2cb073-a30e-41cd-bc71-709be2d03c2d.png)

<details>
<summary>Example for fileInput</summary>

Below the screenshot is a part of [chat button](https://dash11.comm100.io/ui/10100000/livechat/campaign/chatbutton/) page. Switch to image type and click the upload image link in the desktop view section. create a image field named 'imageButtonOnlineImage'.

The configurations:
- imageButtonOnlineImage field
  - `name` is `imageButtonOnlineImage`
  - `default` is `''`
  - `type` is `image`
  - `label` is `Online Button`
- component
  - `componentType` is `fileInput`
  - `isInline` is `false`
  - `isIndent` is `false`
  - `columnSpan` is `8`
  - `fieldOrEntityName` is `imageButtonOnlineImage`

![f-c-upload.png](/.attachments/f-c-upload-2f2cb073-a30e-41cd-bc71-709be2d03c2d.png)

</details>

### galleryImagePicker
`value`: `37`
Only supports [Field](/References/Field)'s is `reference`, the relationship is `oneToMany` or `manyToMany`. it provides the ability to pick the image from system or local, configure [additional fields](/References/UI/Single-Row/Form/Component/AdditionalField) to do it.

Related `uiElementType` as following:
- `type` config the field which stores the source of the image.
- `customImage` config the field which stores the image.

![f-c-banner.png](/.attachments/f-c-banner-3aff91b1-b464-4f91-a589-f07a78d6b19e.png)

<details>
<summary>Example for galleryImagePicker</summary>

Below the screenshot is a part of [chat window](https://dash11.comm100.io/ui/10100000/livechat/campaign/chatwindow/) page. Selected the first item in the style section, switch to a banner image in the header section, then clicking select banner image link. create a reference field named 'builtinChatWindowBannerImage' as follows. 

The configurations:
- builtinChatWindowBannerImage field
  - `name` is `builtinChatWindowBannerImage`
  - `default` is `@imageForChatWindow`
  - `type` is `reference`
  - `label` is `''`
  - `referenceEntityName` is `chatWindowBannerGalleryImage`
  - `referenceType` is `oneToMany`
- component
  - `componentType` is `galleryImagePicker`
  - `isInline` is `false`
  - `isIndent` is `false`
  - `columnSpan` is `12`
  - `fieldOrEntityName` is `builtinChatWindowBannerImage`

![f-c-banner.png](/.attachments/f-c-banner-3aff91b1-b464-4f91-a589-f07a78d6b19e.png)

</details>

### ruleConditionEditor
`value`: `39`
Configure a condition [entity](/References/Entity), the current entity includes this entity, the document about boundary configuration is [here](/References/Entity-in-boundary), the relationship is `oneToMany`, then put [entity](/References/Entity)'s `NameForPlural` to [`FieldOrEntityName`](#fieldOrEntityName), then configure two [additionalFields](/References/UI/Single-Row/Form/Component/AdditionalField) as following. The options data get from [dataSource](/References/UI/Data-Source) and put source's name to [`SelectDataSource`](#selectDataSource). 

Related `uiElementType` as following:
- `when` Config the reference entity field which stores operator.
- `logicalExpression` Config the reference entity field which stores the logical expression.

![f-c-conditions.png](/.attachments/f-c-conditions-353f0200-8b87-40b2-af7e-785235dd7e30.png)

<details>
<summary>Example for ruleConditionEditor</summary>

Below the screenshot is a part of the edit [trigger](https://dash11.comm100.io/ui/10100000/ticketing/settings/triggers/) page. Create a data source named 'ticketingField' for `ruleConditionEditor`, add two additional fields.

The configurations:
- component
  - `componentType` is `ruleConditionEditor`
  - `isInline` is `false`
  - `isIndent` is `false`
  - `columnSpan` is `9`
  - `fieldOrEntityName` is `triggerConditions`
  - additionalFields
    - conditionMetType field
      - `fieldName` is `conditionMetType`
      - `uiElementType` is `when`
    - logicalExpression field
      - `fieldName` is `logicalExpression`
      - `uiElementType` is `logicalExpression`
  - selectDataSource
    - ticketingField

![f-c-conditions.png](/.attachments/f-c-conditions-353f0200-8b87-40b2-af7e-785235dd7e30.png)

</details>

### customComponent
`value`: `40`
The component is provided by other modules, such as livechat and kb， put the name to [`CustomComponentName`](#CustomComponentName), add an extension for the module in the control panel project, the control panel will load the component as 'customComponent' dynamically. 

### button
`value`: `41`
Configure a [button action](/References/UI/Button-Action), put the Id of button action to [`ButtonActionId`](#ButtonActionId), button takes [`ComponentText`](#ComponentText) as the label.

### linkButton
`value`: `42`
Configure a [button action](/References/UI/Button-Action), put the Id of button action to [`ButtonActionId`](#ButtonActionId), button takes [`ComponentText`](#ComponentText) as the label.

![f-c-linkBtn.png](/.attachments/f-c-linkBtn-a9f62e7e-378c-4fd2-a74f-202c7ca87f19.png)

<details>
<summary>Example for linkButton</summary>

Below screenshot is a part of [chat window](https://dash11.comm100.io/ui/10100000/livechat/campaign/chatwindow/) page. selected 'allow visitors to email chat transcripts' option in 'options for visitors' section, create a [button action](/References/UI/Button-Action) for it.

The configurations:
- component
  - `componentType` is `linkButton`
  - `isInline` is `false`
  - `isIndent` is `false`
  - `componentText` is `Customize email subject`
  - `columnSpan` is `12`
  - buttonAction
    - `name` is `customizeEmailSubjectInCampaignLanguage`
    - `type` is `openPage`
    - `targetURL` is `../language/?scopingcampaignid=@query.scopingcampaignid`

![f-c-linkBtn.png](/.attachments/f-c-linkBtn-a9f62e7e-378c-4fd2-a74f-202c7ca87f19.png)

</details>

### icon
`value`: `43`
Only configure [`iconName`](#iconName) and [`helperText`](#helperText) for it.

![f-c-icon.png](/.attachments/f-c-icon-b5408b85-2f79-46e5-af18-044ec85936d9.png)

<details>
<summary>Example for icon</summary>

Below the screenshot is a part of [departments](https://dash11.comm100.io/ui/10100000/global/people/departments/) page. 
edit a department in the table.

The configurations:
- component
  - `componentType` is `icon`
  - `isInline` is `true`
  - `isIndent` is `false`
  - `helperText` is `Deselect this option to make this department unavailable in live chat. It will not appear as an option for offline messages, chat transfers, routing rules, auto-distribution, etc..`
  - `iconName` is `help`

![f-c-icon.png](/.attachments/f-c-icon-b5408b85-2f79-46e5-af18-044ec85936d9.png)

</details>

### switch
`value`: `44`
Only supports [Field](/References/Field)'s type is `bool`. It will take the `helperText`/`label` of the [field option](/References/Field-Option-Group) as label which value is 'true'

![f-c-switch.png](/.attachments/f-c-switch-55833c0c-b219-412f-9a06-221f87c424ab.png)

<details>
<summary>Example for switch</summary>

Below the screenshot is a part of [new agent](https://dash11.comm100.io/ui/10100000/global/people/agents/new) page. create a bool field with the name 'isActive', add two options for it, the switch will take the helperText/label of the option as the label which value is 'true'.

The configurations:
- isActive field
  - `name` is `isActive`
  - `default` is `true`
  - `type` is `bool`
  - `label` is `''`
  - field options
    - true option
      - `key` is `true`
      - `icon` is `dot`
      - `label` is `Active`
    - false option
      - `key` is `false`
      - `icon` is `graydot`
      - `label` is `Inactive`

- component
  - `componentType` is `switch`
  - `isInline` is `false`
  - `isIndent` is `false`
  - `columnSpan` is `12`
  - `fieldOrEntityName` is `isActive`

![f-c-switch.png](/.attachments/f-c-switch-55833c0c-b219-412f-9a06-221f87c424ab.png)

</details>

### invisibleVariable
`value`: `45`
This component doesn't have a corresponding UI. It will set a constant value of the field configured for this component, [InvisibleVariableValue](#InvisibleVariableValue) is the constant value.

<details>
<summary>Example for invisibleVariable</summary>

Config the image of the chat button on [chat button](https://dash11.comm100.io/ui/10100000/livechat/campaign/chatbutton/) page, switch type to image in type section, click 'upload image' in desktop view section. in this case, the imageButtonImageSource field needs to bring enum value to the backend to describe the current image is from local.

The configurations:
- imageButtonImageSource field
  - `name` is `imageButtonImageSource`
  - `type` is `enum`
  - `label` is `''`
  - field options
    - fromGallery option
      - `key` is `fromGallery`
      - `label` is `From Gallery`
    - fromMyComputer option
      - `key` is `fromMyComputer`
      - `label` is `From My Computer`

- component
  - `componentType` is `invisibleVariable`
  - `fieldOrEntityName` is `imageButtonImageSource`
  - `invisibleVariableValue` is `fromMyComputer`

</details>

### timeRangePicker
`value`: `46`
Only supports [Field](/References/Field)'s type is `time`. Get begin time from the configured field, configure a [additional field](/References/UI/Single-Row/Form/Component/AdditionalField) for end time.

Related `uiElementType` as following:
- `EndTimeForTimeRangePicker` get end time from this field.

![f-c-timerange.png](/.attachments/f-c-timerange-4a6feb7d-e87d-476d-910c-a361e1fc098f.png)

<details>
<summary>Example for timeRangePicker</summary>

Below the screenshot is a part of [operating hours & holidays](https://dash11.comm100.io/ui/10100000/ticketing/settings/workingtimeholidays/workinghoursconfig/) page. stay in the operating tab. config the time range of Monday as an example. The component needs two fields to show start time and end time, so config two fields with time type, the component bind mondayStartTime field. the other field as an additional field brings to the component.

The configurations:
- mondayStartTime field
  - `name` is `mondayStartTime`
  - `default` is `09:00:00`
  - `type` is `time`
  - `label` is `Monday Start Time`
- mondayEndTime field
  - `name` is `mondayEndTime`
  - `default` is `17:00:00`
  - `type` is `time`
  - `label` is `Monday End Time`

- component
  - `componentType` is `timeRangePicker`
  - `fieldOrEntityName` is `mondayStartTime`
  - `invisibleVariableValue` is `fromMyComputer`
  - `columnSpan` is `2`
  - `isInline` is `false`
  - `isIndent` is `false`
  - additionalFields
    - mondayEndTime field
      - `fieldName` is `mondayEndTime`
      - `uiElementType` is `EndTimeForTimeRangePicker`

![f-c-timerange.png](/.attachments/f-c-timerange-4a6feb7d-e87d-476d-910c-a361e1fc098f.png)

</details>

### subGroupTitleText
`value`: `47`
Configure the display text via [`componentText`](#componentText).

![f-c-subtitle.png](/.attachments/f-c-subtitle-f3aeee2c-79c2-48dc-9564-672896a33c14.png)

<details>
<summary>Example for subGroupTitleText</summary>

Below the screenshot is a part of [chat button](https://dash11.comm100.io/ui/10100000/livechat/campaign/chatbutton/) page. Switch to adaptive type, 'Desktop View' is a subGroupTitleText component.

The configurations:
- component
  - `componentType` is `subGroupTitleText`
  - `componentText` is `Desktop View`
  - `columnSpan` is `12`
  - `isInline` is `false`
  - `isIndent` is `false`

![f-c-subtitle.png](/.attachments/f-c-subtitle-f3aeee2c-79c2-48dc-9564-672896a33c14.png)

</details>

### dateTimePicker 
`value`: `48`
`version`: `v0.5.x`

It supports to pick the date and time.


<br/>
<br/>

## Label
`string`

Optional. Available for form's component, such as [`input`](#input), [`select`](#select) and [`password`](#password) etc. Support [variable](/References/UI/Variables).

Default is null. 
- If null, use field (or entity)’s label instead.
- If not null.
  - If empty, No label for the component.
![inline.png](/.attachments/inline-2c00a2b4-9c07-47a7-941b-09d5b5eef8d1.png)
  - If not empty, use this as the component label.

<br/>

## LabelDisplayStyle
This config only affects the form's component.

`enum` 

[`shrink(default) 0`](#shrink) [`placeholder 1`](#placeholder) [`above 2`](#above)

### shrink
`value`: `0`
It is default value, if it config to strink or empty, [label](#label) place inside of the component. 
![email.png](/.attachments/email-c86bc355-4017-4bb3-aeb3-592a54781170.png)
<details>
<summary>Example for shrink</summary>

Below the screenshot is a part of [new agent](https://dash11.comm100.io/ui/10100000/global/people/agents/new) page.

The configurations:
- component
  - `labelDisplayStyle` is `''`

![f-c-shrink.png](/.attachments/f-c-shrink-57632adb-4314-441c-ab58-89da1d3078c7.png)

</details>

### placeholder
`value`: `1`
Available for [`input`](#input), [`select`](#select) and [`multiSelect`](#multiSelect)

The [label](#label) display inside of component as placeholder.
![f-c-ms.png](/.attachments/f-c-ms-fe03fa0e-698a-42e7-946c-66a9c8cbf60c.png)
<details>
<summary>Example for placeholder</summary>

Below screenshot is a part of [general settings](https://dash11.comm100.io/ui/10100000/bot/agentassist/agentassist/) page. take [`multiSelect`](#multiSelect) as an example

The configurations:
- component
  - `componentType` is `multiSelect`
  - `labelDisplayStyle` is `placeholder`

![f-c-ms.png](/.attachments/f-c-ms-fe03fa0e-698a-42e7-946c-66a9c8cbf60c.png)

</details>

### above
`value`: `2`
Display label above input
![f-c-above.png](/.attachments/f-c-above-a0229da2-3d7c-4318-b44d-5121026f3dc6.png)
<details>
<summary>Example for above</summary>

Below the screenshot is a part of [new webhook](https://dash11.comm100.io/ui/10100000/livechat/integrationsapi/Webhooks/new) page, take 'Target URL' as an example.

The configurations:
- component
  - `componentType` is `input`
  - `label` is `Target URL`
  - `labelDisplayStyle` is `above`

![f-c-above.png](/.attachments/f-c-above-a0229da2-3d7c-4318-b44d-5121026f3dc6.png)

</details>

<br/>
<br/>

## MessageForRequiredFieldNotFilled
`string`

Optional. Available for form's component which is required, such as [`input`](#input), [`select`](#select) and [`password`](#password) etc. Support [variable](/References/UI/Variables).

- If not empty, display it when the value is empty.
- If it is null or empty, display '$fieldLabel cannot be empty.' when the value is empty.


<details>
<summary>Example for MessageForRequiredFieldNotFilled is not empty</summary>

Below the screenshot is a part of the bot's [intents](https://dash11.comm100.io/ui/10100000/bot/aichatbot/intents/) page. Click the import button on the left top of the page, click the import button in the drawer directly.

The configurations:
- uploadTemplateFile field
  - `name` is `uploadTemplateFile`
  - `label` is `Upload the Completed File`
  - `isRequired` is `true`
  - `type` is `file`
- component
  - `componentType` is `fileInput`
  - `fieldOrEntityName` is `uploadTemplateFile`
  - `messageForRequiredFieldNotFilled` is `The completed file cannot be empty.`

![f-c-err.png](/.attachments/f-c-err-04ae8b25-bd09-488b-8e81-b54746c20205.png)

</details>

<br/>
<br/>
 
## MessageForInvalidFormat
`string`

Optional. Available for form's component, such as [`input`](#input), [`select`](#select) and [`password`](#password) etc. Support [variable](/References/UI/Variables).

If null or empty, display “$fieldLabel is invalid.” when the format is invalid.

<details>
<summary>Example for MessageForInvalidFormat is not empty</summary>

Below the screenshot is a part of [auto translation](https://dash11.comm100.io/ui/10100000/livechat/settings/autotranslation/) page. type a special character and click the save button.

The configurations:
- component
  - `componentType` is `textarea`
  - `messageForInvalidFormat` is `Automatically translate incoming and outgoing chat messages when visitors speak a different language.`

![f-c-area.png](/.attachments/f-c-area-a8e5c781-d4c5-4572-88be-a13a4b57b69b.png)

</details>

<br/>
<br/>

## CustomComponentName
`string`

Optional. Available for [`ComponentType`](#ComponentType) is `customComponent`

Check example about [input component with prefix](#input)

<br/>

## FieldNameForCopyValueWhenChangedFirstTime
`string`

Optional. Available for form's component, such as [`input`](#input), [`select`](#select) etc.

The name of the field, when the component's onblur event is fired which [`FieldOrEntityName`](#FieldOrEntityName) is equal it, fill the value to current component if the value of it is empty at the first time.

<details>
<summary>Example</summary>

Below the screenshot is a part of [new banned IP](https://dash11.comm100.io/ui/10100000/livechat/settings/banlist/bannedip/) page. If 'End IP' is empty, when type the correct value to 'Start IP' then lost focus. Fill the value of 'Start IP' to 'End IP'.

The configurations:
- Start IP component
  - `componentType` is `input`
  - `fieldOrEntityName` is `ipRangeFrom`
  - `fieldNameForCopyValueWhenChangeFirstTime` is `""`
- End IP component
  - `componentType` is `input`
  - `fieldOrEntityName` is `ipRangeTo`
  - `fieldNameForCopyValueWhenChangeFirstTime` is `ipRangeFrom`

![ip.png](/.attachments/ip-0d1bdc0d-7929-45ea-84b6-e4caa6c389d9.png)

</details>

<br/>

## EditorHeight
`int`

Default: `300`, Available for [`htmlEditor`](#htmlEditor) and [`codeEditor`](#codeEditor)

The unit is the pixel.

<br/>

## FieldOrEntityName
`string`

Opional. Not available for [`groupBegin`](#groupBegin), [`groupEnd`](#groupEnt), [`newLine`](#newLine), [`text`](#text), [`placeholder`](#placeholder), [`iframe`](#iframe), [`drawerLink`](#drawerLink), [`button`](#button), [`linkButton`](#linkButton), [`icon`](#icon) and [`subGroupTitleText`](#subGroupTitleText).

[Field](/References/Field) name or boundary [entity](/References/Entity) name in the entity. 
- When field type is `boolean`.
 The component type can be [`checkbox`](#checkbox), [`select`](#select), [`radioGroup`](#radioGroup), [`switch`](#switch).

- When field type is `enum`.
The component type can be [`select`](#select), [`radioGroup`](#radioGroup).

- When field type is `int`.
The component type can be [`input`](#input), [`numberInput`](#numberInput).

- When field type is string or `text` or `number` or `html`.
 the component type can be [`input`](#input), [`textarea`](#textarea), [`codeEditor`](#codeEditor), [`htmlEditor`](#htmlEditor).

- When field type is `reference`.
The component type can be [`select`](#select), [`selectTree`](#selectTree), [`chipInput`](#chipInput), [`table`](#table), [`tansferList`](#tansferList).

- When field type is `IP`.
The component type can be [`input`](#input).

- When field type is `date` or `dateTime`.
The component type can be [`input`](#input), [`datePicker`](#datePicker).

- When field type is `enum`.
The component type can be [`select`](#select), [`checkboxList`](#checkboxList).

- If this is a boundary entity name.
The component type can be [`chipInput`](#chipInput), [`table`](#table). When ComponentType is `table`, display table from the multi rows page ER of boundary entity.

- When field type is `file` or `image`.
Use [`fileInput`](#fileInput)

- When field type is `password`.
The component type can be [`password`](#password), [`passwordWithRetype`](#passwordWithRetype).

- When field type is `stringArray`.
Use [`textarea`](#textarea)

- When field type is `stringArray`.
Use [`textarea`](#textarea)

<br/>

## InputComponentPrefix
`string`

Optional. Available for [`input`](#input).

Show a read-only text before input component, support [variables](/References/UI/Variables). Support [variable](/References/UI/Variables).

[Example](#input).

<br/>

## InputComponentSuffix
`string`

Optional. Available for [`input`](#input).

Show a read-only text after input component, support [variables](/References/UI/Variables). Support [variable](/References/UI/Variables).

<br/>

## ComponentText
`string`

Optional. Available form [`Text`](#text), [`Button`](#text), [`LinkButton`](#linkButton), [`DrawerLink`](#drawerLink) and [`subGroupTitleText`](#subGroupTitleText), 

Display text for component, support Html. Support [variable](/References/UI/Variables).

<br/>

## ButtonActionId
`string`

Optional. Available for [`Button`](#button) or [`LinkButton`](#linkButton)

Related configuration view [here](/References/UI/Button-Action).

<br/>

## SelectDataSource
`string[]`

Optional. Available for [`Select`](#select) or [`RuleConditionEditor`](#ruleConditionEditor).

View [document](/References/UI/Data-Source).

[Example](#ruleConditionEditor)

<br/>

## FormNameForDrawerLinkOrSubFormLink
`string`

Optional. Available for [`drawerLink`](#drawerLink).

Config a [Form](/References/UI/Single-Row/Form) show in a drawer.

[Example](#drawerLink)

<br/>

## GroupTitle
`string`

Optional. Available for [`GroupBegin`](#groupBegin)

Display it as the group's title. Support [variable](/References/UI/Variables).

[Example](#groupExample).

<br/>

## IsGroupExpandable
`bool`

Default: `false`. Available for [`GroupBegin`](#groupBegin)

- If true, the user can click to expand/collapse group and it is collapsed by default.
- If false, the group is always expanded and cannot be collapsed.

[Example](#groupExample)

<br/>

## GroupTitleSize
`enum`

`small(default) 0` `large 1`

Available for [`GroupBegin`](#groupBegin)

<details id="groupExample">
<summary>Example for group components</summary>

Below the screenshot is the layout of [new agent](https://dash11.comm100.io/ui/10100000/global/people/agents/new) page. `groupBegin` and `groupEnd` are configured in pair, `GroupTitle`, `GroupTitleSize` and `IsGroupExpandable` should be configured in `groupBegin`.

The configurations:
- components
  - groupBegin component
    - `componentType` is `groupBegin`
...
  others components
...
  - groupEnd component
    - `componentType` is `groupEnd`
  - groupBegin component
    - `componentType` is `groupBegin`
...
  others components
...
  - groupEnd component
    - `componentType` is `groupEnd`
  - groupBegin component
    - `componentType` is `groupBegin`
    - `groupTitle` is `More Information`
    - `groupTitleSize` is `large`
    - `isGroupExpandable` is `true`
...
  others components
...
  - groupEnd component
    - `componentType` is `groupEnd`

![f-c-layout.png](/.attachments/f-c-layout-2e892242-dda1-4702-90e7-fb21dd0345c5.png)

</details>

<br/>
<br/>

## SizeForImageRadioGroup
`number`

Optional. Available for [`ImageRadioGroup`](#imageRadioGroup)

The unit is “rem”.

<br/>

## IframeUrl
`string`

Optional. Available for [`iframe`](#iframe)

Always pass jwt token through URL so that the iframe content can access the current agent’s private data.

<br/>

## IconName
`string`

Optional. Available for [`Icon`](#icon)

The name of [Icon](/References/UI/Icon)

<br/>

## IsInline
`bool`

Default: `false`

- If `true`, display components inline and there is no space among the components.
- if `false`, display components base on [`ColumnSpan`](#ColumnSpan).

<br/>

## InlineComponentWidth
`number`

Optional. Available when [`IsInline`](#IsInline) is `true`

The unit is Pixel. 
- use case: chat button, the “Offset from right” text has a fixed width
![fixed with.png](/.attachments/fixed%20with-ed24936e-1ae7-4786-a7d4-219b97d0ef88.png)

<details>
<summary>Example for inline components</summary>

Below screenshot is a inline layout of [agent assist](https://dash11.comm100.io/ui/10100000/bot/agentassist/agentassist/) page. [newLine](#newLine) describe later components render in new line.

The configurations:
- text component
  - `componentType` is `text`
  - `componentText` is `Display suggestions only when the score is higher than `
  - `isIndent` is `true`
  - `isInline` is `true`
- placeHolder component
  - `componentType` is `placeHolder`
  - `isIndent` is `false`
  - `isInline` is `true`
  - `InlineComponentWidth` is `10`
- numberInput component
  - `componentType` is `numberInput`
  - `fieldOrEntityName` is `highConfidenceScore`
  - `isIndent` is `false`
  - `isInline` is `true`
- placeHolder component
  - `componentType` is `placeHolder`
  - `isIndent` is `false`
  - `isInline` is `true`
  - `InlineComponentWidth` is `10`
- text component
  - `componentType` is `text`
  - `componentText` is `<a href="https://hosted.comm100.com/kb/10000-2-a87 ...`
  - `isIndent` is `false`
  - `isInline` is `true`
- newLine component
  - `componentType` is `newLine`
  - `isIndent` is `false`
  - `isInline` is `true`

![f-c-inline.png](/.attachments/f-c-inline-31387d0b-2ded-443b-ba90-d10ec24e7845.png)

</details>

<br/>
<br/>

## IsIndent
`bool`

Default: `false`.
It is effective on the Component which is the first one in the row.
- If true, display space before the current component.
- If false, no space before the current component.

View [example](#InlineComponentWidth)

<br/>

## ColumnSpan
`number`

Optional. Available for component With [`IsInline`](#IsInline) is `false`.

Layout algorithm:
- the sum of the "columnSpan" values of all components exceeds 12, and the last component will be in the new line.
- There is a "newline" component in the components, and the components after it will be in the new line.

For example, 
[Input, ColumnSpan 6         ] 
[Input, ColumnSpan 7               ] [NewLine]
[Input, ColumnSpan 4] [Select, ColumnSpan 6        ]
[Check box, ColumnSpan 8              ] [Input, ColumnSpan 4]
[Select, ColumnSpan 4]
	New group will restart accumulate column spans


<details>
<summary>Example</summary>

The below screenshot is a part of [new article](https://dash11.comm100.io/ui/10100000/kb/knowledgebases/articles/new) page. it uses 12-column grid to layout components, but newLine component will break this layout, later components will place in a new line. the value of component's `isInline` is false.

The configurations:
- title component
  - `columnSpan` is `12`
- url component
  - `columnSpan` is `12`
- status component
  - `columnSpan` is `6`
- category component
  - `columnSpan` is `6`

![kb.png](/.attachments/kb-08b8fce2-e14c-4aee-99d5-2d33f02baf9a.png)

</details>

<br/>
<br/>

## ConditionForShowing
`string`

Default: `""`

the group will be hidden when all result of component is `false` between `groupBegin` and `groupEnd`. Support [variable](/References/UI/Variables). 
- If it has value, hide the component when the estimated result is `false`.
- If empty, show the component

eg: `@site.feature.agentAssist==true`

<br/>

## HelperText
`string`

Optional. Not available for components, such as [`groupBegin`](#groupBegin), [`groupEnd`](#groupEnd), [`placeHolder`](#placeHolder) and [`iframe`](#iframe) etc.

Support HTML. Support [variable](/References/UI/Variables).

[Example](#helpTextExample)

<br/>

## HelperTextPosition
`enum`

[`tooltip 0`](#tooltip) [`below(default) 1`](#below) 

### tooltip
`value`: `0`
Display [`HelperText`](#HelperText) in tooltip.
<details>
<summary id="helpTextExample">Example for tooltip</summary>

Below th screenshot is part of [new agent] page. Hover on the question icon.

The configurations:
- component
  - `componentType` is `customComponent`
  - `columnSpan` is `6`
  - `fieldOrEntityName` is `displayName`
  - `helperText` is `Agent’s name is displayed to visitors in the chat window.`
  - `helperTextPosition` is `tooltip`
  - `isInline` is `false`

![f-c-helpertext.png](/.attachments/f-c-helpertext-66574fce-f6e1-4d0e-ac1e-7f9849da89cf.png)

</details>

### below
`value`: `1`
Display [`HelperText`](#HelperText) below component.
<details>
<summary>Example for below</summary>

Below the screenshot is a part of [new public canned message](https://dash11.comm100.io/ui/10100000/global/cannedmessages/publiccannedmessage/new) page.

The configurations:
- component
  - `componentType` is `input`
  - `columnSpan` is `11`
  - `fieldOrEntityName` is `shortcuts`
  - `helperText` is `Multiple shortcuts can be added with commas. Only letters and numbers are allowed in a shortcut, e.g. bye, bye2. To send a canned message, type "#" to trigger the shortcut, e.g. if you have a canned message "Please hold on one minute.", and the shortcut is "hold", you can type "#hold" to locate this canned message. For more details, read our <a href="https://www.comm100.com/livechat/knowledgebase//how-to-use-my-canned-message-when-chatting-with-my-clients.html" target="_blank">knowledge base article</a>.`
  - `helperTextPosition` is `below`
  - `isInline` is `false`

![f-c-helper-b.png](/.attachments/f-c-helper-b-e5dda3a9-5bda-414a-a779-be314b5996cf.png)

</details>

<br/>
<br/>

## ParentFieldName
`string`

Optional.

Show current control as a child component of the parent field.

<details>
<summary>Example</summary>

Below the screenshot is a part of [chat button](https://dash11.comm100.io/ui/10100000/livechat/campaign/chatbutton/) page. Expanded advanced and select 'Display chat button on specified domains/URLs only', render tree UI via this property.

The configurations:
- parent component
  - `componentType` is `checkbox`
  - `fieldOrEntityName` is `isDomainRestrictionEnabled`
- child component
  - `componentType` is `textarea`
  - `fieldOrEntityName` is `allowedDomains`
  - `parentFieldName` is `isDomainRestrictionEnabled`

![f-c-p.png](/.attachments/f-c-p-20480d34-e4e0-4d9c-a61e-c8a1d3a5a0ed.png)

</details>

<br/>
<br/>

## InvisibleVariableValue
`string`

Optional. Available for [`invisibleVariable`](#invisibleVariable)

[Example](#InvisibleVariable)

<br/>

## ConditionForDisabled
`string`

Default: `""`. Available for the component which can receive client input.

If estimated result is `false`, disable component. Support [variable](/References/UI/Variables).
- If it has value, the estimated result is `false`, disable component， otherwise enable it.
- If empty, enable component.

eg: `$isSystem==true and $name!="Subject"`

<br/>

## CodeEditorSyntaxLanguage
`enum`

`javaScript 0` `html 1` `css 2` `none 3`

Optional. Available for [`codeEditor`](#codeEditor)

Language name.
[Example](#codeEditor)