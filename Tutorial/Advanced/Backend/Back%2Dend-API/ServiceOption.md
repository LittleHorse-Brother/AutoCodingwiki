Serviceoption configuration is used to specify the service and gateway of the current program

# Property
- Gateway: Specify the domain name of the current service. This value will be used for splicing when calling the API of other services or returning file links.
- Name: Service name, We will only be able to access entities that are consistent with `entity.service`; By default, we use the service name as default schema. 

# How to use
You can set the configuration of serviceoption in the `startup.cs` file, for example:
```csharp
services.AddApiService("global",Configuration["Global_PartnerApiUrl"]);
```

