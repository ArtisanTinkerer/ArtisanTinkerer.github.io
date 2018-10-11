---
title: "Clean-Code"
date: 2018-10-10
layout: default
---

# Clean Code PHP
https://github.com/jupeter/clean-code-php#functions

## Variables
* use meaningful names
* use searchable names (not numbers)
* avoid nesting deeple, return early
* avoid mental mapping (no $i)
* don't add uneeded context ($carMake)
* typehint to avoid nulls (string $thing)
* use !== and ===




 ## Functions
 * don't use flag arguments - have a differnet function instead
* avoid side effects - have one service which writes to a file - don't use mutable data types
* * don't change globals
* don't use Singletons
* Encapsulate conditions ``` $article->isPublished()```
* avoid negative conditionals
* avoid conditionals  - use polymorphism instead
* avoid type checking - type hint instead
* remove dead code
* use getters and setters
* use private by default

## Classes
* prefer composition over inheritance - have a class instead of extending (Employee has EmployeeTaxData)
* avoid fluent
* prefer final classes - use an interface
### SOLID  
#### Single Responsibility
* Never more than one reason for a class to change - class should just do one thing.

#### Open/Closed
*  Open for extension - closed for modification
#### Liskov Substitution
#### Interface Segregation
#### Dependency Inversion

### DRY














# Chapter 3 Functions
## General

* Small.
* Smaller than that.
* 3 to 4 lines long!
* blocks within if,else and while should be one line long
* * probably a function call
* Adds documentary value - function has descriptive name
* FUNCTIONS SHOULD DO ONE THING. THEY SHOULD DO IT WELL.
THEY SHOULD DO IT ONLY.
* one level of indentation
* you need another function if you can extract another function with a new name.


* switch could be a factory

* Remember Ward’s principle: “You know you are working on clean code
when each routine turns out to be pretty much what you expected.”

## Arguments
* avoid 3 or more arguments

pg 40
