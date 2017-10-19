---
layout: default
title: "Laravel Knowledge Upgrade"
date: 2017-10-17
---

I haven't read the Laravel documentation for a while So I figured I should skim through the latest version (5.5) and see if any gaps in my knowledge need filling.


# Configuring Caching

Should cache the config when deploying:
```php artisan config:cache ```

# Deployment

Don't forget all the optimizations.

# Facades

A static interface to classes that are available in the application's service container.

- static proxies to underlying classes in the service container
- expressive syntax - more testability
- don't need classes 

# Contracts

Set of interfaces which define the core services provided by the framework.

Contracts allow you to define explicit dependencies for your classes. 

Contracts are easier to use test when used on packages.


## Repository Example

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

## How To Use Contracts

* Many types of classes in Laravel are resolved through the service container.
* To get an implementation of a contract. type-hint the interface in the constructor/

**A contract is just an interface**

[htps://laracasts.com/discuss/channels/laravel/when-to-use-contracts]

"If you do decide to change newsletter services, all you have to do is change the binding and your code will function as before."

## CSRF Protection
Cross Site Request Forgery.

**Token is needed in forms**

**By default, the  resources/assets/js/bootstrap.js file registers the value of the csrf-token meta tag with the Axios HTTP library.**

# Security

## Authentication 

Guards define how users are authenticated for each request.

Call middleware from constructor:

```
  $this->middleware('auth');

```


## API Authentication (Passport)

APIs typically use tokens to authenticate users and do not maintain session state.

Install Passport.
Add HasApiTokens trait to the App\User model.

Developers building applications that need to interact with your API need to register their applications by creating a client.
- name and URL to redirect to after approval


## Authorisation

Gates are Closures that determine if a user is authorized to perform a given action and are defined in AuthServiceProvider

# Events

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

## Broadcasting

Websockets are typically used to send a message from the server and update the client.
This saves polling the application for changes.


config is in broadcasting.php

## Cache

Laravel supports Memcached and Redis

Can just cache values (not sure why) or collections.



# Queues

Queues allow you to defer the processing of a time consuming task.
Configuration is in queue.php.


Having several queues can be useful. High priority one can be processed first.

## Creating Jobs
Jobs are stored in the ```app/Jobs``` directory.
To make a job : ```php artisan make:job ProcessPodcast```

Changed queue driver to database.
Jobs are going into the jobs table.

## Running the Queue Worker.

```php artisan queue:work```

## Dealing With Failed Jobs

Failed queue table


# Task Scheduler

* Only need a single Cron entry.
* Schedule is in ```Kernel.php```

# Database

Three ways to access database: Raw SQL, Query Builder or Eloquent.

## DB Facade.

* Use parameter bindings ```$users = DB::select('select * from users where active = ?', [1]);```
 or named bindings ```$results = DB::select('select * from users where id = :id', ['id' => 1]);```
 
* Transactions can retry when experiencing deadlocks. 

## Query Builder

Uses PDO binding, so don't need to protect against SQL injection.
Fluent:
``` $users = DB::table('users')->get();```

The get method returns a collection of StdClass.

If you just want a single row, you can use ->first:
```$user = DB::table('users')->where('name', 'John')->first();```

If you just want a single field you can use:
```->value('email');```

also ```->pluck```

**Results can be chunked**

**Aggregates can also be done** 

Selects can be done.

**Raw selected can be done but be wary of SQL injection**

## Joins

Inner join = ```->join('contacts', 'users.id', '=', 'contacts.user_id') ```
Left Join = ```->leftJoin('posts', 'users.id', '=', 'posts.user_id') ```

Cross Joins and Unions are also possible.

## Where

```$users = DB::table('users')->where('votes', '=', 100)->get();```

An array of conditions:
```
$users = DB::table('users')->where([
    ['status', '=', '1'],
    ['subscribed', '<>', '1'],
])->get();
```
 There are also some additional where clauses like ``` where Between```.

## Pessimistic Locking
A shared lock prevents the selected rows from being modified until your transaction commits:

``` DB::table('users')->where('votes', '>', 100)->sharedLock()->get(); ```


## Migrations

Creating new:
``` php artisan make:migration create_users_table --create=users ```

The command I always forget:

```php artisan migrate:refresh --seed```

##Column Types

```$table->bigInteger('votes');
$table->double('column', 15, 8);
$table->boolean('confirmed');
$table->date('created_at');
$table->dateTime('created_at');
$table->softDeletes();```
```$table->string('name', 10); ``` VarChar with length

```->nullable()```

##Indexes

When creating:
```$table->string('email')->unique()```

After created:
```$table->unique('email');```

Compound index:
```$table->index(['account_id', 'created_at']);```



##Foreign Key Constraints

```
 $table->foreign('user_id')->references('id')->on('users');
```

Constraints can be enabled and disabled:
```
Schema::enableForeignKeyConstraints();

Schema::disableForeignKeyConstraints();

```

##Redis


##Eloquent

Make model with migration:

```
php artisan make:model User -m
```
If you don't want timestamps:

```
public $timestamps = false;

```

###Retrieving Results 

Getting all: ```$flights = App\Flight::all();```

Each Eloquent model serves as a query builder.

Adding additional constraints:

```
$flights = App\Flight::where('active', 1)
               ->orderBy('name', 'desc')
               ->take(10)
               ->get()
               ```


```all``` and ```get``` return a collection.

** Can use cursors **

###Single Results

```
$flight = App\Flight::find(1);
```

```
$flight = App\Flight::where('active', 1)->first();
```
###Aggregates

```$count = App\Flight::where('active', 1)->count();```

###Inserting and Updating Models

Mass Updates:

```
App\Flight::where('active', 1)
          ->where('destination', 'San Diego')
          ->update(['delayed' => 1]);
          ```
Once line create:

```$flight = App\Flight::create(['name' => 'Flight 10']);```


**FirstOrCreate / FirstOrNew**

New does not persist to the database.

**UpdateOrCreate**

###Deleting Models

If you know the primary key, you can just destroy:

```App\Flight::destroy(1);```

You can also delete by a query:

```$deletedRows = App\Flight::where('active', 0)->delete();```

##Query Scopes



####Global Scopes
Global scopes allow you to add constraints to all queries for a given model. (A bit like soft deletes);


Write a scope that implements the Scope interface. It has one method ```apply```.

```
   public function apply(Builder $builder, Model $model)
    {
        $builder->where('age', '>', 200);
    }
    
```
Then these can be added to models:

```
   protected static function boot()
    {
        parent::boot();

        static::addGlobalScope(new AgeScope);
    }

```

**Removing Global Scopes**

```
User::withoutGlobalScope(AgeScope::class)->get();
```




###Local Scopes
Common set of constraints which mat easily be reused throughout the application.
Just added to models:

```
public function scopePopular($query)
    {
        return $query->where('votes', '>', 100);
    }

```
Then use them like this:
```$users = App\User::popular()->active()->orderBy('created_at')->get();```


###Dynamic Scopes
A scope which accepts parameters. LIke this:

```
 public function scopeOfType($query, $type)
    {
        return $query->where('type', $type);
    }
    
```
And used like this:

```$users = App\User::ofType('admin')->get();```

##Events

Eloquent models fire lots of events. These can then be used to execute code.

To get started, define a ```$dispatchesEvents``` property on your Eloquent model that maps various points of the Eloquent model's lifecycle to your own event classes.

##Observers

If you are listening to many events on a mode, you may use observers to group the listeners.

##Relationships

Refer to my Eloquent Cheatsheet for these.


###Querying Relationship Existence

Only gets posts with comments.

```$posts = App\Post::has('comments')->get();```

Get posts without and comments.
```$posts = App\Post::doesntHave('comments')->get();```

You can count the number of related models:
```$posts = App\Post::withCount('comments')->get();```

###Inserting and Updating Related Models

```
$comment = new App\Comment(['message' => 'A new comment.']);

$post = App\Post::find(1);

$post->comments()->save($comment);
```

**Belongs To Relationships**

You can use the associate method:
```
$user->account()->associate($account);
```
or ```dissociate```.

**Many to Many**

Use the attach for many to many relationships:
```$user->roles()->attach($roleId);```

or ```detach```.

**Synching Associations**

The sync method can also be used to construct many-to-many associations.
``$user->roles()->sync([1, 2, 3]);``

##Collections

All multi result sets are Eloquent Collectons which extend the base Laravel Collection.

##Mutators
Accessors and mutators allow you to format Eloquent attribute values when you retrieve or set.

###Accessors
```
public function getFirstNameAttribute($value)
 {
        return ucfirst($value);
 }
```
retrieve like this ```$firstName = $user->first_name;```

###Mutators

Just like this:
```
  public function setFirstNameAttribute($value)
    {
        $this->attributes['first_name'] = strtolower($value);
    }
    ```

##Attribute Casting

#API Resources

When building an API you need to transform Eloquent Models to JSON.
Laravel resource classes do this.

To generater a resource class:
```
php artisan make:resource User
```
You can also make resources which transflom collections of models.

A resource class represents a single model that needs to be transformed to a JSON structure.
There is just a toArray method:
```
 public function toArray($request)
    {
        return [
            'id' => $this->id,
            'name' => $this->name,
            'email' => $this->email,
            'created_at' => $this->created_at,
            'updated_at' => $this->updated_at,
        ];
    }

```

##Serialization

Array:
```return $user->toArray();```

Converting models to JSON:
```
return $user->toJson();
```

Hiding Attributes From JSON:
```
protected $hidden = ['password'];
```
or whitelist with ```$visible```.

You can also ```$append``` attributes.



##Testing

Unit testing: Most unit tests probably focus on a single method


#Refresh



##Service Providers




#Revise

Contracts
Service Container 
When to use queues and when to use observers.



#Don't forget

Guards!

## Difference between Contract and Facade 


#Links
[https://scaleyourcode.com/blog/article/10](https://scaleyourcode.com/blog/article/10)



