# Summary
Among the framework defined events,  for all the entry records are transmitted in the form of IDictionary, which is not in accordance with our usual coding habits. The `TEntity ToEntity<TEntity>(IDictionary<string, object>record)`method is thus provided for the transformation of dictionary into defined classes.

# Defining Class
- Defining an entity class requires inheriting the entity interface.
- The `MapperToEntity` attribute points to the corresponding entity.
- Example
![image.png](/.attachments/image-37a302c8-6c4b-4639-b1f5-429f0bc50440.png)

# ToEntity
Involing the `ToEntity` method generates an instance of `TEntity` and assigns assignments by matching the attribute name with the dictionary's key(<b>Note: Attribute matching is case sensitive except for initials</b>). Subsequent operations can all proceed through this instance.

# Update
- If there is a change to the value of an attribute in the current instance, the manipulated value can be updated back to the dictionary via the update method.
- `void Update<TEntity>(this IDictionary<string, object>data, TEntity) where TEntity:IEntity`。

# Example
![image.png](/.attachments/image-b7ac894e-cd2c-4ac7-93ed-3c6f5a00b939.png)
