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

** Method injection or constructor injection? **

If you just need it once, use method injection.
If you need a few times, inject it in the constructor.



At this point I think it's worth going back to Matt's book.

## The Container ##

Service container or dependency injection container.

** Dependency injection means that dependencies are not newed up, they are injected.**
Most commonly with constructor injection.
Also setter injection.
and method injection.

** Primary benefit, is that we can change what we are injecting. **
:mock dependencies
:instantate shared dependencies

Inversion of control, is when decisions are made at the heighest level (config), not at the class level.

Most common form of dependency injection is constructor injection.

Manual dependency injection can soon get messy:
```
$mailer = new MailgunMailer($a, $b.$c)

```


## The app() Global Helper ##
This is how the container works.
Pass any string to this and it will return an instance.
```
$logger = app(Logger:class);
```
Where are the parameters? (For the constructor.)

* The container reads typehints (autowiring) *

Autowiring means that the container can resolve a class, if it has no constructor dependencies.

If they have constructor parameters, we need to bind to the container.

## Binding classes to the container ##

Binding a class to the container is essentially telling the container how to instantiate it (parameters and dependencies).
Bind in a service providers ```register()``` method.

```
public function register(){

  $this->app->bind(Logger::class, function ($app)){
    return new Logger('log/path/here','error');
  }
}

```


``` $this->app ``` is an instance of the container on every service provider

## Service Providers ##

Just popped back to page 227


Almost all of Laravels bootstrap is separted  into service providers.
A service provider is a class that encapsulates logic for various parts of the application need to run to bootstrap.
** Code which needs to run in preparation for the application to run. **








This next:

https://laracasts.com/lessons/repositories-simplified

https://laracasts.com/series/laravel-from-scratch-2017/episodes/24







