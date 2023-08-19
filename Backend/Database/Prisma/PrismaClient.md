#### Installation
```sh
npm install @prisma/client
```

#### Usage
Prisma Client is a type-safe database client that's generated from your Prisma model definition.

```js
import { PrismaClient } from '@prisma/client'

const prisma = new PrismaClient()

async function main() {
	// insert prisma query
}

main()
	.then(async () => {
		await prisma.$disconnect()
	})
	.catch(async (e) => {
		console.error(e)
		await prisma.$disconnect()
		process.exit(1)
	})
```

___
When used in a framework such as NestJS, we no longer have the need to setup the Prisma client as shown above. 
Instead, we abstract it into a prisma service.
Here's how that's done:

```js
// ./shared/prisma.service.ts

import { Injectable, OnModuleInit } from '@nestjs/common';
import { PrismaClient } from '@prisma/client';

@Injectable()
export class PrismaService extends PrismaClient implements OnModuleInit {
  async onModuleInit() {
    await this.$connect();
  }
}
```