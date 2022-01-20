Provide a simple sub-operation to change the value of the field in the entity. Entity API Post Action corresponding to the table `t_AutoCoding_APIPosAction` table in auto coding database. Contains the following fields: 

- [ActionName](#ActionName)
- [EntityUniqueName](#EntityUniqueName)
- [ApplyToViewEntity](#ApplyToViewEntity)
- [[0-N] HTTPPostActionAction](#[0-N]-HTTPPostActionAction)
- [[0-N]HTTPPostActionCondition](#[0-N]-HTTPPostActionCondition)

# ActionName 
`string`

Required: Yes

Name of the action, For url.

<details>
<summary>Example</summary>

Role has a switch on the interface to turn on/off the role function, so two sub-operations are defined in roleConfig to set the isEnable field in roleConfig to false/true.
![图片.png](/.attachments/图片-debf3228-f528-46d7-8de7-475a3f3db874.png)
![图片.png](/.attachments/图片-99b0c82c-3115-4d80-be1a-a8120900f2dc.png)

Call the sub-operation, set the value of the isEnable field, note that no data is passed in at this time.
![图片.png](/.attachments/图片-1e9c1fa6-797c-4336-9919-f40185412afc.png)

</details>

# EntityUniqueName
`string`

Required: Yes

The operation will affect the fields in which entity. 

# ApplyToViewEntity
`string`

Default: ""

If this field is set to a value, then this sub-operation is a sub-operation of the viewentity interface, not a sub-operation of the entity defined by the EntityUniqueName field. 

<details>
<summary>Example</summary>

ApplyToViewEntity is set to recycleBinTickets, EntityUniqueName is set to ticketingTicket, a sub-operation is defined to set the value of isInRecycleBin in the ticket.
![图片.png](/.attachments/图片-01ee109a-73d4-4c48-ba27-8e65391e79e9.png)
![图片.png](/.attachments/图片-333cdb83-4ef3-49bf-b6d1-5d1bcf4f024d.png)

Call the sub-operation of ApplyToViewEntity, set the value of the isInRecycleBin field, success.
![图片.png](/.attachments/图片-2b393c14-565e-49b4-a5af-3928477782c2.png)

Attempt to call the sub-operation of ticketingTicket, set the value of the isInRecycleBin field, and report an error.
![图片.png](/.attachments/图片-829edb57-dfb6-4e62-800e-63bfbde4e4f9.png)

</details>

# [0-N] HTTPPostActionAction
`Reference`

Required: Yes

reference to: [Entity API Post Action Action](/References/Entity-API/Entity-API-Post-Action/Entity-API-Post-Action-Action)

# [0-N] HTTPPostActionCondition
`Reference`

Required: Yes

reference to: [Entity API Post Action Condition](/References/Entity-API/Entity-API-Post-Action/Entity-API-Post-Action-Condition)