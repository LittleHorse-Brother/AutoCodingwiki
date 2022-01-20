Entity API Post Action Action defines which fields will be affected by the sub-operations of the entity post method, and why the value of the field should be set. Entity API corresponding to the table `t_AutoCoding_APIPostActionAction` table in auto coding database. Contains the following fields: 

- [Field ](#Field )
- [Value ](#Value )

# Field
`string`

Required: Yes

Which field will be affected by the sub-operation.

# Value
`string`

Required: Yes

The field affected by the quilt operation, what value should be set to.

<details>
<summary>Example</summary>

roleConfig has a switch on the interface to turn on/off the role function, so two sub-operations are defined in roleConfig to set the isEnable field in roleConfig to true/false.
![图片.png](/.attachments/图片-debf3228-f528-46d7-8de7-475a3f3db874.png)
![图片.png](/.attachments/图片-99b0c82c-3115-4d80-be1a-a8120900f2dc.png)

Call the sub-operation, set the value of the isEnable field, note that no data is passed in at this time.
![图片.png](/.attachments/图片-1e9c1fa6-797c-4336-9919-f40185412afc.png)

</details>