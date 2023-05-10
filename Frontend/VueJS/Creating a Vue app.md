In order to create a vue application, simply run the command `npm init vue@latest` in the terminal. Prompts will appear like naming the file and adding common plugins.

Or if you want customize the vue create setup by adding specific plugins and others, create the app via the vueCLI instead. 
	`npm install -g @vue/cli` 
	`vue --version` 
	`vue create my-vue-app`

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <link rel="icon" href="/favicon.ico" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>Vite App</title>
  </head>
  <body>
    <div id="app"></div>
    <script type="module" src="/src/main.js"></script>
  </body>
</html>
```

#### main.js 
```js
import { createApp } from 'vue'
import { createPinia } from 'pinia'

import App from './App.vue'
import router from './router'

const app = createApp(App)

app.use(createPinia())
app.use(router)

app.mount('#app')
```

