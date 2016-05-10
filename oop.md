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
  
###Inheritance in object-oriented PHP
  - reduce code duplication with inheritance
  - using inheritance, we can create a reusable piece of code that we write only once in the parent class, and use again as much as we need in the child classes.
  - inheritance allows us to write the code only once in the parent, and then use the code in both the parent and the child classes.
    
  ```
  class Parent {
    // The parent’s class code
  }
   
  class Child extends Parent {                                // use the extends keyword
    // The  child can use the parent's class code
  }
  ```
    
  ```
  // Parent class
  class Vehicle {
    public $model;
    public $color = "white"; 
    
    public function __construct($model, $color = "white") {
      $this->model = $model;
      $this->color = $color;
    }
  
    public function printVehicle() {
      return "My vehicle " . $this -> model ." color is " . $this->color . ".";
    }
  }
  
  class Bike extends Vehicle {
  
  }
  
  class Car extends Vehicle { 
    public $speed;                               //  a child class cn have its own properties and methods
    public drive() {
      $this->speed ++; 
    }
  }
  ```
  
  ####Protected
  - When we declare a property or a method as protected, we can approach it from both the parent and the child classes.
  ```
  // Parent class
  class Vehicle {
      protected $model;
      public $color = "white"; 
      
      public function __construct($model, $color = "white") {
        $this->model = $model;
        $this->color = $color;
      }
    
      function printVehicle() {
        return "model = " . $this -> model ." color =  " . $this->color . ".";
      }
  }


  class Bike extends Vehicle {
    public function printBike() {
      return "My bike model = " . $this -> model;              // Access model from child class
    }
  }
  ```
  
  ####Override the parent’s properties and methods in the child class
  - When we override the class’s properties and methods, we rewrite a method or property that exists in the parent again in the child, but assign to it a different value or code.
  ``` 
  // Parent class
  class Vehicle {
      protected $model;
      public $color = "white"; 
      
      public function __construct($model, $color = "white") {
        $this->model = $model;
        $this->color = $color;
      }
    
      function printVehicle() {
        return "model = " . $this -> model ." color =  " . $this->color . ".";
      }
  }


  class Bike extends Vehicle {
    public function printVehicle() {
      return "model = " . $this -> model;              // Access model from child class
    }
  }
  ```
  
  ####Prevent the child class from overriding
  ``` 
  // Parent class
  class Vehicle {
      protected $model;
      public $color = "white"; 
      
      public function __construct($model, $color = "white") {
        $this->model = $model;
        $this->color = $color;
      }
    
      final function printVehicle() {                    // Use ***final*** to prevent overriding
        return "model = " . $this -> model ." color =  " . $this->color . ".";
      }
  }


  class Bike extends Vehicle {
    public function printVehicle() {                    // EORROR - cannot override final methds
      return "model = " . $this -> model;             
    }
  }
  ```
  ####Abstract classes and methods
  - We use abstract classes and methods when we need to commit the child classes to certain methods that they inherit from the parent class but we cannot commit about the code that should be written inside the methods.
  - An abstract class is a class that has at least one abstract method. 
  - Abstract methods can only have names and arguments, and no other code. 
  
  ```
  abstract class Car { }
  ```
  
  ```
  // Abstract methods inside an abstract class don't have a body, only a name and parameters inside parentheses.
  abstract class Car {
    abstract public function calcNumMilesOnFullTank();
  }
  ```
  
  ####Create child from abstract class
  - The child classes that inherit from abstract classes must add bodies to the abstract methods.
  ```
  class Honda extends Car {
    // Since we inherited abstract method, we need to define it in the child class, 
    // by adding code to the method's body.
    public function calcNumMilesOnFullTank()
    {
      $miles = $this -> tankVolume*30;
      return $miles;
    }
  }
  ```
  
  ####Interfaces
  - An interface commits its child classes to abstract methods that they should implement.
  - We can implement a number of interfaces in the same class.
  ```
  interface interfaceName { 
    // abstract methods
  }
   
  class Child implements interfaceName {
    // defines the interface methods and may have its own code
  }
  ```
  
  ####What are the differences between abstract classes and interfaces?
  ![alt tag](https://github.com/ancabalc/php/blob/master/ai.jpg)
  
  ####Polymorphism in PHP
  - According to the Polymorphism principle, methods in different classes that do similar things should have the same name.
  
