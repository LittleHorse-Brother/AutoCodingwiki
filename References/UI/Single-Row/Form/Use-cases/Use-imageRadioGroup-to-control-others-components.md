## Summary
It uses to control other components, it can provide an intuitive UI. Take [chat button page](https://dash11.comm100.io/ui/10100000/livechat/campaign/chatbutton/) as an example.
There are three types for chat button, the configurations is difference per category, the UI is difference too. 

### The configurations:
Following config is not complete, it only list some key item.

- type field
  - `name` is `type`
  - `default` is `adaptive`
  - `type` is `enum`
  - field options
    - adaptive option
      - `icon` is `adaptiveType`
      - `key` is `adaptive`
    - image option
      - `icon` is `imageType`
      - `key` is `image`
    - textLink option
      - `icon` is `textlinkType`
      - `key` is `textLink`
#### Dispaly ImageRadioGroup when imageAndTextChatButton feature is enabled.
- imageRadioGroup component
  - `componentType` is `imageRadioGroup`
  - `fieldOrEntityName` is `type`
  - `conditionForShowing` is `@site.feature.imageAndTextChatButton==true`

#### Take ColorPicker as an example, Display it when the value of the above field is 'adaptive'
- colorPicker component
  - `fieldOrEntityName` is `adaptiveButtonColor`
  - `componentType` is `colorPicker`
  - `conditionForShowing` is `$type == "adaptive"`


### Switch to `Adaptive` item

![switch-adaptive.png](/.attachments/switch-adaptive-4fc1b12d-7b56-4552-9e83-13b5dfd87c74.png)

### Switch to `Image` item

![switch to image.png](/.attachments/switch%20to%20image-db593068-8f29-49fa-909c-47d84f65e42f.png)

  


