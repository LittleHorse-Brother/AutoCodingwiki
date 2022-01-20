There are some fields that are not in the current entity and are calculated by the aggregation algorithm. Entity API Get Additional Field corresponding to the table `t_AutoCoding_APIGetAdditionalField` table in auto coding database. Contains the following fields: 

- [Name](#Name)
- [EntityUniqueName](#EntityUniqueName)
- [AggregateMethod](#AggregateMethod)
- [AggregateEntities](#AggregateEntities)
- [AggregateFieldName](#AggregateFieldName)
- [Label](#Label)
- [AggregateCondition](#AggregateCondition)

# Name
`string` 

Required: Yes

Name of the aggregation field. The field cannot be same of other filed name in the entity. 

# EntityUniqueName
`string`

Required: Yes

Unique name of the entity. The value of this field is used where the entity is referenced in all auto coding ER.

# AggregateMethod
`enum`

Required: Yes

Allows: `count` `sum` `max` `min`

### count

The value in database is `0`.

Sometimes, you just want to get a quick count of the number of records returned by a query. You can also use the COUNT function to count the number of records in a table. 

### sum

The value in database is `1`.

The SUM function is an aggregate function that adds up all values in a specific column. 

### max

The value in database is `2`.

The MAX functions find the maximum value in a record set.

### min

The value in database is `3`.

The MIN functions find the minimum value in a record set.

<details>
<summary>Example</summary>

The knowledgeBases entity itself does not have images, articles, and custompages, but the business needs to be returned together in the interface, so knowledgeBases is configured with 3 additional fields, images, articles, and custompages. Articles are calculated from the sub-entity article of the sub-entity category, and the image is calculated from the sub-entity image.
![图片.png](/.attachments/图片-c52755c5-d10a-4b85-a777-34ddfb4f1340.png)

When a get request is made, these three fields will be brought back and returned together, so that there is no need to call the corresponding interface to get the data. 
![图片.png](/.attachments/图片-554bd4d4-4007-4b08-bb45-96919ec89319.png)

</details>

# AggregateEntities
`string`

Required: Yes

can be a child entity or a child entity of child entity (connect entity name with dot)

<details>
<summary>Example</summary>

The knowledgeBases entity itself does not have images, articles, and custompages, but the business needs to be returned together in the interface, so knowledgeBases is configured with 3 additional fields, images, articles, and custompages. Articles are calculated from the sub-entity article of the sub-entity category, and the image is calculated from the sub-entity image.
![图片.png](/.attachments/图片-c52755c5-d10a-4b85-a777-34ddfb4f1340.png)

When a get request is made, these three fields will be brought back and returned together, so that there is no need to call the corresponding interface to get the data. 
![图片.png](/.attachments/图片-554bd4d4-4007-4b08-bb45-96919ec89319.png)

</details>

# AggregateFieldName
`string`

Required: Yes

Which field of Aggregate entity is used for calculation.

# Label
`string`

Required: Yes

Because the fields obtained by the aggregation will be returned like ordinary fields, the label field is used to tell the front end what it should be displayed on the page.

# AggregateCondition
`string`

Default: ""

When doing aggregate calculation, it is used as a condition to determine whether a certain piece of data is included in the calculation. This field can use `and` and `or` as complex conditions to judge aggregation calculations.

<details>
<summary>Example</summary>

The article entity itself does not have helpful and notHelpful, but the business needs to be returned together in the interface, so the article is configured with two conditions, which are used to calculate helpful and notHelpful respectively. 
![图片.png](/.attachments/图片-69a2e006-580a-4f12-adbd-d1d918f1087b.png)

When getting, no additional conditions are needed, and the results of the 2 aggregation calculations will be returned as ordinary fields.
![图片.png](/.attachments/图片-cc4ea67e-7460-44b9-b240-0c68aa796c0f.png)
</details>