<!--
根据UI设计，新建和编辑页面Form表单布局是一样的，这种情况下只需要配制一个Form就可以了，Form表单编辑的字段是“Email/Domain” 和 “BlockLevel”. 在这里只描述这个例使用到的配制项，更加详细的文档看[这里](/References/UI/Single-Row). 下面简单的介绍一下相关的表。
-->
According to the [UI design](/Tutorial/Basic:-A-Real%2Dworld-Example/Requirement/UI-Design), the layout of new and edit page forms is the same. In this case, you only need to configure a form. The fields of form are `Email/Domain` and `BlockLevel`. Here only describe the configuration items used in this tutorial. For more detailed documents, see [here](/References/UI/Single-Row). The following briefly introduces the related tables.

<br/>

Related tables：
- `t_AutoCoding_UIPageSingleRow`: Config the name of the `Form` associated with the form page.
- `t_AutoCoding_UIForm`: Config `name`, `title` and `description` of `Form`.
- `t_AutoCoding_UIFormButton`: Config the buttons of `Form`.
- `t_AutoCoding_UIFormComponent`: Config the components of `Form`.

`t_AutoCoding_UIPageSingleRow ` and `t_AutoCoding_UIForm` associate with `Entity` by `EntityUniqueName`，`t_AutoCoding_UIFormButton` and `t_AutoCoding_UIFormComponent` associate with `t_AutoCoding_UIForm` by `FormId`。

<br/>

## Preparation
- The [Entity](/Tutorial/Basic:-A-Real%2Dworld-Example/Development/Create-Entity) has been configured.

<br/>

