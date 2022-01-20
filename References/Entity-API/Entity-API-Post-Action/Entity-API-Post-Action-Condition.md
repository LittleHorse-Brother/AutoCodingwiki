Entity API Post Action Condition defines the conditions under which the sub-operations of the entity post method should be successfully executed. Entity API corresponding to the table `t_AutoCoding_APIPostActionCondition` table in auto coding database. Contains the following fields: 

- [Field ](#Field )
- [Value ](#Value )

# Field
`string`

Required: Yes

The sub-operation will determine the operation can be executed according to which field.

# Value
`string`

Required: Yes

When the sub-operation judges that the operation can be executed, what should be the value.

<details>
<summary>Example</summary>

AutoTranslation has a switch on the interface to turn on/off the autoTranslation function, so two sub-operations are defined in autoTranslationConfig to set the isEnable field in autoTranslationConfig to true/false.
![图片.png](/.attachments/图片-291942bb-b5e7-4806-8e7a-5d78068544b7.png)
![图片.png](/.attachments/图片-d909eb7d-015b-442a-bbee-26d89eb72f58.png)

autoTranslationConfig hopes that its opening operation can be called normally only when the isEnable field is false, otherwise an error will be reported, so this sub-operation defines the operating conditions, and the condition is that the isEnable field is false.
![图片.png](/.attachments/图片-eb06a9c0-3e91-4ab7-819d-b9b334b15c95.png)

When the condition is met, the sub-operation is called, and it succeeds.
![图片.png](/.attachments/图片-13e6c655-e1ab-42dc-a8f5-5a82ab813543.png)

When the condition is not met, an error will be reported when calling the sub-interface.
![图片.png](/.attachments/图片-e05a8b50-235c-443e-80fd-420013424ed9.png)

</details>