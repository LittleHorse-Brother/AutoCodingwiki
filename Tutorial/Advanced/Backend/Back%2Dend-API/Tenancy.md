# Summary

站点数据库有多个数据库，根据siteid的不同，需要根据实际情况把实体映射到不同数据库的实体表中，框架会自动的处理

tenant代表啥？

# ITenancyResolver

ITenancyResolver会获取siteId的值,根据siteid，创建对应的tenant。

通过api访问实体时，需要在url中传入siteId的值，才能正确获取到数据，如`https://autoportal.comm100dev.io/api/KB/designs?kbId=f852e328-6de3-4da8-9080-429b820a5564&siteId=1000`.

# BaseDBContext

初始化时，如果IsSupportMultipTenancy为true，会通过ITenancyResolver去获取tenant，之后自动切换到siteid对应的数据库。

# ITenancyDomainService

ITenancyDomainService用于获取siteid，数据库之间的相关信息。

![图片.png](/.attachments/图片-f226655e-2eea-4817-b744-0879237f3da8.png)

# Site Tenancy Resolver in Comm100.Public

这是啥？

# Custom Code
                 
custom code的情况下，可以通过灵活的引入ITenancyResolver，BaseDBContext，ITenancyDomainService自行处理siteId和数据库之间的关系。