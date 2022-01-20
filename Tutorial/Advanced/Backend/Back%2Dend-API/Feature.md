# Summary

Feature is used to control whether the user has a certain function. For example, the function that needs to control the Routing Rule in business is only enabled for Enterprise users. The configuration of this feature is reflected in the api, that is, when some features are turned off, the corresponding API cannot be used. The framework provides several support for Feature. 

1. FeatureNameForAvailability property in Auto Coding Entity 
2. FeatureAttribute & IFeatureDomainService

# How to configure it in Auto Coding ER

In Autocoding, you can set specific Feature Point items for an entity. Currently, only one Feature Point can be configured for an entity. 

In the `t_AutoCdoing_Entity` table of the autocoding database, the `FeatureNameForAvailability` field is used to configure the FeaturePoint required by the Entity. The configured FeaturePoint will point to the FeaturePoint defined in the system, such as `system.t_Global_FeaturePointItem`. The framework will automatically check whether the current account has a certain feature and whether it can access the entity. If the site does not have the feature, accessing the create/edit/delete operation through the api will report an error, stating that Feature is not available. But get is not affected. 

<details>
<summary>Example</summary>

Site 1000 has no role feature 

![图片.png](/.attachments/图片-879a6f83-e2ec-4d4f-9a9c-c1a7c1f7e049.png)

Through api call, get method, not affected by feature, can successfully return data 

![图片.png](/.attachments/图片-a8439bd3-3e7e-42de-a39a-e448e328a263.png)

Call through api, put method, modify data, report error 

![图片.png](/.attachments/图片-89e8a523-99de-4dd2-a923-bb82749b8c98.png)

</details>

# How to use it in Custom Code

- FeatureAttribute

  It is used to control which features are needed for a function to be used. When using custom code, you can add FeatureAttribute to the method of the application layer, so that the function needs certain features to be called.

  ![图片.png](/.attachments/图片-ad7d4934-1a3f-4f7e-bfcc-1fc71b260408.png)

- FeatureDomainService

  Custom code can also manually check the feature by introducing FeatureDomainService 

  ![图片.png](/.attachments/图片-5711e81a-98b9-4144-a3ee-004f5877b6c5.png)