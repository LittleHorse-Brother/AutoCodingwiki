<!--
Autocoding项目是一个前后端分离的项目，所以需要创建API，供前端进行CRUD操作。 autocoding提供的API是restful API, 通API地址和请求可以读懂API属于哪个模块和操作那个资源。
-->

The auto coding project is a front-end and back-end separated project, so we need to create API for the front-end **CRUD** operations. The API provided by auto coding is a [Restful API](https://en.wikipedia.org/wiki/Representational_state_transfer). You can easily understand which module the API belongs to and operate which resource through the API. 
<!--
根据UI设计，页面有下面的功能：
- 分页显示规则
- 新建规则
- 修改已经存在的规则
- 删除已经存在的规则
- 批量删除已经存在的规则
-->
According to the [UI design](/Tutorial/Basic:-A-Real%2Dworld-Example/Requirement/UI-Design), the page has the following functions:
- Pagination display blocked sender's rules
- Create a new blocked sender's rule
- Modify existing blocked sender's rule
- Delete existing blocked sender's rule
- Batch delete existing blocked sender's rules

## Preparation
<!--
Entity相关的配制已经弄好， 下面的配制将用entity的`unqiueName`和`nameForPlural`.
-->
[Entity](/Tutorial/Basic:-A-Real%2Dworld-Example/Development/Create-Entity) related configuration is ready，the following configuration will be use entity's `uniqueName` and `nameForPlural`.

## Steps
1. [Create a record in the 'T_AutoCoding_API' table](#create-api)
2. [Test API](#test-api)

<a id="create-api"></a>
## 1. Create a record in the `T_AutoCoding_API` table
<!--
这是配制API的表，autocoding系统根据这里的配制生成相关的API, 表里有很多配制，这里只描述使用的属性。根据页面的功能，API需要支持`GET`, `POST`，`PUT` 和 `DELETE`方法.
-->
This table for configuring the API. The auto coding system generates related APIs according to the configuration. There are many fields in the table, here only described the fields used. According to the functions of the page, the API needs to support **GET**, **POST**, **PUT** and **DELETE** methods.

Script as following：

![api-table.PNG](/.attachments/api-table-b52fdd79-4659-4e73-9dfa-8ade2a0b6615.PNG)

### EntityUniqueName
<!--
设置`EntityUniqueName`为`blockedSender`，通过Entity的`uniqueName`把Entity的配制和API的配制关联起来
-->

Set `entityuniquename` to `blockedsender`, and associate entity's configuration with API's configuration by entity's [`uniqueName`](/Tutorial/Basic:-A-Real%2Dworld-Example/Development/Create-Entity#uniquename).

### IfHasHttpGet
<!--
设置`IfHasHttpGet`为`true`，API支持GET请求, 使用GET请求去获取单条和多条记录.
-->
Set `IfHasHttpGet` to `true`. The API supports the **GET** method and uses **GET** request to obtain single and multiple records.
<!--
终端的格式:
- 获取单条记录，`/{application}/{entity's nameForPlural}/{id}`
- 获取列表， `/{application}/{entity's nameForPlural}`
-->
The format of endpoint:
- Obtain single record: `/{application}/{entity's nameForPlural}/{id}`
- Obtain multiple records: `/{application}/{entity's nameForPlural}`

### IfHasHttpPost
<!--
设置`IfHasHttpPost`为`true`，API支持POST请求, 使用POST请求去新增一条记录, 或都批量更新. 终端的格式： `/{application}/{entity's nameForPlural}`
-->
Set 'IfHasHttpPost' to 'true'. The API supports the **POST** method. Use **POST** request to add a new record or batch update them.

The format of endpoint: `/{application}/{entity's nameForPlural}`

### IfHasHttpPut
<!--
设置`IfHasHttpPut`为`true`， API支持PUT请求, 使用PUT请求去更新单条记录。终端的格式： `/{application}/{entity's nameForPlural}/{id}`
-->
Set 'ifhashttpput' to 'true'. The API supports the **PUT** method and uses **PUT** request to update a single record.

The format of endpoint: `/{application}/{entity's nameForPlural}/{id}`

### IfHasHttpDelete
<!--
设置`IfHasHttpDelete`为`true`， API支持Delete请求, 使用Delete请求去删除单条或者多条记录。
-->
Set 'IfHasHttpDelete' to 'true'. The API supports the **DELETE** method. **DELETE** request are used to delete single or multiple records.
<!--
终端的格式:
- 删除单条记录，`/{application}/{entity's nameForPlural}/{id}`
- 删除多条记录， `/{application}/{entity's nameForPlural}`
-->
The format of endpoint:
- Delete single record，`/{application}/{entity's nameForPlural}/{id}`
- Delete multiple records， `/{application}/{entity's nameForPlural}`

### IsPagination
<!--
设置`IsPagination`为`true`，GET API支持分页功能。在当前例，获取Blocked sender列表数据时使用分页功能。
-->
Set the 'IsPagination' to 'true'. Get API supports paging. In the current example, paging is used to get the blocked sender's list.

<br/>

<a id="test-api"></a>
## 2. Test API

<mark>After making any API changes (including configurations of entity and entity's fields as well), you have to restart the backend API application to take effect.</mark>

<mark>
All the following backend endpoints' URL starts with `http://localhost:8080/api/ticketing`.
</mark>

Note:
The `localhost:8000` is a proxy front for overcoming the cross-domain issue in the web browser. The actual backend service is `localhost:5000`. If you want to access the backend service directly, the URL starts with `http://localhost:5000` (NO ticketing).

### Steps:
&nbsp;&nbsp;&nbsp;&nbsp;2.1. [Get API](#get-api)
&nbsp;&nbsp;&nbsp;&nbsp;2.2. [Get list API](#get-list-api)
&nbsp;&nbsp;&nbsp;&nbsp;2.3. [Update API](#update-api)
&nbsp;&nbsp;&nbsp;&nbsp;2.4. [Batch delete API](#batch-delete-api)
&nbsp;&nbsp;&nbsp;&nbsp;2.5. [Delete API](#delete-api)

<br/>

<a id="get-api"></a>
### Get API
- EndPoint: `/blockedSenders/{id}`
- Method: `GET`
- Query: 
  - siteId: `siteId`

![postman1.PNG](/.attachments/postman1-76d9a85c-31a4-4092-b095-e8b334c07d7a.PNG)

<a id="get-list-api"></a>
### Get list API
- EndPoint: `/blockedSenders`
- Method: `GET`
- Query: 
  - siteId: `siteId`
  - pageIndex: `1`
  - pageSize: `50`

![plist.PNG](/.attachments/plist-5872ca95-c9a7-4c3e-aeec-d375dac0ee0a.PNG)

<a id="update-api"></a>
### Update API
- EndPoint: `/blockedSenders/{id}`
- Method: `PUT`
- Query: 
  - siteId: `siteId`
- Params:
  - blockLevel: `markFutureMessagesAsJunk`
  - emailOrDomain: `test.com`

![update.PNG](/.attachments/update-d91370f1-47d2-4b76-923f-eaadc490c9e4.PNG)

<a id="batch-delete-api"></a>
### Batch delete API
- EndPoint: `/blockedSenders`
- Method: `DELETE`
- Query: 
  - siteId: `siteId`
- Params: `["id1", "id2"]`

![batchdelete.PNG](/.attachments/batchdelete-b486f426-efee-453c-98d6-7aa6e085ce3a.PNG)

<a id="delete-api"></a>
### Delete API
- EndPoint: `/blockedSenders/{id}`
- Method: `DELETE`
- Query: 
  - siteId: `siteId`

![delete.PNG](/.attachments/delete-8d5501db-3086-482c-81e9-3d67de4a2036.PNG)
