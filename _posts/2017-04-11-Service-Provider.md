---
layout: default
title: "Service Provider"
date: 2017-07-20
---

# Why do we need Service Providers?

This puzzled me for a while, until I read this:

[LaravelTips](https://laraveltips.wordpress.com/2015/06/11/how-to-create-a-service-provider-in-laravel-5-1/)

## Make an Interface.

```
namespace App\Helpers\Contracts;

Interface RocketShipContract
{

    public function blastOff();

}
```

## Make a Concrete Class (which implements the interface).

```
use App\Helpers\Contracts\RocketShipContract;

class RocketShip implements RocketShipContract
{

    public function blastOff()
    {

        return 'Houston, we have ignition';

    }

}

```

## Create a Service Provider

```
php artisan make:provider RocketShipServiceProvider

```

Use this to bind the concrete class to the interface:

```
    public function register()
    {
        $this->app->bind('App\Helpers\Contracts\RocketShipContract', function(){

            return new RocketShip();

        });
    }
```

## Using The Rocketship.

```
public function index(RocketShipContract $rocketship)
```


We have type hinted the interface but this will create an instance of the concrete class.
This is because of the binding in the service provider.


## Why Do This?

Makes it easy to swap a different concrete class in, just by swapping the binding. 

Cool.








