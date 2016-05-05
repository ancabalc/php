# Object-oriented PHP
  - Object-oriented programming is a programming style in which it is customary to group all of the variables and functions of a particular topic into a single class. 
  - Object-oriented programming is considered to be more advanced and efficient than the procedural style of programming. This efficiency stems from the fact that it supports better code organization, provides modularity, and reduces the need to repeat ourselves.
  
## Classes, objects, methods and properties
  
####Class
  - In order to create a class, we group the code (variables and functions) that handles a certain topic into one place
  
  ```
  class Car { // naming convention is upper camel case
    // The code
  }
  ```
  
####Add properties to a class
  - Properties are the variables inside a class. 
  - Properties can accept values like strings, integers, and booleans (true/false values), like any other variable.
   
  ```
  class Car {
    public $model                           // the public keyword in front of a class property
    public $color = 'beige';                // a property can have a default value
    public $hasSunRoof = true;              // naming convention camel case
  }
  ```
  
####Add methods to a class
  - The classes most often contain functions. 
  - A function inside a class is called a method
  
  ```
  class Car {
 
    public $color = 'beige';
    public $hasSunRoof = true;
   
    public function car() {               // public keyword in front of a method
      return "car";                       // naming convention camel case
    }
  }
  ```
  
####Objects
- We can create several objects from the same class, with each object having its own set of properties.

  ```
  $bmw = new Car ();                        // We created the object from a class with the new keyword.
  $mercedes = new Car ();                   // The process of creating an object is also known as instantiation.
  ```
  ![alt tag](https://github.com/ancabalc/php/blob/master/classes_and_objects.jpg)


####Get an object's properties
  ````
  echo $bmw -> color;                      
  echo $mercedes -> color;
  ````
  
####Set object's properties
  ````
  $bmw -> color = 'blue';
  $mercedes -> color = 'red';
  ````
  
##### EG: Try to drive the car


####The $this keyword
- The $this keyword indicates that we use the class's own methods and properties, and allows us to have access to them within the class's scope.

  ```
  class Car {
 
    public $model;
    public $color = 'beige';
    public $hasSunRoof = true;
   
    public function car() {                                 
      return "My car has " . $this->color . " color.";   // approach the class properties with the $this keyword    
    }                                                    // only $this keyword starts with the $ sign, while the names of the                                                              // properties and methods do not start with it.
    public function has ??
  }
  ```
  
####Access modifiers: public vs. private
  - *public* access modifier allows a code from outside or inside the class to access the class's methods and properties
  - *private* modifier prevents access to a class's methods or properties from any code that is outside the class.
  
  #####The public access modifier
  ```
  class Car {
    // public methods and properties.
    public $model;    
   
    public function getModel()
    {
      return "The car model is " . $this -> model;
    }
  }
   
  $mercedes = new Car();
  //Here we access a property from outside the class
  $mercedes -> model = "Mercedes benz";
  //Here we access a method from outside the class
  echo $mercedes -> getModel();
  ```
  
  #####The private access modifier
  ```
  class Car {
    //private
    private $model;
      
    public function getModel()
    {
      return "The car model is " . $this -> model;
    }
  }
   
  $mercedes = new Car();
  // We try to access a private property from outside the class.
  $mercedes -> model = "Mercedes benz";
  echo $mercedes -> getModel();
  ```
   
  **Setters** that set the values of the private properties.
  
  **Getters** that get the values of the private properties.
  ```
  class Car {
    //the private access modifier denies access to the method from outside the class’s scope
    private $model;
   
    //the public access modifier allows the access to the method from outside the class
    public function setModel($model)
    {
      $this -> model = $model;
    }
    
    public function getModel()
    {
      return "The car model is  " . $this -> model;
    }
  }
   
  $mercedes = new Car();
  //Sets the car’s model
  $mercedes -> setModel("Mercedes benz");
  //Gets the car’s model
  echo $mercedes -> getModel();
  ```
  
  ```
  class Car {
 
    //the private access modifier denies access to the method from outside the class’s scope
    private $model;
   
    //the public access modifier allows the access to the method from outside the class
    public function setModel($model)
    {
      //validate that only certain car models are assigned to the $carModel property
      $allowedModels = array("Mercedes benz","BMW");
   
      if(in_array($model,$allowedModels))
      {
        $this -> model = $model;
      }
    }
    
    public function getModel()
    {
      return "The car model is  " . $this -> model;
    }
  }
   
   
  $mercedes = new Car();
  //Sets the car’s model
  $mercedes -> setModel("Mercedes benz");
  //Gets the car’s model
  echo $mercedes -> getModel();
  ```
  
####The __construct() method
  - The names starts with two underscores __construct()
  - We use __construct() in order to do something as soon as we create an object out of a class
  - Usually we use the constructor to set a value to a property.
  
  ```
  class Car{
    private $model;
   
    // A constructor method.
    public function __construct($model) {      // wint or without params
      $this -> model = $model;
    }
  }
  ```

