# Summary
`ExpressionCondition` is designed to solve the problem that a query condition needs to filter multiple fields with certain logic. An `ExpressionCondition` can contain multiple sub conditions,and complex queries including logical expressions can be realized by constructing `ExpressionCondition`.
# Class Definition
- Conditions
  - `IList<BaseConditionItem>`
  - Each [BaseConditionItem](https://dev.azure.com/Comm100/Auto%20Coding/_wiki/wikis/Auto-Coding.wiki/703/BaseConditionItem) represents a sub condition.

- ExpressionType
  - `enum`
    - `all`: Connect each condition with `and` connector, and each sub condition should be satisfied
    - `any`: Connect each condition with `or` connector, only any condition is satisfied
![image.png](/.attachments/image-8df8ada8-7e9c-4ef8-8d62-024fd69cff9f.png)
    - `logicalExpression`: All the sub conditions are connected in the form of logical expressions, and the current `ExpressionCondition` is true。
- ExpressionStr
  - `string`
  - Available when `ExpressionType` is `logicalExpression`. 
  - Logical expression string.
  <details>
  <summary>Example:</summary>

  If you have 5 conditions, you can use Expression like (1 or 2 or 3) and (4 and 5). This expression means the rule will be triggered when any of the 1 to 3 conditions is met as well as condition 4 and condition 5 are met. The number here is `BaseConditionItem.OrderNum`.
  </details>