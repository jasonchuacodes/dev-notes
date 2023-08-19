With classes, we have access to the `$this` keyword. 
We can use this for object reassignment to set the values of the class attributes such as what is shown in the `__construct` method in the [[Constructor]]. 

We can also access the parameters passed with `$this`. 
Take this example in Laravel [[Form Request]] where we used `$this->file` to access the `file` that was passed in the request. 
