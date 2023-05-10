In TypeScript, you can define the types of function parameters and return values using type annotations. Here's an example:
```ts
function add(x: number, y: number): number {
  return x + y;
}
```
In this example, the `add()` function takes two parameters of type `number`, and returns a value of type `number`. The function signature includes the types of the parameters and the return value, separated by colons.

You can also use type aliases to define more complex types for function parameters and return values. For example:
```ts
type Person = {
  name: string;
  age: number;
};

function getFullName(person: Person): string {
  return `${person.name} (${person.age})`;
}
```

To specify the type of a function that returns a promise, you can use the `Promise` type, along with the type of the resolved value. For example:
```ts
function fetchData(): Promise<Person[]> {
  return fetch('/api/people').then(response => response.json());
}
```
In this example, the `fetchData()` function returns a promise that resolves to an array of `Person` objects. The function signature includes the `Promise<Person[]>` type as the return value type.