# Getting Started
In this article, we will demonstrate getting started with `Test.Framework`, showing you how to write and run your first set of integration tests.

## Create a xUnit test project 
Our test framework is encapsulated on the basis of xUnit. The basic test case writing rules follow the syntax of xUnit . First of all, we need to create a new xUnit project.

Add a new project in your solution. This will bring you to the first step of the new project wizard, where you pick your project type.

In the drop down boxes, choose your language (C#), your platform (All platforms), and your project type (Test). Scroll through the list if necessary until you find the item titled "xUnit Test Project (.NET Core)". Select it, then click "Next".
![image.png](/.attachments/image-f6e1a67b-f9d3-483f-b78b-e22eb94eecb0.png)

## Add Dependency
After creating the project, add the nuget dependency of `test.framework` and the project dependency of API project：
![image.png](/.attachments/image-db196635-3907-4701-9692-f8c68f351e97.png)

## Modify project file
Add the following code to the project file:
```
  <Target Name="CopyDepsFiles" AfterTargets="Build" Condition="'$(TargetFramework)'!=''">
    <ItemGroup>
      <DepsFilePaths Include="$([System.IO.Path]::ChangeExtension('%(_ResolvedProjectReferencePaths.FullPath)', '.deps.json'))" />
    </ItemGroup>

    <Copy SourceFiles="%(DepsFilePaths.FullPath)" DestinationFolder="$(OutputPath)" Condition="Exists('%(DepsFilePaths.FullPath)')" />
  </Target>
```

## Write Test Class
The new test class inherits `BaseIntegrationTest<TStartup>` and implements the default constructor:
![image.png](/.attachments/image-e085fcb8-a148-4813-9be4-864acde6de81.png)
After inheriting `BaseIntegrationTest<TStartup>`, your test class will have the ability to start testServer and initialize the database.

## Add Test Profile
Add `testsettings.json' to your test project and set the `Copy to Output Directory' property to `Copy if newer'.
![image.png](/.attachments/image-c949d84f-438b-405f-bcc3-9dc515780830.png)
The configuration file is configured as follows:
![image.png](/.attachments/image-fd636b10-fea8-4af4-94f1-e81f64e982b4.png)
- IfAutoGenerateDatabase: Whether databases are automatically generated (excluding the autocoding database). The database connection depends on the configuration of `appsettings.json` in the test target project, either specifying an existing database or automatically generating the database.
- SiteId: Available when `IfAutoGenerateDatabase` is false. Specify the test site in the existing database.
- Email: Available when `IfAutoGenerateDatabase` is false. Specify the agent email for the site.
- ApiKey: Available when `IfAutoGenerateDatabase` is false. Specify the agent Apikeyfor the site.
- DbScriptPath: Available when `IfAutoGenerateDatabase` is true. The script address of generating database, you can specify the physical address of DbScripts under the SQLScript library directly.

## Add StartupCollection
For projects that need to use the `TestFramework`, the class `StartUpCollection` must be added to the project as follows:
![image.png](/.attachments/image-b5230f58-be0f-4fae-a3e7-39efbed63be9.png)
<b>Notice: For all test classes that need to inherit `BaseIntegrationTest<TStartup>`, they must be in the same project and have the same namespace.</b> This is determined by the nature of xUnit.

## Add Test Method
Client objects can be created from built-in object `_factory` to send requests.
![image.png](/.attachments/image-db26ef59-5ece-4229-a7a1-de3a06c22c8d.png)
The framework provides request methods that include authentication, need using `Test.Framework.Extensions` namespace.
![image.png](/.attachments/image-a753bfd8-8c62-447f-b404-8f417a58478c.png)

## Run Tests
You can find test explorer in View->Test Explorer.
![image.png](/.attachments/image-c60d20c7-7bc6-4ef0-8eac-6948ce907225.png)
