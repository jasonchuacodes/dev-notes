Here's an example where the About page is lazy loaded into the browser only upon request.
```js
const About = () => import(/* webpackChunkName: "about"*/ '../views/About.vue')

const routes = [
  ...
  {
    path: '/about',
    name: 'About',
    component: About
  }
]
```

Normally, we would import a page like About.vue and use it as the definition of the `component` route.
But with lazy loading, we instead create a constant like `const About` which points to the About.vue page and use that constant for the route component option instead.