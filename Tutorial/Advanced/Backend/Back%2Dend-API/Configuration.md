For most applications, you can directly use the extension function under comm100.web to implement all applications. We add two [configuration providers](https://docs.microsoft.com/en-us/aspnet/core/fundamentals/configuration/?view=aspnetcore-5.0#cp) in it to obtain the configuration stored in AWS secret manager and config option. You just need to add the following code to the program.cs file:

![image.png](/.attachments/image-79c84b71-8ec3-4954-93ce-717795e99d18.png)

Under our current framework system, there are four configuration configuration modes we usually use, from low to high priority:
1. [AppSettings file](https://dev.azure.com/Comm100/Auto%20Coding/_wiki/wikis/Auto-Coding.wiki/693/AppSettings-file)
2. [Environment Variable](https://dev.azure.com/Comm100/Auto%20Coding/_wiki/wikis/Auto-Coding.wiki/694/Environment-Variable)
3. [AWS Secrets Manager](https://dev.azure.com/Comm100/Auto%20Coding/_wiki/wikis/Auto-Coding.wiki/673/AWS-Secrets-Manager)
4. [Configuration Option](https://dev.azure.com/Comm100/Auto%20Coding/_wiki/wikis/Auto-Coding.wiki/691/Config-Option)

Each of the above four configurations can override the previous configuration. Details can be viewed in [Configuration in ASP.NET Core](https://docs.microsoft.com/en-us/aspnet/core/fundamentals/configuration/?view=aspnetcore-5.0).

All configuration information can be obtained through `IConfiguration`.
- You can use dependency injection to get a reference to the IConfiguration.
![image.png](/.attachments/image-f2b297c4-2b7f-4e10-89d4-14f1b8f860f7.png)
- Get settings value by IConfiguration.
![image.png](/.attachments/image-ba87dfc5-c4cb-4ca7-9aca-ac63df4fba4a.png)

# How to read the specified partner-related configuration option

You can read directly using this extended function below:

![image.png](/.attachments/image-b7d4ad30-e525-4bed-bb80-9ce53cc83d09.png)