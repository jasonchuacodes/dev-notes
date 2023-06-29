To declare options like `props` with full type inference support, we can use the `defineProps` API, which are automatically available inside `<script setup>`

// BaseButton.ts
```js
<script setup lang="ts">
interface ButtonProps {
  id: string
  label?: string
}

defineProps<ButtonProps>();
</script>

<template>
  <button :id="id" :label="label">{{ slot }}</button>
</template>
```

// Layout.ts
```js
<script setup lang="ts">
import BaseButton from '@/components/BaseButton'
</script>

<template>
  <h1>Welcome</h1>
  <BaseButton id="my-id" name="sign-in-button">Sign In</BaseButton>
</template>
```

___
### withDefaults()

If needed, we can set the default value of the prop by using `withDefaults()`. It accepts two arguments: 
1.the defineProps<`T`>()
2.the object with the default values

Here's an example of assigning a default label to our Button above:
```js
<script setup lang="ts">
interface ButtonProps {
  id: string
  label?: string
}

const props = withDefaults(defineProps<ButtonProps>(), {
	label: 'My Button'
})
</script>

<template>
  <button :id="id" :label="label">{{ slot }}</button>
</template>
```