# Summary
A `Context` in an `Event` is designed to exist as a context for sharing data across events. For example, in some business, we get or calculate some data in the EntityWillEvent, and the resulting data need to be in the EntityPosteventbelow, then we can deposit the data into the `Context` and get it from the `context` in subsequent events. 

# How to use
- void Set(string key, object value)
  - Example
  ![image.png](/.attachments/image-956d611f-fb2c-4087-86c7-f330526ca143.png)

- Object Get(string key)
  - Example
  ![image.png](/.attachments/image-3eee3a78-3c45-4316-892e-5095a828066f.png)
