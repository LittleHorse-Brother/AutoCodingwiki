<!--
页面相关的配制在 “t_autocoding_UIPage” 表里, 这里只能配制一些页面的基本信息， 比如： 页面的地址，`title` 等等。 在这个培训里只介绍例子用到的相关配制，更加详细的配制看这里。
-->
Page-related configuration is in the `t_autocoding_UIPage` table, here only some basic information of the page can be configured, such as page address, ` title ', etc. In this tutorial, we only introduce the relevant configurations used in the example. For more detailed configurations, see [here](/References/UI/Page).
<!--
## Preparation

- 菜单已经创建好了，下面的配制将用到页面的路径。 
- Entity已经配制好
-->
## Preparation
- The `Blocked Senders` has been created, and the following configuration will use the `path` of the page.
- [Entity](/Tutorial/Basic:-A-Real%2Dworld-Example/Development/Create-Entity) is ready

<!--
## Steps

- 创建一条记录在 “t_autocoding_UIPage” 表里
- 测试
-->
## Steps
1. [Create a record in the 't_autocoding_UIPage' table](#create-page)
2. [Test](#test)

<a id="create-page"></a>
<!--
## 1. Create a record in the 't_autocoding_UIPage' table
根据UI设计，这个页面是通过配制出来的，页面的描述信息通过tooltip的方式显示。 下面将详细介绍各个配制项。
-->
According to the [UI design](/Tutorial/Basic:-A-Real%2Dworld-Example/Requirement/UI-Design), this page is configured, and the description information of the page is displayed in **tooltip**. Each configuration item is described in detail below.

Script:

![createPage.PNG](/.attachments/createPage-544134d4-6bd7-43fb-a37d-ad6bbbb5b7ff.PNG)

### title
<!--
设置`title`为`Blocked Senders`. 这个值显示在页面的上面和浏览器的选项卡里。

`title`显示的逻辑：
- 在列表页面, titel的取值顺序为: `Multi-Row.title || Page.title || entity.labelForPlural`
- 在新建页面，默认值是`New {entity.label}`。 titel的取值顺序为: form.title || "New {entity.label}"
- 在编辑页面，默认值是`Edit {entity.label}`。 titel的取值顺序为: form.title || "Edit {entity.label}".
-->
Set `title` to `Blocked Senders`. This value is displayed at the top of the page and in the browser tab.

The logic of `title` display:
- On the list page, the order of the value of the `title`: [Multi-Row](/References/UI/Multi%2DRow#title).title || [page](/References/UI/Page#title).title || [entity](/References/Entity#labelforplural).labelForPlural.
- In the new page, the default value is `New {entity.label}`. The order of the value of the `title`: [form](/References/UI/Single-Row/Form#title).title || "New {[entity](/References/Entity#labelforplural#label).label}".
- On the edit page, the default value is `Edit {entity.label}`. The order of the value of the `title`: [form](/References/UI/Single-Row/Form#title).title || "Edit {[entity](/References/Entity#labelforplural#label).label}"

### path
<!--
设置`path`为`/ticketing/settings/blockedsenders/`, 跟“Blocked Senders”菜单里的`path`保持一致。将根据这个值和`entityUniqueName`找到页面的相关的配制。
-->
Set `path` to `/ticketing/settings/blockedsenders/`. Consistent with `path` in the "Blocked Senders" menu. Find the configuration of the page based on `path` and `entityUniqueName`.

### pageType
<!--
设置`pageType`为`0`. 这项是一个枚举值，页面的配制类型分为下面三种：
- `0` 是 `entity` 表示当前页面内容是可以配制，页面布局不包含选项卡
- `1` 是 `freeStylePage` 表示当前页面内容不能配制，往往页面是定制开发由各个模块
- `2` 是 `pageWithTabs` 页面里包含选项卡，每个选项卡又是一个单独的页面级的配制

根据UI设计，当前的例子应该是`0`,页面布局只包括table和form.
-->
Set `pageType` to `0`. This is an enumeration value. There are three types of page configuration:
- `0` is `entity`, indicating that the current page's content can be configured, and the page layout does not contain **tabs**.
- `1` is `freeStylePage`, which means that the current page content cannot be configured. The page is usually customized and developed by other modules.
- `2` is `pageWithTabs`, and each tab is a separate page-level configuration.

According to the [UI design](/Tutorial/Basic:-A-Real%2Dworld-Example/Requirement/UI-Design), the current example should be `0`. The page layout only includes **table** and **form**.

### entityUniqueName
Set `entityUniqueName` to `blockedSender`. Associate `Entity`'s configuration with `Page`'s configuration by entity's [`uniqueName`](/Tutorial/Basic:-A-Real%2Dworld-Example/Development/Create-Entity#uniquename).

### description
<!--
当前页面的描述信息，一般显示在title的下面，或者以tooltip的形式显示在`title`的后面，怎么显示由`descriptionPosition`决定。根据UI设计，当前例子显示在`title`的后面。

`description`的显示逻辑：
- 在列表页面, description的取值顺序为: Multi-Row.description || Page.description
- 在新建页面，默认值是空。 description的取值顺序为: form.description || ""
- 在编辑页面，默认值是空。 description的取值顺序为: form.description || "".
-->
The description information of the current page is usually displayed below the `title` or as the content of the tooltip displayed behind the `title`. How to display it is determined by the `descriptionPosition`. According to the [UI design](/Tutorial/Basic:-A-Real%2Dworld-Example/Requirement/UI-Design), the current example is displayed after the `title`.

The logic of `description` display:
- On the list page, the order of the value of the `description`: [Multi-Row](/References/UI/Multi%2DRow#description).description || [page](/References/UI/Page#description).description || "".
- In the new page, the default value is empty. The order of the value of the `description`: [form](/References/UI/Single-Row/Form#description).description || "".
- On the edit page, the default value is empty. The order of the value of the `description`: [form](/References/UI/Single-Row/Form#description).description || "".

### descriptionPosition
<!--
设置`descriptionPosition`为`0`· 它决定了`description`的显示位置。它是一个枚举值，有两种场景供选择：
- `0` 是 `tooltip` `description`在tooltip里显示, 当鼠标移到问号图标上面，tooltip就会显示
- `1` 是 `belowTitle` `description`在`title`下面显示

`descriptionPosition`的取值：
- 在列表页面, descriptionPosition的取值顺序为: Multi-Row.descriptionPosition|| Page.descriptionPosition
- 在新建页面，默认值是`0`。 descriptionPosition的取值顺序为: form.descriptionPosition || "0"
- 在编辑页面，默认值是`0`。 descriptionPosition的取值顺序为: form.descriptionPosition || "0".
-->
Set `descriptionPosition` to `0`. It determines the display position of `description`. It is an enumeration value and has two positions to choose from:
- `0` is `tooltip`, the `description` is displayed in the tooltip. When the mouse moves over the question mark, the tooltip will be displayed.
- `1` is `belowTitle`, the `description` is displayed below `title`.

The value of `descriptionPosition`:
- On the list page, the order of the value of the `descriptionPosition`: [Multi-Row](/References/UI/Multi%2DRow#descriptionposition).descriptionPosition || [page](/References/UI/Page#descriptionposition).descriptionPosition || "0".
- In the new page, the default value is `0`. The order of the value of the `descriptionPosition`: [form](/References/UI/Single-Row/Form#descriptionposition).descriptionPosition || "0".
- On the edit page, the default value is `0`. The order of the value of the `descriptionPosition`: [form](/References/UI/Single-Row/Form#descriptionposition).descriptionPosition || "0".

<a id="test"></a>
## 2. Test
<!--
因为页面内容没有配制，比如将要配制的table和form。当点击"Blocked Senders"菜单时，页面会报错提示没有配制的信息。
-->
Because the page content is not configured, such as the **table** is not configured. When you click the "blocked senders" menu, the crashed page will display alone with an error message in the dev console.
