`php artisan make:migration create_modelnames_table`

Table migrations are used to create a table in the Database.  
With the Schema builder `Schema::create` it is made easy to create a table and set its column and data type.

Here's an example:
```php
Schema::create('user', function (Blueprint $table) {
	$table->id();
	$table->string('fullname');
	$table->tinyInteger('age');
	$table->timestamps();
});
```

The `string` method here sets the first_name column to by type string.

Here are some common methods used to set the column data type:
-  `bigIncrements`: Adds an auto-incrementing unsigned big integer (8 bytes) column to the table.
-  `bigInteger`: Adds a big integer (8 bytes) column to the table.
-  `boolean`: Adds a boolean column to the table.
-  `increments`: Adds an auto-incrementing unsigned integer (4 bytes) column to the table.
-  `integer`: Adds an integer (4 bytes) column to the table.
-  `tinyInteger`: Adds a tiny integer (1 byte) column to the table.
-  `smallInteger`: Adds a small integer (2 bytes) column to the table.
-  `decimal`: Adds a decimal column to the table, with the precision(total number of digits) and scale(decimal places) specified as arguments.
-   `text`: Adds a text column to the table.
-   `longText`: Adds a long text column to the table.
-   `date`: Adds a date column to the table.
-   `year`: Adds a year column to the table.`

Adding `unsigned` to the integer types sets the column to only non-negative values.
-  `unsignedBigInteger`: Adds an unsigned big integer (8 bytes) column to the table.
-  `unsignedInteger`: Adds an unsigned integer (4 bytes) column to the table.
-  `unsignedMediumInteger`: Adds an unsigned medium integer (3 bytes) column to the table.
-  `unsignedSmallInteger`: Adds an unsigned small integer (2 bytes) column to the table.
-  `unsignedTinyInteger`: Adds an unsigned tiny integer (1 byte) column to the table.

Here are other methods that you might use:
-  `binary`: Adds a binary column to the table.
-  `float`: Adds a floating-point column to the table.  
-  `time`: Adds a time column to the table.
-  `timestamp`: Adds a timestamp column to the table.
-  `char`: Adds a fixed-length string column to the table.
-  `mediumInteger`: Adds a medium integer (3 bytes) column to the table.
-  `mediumText`: Adds a medium text column to the table.
-  `dateTime`: Adds a date-time column to the table.
-  `double`: Adds a double-precision floating-point column to the table.
-  `enum`: Adds an enumerated column to the table, with the allowed values specified as an array.


----
#### Updating columns

```php

```

When trying to update columns to types that are not made readily available in Laravel doctrine/dbal package like 'tinyInteger', it will throw an error `unknown column type`.

You need to manually register it in the package. See [[Error - Updating tinyInteger column]] for the solution.
