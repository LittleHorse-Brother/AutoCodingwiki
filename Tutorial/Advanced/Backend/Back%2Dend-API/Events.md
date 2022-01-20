# Summary
In C#, a class can define events and other classes can register with them to be notified when something happens. This is useful for a desktop application or standalone windows service, but for a web application it's a bit problematic since objects are created in a web request and are short-lived. It's hard to register some class events. Directly registering to another class's event makes classes tightly coupled.

Domain events can be used to decouple business logic and to react to important domain changes in an application.

# EventBus
The EventBus is a `singleton` object that is shared by other classes to trigger and handle events. To use the event bus, you need to get a reference to it. You can do that in two ways.

## Injecting IEventBus
You can use dependency injection to get a reference to the IEventBus. 
```
public class TaskAppService : BaseAppService
{
    public IEventBus EventBus { get; set; }

    public TaskAppService(IEventBus eventBus)
    {
        EventBus = eventBus;
    }
}
```
## Getting The Instance Form Container
You can use [Container]() to resolve a instance of `IEventBus`. 
![image.png](/.attachments/image-7c7a6ed0-e808-424b-a97f-f0e1b44c0523.png)

# Defining Events
 Before you can trigger an event, you need to first define it. An event is represented by a class that is derived from IEvent. Assume that we want to trigger an event when a task is completed:
```
public class TaskCompletedEventData : IEvent
{
    public int TaskId { get; set; }
    public string Name => this.GetType().Name;
    public DateTime EventTime => DateTime.UTCNow;
}
```
This class contains properties that are needed by the class that handles the event. The `IEvent` interface defines the Name(the event name) and the EventTime (when it's triggered) properties.