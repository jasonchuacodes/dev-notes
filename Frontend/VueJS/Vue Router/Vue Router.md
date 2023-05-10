VueRouter allows you to create and manage different routes for your Vue.js application, allowing users to navigate between different views or pages without triggering a full page reload.

```js
import { createRouter, createWebHistory } from 'vue-router'
import EventListView from '../views/EventListView.vue'
import AboutView from '../views/AboutView.vue'

const router = createRouter({
  history: createWebHistory(import.meta.env.BASE_URL),
  routes: [
    {
      path: '/',
      name: 'event-list',
      props: true,
      component: EventListView,
    },
    {
      path: '/about',
      name: 'about',
      component: AboutView,
    },
  ],
})

export default router
```

#### Using router-links
```js
<template>
  <router-link to="/about">About</router-link>
</template>

<script>
import { RouterLink } from 'vue-router';

export default {
  components: {
    RouterLink
  },
  // ...
}
</script>
```
