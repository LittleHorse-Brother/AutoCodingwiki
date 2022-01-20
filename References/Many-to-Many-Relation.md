ManyToManyRelation is used to define two entities as many-to-many relationships, such as the relationship between `agent` and `department`.

- [Entity1](#Entity1)
- [Entity2](#Entity2)
- [ApplyType](#ApplyType)

## Entity1

`string`

Required

Requirement entity unique name. The first entity in a many-to-many relationship.

## Entity2

`string`

Required

Requirement entity unique name. The second entity in a many-to-many relationship.

## ApplyType

`enum`

Default: `both`

In practice, a many-to-many relationship is two-way. But in order to reduce the complexity of the system, we need to isolate the relationship from the other side. 

For example: many-to-many relationship between `shift` and `agent`. The `shift` know that they are a many-to-many relationship with `agent`, but there is no need to know that they are a many-to-many relationship with the `shift` in `agent` entity.

### both

The value in database is `0`.

Indicates that a many-to-many relationship is applied to two entities (entity1 & entity2).

### applyToEntity1

The value in database is `1`.

Indicates that the many-to-many relationship will only apply to the entity1.

### applyToEntity2

The value in database is `2`.

Indicates that the many-to-many relationship will only apply to the entity2.

---

# What the auto coding framework did?

Let's use an example of a many-to-many relationship, such as shift and agent.

## Configure in database

- entity1: `shift`
- entity2: `agent`
- applyType: `1`

## Relation Table

The many-to-many relational table is automatically determined by the declarations of Entity1 and Entity2. For examples: If the entity1 is shift under livechat and the entity2 is agent under global. So the final relational table name is `t_LiveChat_ShiftAgentRelation`.

## Ids property in entity

Who: `applied`. This means that only the entity being applied will take effect with this rule.

If the many-to-many relationshipt is set to apply to the entity. When the many-to-many relationship configuration is complete, the corresponding entity automatically appears the id list property of the associated entity. 

In the case of shift and agent above, the `agentIds` will appears below shift entity, with the content being the associated list ids of agent.

![m2m-ids.PNG](/.attachments/m2m-ids-ed9d2261-b94f-4947-ad28-de145253af37.PNG)


## Include many-to-many entity

Who: `applied`. This means that only the entity being applied will take effect with this rule.

For many-to-many relationships, referenced entities can generally be loaded with the `include` parameter. With the include parameter, the corresponding entity is automatically loaded so that the front-end does not need to pull the entity data.

The requested url will be `shifts/{id}?include=agent`.

![image.png](/.attachments/image-19452131-d2da-4891-9576-2676d4a3acd1.png)

## Delete entities that are referenced by many-to-many

Who: `any`

When you delete an entity, all many-to-many relationships are deleted synchronously. For example: When you delete an `agent`, all shift agents relation associated with this agent via many-to-many reference will be deleted.

## Update many-to-many relationships

Who: `applied`. This means that only the entity being applied will take effect with this rule.

There is only one way to update the meny-to-many relationship, which is to update the corresponding many-to-many relationship by updating the list of ids under the entity. For example: we want to update the agent list of a specified shift.

`PUT /shifts/{id}`

![image.png](/.attachments/image-53b6d0c0-d1b8-4469-bc72-c349d7a128cc.png)

The server will update the agent relationships for the specified shift. The agent relationship that is not in the list will be removed.

Note: Many-to-many relationship cannot be updated through other api or method.

## Filter by many-to-many entities

Who: `applied`. This means that only the entity being applied will take effect with this rule.

Please refer to the following article: 
[How to configure query to filter by many-to-many entities?](/Use-Cases/General/How-to-configure-query-to-filter-by-many%2Dto%2Dmany-entities?)