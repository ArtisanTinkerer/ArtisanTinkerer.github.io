---
layout: default
title: "Head-First-Design-Patterns"
date: 2017-04-04
---

Just making some notes as I attempt to work through this book and start using recognised Design Patterns.

# Strategy

A family of algorithmns.

<img src="/images/Strategy.png" alt="missing" class="inline"/>


# Observer

The Observer Pattern defines a one-to-many dependency between objects so that when one object changes state, all of its dependents are notified and update automatically.


<img src="/images/Observer.png" alt="missing" class="inline"/>


# The Decorator Pattern

Decorate your classes at runtime using a form of object composition.

Example is zillion types of Starbucks all * with * different additions ** EspressoWithSteamedMilkandMocha **.

Identify areas which may change.

1. Take a DarkRoast object
2. Decorate it with a Mocha object
3. Decorate it with a Whip 

Decorators implement the same interface as the component they are going to decorate.
Pg 95 the Decorator extends the Beverage class.

<img src="/images/Decorator.png" alt="missing" class="inline"/>

https://sourcemaking.com/design_patterns/decorator/php

https://sourcemaking.com/design_patterns


This is how you use it:

```
  drink = new Darkroast();
  drink = new Mocha(Drink);
  drink = new Whip(Drink);
  
```

# The Factory Pattern

new - think when newing, is this better in a Factory?

Identify the aspects that vary and separate them from what stays the same.
** An object that just creates objects, other objects use this, when they need new objects = Factory. **

```
pizza = factory.createPizza(type);

```
## Simple Factory

<img src="/images/Simple Factory.png" alt="missing" class="inline"/>

Got the simplw one working OK.


Tie the store and the factory together.


** Come back to this **
Pg - 139.


# The Singleton Pattern

* One of a Kind Objects - only one instance *

The PHP Way:
```
// General singleton class.
class Singleton {
  // Hold the class instance.
  private static $instance = null;
  
  // The constructor is private
  // to prevent initiation with outer code.
  private function __construct()
  {
    // The expensive process (e.g.,db connection) goes here.
  }
 
  // The object is created from within the class itself
  // only if the class has no instance.
  public static function getInstance()
  {
    if (self::$instance == null)
    {
      self::$instance = new Singleton();
    }
 
    return self::$instance;
  }
}
```

# The Command Pattern - Encapsulating Invocation

Remote control analogy. Lots of classes with different interfaces.
Command object sits in the middle and decouples.

* The Command Pattern * encapsulates a request as an object, thereby letting you parameterize other objects with different requests, queue or log requests, and support undoables operations.

** Read over this chapter again **



# Adapter

Travel plug analogy.

Make an adapter so that a Turkey can be used like a Duck.

```
public class TurkeyAdapter implemements Duck{
  Turkey turkey;

  public TurkeyAdapter(Turkey turkey){
    this.turkey = turkey;
  }
  
  public void quack() {
    turkey.gobble();
  }


  public void fly() {
    turkey.hop();
  }


}

```

## Summary
Basically just create an adapter class which sits between a client and adaptee and translates the requests.

## Facade Pattern

Analogy home theatre, lots of tasks to watch a film.
Facade Pattern takes a complex system and makes it easier by implementing a Facade class that provides one, more reasonable interface.

Facade will just have one method (watchMovie) which triggers all the sub tasks.


* The Facade Pattern * provides a unified interface to a set of interfaces in a subsystem. Facade defines a higher-level interface that makes the subsystem easier to use.

** A Simplified Interface **

## The Principle of Least Knowledge

"talk only to your immediate friends"

From a method in an object you can only invole methods which belong to:

1, The object itself
2, Objects passed in as a parameter to the method
3, Any object the method creates or instantiates
4, Any components of the object



pg 266


# Notes

** Look up, how to choose a design pattern.  **

** Watch the Laracast again **

## OO Principles

Encapsulate what varies
Favor composition over inheritance
Program to interfaces not implementations
Strive for loosely coupled designs between objects that interact

** Code should be closed to to change,  open to extension  **


## Design Principle

Identify the aspects of your application that vary and separate them from what stays the same.

* Composition over inheritance * (or composite reuse principle) in object-oriented programming is the principle that classes should achieve polymorphic behavior and code reuse by their composition (by containing instances of other classes that implement the desired functionality) rather than inheritance from a base or parent class.[2] 

pg86

