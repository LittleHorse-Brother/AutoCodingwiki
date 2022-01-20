Some entity data cannot be deleted under certain conditions. When the data meets the conditions defined here, it can be deleted. Entity API Delete Condition corresponding to the table t_AutoCoding_APIDeleteCondition table in auto coding database. Contains the following fields:


- [FieldName](#FieldName)
- [Value](#Value)
- [NotMetErrorMessage](#NotMetErrorMessage)

# FieldName
`string` 

Required: Yes

Which field is used to determine whether the data can be deleted. 

# Value
`string` 

Required: Yes

When the value of the field, the data can be deleted. 

<details>
<summary>Example</summary>

The role can only be deleted when it is user-defined, that is, when the type is 2, so the deletion condition is defined in delete condition.
![图片.png](/.attachments/图片-586d8184-2744-4b81-aef7-67b3a0ac6254.png)

When deleting a custom role, the data meets the defined deletion conditions and is deleted normally.
![图片.png](/.attachments/图片-ade747b9-a611-42ef-a84a-8642c2552791.png)

</details>

# NotMetErrorMessage
`string` 

Required: Yes

When the judgment conditions are not met, the data cannot be deleted, but when the caller tries to delete the data, it should report what error to remind the user.

<details>
<summary>Example</summary>

The role can only be deleted when it is user-defined, that is, when the type is 2, so the deletion condition is defined in delete condition.
![图片.png](/.attachments/图片-586d8184-2744-4b81-aef7-67b3a0ac6254.png)

When trying to delete the role of admin, because the data does not meet the defined deletion conditions, an error cannot be deleted.
![图片.png](/.attachments/图片-d5e2a572-544b-49bb-8e47-decc0de591be.png)

</details>