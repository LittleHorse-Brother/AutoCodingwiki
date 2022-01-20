In auto coding framework entity is stored in the `t_AutoCoding_Entity` table of the `{deployName}.AutoCoding` database. What we need to do for creating an entity is adding a record to that table.

There are lots of columns in the `t_AutoCoding_Entity` table. In this tutorial, we only cover some of the most important columns. Full document is [here](/References/Entity)

## Preparation
At first, following the steps of [create database table](/Tutorial/Basic:-A-Real%2Dworld-Example/Development/Create-Database-Table) to create `T_Ticketing_BlockedSender` table in the site database.

## Steps

There are two parts we need to do to create an entity:
  1. [Add entity record, setup properties related to an entity](#create-entity)
  1. [Add fields of the entity](#create-fields)

<a id="create-entity"></a>
## 1. Create entity record
Execute following script in `{deployName}.AutoCoding` database:

![new-entiry.PNG](/.attachments/new-entiry-f505b0ba-f068-465b-82af-afd7dbdd591c.PNG)


### uniqueName

UniqueName is the identifier of an entity, it must be unique in our system. In our case, we can call it `blockedSender`. We can also change it to `ticketingBlockedSender` to avoid conflict.

UniqueName is only for internal use, it will not appear in a UI or API URL.

### nameForPlural

Set `nameForPlural` to `blockedSender`. `NameForPlural` is used in the following places: 
  - Page URL: `/ticketing/settings/blockedsenders/`, the document is [here](/References/Entity#nameForPlural)
  - API URL: send `GET /ticketing/blockedSenders` to fetch all blocked senders in a site.

If an entity is a single record entity (meaning there is only one record in a site), then `nameForPlural` will not be used, use the `name` instead.

### name

Set `name` to `blockedSender`

`name` is used in the following places: 
  - Database table name: for `blockedSender` entity the corresponding database name is `t_ticketing_blockedSender`
  - Page URL: only for single record entity
  - API URL: only for a single record entity

### label

Set `label` to `Blocked Sender`. Label is for display. For example:
  - Label of the `New Blocked Sender` button
  - Delete confirm message: Are you sure you want to delete the blocked sender "aaa.com"?


### labelForPlural

Set `labelForPlural` to `Blocked Senders`

`LabelForPlural` is for display when the context requires a plural name. For example, the confirm message for batch delete is `Are you sure you want to delete the 2 blocked senders?`

### isMultiRecord

Set `isMultiRecord` to `0` means that the current entity **is** a multiple records entity (this is a mistake, we shouldn't use 0 as true here). Multiple records means that we might have multiple blocked senders in one site.

Other values of `isMultiRecord` are described in [here](/References/Entity#isMultiRecord).

### application

`application` is also known as the module name. Set `application` to `ticketing`.
`application` is used in the following places: 
  - Database table name: `t_ticketing_blockedSender`
  - Page URL: `/ticketing/settings/blockedsenders/`

### fieldToBeDisplayedWhenReferenced

This should be one of the field's name of the `blockedSender` entity.

If we want to display the blocked senders in a drop-down list, this field is what we need to show as a drop-down list item.

For `blockedSender` entity, it should be `emailOrDomain`.

### isAuthenticateRequired

If it is `true`, sign in an agent is required to access this entity. In this tutorial, we don't have a sign in service so we set it to `false` for convenience.

<br/>

<a id="create-fields"></a>
## 2. Create Fields of the entity
Fields describe the properties of the current entity, the name will be used to the property name of the corresponding entity in the API. The name of field must be consistent with the field name of the table in database, but field's name must be named as lower camel case, take `EmailOrDomain` column for example, it named `EmailOrDomain` in the `t_ticketing_blockedSender`, but it named `emailOrDomain` in the field.

### Steps
Base on [UI design](/Tutorial/Basic:-A-Real%2Dworld-Example/Requirement/UI-Design), there are three properties need to be created, their named `id`, `emailOrDomain` and `blockLevel`. There are many columns in the field configuration, here only describe the columns used in the corresponding fields.

&nbsp;&nbsp;&nbsp;&nbsp;2.1. [Create 'id' field](#create-id-field)
&nbsp;&nbsp;&nbsp;&nbsp;2.2. [Create 'emailOrDomain' field](#create-emailordomain-field)
&nbsp;&nbsp;&nbsp;&nbsp;2.3. [Create 'blockLevel' field](#create-blocklevel-field)

<a id="create-id-field"></a>
### 2.1. Create `id` field
According to [ER design](/Tutorial/Basic:-A-Real%2Dworld-Example/Requirement/ER-Design), `id` is the primary key in the table, which is automatically generated and describes each record uniquely in the table. In the endpoint, API can get, edit and delete a record via `ID`'s value.

Script as following:

![id.PNG](/.attachments/id-e3b8f0a5-f293-4ac6-8ce1-467b7d6e67fd.PNG)

#### entityUniqueName
Set `entityUniqueName` to `blockedsender`. This value is defined when creating the [entity](#create-entity), the entity is associated with the field by it.

#### name
Set `name` to `id`. The name of field must be consistent with the field name of the table in database, but field's name must be named as lower camel. `id` as a property of the entity which is described in the API response, get the value of `id` from the entity via `name`.


#### type
Set `type` to `0`, `0` indicates GUID type. others supported types view [here](/References/Field#type)

`type` used scenarios:
- Validate the format of data.
- When retrieve the data via API, format the data according to the type.
- Convert the format in the frontend, eg: the current field type is `int`, accepted value is string when typing in the input, so  covert data to `int`.


#### isPrimary
Set `isPrimary` to `true`, mark that the current field is the primary key.
- If entity is multiple records, you must set a field to be the primary key.
- If entity is a single record, you don't need to set the primary key, use siteId instead.

<a id="create-emailordomain-field"></a>
### 2.2. Create `emailOrDomain` field
`emailOrDomain` uses to save restricted email or email's domain. The value is unique in site level. This is the feature of ticketing module. Ticketing will no longer receive messages from restricted email or email domain.

Script as following:

![emailordomain.PNG](/.attachments/emailordomain-ce99ea8d-3cdb-4536-ac10-473df1fded70.PNG)

#### entityUniqueName
Set `entityUniqueName` to `blockedSender`, This value is defined when creating [entity](#create-entity), the entity is associated with the field by it.

#### name
Set `name` to `emailOrDomain`. The name of field must be consistent with the field name of the table in database, but field's name must be named as lower camel. `emailOrDomain` as a property of the entity which is described in the API response, get the value of `emailOrDomain` from the entity via `name`.

#### label
Set `label` to `Email/Domain`, `label` is used in the UI.
- In the list page, it is displayed in the table header.
- In the form page, it as label of `emailOrDomain` element.
- It is used in the error message. eg: `Email/Domain is invalid.`.


#### type
Set `type` to `2`, `2` indicates the type of string. others supported types view [here](/References/Field#type)

`type` used scenarios:
- Validate the format of data.
- When retrieve the data via API, format the data according to the type.
- Convert the format in the frontend, eg: the current field type is `int`, accepted value is string when typing in the input, so  covert data to `int`.

#### isRequired
Set `isRequired` to `true`. This field is required when submitting a form. If the value is empty, showing a error message below the input when clicking the `Save` button, like `Email/Domain cannot be empty.`.

#### isUnique
Set `isUnique` to `true`. the value of this field cannot be repeated at the site level. For example, it doesn't allow that exist two records with the same values of `siteid` and `EmailOrDomain`. In the form page, if the current value exists in database, it show error message like `Email/Domain "xxx" already exists`.

#### maxLength
Set `maxLength` to `256`, the value of the field is limited in length, the default value is `0`, it indicates the  length of the field is unlimited. In the form page, the input can't type when the length of value more than `maxlength`.

#### regexValidation
Set `regexValidation` to `(^[a-zA-Z0-9.!#$%&’*+/=?^_'{|}~-]+@[a-zA-Z0-9-]+(?:\.[a-zA-Z0-9-]+)*$)|(^([a-z0-9]+(-[a-z0-9]+)*\.)+[a-z]{2,}$)`, it is regular expression. In the form page, use the expression to validate current value  when clicking `Save` button. If the value is invalid, show a error message below the input like `Email/Domain is invalid.`.

<a id="create-blocklevel-field"></a>
### 2.3. Create `blockLevel` field
According to [UI design](/Tutorial/Basic:-A-Real%2Dworld-Example/Requirement/UI-Design), select different block level for blocked sender's rule, so config an `enum` type for field.

The values are as follows:
- 0: Reject all future messages
- 1: Mark future messages as junk

#### Steps
`t_AutoCoding_Field` and `t_autocoding_FieldOptionGroup` is a one-to-one relationship, `t_autocoding_ FieldOptionGroup` and `t_autocoding_FieldOption' is a one-to-many relationship.

&nbsp;&nbsp;&nbsp;&nbsp;2.3.1. [Create a record in 't_autocoding_FieldOptionGroup' table](#create-fieldoptiongroup-table)
&nbsp;&nbsp;&nbsp;&nbsp;2.3.2. [Add tow records in 't_autocoding_FieldOption'](#add-fieldoption-table)
&nbsp;&nbsp;&nbsp;&nbsp;2.3.3. [Create 'blockLevel' field](#create-blocklevel-field-2)

<a id="create-fieldoptiongroup-table"></a>
#### 2.3.1 Create a record in `t_autocoding_fieldoptiongroup` table
Create a record in this table, associate `t_AutoCoding_Field` and `t_autocoding_FieldOption` by the group `Id`.

Script as following:

![new-optionGroup.PNG](/.attachments/new-optionGroup-0b545b3b-aca7-46ee-9dab-5b9a70e99fe8.PNG)

#### name
Define an readable name, the general format is `{application}{field name}`

<a id="add-fieldoption-table"></a>
#### 2.3.2 Add two records in `t_autocoding_fieldoption`
Get the `Id` of the previous step, take it as the value of `OptionGroupId`, and create two records for enumeration values.

Script as following:

![newOptions.PNG](/.attachments/newOptions-c36b3247-7ffb-41aa-837e-57348e97adcb.PNG)

#### value
Corresponding enumeration value.

#### name
Enumeration name, use lower camel to define a meaningful name, name instead of enumeration value in API. In this tutorial, name as value of radio element in form page.


#### label
The description for enumeration value.

`label` used scenarios:
- In the list page, display in the `block level`'s column to describe selected block level in the current row.
- In the form page, as the radio's label.


<a id="create-blocklevel-field-2"></a>
#### 2.3.3 Create `blockLevel` field
Create a 'blocklevel' field with prepared the data in the previous steps.

Script as following：

![blocklevel.PNG](/.attachments/blocklevel-5f2027a0-7ba7-44b8-8e6a-c157cb226962.PNG)

#### entityUniqueName
Set `entityUniqueName` to `blockedSender`, This value is defined when creating [entity](#create-entity), the entity is associated with the field by it.

#### name
Set `name` to `blockLevel`. The name of field must be consistent with the field name of the table in database, but field's name must be named as lower camel. `emailOrDomain` as a property of the entity which is described in the API response, get the value of 'blockLevel' from the entity via `name`.

#### label
Set `label` to `block level`, used in display.

`label` used scenarios:
- In the list page, it is displayed in the table header
- In the new/edit page, it as the label of radio group.

#### type
Set `type` to `14`, `14` indicates enumerable type. others supported types view [here](/References/Field#type)

`type` used scenarios:
- Validate the format of data.
- When retrieve the data via API, format the data according to the type.
- Convert the format in the frontend, eg: the current field type is `int`, accepted value is string when typing in the input, so  covert data to `int`.

#### default
Set `default` to `markFutureMessagesAsJunk`, which is created in the [second step](#create-fieldoptiongroup-table). Open new page, there is a default selected item in radio group. 

#### optionGroupId
Set `optionGroupId` to option group `Id` which created in the [first step](#create-fieldoptiongroup-table). 
