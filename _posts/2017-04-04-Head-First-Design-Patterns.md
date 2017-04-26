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

1 Take a DarkRoast object
2 Decorate it with a Mocha object
3 Decorate it with a Whip 



# Notes


## OO Principles

Encapsulate what varies
Favor composition over inheritance
Program to interfaces not implementations
Strive for loosely coupled designs between objects that interact

** Code should be closed to to change, tey open to extension  **


## Design Principle

Identify the aspects of your application that vary and separate them from what stays the same.

* Composition over inheritance * (or composite reuse principle) in object-oriented programming is the principle that classes should achieve polymorphic behavior and code reuse by their composition (by containing instances of other classes that implement the desired functionality) rather than inheritance from a base or parent class.[2] 

pg86

