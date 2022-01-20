Describes a button. Includes general info, such as [`type`](#label), [`label`](#label) etc. Below the screenshot is submitting button of livechat's [auto translation](https://dash11.comm100.io/ui/10100000/livechat/settings/autotranslation/) page. 

![button.png](/.attachments/button-87c3f931-5d3b-4c00-b7b2-df1c72d10cfa.png)

## Fields:
- [Type](#type)
- [Label](#Label)
- [CustomButtonActionId](#CustomButtonActionId)
- [ConditionForShowing](#ConditionForShowing)
- [Order](#Order)

<br/>

## Type
`enum`

[`ok (default) 0`](#ok) [`cancel 1`](#cancel) [`apply 2`](#apply) [`customButton 3`](#customButton)

### ok
`value`: `0`
Configure [`Label`](#label) to change the display label. Its function is to save the data in the current form. 

The action after saving is as follows:
- If `IsMultiRecord` is `no`，stay on the current page.
- If `IsMultiRecord` is `yes`.
  - If the relationship with the scoping entity is `oneToOne`, stay on the current page.
  - If the form page comes from the list page, back to the list page.

![form-button-ok.png](/.attachments/form-button-ok-d8a2324d-18fa-4366-acf6-1b73c43432ee.png)

<details>
<summary>Example</summary>

Below the screenshot is submitting button of livechat's [auto translation](https://dash11.comm100.io/ui/10100000/livechat/settings/autotranslation/) page. 

The configurations as following
- entity
  - singleRowUI
    - buttons
      - ok button
        - `type` is `ok`
        - `label` is `Save`

![form-button-ok.png](/.attachments/form-button-ok-d8a2324d-18fa-4366-acf6-1b73c43432ee.png)

</details>

### cancel
`value`: `1`
Configure Label to change the display label. Discard current operations.

The action after the Discard operation as follows:
- If `IsMultiRecord` is `no`，stay on the current page.
- If `IsMultiRecord` is `yes`.
  - If the relationship with the scoping entity is `oneToOne`, stay on the current page.
  - If the form page comes from the list page, back to the list page.

![f-b-cancel.png](/.attachments/f-b-cancel-c36dda49-3018-4d9e-b52d-f45461f0cf49.png)

<details>
<summary>Example</summary>

Below the screenshot is the cancel button of livechat's [auto translation](https://dash11.comm100.io/ui/10100000/livechat/settings/autotranslation/) page. 

The configurations as following
- entity
  - singleRowUI
    - buttons
      - cancel button
        - `type` is `cancel`
        - `label` is `Cancel`

![f-b-cancel.png](/.attachments/f-b-cancel-c36dda49-3018-4d9e-b52d-f45461f0cf49.png)

</details>

### apply
`value`: `2`
Configure [`Label`](#label) to change the display label. If in a new page, Redirect to the edit page when clicking it. If in the edit page, save current data and stay on the current page.

![f-b-a.png](/.attachments/f-b-a-c1373f19-2f33-43f3-97ef-e614c588a6bb.png)

<details>
<summary>Example</summary>

Below screenshot is the "Apply" button of kb's [edit design](https://dash11.comm100.io/ui/10100000/kb/knowledgebases/designs/edit) page. 

The configurations as following
- entity
  - singleRowUI
    - buttons
      - apply button
        - `type` is `apply`
        - `label` is `Apply`

![f-b-a.png](/.attachments/f-b-a-c1373f19-2f33-43f3-97ef-e614c588a6bb.png)

</details>

### customButton
`value`: `3`
It is not provided by autocoding. Provide the Id of [ButtonAction](/References/UI/Button-Action) to `CustomButtonActionId`

![f-b-p.png](/.attachments/f-b-p-997f9b94-9e5d-4765-bbcd-ebf44d0cdbc4.png)

<details>
<summary>Example</summary>

Below screenshot is preview button of kb's [edit design](https://dash11.comm100.io/ui/10100000/kb/knowledgebases/designs/edit) page. Create a record of [ButtonAction](/References/UI/Button-Action) with name 'CKBPreviewDesignButton', put button action Id to [customButtonActionId](#CustomButtonActionName) of button.

The configurations as following
- entity
  - singleRowUI
    - buttons
      - customButton button
        - `type` is `customButton`
        - `label` is `Preview`
        - customButtonAction
          - `type` is `custom`
          - `name` is `CKBPreviewDesignButton`

![f-b-p.png](/.attachments/f-b-p-997f9b94-9e5d-4765-bbcd-ebf44d0cdbc4.png)

</details>

<br />
<br/>

## Label
`string`

Required.

Button’s label. Support [variable](/References/UI/Variables).

<br/>

## CustomButtonActionId
`string`

Optional. Available for [`Type`](#type) is `customButton`

The Id of [ButtonAction](/References/UI/Button-Action)

<br />

## ConditionForShowing
`string` 

Optional.

Config expression in here, show component when the value of the expression is true, [variable](/References/UI/Variables) support.

`Example: @site.feature.domainRestriction==true and $isDomainRestrictionEnabled==true`

<br />

## Order
`int`

it is Ascending, the first button is primary