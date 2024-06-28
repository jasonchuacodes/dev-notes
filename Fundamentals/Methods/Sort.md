`sort()` - is a compare function used to sort the elements of an array in place. The resulting value (positive or negative) of the comparison will determine the order of the items.

#### Usage
```js
products.sort((a, b) => a.price - b.price);

// (-) - a comes before b 
// (+) - b comes before a
// 0 - order remains the same
```
