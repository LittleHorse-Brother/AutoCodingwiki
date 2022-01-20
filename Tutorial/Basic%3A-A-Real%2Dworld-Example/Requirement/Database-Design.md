The table name MUST follow this conversion: t_{application}_{entityName}. In our case, the table for blocked sender entity is `t_ticketing_blockedSender`.

| Name          | Type             | Primary Key | Default       | Description                                                    |
| ------------- | ---------------- | ----------- | ------------- | -------------------------------------------------------------- |
| Id            | uniqueidentifier | Y           | auto generate |                                                                |
| SiteId        | int              | N           | required      |                                                                |
| EmailOrDomain | nvarchar(256)    | N           | required      | Examples: someone@example.com or example.com                   |
| BlockLevel    | smallint         | N           | required      | 0: Reject all future messages; 1: Mark future messages as junk  |
| IsDeleted     | bit              | N           | 0             | This is for soft delete.  By default, our system doesn't perform hard delete to database records, the delete operation is just set this field to true underhood.                                                                |
| RowVersion    | timestamp        | N           | auto-generate | This is for data diffing and syncing, you don't have to understand it in this tutorial.                                    |
