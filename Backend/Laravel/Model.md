`php artisan make:model MyModelName`

---
### One-to-Many relationship

Before we make use of the relationship, we have to  define it first. 

Let's define the relationship between Scenario model and Month model.
```php
class Scenario extends Model 
{
protected $guarded = [];


public function months() {
	return $this->hasMany(Month::class);
	}
}

```

```php
class Month extends Model
{
protected $guarded = [];

public function scenario()
	{
		return $this->belongsTo(Scenario::class);
	}
}
```

Let's use the relationship to create and fetch related data.
```php
// create the scenario
$scenario = Scenario::create([...]);



// now we can use the relationship betweenscenario:month to create a record for months
$scenario->months()->create([...]);

//we can also use the relationship to get all the months for a given scenario
$allmonths = $scenario->months;
```


---
#### Batch Inserts
There might be a time where you want to create multiple records. One way to do it is by doing `for loops`. But that is inefficient. The better way to do this is to do *batch inserts*. 

To do batch inserst, we have to define an array of data and insert all of them into the table in one query - instead of creating each record one by one. 

Here's an example:
```php
$data = [];

foreach ($subscribers as $subscriber){
  $data[] = [
    'name' => $subscriber->name,
    'age' => $subscriber->age
  ];
}

User::insert($data);
```
This is most useful when there are a large number of records to add. Creating records one by one is expensive while inserting them by batches will result to less queries to the database. 
Another technique to build on top of batch inserts is inserting by chunk. See the chunk() method in [[Collections]].