## Class Definition

- All custom exceptions need to be integrated with BaseExcpetion （comm100.framework.exceptions.BaseException）
- The naming of all exception classes is subject to review by Product Marketing Team. 

Example:

 ![image.png](/.attachments/image-bd78c476-48c8-410a-a4be-2cf3ab788dff.png)

## Status Code Control

- By default, the exception returns 500
- The status code can be controlled via HttpStatusAttribute(comm100.framework.Exceptions.HttpStatusAttribute)

Example:

 ![image.png](/.attachments/image-754ac1db-f911-4633-bd09-df6cb08a1d0f.png)

## More Information
- In some cases you need to return more description to the caller, you can set the Details value to implement.

 ![image.png](/.attachments/image-07a89b88-07ed-4a80-a7db-8dc6be9bbe82.png)

The details information will return by api error result.

 ![image.png](/.attachments/image-a89e8836-8427-4d72-a16c-a43e0a13de0a.png)

## Exception Handling
- Use ExceptionMiddleware（comm100.framework.Exceptions.ExceptionMiddleware）to handle all exceptions.  Please add this Middleware when the app starts.

 ![image.png](/.attachments/image-ac126908-c259-42ec-9f9e-77a861f4546d.png)

## Exception defined in Framework

 ![image.png](/.attachments/image-a266de31-7b0b-449a-86c2-957b09de8ec6.png)

## Incorrect Demonstration
- Use the Exception class directly

![image.png](/.attachments/image-261fe3f4-1d5f-4fc0-8220-02400fd238a9.png)
 
