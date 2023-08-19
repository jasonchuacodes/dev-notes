Here is an example of a json file.
```php
{
	"master_c5f_suppliers": [
		{
		"name": "AK"
		},
		{
		"name": "MCC"
		}
	],

	"master_gpi_extracts": [
		{
		"gpi_extract_name": "IPM",
		"payout_excess_extraction_capacity": 0
		},
		{
		"gpi_extract_name": "HBM",
		"payout_excess_extraction_capacity": 0
		}
	],
}
```

### Examples
- from [[PHP]] or [[Laravel]]

We can extract the values of the json file by using `file_get_contents()` and decoding the content with `json_decode`.

```php
$json = collect(json_decode(file_get_contents(base_path('database/json/masterData.json'))));

```

When working with Laravel, it is best to transform the data from the json file into a [[Collection]] with the `collect()` method. By doing so, we would have access to the different methods like `filter()`, `map()`, `sum()`, etc.