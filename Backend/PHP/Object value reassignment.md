If ReactJS has setState from useState, PHP has object value reassignment with obj→value. 

Here’s and example:
```php
$user = User::find(1);

dd($user) // { name: “jason”, age: 27 }

$user→name = “Jason Clyde”;
$user→age = 28;
$user→save();

dd($user) // { name: “Jason Clyde”, age: 28 }
```

This is particularly useful when querying a record from the database and wanting to add or modify the record's attribute values.
