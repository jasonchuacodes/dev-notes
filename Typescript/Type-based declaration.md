It is possible and more straightforward to define props with pure types via a generic type argument. This technique is called `type-based declaration` and looks something like this: 
```ts
  type Props = {
    foo: string
    bar?: number
  }

 const props = defineProps<Props>()
```

This is more convenient as opposed to the regular declaration of props and type, like this: 
```ts
  const props = defineProps({
    foo: { type: String, required: true },
    bar: Number
  })
```
