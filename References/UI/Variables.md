## Condition Expression

- Current Entity field name start with "$".
- Global entity variable name starts with "@".
- Multiple conditions can be connected by "and" | "or".
  - Support parentheses.
- Global entities: config, currentAgent, site.features, site.products, query.

<details>
<summary>Example</summary>

Below is a condition expression.

`@site.features.multipleKnowledgebase == true and @site.products.bot == false`

</details>

<br>
<br>

## String Template

- Current Entity field name start with "$".
- Global entity variable name starts with "@".
- Global entities: config, currentAgent, site.features, site.products, query.

<details>
<summary>Example</summary>

Below is a string template.

`https://@config.kbFrontDomain/kb/@siteId/\$category.kbId-/$id`

</details>