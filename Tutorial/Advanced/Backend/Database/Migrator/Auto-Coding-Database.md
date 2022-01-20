## Create project folder 

.gitlab-ci.yml file, Dockerfile file and job.yaml file copied from other projects.

![图片.png](/.attachments/图片-d1c785e7-e1ea-45c2-9c38-a96285c6eefb.png)

In the job.yaml file, modify the -m parameter to the name of your service. Please be careful not to modify the -d parameter. It comes from the deployment environment, which is the name of the branch. 

![图片.png](/.attachments/图片-66bdec23-ccbd-4373-aca0-94210d32257e.png)

In the .gitlab-ci.yml file, modify the name of the job to be the same as the name in the job.yaml file.

![图片.png](/.attachments/图片-32345c67-76ec-4d02-afa1-4ae0ca65192d.png)

In the .gitlab-ci.yml file, modify the database connection and confirm that the connection is the target database for script execution. The script will get the deployment Name from the -d parameter in job.yaml, and then go to the database connection configured here to execute the sql script in the deploymentName.autocoding database.

![图片.png](/.attachments/图片-bb27d33e-842d-47b3-80fc-5eeab8219cf7.png)

## Generate sql scripts from existing databases, or write sql scripts by hand

Put all scripts in the scripts folder. Only the SQL scripts related to the autocoding project should be placed here. Which autocoding-related tables are used by your service? Here are the tables. Depending on the actual situation of the service, all autocoding tables may be included here. 

![图片.png](/.attachments/图片-00be3ab7-8b02-44af-96ec-0a7f763fc539.png)

![图片.png](/.attachments/图片-fa4c92d0-f19d-4f1c-b1ec-cf07f59682e2.png)

## Add database generator to project as a submodule

![图片.png](/.attachments/图片-c01956c4-74d9-4b1f-adac-910443bc9ed8.png)

The Generator folder will be automatically created, which stores the code of the AutoCodingDatabaseGenerator project. 

![图片.png](/.attachments/图片-43b96924-d1b3-4a3c-b48c-6de64c5e76ec.png)

![图片.png](/.attachments/图片-6eb79f5e-1b65-47ab-a6ec-faf1163876b2.png)

In the .gitmodules file, you can see that AutoCodingDatabaseGenerator has been added as a subproject.

![图片.png](/.attachments/图片-293d897d-c29c-4b3b-b82d-b21992097814.png)

## Build AutoCodingDatabaseGenerator

![图片.png](/.attachments/图片-5d0bd263-4a5d-4bda-967d-bdbb47a1954d.png)

![图片.png](/.attachments/图片-defe09fd-31dd-4337-83db-5faf0b9de748.png)

## Generate a database through the command line 

![图片.png](/.attachments/图片-2508a21c-e01e-4283-b04b-7cc406e817ea.png)

Incoming parameter description: 

-d

`Required`

The deployment name of the auto coding database instance.

-c

`Required`

The connection string of the auto coding database. Support aws secretsManager.

-m

`Required`

The schema used by all table. 

-s

The path of the scripts to execute.

-f

Force overwrite or not. If set to true, the table in the database will be deleted first, and then re-created and inserted data. The default is true. 

## Release

Submit the changes to git, and the ci cd process should be automatically packaged and scripts executed automatically. After the ci cd process is finished, the script will be executed correctly in the configured database. 