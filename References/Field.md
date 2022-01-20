Field describes all fields of an entity, corresponding to the table `t_AutoCoding_Field` table in auto coding database. Contains the following fields: 

- [EntityUniqueName](#EntityUniqueName)
- [Name](#Name)
- [Label](#Label)
- [Type](#Type)
- [IsRequired](#IsRequired)
- [IsUnique](#IsUnique)
- [ReferenceEntityName](#ReferenceEntityName)
- [IsAutoGenerate](#IsAutoGenerate)
- [Default](#Default)
- [MaxLength](#MaxLength)
- [MinLength](#MinLength)
- [Max](#Max)
- [Min](#Min)
- [RegexValidation](#RegexValidation)
- [ReferenceType](#ReferenceType)
- [IfWillBeDeletedWhileReferencedPrimiaryBeingDeleted](#IfWillBeDeletedWhileReferencedPrimiaryBeingDeleted)
- [IsPrimary](#IsPrimary)
- [IfStopDeleteOfReferencedPrimary](#IfStopDeleteOfReferencedPrimary)
- [IfAutoCreateWhenPrimaryCreated](#IfAutoCreateWhenPrimaryCreated)
- [SourceDataForAutoCreating](#SourceDataForAutoCreating)
- [UpdateOccasion](#UpdateOccasion)
- [EffectByFieldName](#EffectByFieldName)
- [ConditionForAvailability](#ConditionForAvailability)
- [UniquenessScopingField](#UniquenessScopingField)
- [AllowedFileExtensions](#AllowedFileExtensions)
- [Suggestion](#Suggestion)
- [ShadowExpression](#ShadowExpression)
- [OptionGroupId](#OptionGroupId)
- [IsBase64EncodeSupported](#IsBase64EncodeSupported)

# EntityUniqueName

`string`

`Required`

Point to a specific entity.

# Name
`string` 

`Required`

The name of the field. It must be named as lower camel case. For example: `title`, `customUrl` or `createdBy`. The name must be consistent with the field name of the table in database. Similarly, the name will be used to the property name of the corresponding entity in the api.
<details>
<summary>Example</summary>

![field-name.png](/.attachments/field-name-6edf906b-4660-4a93-9e19-73b5cb1aa913.png)
</details>
<br>

# Label

`string` 

Default: `""`

By default the contents of the label will be used on the table header of the entity table, as well as in the label for the field value input of current entity's creation or edition form. Support [variable](/References/UI/Variables).
<details>
<summary>Example</summary>

![field-label.png](/.attachments/field-label-d707b5e6-28f1-4d44-a49f-93c1c2b7a4a9.png)
</details>
<br>

# Type

`enum`

`Required`

There are following types of field, which have difference functions.
<details>
<summary>Types</summary>

+ ### guid
  + Enumeration value: `0`
  + Use `uniqueidentifier` in database.
  + Represents the guid field which is typically used as the primary key. 
  + Example:
    + The `id` of the agent.

+ ### selfIncrementId 
  + Enumeration value: `1`
  + Use `int` in database.
  + A self-increment integer type that is used as an entity with integer as the primary key.
  + Example:
    + The `id` of the ticket.

+ ### string
  + Enumeration value: `2`
  + Use `nvarchar` in database.
  + The general string field.You can configure `MaxLength` and `MinLength` to set length constraints and `RegexValidation` to set regular expression constraints. 

+ ### datetime 
  + Enumeration value: `3`
  + Use `datetime2` in database.
  + For datetime format, save utc time in database and use [ISO 8601 Standard](https://en.wikipedia.org/wiki/ISO_8601) for api. When you send parameters, you'd better use the format of iso8601 standard, otherwise it will default to the UTC time zone.
  <details>
  <summary>Example:</summary>

  ![datetimeExample.png](/.attachments/datetimeExample-c8adefb3-5279-4279-a511-8b472c5d7010.png)
  </details>

+ ### email 
  + Enumeration value: `4`
  + Use `nvarchar` in database.
  + For Email address, system will do format checking.  

+ ### integer 
  + Enumeration value: `5`
  + Use `int` in database.
  + For integer type, you can apply maximum/minimum constraint by configuring `Min` and `Max`. 

+ ### float 
  + Enumeration value: `6`
  + Use `decimal` in database.
  + For decimal type, you can apply maximum/minimum constraint by configuring `Min` and `Max`. 

+ ### file 
  + Enumeration value: `7`
  + Use `nvarchar` `image` in database.
  + For file type. When transferring parameters, you need to provide a link that can be downloaded directly from the network (you can upload to the fileservice first, and then fill in the download link of the fileservice). We will download the file according to the link and save it to the database.
  <details>
  <summary>Example:</summary>

  ![image.png](/.attachments/image-e1ddcc48-1ab3-459c-aa38-514fdf1b3dd5.png)
  </details>

+ ### image 
  + Enumeration value: `8`
  + Use `nvarchar` `image` in database.
  + For image type. When transferring parameters, you need to provide a link that can be downloaded directly from the network (you can upload to the fileservice first, and then fill in the download link of the fileservice). We will download the file according to the link and save it to the database.
  <details>
  <summary>Example:</summary>

  ![image.png](/.attachments/image-e1ddcc48-1ab3-459c-aa38-514fdf1b3dd5.png)
  </details>

+ ### date 
  + Enumeration value: `9`
  + Use `nvarchar` in database.
  + For date type such as `2020-10-20`. 
  <details>
  <summary>Example:</summary>

  ![image.png](/.attachments/image-a007ab45-adb6-49ff-9d86-6d2c4850657e.png)
  </details>

+ ### time 
  + Enumeration value: `10`
  + Use `nvarchar` in database.
  + for time type such as `17:00:00`.  24-hour system is always used. 
  <details>
  <summary>Example:</summary>

  ![image.png](/.attachments/image-c7f21e0e-867c-4aa0-9a9f-7e8e52bcfa6a.png)
  </details>

+ ### text 
  + Enumeration value: `11`
  + Use `nvarchar(max)` in database.
  + For long text. 

+ ### reference 
  + Enumeration value: `12`
  + Use `int` `uniqueidentifier` `nvarchar` in database. When field is of reference type, `ReferenceType`, `ReferenceEntityName`,`IfWillBeDeletedWhileReferencedPrimaryBeingDeleted`,`IfStopDeleteOfReferencedPrimary`,`IfAutoCreateDefaultEntityWhenReferencedPrimaryCreated` and `SourceDataForAutoCreatingDefaultEntity` need to be configured. 
  + If this field is mapped to a database field, an `Id` will be added. For example, the category field of an article corresponds to a database table field, which is a categoryId. In the API parameter transfer and return results, an `Id` will also be added to the attribute name
  <details>
  <summary>Example:</summary>

  ![image.png](/.attachments/image-286729d3-65f6-453c-a99c-8a6aeb6210df.png)
  </details>

+ ### bool 
  + Enumeration value: `13`
  + Use `bit` in database.

+ ### enum 
  + Enumeration value: `14`
  + Use `int` in database. 
  + For enum type. Enumeration values are associated to table t_AutoCoding_FieldOption through 'OptionGroupId'.

  <details>
  <summary>Example:</summary>

  ![image.png](/.attachments/image-8dfef5b9-8ee2-47e5-aa38-c14a7320e9d3.png)
  </details>

+ ### password 
  + Enumeration value: `15`
  + Use `nvarchar` in database. 
  + Use to save specific password content, encrypted with AES and automatically decrypted when read. 
  + The implementation of encryption and decryption is as follows：
  ![image.png](/.attachments/image-70dec86e-32c2-47fc-9fdb-59fc5e42d383.png)

  <details>
  <summary>Example:</summary>

  ![image.png](/.attachments/image-c5af5b11-ab50-4987-918a-243a5579b8bf.png)
  ![image.png](/.attachments/image-d335e837-1a77-49e5-8bb1-723913df5d14.png)
  </details>

+ ### order 
  + Enumeration value: `16`
  + Use `int` in database. 
  + Used for records that need to be sorted, such as rule conditions.
  <details>
  <summary>Example:</summary>

  ![image.png](/.attachments/image-74ec1b76-5431-4501-a175-e002190a0b9c.png)
  </details>

+ ### ip 
  + Enumeration value: `17`
  + Use `bigint` in database.
  + We use dotted decimal notation (192.168.1.1) for transmission and use bigint for storage.
  <details>
  <summary>Example:</summary>

  ![image.png](/.attachments/image-9897f9e7-13f3-4475-84e0-8aada7df022c.png)
  ![image.png](/.attachments/image-52aba1aa-4c56-4732-9104-e5a3f330b632.png)
  </details>

+ ### timestamp 
  + Enumeration value: `18`
  + Use `datetime2` in database.
  + For lastModifiedTime field, automatically assign current time when an entity update occurs. 

+ ### stringArray 
  + Enumeration value: `19`
  + Use `nvarchar` in database.
  + For api we use IEnumerable<string> and save in database using json serialization.
  <details>
  <summary>Example:</summary>

  ![image.png](/.attachments/image-e6767706-fea6-447a-9839-231a201ac679.png)
  </details>

+ ### html 
  + Enumeration value: `20`
  + Use `nvarchar` in database.
  + Do validation to prevent JS injection.

+ ### currentAgent 
  + Enumeration value: `21`
  + Use `uniqueidentifier` in database. The current `AgentId` will be assigned automatically.
  + If this field is mapped to a database field, an `Id` will be added. For example, the createBy field of an article corresponds to a database table field, which is a createdById. In the API parameter transfer and return results, an `Id` will also be added to the attribute name.

+ ### multipleReference
  + Enumeration value: `22` 
  + Use `uniqueidentifier` in database. Multiple entities can be associated. The associated entity is controlled by the `EffectByFieldName` field, and the mapping field is the field name plus `Id`. 
  <details>
  <summary>Example:</summary>

  ![image.png](/.attachments/image-07de8720-c54f-4386-9be8-94a8789f6feb.png)
  </details>

+ ### timezone 
  + Enumeration value: `23`
  + Use `nvarchar` in database. timezones list is obtained from `/API/entity/timezones`.

+ ### compressedString 
  + Enumeration value: `24`
  + Use `binary` in database. Compress the field value, compress the input data, and save it into the database in binary.
  <details>
  <summary>Example:</summary>

  ![image.png](/.attachments/image-bf7daf39-859d-4f89-8f74-f2039c559f95.png)
  ![image.png](/.attachments/image-1a610c51-59b4-42d2-86d1-5386cddd231f.png)
  </details>

+ ### json 
  + Enumeration value: `25`
  + Use `nvarchar` in database.

+ ### shadow 
  + Enumeration value: `26`
  + Without mapping the specific fields of entity table, you can assemble the required data through expressions.
  + Two kinds of parameters are supported：
    + config variable：{@config.optionKey}
    + entity member variable：{$fieldName}
  <details>
  <summary>Example:</summary>

  ![image.png](/.attachments/image-1e14be74-8eae-4e95-bf73-5033451dc0a1.png)
  ![image.png](/.attachments/image-300df25d-4947-4e6b-ac2b-1c4e40519f07.png)
  </details>

+ ### long 
  + Enumeration value: `27`
  + Use `bigint` in database.

</details>

# IsRequired

`bool`

Default：`false`

Is Required for HTTP Post and Put and in database operation
<br>

# IsUnique

`bool`

Default：`false`

Is the field unique. The range of uniqueness can be restricted by `UniquenessScopingField`.
<br>

# ReferenceEntityName

`string`

Default: `""`

Available when `type` is `reference`. Point to a specific entity. 

<br>

# IsAutoGenerate

`bool`

Default: `false`

Available when `type` is `guid`.

<br>

# Default

`string`

Default: `""`

This field will be filled with default value when no parameter is passed.
+ @now, use current time for default, only available for `datetime`
+ @{entityName}?{condition} = \${fieldName}, read default value from another entity, for example: @systemDesignTemplate?pageType=$pageType. In the actual query, “$pageType” represents the value of the pageType field under current entity. 

<details>
<summary>Example:</summary>

According to the incoming `pageType`, select the corresponding `default` value and fill in the `body` field.
![image.png](/.attachments/image-0ab09e7b-4c5f-4df5-afa0-eb5cd7f79560.png)
![image.png](/.attachments/image-a2ef5800-e538-4add-896d-776ae71480f8.png)
![image.png](/.attachments/image-2e3aa236-455c-4597-baf1-47200c2495e7.png)
</details>
<br>

# MaxLength

`int`

Default: `0`

Available when [`type`](#type) is `string` `text` `file` `image` `CompressedString` `Email` `EncodedHtml` `Html` `Password`.
<br>

# MinLength

`int`

Default: `0`

Available when [`type`](#type) is `string` `text` `file` `image` `CompressedString` `Email` `EncodedHtml` `Html` `Password`
<br>

# Max

`int`

Default: `0`

Available when [`type`](#type) is `order` `float` `integer`.

<br>

# Min
`int`

Available when [`type`](#type) is `order` `float` `integer`.
<br>

# RegexValidation
`string`

Available when [`type`](#type) is `string` `text` `CompressedString` `Email` `stringArray`. If the regular expression cannot be matched, an error will prompt `suggestion` information.
<details>
  <summary>Example:</summary>

  ![image.png](/.attachments/image-fd0dfeab-e9f3-4b6e-b500-b2f4c71ff8e7.png)
  ![image.png](/.attachments/image-a8b0e631-1be1-4872-8ae4-c71655f4847a.png)
  ![image.png](/.attachments/image-150795cb-f831-4b3a-9420-5093ca6589e6.png)
</details>
<br>

# ReferenceType
`enum`

`oneToOne` `oneToMany` `oneToZeroOrOne`

Available when [`type`](#type) is `reference`.
<br>

# IfWillBeDeletedWhileReferencedPrimiaryBeingDeleted
`bool`

Available when [`type`](#type) is `reference`. default value is false. When the value is true, the parent entity associated with this field will be deleted in cascade.
<details>
  <summary>Example:</summary>

  ![image.png](/.attachments/image-88c659f5-8838-489c-9296-44551578919f.png)
  ![image.png](/.attachments/image-acdb7364-eaaf-4950-9e1d-5d83fbd99f4a.png)
  ![image.png](/.attachments/image-b4b3c8db-4cd3-44dc-8c4f-cd567b4345a9.png)
  ![image.png](/.attachments/image-568f89b2-a07b-4f86-88d4-1c92317f41df.png)
</details>
<br>

# IsPrimary
`bool`

Indicates whether the current field is the primary key of the corresponding entity or not. All multi-instance entities need to define a field as the primary key. In contrast, the primary key does not need to be defined for a single entity because we use `siteId` as the primary key.
<br>

# IfStopDeleteOfReferencedPrimary
`bool`

Available when [`type`](#type) is `reference`. When `IfStopDeleteOfReferencedPrimary`is true and `IfWillBeDeletedWhileReferencedPrimiaryBeingDeleted` is false，the associated entity of this field is a strong reference relationship. If the current entity references the associated entity, the associated entity cannot be deleted.
<details>
<summary>Example:</summary>

The campaignPrechat will reference the taskbot. To ensure that taskbot must exist，it is necessary to ensure that there is no corresponding campaignPrechat record reference when deleting the taskbot.This function can be realized by setting the IfStopDeleteOfReferencedPrimaryof the corresponding reference field to true.
![image.png](/.attachments/image-9370ce53-0b65-4e25-93db-58c9ac0d3dbf.png)
</details>
<br>

# IfAutoCreateWhenPrimaryCreated
`bool`

Available when [`type`](#type) is `reference`. It needs to be used with `SourceDataForAutoCreating`. if `IfAutoCreateWhenPrimaryCreated` is `true`, When a reference entity is created, the data will be obtained according to the template configured in `sourcedataforautocreating` and the current entity will be created automatically.
<br>

# SourceDataForAutoCreating
`string`

Available when [`type`](#type) is `reference` and `IfAutoCreateWhenPrimaryCreated` is `true`. Point to a specific templete entity.
<details>
<summary>Example:</summary>

While creating KB, create default Category, Design CustomPage.
![image.png](/.attachments/image-187c8f95-ce2d-4a00-bed1-44b571d7d41a.png)
Under the new KB, the data initialized by default will be added.
![image.png](/.attachments/image-890f475a-8f3d-44de-a057-51b1910b1333.png)
</details>
<br>

# UpdateOccasion
`enum`

`create` `createAndUpdate` 

Available when [`type`](#type) is `currentAgent`. If value is `create`, the agent information is updated only when the record is created. If value is `createAndUpdate`, the agent information is updated when the record is created or updated. For example: createdBy is `create` and updatedBy is `createAndUpdate`, When agent1 creates a record, Both createdBy and updatedBy will be inserted with the id of agent1; When agent2 updates this record, the value of createdBy is not updated, and the value of updatedBy is updated to the id of agent2.
<br>

# EffectByFieldName
`string`

Available when [`type`](#type) is `multipleReference`. Controls which entity field name the multiplereference points to.
<details>
<summary>Example:</summary>

![image.png](/.attachments/image-07de8720-c54f-4386-9be8-94a8789f6feb.png)
</details>
<br>

# ConditionForAvailability
`string`

The fields in the current entity can be in the condition and logic expression of “and” and “or” are supported. “()” is also supported. When the condition is false, the field is not available, which means the field disappears in HTTP APIs. 
<details>
<summary>Example:</summary>

When ChatWindow satisfies the condition that isbackgrounddisplayed is true and style is classic or circle, `backgroundTexture`field will take effect.
![image.png](/.attachments/image-aaee63f7-1da8-4194-a493-e40076152506.png)
</details>
<br>

# UniquenessScopingField
`string`
 
Name of the field in the current entity. This field is not applicable when IsUnique is false. When IsUnique is True and UniqunessScopingField points to a field, the current field is unique in the scope of the same value in UniquenessScopingField. For example, in GreetingMessage entity in bot, ChannelId is unqiue in the scope of BotId, which means there is only one greeting message for one channel in a bot.
<details>
  <summary>Example:</summary>

  Tag has unique name in KB.
  ![image.png](/.attachments/image-6a4bb3a6-48a1-4dd5-a642-9890b51f52e9.png)
  ![image.png](/.attachments/image-aa300dbc-2557-43a4-abdb-15bcb79cb88b.png)
  ![image.png](/.attachments/image-365a992d-2585-42a5-966e-381882275996.png)
 </details>
<br>


# AllowedFileExtensions
`string[]`

Available when `type` is `file` `Image`. The acceptable format is *.{type}, If only jpg files are allowed, set it to["*.jpg"].
<details>
  <summary>Example:</summary>

  ![image.png](/.attachments/image-13e9eafe-6afa-42d0-803a-560fb6081178.png)
 </details>
<br>

# Suggestion
`string`

Available when `type` is `string` `text` `CompressedString` `Email` `stringArray`. 

When the user enters content that does not match to the regular expression, we want to return more prompt content to the user. These suggestion content will be attached to the error message and returned to the user.
<details>
  <summary>Example:</summary>

  ![image.png](/.attachments/image-fd0dfeab-e9f3-4b6e-b500-b2f4c71ff8e7.png)
  ![image.png](/.attachments/image-a8b0e631-1be1-4872-8ae4-c71655f4847a.png)
  ![image.png](/.attachments/image-150795cb-f831-4b3a-9420-5093ca6589e6.png)
</details>
<br>

# ShadowExpression
`string`

Available when [`type`](#type) is `shadow`. Constructing shadow field with expression.

Two kinds of parameters are supported：
  + config variable：{@config.optionKey}
  + entity member variable：{$fieldName}
  <details>
  <summary>Example:</summary>

  ![image.png](/.attachments/image-1e14be74-8eae-4e95-bf73-5033451dc0a1.png)
  ![image.png](/.attachments/image-300df25d-4947-4e6b-ac2b-1c4e40519f07.png)
  </details>
<br>

# OptionGroupId

`guid`

Available when [`type`](#type) is `enum`. Point to [`FieldOptionGroup`](/References/Field-Option-Group) to define the option value of the enum field.

# IsBase64EncodeSupported

`bool`

Default: `false`

 Available when [`type`](#type) is `string`, `text`, `CompressedString`, `Email`, `EncodedHtml`, `Html` or `Password`. Default is false. In order to avoid some text content being intercepted by WAF, it is necessary to encode the text, you can set `IsBase64EncodeSupported` to `true`. When this value is set to true, the parameter content can be Base64 encoded or not. When the encoded content is passed in, it needs to be preceded by the content `data:text/plain; base64,`; If you don't need to encode, pass in the original text.
<details>
<summary>Example:</summary>

![image.png](/.attachments/image-6c35af08-7b0c-4b58-aaf4-56c85b3d3b58.png)
![image.png](/.attachments/image-67fe8f82-64bc-49c0-b242-41d197792e38.png)
</details>
<br>


