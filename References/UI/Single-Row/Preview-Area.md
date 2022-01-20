Describes a Preview-Area object. Includes general info of a Preview-Area object, such as `EntityName`, `ComponentName`. Below is [prechat](https://dash11.comm100.io/ui/10100000/livechat/campaign/prechat/) page.

![preview-prechat.png](/.attachments/preview-prechat-32769c1a-5f88-4cae-8b1d-5bd1116aed20.png)

## Fields
- [EntityName](#EntityName)
- [ComponentName](#ComponentName)

<details>
<summary>Example</summary>

Below screenshot is a part of livechat's [prechat](https://dash11.comm100.io/ui/10100000/livechat/campaign/prechat/) page.

The configurations as following:
- entity
  - `uniqueName` is `campaignPreChat`
  - `uiPreviewArea`
    - `componentName` is `CLiveChatPreChatPreview`
    - `entityName` is `campaignPreChat`

![preview-prechat.png](/.attachments/preview-prechat-32769c1a-5f88-4cae-8b1d-5bd1116aed20.png)
</details>

<br /><br />

## EntityName
`string`

Required.

The unique name of entity, it bind to the [`ComponentName`](#ComponentName).

<br /><br />

## ComponentName
`string`

Required.

The Component is not provided by autocoding, it is a custom component.