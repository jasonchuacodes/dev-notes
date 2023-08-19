An *object* is a data structure that represents an instance of a class. 
It combines data (`attributes/properties`) and behavior (`methods`) in a single entity.

The *class* serves as a blueprint for the object since each object can have different attributes or properties (`such as name, age, and address`) or methods (`such as introduce()`).

Let's create a Person *class*.
```php
class Person {
	public $name;
	public $age;
	public $address;

public function __construct($name, $age, $address) {
	$this->name = $name;
	$this->age = $age;
	$this->address = $address;
    }

    public function introduce() {
        return "Hi, my name is " . $this->name . ", I am " . $this->age . " years old, and I live at " . $this->address . ".";
    }
}
```

Having created the blueprint, we can now create the object by creating an instance of this class with the `new` keyword.

Let's create a new Person *object*.
```php
$person = new Person("John Doe", 30, "123 Main St");

echo $person->introduce();

```

___
### Related
- [[$this]]
- [[Constructor]]
