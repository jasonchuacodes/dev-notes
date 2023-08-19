#### Purpose
Similar to how models work, this is our data - User, Product, Order, etc.


#### Usage
We create an entity by adding the decorator `@Entity` and defining the columns that define the Entity.
```js
import { Exclude } from 'class-transformer';
import { Column, Entity, PrimaryGeneratedColumn } from 'typeorm';
import { UserRole } from '../../constants/enums';

@Entity()
export class User {
    @PrimaryGeneratedColumn()
    id: number;
    
    @Column()
    first_name: string;

    @Column()
    last_name: string;

    @Column({ unique: true })
    email: string;

    @Exclude()
    @Column()
    password: string;

    @Column({
        type: "set",
        enum: UserRole,
        default: [UserRole.USER],
    })
    roles: UserRole[];
}
```

#### Notes
- to create a column type of  `array`, we have to add the options of the @Column decorator to `type: "set"`
- 