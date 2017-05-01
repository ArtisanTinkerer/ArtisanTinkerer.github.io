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

Tie the store and the factory together.



Pg - 139.



# Notes


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

