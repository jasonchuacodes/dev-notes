Setting up functions between parent-child components is not as straightforward as in single component.
In order to update the parent component’s value, our child-component needs to emit the event.
Once the event is emitted, this can then be listened to by the parent component.

Here’s that in action:
Our button component (child) is emitting an add-count event where we gave num a value of 1.
When this button is clicked, the event is fired and the counter component (parent) listens for it. When this happens, the addCount function is going to be fired.

// button.ts
```ts
<script setup lang="ts">

const emit = defineEmits<{ 
  (event: 'add-count', num: number): void  
  (event: 'reset-count'): void 
}>()

</script>

<template>
  <p>
    <button @click="emit('add-count', 1)">Add</button>
    <button @click="emit('reset-count')">Reset</button>
  </p>
</template>
```

// counter.ts
```ts
<script setup lang='ts'>
import AddButton from './AddButton.vue'

const count = ref<number | null>(null)

function addCount(num: number) {
  if (count.value !== null) {
    if (count.value >= props.limit) {
      alert(props.alertMessageOnLimit)
    }
    else {
      count.value += num
    }
  }
}
</script>
<template>
  <p>{{ count }}</p>
  <AddButton 
    @add-count="addCount"
    @reset-count="count = 0"
  ></AddButton>
</template>
```
