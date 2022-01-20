Entity API Get Condition defines which conditions must be met by the get method of the entity interface to return data. Entity API Get Condition corresponding to the table `t_AutoCoding_APIGetCondition` table in auto coding database. Contains the following fields: 

- [Name](#Name)
- [EntityUniqueName](#EntityUniqueName)
- [Operator](#Operator)
- [IsRequired](#IsRequired)
- [Fields](#[N]-Fields)

# Name
`string`

Required: Yes

Use this name as query string key

# EntityUniqueName
`string`

Required: Yes

Unique name of the entity. The value of this field is used where the entity is referenced in all auto coding ER.

# Operator
`enum`

Required: Yes

Allows: `equal` `like` `fulltext` `between` `notEquals` `notLike`

### equal

The value in database is `0`.

The EQUAL operator is used to select specific values. 

### like

The value in database is `1`.

The LIKE is used to extract records where a particular pattern is present. 

### fulltext

The value in database is `2`.

The FULLTEXT is used to search the data in the full-text index library.

### between

The value in database is `3`.

The BETWEEN operator is used to select values within a given range. 

### notEquals

The value in database is `5`.

### notLike

The value in database is `6`.

<details>
<summary>Equal Example</summary>

chatbotEntity needs to return the data of a certain chatbot, so it is configured with an equal condition, the name is chatbotid.
![图片.png](/.attachments/图片-64554051-6680-491b-abe9-0e9244387e74.png)

When this condition is attached to the get request, the result that matches the value of the corresponding field will be returned.
![图片.png](/.attachments/图片-03f554e0-d355-4e90-b484-6fbe2a86015d.png)

</details>
<br>

<details>
<summary>Like Example</summary>

The search function of auditLog needs to search the actionSummary field, so it is configured with a like condition, the name is keywords, and the actionSummary field is matched. 
![图片.png](/.attachments/图片-1d95eb55-bc8a-4eca-a221-a297c01da108.png)

When the get request, with this condition, it will go to the corresponding field to do like matching.
![图片.png](/.attachments/图片-38b7dcc3-d2ab-48c1-b6e6-9ae7fdd39c78.png)

</details>
<br>

<details>
<summary>Fulltext Example</summary>

When searching for an article, you need to perform a full-text index search to match the two fields of title and body. In HTTPGetCondition, configure the name as keywords, and the fields as title and body. 
![图片.png](/.attachments/图片-72c0bb0c-6cd1-46dc-94db-ae02e5fc1062.png)

In the get request, pass in the name and its corresponding value, it will be matched in the title and body, and the corresponding data will be returned.
![图片.png](/.attachments/图片-3a1a289c-e94d-40a8-baf6-ae54dc7609a7.png)

</details>
<br>

<details>
<summary>Between Example</summary>

The article needs the function of searching by time period, so it is configured with a between condition, the name is createdTime, and the createdTime field is matched.
![图片.png](/.attachments/图片-05b00f97-edf9-40c1-8b2a-9128862486ad.png)

query article before 2021-03-09, the query string should be `articles?createdTime=,2021-03-09`
![图片.png](/.attachments/图片-364cba38-a2e0-461c-83cf-5ebd3e043022.png)

-query article from 2020-02-02 to 2020-03-03, the query string should be `articles?createdTime=2020-02-02,2020-03-03`
![图片.png](/.attachments/图片-a6313c8f-5203-4d0a-afe4-91871d74e1a4.png)

query article from 2020-02-02, the query string should be `articles?createdTime=2020-02-02` or `articles?createdTime=2020-02-02,`
![图片.png](/.attachments/图片-0f8d07ba-3a6d-444b-92e1-24aee5669ec1.png)

![图片.png](/.attachments/图片-328dc235-de5e-48ed-94eb-5685caf309d0.png)
</details>

# IsRequired
`Bool`

Required: Yes

Used to determine whether the condition of the get request is necessary.

<details>
<summary>Example</summary>

The search function of auditLog requires fuzzy matching, so it is configured with a like condition, the name is keywords, and it is not necessary to set this condition.
![图片.png](/.attachments/图片-1d95eb55-bc8a-4eca-a221-a297c01da108.png)

It is not necessary to attach this condition when the get request is made, and the result can still be obtained.
![图片.png](/.attachments/图片-8cbb5c33-85f6-4eae-bd22-80420be452ef.png)

chatbotEntity needs to return the data of a certain chatbot, so it is configured with an equal condition, the name is chatbotid.
![图片.png](/.attachments/图片-64554051-6680-491b-abe9-0e9244387e74.png)

This condition is not attached to the get request, and the request reports an error.
![图片.png](/.attachments/图片-c23334d2-0871-429c-917b-61e03a53274e.png)

</details>

# [N] Fields
`Reference`

Required: Yes

Fields of this condition match 
- For normal fields, use field name directly
- For reference entity’s field, the syntax should be `reference_field_name.fieldname`, if match to reference entity’s key, we can omit the `.fieldName`. For example:
  - Search article by category id, we accept the categoryId parameter. And we can use `category` here. Note that `category` is the name of the field referencing to category entity in the article entity. And here we omit the `.id`.

    <details>
    <summary>Example</summary>

     ![图片.png](/.attachments/图片-6ebea80e-defb-49f8-aba2-458a9d113a4c.png)
     ![图片.png](/.attachments/图片-c10cb65d-c67d-4a47-a88a-3a270d1b33a1.png)

    </details>

  - Search article by knowledge base id, we can use `category.kb`. Note that `kb` is the name of the field referencing to knowledge base entity in the category entity. And here omit the `.id`.

    <details>
    <summary>Example</summary>

     ![图片.png](/.attachments/图片-7a54b37e-422e-4820-8c65-f07237d37039.png)
     ![图片.png](/.attachments/图片-38f19416-9453-4dbc-86f8-3a9b89cebe25.png)

    </details>

  - Search article by category name, we can use `category.name`
- For many-to-many reference entity, we use the plural name of the reference entity instead of the field name. For example:
  - Search article by tag id, we can use `tags` here. We also omitted the `.id` here.

    <details>
    <summary>Example</summary>

     ![图片.png](/.attachments/图片-eac3a735-e93a-405d-92db-116611b810f2.png)
     ![图片.png](/.attachments/图片-419359be-3e8d-4127-baf6-934138e49efd.png)

    </details>
  - Search article by tag name, we can use `tags.name` here.

