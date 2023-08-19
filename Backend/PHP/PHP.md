The framework that I learned for PHP is [[Laravel]].

### Concepts
Here are some useful concepts in PHP:
- [[Traits]]
- [[$this]] keyword

---
### Methods

`file_get_contents` - used to get the contents of a file. Accepts an argument for file_path.
`base_path` - used to get the base_path of the PHP/Laravel application.

```php
file_get_contents(base_path('databse/json/masterData.json'));
```

---
### Tips

**Appending values to an existing array**
We can use the `[]` notation to append values to an existing array.
Take the example for the empty array below `$data`. 
Notice that we are adding the item values to `$data[]` instead of just `$data`. 

The square brackets signify that we are appending the values, not assigning the values.

```php
$array = json_decode(get_file_contents("path-to-file/my_file.json"));

$data = [];

foreach ($array as $item) {
		$data[] = [
		"name" => $item->name,
		"contents" => $item->contents,
		"place" => $item->place,
	];
}

// dd($data) will print out a set of arrays $data = [ [], [], [] ];
```