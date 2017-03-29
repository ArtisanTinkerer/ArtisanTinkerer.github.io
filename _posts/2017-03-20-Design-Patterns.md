---
layout: default
title: "Design Patterns"
date: 2017-03-20
---

# Decorator Pattern


*The decorator pattern (also known as Wrapper, an alternative naming shared with the Adapter pattern) is a design pattern that allows behavior to be added to an individual object, either statically or dynamically, without affecting the behavior of other objects from the same class.*

  **Build up object at runtime**
  
  
  ```
  interface CarService{
    public function getCost();
  }
  
    class BasicInspection implements CarDervice {

      public function getCost()
    {
      return 25;
    }  
    
    
    
    
    
    class OilChange implements CarService {
    
      protected $carService;
      
      //so for this to work, we need an existing CarService
      
      function __construct(CarService $carService)
      {
        $this->carService =$carService;
      }
    
      public function getCost()
    {
        return 29 + $this->carService->getCost();
    }
    
    
  }
  ```
  
  Then we can do ```echo (new OilChange(new BasicInspection()))->getCost();```
  More classes can then be chained on to this. 
  

  "stack on responsinbilities with a Decorator"
  
  Core service (BasicInspection)  and then decorator (OilChange) which is forced to implement the same contract.
  The decorator must accept this in the constructor.
  
  
## When is this appropriate.
  
  Be careful when using inheritance, may be inheriting a lot whihc you don't need.
  
  
## My Summary
  
  Basically you have a core class and when you want to add functionality, you pass an instance of the core class into the constructor of the class with 
  the additional functionality.
  
  
  
  
# Adapter 

Memory card adapter analogy.

"An adapter allows you to translate one interface for use with another"


## Book
```
class Book{

 public function open()
 {
  var_dump('opening the paper book.');
 }
 
 public function turnPage()
 {
  var_dump('turning the page of the paper book.');
 }

}
```
## Person
```
class Person{

 public function read($book)
 {
   $book->open();
   $book->turnPage();
 }
 
 public function turnPage()
 {
  var_dump('turning the page of the paper book.');
 }

}
```

Person can read a book.

## Interfaces

```
interface BookInterface {

  public function open();
  
  public function turnPage();
 
}

```

## Person
```
class Person{

 public function read(BookInteface $book) //decoupled the code
 {
   $book->open();
   $book->turnPage();
 }
 
 public function turnPage()
 {
  var_dump('turning the page of the paper book.');
 }

}
```

Interface for Kindle is different.

Kindle

```
class Kindle{

 public function turnOn()
 {
   var_dump('turn the Kindle on');
 }
 
 public function pressNextButton()
 {
  var_dump('press the next button on the Kindle.');
 }


}
```
and associated interface.

```
interface eReaderInterface {

  public function turnOn();
  public function pressNextButton()'
 
}

```

Adapter which allows two different classes to communicate.
This needs to implement the Book functions.


```
class KindleAdapter implements BookInterface

private $kindle;

//inject a Kidle
public function __construct(Kindle $kindle
 {
  $this->kindle = $kindle;
 }


 public function open()
 {
   return $this->kindle->turnOn();
 }
 
 public function turnPage()
 {
  return $this->kindle->pressNextButton();
 }


}
```

## My Summary

So, basically we create an adapter which:
 1, implements BookInterface
 2, gets a Kindle injected
 3, maps the book functions to the the matching Kindle functions


Then you can access a Kindle in the same way as a book.



```
(new Person)->read(new KindleAdapter(new Kindle))
```

The adapter allows the Kindle to be used like a Book.

**Without changing the Book code**

# Interface

Good when worried about code duplication.

Example is two classes with similiar functions but one different.

VeggieSub and TurkeySub

Shared methods should be moved to abstract parent 'Sub'.
Children extend Sub.

The make method is in the parent.

```
public function make()
{

  return $this
   ->layBread()
   ->addLettuce()
   ->addTurkey()
   ->addSauces();

}

Turkey and Veggie Sub classes only contain methods which are unique to them.


```

