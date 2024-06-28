
Laravel collections can be used to work with arrays, database query results, and any other iterable object. Collections provide a set of convenient methods that allow you to easily filter, sort, group, and transform data. Some of the common collection methods include:

#### Methods
- `map()`
- `filter()`
- `each()`
- `reduce()`
- `sort()`
- `groupBy()`
- `sortBy()`

____

- *each()*: Perform a given action on each item in the collection.
- *reduce()*: Reduce the collection to a single value using a callback function.
- *sort()*: Sort the collection by a given key or callback function.
- *groupBy()*: Group the collection by a given key or callback function.

- *map()*: Transform each item in the collection using a callback function.
Here's an example of using collection and the `map()` method.
This will create a new collection where each item is doubled.
```php
$collection = collect([1, 2, 3, 4, 5]);

$transformed = $collection->map(function ($item, $key) {
	return $item * 2; 
});
```


- *filter()*: Filter the collection using a callback function.
You can also chain multiple methods together to perform more complex operations on the data. Here we chain `map()` with `filter()`:
```php
$filtered = $collection
	->filter(function ($item, $key) {return $item > 2; })
	->map(function ($item, $key) { return $item * 2; });
```


-  *sortBy()*: Sort a collection by a specified key.
 If a collection is sorted by multiple keys, the order of the `sortBy()` calls matters.
```php
$products = collect([ 
	['name' => 'Product A', 'price' => 10], 
	['name' => 'Product B', 'price' => 20], 
	['name' => 'Product C', 'price' => 10], 
	['name' => 'Product D', 'price' => 15] 
]); 

$sortedProducts = $products
	->sortBy('name'); 
	->sortBy('price')

$sortedProducts->each(function ($product) { echo $product['name'] . ' - ' . $product['price'] . "\n"; });

// Product A - 10 
// Product C - 10 
// Product D - 15 
// Product B - 20
```



----
#### Advanced methods

- *unique()*: The `unique()` method in Laravel collections returns a new collection with only the unique values. However, the keys in the new collection may not be ordered or sequential, depending on the order of the original collection.
- *values()*: The `values()` method is used on a Laravel collection to reset the keys of the collection to be sequential and re-indexed starting from zero.

`unique()` and `values() `method is often used together to reset the keys of the unique values.
Here's an example:
```php
$array = [1, 2, 3, 3, 4, 5, 5, 5]

$collection = collect($array);

$unique_items = $collection
	->unique()
	->values();

// $unique_items will contain the collection [1, 2, 3, 4, 5] 
// with keys [0, 1, 2, 3, 4]

```


- *flatMap()*: The `flatMap()` method in Laravel collections is a combination of the `map()` and `flatten()` methods. It applies a transformation to each item in a collection and then flattens the result into a single collection. 

This method comes in handy for nested arrays. 
Here's an example of `flatMap()` in action:
```php
$collection = collect([
    'A' => [
        ['apple'],
        ['banana', 'kiwi'],
    ],
    'B' => [
        ['cherry', 'plum'],
        ['pear'],
    ],
]);

$modifiedCollection = $collection->flatMap(function ($subcollection) {
    return collect($subcollection)->flatMap(function ($item) {
        return collect($item)->map(function ($subitem) {
            return str_split($subitem);
        });
    });
});

$uniqueValues = $modifiedCollection
	->flatten()
	->unique();

// uniqueValues = [ 'a', 'p', 'l', 'e', 'b', 'n', 'k', 'i', 'w', 'c', 'h', 'e', 'r', 'y', 'u', 'm' ]

```


- *chunk()* : this method will split an array into specified chunks. Chaining this method to the `each()` function will make the logic behave just like a foreach loop but done in chunks to prevent query parameter limits. 

Here's an example of the `chunk()` method:
```php
$data = [];

// 10,000 users 
foreach($users as $user){
  $data[] = [
    'name' => $user->name
  ]
}

collect($data)->chunk(100)->each(function ($data_chunk){
  DB::table('subscribers')->insert($data_chunk);
})
```