---
layout: default
title: "Service Container"
date: 2017-04-11
---

A little container which houses all the bindings in our application.


```
class Bar{}

Route::get('bar',function(Bar $bar){
  dd($bar);

});

```

Nowhere did we new up the bar
Laravel uses reflection - peeks into the argument list, to see what we expect. Then it (news up a Bar) does it for us. 

If Bar needs a Baz, Laravel will also new that up for us. 

The IOC container is the same as the service container. 

You can bind to the service container:

```
App::bind('Bar', function(){
  return new Bar(new Baz)
  }
)

```

** Not sure why? **


## Interfaces

```
interface BarInterface {};

class Bar implements BarInterface {}

App::bind('BarInterface', function()
{
  return new Bar;

})

Route::get ('bar',function(BarInterface $bar)){

  dd($bar);
  
});

```
In this case Laravel cannot instantiate an interface, so throws error. (If no bindng in the container.)

I can fix this by adding:

```
App::bind('BarInterface','Bar');
```
-4:58

Repositories class
FooRepository

```
class FooRepository{

    public function get()
    {
        return ['array','of','items'];
  
    }
  
}
```

Shouldn't really new up Repositories.

So inject.

```
public function __construct(FooRepository $repository)
```

then can do:

```
  $this->repository->get();
```


So Laravel created a FooRepository.


You may need a dependency just for a method.
So, we have method injection.

```
public function doSomething(FooRepository $repository)
```

## Method injection or constructor injection? **

If you just need it once, use method injection.
If you need a few times, inject it in the constructor.


This next:

https://laracasts.com/lessons/repositories-simplified

https://laracasts.com/series/laravel-from-scratch-2017/episodes/24







