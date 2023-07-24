routeMiddleware is ran for those pages where the middleware is defined. This is for route redirects incase the user is not authorized to visit a certain page.
Here's an example on how to set it up:
```js
export default defineNuxtRouteMiddleware((routeTo, _routeFrom) => {
  const isConnected = useCookie("is-connected").value;
  const privateRoutes = ["profile", "edit-campaign"];

  if (!isConnected && privateRoutes.includes(String(routeTo?.name) ?? "")) {
    return navigateTo({ name: "index" });
  }
});
```

______
### The problem with pinia state and routeMiddleware

I had with the problem I encountered with Nuxt middleware (for route-protection) and pinia state.
Apparently, on initial load, pinia state is null whilst it is initializing. If there is logic being set that is dependent on pinia state (i.e. redirect if isConnected is false), this will cause problems on  page refresh because Nuxt won't wait for pinia to finish loading and thus will automatically redirect to the public route even though isConnected is true.

Using pinia state is essentially the wrong way of implementing route-protection.
Instead, we make use of cookies. Set the cookie on login and access it within the middleware logic.
Problem fixed :emo_roger:

Sidenote:
Nuxt has a composable for cookies called useCookie.
Here's how it is used:
```js
const myCookie = useCookie("is-connected")

myCookie.value = "true"; // this will save the cookie

//alternatively, 
useCookie("is-connected").value = null // this will remove the cookie
```
