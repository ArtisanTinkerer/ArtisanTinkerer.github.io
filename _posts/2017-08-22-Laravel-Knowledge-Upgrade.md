---
layout: default
title: "Laravel Knowledge Upgrade"
date: 2017-10-17
---

I haven't read the Laravel documentation for a while So I figured I should skim through the latest version (5.5) and see if any gaps in my knowledge need filling.


## Configuring Caching

Should cache the config when deploying:
```php artisan config:cache ```

## Deployment

Don't forget all the optimizations.

## Facades

A static interface to classes that are available in the application's service container.

- static proxies to underlying classes in the service container
- expressive syntax - more testability
- don't need classes 

## Contracts

Set of interfaces which define the core services provided by the framework.

Contracts allow you to define explicit dependencies for your classes. 

Contracts are easier to use test when used on packages.


### Repository Example

$cache is passed into the constructor:
```
public function __construct(\SomePackage\Cache\Memcached $cache)
```

Code is tightly coupled to a given cache implementation.

**Solution**
Depend on a simple, vendor agnostic interface:
```
use Illuminate\Contracts\Cache\Repository as Cache;

...

 public function __construct(Cache $cache)

```
The contracts package contains no implementation and no dependencies.
Easier to replace cache implementation.

#### How To Use Contracts

* Many types of classes in Laravel are resolved through the service container.
* To get an implementation of a contract. type-hint the interface in the constructor/

**A contract is just an interface**

[htps://laracasts.com/discuss/channels/laravel/when-to-use-contracts]

"If you do decide to change newsletter services, all you have to do is change the binding and your code will function as before."

## CSRF Protection
Cross Site Request Forgery.
**Token is needed in forms**

**By default, the  resources/assets/js/bootstrap.js file registers the value of the csrf-token meta tag with the Axios HTTP library. **

## Security

### Authentication 

Guards define how users are authenticated for each request.

Call middleware from constructor:

```
  $this->middleware('auth');

```


### API Authentication (Passport)

APIs typically use tokens to authenticate users and do not maintain session state.

Install Passport.
Add HasApiTokens trait to the App\User model.

Developers building applications that need to interact with your API need to register their applications by creating a client.
- name and URL to redirect to after approval


### Authorisation

Gates are Closures that determine if a user is authorized to perform a given action and are defined in AuthServiceProvider

## Digging Deeper

### Events

Laravel's events provide a simple Observer implementation.

Event classes are in ```app/Events```.

Listeners classes are in ```app/Listeners```.

Events serve as a great way to decouple various parts of your application -
single event can have several listeners which do not depend on each other.

Events and Listeners are registered in ```EventServiceProvider```.

```
protected $listen = [
        'App\Events\TestEvent' => [
            'App\Listeners\TestListener',
        ],
    ];
```
Then just run ```php artisan event:generate```.

An event class is simply a data container which holds the information related to the event. 

Example - Order Shipped

```
    public function __construct(Order $order)
    {
        $this->order = $order;
    }

```

Event Listeners receive the event instance in their handle method.

### Broadcasting

Websockets are typically used to send a message from the server and update the client.
This saves polling the application for changes.


config is in broadcasting.php

## Cache

Laravel supports Memcached and Redis

Can just cache values (not sure why) or collections.



## Notifications


## Queues

Queues allow you to defer the processing of a time consuming task.
Configuration is in queue.php.


Having several queues can be useful. High priority one can be processed first.

### Creating Jobs
Jobs are stored in the ```app/Jobs``` directory.
To make a job : ```php artisan make:job ProcessPodcast```

Changed queue driver to database.
Jobs are going into the jobs table.

### Running the Queue Worker.

```php artisan queue:work```

### Dealing With Failed Jobs

Failed queue table

# Refresh

## Service Providers




# Revise

Contracts
Service Container 
When to use queues and when to use observers.



# Don't forget

Guards!

## Difference between Contract and Facade 


