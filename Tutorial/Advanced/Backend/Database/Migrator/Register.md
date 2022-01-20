Introduce the registration procedure into the project through nuget. 
![图片.png](/.attachments/图片-dea1e109-b367-447f-bf14-554ef7091f1e.png)


Through nuget, introduce the relevant scripts into the project, and import which databases need to be used.
![图片.png](/.attachments/图片-902aef1e-b147-40ef-a342-32f8d7bf8f8b.png)


Scripts imported through nuget will automatically appear in the project and will be automatically packaged out. 
![图片.png](/.attachments/图片-d165efca-c1cd-49c0-a21c-e513a312dd02.png)
![图片.png](/.attachments/图片-aa886090-4466-4f55-a1ea-0d72dab2a461.png)
![图片.png](/.attachments/图片-7a09a7b2-6130-4ad0-a7fa-7dc4d5db5cde.png)

Rely on the corresponding module in the appmodule (partnerregistermodule for partner, siteregistermodule for site). 
![图片.png](/.attachments/图片-46ec8593-1dac-4079-b3b7-0c5ebedb1cd3.png)

Rely on the corresponding service in the constructor and use the corresponding service for registration. 
![图片.png](/.attachments/图片-786c9bc5-b1c0-4bfc-98be-357a22966511.png)