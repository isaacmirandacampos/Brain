# Graphql Advantages
created:: 2024-07-07 23:43
status:: #zettel/permanent 
tags:: #database #pattern

### The problems
-  **Over fetching**: When we use api rest, we sometimes need make multiple requests to get all data that needs, which is ineffective.
- **Under fetching**: A other case is when we have that endpoints, but the screen do not need all data which is ineffective because the request is more weight.
#### How to solve
In graphql we can make resolvers, that are similar the controllers of api rest, that allows us combined them and make a single custom request that will get all data we needed in page.
#### Considerations
The graphql add a schema between backend and frontend, allowing the backend and frontend team working separable, the frontend do not need maintain a constant communication with backend team to request the data. 

