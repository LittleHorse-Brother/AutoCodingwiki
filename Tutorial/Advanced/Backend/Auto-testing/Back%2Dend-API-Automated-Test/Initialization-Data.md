# Summary
If it comes to testing of database, it is likely that there will be some existing test data in the database before testing, which will have an impact on the execution results of our test cases, or prepare some relevant data when executing some test cases.

For preparing test data, we can use the call API to prepare data, but it is not suitable for some scenarios where the data is too complex or cross application data needs to be prepared.

We provide a way to manage test data using SQL scripts.

# Usage

You can create a directory in the project to manage SQL scripts and prepare scripts for test data in it.

Set the property of script `Copy to Output Directory` to `Copy if newer`.
![image.png](/.attachments/image-3ac21fdd-e4d8-4dca-ae69-23ae96d07804.png)

Calling `InitData` method in test method to execute SQL scripts.
![image.png](/.attachments/image-c69f5c42-1194-4fc7-a0e1-95627b1c6816.png)
![image.png](/.attachments/image-277c860b-4c22-464c-90a1-dbdce42273fd.png)




