# Command-Query Segregation - CQS
created:: 2024-09-20 08:12
status:: #zettel/fleeting
tags::

- The CQS say that an endpoint is command or query. In other words, a post or update endpoint per example, can't return anything when a query can't perform changes. This practice avoid side-affect.

# References
-  [How to Design & Persist Aggregates - Domain-Driven Design w/ TypeScript | Khalil Stemmler](https://khalilstemmler.com/articles/typescript-domain-driven-design/aggregate-design-persistence/)

