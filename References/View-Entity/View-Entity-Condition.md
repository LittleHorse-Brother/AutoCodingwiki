A View Entity Condition is a condition subset of a View Entity. View Entity Condition corresponding to the table `t_AutoCoding_ViewEntityCondition` table in auto coding database. Contains the following fields: 

- [FieldName](#FieldName)
- [Value](#Value)

# FieldName
`string`

Required: Yes

The filed from the base entity.
# Value
`string`

Required: Yes

“=” operator will be used.

<details>
<summary>Example</summary>

There are a lot of data in SecureFormField under LiveChat. According to isVisible, IsSystem can be divided into fields of multiple manifestations. At this time, by configuring the view entity secureFormFieldView to make the base entity secureFormField, and adding the filter condition isVisible to true and IsSystem to false, a logical entity secureFormFieldView appears, thereby shielding the database implementation details and simplifying the effect of interface calls. 

The filter conditions for view entity data are: isVisible is true, IsSystem is false.
![图片.png](/.attachments/图片-8a6e6047-1fcd-4a4f-997e-a0a9966d2ddd.png)

There is a piece of data in the SecureFormField table that isVisible and IsSystem are false.
![图片.png](/.attachments/图片-96e3aa1d-0a43-4d5e-90ce-46c1f29d213c.png)

Through the secureFormFieldView interface, only data that meets the conditions can be obtained, and the data whose isVisible and IsSystem are both false does not appear in the results.
![图片.png](/.attachments/图片-97bf3475-a902-4fbd-bc2b-182182152324.png)

</details>
