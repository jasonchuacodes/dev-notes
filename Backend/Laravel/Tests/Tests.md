`php artisan make:test MyTestName`

Laravel tests refer to a set of automated tests that are used to ensure the functionality and correctness of a Laravel application.

Laravel Tests are usually written in PHP and are run using the [[PHPUnit]] testing framework. They can be used to test different aspects of the application, such as controllers, models, routes, middleware, and more.

Tests come with *Assertions* that are used to assess if the function is successful or fails. These assertions simply asks about the expected behavior.

Read more about the different assertions we can use for Laravel Tests here: 
- [Database Assertions](https://laravel.com/docs/9.x/database-testing)
- [Console Assertions](https://laravel.com/docs/9.x/console-tests)


Let's have an example. 
Here's our sample *function*.
```php
// User store function
public function store($name) {
	$user = User::create('name' => $name);

	return $user;
}

```

Here's the *test*.
```php
// test UserTest
public function test_in_store_function_should_log_the_name_value() 
{
	$name = 'John Doe'; 
	$user = User::store($name); 
	
	$this->assertInstanceOf(User::class, $user); 
	$this->assertEquals($name, $user->name); 
	
	$storedUser = User::find($user->id); 
	$this->assertEquals($name, $storedUser->name);
}
```

Let's run the test by running the command in the terminal.
`php artisan test --filter UserTest`


Here are some Laravel Tests:
- [[Console]] Test
- [[Database]] Test
- [[Mocking]]