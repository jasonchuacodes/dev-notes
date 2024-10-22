Here's sa comprehensive example on how to setup a graphql schema

Let's define the threads schema:

```graphql
// threads.graphql

"A thread started by a user"
type Thread {
    id: UUID!
    name: String!
    type: String!
    userId: UUID!
    user: User @belongsTo
    createdAt: DateTime!
    updatedAt: DateTime!
}

"Input for creating threads."
input CreateThreadInput {
    name: String! @rules(apply: ["required"])
    organizationId: String!
    type: String!
}

"Input for updating threads."
input UpdateThreadInput {
    id: String! @rules(apply: ["min:8", "max:36", "required"])
    name: String
        @rules(apply: ["min:5", "max:250", "unique:threads,name", "required"])
}

"Input for deleting a thread."
input DeleteThreadInput {
    id: String! @rules(apply: ["required"])
}
```

```graphql
// schema.graphql

#import threads.graphql

type Query {
    threads(
        name: String!
        organizationId: String!
    ): [Thread!]! @paginate(defaultCount: 10)
}

type Mutation {
    createThread(input: CreateThreadInput! @spread): Thread
        @guard
        @canModel(
            ability: "create"
            injectArgs: true
            model: "App\\Models\\Thread"
        )
        @field(resolver: "App\\GraphQL\\Mutations\\CreateThreadMutation")
    
    updateThread(input: UpdateThreadInput! @spread): Thread
        @guard
        @canModel(
            ability: "update"
            injectArgs: true
            model: "App\\Models\\Thread"
        )
        @update
}
```
### Notes: 
- As usual in graphql, we define `queries` and `mutations` under their own type in the `schema.graphql` file.
- We can import graphql files by adding an import statement prefixed by a hashtag `#` at the very top of the schema file.
- We can add a description for the graphql types, fields, and inputs by using string literals enclosed in double quotes.
- We can use Laravel Lighthouse's custom directives such as @guard, @rules, @field, @canModel, etc for added functionality.




