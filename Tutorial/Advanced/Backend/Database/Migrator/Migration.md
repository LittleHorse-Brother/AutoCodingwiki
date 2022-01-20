## Rules

The migration files of all databases are stored in the Migrations file of the project corresponding to the database
A single migration file is named after V+date(YYYY-MM-DD)+release order (3 digits)+description, such as V20210928001_chineseversion.
Each migration file is inherited from FluentMigrator.Migration.
Each migration file needs to have the Migration attribute attached, and the version and description are passed in. 

![图片.png](/.attachments/图片-f172eb1e-3648-476a-8245-996a0b01f093.png)

## SiteMigrate

For the site database, it is often necessary to operate on the table according to the siteid, which can be achieved by inheriting SiteidMigration.
The migration of the site database will traverse all the siteids of all the site databases, and only need to operate according to the siteid in the migration file.
When the site database writes the migration file, it needs to update the script synchronously, that is, the script needs to always keep the latest version. 

![图片.png](/.attachments/图片-c5fcc500-4ba3-4282-8141-96a4cfd8117f.png)
![图片.png](/.attachments/图片-a33be8b5-3218-4cb6-9741-ff423c87646b.png)

## FullTextIndexMigrate

For the fulltextindex database, you need to operate the table according to the databaseid, which can be achieved by inheriting FulltextindexMigration.
The migration of the fulltextindex database will traverse all the databaseids of the fulltextindex database, and you only need to operate according to the databaseid in the migration file.
When the Fulltextindex database writes the migration file, it needs to update the script synchronously, that is, the script needs to always keep the latest version. 

![图片.png](/.attachments/图片-63073ec0-636d-4a02-bba8-5ad781651a0a.png)
![图片.png](/.attachments/图片-72a7f591-fcaa-46cf-9776-54869af62bac.png)

For detailed syntax documentation of migration, see https://fluentmigrator.github.io/articles/intro.html. 