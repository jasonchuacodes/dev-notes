
### Type annotation
This is the common way of handling types for props and functions. 
The syntax `(prop: PropTypes)` is a type annotation that specifies the expected type of the `error` parameter. It is used in function or method parameter declarations to indicate the type of the parameter. 
```js
const handleChange = (e: InputEvent): void => {
};
```

### Type Assertion
The syntax `(error as { code: string })` is a type assertion in TypeScript. 
It allows you to tell the TypeScript compiler that you know more about the type of a value than TypeScript can infer on its own. In this case, it's used to inform TypeScript that the `error` variable should be treated as an object with a `code` property of type `string`.

```js
catch (error) {
  if ((error as { code: string }).code === "UNCONFIGURED_NAME") return null;
  toast.error("Something went wrong!");
}
```