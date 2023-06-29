Composables in Vue are a way to encapsulate and reuse logic in a composable function format. They allow you to separate concerns and create reusable code that can be easily shared and composed within your Vue components. 

Composables are typically created using Vue's Composition API, which provides hooks-like functions such as `ref`, `reactive`, and `computed`.

Here's an example:
```js
// src/composables/useCounter.js
import { ref } from 'vue';

// Define a composable function
export function useCounter(initialValue) {
  const count = ref(initialValue);

  function increment() {
    count.value++;
  }

  function decrement() {
    count.value--;
  }

  return {
    count,
    increment,
    decrement
  };
}
```

To use this composable in a Vue component, we can import and invoke it:
```js
// src/components/counter.js
<script setup> 
import { useCounter } from './useCounter';

const { count, increment, decrement } = useCounter(0);
};
</script>

<template>
  <div>
    <p>Count: {{ count }}</p>
    <button @click="increment">Increment</button>
    <button @click="decrement">Decrement</button>
  </div>
</template>

```