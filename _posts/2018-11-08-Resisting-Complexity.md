---
title: "Resisting-Complexity"
date: 2018-11-08
layout: default
---

https://murze.be/resisting-complexity

# Resisting Complexity

## Watering plant analogy.
Need a gardener.

```names.reverse```
```date->format()```

```gardener->water($plant)```


```object.method();```

An affordance. 

```$plant->water()```

## Eliminating agent nouns
* driver

eg
before:
```
$this->announcementBroadcaster->broadcast($announcement);

```
after:
```
$announcement->broadcast();

```

## Conquering Fear of Facades

## Ergonomics Matter

## Push side work to event listerners
Listener naming - not the event - what are they actually doing?
```
SendPurchaseFulfillmentEmail
```

## Breaking up God Objects
```
user()->redeemLicense
```
not an affordance, instead:
```
$licence->redeem($user)
```
and move to the licence class.

## Uncovering New Concepts

** Affordances are clues about how an object should be used **

Example:

long purchase:

```
$purchase = Purchase::create([
  `product` => $product
  etc
  etc 
```


add a checkout object
```
$checkout = new Checkout($product,$email);
$purchase = $checkout->complete


```

## Maybe you just need a function
LicenseCodeGenerator just for one function

Create an invokable class (just a function hidden in a class)

In test:
```
$this->app->instance(GenerateLicenseCode::class, function(){
  return 'abc123'
})

```

In app:

```
= app(GenerateLicenseCode::class)->__invoke()

```


in GenerateLicenseCode class:
```
public function __invole()
{
  return str_random(32);
}

```

Next step:

Class LicenceCode
```
public static function generate(params)
{
 pp(GenerateLicenseCode::class)->__invoke()
}
```


app:
```
LicenceCode::generate
```

This is just done, so that we override the function in test.








