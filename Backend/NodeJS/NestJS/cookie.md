#### Purpose
setting cookies in the request response.

#### Usage

```js
async login(
  @Res({ passthrough: true}) response: Response
) {

  const jwt = 'custom_token'
  
  response.cookie('jwt', jwt, {httpOnly: true})

  return {
    message: "Success"
  }
}

```

#### Notes
`passthrough: true` is set to indicate that the response object should be returned to the calling function after it is modified.

By default, the response object is not returned to the calling function, but rather handled internally by NestJS. However, by using the `@Res({ passthrough: true })` decorator, you can modify the response object and return it to the calling function for further processing.

`httpOnly:true` is set to prevent client-side JavaScript from accessing the cookie. This increases the security of the cookie by preventing cross-site scripting (XSS) attacks from stealing the cookie data.