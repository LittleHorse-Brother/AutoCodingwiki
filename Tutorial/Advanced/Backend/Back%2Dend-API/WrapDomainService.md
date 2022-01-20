In custom code, database related operations are often required. For this, we provide a relatively simple way of data operation: WrapDomainService.
# Outline
[Define entity classes](#Define-entity-classes)
[Use it in your code](#Use-it-in-your-code)

## Define entity classes
When defining an entity class, you need to inherit the `IEnity` interface. By default, the program will find the corresponding entity name(`t_AutoCoding_Entity.UniqueName`) according to the class.
![image.png](/.attachments/image-bb60371f-13bd-4204-b5b1-65a06ee2c30e.png)

If you want to define the class name with `t_AutoCoding_Entity.UniqueName` is inconsistent. We provide `MapperToEntity` attribute for mapping.
![image.png](/.attachments/image-cc787b0e-5b45-49a9-a15d-2d6efe5c21da.png)

## Use it in your code
When you define the entity class, you can use it in custom code for data operations
![image.png](/.attachments/image-02743e31-4a86-43a6-aec5-f8c31f30daf1.png)

