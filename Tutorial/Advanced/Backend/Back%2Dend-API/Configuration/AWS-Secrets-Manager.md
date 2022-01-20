Generally, for the sake of security, we will store the relevant information of `ConnectionStrings` in AWS secrets manager. For all configurations stored in AWS Secrets Manager, we will load them into IConfiguration to override the corresponding configurations of `AppSettings` and `Environment Variable`.

If you do not rely on the framework of autocoding in your project, but want to use the configuration in AWS secrets manager, you can also add a `configuration provider` in program.cs
![image.png](/.attachments/image-c4183ec0-fe15-4b41-a6c6-83a110a74f4e.png)
![image.png](/.attachments/image-b4a137e7-169b-4320-a2bf-545145708d0f.png)
![image.png](/.attachments/image-cd476b0c-4782-4255-a375-cebfe2ca4d0a.png)
![image.png](/.attachments/image-1d9bd946-3b28-462f-95e6-d87e048c9954.png)