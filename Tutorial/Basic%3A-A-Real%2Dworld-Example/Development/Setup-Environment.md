<!--- 
我们为这个tutorial专门建了一个开发环境，后续的开发工作在这个环境里做。这个开发环境是一个独立的git项目，可以独立运行。
-->

We have built a development environment for this tutorial, and subsequent development work will be done in this environment. This development environment is an independent git repository and can be run independently.

## GIT Address

https://gitlab.comm100dev.io/x2/common/onboarding/autocodingtutorial
(only accessible from LAN environment.)

## Setup package manager
Please follow this guide setup NPM and NuGet: https://dev.azure.com/Comm100/Main/_wiki/wikis/Comm100%20RandD.wiki/1127/Use-package-dependencies-in-LAN-environment

## Structure
<!--
这里只简单的介绍这个培训里用到的命令，脚本以及安装包的位置。
-->


Here is just a briefly describes the location of the command, script, and postman's installer used in this tutorial. For details, you can read the **README** file inside the repository.
- Root
  - Backend
    - run.bat
    - README.md
  - Frontend
    - README.md
  - Database
    - Demo.AutoCoding.bak
    - Demo.General.sql
  - Tools
    - Postman installer

<br/>

## Preparation
- Use SQL Server Management Studio
- Use a browser to detect the issues
- Use "Postman" to debug API

## Steps:
1. [Create databases](#create-database)
2. [Start up the backend services](#start-backend-svc)
3. [Modify the configuration of the project](#modify-links)
4. [Run the test site](#run-test)
5. [Test with postman or test site](#test)

<br/>

<a id="create-database"></a>
## 1. Create databases

<!--
使用SQL Server Management Studio去链接数据库服务， 数据库服务没有限制，可以是本地或者远程。链接好服务后按步骤执行：
-->

Connect database service with SQL Server Management Studio. There are no restrictions on database service, which can be local or remote. Follow the steps after linking the service.

### 1.1. Execute "Demo.General.sql" script
<!--
执行完Demo.General.sql脚本，会创建名叫“Demo.General”的数据库，点开tables节点，里面应该有一张名叫“t_onboarding_demo”的表。
-->
After executing the **Demo.General.sql** script, a database named "Demo.General" will be created. Click the tables node, and there should be a `t_onboarding_demo` table.

### 1.2. Recover "AutoCoding" database
<!--
通过备份文件Demo.AutoCoding.bak恢复AutoCoding数据库。这里有详细的[文档]
(https://docs.microsoft.com/en-us/sql/relational-databases/backup-restore/quickstart-backup-restore-database?view=sql-server-ver15)。
-->

Recover the "AutoCoding" database by the backup file named "Demo.AutoCoding.bak". Here's the detail [documentation](https://docs.microsoft.com/en-us/sql/relational-databases/backup-restore/quickstart-backup-restore-database?view=sql-server-ver15)

<br/>

<a id="start-backend-svc"></a>
## 2. Start up the backend services
<!--
在Backend文件夹下面执行run.bat命令，弹出两个命令窗口，启动了"DemoApi" 和 “EntityApi”服务。 从命令窗口你看到各个服务的地址。
-->

Execute the **run.bat** under the `Backend` folder, and two command windows pop up to start up the "DemoApi" and "EntityApi" services. You can get the address of the service from the command window.

DemoApi's address：

![a.png](/.attachments/a-668f6420-3739-4b00-8483-86c71471d0cd.png)

EntityApi's address：

![b.png](/.attachments/b-3addbb8e-fa64-452b-8c1c-24f8ab007ddc.png)

<br/>

<a id="modify-links"></a>
## 3. Modify the configuration of the project
<!--
根据README里的介绍， 修改项目的数据库链接和API地址。
-->

According to the introduction in **README**, modify the database links and API address of the project.

<br/>

<a id="run-test"></a>
## 4. Run the test site
Perform the following steps in the `FrontEnd` directory of the project：
&nbsp;&nbsp;&nbsp;&nbsp;4.1 Execute "npm install" in the root of the project to install dependencies.
&nbsp;&nbsp;&nbsp;&nbsp;4.2 Execute "npm run start" in the root of the project to start up the test site.

If you have problems with the previous steps, please check the **README** of the project

After startup, you can open the site in the browser.

![3.png](/.attachments/3-cfde4e02-27e5-4955-8748-88a2e63401cb.png)

![4.PNG](/.attachments/4-65855dd2-3697-4281-ad06-4a2ce65aee4b.PNG)

<br/>

<a id="test"></a>
## 5. Test with postman or test site

- Browser
Open the devtool of the browser to check whether there is an error on the current page.

![br.PNG](/.attachments/br-be8f016e-0e1d-44de-9546-d28d1979b64c.PNG)

- Postman
You can use postman to test the APIs.

![post.PNG](/.attachments/post-499939c3-04c2-4542-b630-a48369b630bd.PNG)


