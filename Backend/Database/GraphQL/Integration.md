To use the `GameQuery` GraphQL query in your frontend (FE) application, you'll typically use a GraphQL client library such as Apollo Client. Apollo Client is a popular choice for integrating GraphQL into frontend applications. Below, I'll outline the steps to set up Apollo Client in a React application and use the `GameQuery` to fetch and display data.

#### Setting up and using Apollo Client in FE:
1. Install Apollo Client and GraphQL.
   `npm install @apollo/client graphql`
   
2. Setup Apollo Client.
Set up Apollo Client in your application. This usually involves creating an Apollo Client instance and wrapping your application with the `ApolloProvider` component.
```js
// src/apolloClient.js
import { ApolloClient, InMemoryCache, ApolloProvider } from '@apollo/client';
import React from 'react';
import ReactDOM from 'react-dom';
import App from './App';

const client = new ApolloClient({
  uri: 'http://localhost:4000/graphql', // Your GraphQL server URI
  cache: new InMemoryCache(),
});

ReactDOM.render(
  <ApolloProvider client={client}>
    <App />
  </ApolloProvider>,
  document.getElementById('root')
);
```

3. Create the `GameQuery`.
Define the `GameQuery` in your frontend code. You can use Apollo Client's `gql` template literal to parse the query.
``` js
// src/queries.js
import { gql } from '@apollo/client';

export const GAME_QUERY = gql`
  query GameQuery($id: ID!) {
    game(id: $id) {
      platform
      title
      reviews {
        content
        author {
          name
        }
      }
    }
  }
`;
```

4. Use the Query in a React Component.
```js
import { useQuery } from '@apollo/client';

const GameDetails = ({ gameId }) => {
	cosnt { data } = useQuery(GAME_QUERY, {
		variables: { 
			id: gameId // This is where we insert the variable for fetching a single item
		}
	})

	const { game } = data;

	return (
		<div>
			<h1>{game.title}</h1>
			<h2>Reviews</h2>
			<ul>
				{game.reviews.map((review, index) => (
					<li key={index}>
					<p>{review.content}</p>
					<p>Author: {review.author.name}</p>
					</li>
				))}
			</ul>
		</div>
	)
}

export default GameDetails
```