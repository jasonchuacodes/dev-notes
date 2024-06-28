Before selecting anything from a database, it needs to be populated with tables and data.
See [[Migration]] to add tables and [[Model]] and [[Seeders]] to create data into tables. 

Now that we have our database, tables, and data setup, we can now do queries to our data.

---
#### Methods
- *get()* - the `get`method is used to fetch data from the database, it retrieves all the columns from the table.

  Suppose you have a "users" table in your Laravel application with the following columns: `id`, `name`, `email`, `created_at`, and `updated_at`. 
  To retrieve all the data from this table, you could use the `get()` method like this:
```php
$users = DB::table('users')->get();
```
  
- *select()* - with the `select` method, you can specify only the columns you need to retrieve in the get() method. This will optimize the query and can drastically reduce memory usage and speed up the query execution.
  if you only need the `id` and `name` columns, you can use the `select()` method to fetch only those columns, like this:

```php
$users = DB::table('users')
	  ->select('id', 'name')
	  ->get();
```
