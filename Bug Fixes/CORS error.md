#### Problem
receiving the ff error when doing a POST request.
``"CSRF token mismatch"``
``"CORS error"``

This is caused by a mismatch on the port being used on the Frontend React(port:3000) vs Backend Laravel(port:8000).

#### Solution
configure `.env` file and add `SANCTUM_STATEFUL_DOMAINS=localhost`

There's an article about Laravel sanctum setup for SPA authentication but it is with Vue. 
 The concepts are very much applicable with a React Project though. 
 Read more about it here - (https://blog.codecourse.com/setting-up-laravel-sanctum-airlock-for-spa-authentication-with-vue)


#### Notes
for projects using NestJS for BE, this can be fixed by enabling Cors in the Nest application.
```js
const app = await NestFactory.create(AppModule);

app.enableCors({
	origin: ['http://localhost:3000', 'http://localhost: 8080'] // insert port being used here
	credentials: true
})
```