addLettuce and addMeat are the unique methods.

Generalise this to ```addPrimaryToppings()```
The fact that this is abstract forces ths children to implement it.

```
protected abstract function addPrimaryToppings(){

}

```

Then make sure that the methods in the children have the same name. (addPrimaryToppings.)


## My thoughts.

This is pretty much what I did with the Datatables classes, without adding the abstract methods to the parent.
This is a pretty obvious way to use inheritance. 


# The Strategy Design Pattern

## Define a family of algorithms

"Multiple strategies to execute a single task."

Eg logging - to file or to db or e-mail

```
class LogToFile{

}


class LogToDatabase{

}


class LogToXWebService{

}

```

## Encapsulate and make them interchangeable

Create an interface!

```
interface Logger {

 public function log($data);

}

```

So now all the other classes can implement this:

```
class LogToDatabase implements Logger{

  public function log($data){
    var_dump('Log to db');
  }
  
}

```

Because we code to an interface, this allows the classes to be interchangeable.

```
class App{

 public function log($data, Logger $logger)
 {

   $logger->log($data)
   
 }


$app = new App;

$app->log('Some info', new LogToFile);


```

## In my words.

Just use an interface for a family of classes, this forces them to use the same methods and 
makes them interchangeable. (Polymorphism.)

# The Chain or Responsibility



```
//this forces all the classes to have a check methid
abstract class HomeChecker {

 protected $sucessor;

 public abstract function check(HomeStatus $home);
 
 public function succeedWith(HomeChecker $home){
 
  $this->successor = $sucessor
 }
 
 public function next(HomeStatus $home){
 
 if($this->successor)
 
 {
  $this->successor->check($home);
  }
 
 }
 
}

class Locks extends HomeChecker {

 public function check(HomeStatus $home)
 {
   if (!$home->locked)
   {
    throw new Exception('The doors are not locked');
   }
   
   $this->next(home);

 }

}

class Lights extends HomeChecker{


}

class Alarms extends HomeChecker{


}

class HomeStatus {
 public $alarmOn = true;
 public $locked = true;
 public $lightsOff = true;
 
}

//first set up objects
//distinction betwwen decorator, is that any object can slice through the chain
$locks = new Locks;
$lights = new Lights;
$alarm = new Alarm;

$locks->succeedWith($lights);
$lights->succeedWith($alarm);


$status = new HomeStatus;


$locks->check(new HomeStatus);


```


If the check function passes, the next function is called and then the check function of the succesor.

# The Specification Pattern

Default to not using.

Business rule -eg Gold Customer

"A customer specification"
```
class CustomerIsGold {

 public function isSatisfiedBy(Cuustomer $customer)
 
 {
   return $customer->type =='gold';
 
 
 }

}

```

*Could just be isGold on Customer*
Test

```

 $specification = new CustomerIsGold;
 
 $goldCustomer = new Customer('gold');
 
 $specification->isSatisfiedBy($goldCustomer)

```

# The Observer Pattern

One of the most popular.

1-2-1 dependency, so that when one object changes, it's dependents are notified.

eg discussion, notify when comments added

```
interface Subject { //Subscriber

  public function attach($observer);
  public function detach($observer);
  public function notify();

}

interface Observer { //Publisher

 public function handle();
 
}




```

Basic event system.

## Using in Laravel

```

Event::listen(`user.login`), function()
{
 var_dump('fire off an email');
});


Event::listen(`user.login`), function()
{
 var_dump('do some reporting');
});

get('/', function()
{
 Event::fire('user.login');
});
```
in a controller:

```
class HomeController {

 public function index(Dispatcher $dispatcher)
 
 {
  $dispatcher->fire('UserHasLoggedIn');
 }

}

```

### Listeners

1, In a Listeners folder
```
class EmailNotifier{

 public function handle()
 {
  var_dump('fire off an email');
 }


}

```

add to EventServiceProvider

```
protected $listen = [
 'UserHasLoggedIn' => [
    'App\Listeners\EmailNotifier',
 ],
];

```








  
  
  
  
