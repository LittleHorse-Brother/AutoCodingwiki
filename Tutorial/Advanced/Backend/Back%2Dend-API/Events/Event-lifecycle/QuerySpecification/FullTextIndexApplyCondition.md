# Summary
`FullTextIndexApplyConditon` was designed to provide full-text index queries, which need to be supplemented in their own right.

# Class Definition
![image.png](/.attachments/image-8563c36e-c9f7-453c-b400-3b7e516e4f06.png)
- SqlScript：Full text index related scripts that are loaded before the queried conditions and after the queried table. For example：`select * from {table} {FullTextIndexApplyConditon.SqlScript} where {condition}`
- Parameters： There may be parameters in the script that require the parameter names and values to be deposited into the `Parameters`.

# Example
![image.png](/.attachments/image-e2f2bddd-0206-479a-ada6-a32c23e16466.png)