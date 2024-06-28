Testing the graphql schema can be done in Apollo Sandbox. 
When a StandAloneServer is already setup, we can visit the port where the ApolloServer is running.

In this example, the example [[Backend/Database/GraphQL/Setup|setup]] is running in `port 4000`.

Example #1:
Let's define a GamesQuery and that fetches all the games with their title:
```
query GamesQuery {
	games {
		title
	}
}

/** 
	{
	  "data": {
	    "games": [
	      {
	        "title": "Zelda - Breath  of the Wild"
	      },
	      {
	        "title": "Resident Evil"
	      },
	      {
	        "title": "Witcher 3 - Bloodhunt"
	      }
	    ]
	  }
	}
*/
```
this games query returns the a JSON data of all the games with their title:

____
Example #2: 
This sample query showcases nested queries for a selected game.
In order to pass the $id of the query, we just have to set the JSON `variables` in the query.
```
// JSON variables
{
  "id": "1"
}
```

```
query GameQuery($id ID!) {
	game(id: $id) {
		title,
		platform,
		reviews {
			content,
			author {
				name
			}
		}
	}
}

/**
{
  "data": {
    "game": {
      "platform": [
        "Switch"
      ],
      "title": "Zelda - Breath  of the Wild",
      "reviews": [
        {
          "content": "zelda botw is very fun",
          "author": {
            "name": "Mario"
          }
        },
        {
          "content": "zelda totk is better",
          "author": {
            "name": "Yoshi"
          }
        }
      ]
    }
  }
}
*/
```
