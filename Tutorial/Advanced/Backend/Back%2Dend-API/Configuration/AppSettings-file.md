In Appsettings.json file, we usually configure the following six configurations:

- ConnectionStrings: Database connection configuration
  - Configuration is used to connect the `AutoCoding`, `General` and `Site` database.
  - Reporting is used to connect the `Reporting` database。

- DeploymentName: Use as database prefix name, For example, DeploymentName is Phoenix, and AutoCoding database is Phoenix.AutoCoding.

- ConnectionPool：Connection pool configuration
  - MaxPoolSize
  - MinPoolSize

- Logging: Please refer to [Configure logging](https://docs.microsoft.com/en-us/aspnet/core/fundamentals/logging/?view=aspnetcore-5.0#configure-logging) for configuration details.
  - LoggingLevel
    - Default
    - Microsoft
    - Microsoft.Hosting.Lifetime

- Kestrel: Please refer to [Configure endpoints for the ASP.NET Core Kestrel web server](https://docs.microsoft.com/en-us/aspnet/core/fundamentals/servers/kestrel/endpoints?view=aspnetcore-5.0) for configuration details.
  - Endpoints
    - Http
      - url

- AllowedHosts: Please refer to [Host filtering with ASP.NET Core Kestrel web server](https://docs.microsoft.com/en-us/aspnet/core/fundamentals/servers/kestrel/host-filtering?view=aspnetcore-5.0) for configuration details.

<b>note:</b>
The database connection string is composed of `ConnectionStrings`, `DeploymentName` and `ConnectionPool`. These values in AppSettings can be replaced by the configuration values in `Environment Variable` and `AWS Secrets Manager`. In the external network environment, `connectionStrings` is stored in AWS Secret Manager.

The configuration information of `Logging` will be replaced by the configuration information in `ConfigOption`.

Example:
![image.png](/.attachments/image-fc7ab304-b865-4bf6-a27f-ff65beeeae3a.png)



