<!--
根据UI设计，点击菜单进入“Blocked Senders”页面，使用table显示已经存在的限制规则, 通过table右侧的操作列可以编辑或者删除已经存在的数据，table本身要支持分页和批量操作，在table上面还有个新建按钮等乖。上面的的UI可以通过脚本配制出来，但涉及到多张表，下面简单地描述涉及到的表. 

相关的表：
- `t_autocoding_UIPageMultiRow` 配制列页面的`title`, `description`, 通过什么方式显示列表数据等等。 当前例子通过table显示数据。
- `t_autocoding_UITable` 配制table的功能，比如是否支持分页，是否支持批量操作等等。
- `t_autocoding_UITableColumn` 配制table显示Entity数据列。这里不包括批量操作和操作列， 它们有单独的配制。
- `t_autocoding_UITableOperation` 配制table的操作列。
- `t_autocoding_UIBatchOperation` 配制批量操作的按钮。
- `t_autocoding_UITableComponent` 配制在table上面显示的按钮。

上面的表通过EntityUniqueName跟Entity的配制关联起来。下面的配制步骤里只描述例子使用到的字段，更详细的文档看这里
-->
According to the [UI design](/Tutorial/Basic:-A-Real%2Dworld-Example/Requirement/UI-Design), click the "Blocked Senders" menu to enter the "Blocked Senders" page, and use the table to display the existing restriction rules. You can edit or delete the existing data through the operation's column on the right side of the table. The table itself supports paging and batch operations, and there is a new button on the table. The above UI can be configured by script, The tables involved are briefly described below:

Related tables:
- `t_autocoding_UIPageMultiRow` configure the `title` and `description` of the page, how to display the list data, etc. The current example displays data through the table.
- `t_autocoding_UITable` configure the functions of table, such as whether it supports paging, batch operation, etc.
- `t_autocoding_UITableColumn` config the table's column. Batch operations and operation columns are not included here. They have separate configurations.
- `t_autocoding_UITableOperation` config the operation column of the table.
- `t_autocoding_UIBatchOperation` config buttons for batch operation.
- `t_autocoding_UITableComponent` config buttons above the table.

The above table is associated with the configuration of entity through `entityUniqueName`. The following configuration steps only describe the fields used in the example. For more detailed documents, see [here](/References/UI/Multi%2DRow).

## Preparation
- The [Entity](/Tutorial/Basic:-A-Real%2Dworld-Example/Development/Create-Entity)'s configuration has been configured.
- The [Page](/Tutorial/Basic:-A-Real%2Dworld-Example/Development/Create-Page)'s configuration has been configured.

