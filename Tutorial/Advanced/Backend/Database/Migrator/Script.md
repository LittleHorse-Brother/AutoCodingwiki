## Normal
The scripts of each database are put into the database.automation project, and the project corresponding to each database.
Each project has a script folder with the same name for storing scripts.
Except site database, fulltextindex database and center database, do not update the scripts of other databases.

The pictures in the Sql script are currently written in the script using binary value, modified to @imagePath=relative path, and the binary information of the picture will be automatically read when the sql script is executed, and the final sql statement will be generated.

<details>
<summary>Example</summary>
The t_livechatwindowlog_init script in the Configuration.defaultpartner project 

![图片.png](/.attachments/图片-73b5aafa-aa02-4a4f-aa56-74c18e11ce84.png)
![图片.png](/.attachments/图片-24b6a5ea-b08a-4270-94f3-1a26d9c685d6.png)
</details>

## configuration.site

The scripts of the configuration.site database are subdivided into 3 directories. Note that the scripts of the site database must always be kept up to date.
The script in the configuration.site.databasecreate directory stores scripts that have nothing to do with siteid or that is a field in the table. They will be executed only once when the site database is created.
The script in the configuration.site.register/createtable directory stores the creation script of the table related to the siteid, which will be executed every time the site is registered.
The scripts in the configuration.site.databasecreate/InitData directory store the initial data scripts of the site, which will be executed every time the site is registered. 

![图片.png](/.attachments/图片-56a99280-d042-4ee3-9e64-0e01e6032845.png)

When siteid is used as a parameter in script, always use @SiteId. When siteid is used as part of the table name, use {0}, see sqlparamconstants in the configuration.site project for details.

![图片.png](/.attachments/图片-009bef23-7200-48ed-b390-4866c676ce56.png)

## reporting.site

The scripts of the reporting.site database are subdivided into 2 directories. Note that the scripts of the site database must always be kept up to date.
The scripts in the reporting.site.databasecreate directory store scripts that have nothing to do with siteid or where siteid is a field in the table. They will only be executed once when the site database is created.
The script in the reporting.site.register directory stores the creation script of the table related to siteid, which will be executed every time the site is registered.

![图片.png](/.attachments/图片-46422e56-4d90-4fbd-9fd7-21d81a0a2ce9.png)

When siteid is used as part of the table name, use {siteId}, see sqlparamconstants in the reporting.site project 

![图片.png](/.attachments/图片-09e217e8-8493-4338-af9a-abf2387043ea.png)

## center

The scripts of the Center database are subdivided into 3 directories. Note that the scripts of the center database must always be kept up to date.
The scripts in the Center.databasecreate directory store scripts that have nothing to do with partnerid or whose partnerid is a field in the table. They will only be executed once when the database is created.
The script in the Center.databasecreate.Partner10000 directory stores the initial data script of the partner 10000, they will only be executed once when the database is created.
The script in the Center.register directory stores the initial data script of the partner, which will be executed every time the partner is registered. 

![图片.png](/.attachments/图片-82fd1db1-4065-45d3-b32b-2a9baabd6776.png)

When partnerid is used as a parameter, always use the method of @partnerid. When partnerid is used as part of the table name, use {PartnerId}. For details, see sqlparamconstants in the center project. 

![图片.png](/.attachments/图片-f80d814d-c95c-40d7-b9c5-2a942be65828.png)

## Others

The scripts of the Configuration.Fulltextindex database are stored in the Configuration.Fulltextindex.Register directory, and the scripts of the Reporting.Fulltextindex database are stored in the Reporting.Fulltextindex.Register directory. Note that the scripts of the two fulltextindex databases must always be kept up to date.
The scripts of the File and Queue database are stored in the directory with the corresponding name.
There is no sql script for the Reporting.General database. 