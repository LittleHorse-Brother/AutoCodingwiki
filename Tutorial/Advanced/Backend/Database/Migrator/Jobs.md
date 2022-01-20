A job is a yaml file used to perform database initialization/upgrade/downgrade. Different operations are achieved by configuring different jobs.

When the version is released, it is usually necessary to provide the image of the migrate corresponding to the version to be released, and provide the corresponding job file according to the situation of different platforms. 

# Summary

At present, we have configured multiple example jobs in the code base for different scenarios. 

![图片.png](/.attachments/图片-e4322b3c-a6d7-48e5-be90-8014d44bf52c.png)

## Generic

The yaml file at the beginning of job_platform_generic is the job required to perform initialization/upgrade/downgrade operations on the database in general scenarios. 

### job_platform_generic_init

The init operation in the general case. All current libraries will be initialized. Note that when a new environment is created, migrate will need to create a new branch, and then the cicd process will automatically initialize all databases without additional execution of this job. 

Under env are the configured environment variables. For parameter descriptions, see [Deployment](/Tutorial/Advanced/Backend/Database/Migrator/Deployment). 

![图片.png](/.attachments/图片-2a87a230-c24b-4001-a0f9-0ad3b236740e.png)

### job_platform_generic_upgrade

The upgrade operation in general cases. The -v parameter is the database version to be upgraded to. 

Under env are the configured environment variables. For parameter descriptions, see [Deployment](/Tutorial/Advanced/Backend/Database/Migrator/Deployment). 

![图片.png](/.attachments/图片-b9ea6a4b-ccc1-43d6-b195-1b0d03c10caa.png)

### job_platform_generic_downgrade

The downgrade operation in general. The -v parameter is the database version to be downgraded to. If there is no previous version, pass in -1. 

Under env are the configured environment variables. For parameter descriptions, see [Deployment](/Tutorial/Advanced/Backend/Database/Migrator/Deployment). 

![图片.png](/.attachments/图片-0949c48a-7bed-4036-8055-78dcb6123c2c.png)

## Plartform max specific

The yaml file starting with job_database_max is used to perform initialization/upgrade/downgrade operations of the max platform. 

### job_platform_max_init

The init operation in the max environment. Note that the environment variable IfMaxEnv has a value of true. This value is used by the program to determine whether to perform operations on the max platform. When this value is true, the value of the configuration items in some tables will be different. 

Under env are the configured environment variables. For parameter descriptions, see [Deployment](/Tutorial/Advanced/Backend/Database/Migrator/Deployment). 

![图片.png](/.attachments/图片-cb66b6b0-a3da-4ffe-be34-4a3aeb7f850d.png)

### job_platform_max_upgrade

The upgrade operation in the max environment. The -v parameter is the database version to be upgraded to. 

The init operation in the max environment. Note that the environment variable IfMaxEnv has a value of true. This value is used by the program to determine whether to perform operations on the max platform. When this value is true, the value of the configuration items in some tables will be different. 

Under env are the configured environment variables. For parameter descriptions, see [Deployment](/Tutorial/Advanced/Backend/Database/Migrator/Deployment). 

![图片.png](/.attachments/图片-54f8b1c9-c049-4bbf-a393-1af988d58f34.png)

### job_platform_max_downgrade

The operation of downgrade in max environment. The -v parameter is the database version to which you need to downgrade. If there is no previous version, pass in -1. 

The init operation in the max environment. Note that the environment variable IfMaxEnv has a value of true. This value is used by the program to determine whether to perform operations on the max platform. When this value is true, the value of the configuration items in some tables will be different. 

Under env are the configured environment variables. For parameter descriptions, see [Deployment](/Tutorial/Advanced/Backend/Database/Migrator/Deployment). 

![图片.png](/.attachments/图片-dc107ffb-c57a-4ee9-bb3e-1a9ac215aaef.png)

## Database center specific

The yaml file at the beginning of job_database_center is used to perform initialization/upgrade/downgrade operations of the center database. For other scenarios that need to perform operations on a specific database, you can refer to this job. 

### job_database_center_init

Used to initialize the center database. The -b parameter is used to specify that only the center database is initialized. 

Note that in the environment variable, only ConnectionStrings_Center is configured with a value, indicating that in this job, only the database under the center instance will be operated. 

Under env are the configured environment variables. For parameter descriptions, see [Deployment](/Tutorial/Advanced/Backend/Database/Migrator/Deployment). nt)。

![图片.png](/.attachments/图片-37e758fd-54d7-4a06-8b07-757975bacec3.png)

### job_database_center_upgrade

Used to perform the upgrade operation on the center database. The -b parameter is used to specify that only the center database is initialized. The -v parameter is the database version to be upgraded to. 

Note that in the environment variable, only ConnectionStrings_Center is configured with a value, indicating that in this job, only the database under the center instance will be operated. 

Under env are the configured environment variables. For parameter descriptions, see [Deployment](/Tutorial/Advanced/Backend/Database/Migrator/Deployment). 

![图片.png](/.attachments/图片-ab9681cc-183f-4413-aa28-147d53bf858c.png)

### job_database_center_downgrade

Used to downgrade the center database. The -b parameter is used to specify that only the center database is initialized. The -v parameter is the database version to which you need to downgrade. If there is no previous version, pass in -1. 

Note that in the environment variable, only ConnectionStrings_Center is configured with a value, indicating that in this job, only the database under the center instance will be operated. 

Under env are the configured environment variables. For parameter descriptions, see [Deployment](/Tutorial/Advanced/Backend/Database/Migrator/Deployment). 

![图片.png](/.attachments/图片-90b7f92e-e2f6-4e8c-9ca1-8bf7d9531eea.png)

# gitlab-ci.yml

In the cicd process, this file will be read, and the corresponding job will be executed according to the configuration of this file. 

When testing, you need to set the job in gitlab-ci.yml to the job that needs to be executed.

The following three places need to be modified: 

![图片.png](/.attachments/图片-c7040722-db94-4011-94cc-00d280642f3b.png)

![图片.png](/.attachments/图片-41e6bae6-ebd1-42c7-b993-ca07632ef9d9.png)

# Parameters

For details, see [Deployment](/Tutorial/Advanced/Backend/Database/Migrator/Deployment). 

Note that all parameters that support reading from environment variables are configured as environment variables in the previous job. 

# FAQ

## How to only operate on a specific instance 

Under env, there are three database connections: `ConnectionStrings_Configuration`, `ConnectionStrings_Reporting` and `ConnectionStrings_Center`. If you need to operate only for a specific instance, only configure the corresponding database instance connection, and configure other instances to be empty.

For example: If you need to operate only on the Configuration instance, only configure the value of `ConnectionStrings_Configuration`, and the connection configuration of the other two instances is empty. 

## How to only operate against a specific database 

1. Only configure the database connection of the instance where this database is located.

2. Only this specific database is passed in the -b parameter.

3. Reference [Center](#job_database_center_init). 