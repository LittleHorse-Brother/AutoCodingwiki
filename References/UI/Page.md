Describes a web page. Includes general info of a page, such as `path` `title`, etc. Below is the [bot intents page](https://dash11.comm100.io/ui/10100000/bot/aichatbot/intents/). When the current page's URL ends with '\new', it means the current page will display as a new page. Also when the current page's URL ends with '\edit', it means the current page will display as an edit page. But when the entity of the current page is the single record or the relationship to the scoping entity is 'oneToOne'/'oneToZeroOrOne', the current page will display as an edit page.
![image.png](/.attachments/image-1a021ac4-ab35-40af-85ce-1ff56e538997.png)

## Fields
- [Path](#Path)
- [PageType](#PageType)
- [Title](#Title)
- [Description](#Description)
- [DescriptionPosition](#DescriptionPosition)
- [HasGobackButton](#HasGobackButton)
- [Permission](#Permission)
- [ScopingEntityUniqueName](#ScopingEntityUniqueName)
- [EntityUniqueName](#EntityUniqueName)
- [IsReportEntity](#IsReportEntity)
- [ReportingEntityName](#ReportingEntityName)

<br>
<br>

## Path

`string`

Required. Globally Unique.

`Path` is part of the URL of the current page. The format of the page URL is 
```
http(s)://{domain}/ui/{siteId}{path}
```

For example:

URL of the live chat Dashboard page is

```
https://dash11.comm100.io/ui/10100000/livechat/dashboard/
```

The `path` of this page is `/livechat/dashboard/`.

<br>
<br>

## PageType
`enum`

[`entity (default) 0`](#entity) [`freeStylePage 1`](#freeStylePage) [`pageWithTabs 2`](#pageWithTabs)

### entity
`value`: `0`
A page for an entity handled by the auto coding framework.

### freeStylePage
`value`: `1`
A page handled by custom code. The autoCoding will render a component named CFreeStylePages. UI Components inside CFreeStylePages share the same global context and login session. CFreeStylePages will route to different UI based on the current url, the code of freestyle page and auto coding page will be statically linked together and split to different js files in production.

### pageWithTabs
`value`: `2`
A page contains tabs. The document of `Tab` is [here](/References/UI/Page/Tab).


<br>
<br>

## Title
`string`

Default: `""`. Available when [`pageType`](#pageType) is not `freeStylePage`.

Title of the current page. Usage:

- Display at the top of a page.
- Browser title.

If `title` is empty, use Entity's `Label` or `LabelForPlural` as the title instead. Support [variable](/References/UI/Variables).


<br>
<br>

## Description
`string`

Default: `""`. Available when [`pageType`](#pageType) is not `freeStylePage`.

Use for the introduction of the current page. Html supported. Display position controlled by the [`DescriptionPosition`](#DescriptionPosition) field. Support [variable](/References/UI/Variables).


<br>
<br>

## DescriptionPosition

`enum`

[`tooltip (default) 0`](#tooltip) [`belowTitle 1`](#BelowTitle)

Available when [`pageType`](#pageType) is not `freeStylePage`.

### tooltip

`value`: `0`

Display in a question mark icon beside the page title.

<details>
<summary id="tooltipexample">Example</summary>

Below is part of the [bot intents](https://dash11.comm100.io/ui/10100000/bot/aichatbot/intents/) page. The description of this page hides inside the question mark icon beside the title.
set `DescriptionPosition` to `belowTitle` and `Description` to the texts.
![image.png](/.attachments/image-53c0cc15-ac2d-46b7-b490-c63aab30b6b8.png)
</details>

### belowTitle

`value`: `1`

Display below the page title.
<details>
<summary id="belowtitleexample">Example</summary>

Below is part of the [bot entities](https://dash11.comm100.io/ui/10100000/bot/aichatbot/entities/chatbotEntity/?scopingchatbotid=ec0b425a-5c94-4893-9e5c-01f7eef03a1d) page. The description of this page displays below the title.

![image.png](/.attachments/image-9afc33d1-9f3c-46e9-b5c8-fd1705295508.png)
</details>


<br>
<br>

## HasGoBackButton

`bool`

Default: `false`. Available when [`pageType`](#pageType) is not `freeStylePage`.

- If `true`, show an arrow icon to the left of the page’s title. Click to go to `../` page (1 level up in path).
- If `false`, do not show the go back button

<details>
<summary>Example</summary>

Below is part of the [Webhooks](https://dash11.comm100.io/ui/10100000/livechat/integrationsapi/Webhooks/) page with a go-back-button. Click the go-back-button will open the [Integrations & API](https://dash11.comm100.io/ui/10100000/livechat/integrationsapi/) page.

![image.png](/.attachments/image-4207e3af-f118-44a1-9e48-d67445b58c5c.png)
</details>


<br>
<br>

## Permission
`int`

Id of Permission Entity. 
- If zero, all agents can open this page.
- If not zero, and the agent doesn’t have this permission, display the no permission page.


<br>
<br>

## ScopingEntityUniqueName

`string`

Components inside this page will be filtered by scopingEntityUniqueName. 
For example, the article page's scopingEntityUniqueName is knowledgebase.


<br>
<br>

## EntityUniqueName
`string`

Available when [`pageType`](#pageType) is `entity`.
Display UI generated by auto coding framework from this entity.


<br>
<br>

## IsReportEntity
`bool`

Available when [`pageType`](#pageType) is `entity`.
Set to `true` then this page is generated by auto reporting. Use this field together with the [`ReportingEntityName`](#ReportingEntityName) field.

<details>
<summary id="example-for-reporting-page">Example for Reporting Page
</summary>

Below is the [Bot Rating Report](https://dash11.comm100.io/ui/10100000/reporting/bot/rating/) page.

Configurations of the page are:
- `type`: `entity`
- `title`: `Rating`
- `path`: `/reporting/bot/rating/`
- `isReportEntity`: `true` 
- `reportingEntityName`: `ratingScoreByTime`.

![image.png](/.attachments/image-f13182a0-1921-4f16-80fb-306082cabfe2.png)
</details>


<br>
<br>

## ReportingEntityName
`string`

Available when [`IsReportEntity`](#IsReportEntity) is `true`.

Entity name of the reporting entity. This is **NOT** the auto coding entity name.

[Example for reporting page](#example-for-reporting-page)