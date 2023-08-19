`slice()` - returns a sliced array based based on the params set.


#### Usage
Takes two params, for start and end of slice.
```js
array.slice(start,end)
```

#### Techniques
slice is a highly used function in pagination logic.
```js
products = [...];

page = 1
perPage = 9

products = products.slice((page - 1) * perPage, page * perPage)
```

if page = 1 and perPage = 9
```js
products.slice((1-1)* 9, 1*9)

products.slice(0,9) // takes the first set of 9 product items
```

if page = 2
```js
products.slice((2-1)* 9, 2*9)

products.slice(9,18) // takes the second set of 9 product items
```