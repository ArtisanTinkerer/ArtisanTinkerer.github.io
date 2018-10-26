---
title: "Laracasts Design Patterns"
date: 2018-10-26
layout: default
---

# The Decorator Pattern

A decorator allows us to dynamically extend the behaviour of a cparticular object at runtime, without needing to resort to unnecessary inhertiance.

Example is a car service.

```
interface CarService{
  public function getCost();
}


class BasicInspection implements CarService {

  public function getCost()
  {
    return 25;
  }
}
```

Can add a decorator for additional functionality:

```
class OilChange implements CarService {

protected $carService;

function __construct(CarService $carService)
{
  $this->carService = $carService;
}

public function getCost()
  {
    return 29 + $this->carService->getCost();
  }

}


```
OilChange is decorator which is forced to implement the same interface.
Decorator must accept same contract in its constructor.

This is how to call it:

```
service =  new TireRotation (new OilChange ( new BasicInspection())))->getCost();
```

Why us compostion instead of inheritance.

If we just do
```
class Carservice() {

public function withOilChange()
{

}

public function withTireRotation()
{

}
}

```

* Breaking Open/Closed principle
 - not closed for modification





