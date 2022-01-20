# General

## JWT

You can use OAuth2 to authenticate all your API requests to Comm100. OAuth provides a more secure way for your application to access your account data without requiring sensitive information like email and password to be sent with the requests. 

### Public Key & Private Key

Public Key is used to verify the token, taken from the `T_Global_SystemConfigOption` table, OptionKey is JWT_PublicKey, and the corresponding value is the value of OptionValue. 

![图片.png](/.attachments/图片-b9366b6d-dd89-4d62-be5b-0a26c4b744ba.png)

Private Key is used to generate token. It is kept and used by the token generation service. 

### OAuth Access Token

We are using jwt to implement oauth. When accessing the interface, you need to apply for an oauth token first, and then attach the token to the Authorization section.

![图片.png](/.attachments/图片-7beecbe4-59a7-4e35-befe-9d0dabbb7e96.png)

### Token Revocation

If there is a token that needs to be revoked, store the id, siteid and other related information of the token in the `t_Global_RevokedJWT` table of the general library. During authentication, the framework will read the data in the table and use the id value to confirm whether the token has been revoked.

## API Key

Authentication to the API is done via HTTP Basic Auth. Provide your email as the basic auth username and API_KEY as the password. 

# How to use

- Startup.cs

  Here, the default services are introduced through the AddDefaultServices method. 

  ![图片.png](/.attachments/图片-706141d4-e16e-45c2-a8b8-0212bedf7d9c.png)

- program.cs

  In webhost, use the CreateWebHostBuilder method defined by the framework to set up various things defined by the framework.

  ![图片.png](/.attachments/图片-af426c9a-43c4-45b5-bb9e-0275beadb1a4.png)

# Custom Code

- App Service

  Drived from BaseAppService

  ![图片.png](/.attachments/图片-5b577efe-ab4c-4e74-93ac-86acec1dc57c.png)

  Add Authorization Attribute

  ![图片.png](/.attachments/图片-8f057cf4-5024-4a49-ba5c-25e906da1adb.png)

  Note that Authorization Attribute can pass in permission parameters, requiring visitors to have specific permissions.

  ![图片.png](/.attachments/图片-21ba4802-691a-4b05-8003-806bf86d6a45.png)

  For specific permission items, see the `t_Global_PermissionItem` table of the General library, and the id value of the data is used as the permission value. For example, interface access requires users to have access to Join Chats and Transfer Chats, so pass 1011 and 1012 to Authorization Attribute.

  ![图片.png](/.attachments/图片-3b41915b-1e77-40d3-bb13-bace4af7ad2b.png)

- App Module

  Drived from BaseApplicationModule

  ![图片.png](/.attachments/图片-0e80cee3-28d9-4696-8e6d-8947a72ab2e9.png)

  Register app module in WebAPIModule.cs 

  ![图片.png](/.attachments/图片-787b7718-c726-484f-9b89-e9fad29d7606.png)

# Internal API Call

## T_Global_OAuthClient

Configure each field in the `T_Global_OAuthClient` table of the general library. Configuration is complete, record the value of ClientId.

![图片.png](/.attachments/图片-ad929a09-6dcb-4ab7-949f-76290c4dfad3.png)

## IOAuthService

Use the IOAuthService to generate an access token. The definition and implementation of this interface are both in the Comm100.Public module.  

![图片.png](/.attachments/图片-7b75c273-d7c6-447a-8204-c558d80f5676.png)

## Usage

Put the token in the http header (Authorizatoin: Bearer xxxx) when the api is called. 

## Others

Keep in mind that this token has a certain statute of limitations, make sure to re-acquire it before it expires and also you should save this token somewhere to avoid calling this function too frequently. 

When calling an api, please pass the SiiteId over to the queryStirng. If your api call needs to represent an agent, please pass the agentId over to the queryStirng as well. 