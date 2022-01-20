Create the table named `t_Ticketing_BlockedSender` in site database base on [database design](/Tutorial/Basic:-A-Real%2Dworld-Example/Requirement/Database-Design).

## Steps
### 1, Connect to database by SQL server management studio

### 2, Go to site database

The name of site database is `{deployName}.Site{siteId}`

### 3, Create the table in site database
Following script, config Id as a primary key, and set the default value of IsDeleted to `0`.

![new create table.PNG](/.attachments/new%20create%20table-b8ebde8d-35d3-45fb-bfff-9aefb6c86f0e.PNG)


