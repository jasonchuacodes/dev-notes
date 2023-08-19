#### Installation
`npm install @faker-js/faker --save-dev`

#### Purpose
to create dummy data for models/entities

#### Usage
```js
import { faker } from '@faker-js/faker';

const randomName = faker.person.firstName(); // Rowan Nikolaus
const randomEmail = faker.internet.email(); // Kassandra.Haley@erich.biz

```

#### Note
Faker is a method. 
It needs to be used as `faker.person.firstName()` - not `faker.person.firstName`