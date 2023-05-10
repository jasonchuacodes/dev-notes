`php artisan make:seeder ModelNameSeeder`

Here's an example of seeding data to the users_table.
```php
class UserSeeder extends Seeder

{

public function run()
	{
		$faker = Factory::create();
		
		$data = [];
		for ($i = 0; $i < 5; $i++) {
		$firstName = $faker->firstName();
		$lastName = $faker->lastName();
		
		$data[] = [
				'name' => "$firstName $lastName",
				'username' => strtolower("$firstName$lastName"),
				'email' => 'user' . $i . '@gmail.com',
				'department' => $faker->randomElement(['Material', 'SC planning']),
				'created_at' => now(),
				'updated_at' => now(),
				'deactivated_at' => null,
				'deleted_at' => null
			];
		}
		User::upsert($data, ['email']);
	}
}
```

In Laravel Seeders, `$this->call()` is a method used to run other seeders from within the current seeder. It allows for the creation of a seed hierarchy.
```php
class MasterSeeder extends Seeder

{
public function run()
	{
	$this->call([
		MasterC5fSupplierSeeder::class,
		MasterGpiExtractSeeder::class,
		MasterTankSeeder::class,
		MasterPlantSeeder::class,
		MasterItem::class,
		MasterPlantMaterialSeeder::class,
		MasterClientSeeder::class,
		MasterShippingSeeder::class
	]);
	}
}
```

To run all the seeders, run the command in the terminal: 
`php artisan db:seed`

To run a specific seeder, run the command in the terminal:
`php artisan db:seed --class=ModelNameSeeder`

