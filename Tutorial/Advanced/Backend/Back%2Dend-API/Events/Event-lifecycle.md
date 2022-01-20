# Summary
Typically in the framework's operations (List, Read, Create, Update, Delete, PostAction), each operation provides four different life cycle Events.
# LifeCycle 
- EntityPreEvent
  - EntityPreEvent only works before a transaction is opened.
- EntityWillEvent
  - EntityWillEvent functions after a transaction is opened and before the operation is executed.
- Entity(past participle)Event
  - Entity (past participle) Events function before a transaction closes after an operation is executed.
- EntityPostEvent
  - EntityPostEvent acts after a transaction ends.
- For example, with Read, the source implementation looks like this
  ![image.png](/.attachments/image-0d6cc30b-ed94-42e1-9f21-5c3f32020ec1.png)

<b>Note: </b>The above lifecycle applies only to synchronous events, and asynchronous events are done by new threads. If transactions are required in an asynchronous event, you need to add a `Transaction` attribute to the event when it is defined. 
# Defined Events
- List
  - EntityPreListEvent
    - Spec: [QuerySpecification](https://dev.azure.com/Comm100/Auto%20Coding/_wiki/wikis/Auto-Coding.wiki/696/QuerySpecification)
  - EntityWillListEvent
    - Spec: [QuerySpecification](https://dev.azure.com/Comm100/Auto%20Coding/_wiki/wikis/Auto-Coding.wiki/696/QuerySpecification)
  - EntityListedEvent
    - List: IEnumerable<Dictionary<string,object>>
  - EntityPostListEvent
    - List: IEnumerable<Dictionary<string,object>>
- Read
  - EntityPreReadEvent
    - Id: object
    - include： string[]
  - EntityWillReadEvent
    - Id: object
    - include： string[]
  - EntityReadEvent
    - Id: object
    - Entity: IDictionary<string,object>
  - EntityPostReadEvent
    - Id: object
    - Entity: IDictionary<string,object>
- Post -- Create
  - EntityPreCreateEvent
    - Entity: IDictionary<string,object>
  - EntityWillCreateEvent
    - IDictionary<string,object>
  - EntityCreatedEvent
    - Id: object
    - Entity: IDictionary<string,object>
  - EntityPostCreatedEvent
    - Id: object
    - Entity: IDictionary<string,object>
- Put -- Update
  - EntityPreUpdateEvent
    - Id: object
    - Original: IDictionary<string,object>
    - New: IDictionary<string,object> 
  - EntityWillUpdateEvent
    - Id: object
    - Original: IDictionary<string,object>
    - New: IDictionary<string,object> 
  - EntityUpdatedEvent
    - Id: object
    - Original: IDictionary<string,object>
    - New: IDictionary<string,object> 
  - EntityPostUpdateEvent
    - Id: object
    - Original: IDictionary<string,object>
    - New: IDictionary<string,object> 
- Delete
  - EntityPreDeleteEvent
    - Id: object
  - EntityWillDeleteEvent
    - Id: object
  - EntityDeletedEvent
    - Id: object
    - Entity: IDictionary<string,object>
  - EntityPostDeleteEvent
    - Id: object
    - Entity: IDictionary<string,object>
- Post Action
  - EntityPreDoActionEvent
    - Action: string
    - Id: object
    - Data: IDictionary<string,object>
  - EntityWillDoActionEvent
    - Action: string
    - Id: object
    - Data: IDictionary<string,object>
  - EntityDoneActionEvent
    - Action: string
    - Id: object
    - Data: IDictionary<string,object>
  - EntityPostDoActionEvent
    - Action: string
    - Id: object
    - Data: IDictionary<string,object>
    - Result: object
- Bulk Update
  - EntityPreBulkUpdateEvent
    - Id: object
    - Original: IDictionary<string,object>
    - New: IDictionary<string,object> 
  - EntityPostBulkUpdateEvent
    - Id: object
    - Original: IDictionary<string,object>
    - New: IDictionary<string,object> 


Events provided by the framework contain [Context](https://dev.azure.com/Comm100/Auto%20Coding/_wiki/wikis/Auto-Coding.wiki/704/Context)properties, Cross event referencing is possible through [Context](https://dev.azure.com/Comm100/Auto%20Coding/_wiki/wikis/Auto-Coding.wiki/704/Context) properties.

All `EntityPreEvent` contains a [TransactionIsolationLevel](https://dev.azure.com/Comm100/Auto%20Coding/_wiki/wikis/Auto-Coding.wiki/707/TransactionIsolationLevel)property. The level of segregation of a transaction can be modified by  modifying [TransactionIsolationLevel](https://dev.azure.com/Comm100/Auto%20Coding/_wiki/wikis/Auto-Coding.wiki/707/TransactionIsolationLevel).

