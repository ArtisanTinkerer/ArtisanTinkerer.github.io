---
layout: default
title: "Laracasts-SOLID"
date: 2017-03-30
---

# Single Responsibility
S in SOLID - single responsibility

"A class should have one, and only one, reason to change"

"A class should have one job"

## Examples:
**Sales reporter should not have authentication in "extract to controller"**

**Querying the db and doing a calculation.**

**Formatting output.**

Class would have to change, if we need to change either of these.

*This violates single responsibility*

## How Fixed

**Querying the db and doing a calculation.**
This was moved to a repository.

**Formatting output.**

1, Leave this to the consumer.

This is not the sales reporters job, so this means it needs to go.

2,

In the Reporting folder, create an interface.

```
interface SalesOutputInterface
{

  public function output($sales);
  

}

//and output classes which implement this

class HtmlOutput implements SalesOutputInterface {

  public function output()
  {
    return "<h1>$sales</h1>";
  }

}

```

# Open Closed

## "Entities should be open for extension but closed for modification."

"open for extension" - easy to change behaviour.
"closed for modifications" - change without modifying source code - extension

Modify behaviour without ever touching the original source.
= avoid code rot

```

class Square {

  public $width;
  public $height;
  
  function __construct($height, $width)
  {
    $this->height = $height;
    $this->width = $width;
    
  }
}

```
"We want to calculate the area"

```
class AreaCalculator{

  public function calculate($squares)
  
  
  {
  
      $area = 0;
      foreach($squares as $square)
      {
      
        $area += $square->width * $square->height;
      
      }
      
      retuen $area;
  
  }

}

```

"We also need circles"

```
class Circles {

  public $radius;
  
  
  function __construct($radius)
  {
  
    $this->radius = $radius;  
    
  }
}
```

Now we need the area!
Edit the original code = broken open/close principle.

*I think - interface and then implement for each shape?*


** Separate extensible behaviour behind an interface and flip the dependencies.**

Interface is a contract.

"Code to an interface".

Polymorphism - sharing a common interface,

# Liskov Substitution

"Code to an interface".


"Derived classes must be substitutable for their base classes"


- functions in derived classes should return same things
- so consumer recieves same thing
- instanceof suggests breaking LSP
- comment in the interface what should be returned


# Interface Segregation





# Watch Repositories




