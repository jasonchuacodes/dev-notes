`filter()` - returns an item that passes the condition being set.

#### Usage
```js
const products = [
 { id: 1, title: "a" }, 
 { id: 2, title: "b" }, 
 { id:3, title: "aa" }
]

const search = "a"

products.filter( p => p.title.indexOf(search) >= 0) 
// this will return id's 1 and 3 since it matches the search value
```


alternatively, we can use includes()
```js
products.filter(p => p.title.includes(s))
// this will still return id's 1 and 3
```
