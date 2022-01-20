# QuerySpecification
## Filter
### Properties
- Filter
  - `Dictionary<string,onject>` key ignore case
### Functions
- ApplyFiltering(IDictionary<string,object[]> filters)
  - Add additional `filters`to the filter

## Sorting
### Properties
- IsSorting
  - `bool`
- SortBy
  - `string`
- SortOrder
  - `enum`: `asc` `desc`
### Functions
- ApplySorting(string sortBy, EnumSortOrder sortOrder)
  - IsSorting is set to true regardless of the previous value.

## Include
### Properties
- Include
  - `string[]`
### Functions
- ApplyIncluding(string[] include)
  - replace the original include

## Pagination
### Properties
- PageIndex
  - `int`
- PageSize
  - `int`
- IsPagination
  - `bool`
### Functions
- ApplyPaging(int index, int size)
  - IsPagination is set to true regardless of the previous value.

## IsIncludeDeleted
If the `entity.DeletePolicy` is soft(0), the already deleted data can be queried by `IsIncludeDeleted` parameters.
### Properties
- IsIncludeDeleted
  - `bool`
### Functions
- ApplyIncludeDeleted(bool isIncludeDeleted)
  -  Assign a value to `IsIncludeDeleted`.

## ExpressionCondition
Complex condition queries can be done by constructing [ExpressionCondition](https://dev.azure.com/Comm100/Auto%20Coding/_wiki/wikis/Auto-Coding.wiki/699/ExpressionCondition). For example：`Contact.Name` like @parameter or `ContactIdentity.Value` like @Parameter
### Properties
- ExpressionConditions
  - [`IList<ExpressionCondition>`](https://dev.azure.com/Comm100/Auto%20Coding/_wiki/wikis/Auto-Coding.wiki/699/ExpressionCondition)
### Functions
- ApplyExpressionCondition([ExpressionCondition](https://dev.azure.com/Comm100/Auto%20Coding/_wiki/wikis/Auto-Coding.wiki/699/ExpressionCondition) expressionCondition)
  - 在已有的ExpressionConditions列表中添加新的[ExpressionCondition](https://dev.azure.com/Comm100/Auto%20Coding/_wiki/wikis/Auto-Coding.wiki/699/ExpressionCondition).

## FullTextIndex
Full text index filtering conditions are provided
### Properties
- FullTextIndexApplies
  - [`IList<FullTextIndexApplies>`](https://dev.azure.com/Comm100/Auto%20Coding/_wiki/wikis/Auto-Coding.wiki/701/FullTextIndexApplyCondition)
### Functions
- ApplyFullIndexApply([FullTextIndexApplyCondition](https://dev.azure.com/Comm100/Auto%20Coding/_wiki/wikis/Auto-Coding.wiki/701/FullTextIndexApplyCondition) fullTextIndexApplyCondition)
  - Additional full text index query condition. 