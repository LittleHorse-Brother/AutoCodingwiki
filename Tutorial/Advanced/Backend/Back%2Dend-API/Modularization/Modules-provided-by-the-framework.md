# ERWebModule
Usually in projects based on the autocoding framework, in the web layer, you need to define a module dependency on `ERWebModule` as shown below：

![image.png](/.attachments/image-a4d357e5-e4d3-44fb-8972-6a38a5a56de8.png)

In `ERWebModule`,  we also rely on many other modules, of which <b>PublicDomainModule</b> as shown below should be noted:

![image.png](/.attachments/image-52feedb0-1e82-45f4-b343-b4d29ced1db0.png)

As you can see from the above, the `PublicDomainModule` registers many public interfaces, such as [TenancyResolver](https://dev.azure.com/Comm100/Auto%20Coding/_wiki/wikis/Auto-Coding.wiki/682/Tenancy), [AuditLogger](https://dev.azure.com/Comm100/Auto%20Coding/_wiki/wikis/Auto-Coding.wiki/676/Audit-log) and so on. If you want to inject instances of these interfaces into your services, you must rely on this module.

# BaseApplicationModule
This is the module base class for the application layer, Usually in projects based on the autocoding framework, the application layer needs to define its own module drived from BaseApplicationModule as shown below：

![image.png](/.attachments/image-c5b0e96d-13b3-4566-997c-1762e710d155.png)

In the `BaseApplicationModule`, we do two things：
- App Service Interceptor: <b>need to be drived from BaseAppService.</b>
  - [Authorization](https://dev.azure.com/Comm100/Auto%20Coding/_wiki/wikis/Auto-Coding.wiki/680/Authorization)
  - Transaction 
    - In customcode, you can add the 'Transaction' attribute to the method if you want to add transactions to some businesses.
    - How to use
      - Defining AppService requires inheriting BaseAppService
      - Add the `Transaction` attribute to the method that requires transactions, which supports the Transaction Isolation Level parameter and defaults to `ReadCommited`.
      - Example
      ![image.png](/.attachments/image-1e3f62de-c5c5-4104-9bfb-b3db652bad6b.png)
- Auto Register Service:
  - For services that conform to naming conventions, we will automatically register to `IOC Container`.
  - Uses all interfaces that have name matched by implementation type name. Matches `Foo` to `IFoo`.
  - Usually we define an interface at the Application layer as `IxxAppService`, and the implementation class is named `xxAppService`.

# BaseDomainModule
BaseDomainModule, similar to BaseApplicationModule, is the base class of module for domain layer. Auto Register Service  is also provided.




 