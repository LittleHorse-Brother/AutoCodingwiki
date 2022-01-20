`DataFile` is used to filter data. It only available when component type is [`select`](/References/UI/Single-Row/Form/Component#select), [`multiselect`](/References/UI/Single-Row/Form/Component#multiSelect), [`transferList`](/References/UI/Single-Row/Form/Component#transferList) and [`radioGroup`](/References/UI/Single-Row/Form/Component#radioGroup) with oneToMany or manyToMany reference. Get reference entity list with conditions. If there are multiple configured conditions, all conditions must meet. 

Take the `Bot` configuration of the `ticket` module as an example. Click [here](https://autoportal.comm100dev.io/ui/1000/ticketing/channels/facebook/facebookaccount/edit) to jump to the `Bot` configuration page of Facebook, where there is a `select` component to select different `Bot` to reply to Facebook messages. Because some bots do not support Facebook, they need to filter out the bots that support Facebook. When rendering components, they will send a get request to get the data according to the configured conditions of the components.

<details>
<summary id="example">Example</summary>

<br/>

DataFilter:
- `FieldName` is `channelId`
- `value` is `Facebook Messenger`

`Select` component:

![select-bot.png](/.attachments/select-bot-5ff03538-c15f-436f-ba66-1a977a87b957.png)

GET Request:

![request.png](/.attachments/request-3ecdfecd-3ef7-4126-9a85-7cc47f76c349.png)

</details>

## Fields
- [FieldName](#FieldName)
- [Value](#Value)
- [ComponentId](#ComponentId)

<br/>

## FieldName
`string`

Required.

The name of the [condition](/References/Entity-API) belongs to the referenced Entity.

[Example](#example)

<br/>

## Value
`string`

Required.

Generate a condition as '[`Name`](#Name)=`Value`'
eg: `engineType=dialogflow`

<details>
<summary id="example">Example</summary>

Below screenshot is a part of ["general settings"](https://dash11.comm100.io/ui/10100000/bot/agentassist/agentassist/) page. It is 'manyToMany' between 'agentAssist' and 'chatbot'.

The configurations:
- entity
  - `manyToManyRelations` is `["chatbot", "knowledgeBase"]`
- component
  - `fieldOrEntityName` is `chatbots`
  - dataFilters
    - `fieldName` is `engineType`
    - `value` is `dialogflow`

GET Request: `https://dash11.comm100.io/api/Bot/chatbots?engineType=dialogflow&siteId=10100000`

![aibot.png](/.attachments/aibot-93beb223-df09-417f-870b-69f189cc4ed2.png)

</details>

<br/>

## ComponentId
`string`

Required.

The Id of the component needs a data filter. 