#Defining Events
To handle an event, you should implement the IEventHandler<TEvent> interface as shown below:
![image.png](/.attachments/image-b56f94b4-8ec7-4b9f-9a2a-57a7fb79a952.png)
If you want to handle an event asynchronously, you should implement the IAsyncHandler<TEvent> interface.
## Handling Multiple Events
You can handle multiple events in a single handler. If so, you should implement IEventHandler<TEvent> for each event. Example:
![image.png](/.attachments/image-5482fc75-0502-40b5-a34c-342133b95e62.png)
# Handling Event
To handle an event, you should implement the IEventHandler<T> interface as shown below:

![image.png](/.attachments/image-455c626c-afa5-4c4b-9b94-faaf5fbcd6cf.png)

The IEventHandler defines a HandleEvent method and implements it as shown above.

EventBus is integrated into the dependency injection system. We implemented ITransientDependency (above), so when a KBUpdateEvent event occurs, it creates a new instance of the KBUpdateValidator class, calls its HandleEvent method, and then disposes it. 

# Registration Of Handlers
We have to register handlers to the event bus in order to handle events.
## Auto Register(Recommended)
Event Handler need implement `ITransientDependency` or `ISingletonDependency` interface.
### Filter
- All Entities
  - Add `AutoRegister` attribute as shown below:
  ![image.png](/.attachments/image-9172d01e-9852-4995-8eaa-ce55543df3b5.png)
- Specific Entity
  - Add `EntityFilter` attribute
   - Example:
      This EventHandler is triggered only when Update KnowledgeBase is present.
      ![image.png](/.attachments/image-19b319f5-632f-4d73-982e-5630e649fea1.png)
- Specific Post Action
  - Add `EntityActionFilter` attribute
    - Specify the `Entity` and `Post Action` to which EventHandler applies.
    - Example
      ![image.png](/.attachments/image-3ce55c77-df81-4c0e-bf06-844e5db00fba.png)
      We can see that Junk has multiple post actions, but now just need to extend notJunk's EventHandler, you can trigger the specified post action by `EntityActionFilter`.
      ![image.png](/.attachments/image-bd7ebc4d-3a55-4523-8d1c-8141b89b4dbe.png)
## Register Manually
- Manual register via Container
  - You can call Container.Register<T>(DependencyLiveStyle lifeStyle) in application module. This is equivalent to EventHandler being drived from `ITransientDependency` or `ISingletonDependency` interface.
  - Example：
  ![image.png](/.attachments/image-95610e2c-b6a8-4fc8-b095-70cf790cd1b8.png)
- Register `EventHandler` through `EventBus`
  - You can resolve an instance of `IEventBus`, and call register function. This is equivalent to adding the `AutoRegister`attribute.
  ![image.png](/.attachments/image-61c2d3ff-d74b-40b4-beb0-c9f7b4a7b153.png)
  - Filter condition can be added in register method. `EntityFilter` and `EntityAcrtionFilter` are implemented by this filter condition.
  ![image.png](/.attachments/image-070bdaea-cebc-4a99-b2a2-f0fc20153804.png)

# Trigger
- Auto Trigger
  - In the Application layer of the framework, different events are defined in each operation. When defining an EventHandler, you can expand the business of the corresponding operation by inheriting the corresponding event. For details, please refer to[Event lifecycle](https://dev.azure.com/Comm100/Auto%20Coding/_wiki/wikis/Auto-Coding.wiki/659/Event-lifecycle)
  - If the defined EventHandler is driven from `IEventHandler<TEvent>`, the whole operation is synchronized. If it is driven from `IAsyncEventHandler<TEvent>`, the EventHandler will be executed asynchronously.
- Trigger Manually
  - You can use dependency injection to get a reference to the IEventBus([Injecting IEventBus](https://dev.azure.com/Comm100/Auto%20Coding/_wiki/wikis/Auto-Coding.wiki/665/Events?anchor=injecting-ieventbus))，call the `Trigger` or `TriggerAsync` method of event bus。
  ![image.png](/.attachments/image-29f6d598-37fd-4b36-a80c-0fafc6b1448f.png)
  ![image.png](/.attachments/image-ea3f5a9a-a48e-4b86-bc50-03c0f50808a3.png)
    - Trigger: Synchronous trigger
    - TriggerAsync: Asynchronous trigger
  - Example：
    ![image.png](/.attachments/image-02f2f003-faf1-438d-9d25-f5f01d70c06f.png)
