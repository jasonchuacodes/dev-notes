Laravel Lighthouse is a popular GraphQL server package for Laravel applications.

## Installation
`composer require nuwave/lighthouse`

## Schema
Uses SDL (Schema Definition Language) for defining types, queries, and mutations.
```graphql
type User {
    id: ID!
    name: String!
    email: String!
    posts: [Post!]! @hasMany
}
```

## Resolvers
- Automatically resolves fields based on Eloquent relationships.
- Custom resolvers can be defined using the `@field` directive or by creating resolver classes.

## Directives
- Provides a wide range of built-in directives for common operations.
- Allows creation of custom directives for specialized logic.
