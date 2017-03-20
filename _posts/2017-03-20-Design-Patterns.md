---
layout: post
title: "Design Patterns"
date: 2016-03-20
---

#Decorator


*The decorator pattern (also known as Wrapper, an alternative naming shared with the Adapter pattern) is a design pattern that allows behavior to be added to an individual object, either statically or dynamically, without affecting the behavior of other objects from the same class.*

  * Build up object at runtime
  
  
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
  
  
  ## In my language
  
  Basically you have a core class and when you want to add functionality, you pass an instance of the core class into the constructor of the class with 
  the additional functionality.
  
  
  
  
  # Adapter 
  
  
  
  
