# Summary
Framework provides the infrastructure to build modules and compose them to create an application. A module can depend on another module. Generally, an assembly is considered a module. If you create an application with more than one assembly, it's recommended that you create a module definition for each one.

# Module Definition
A module is defined with a class that is derived from `AbstractModule`. Say that we're developing a entity domain module that can be used in different applications. The simplest module definition can be as shown below:

![image.png](/.attachments/image-1f618ef7-bb64-43bd-abdf-b88178beef99.png)

The Module definition class is responsible for registering its classes via dependency injection, if needed (it can be done conventionally as shown above). It can also configure the application and other modules, add new features to the application, and so on...

#Lifecycle Methods
Framework calls some specific methods of modules on application startup and shutdown. You can override these methods to perform some specific tasks.

Framework calls these methods ordered by dependencies. If module A depends on module B, module B is initialized before module A.

The exact order of startup methods: PreInitialize-B, PreInitialize-A, Initialize-B, Initialize-A, PostInitialize-B and PostInitialize-A. This is true for all dependency graphs. The shutdown method is also similar, but in reverse order.

## PreInitialize
This method is called first, when the application starts. It's the go-to method to configure the framework and other modules before they initialize.

You can also write some specific code here to run before the dependency injection registrations. For example, if you create a conventional registration class, you should register it here using the IocManager.AddConventionalRegisterer method.

## Initialize
This is the place where dependency injection registration should be done. It's generally done using the `Container.Register` method. If you want to define custom dependency registration, see the [dependency injection documentation](https://dev.azure.com/Comm100/Auto%20Coding/_wiki/wikis/Auto-Coding.wiki/687/Dependency-injection).

## PostInitialize
This method is called last in the startup process. It's safe to resolve a dependency here.

## Shutdown
This method is called when the application shuts down.

# Module Dependencies
A module can be dependent on another. You need to explicitly declare the dependencies using the DependsOn attribute, like below:
![image.png](/.attachments/image-9a9b524e-a6ca-44a8-998e-282a1938e418.png)