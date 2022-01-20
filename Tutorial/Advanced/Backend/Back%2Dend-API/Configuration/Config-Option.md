In our program, we often need to get configuration information from ConfigOption table, so we add `ConfigOption` configuration to`IConfiguration`, ConfigOption configuration information will be refreshed every 30s.

When configuring the optionkey, `:` represents a child. Taking `Logging` as an example, we usually configure `Appsettings` as follows:

![image.png](/.attachments/image-aa3e86a0-a81c-4e9d-94b3-ac26ca63fe04.png)

When we configure overlay `Appsettings` in `ConfigOption`, we can configure as follows:

![image.png](/.attachments/image-dc92a9ed-5a3e-44c8-be8e-b6815ecde125.png)