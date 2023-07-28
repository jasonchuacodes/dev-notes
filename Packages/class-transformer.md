#### Installation
`npm install class-transformer --save`

Additionally, `reflect-metadata` shim is required, install it too:
`npm install reflect-metadata --save`

#### Purpose
To transform the returned response of a http request. Usually used when adding an exception to the response. i.e. excluding password or password_confirm in the return body.