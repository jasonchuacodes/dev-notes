`reduce()` -  used to apply a specific function (known as a reducer) to all the elements of an array and reduce them to a single value.

#### Usage
array.reduce(callback, initialValue)

```js
const numbers = [1, 2, 3, 4, 5]; 

const sum = numbers.reduce((acc, curr) => { 
	return accumulator + currentValue; 
}, 0); 

console.log(sum); // Output: 15
```

