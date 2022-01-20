# What is Dependency Injection?
If you already know the Dependency Injection, Constructor and Property Injection pattern concepts, you can skip to the [next section](#Dependency Injection framework).

Wikipedia says: "Dependency injection is a software design pattern in which one or more dependencies (or services) are injected, or passed by reference, into a dependent object (or client) and are made part of the client's state. The pattern separates the creation of a client's dependencies from its own behavior, which allows program designs to be loosely coupled and to follow the dependency inversion and single responsibility principles. It directly contrasts the service locator pattern, which allows clients to know about the system they use to find dependencies.".

It's very hard to manage dependencies and develop a modular and well-structured application without using dependency injection techniques.

# Dependency Injection framework
There are many dependency injection frameworks that automate resolving dependencies. They can create objects with all the dependencies, and the dependencies of dependencies, recursively. Simply write your classes with the constructor & property injection patterns, and the DI framework will handle the rest!

AutoCoding Framework use [Castle Windsor](https://github.com/castleproject/Windsor/blob/master/docs/README.md) for Dependency Injection.

In a dependency injection framework, you first register your interfaces/classes to the dependency injection framework, and then resolve (create) an object. In AutoCoding, it's something like that:
```
var container = CIocManager.Instance;

container.Register<IPersonRepository,PersonRepository>(DependencyLifeStyle.Transient);
container.Register<IPersonAppService,PersonAppService>(DependencyLifeStyle.Transient);

var personService = container.Resolve<IPersonAppService>();
personService.CreatePerson("John Doe", 32);
```

First, we created the `IocContainer` and registered PersonRepository and PersonAppService with their interfaces. We then used the container to create an IPersonAppService. It created the concrete class PersonAppService with it's dependencies and then returned it. In this simple example, it may not be clear what the advantages are of using a DI framework. You will, however, have many classes and dependencies in a real enterprise application. The registration of dependencies are separated from the creation and use of objects, and is made only once during the application's startup.

Note that we also set the life cycle of the objects as transient. This means that whenever we resolve an object of these types, a new instance is created. There are many different life cycles, such as the singleton and scoped.

# Registering Dependencies
##  Conventional Registrations
AutoCoding framework automatically registers all Domain Services, Application Services by convention([Reference BaseApplicationModule](https://dev.azure.com/Comm100/Auto%20Coding/_wiki/wikis/Auto-Coding.wiki/669/Modules-provided-by-the-framework?anchor=baseapplicationmodule)). For example, you may have a IPersonAppService interface and a PersonAppService class that implements it:
```
public interface IPersonAppService : IApplicationService
{
    //...
}

public class PersonAppService : IPersonAppService
{
    //...
}
```
AutoCoding framework automatically registers it since it implements the IApplicationService interface (it's just an empty interface). It is registered as transient, meaning it is created each time, per use. When you inject (using constructor injection) the IPersonAppService interface into a class, a PersonAppService object will be created and passed into the constructor, automatically.

<b>Naming conventions</b> are very important here. For example, you can change the name of PersonAppService to MyPersonAppService or another name which contains the 'PersonAppService' postfix. This registers it to IPersonAppService because it has the same postfix. You can not, however, name your service without the postfix, such as 'PeopleService'. If you do so, it's not registered to the IPersonAppService automatically. Instead, it's registered to the DI framework using self-registration (not the interface). In this case, you can manually register it.

## Custom/Direct Registration
If conventional registrations are not sufficient for your needs, you can either use the IocManager or Castle Windsor to register your classes and dependencies.

### Using IocManager
You can use the IocContainer to register dependencies (generally in the PreInitialize method of your [module definition](https://dev.azure.com/Comm100/Auto%20Coding/_wiki/wikis/Auto-Coding.wiki/667/Modularization) class):
```
Container.Register<IMyService, MyService>(DependencyLifeStyle.Transient);
```


# Resolving Dependencies
## Constructor Injection Pattern
```
public class PersonAppService
{
    private IPersonRepository _personRepository;

    public PersonAppService(IPersonRepository personRepository)
    {
        _personRepository = personRepository;
    }

    public void CreatePerson(string name, int age)
    {
        var person = new Person { Name = name, Age = age };
        _personRepository.Insert(person);
    }
}
```
This is known as constructor injection. PersonAppService does not know which classes implement IPersonRepository or how it is created. When an PersonAppService is needed, we first create an IPersonRepository and pass it to the constructor of the PersonAppService:
```
var repository = new PersonRepository();
var personService = new PersonAppService(repository);
personService.CreatePerson("John Doe", 32);
```
Constructor Injection is a great way of making a class independent to the creation of dependent objects, but there are some problems with the code above:
- Creating a PersonAppService becomes harder. It has 4 dependencies. We must create these 4 dependent objects and pass them into the constructor of the PersonAppService.
- Dependent classes may have other dependencies (Here, PersonRepository has dependencies). We have to create all the dependencies of PersonAppService, all the dependencies of these dependencies and so on and so forth. We might not even be able to create a single object because the dependency graph is too complex!

## Resolve an instance by IOC Container
You may have to directly resolve your dependency instead of using constructor & property injection. This should be avoided when possible, but it may be impossible. AutoCoding framework provides some services that can be injected and used easily. Example:
```
var container = CIocManager.Instance;
var personService = container.Resolve<IPersonAppService>();
personService.CreatePerson("John Doe", 32);
```