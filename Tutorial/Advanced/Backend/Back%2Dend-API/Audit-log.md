# Summary

For some businesses, for security reasons, it is necessary to record who, when, what operations were performed, and what data was changed to what data. This requirement can be achieved by simply configuring audit log. For entity addition/deletion/modification operations, the audit log of the addition/deletion/modification will be recorded respectively, and the details of the operation, such as modification time, modification person, and modified fields will be recorded. 

# Configure

In the `t_AutoCoding_Entity` table, there are several fields for configuring audit log 

- IsRecordAuditLog

  Used to configure whether the entity needs to record audit log when adding/deleting/modifying operations. If it needs to be recorded, configure it to true, otherwise, configure it to false 

- AuditLogActionType

  Point to the id of the `System.t_System_AuditLogActionType` table 

- FieldToBeDisplayedWhenReferenced

  Used to configure the entity to record the audit log, if the FieldToBeDisplayedWhenReferenced field of the entity data has a value, the value will be retrieved and this value will be used as part of the audit log's action summary.

  For example: for department operations, you need to record the audit log, and its FieldToBeDisplayedWhenReferenced is configured as the name field, then when recording the audit log, the action summary will become `add/delete/change Department: DepartmentName (ID: xxx)` 

In the `t_System_AuditLogActionType` table, there are several fields for configuring audit log 

- Name

  The name of the behavior when adding/deleting/changing an entity 

- ModuleId

  Which application the behavior belongs to, the name of the application 

# Detail

For entities configured with `IsRecordAuditLog` to true, when adding/deleting/modifying, the framework will automatically obtain the current operating agentId, entity application, label and other information, generate the audit log table content, and save it to the site library. `t_Global_AuditLog{siteId}` in the table 

Description of some fields in the `auditlog` table 

- ModuleId

  Which application the behavior belongs to, the name of the application 

- ActionTypeId

  Point to the id of the `t_System_AuditLogActionType` table 

- AcitonSummary

  Check the `FieldToBeDisplayedWhenReferenced` field in the `t_AutoCoding_Entity` table. For the entity data that needs to record the audit log, if its FieldToBeDisplayedWhenReferenced field has a value, the value will be retrieved and this value will be used as part of the audit log's action summary. 

  Check whether there is an id field in the entity data and whether there is a value in the id field. If so, the id will be used as part of the action summary. 

  The final AcitonSummary will become `add/delete/change entityName: data[FieldToBeDisplayedWhenReferenced]: (ID: xxx)`, for example, add department, AcitonSummary will be generated as `Create Department: DepartmentName (ID: xxx)` 

- AcitonDetails

  AcitonDetails will list all the changed fields, as well as the modified value of this field, and the value before the modification. Depending on the operation, the saved data will be different 

  - create

    All fields will be saved 

  - update

    Only the modified fields will be saved 

  - delete

    No data will be saved 

<details>
<summary>Example</summary>

The Agent’s FieldToBeDisplayedWhenReferenced is set to displayName, when a new agent is created, the displayName of the new agent will be recorded in the ActionSummary, and the ActionDetails will record the values of all fields of the agent created when the operation is added. 

![图片.png](/.attachments/图片-a50467fc-aad5-4318-a5aa-95e4efea05df.png)
![图片.png](/.attachments/图片-d970db33-c5bc-48c6-a688-a283c79643a2.png)

chatButton的FieldToBeDisplayedWhenReferenced设置为空，更新chatButton的数据，ActionSummary中只会记录update chatButton和它的id，ActionDetails会记录修改的所有字段

![图片.png](/.attachments/图片-b244f0e4-d774-4a9f-bb25-20e4706351c6.png)
![图片.png](/.attachments/图片-2c03ee51-1e35-414c-9af4-4886192fd379.png)

</details>

# Others

For custom code, if you need to record the audit log, but the framework-level audit log does not meet the requirements, you can set IsRecordAuditLog to false and write custom code to record the audit log in the `t_Global_AuditLog{siteId}` table of the site library. 