```js
// filepath: src/resolvers
const { games, authors, reviews } = require("./lib/data");

const resolvers = {
	Query: {
		// For fetching a list of items
		games: {
			return games
		},
		reviews: {
			return reviews
		},
		author: {
			return authors
		},
		
		// For fetching a single item, we need to use the args argument. The _parent is an argument that we do not need yet for fetching a single item - hence the _underscore. 
		// In the ApolloSandbox query, we can pass the ID as a variable in the query.
		game(_parent, args) {
			return games.find((game) => game.id === args.id)
		},
		author(_parent, args) {
			return authors.find((author) => author.id === args.id)
		}
	},
	// For fetching nested data, we need define a new `key` that matches the type and field in the schema. 
	Game: {
		reviews(parent) {
			return reviews.filter((review) => review.game_id === parent.id)
			// Notice here that we are using the parent.id as the filter value for the reviews. The parent.id value points to the parent model which is `Game`
		}
	},
	Author: {
		reviews(parent) {
			return reviews.filter(() => review.author_id === parent.id)
		}	
	},
	Review: {
		game(parent) {
			return games.find((game) => game.id === parent.game_id) 
			// Notice here that we are using the game_id property from the parent `Review` model to find the game item.
		},
		author(parent) {
			return authors.find((author) => author.id === parent.author_id)
		}
	}
}

```

_____
For the purpose of testing, I've created a hard-coded dummy data for games, authors, and reviews. 
In a real-world application, these data can be queried from a database.
```js
// filepath:  lib/data
const games = [
    {id: '1', title: 'Zelda - Breath  of the Wild', platform: ['Switch'],},
    {id: '2', title: 'Resident Evil', platform: ['Switch', 'PS5', 'PC'],},
    {id: '3', title: 'Witcher 3 - Bloodhunt', platform: ['Switch', 'PS5'],}
]

const authors = [
    { id: '1', name: 'Mario', verified: true},
    { id: '2', name: 'Yoshi', verified: false},
    { id: '3', name: 'Peach', verified: true},
]

const reviews = [
    { id: '1', rating: 9, content: 'zelda botw is very fun', author_id: '1', game_id: '1'},
    { id: '2', rating: 10, content: 'zelda totk is better', author_id: '2', game_id: '1'},
    { id: '3', rating: 7, content: 'jumpscare go brrt', author_id: '3', game_id: '2'},
    { id: '4', rating: 5, content: 'very scary', author_id: '1', game_id: '2'},
    { id: '5', rating: 9, content: 'the lore and story is awesome!', author_id: '1', game_id: '3'},
]

module.exports = { games, authors, reviews }
```