Laravel provides a simple API for testing your application's custom console commands.

The argument inside the `$this->artisan()` method runs a php artisan command as if we ran it in the terminal like `php artisan import:myImport`. From here, we can chain different assertions for the test.

Here we have an example of a test for an Import Command for MasterClients Excel sheet.
```php
class MasterClientsCommandTest extends TestCase
{
// database should reset to its original state after each test
use RefreshDatabase; 

protected $mock_file = 'tests/imports/master_clients.txt';

public function test_in_MasterClientsCommand_it_should_return_error_message_if_file_does_not_exist()
	{
	$this->artisan('import:master-clients this-file-did-not-exist.csv')
	->expectsOutputToContain('File does not exist or is not a CSV file')
	->assertSuccessful();
	}

public function test_in_MasterClientsCommand_it_should_return_success_message_if_file_is_imported()
	{
	Storage::fake('local');
	Storage::disk('local')->put('mock_master_clients.csv', file_get_contents($this->mock_file));
	
	$file = Storage::path('mock_master_clients.csv');
	
	$this->artisan("import:master-clients $file")
	->expectsOutputToContain('successfully imported')
	->assertSuccessful();
	}

  
public function test_in_MasterClientsCommand_it_should_return_the_correct_number_of_rows_based_on_the_csv_file()
	{
	
	Storage::fake('local');
	Storage::disk('local')->put('mock_master_clients.csv', file_get_contents($this->mock_file));
	
	$file = Storage::path('mock_master_clients.csv');
	$this->artisan("import:master-clients $file");
	$this->assertDatabaseCount('master_clients', 5);
	}
}
```