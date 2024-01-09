Used to watch for any updates on the value of a reactive item.

The syntax for setting up a watch method is as follows:
```js
const state = reactive({ count: 0 }) 

watch(
	() => state.count, 
	(count, prevCount) => { /* ... */ } 
)
```

This is particularly useful as in route changes. In the example below, we are updating the localstorage `hash` value whenever the route hash changes.
```js
onMounted(() => {
	// in Nuxt3, we have to check if we are on CSR (client-side rendering since localStorage is not available on SSR. Hence, the need for process.client)
    if (process.client) {
      currentHash.value = localStorage.getItem('hash') || '#home'
    }

    watch(() => route.hash, (_oldHash, newHash) => {
      currentHash.value = newHash
      localStorage.setItem('hash', newHash)
    })
  });
```