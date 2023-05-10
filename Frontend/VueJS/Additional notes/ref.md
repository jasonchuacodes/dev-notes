In Vue.js, `ref` is a function provided by the Vue.js library that creates a reactive reference to a value. This means that when the value changes, any component that uses the ref will automatically be updated to reflect the new value.

For example, consider the following code:
```js
import { ref } from 'vue'

const count = ref(0)

count.value++ // This will trigger a re-render in any components that use `count`
```

Notice that 'count' isn't called directly - instead we use the property .value.
When a value is wrapped in a `ref`, it becomes an object with a `value` property that holds the actual value.