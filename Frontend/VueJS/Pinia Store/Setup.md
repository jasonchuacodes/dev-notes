Pinia is a state management system for Vue.js applications.
Pinia uses reactive objects and functions to ensure that changes to state are automatically detected and propagated to all components that depend on that state.

In order to use pinia, we first need to define the pinia store with `defineStore`:
```js
// todoStore.js
import { defineStore } from 'pinia'

export const useTodoListStore = defineStore("todolist", () => {
...
	const todos = ref([]);

	const addTodo = () => {
	...
	}

	const deleteTodo = () => {
	...
	}
	
return {todos, addTodo, deleteTodo}
}
```

The `defineStore` function takes two arguments:
1.  The `id` of the store, which is used to identify the store across the application.
2.  A callback function that *returns* the store's initial state and its methods.
Adding the prefix 'use' is only for naming convention - useNameStore.

In order to use the newly created store, we simply need to import it in the component that will use the store and destructure the states that we will use.
```js
// TodoList.vue component
<script setup>
    import { useTodoListStore } from '../stores/todoStore';
    const {todos} = useTodoListStore();
</script>

<template>
    <div v-for="(todo, index) in todos" :key="index">
        <div class="content">
            <span :class="{ completed: todo.completed }">{{ todo.item }}</span>
        </div>
    </div>
</template>
```
