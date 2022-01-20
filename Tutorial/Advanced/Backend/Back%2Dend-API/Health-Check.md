# Description

ASP.NET Core offers Health Checks Middleware and libraries for reporting the health of app infrastructure components.

Health checks are exposed by an app as HTTP endpoints. Health check endpoints can be configured for a variety of real-time monitoring scenarios:

- Health probes can be used by container orchestrators and load balancers to check an app's status. For example, a container orchestrator may respond to a failing health check by halting a rolling deployment or restarting a container. A load balancer might react to an unhealthy app by routing traffic away from the failing instance to a healthy instance.

- Use of memory, disk, and other physical server resources can be monitored for healthy status.

- Health checks can test an app's dependencies, such as databases and external service endpoints, to confirm availability and normal functioning.


# Add Default Health Check

- Add the framework default Service to the ConfigureServices method of startup.cs 

![图片.png](/.attachments/图片-681f9363-48df-428a-ab4a-4958012031d1.png)

- In the Configure method of startup.cs, add Health Check to endpoints 

![图片.png](/.attachments/图片-81e5aa27-83c7-4035-87e9-9dfa0e99537f.png)

  - Note that the path can be customized in UsehealthCheck 

  ![图片.png](/.attachments/图片-1333b5eb-19fe-4053-9355-372992f73b64.png)

- If the check is passed, 200 0k will be returned, along with the status and description of the check 

  ![图片.png](/.attachments/图片-28207dbb-26da-47ea-98a0-0e5cc20cb4a9.png)

# Custom health checks

All custom health checks need to implement the [IHealthCheck](https://docs.microsoft.com/en-us/dotnet/api/microsoft.extensions.diagnostics.healthchecks.ihealthcheck?view=dotnet-plat-ext-5.0) interface. The [CheckHealthAsync](https://docs.microsoft.com/en-us/dotnet/api/microsoft.extensions.diagnostics.healthchecks.ihealthcheck.checkhealthasync?view=dotnet-plat-ext-5.0) method returns a [HealthCheckResult](https://docs.microsoft.com/en-us/dotnet/api/microsoft.extensions.diagnostics.healthchecks.healthcheckresult?view=dotnet-plat-ext-5.0) that indicates the health as `Healthy`, `Degraded`, or `Unhealthy`.

- Custom health check

  ![图片.png](/.attachments/图片-11638829-9ab8-4a1b-a81e-eeed983e6389.png)

- Add a custom health check to the ConfigureServices method of startup.cs 

  ![图片.png](/.attachments/图片-b00ecc28-00ff-463b-8cd6-28d363ec8cce.png)

If all health checks pass, 200 ok will be returned, and the status and description of each check will be returned 

![图片.png](/.attachments/图片-98b37512-ef47-4b36-bc2c-394fc0b1d72d.png)

# Mutiple health checks

When there are multiple health checks, multiple health checks can be added at once 

![图片.png](/.attachments/图片-9d628def-1eda-4c54-b9bc-0f1b651f60b3.png)

- If the health check fails, 500 internal server error will be returned, and the status and description of each check will be returned. If the check throws an exception, the exception information will be returned together

  ![图片.png](/.attachments/图片-1f332bf3-6bb6-4fd1-8622-2762427facb6.png)

  ![图片.png](/.attachments/图片-6312bb98-84ad-406b-a235-51f60ca5e177.png)

- If all health checks pass, 200 ok will be returned, and the status and description of each check will be returned 

  ![图片.png](/.attachments/图片-98b37512-ef47-4b36-bc2c-394fc0b1d72d.png)
