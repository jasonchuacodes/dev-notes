CSRF token mismatch error on a [[React]] | [[Laravel]] project when doing axios.post request.
-   Solution - configure `.env` file and add `SANCTUM_STATEFUL_DOMAINS=localhost`

 There's an article about laravel sanctum setup for SPA authentication but it is with Vue. 
 The concepts are very much applicable with a React Project though. 
 Read more about it here - (https://blog.codecourse.com/setting-up-laravel-sanctum-airlock-for-spa-authentication-with-vue)