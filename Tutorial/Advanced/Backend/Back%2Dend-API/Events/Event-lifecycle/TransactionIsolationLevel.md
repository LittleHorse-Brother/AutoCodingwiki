# Summary
TransactionIsolationLevel is a property that is present in the EntityPreEvent. Before opening a transaction, modify its value and can act to modify the transaction isolation level.

# Class Definition
- ![image.png](/.attachments/image-5f7cfb28-f101-4df1-b2a5-420c852db8a4.png)

# How to use
- The The transaction segregation level is modified by assigning a value to the `TransactionIsolationLevel.IsolationLevel` only if there is a TransactionIsolationLevel in the `EntityPreEvent`.
- `TransactionIsolationLevel.IsolationLevel`is the system IsolationLevel type and is required to use System.Data namespace.
Example:
![image.png](/.attachments/image-379c3087-f490-46c6-a100-b692dc6b5a27.png)


