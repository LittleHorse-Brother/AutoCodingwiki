Describe a button action used to expand the function of the button. Includes insert a variable to an input or an editor, open page, etc.

## Fields
- [Id](#Id)
- [Name](#Name)
- [Type](#Type)
- [DataSource](#DataSource)
- [TitleForInsertVariableOrImage](#TitleForInsertVariableOrImage)
- [DescriptionForInsertVariableOrImage](#DescriptionForInsertVariableOrImage)
- [TargetURL](#TargetURL)
- [IsOpenPageInNewTab](#IsOpenPageInNewTab)
- [TargetEntityName](#TargetEntityName)
- [SubmitFormRequestPath](#SubmitFormRequestPath)
- [SubmitFormSuccessMessage](#SubmitFormSuccessMessage)

<br>
<br>

## Id

`string`

Default: `""`. Unique.

<br>
<br>

## Name

`string`

Default: `""`. Required when [`Type`](#Type) is [`custom`](#custom).

The name of the custom component. Only available for [`custom`](#custom).

[Example](#customexample)

<br>
<br>

## Type

`enum`

[`insertVariable (default) 1`](#insertVariable) [`openPage 3`](#openPage) [`entityInDrawer 4`](#entityInDrawer) [`submitForm 5`](#submitForm) [`custom 6`](#custom)

### insertVariable

`value`: `1`

Open a drawer with a data list (Data come from [`DataSource`](#DataSource) API) when clicking, and then select a variable in the drawer to insert to an input or an editor.

<details>
<summary id="insertvariableexample">Example</summary>

Below is part of the [New Trigger](https://dash11.comm100.io/ui/10100000/ticketing/settings/triggers/new) page.

Configurations of the button action are:
- `type`: `insertVariable`
- `dataSource`: `["ticketingField"]`
- `titleForInsertVariableOrImage`: `Add a Field`
- `descriptionForInsertVariableOrImage`: `Add a macro parameter into this email or canned response`

![InsertVariable.png](/.attachments/InsertVariable-d6a320a0-a79c-4d61-b257-d44141aaba7f.png)
</details>

<br>

### openPage

`value`: `3`

Open a page when clicking. The URL of the page is determined by [`targetURL`](#targetURL).

<details>
<summary id="openpageexample">Example</summary>

Below is part of the [Installation](https://dash11.comm100.io/ui/10100000/livechat/campaign/installation/) page.

Configurations of the button action are:
- `type`: `openPage`
- `targetURL`: `https://@currentDomain/frontEnd/assets/livechat/previewpage/?campaignId=@query.scopingcampaignid&siteId=@site.siteId`
- `isOpenPageInNewTab`: `true`

![OpenPage.png](/.attachments/OpenPage-46101d35-dfd3-48f2-a4f1-dbe9ba138ee8.png)
</details>

<br>

### entityInDrawer

`value`: `4`

Open a drawer when clicking, display an entity in the drawer. The entity is determined by [`targetEntityName`](#targetEntityName).

<details>
<summary id="entityindrawerexample">Example</summary>

Below is part of the [Installation](https://dash11.comm100.io/ui/10100000/livechat/campaign/installation/) page.

Configurations of the button action are:
- `type`: `entityInDrawer`
- `targetEntityName`: `emailInstallationCode`

![EntityInDrawer.png](/.attachments/EntityInDrawer-89c34f29-7eae-4482-9706-091551bcbdb2.png)
</details>

<br>

### submitForm

`value`: `5`

Submit the current form to an address. The address is determined by [`submitFormRequestPath`](#submitFormRequestPath). Only available when the button action is used in a form.

<details>
<summary id="submitformexample">Example</summary>

Below is part of the [Installation](https://dash11.comm100.io/ui/10100000/livechat/campaign/installation/) page (email your code to your webmaster).

Configurations of the button action are:
- `type`: `submitForm`
- `submitFormRequestPath`: `/livechat/campaigns/@query.scopingcampaignid/installation:emailCode`
- `submitFormSuccessMessage`: `Code sent successfully.`

![SubmitForm.png](/.attachments/SubmitForm-835c4656-4e28-4e67-8e87-e373bcc1e765.png)
</details>

<br>

### custom

`value`: `6`

Find component by [`Name`](#Name) and execute.

<details>
<summary id="customexample">Example</summary>

Below is part of the [New Article](https://dash11.comm100.io/ui/10100000/kb/knowledgebases/articles/new) page.

Configurations of the button action are:
- `name`: `CKBPreviewArticleButton`
- `type`: `custom`

![Custom.png](/.attachments/Custom-3524f08c-9e9a-4523-be83-94167c265ff9.png)
</details>

<br>
<br>

## DataSource

`stringarray`

Default: `[]`. Required when [`Type`](#Type) is [`InsertVariable`](#InsertVariable).

The [`Name`](/References/UI/Data-Source#Name) list of the data source. Only available for [`insertVariable`](#insertVariable).

[Example](#insertvariableexample)

<br>
<br>

## TitleForInsertVariableOrImage

`string`

Default: `""`. Optional.

The title for the insert drawer. Only available for [`insertVariable`](#insertVariable). Support [variable](/References/UI/Variables).

[Example](#insertvariableexample)

<br>
<br>

## DescriptionForInsertVariableOrImage

`string`

Default: `""`. Optional.

The description for the insert drawer. Only available for [`insertVariable`](#insertVariable). Support [variable](/References/UI/Variables).

[Example](#insertvariableexample)

<br>
<br>

## TargetURL

`string`

Default: `""`. Required when [`Type`](#Type) is [`openPage`](#openPage).

Page URL to open. Only available for [`openPage`](#openPage), support [variable](/References/UI/Variables).

[Example](#openpageexample)

<br>
<br>

## IsOpenPageInNewTab

`bool`

Default: `false`.

Only available for [`openPage`](#openPage).

- If true, open in a new browser tab.
- If false, open in the current browser tab.

[Example](#openpageexample)

<br>
<br>

## TargetEntityName

`string`

Default: `""`. Required when [`Type`](#Type) is [`entityInDrawer`](#entityInDrawer).

Entity [`UniqueName`](/References/Entity#UniqueName) to use for the drawer. Only available for [`entityInDrawer`](#entityInDrawer).

[Example](#entityindrawerexample)

<br>
<br>

## SubmitFormRequestPath

`string`

Default: `""`. Required when [`Type`](#Type) is [`submitForm`](#submitForm).

Request path to submit. Only available for [`submitForm`](#submitForm), support [variable](/References/UI/Variables).

[Example](#submitformexample)

<br>
<br>

## SubmitFormSuccessMessage

`string`

Default: `""`. Optional.

The message to show when the submitting is successful. Only available for [`submitForm`](#submitForm). Support [variable](/References/UI/Variables).

[Example](#submitformexample)