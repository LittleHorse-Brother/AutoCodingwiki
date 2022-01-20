# Init
Through the command line, call the init method, pass in the parameters, and deploy the database.
Note: All database connections can be obtained through environment variables instead of being passed in. 

![图片.png](/.attachments/图片-bf47d5fc-6872-4a60-825d-da5147258c72.png)

## -c
The connection string of the center database.
If this parameter is not passed in, all database in center instance will not be created.

## -f
The connection string of the configuration database.
If this parameter is not passed in, all database in configuration instance will not be created.

## -r
The connection string of the reporting database.
If this parameter is not passed in, all database in reportinginstance will not be created.

## -d

The deployment name of the database instance.

## -m 

The base domian name used to generate url in [Parameters](/Tutorial/Advanced/Backend/Database/Migrator/Deployment/Parameters).

## -b

Allows `File`, `Center`, `Queue`, `ConfigurationGeneral`, `ConfigurationGeneralDefaultPartner`, `ConfigurationSite`, `ConfigurationFullTextIndex`, `ReportingGeneral`, `ReportingSite`, `ReportingFullTextIndex`.

Which databases need to init, if no passed, all databases will be init.
Multiple parameters must be separated by ;.

## -p
The macro params when excute scripts.
It must be passed in as a key-value pair, and the middle of the key-value pair is connected by an equal sign. The key must be in {}, that is, {param}.
Multiple parameters must be separated by ;.
Note that the macro parameter needs to be used in conjunction with the script.
For all the default generated parameters, see [Parameters](/Tutorial/Advanced/Backend/Database/Migrator/Deployment/Parameters).

# Migration

Through the command line, call the migrate method, pass in parameters, and migrate the database.
Note: All database connections can be obtained through environment variables instead of being passed in. 

![图片.png](/.attachments/图片-6c34162f-912d-4a72-9893-825ca74be3f7.png)

## -c
The connection string of the center database.
If this parameter is not passed in, all database in center instance will not be migrate.

## -f
The connection string of the configuration database.
If this parameter is not passed in, all database in configuration instance will not be migrate.

## -r
The connection string of the reporting database.
If this parameter is not passed in, all database in reporting instance will not be migrate.

## -d

The deployment name of the database instance.

## -m 

The base domian name used to generate url in [Parameters](/Tutorial/Advanced/Backend/Database/Migrator/Deployment/Parameters).

## -v

`Required`

The version of database need migrateup/migratedown.

## -b

`Required`

Allows `File`, `Center`, `Queue`, `ConfigurationGeneral`, `ConfigurationGeneralDefaultPartner`, `ConfigurationSite`, `ConfigurationFullTextIndex`, `ReportingGeneral`, `ReportingSite`, `ReportingFullTextIndex`.

Which databases need to migrate, if no passed, all databases will be migrate.
Multiple parameters must be separated by ;.

## -p
The macro params when excute scripts.
It must be passed in as a key-value pair, and the middle of the key-value pair is connected by an equal sign. The key must be in {}, that is, {param}.
Multiple parameters must be separated by ;.
Note that the macro parameter needs to be used in conjunction with the script.
For all the default generated parameters, see [Parameters](/Tutorial/Advanced/Backend/Database/Migrator/Deployment/Parameters).