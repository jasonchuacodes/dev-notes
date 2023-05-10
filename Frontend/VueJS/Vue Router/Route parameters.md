What if we wanted `page` to be part of the URL?
```
http://localhost:8080/events/4
```

Use a Route parameter:
```js
const routes = [
  ...
  { 
   path: '/events/:page', 
   component: Events
   }
]

// It's the colon [:] on :page that's making it a route parameter
```
``

Access it from the template like this: 
```jsx
<h1> You are on page {{ $route.params.page }} </h1>
```

____

#### Props option
Alternatively, we can configure the route to have a `props` option.
```jsx
const routes = [
  ...
  { 
   path: '/events/:page', 
   component: Events,
   props: true
   }
]
```

From the template, add props in the script before using
```jsx
<template>
  <h1> You are on page {{ page }} </h1>
</template>

<script>
export default {
  props: ['page']
}
</script>
```