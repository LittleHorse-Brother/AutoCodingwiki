<!--
根据UI设计，下面的配制只在'Setting'菜单下面加一个"Blocked Senders"菜单。这里只描述这个例子用的相关的配制，更加详细的配制看这里。 简单的描述配制菜单相关的表`t_autocoding_level1Menu`, `t_autocoding_level2Menu` 和 `t_autocoding_level2Submenu`. 

表相关的描述：
- `t_autocoding_level1Menu` 这里配制的菜单是各个模块的入口
- `t_autocoding_level2Menu` 这里配制的菜单模块提供的功能
- `t_autocoding_level2Submenu` 这里配制的菜单是功能的细分

`t_autocoding_level1Menu` 和 `t_autocoding_level2Menu` 是one-to-many的关系，通过`t_autocoding_level2Menu`表中Level1MenuId`字段把menu1 和 menu2关联。 `t_autocoding_level2Menu`和`t_autocoding_level2Submenu`也是one-to-many的关系，通过`t_autocoding_level2Submenu`表中的`Level2MenuId`字段把menu2和menu2字菜单关联。
-->
According to the [UI design](/Tutorial/Basic:-A-Real%2Dworld-Example/Requirement/UI-Design), the following configuration only adds a "blocked senders" menu under the "setting" menu. Here only describes the relevant configuration used in this tutorial. For more detailed configuration, see [here](/References/UI/Menu). Related tables as `t_ autocoding_ level1Menu`, `t_ autocoding_ Level2Menu` and `t_ autocoding_ level2Submenu`.

Table related Description:
- `t_autocoding_level1Menu` The menu configured here is the entrance of each module
- `t_autocoding_level2Menu` The features provided by the module configured here
- `t_autocoding_level2Submenu` The menu configured here is a subdivision of feature

`t_autocoding_level1Menu` and `t_autocoding_level2Menu` are one-to-many relationships. `t_autocoding_level1Menu` and `t_autocoding_level2Menu` are associated through the `Level1MenuId`. `t_autocoding_level2Menu` and `t_autocoding_level2Submenu` are also one-to-many relationships. `t_autocoding_level2Menu` and `t_autocoding_level2Submenu` are associated through the `Level2MenuId` field.

## Preparation
- The 'Settings' menu is ready
- The [Entity](/Tutorial/Basic:-A-Real%2Dworld-Example/Development/Create-Entity) has been configured

## Steps:
1. [Create the 'Blocked Senders' menu](#create-blocked-senders)
2. [Test the menu](#test)

<a id="create-blocked-senders"></a>
## 1. Create the 'Blocked Senders' menu
<!--
“Blocked Senders”菜单是“Settings”菜单的子菜单，只要在“t_autocoding_level2Submenu”里加一条记录。
-->
The `Blocked Senders` menu is a submenu of the `Settings` menu, as long as creating a record in the `t_autocoding_level2Submenu`.

Script as following:

![submenu.PNG](/.attachments/submenu-0fd13c33-bb88-4ce8-967e-3073a3f24cd4.PNG)

### label
<!--
设置`label`为`Blocked Senders`. 它作为菜单的label显示，简短描述菜单的功能。
-->
Set `label` to `Blocked Senders`. It is displayed as the label of the menu and briefly describes the function of the menu.

### path
<!--
设置`path`为`/ticketing/settings/blockedsenders/`. 指的是页面的相对路径，这里不区分大小写的，通过反斜杆把每一段隔开，系统只支持三级菜单，在文档中用"level1Menu", "level2Menu" 和 "level2SubMenu"表示菜单相应的配制。

在当前例子里，完整的url是“{basePath}/ticketing/settings/blockedsenders/”
- basePath: 格式如“{domain}/ui/{siteId}”。例如：“https://autoportal.comm100dev.io/ui/1000”
- ticketing: 这是level1Menu的application对应的值。 如当前的页面的路径匹配这一段，level1Menu会被选中。
- settings: 表示Level2Menu的`name`。 如当前的页面的路径匹配这一段, "Setting"菜单会被展开。
- blockedsenders: 是自定义的，最好与当前的页面的功能相关。如当前的页面的路径匹配这一段, 这个菜单会被选中。

更详细的配制看[这里](/References/UI/Menu/Level-2-Menu#path)
-->
Set `path` to `/ticketing/settings/blockedsenders/`. It refers to the relative path of the page. It is not case sensitive. Each segment is separated by `/`. The AutoCoding only supports three-level menus. In the document, the menu configuration is represented by "level1menu", "level2menu" and "level2submenu".

In the current example, the complete URL is `{basePath}/ticketing/settings/blockedsenders/`.
- `basePath`: The format is `{domain}/ui/{siteId}`. eg: `https://autoportal.comm100dev.io/ui/1000`
- `ticketing`: This is the value corresponding to the application of level1menus. If the path of the current page matches this section, level1Menu will be selected.
- `settings`:Tthe `name` of level2Menu. If the path of the current page matches this section, the "Setting" menu will be expanded.
- `blockedsenders`: It's custom, preferably related to the function of the current page. If the path of the current page matches this section, this menu will be selected.

See [here](/References/UI/Menu/Level-2-Menu#path) for more details.

### level2MenuId
<!--
设置`level2MenuId`为"Settings"菜单的`id`.
-->
Set `level2MenuId` to the `id` of the `Settings` menu.

### order
<!--
设置`order`为`70`. 它是确定菜单在“Settings”菜单的子菜单列表中的位置，根据这个值来进行升序排序。
-->
Set `order` to `70`. It determines the position of the menu in the submenu list of the `Settings` menu, Sort it in ascending order according to this value.

<a id="test"></a>
## 2. Test the menu
<!--
对照UI设计，检查“Blocked Senders”菜单的位置是否对。
-->
Check the location of the "Blocked Senders" menu against the [UI design](/Tutorial/Basic:-A-Real%2Dworld-Example/Requirement/UI-Design). Clicking the menu will go to the 404 page, because [page](/Tutorial/Basic:-A-Real%2Dworld-Example/Development/Create-Page) is not configured.