## Steps:
1. [Config Multi-Row](#multi-row)
2. [Config Table](#config-table)
3. [Config the columns of the table](#config-table-column)
4. [Config the operation column of the table](#config-table-operation)
5. [Config the batch operation column of the table](#config-table-batchoperation)
6. [Config the new button above the table](#config-table-btn)
7. [Test](#test)

<br/>

<a id="multi-row"></a>
## 1. Config Multi-Row
<!--
根据UI设计，使用table展示数据，在列表页面的`title`，`description` 和 `descriptionPosition`信息使用Page配制的. 在`t_autocoding_UIPageMultiRow`创建一条记录，配制好下面的字段。
-->
According to the [UI design](/Tutorial/Basic:-A-Real%2Dworld-Example/Requirement/UI-Design), the table is used to display the data. The information of `title`, `description` and `descriptionPosition` use the configuration of the [Page](/Tutorial/Basic:-A-Real%2Dworld-Example/Development/Create-Page). Create a record in the `t_autocoding_UIPageMultiRow` table, the configuration as following.

Script:

![mr.PNG](/.attachments/mr-4a2abdb4-88b9-4c3b-b7f1-fe5a20b20be8.PNG)

### entityUniqueName
<!--
设置“entityUniqueName”为 “blockedSender”。 就是Entity的“uniqueName”，通过这个值把Multi-Row的配制跟Entity关联。
-->
Set `entityUniqueName` to `blockedSender`. It is the `uniqueName` of [Entity](/Tutorial/Basic:-A-Real%2Dworld-Example/Development/Create-Entity), which associates the configuration of Multi-Row with the entity.

### presentationType
<!--
设置“presentationType”为“0”， 这是一个枚举值，列表页面显示数据的方式如下：
- 0是“table” 用table显示数据。
- 1是“tree”  用于显示具有树形结构的数据。
- 2是“imageList” 用于显示图片的，

当前的例子是使用table来显示数据。
-->
Set `presentationType` to `0`. This is an enumeration value：
- `0` is `table`, use table to display data.
- `1` is `tree`, display data with a tree structure.
- `2` is `imageList`. used to displaying pictures.

The current example is to use table to display data.

<br/>

<a id="config-table"></a>
## 2. Config Table
<!--
主要配制table的功能，根据UI设计,table支持分页和批量操作。在`t_autocoding_UITable`创建一条记录，配制好下面的字段：
-->
According to the [UI design](/Tutorial/Basic:-A-Real%2Dworld-Example/Requirement/UI-Design), the table supports paging and batch operation. Create a record in the `t_autocoding_UITable` table,  the configuration as following:

Script:

![table.PNG](/.attachments/table-b2699c29-19ff-4479-9114-a688ac488b2b.PNG)

### entityUniqueName
<!--
设置“entityUniqueName”为 “blockedSender”。 就是Entity的“uniqueName”，通过这个值把Table的配制跟Entity关联。
-->
Set `entityUniqueName` to `blockedSender`. It is the `uniqueName` of [Entity](/Tutorial/Basic:-A-Real%2Dworld-Example/Development/Create-Entity), which associates the configuration of the Table with the entity.

### isEnableBatchOperation
<!--
设置“isEnableBatchOperation”为 “true”. 表示table支持批量操作，批量操作相关的配制请看这里。
-->
Set `isEnableBatchOperation` to `true`. Indicates that the table supports batch operation. Please see [here](#config-table-batchoperation) for the configuration of batch operation.

### isPagination
<!--
设置“isPagination”为 “true”. 表示table支持分页。
-->
Set `isPagination` to `true`. Indicates that the table supports paging.

<br/>

<a id="config-table-column"></a>
## 3. Config the columns of the table
<!--
根据UI设计，列表页面显示的数据例是"Email/Domain" 和 “Block Level”. 只在`t_autocoding_UITableColumn`创建两条记录，配制两个column. 
-->
According to the [UI design](/Tutorial/Basic:-A-Real%2Dworld-Example/Requirement/UI-Design), the data displayed on the list page are `Email/Domain` and `Block Level`. Create two records in the `t_autocoding_UITableColumn` table. configuration as following.

Steps:
3.1. [Config the "Email/Domain" column](#email-domain)
3.2. [Config the "Block Level" column](#block-level)

<br/>

<a id="email-domain"></a>
### 3.1. Config the "Email/Domain" column
<!--
"Email/Domain"列支持点击，点击label跳到编辑页面。配制如下：
-->
"Email/Domain" column can clickable，Click label to jump to the edit page. The configuration as follows：

Script:

![email-domain.PNG](/.attachments/email-domain-9489e1da-6521-43d5-af2d-71ae9523e5d8.PNG)

#### entityUniqueName
<!--
设置“entityUniqueName”为 “blockedSender”。 就是Entity的“uniqueName”，通过这个值把Table的Column配制跟Entity关联。
-->
Set `entityUniqueName` to `blockedSender`. It is the `uniqueName` of [Entity](/Tutorial/Basic:-A-Real%2Dworld-Example/Development/Create-Entity), which associates the configuration of the Table's column with the entity.

#### fieldName
<!--
设置“fieldName”为 “emailOrDomain”。 这个值是"emailOrDomain"字段的name.
-->
Set `fieldName` to `emailOrDomain`. The `name` of `emailOrDomain` [field](/Tutorial/Basic:-A-Real%2Dworld-Example/Development/Create-Entity##create-fields).

#### order
<!--
设置“order”为 “100”。 table中的列根据这个值进行升序。
-->
Set `order` to `100`. The data columns in the table are in ascending order based on this value.

#### width
<!--
设置“width”为 “50%”。 设置显示列的宽度。
-->
Set `width` to `50%`. Set the width of the column.

#### cellComponentType
<!--
设置“cellComponentType”为“4”，这是一个枚举值，"4"表示的是 “link”, 更多的枚举值看这里。根据UI设计, 这列显示成链接。
-->
Set `cellComponentType` to `4`. This is an enumeration value, `4` is `editEntityLink`. Others values, see [here](/References/UI/Multi%2DRow/Table/Columns#cellcomponenttype). According to the [UI design](/Tutorial/Basic:-A-Real%2Dworld-Example/Requirement/UI-Design), this column is displayed as a link.

<br/>

<a id="block-level"></a>
### 3.2. Config the "Block Level" column
<!--
根据UI设计，只要显示“Block Level”的描述信息。
-->
According to the [UI design](/Tutorial/Basic:-A-Real%2Dworld-Example/Requirement/UI-Design), display the description of selected "block level".

Script:

![blocklevel.PNG](/.attachments/blocklevel-8e0e5e79-3ade-41b7-bcf5-55699fa1c028.PNG)

#### entityUniqueName
<!--
设置“entityUniqueName”为 “blockedSender”。 就是Entity的“uniqueName”，通过这个值把Table的Column配制跟Entity关联。
-->

Set `entityUniqueName` to `blockedSender`. It is the `uniqueName` of [Entity](/Tutorial/Basic:-A-Real%2Dworld-Example/Development/Create-Entity), which associates the configuration of the Table's column with the entity.

#### fieldName
<!--
设置“fieldName”为 “blockLevel”。 这个值是"blockLevel"字段的name.
-->
Set `fieldName` to `emailOrDomain`. The `name` of `blockLevel` [field](/Tutorial/Basic:-A-Real%2Dworld-Example/Development/Create-Entity##create-fields).

#### order
<!--
设置“order”为 “200”。 table中的列根据这个值进行升序。
-->
Set `order` to `200`. The data columns in the table are in ascending order based on this value.

#### width
<!--
设置“width”为 “50%”。 设置显示列的宽度。
-->
Set `width` to `50%`. Set the width of the column.

#### cellComponentType
<!--
设置“cellComponentType”为“14”，这是一个枚举值，"14"表示的是 “text”, 更多的枚举值看这里。根据UI设计, 这列显示成文本。
-->

Set `cellComponentType` to `14`. This is an enumeration value, `14` is `text`. Others values, see [here](/References/UI/Multi%2DRow/Table/Columns#cellcomponenttype). According to the [UI design](/Tutorial/Basic:-A-Real%2Dworld-Example/Requirement/UI-Design), this column is displayed as a text.

<br/>

<a id="config-table-operation"></a>
## 4. Config the operation column of the table
<!--
根据UI设计，table右边的操作列包括两个图标：edit 和 delete, 移到图标上显示tooltip. 创建两条记录在`t_autocoding_UITableOperation`。
-->

According to the [UI design](/Tutorial/Basic:-A-Real%2Dworld-Example/Requirement/UI-Design), the operation column on the right side of the table includes two icons: `edit` and `delete`. The mouse hover on the icon to display the tooltip.

<a id="create-icon"></a>
### Preparation：
<!--
这个配制中使用到了两张图标，大多数情况下图标已经存在数据库表“t_autocoding_icon”中，如果不存在，要求UX组根据UI在设计一张图片，图片格式只能是svg,定议好图片的名字， 然后插入到“t_autocoding_icon”表中。
-->

Two icons are used in this tutorial. In most cases, the icon already exists in the `t_autocoding_icon` table. If it doesn't exist, let UX team to design an image according to [UI design](/Tutorial/Basic:-A-Real%2Dworld-Example/Requirement/UI-Design), and the format of image can only be SVG. The name of the image is determined, then add a record to `t_autocoding_icon` table.

Script：

![icon.PNG](/.attachments/icon-a9c1f9d6-d3e0-4b42-8415-07161129d906.PNG)

#### name
<!--
Icon的名字. 这个名字将用到其他地方。
-->

The name of icon. The name will be used elsewhere. in this tutorial, eg: `edit` or `delete` icon.

#### svg
<!--
Svg图片的内容。
-->

The content of Svg.


<br/>

Steps：
4.1. [Config Edit operation](#operation-edit)
4.2. [Config Delete operation](#operation-delete)

<br/>

<a id="operation-edit"></a>
### 4.1. Config Edit operation
<!--
点击Edit图标跳到编辑页面。系统支持跳转到编辑页面的操作。配制如下：
-->
Click the edit icon to jump to the edit page. The AutoCoding supports the operation of jumping to the edit page. The configuration as follows:

Script:

![op-edit.PNG](/.attachments/op-edit-c502e317-2d22-4116-b49e-0820d93fc4fb.PNG)

#### entityUniqueName
设置“entityUniqueName”为 “blockedSender”。 就是Entity的“uniqueName”，通过这个值把Table的operation配制跟Entity关联。

Set `entityUniqueName` to `blockedSender`. It is the `uniqueName` of [Entity](/Tutorial/Basic:-A-Real%2Dworld-Example/Development/Create-Entity), which associates the configuration of the Table's operation with the entity.

#### type
<!--
设置“type”为“1”， 这是个枚举值，“1”表示“Edit”， 点击会跳到编辑页面。 其他的枚举值请看[这里](/References/UI/Multi%2DRow/Table/Operations#type)。
-->
Set `type` to `1`. This is an enumeration value. `1` is `Edit`. Click it jump to the edit page. For other enumeration values, see [here](/References/UI/Multi%2DRow/Table/Operations#type)

#### iconName
<!--
设置“iconName”为“edit”. [Icon](/References/UI/Icon)的名字. 如果使用了新的图标按里的说明。
-->
Set `iconName` to `edit`. the name of [icon](/References/UI/Icon). If a new icon is used, follow the [instructions](#create-icon).


#### tooltip
<!--
设置“tooltip”为“Edit”. 显示tooltip里的文本， 当鼠标移到图标上会出现tooltip.
-->
Set `tooltip` to `Edit`. Display it in toolip, and when the mouse hover on the icon, it will appear.

#### order
<!--
设置“order”为“1”， 决定配制的操作在table的cell里显示顺序，按这个值升序。
-->
Set `order` to `1`. Determine the order in which the configured operations are displayed in the table cell, and is ascending by this value.

<br/>

<a id="operation-delete"></a>
### 4.2. Config Delete operation
<!--
点击Delete图标弹出确认框。系统支持删除的操作。配制如下：
-->
Click the `Delete` icon to pop up the confirmation box. The AutoCoding supports deletion. The configuration as follows:

Script:

![op-d.PNG](/.attachments/op-d-1089195b-2a45-425b-adba-613c203d2597.PNG)

#### entityUniqueName
<!--
设置“entityUniqueName”为 “blockedSender”。 就是Entity的“uniqueName”，通过这个值把Table的Oparation配制跟Entity关联。
-->

Set `entityUniqueName` to `blockedSender`. It is the `uniqueName` of [Entity](/Tutorial/Basic:-A-Real%2Dworld-Example/Development/Create-Entity), which associates the configuration of the Table's operation with the entity.

#### type
<!--
设置“type”为“2”， 这是个枚举值，“2”表示“delete”， 点击时会出现二次确认。 其他的枚举值请看[这里](/References/UI/Multi%2DRow/Table/Operations#type)。
-->
Set `type` to `2`. This is an enumeration value. `2` is `Delete`. A second confirmation will appear when you click. For other enumeration values, see [here](/References/UI/Multi%2DRow/Table/Operations#type)

#### iconName
<!--
设置“iconName”为“delete”. [Icon](/References/UI/Icon)的名字。如果使用了新的图标按里的说明。
-->

Set `iconName` to `delete`. the name of [icon](/References/UI/Icon). If a new icon is used, follow the [instructions](#create-icon).


#### tooltip
<!--
设置“tooltip”为“Delete”. 显示tooltip里的文本， 当鼠标移到图标上会出现tooltip.
-->
Set `tooltip` to `Delete`. Display it in toolip, and when the mouse hover on the icon, it will appear.

#### order
<!--
设置“tooltip”为“2”， 决定配制的操作在table的cell里显示顺序，按这个值升序。
-->
Set `order` to `2`. Determine the order in which the configured operations are displayed in the table cell, and is ascending by this value.

<br/>

<a id="config-table-batchoperation"></a>
## 5. Config the batch operation column of the table
<!--
根据UI设计，table支持批量删除，在table配制中,已经配制table支持批量操作。这里配制Delete按钮。在“t_autocoding_UIBatchOperation”插入一条记录。在例子中，当在列表页面里选中左边的checkbox, table头部就会出现Delete按钮。
-->

According to the [UI design](/Tutorial/Basic:-A-Real%2Dworld-Example/Requirement/UI-Design), the table supports batch deletion. In the table configuration, the configured table supports batch operation. Here config the delete button, create a record in `t_autocoding_UIBatchOperation` table. In the example, when you select the check box on the left in the table, the batch delete button will appear in the table header.

Script:

![batch-delete.PNG](/.attachments/batch-delete-138866af-a015-465a-9749-0afb11d83f04.PNG)

### entityUniqueName
<!--
设置“entityUniqueName”为 “blockedSender”。 就是Entity的“uniqueName”，通过这个值把Table的批量操作配制跟Entity关联。
-->

Set `entityUniqueName` to `blockedSender`. It is the `uniqueName` of [Entity](/Tutorial/Basic:-A-Real%2Dworld-Example/Development/Create-Entity), which associates the configuration of the Table's batch operation with the entity.

### type
<!--
设置“type”为“0”， 这是个枚举值，“0”表示“delete”， 点击时会出现二次确认。 其他的枚举值请看[这里](/References/UI/Multi%2DRow/Table/BatchOperations#type)。
-->
Set `type` to `0`. This is an enumeration value, `0` is `delete`, and a second confirmation will appear when you click. For other enumeration values, see [here](/References/UI/Multi%2DRow/Table/BatchOperations#type).

<br/>

<a id="config-table-btn"></a>
## 6. Config the new button above the table
<!--
根据UI设计，点击table上面的按钮将打开新建页面。在“t_autocoding_UITableComponent”里插入一条记录。
-->
According to the [UI design](/Tutorial/Basic:-A-Real%2Dworld-Example/Requirement/UI-Design), click the button above the table to open the new page. create a record in the `t_autocoding_UITableComponent` table.

Script:

![a-btn.PNG](/.attachments/a-btn-fc7aeaa9-1965-4208-a80f-1b69ae072185.PNG)

### entityUniqueName
<!--
设置“entityUniqueName”为 “blockedSender”。 就是Entity的“uniqueName”。
-->
Set `entityUniqueName` to `blockedSender`. It is the `uniqueName` of [Entity](/Tutorial/Basic:-A-Real%2Dworld-Example/Development/Create-Entity), which associates the configuration of the button with the entity.

### type
<!--
设置“type”为“0”， 这是个枚举值，“0”表示“newButton”， 点击时会跳到新建页面， 其他的枚举值请看这里。
-->
Set `type` to `0`. This is an enumeration value, `0` is `newButton`. click it to open the new page. For other enumeration values, see [here](/References/UI/Multi%2DRow/Table/ComponentsAboveTable#type).

<br/>

<a id="test"></a>
## 7. Test
<!--
经过上面的配制，点击“Blocked Senders”菜单，将进入列表页面，对照UI设计，检查页面布局是否跟设计效果图一致。
-->

After the above configuration, click the "Blocked Senders" menu to enter the list page, check whether the page layout is consistent with the [UI design](/Tutorial/Basic:-A-Real%2Dworld-Example/Requirement/UI-Design).
