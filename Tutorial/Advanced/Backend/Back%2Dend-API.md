Before you start working, you need to have the following ready and know how to use these:
  - Visual Studio 2019 with .Net Core 3.1
  - SQL Server 2017 or up
  - Git
  - Comm100 Development Environment account

## Create a new solution

Create an empty .NET Core web application using Visual Studio. Of course you can remove some unnecessary UI-related files, because we will only provide APIs

## Add Reference

Before using the Auto Coding backend framework, you first need to get the Auto Coding backend framework DLL. In the development environment, you can get it from the local NuGet server. You need to add the Package Source in Visual Studio

![image.png](/.attachments/image-1e6a7c87-ee5f-4d51-8a84-bdb70cee05f2.png)

## Create the auto coding database

Before you can start running the program, you need to have an auto coding database. You can either use an existing auto coding database directly or backup and restore it from another auto coding database. Also you can pull the auto coding database scripts from the code repository and use an generator tool to create the specified auto coding database.

## Create the product database

For product database, you can generate it according to the actual situation. In general, deploying a full production test environment is the best choice. If you just want to experience Auto Coding, you can manually create this database.

## Configurate the application

### startup.cs

In the startup, add ioc reference 

![图片.png](/.attachments/图片-80e45b5f-afc9-4f65-9706-3c5f2bd2de96.png)

Introduce the default service defined by the framework here, and register the components of the framework to the container.

![图片.png](/.attachments/图片-706141d4-e16e-45c2-a8b8-0212bedf7d9c.png)

Pay attention to the parameters of the Install method. The application determines which part of the entity can be accessed by the program, and the namespcae determines which database table the entity will eventually access. See details: [Database](/References/Database)

![图片.png](/.attachments/图片-8b4b98bd-ba20-4ea6-9013-a6473559071a.png)
Here, through the use of Middleware, inject the framework, and set the use 
of a unified error handling program 

![图片.png](/.attachments/图片-f0d86cb9-45fa-48de-8a5c-8a454844dcad.png)

### program.cs

In webhost, use the CreateWebHostBuilder method defined by the framework to set up various things defined by the framework.

![图片.png](/.attachments/图片-af426c9a-43c4-45b5-bb9e-0275beadb1a4.png)

### WebAPIMoudle.cs

Here is the description of the dependency injection required by the ioc. There should be a module file at each layer to inject the interface and implement to the ioc.

![图片.png](/.attachments/图片-61d0ee97-4fb3-461b-9421-cc872d31dcf6.png)

### appsettings.josn

Here, you need to provide a connection to the autocoding database in Configuration, a connection to the Reporting database in Reporting, and a deployment name in DeploymentName. Among them, [{DeploymentName}.autocoding] will be used as the autocoding database table name.

![图片.png](/.attachments/图片-e45f8c0f-14ee-4a5a-8aef-e3cfc0243cb1.png)

## Configurate the ER in auto coding database

The details of Configure the ER can be found in [Entity](/References/Entity).

## Run the application

Everything is set up, run the program.