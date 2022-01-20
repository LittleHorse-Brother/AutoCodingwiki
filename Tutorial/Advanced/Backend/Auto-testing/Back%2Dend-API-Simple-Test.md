# Getting Started
In this document, we will describe how to perform simple automated tests on configured entities (rather than through custom code) 

## Begin Test
Code location
![图片.png](/.attachments/图片-174bcb42-7bad-49de-8f99-bbce5c6eefe5.png)

Create a fork for each project group, because it involves project permissions, it is recommended that each project team use their own project public account to create a fork 
![图片.png](/.attachments/图片-1f624f88-00eb-40bd-959d-863813f857a2.png)

In the project team’s own project, the AutoTesting project from fork is introduced through sub-modules 
![图片.png](/.attachments/图片-708d93d3-8655-40fa-a394-f5d31869d5b8.png)

Add AutoEntityTest and Test.Framework to the solution 
![图片.png](/.attachments/图片-c3f87cad-296f-406c-b282-8982bba9e87c.png)

Open the appsettings.json file and configure the relevant data 
![图片.png](/.attachments/图片-80131591-53bf-43f3-b982-476fffae2bc1.png)

- Entities: Which entities need to be tested, separated by commas. 
- Application: Under which application the entity is under, note that all tested entities need to be under the same application. 
- DeploymentName: The deployment name of the database.
- SiteId: Specify the test site in the existing database.
- DatabaseId: Specify test database id in the existing database.
- PartnerId: Specify the partner id the site.

Everything is ready, you can view and execute each test case in Test Explorer 
![图片.png](/.attachments/图片-4cc2bb4a-f7e9-4853-9c3a-353a218a2083.png)

## CICD integration 

In the bin of the project, execute the corresponding command, it will automatically run all the test items, and give the result 
![图片.png](/.attachments/图片-c585149f-7eca-478d-9fcd-0c691fc5b739.png)

Or directly under the project folder, execute the corresponding command, it will automatically run all test items, and give the results 
![图片.png](/.attachments/图片-aae15f7a-26f9-4e45-827c-d614a98e0d9e.png)