The framework that I used for Javascript is [[React]].

Here are some helpful methods in Javascript.

- `map()`
- `keys()`
You can use map() in combination with keys() to get the values and keys of a given array.

Suppose you have an object `myObj`:
```js
const myObj = { foo: 1, bar: 2, baz: 3 };
```

You can get an array of the keys in `myObj` using the `Object.keys()` method:
```js
const myKeys = Object.keys(myObj);

console.log(myKeys);
// Output: ['foo', 'bar', 'baz']
```

You can then use the `map()` method to transform the `myKeys` array into a new array of objects with each object containing the key, index, and corresponding value from `myObj`:
```js
const mappedArray = 
	Object.keys(myObj).map((key, index) => {
	  return {
	    key: key,
	    index: index,
	    value: myObj[key]
	  };
	});

console.log(mappedArray);
// Output: [
//   { key: 'foo', index: 0, value: 1 }, 
//   { key: 'bar', index: 1, value: 2 }, 
//   { key: 'baz', index: 2, value: 3 }
// ]

```



- `filter()`
- `reduce()`


