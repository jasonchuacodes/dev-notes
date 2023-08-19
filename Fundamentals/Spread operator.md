`...`
The spread syntax is a versatile feature in JavaScript that allows you to spread elements from an iterable (like an array or string) or properties from an object.

#### Usage
when used in arrays, the spread syntax spreads the elements or characters individually.
```js
const numbers = [1, 2, 3];
const newArray = [...numbers, 4, 5];

console.log(newArray); // [1, 2, 3, 4, 5]

const str = "hello";
const newString = [...str];
console.log(newString); // ["h", "e", "l", "l", "o"]
```

when used in objects, the spread syntax spreads the properties of the object.
```js
const obj1 = { x: 1, y: 2 };
const obj2 = { z: 3 };

const mergedObj = { ...obj1, ...obj2 };

console.log(mergedObj); // { x: 1, y: 2, z: 3 }

```


#### Techniques
In this example below, `...` is used in conjunction with object destructuring to separate specific properties from an object. 

In this case, we have separated the `password_confirm` property from the `person` object.
```js
const person = {
  first_name: "John",
  last_name: "Doe",
  password: "123",
  password_confirm: "123"
}

const {password_confirm, ...data} = person

console.log(data) // { first_name: "John", last_name: "Doe", password: "123" }

console.log(password_confirm) 
//{ password_confirm: "123" }
```
