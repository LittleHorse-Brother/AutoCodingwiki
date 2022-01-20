These entities are under the aggregation of the current entity as an aggregate root. These entities need to be included when creating/updating the current entity, corresponding to the table `t_AutoCoding_EntityInBoundary` table in auto coding database. Contains the following fields: 

- [EntityName](#EntityName)
- [PrimaryEntityUniqueName](#PrimaryEntityUniqueName)
- [IsRequired](#IsRequired)
- [ConditionForAvailability](#ConditionForAvailability)

# EntityName

`string`

Required

Name of the in-boundary entity. 

# PrimaryEntityUniqueName

`string`

Required

The unique name of the main entity, used to confirm which entity the current Entity Inboundary configuration belongs to.

<details>
<summary>Example</summary>

We know that Field and FieldOption are a combination relationship, and FieldOption that is separated from Field has no meaning, so we can set the FieldOption to be processed at the same time when processing Field. 

If you want to operate fieldOption while operating the field, perform the following configuration: 

  - entityName: `fieldOption`
  - primaryEntityUniqueName: `field`

![图片.png](/.attachments/图片-eca99f40-5bf6-4313-b970-2ecaa28f269e.png)

</details>

# IsRequired

`bool`

Default: `false`

Indicate that this entity is required when update/create primary entity. If you want to require the corresponding in-boundary entity to be passed in when creating an entity, set IsRequired to true, and the framework will automatically verify whether the passed in-boundary entity exists and is legal. 

<details>
<summary>Example</summary>

In the relationship between Field and FieldOption, if we need to set FieldOption as necessary (for example, when creating a Field of type DropDownList). We can set IsRequired to `true`. 

When IsRequired is true, if the corresponding sub-entity data is not transmitted when the api is called for operation, the system will report an error 

![图片.png](/.attachments/图片-ddb9b61a-f787-430c-ae2b-97086bbe3b3b.png)

When IsRequired is true and the incoming in-boundary entity data is empty, an error will also be reported 

![图片.png](/.attachments/图片-17873dfe-6c0e-4d4a-9449-04a5ff9e5a1e.png)
<br>

When IsRequired is true and the data of the corresponding in-boundary entity is correctly passed in, it can succeed

![图片.png](/.attachments/图片-824820d7-e22b-4182-b08c-38ba7a18af0a.png)

When IsRequired is false, the framework will automatically process the data according to the incoming in-boundary entity 

The article has an in-boundary whose IsRequired is false and the name is tag 

![图片.png](/.attachments/图片-8f3475e0-365e-473a-bb68-129948fd3b6e.png)

When IsRequired is false, there is no need to pass in the data of the corresponding in-boundary entity 

![图片.png](/.attachments/图片-483f36c0-e081-4a6e-81b3-ce5f4c2748a0.png)

</details>

# ConditionForAvailability

`string`

Default: `""`

Indicates that this in-boundary entity will be available under certain conditions.

<details>
<summary>Example</summary>

In the relationship between Field and FieldOption, FieldOption only needs to be filled in when FieldType is dropdownList, radioBox and checkboxList, so we can control it through the configuration item ConditionForAvailability and configure it as `$type=="radioBox" or $type=="dropdownList" or $type=="checkboxList"` to meet the above requirements. In addition, the verification of IsRequired will be carried out on the basis of satisfying this condition. 

As in the following example, when the parameters passed in do not meet the condition of ConditionForAvailability, even if IsRequired is true, you can create a Field without passing in FieldOption.

![图片.png](/.attachments/图片-7858e167-a775-4dd9-93a6-592b7de02b47.png)
</details>

# Others

- The data of the in-boundary entity in the parent entity data can be an object array or an object, depending on the relationship between the two: one-to-many transmission array, one-to-one transmission object


# Difference during update 
- One-to-many, many-to-many 
![图片.png](/.attachments/图片-13287151-79f3-4e11-bc07-33158fe41ab3.png)
  - Part of the data of the in-boundary entity already exists in the database. For this part of the data, do update:
![图片.png](/.attachments/图片-aa18aff0-e610-4da1-acbd-3c99006bfb55.png)
![图片.png](/.attachments/图片-ae1eb68e-b7f6-40e9-aaed-ffb22f1dfa9a.png)
<br>

  - Part of the in-boundary entity data itself is in the parent entity of the database. At the time of this update, it no longer exists in the parent entity. For this part of data, delete:
![图片.png](/.attachments/图片-f7c82582-0513-4db5-a78c-68093b8da6e1.png)
<br>

  - Part of the in-boundary entity data does not exist in the database. For this part of the data, do create: 
![图片.png](/.attachments/图片-9a3d254d-9e58-4ab7-858b-d48e01150557.png)
![图片.png](/.attachments/图片-b1cd99c3-46a1-4b02-95c9-df731a5c51a9.png)
<br>

- One to one 
  - The data of the in-boundary entity already exists. During update, if the in-boundary entity passes in null, the data of the in-boundary entity will be deleted. 

  - The data of the in-boundary entity already exists. If the in-boundary entity is correctly passed in during update, then the data of the in-boundary entity will be updated. 

  - The data of the in-boundary entity does not exist, and the data of the in-boundary entity is created if the in-boundary entity is correctly passed in during update 