#### Purpose
if there are service functions that are reusable (such as create, edit, find, delete), it would be best to create an abstract service for this. This would follow the DRY - don't repeat yourself - principle.

#### Usage

Here's how the code would look like for the `AbstractService`. 
Take note that in the constructor it requires a repository.

```js
import { Repository } from "typeorm";

export class AbstractService {
    protected constructor(
        protected readonly repository: Repository<any>,
    ) {}

    async save(options) {
        return this.repository.save(options);
    }

    async findBy(options) {
        return this.repository.findBy(options);
    }
    
    async findOneBy(options) {
        return this.repository.findOneBy(options);
    }

    async update(id: number, options) {
        return this.repository.update(id, options);
    }
}
```

To use our newly created abstractService, we'll extend our class to the abstractService class.
`super()` is a reference to the base class constructor to fill the required `repository` value.

```js
export class UserService extends AbstractService {
    constructor(
      @InjectRepository(User) 
      private readonly userRepository: Repository<User>
    ){
      super(userRepository)
    }
}
```