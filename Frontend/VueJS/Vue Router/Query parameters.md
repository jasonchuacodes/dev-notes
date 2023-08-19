How do we read query paramaters off the URL?
```
http://localhost:8080/events/events?page=4
```

From the component code, you can access it by adding $this
```js
computed: {
	page() {
		return parseInt(this.$route.query.page) || 1
		// returns the query page = 4
	}
}
```

From the template, you can access it using `$route.query`
```jsx
<h1> You are on page {{ $route.query.page }} </h1>
```
