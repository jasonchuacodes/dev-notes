Read the Getting Started documentation here: [graphql docs](https://graphql.org/graphql-js/)

```js
const { games, reviews } = require('./database/sample_data')
const resolvers = require('./src/resolvers')
const typeDefs = require('./src/schema')

const apolloPort = 4000;

const server = new ApolloServer({
  typeDefs, 
  resolvers, 
});


const startApollo = async () => {
  try {
    const { url } = await startStandaloneServer(server, {
      listen: { port: apolloPort },
    });
    console.log(`🚀  Apollo Server ready at: ${url}`);
  } catch (error) {
    console.error("Error starting the server:", error);
  }
}

startApollo();

app.listen(port, () => {
  console.log(`Express App listening on port ${port}`);
});
```


Notes:
Resolvers must use the keys to match the types and fields in the schema.
	Query: This corresponds to the root query type in your schema. The keys within the `Query` resolver (like `games`, `reviews`, `authors`, `review`, `game`, `author`) must match the query fields defined in your schema.
	