# Summary
In integration testing, the data is directly stored in the database. Usually, the running time of test cases is out of order, and there may be cases that test cases affect each other. For this reason, we provide `TestPriority` attribute, so that test cases can be executed in a certain order.

# Usage
Decorate the test method with `TestPriority` attribute. You can use integer parameters to define the priority of test method. For example, if we add `testpriority(-1)` to `GetKnowledgebaseByIdSuccess` in `sampletest`, then we can get the knowledgebase initialized in `GetKnowledgebaseByIdSuccess` in the use case of `ListKnowledgebaseSuccess`. 
![image.png](/.attachments/image-12bf5ac2-4c8c-4e70-b41c-cc085ee86c72.png)


