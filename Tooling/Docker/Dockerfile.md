```js
FROM node:16.16.0-alpine

WORKDIR /app

COPY package.json /app

RUN yarn install --frozen-lock

COPY . . 

CMD ["yarn", "start"]

```