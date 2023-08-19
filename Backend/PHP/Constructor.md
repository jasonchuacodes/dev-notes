A *constructor* allows you to initialize a [[class]]'s properties upon creation of the object.

If you create a `__construct()` function, PHP will automatically call this function when you create an object from a class.

This is quite useful when you want to set a property/attribute based on the parameters passed upon creating the instance of the class.

Let's set the `$name` variable of the Fruit class using `$this` inside the constructor.
```php
class Fruit {  
  public $name;  
  public $color;  
  
  function __construct($name) {  
    $this->name = $name;  
  }  
  function get_name() {  
    return $this->name;  
  }  
}  
  
$apple = new Fruit("Apple");  
echo $apple->get_name();  

```

With a new feature in PHP 8 called *Constructor Property Promotion* we can variables with  `__construct()` in a shorter way.
```php
class User { 
public function __construct( 
	private string $name, 
	private string $email, 
	private int $age 
){
// Constructor code here
} 

public function getProfile { 
	return "$this->name, $this->email, $this->age"; 
	} 
}
```