#### Purpose
Encapsulates logic for reusable functions across multiple child classes.
In this example, we extract the reusable functions findby, findall, create, update, and delete functions into one service.

We then make this service injectable so that other specific services (i.e. UserService, ProductService) may extend from this.
#### Usage
```js
// abstract.service.ts
import { Injectable } from '@nestjs/common';
import { Prisma } from '@prisma/client';
import { PrismaService } from './prisma.service';

@Injectable()
export class AbstractService {
  constructor(
    protected prisma: PrismaService,
    protected modelname: Prisma.ModelName,
  ) {}

  async findAll() {
    return await this.prisma[this.modelname].findMany();
  }

  async findManyBy(option: Prisma.UserWhereInput) {
    const users =  await this.prisma[this.modelname].findMany({
      where: option
    });

    return users;
  }
}
```

```js
// user.service.ts
import { Injectable } from '@nestjs/common';
import { PrismaService } from 'src/shared/prisma.service';
import { AbstractService } from 'src/shared/abstract.service';

@Injectable()
export class UserService extends AbstractService{
  constructor(prisma: PrismaService) {
    super(prisma, "User")
  }
}

```