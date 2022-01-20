# BaseIntegrationTest<TStartup> built-in objects
## _factorty
`TStartup` is your web application's `Startup` class. With this instance, your test class can create a client using the factory's CreateClient method:
![image.png](/.attachments/image-755bebc8-522d-4b40-9a85-c6c1c42002cc.png)

## _configuration
You can get configuration information through the instance of `_configuration`，including `appsettings.json`和`testsettings.json`.

## _output
Additional information can be output through an instance of `_output`。
![image.png](/.attachments/image-4eb46a72-32b8-4194-95bd-fd378f35c551.png)
![image.png](/.attachments/image-f50a78e4-9e7f-4c09-aab8-02eb1881d897.png)

# Assert Extesions
should use `Test.Framework.Extensions`
## Boolean
![image.png](/.attachments/image-ab45a3e1-10b5-4cb6-ad78-1b996d6191b4.png)

## Collection
![image.png](/.attachments/image-72552ee9-fd9f-44a0-bd73-f28427ed05fa.png)

## Object
![image.png](/.attachments/image-c8508d15-415f-4132-9719-7099a9d4fa12.png)

## String
![image.png](/.attachments/image-3051ea38-1bb8-48c9-8c7d-6514af962ab7.png)