## Steps
1. [Config Single-Row](#single-row)
2. [Config Form](#create-form)
3. [Config Form Button](#create-form-button)
4. [Config Form Component](#create-form-component)
5. [Test](#test)

<br/>

<a id="single-row"></a>
## 1. Config Single-Row
<!--
AutoCoding项目里，通过配制Form可以配制出不同的UI. 也可以给同一个Single-Row配制多个Form, 例如：当前Entity引用其他Entity, 引用的Entity通过drawer来修改。通过Form的name来关联Form的配制。 根据UI设计，新建Blocked Sender页面和编辑Blocked Sender页面是一致的，可以把`NewFormName`和`EditFormName`都设置成同一个值, 在这个例子里，把Form的name定义为“blockedSenderForm” 配制如下.
-->
In the **AutoCoding** project, different UI can be configured by configuring form. Multiple forms can also be configured for the same single row. For example, the current entity refers to other entity, and the referenced entity can be modified in the drawer. The configuration of the form is associated with the form's `name`. According to the UI design, the new page is consistent with the edit page. You can set both 'NewFormName' and 'EditFormName' to the same value. In this example, define the name of the form as "blockedSenderForm" and configure it as follows.

Script:

```SQL
INSERT INTO [dbo].[t_AutoCoding_UIPageSingleRow]
( [EditFormName]
, [NewFormName]
, [EntityUniqueName]
) VALUES
N'blockedSenderForm', N'blockedSenderForm', N'blockedSender'
```

### entityUniqueName
<!--
设置`entityUniqueName`为`blockedSender`，就是`Entity`的`UniqueName`，通过这个将`Single Row`与`Entity`关联起来。
-->
Set `entityUniqueName` to `blockedSender`. It is the `uniqueName` of [Entity](/Tutorial/Basic:-A-Real%2Dworld-Example/Development/Create-Entity), which associates the configuration of the Single-Row with the entity.

### newFormName
<!--
设置`newFormName`为`blockedSenderForm`，Form的名字，在新建页面将使用这个Form的配制。
-->
Set `newFormName` to `blockedSenderForm`. The `name` of Form's configuration, the configuration of this form will be used in the new page.

### editFormName
<!--
设置`editFormName`为`blockedSenderForm`，这个值当作Form配制的name，在编辑页面将使用这个Form的配制。
-->
Set `editFormName` to `blockedSenderForm`. The `name` of Form's configuration, the configuration of this form will be used in the edit page.

<br/>

<a id="create-form"></a>
## 2. Config Form
<!--
因为Blocked Sender的新建页面和编辑页面是一致的，只需要在“t_AutoCoding_UIForm”表里插入一条记录，Form的名字是“blockedSenderForm”
-->
Because the new page of blocked sender is consistent with the edit page, you only need to create a record in the `t_AutoCoding_UIForm` table. The name of the form is "blockedsenderform".

Script:

![form.PNG](/.attachments/form-ee53c853-10b1-4e3b-91b2-7a80a492fa03.PNG)

### EntityUniqueName
<!--
设置`EntityUniqueName`为`blockedSender`，就是`Entity`的`uniqueName`，通过这个将`Form`与`Entity`关联起来。
-->
Set `entityUniqueName` to `blockedSender`. It is the `uniqueName` of [Entity](/Tutorial/Basic:-A-Real%2Dworld-Example/Development/Create-Entity), which associates the configuration of the Form with the entity.

### name
<!--
设置`name`为`blockedSenderForm`，与`Single Row`中的`NewFormName`和`EditFormName`保持一致。
-->
Set `name` to `blockedSenderForm`. It consistent with the `NewFormName` and `EditFormName` of the `Single Row` configuration.

### title
<!--
设置`title`为`''`，表示该`Form`没有指定`Title`，在新建页面显示为`New {{label}}`，在编辑页面显示为`Edit {{label}}`，`label`为关联的`Entity`的`label`。
-->
Set `title` to `''`. It means that the `form` does not specify `title`. It is displayed as `New {label}` on the new page, as `Edit {label}` on the edit page, and the `label` is the `label` of the associated [entity](/Tutorial/Basic:-A-Real%2Dworld-Example/Development/Create-Entity).

### description
<!--
设置`description`为`''`，表示该`Form`没有指定`Description`，故而不显示。
-->
Set `description` to `''`. Indicates that the form does not specify a description, so it is not displayed on the new/edit page.

<br/>

<a id="create-form-button"></a>
## 3. Config Form Button
<!--
根据UI设计，Blocked Sender表单页面需要两个按钮，分别为Save和Cancel，故而需要配置两条数据。AutoCoding自动把form最左边的按钮使用主色调。Save按钮排在Cancel的之前。
-->
According to the UI design, the "Blocked Sender" form page needs two buttons, named `Save` and `Cancel`, so create two records in the `t_AutoCoding_UIFormButton` table. Autocoding automatically uses the primary style to the first button, So the "Save" button comes before "Cancel" button.

### Steps:
&nbsp;&nbsp;&nbsp;&nbsp;3.1. [Config Save Button](#config-save-btn)
&nbsp;&nbsp;&nbsp;&nbsp;3.2. [Config Cancel Button](#config-cancel-btn)

<a id="config-save-btn"></a>
### 3.1. Config Save Button
<!--
根据UI设计，点击“Save”按钮会提交当前的Form.
-->
According to the UI design, click the "save" button to submit the current form.

Script:

![form-btn1.PNG](/.attachments/form-btn1-3a2ef60c-a12a-4d74-abb8-625376a98deb.PNG)

#### formId
<!--
填入已经配制好的`Form`的`Id`，通过这个将`Form Button`与`Form`关联起来。
-->
Fill in the 'ID' of the 'form' that has been configured, and associate form button with form's configuration through this.


#### type
<!--
设置`Type`为`0`，这是一个枚举值，对应关系如下：
- `0`: `save` 用于提交表单数据，成功后如果有列表页面则返回列表页面，否则停留在当前页面。
- `1`: `cancel`  用于丢弃当前表单修改的数据，如果有列表页面则返回列表页面，否则停留在当前页面。
- `2`: `apply` 用于提交表单数据，成功后如果当前页面为新建页面则跳-转到编辑页面，否则停留在当前页面。
- `3`: `custom` 用于自定义表单按钮. 详细的介绍看这里。
-->

Set `type` to `0`. This is an enumeration value, the enumeration values as follows:
- `0`: `save` It is used to submit form data. If there is a list page, it will return to the list page after success, otherwise it will stay on the current page.
- `1`: `cancel`  Used to discard the modified data of current form. If there is a list page, it will return to the list page, otherwise it will stay on the current page.
- `2`: `apply` It is used to submit form data. If the current page is a new page, it will jump to the edit page, otherwise it will stay on the current page.
- `3`: `custom` Use to customize form buttons, see [here](/References/UI/Single-Row/Form/Button#type) for a detailed introduction

#### label
<!--
设置`label`为`Save`，表单按钮上显示的文字。
-->
Set `label` to `Save`. The text displayed on the form button.

#### order
<!--
设置`order`为`1`，表单按钮的顺序，按升序由左到右显示。
-->
Set `order` to `1`. The order of the form buttons, display them from left to right in ascending order.

<a id="config-cancel-btn"></a>
### 3.2. Config Cancel Button
<!--
根据UI设计，点击“Cancel”按钮跳回列表页面。
-->
According to the UI design, click the "Cancel" button to jump back to the list page.

Script:

![form-btn2.PNG](/.attachments/form-btn2-eab908ea-d7d9-4c4c-920a-22f595d91a15.PNG)

#### formId
<!--
值是前面创建的`Form`的`Id`，通过这个将`Form Button`与`Form`关联起来。
-->
Fill in the 'ID' of the 'form' that has been configured, and associate form button with form's configuration through this.

#### type
<!--
设置`type`为`1`，这是一个枚举值，对应关系如下：
- `0`: `save` 用于提交表单数据，成功后如果有列表页面则返回列表页面，否则停留在当前页面。
- `1`: `cancel`  用于丢弃当前表单修改的数据，如果有列表页面则返回列表页面，否则停留在当前页面。
- `2`: `apply` 用于提交表单数据，成功后如果当前页面为新建页面则跳-转到编辑页面，否则停留在当前页面。
- `3`: `custom` 用于自定义表单按钮。
-->

Set `type` to `1`. This is an enumeration value, the enumeration values as follows:
- `0`: `save` It is used to submit form data. If there is a list page, it will return to the list page after success, otherwise it will stay on the current page.
- `1`: `cancel`  Used to discard the modified data of current form. If there is a list page, it will return to the list page, otherwise it will stay on the current page.
- `2`: `apply` It is used to submit form data. If the current page is a new page, it will jump to the edit page, otherwise it will stay on the current page.
- `3`: `custom` Use to customize form buttons, see [here](/References/UI/Single-Row/Form/Button#type) for a detailed introduction

#### label
<!--
设置`label`为`Cancel`，表单按钮上显示的文字。
-->
Set `label` to `Cancel`. The text displayed on the form button.

#### Order
<!--
设置`Order`为`2`，表单按钮的顺序，按升序由左到右显示。
-->
Set `order` to `2`. The order of the form buttons, display them from left to right in ascending order.

<br/>

<a id="create-form-component"></a>
## 4. Config Form Component
<!--
根据UI设计，Blocked Sender表单页面需要三个组件，分别为input、subGroupTitleText和radioGroup，三个组件在同一个卡片里，并且页面只有一个卡片。AutoCoding会把所的组件排在同一个卡片里，如果没有配制groupBegin和groupEnd组件的场景，更详细的配制看[这里](/References/UI/Single-Row/Form/Component)。
-->
According to the UI design, the "Blocked Sender" form page needs three components: `input`, `subGroupTitleText` and `radioGroup`. The three components are in the same card, and the page has only one card. Autocoding will arrange all components in the same card, if there is no scene of configuring `groupBegin` and `groupEnd` components, see [here](/References/UI/Single-Row/Form/Component) for more details.

<a id="column-span"></a>
### Example about `ColumnSpan` layout：
Conditions for new line:
1. The sum of the "columnSpan" values of all components exceeds 12, and the last component will be in the new line.
2. There is a "newline" component in the components, and the components after it will be in the new line.

Example:
[Input, ColumnSpan 6 ]
[Input, ColumnSpan 7 ] [NewLine]
[Input, ColumnSpan 4] [Select, ColumnSpan 6 ]
[Check box, ColumnSpan 8 ] [Input, ColumnSpan 4]
[Select, ColumnSpan 4]
New group will restart accumulate column spans

### Steps:
&nbsp;&nbsp;&nbsp;&nbsp;4.1. [Config "Email/Domain" input](#config-component-input)
&nbsp;&nbsp;&nbsp;&nbsp;4.2. [Config "Block Level" subGroupTitleText](#config-component-subgrouptitletext)
&nbsp;&nbsp;&nbsp;&nbsp;4.3. [Config "Block Level" radio group](#config-block-level-radiogroup)

<a id="config-component-input"></a>
### 4.1. Config "Email/Domain" input

Script:

![column1.PNG](/.attachments/column1-8c48ff32-95f7-4efc-8cbd-3fcf7f404640.PNG)

#### formId
<!--
已经配制好的`Form`的`Id`，通过这个将`Form Component`与`Form`关联起来。
-->

Fill in the 'ID' of the 'form' that has been configured, and associate form component with form's configuration through this.

#### componentType
<!--
设置`componentType`为`4`，这是一个枚举值，`4`表示当前组件为`input`。 其他的枚举值看这里。
-->

Set `componentType` to `4`. This is an enumeration value, `4` is `input`. For other enumeration values, see [here](/References/UI/Single-Row/Form/Component#componenttype).

#### fieldOrEntityName
<!--
设置`fieldOrEntityName`为`emailOrDomain`，就是Entity filed的名字。
-->
Set `fieldOrEntityName` to `emailOrDomain`. This is [field](/Tutorial/Basic:-A-Real%2Dworld-Example/Development/Create-Entity#create-fields)'s name or boundary entity's name. In this tutorial, it is field's name. The detailed introduction view [Here](/References/UI/Single-Row/Form/Component#fieldorentityname).

#### helperText
<!--
设置`helperText`为`Examples: someone@example.com or example.com`，帮助文本，默认显示在组件的下面。 可以配制帮助本显在tooltip里，跟在组件的后面。详细的文档看这里
-->
Set `helperText` to `Examples: someone@example.com or example.com`. The help text is displayed below the component by default. You can configure the help to be displayed in the tooltip, following the component. [Here](/References/UI/Single-Row/Form/Component#helperposition) for a detailed introduction.

#### order
<!--
设置`order`为`1`，表单组件的顺序，按升序由上到下显示。
-->
Set `order` to `1`. The order of form components, displayed from top to bottom in ascending order.

#### columnSpan
<!--
设置`columnSpan`为6，表示当前组件渲染的宽度为50%。关于columnSpan的排版看这个[例子](#column-span)。
-->
Set `columnSpan` to `6`, indicating that the width of the current component rendering is 50 percent. Look at this [example](#column-span) for the layout of `columnSpan`. 

#### label
<!--
设置`label`为`Email/Domain`，表示当前input的placeholder为`Email/Domain`。
-->
Set `label` to `Email/Domain`. Use it as component label.

#### messageForInvalidFormat
<!--
设置`messageForInvalidFormat`为`Email/Domain is invalid.`，格式错误提示， 在这个例了，当输入错的格式就会显示在input下面。
-->
Set `messageForInvalidFormat` to `Email/Domain is invalid.`. Format error prompt, in this tutorial, when the wrong format is entered, it will be displayed under input.

<a id="config-component-subgrouptitletext"></a>
### 4.2. Config "Block Level" subGroupTitleText

Script:

![form-c1.PNG](/.attachments/form-c1-10b288ce-f42d-4b1e-8ea5-6cc486b501ea.PNG)

#### formId
<!--
已经配制好的`Form`的`Id`，通过这个将`Form Component`与`Form`关联起来。
-->
Fill in the 'ID' of the 'form' that has been configured, and associate form component with form's configuration through this.

#### componentType
<!--
设置`componentType`为`47`，这是一个枚举值，`47`表示当前组件为`subGroupTitleText`。
-->
Set `componentType` to `47`. This is an enumeration value, `47` is `subGroupTitleText`. For other enumeration values, see [here](/References/UI/Single-Row/Form/Component#componenttype).

#### componentText
<!--
设置`componentText`为`Block Level`，表示当前组件显示的内容为`Block Level`。
-->
Set `componentText` to `Block Level`. Indicating that the component displays `Block Level`.

#### order
<!--
设置`order`为`50`，表单组件的顺序，按升序由上到下显示。
-->
Set `order` to `50`. The order of form components, displayed from top to bottom in ascending order.

#### columnSpan
<!--
设置`columnSpan`为12，表示当前组件渲染的宽度为100%。 关于columnSpan的排版看这个[例子](#column-span)。
-->
Set `columnSpan` to `12`, indicating that the width of the current component rendering is 100 percent. Look at this [example](#column-span) for the layout of `columnSpan`. 

<a id="config-block-level-radiogroup"></a>
### 4.3. Config "Block Level" radio group

Script:

![fordd.PNG](/.attachments/fordd-41641f1c-bc75-41bc-a264-eb1250edc194.PNG)

#### formId
<!--
已经配制好的`Form`的`Id`，通过这个将`Form Component`与`Form`关联起来。
-->
Fill in the 'ID' of the 'form' that has been configured, and associate form component with form's configuration through this.

#### componentType
<!--
设置`componentType`为`8`，这是一个枚举值，`8`表示当前组件为`radioGroup`。
-->
Set `componentType` to `8`. This is an enumeration value, `8` is `radioGroup`. For other enumeration values, see [here](/References/UI/Single-Row/Form/Component#componenttype).

#### fieldOrEntityName
<!--
设置`fieldOrEntityName`为`blockLevel`，就是`Entity Field`里面的`blockLevel`。
-->
Set `fieldOrEntityName` to `blockLevel`. This is [field](/Tutorial/Basic:-A-Real%2Dworld-Example/Development/Create-Entity#create-fields)'s name or boundary entity's name. In this tutorial, it is field's name. The detailed introduction view [Here](/References/UI/Single-Row/Form/Component#fieldorentityname).

#### order
<!--设置`order`为`100`，表单组件的顺序，按升序由上到下显示。
-->
Set `order` to `100`. The order of form components, displayed from top to bottom in ascending order.

#### isIndent
<!--
设置`isIndent`为`true`. 如果为ture， 这个组件会缩进，默认值是false.
-->
Set `isIndent` to `true`. If true, the component will be indented. The default value is false.

#### ColumnSpan
<!--
设置`ColumnSpan`为12，表示当前组件渲染的宽度为100%。 关于columnSpan的排版看这个[例子](#column-span)。
-->
Set `columnSpan` to `12`, indicating that the width of the current component rendering is 100 percent. Look at this [example](#column-span) for the layout of `columnSpan`. 

<br/>

<a id="test"></a>
## 5. Test
- Click "New Blocked Sender" on the list page to jump to the new page. Check whether it meets the requirements according to the UI design
- Click the "Edit" icon in the table to jump to the edit page. Check whether it meets the requirements according to the UI design.