#### Purpose
to seed data to our database entity

#### Usage
Creating seeders in NestJS requires us to create a standalone application. 
Read more about it here: [Standalone application](https://docs.nestjs.com/standalone-applications)

Here's a template for a standalone application. 
```js
const bootstrap = async () => {
  const app = await NestFactory.createApplicationContext(AppModule);

  // insert seeder logic here

  await app.close();
}

bootstrap();
```

____

Now let's build our seeder logic:
```js
(async () =>  {
    const app = await NestFactory.createApplicationContext(AppModule);
    
    const userService =  app.select(UserModule).get(UserService);
    const password = await bcrypt.hash('123', 12);
    
    for (let i = 0; i< 30; i++) {
        await userService.save(
            {
                first_name: faker.person.firstName(),
                last_name: faker.person.lastName(),
                email: faker.internet.email(),
                password,
                is_ambassador: true,
            }
        )
    }
    
    await app.close();
})(); 
// Note that we simplified our bootstap function and called it immediately.
```

___
After we have built our seeder, we need to add a script command in our `package.json` file.

```json
"scripts": {
	"seed:amb": "ts-node ./commands/ambassador.seed.ts"
}
```

Note that we need to install the [[ts-node]] package for this to work.