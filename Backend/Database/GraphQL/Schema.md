Typedefs - otherwise known as type definitions are descriptions of data type and the relationship they have with other data types. Essentially, a schema.

```gql
const typeDefs = `#graphql  
  type Game {
    id: ID!
    title: String!
    platform: [String!]!
    reviews: [Review!]
  }

  type Review {
    id: ID!
    rating: Int!
    content: String!
    game: Game!
    author: Author!
  }

  type Author {
    id: ID!
    name: String
    verified: Boolean
    reviews: [Review!]
  }

  type Query {
    reviews: [Review]
    review(id: ID!): Review
    games: [Game]
    game(id: ID!): Game
    authors: [Author]
    author(id: ID!): Author
  }
`

module.exports = { typeDefs }
```

Notes:
- Available types are `Int`, `Float`, `String`, `Boolean`, and `ID` 
- The bang(!) symbol signifies a required field
- The `type Query` is required in every graphql schema. This defines the entry point to the graph and specify the return types of those entry points.