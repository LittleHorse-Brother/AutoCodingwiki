# summary
When instantiating through dependency injection, it sometimes takes a lot of time to create all the dependent instances and spend a lot of space to store them, but these instances may not be used for a long time, so the overhead is not worth it. Therefore, we provide a lazy loading mechanism to create instances only when using them to avoid unnecessary consumption.
# How to use
You can resolve any service using Lazy<IxxxService> in your app. This service will be lazily resolved when the first time you access lazy.Value property. For example:

![image.png](/.attachments/image-2690041e-2440-4142-99c8-626cb434dfda.png)


