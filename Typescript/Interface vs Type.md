`Interfaces` are best suited for defining the type of an Object.
`Type` is for general use. Also with type, we can make use of the union operator `|` where we can set multiple values for the type.

Here's an example of a Type used for constants or variables:
```ts
type buttonType = 'primary' | 'secondary' | 'success' | 'danger'
```
Here's an example of an Interface to be used for Objects:
```ts
interface IPerson {
	name: string; 
	age: number; 
	activeAvenger: boolean; 
	powers: string[];
}
```

___
#### How do we use these types?

We can apply the type by appending it to the variables or constants. 
In this example below, having the type can ensure that all `buttonType` variables have the correct value.
```ts
type buttonType = 'primary' | 'secondary' | 'success' | 'danger'

// TypeScript will report an error because this doesn't exist in the type! 
const errorBtnStyles: buttonType = 'error' 

// This variable is type safe! 
const dangerBtnStyles: buttonType = 'danger'
```


For Interfaces, we can use it much like types by appending it to the Object name.
```ts
interface IPerson {
	name: string; 
	age: number; 
	activeAvenger: boolean; 
	powers: string[];
}

let person: IPerson = { 
	name: 'Peter Parker', 
	age: 20, 
	activeAvenger: true, 
	powers: ['wall-crawl', 'spider-sense'] 
}