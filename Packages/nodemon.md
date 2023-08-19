#### Installation
```sh
npm install nodemon --save-dev
```

#### Purpose
To watch for file changes and automatically restart the node server. Otherwise, you'll need to manually restart this in order for any file changes to reflect (i.e. controller, service, etc.).

#### Usage
In your package.json file, configure the script for `start:dev`
```json
"scripts": {
  "start:dev": "nodemon --exec ts-node -r tsconfig-paths/register src/main.ts"
}
```

now you can restart your server once and this will reflect.
