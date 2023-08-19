```js
version: '3'
services:
  app:
    build:
      context: .
    image: node:latest
    restart: always
    ports: 
      - '3000:3000'
    volumes:
      - .:/app
    depends_on:
      - db
  db:
    image: postgres:latest
    restart: always
    environment:
      POSTGRES_DB: sampledb
      POSTGRES_USER: postgres
      POSTGRES_PASSWORD: postgres
    volumes:
      - pgdata:/var/lib/postgresql/data
volumes:
  pgdata:

```