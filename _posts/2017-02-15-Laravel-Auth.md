---
layout: default
title: "Laravel Auth"
date: 2017-02-15
---


# Authentication and Authorisation

## RegisterController

## LoginController

This is where we change the redirect after login:
``` 
protected $redirectTo = '/home';

```


## ForgotPasswordController

## ResetPasswordController

# Auth::routes()

```

// Authentication Routes...
$this->get('login', 'Auth\LoginController@showLoginForm')->name('login');
$this->post('login', 'Auth\LoginController@login');
$this->post('logout', 'Auth\LoginController@logout')->name('logout');

// Registration Routes...
$this->get('register', 'Auth\RegisterController@showRegistrationForm')->name('register');
$this->post('register', 'Auth\RegisterController@register');

// Password Reset Routes...
$this->get('password/reset', 'Auth\ForgotPasswordController@showLinkRequestForm');
$this->post('password/email', 'Auth\ForgotPasswordController@sendResetLinkEmail');
$this->get('password/reset/{token}', 'Auth\ResetPasswordController@showResetForm');
$this->post('password/reset', 'Auth\ResetPasswordController@reset');

```


# Adding To a New Application (Dashboard)

Connecting to the User database, to get perms.

* Rules are defined in AuthServiceProvider boot method



# Authorisation


* Using primary verbs: can, cannot, allows and denies.

* Peformed using the Gate facade.

* Convenience helpers for controllers, User model, as middleware and Blade .

## Defining Rules

boot() method of AuthServiceProvider

* rules are called abilities - string key and returns a boolean

Steps:

1. Define a key verb-modelName  eg. update-contact
2. Define the closure - user and then object(s) checking access to eg. ($user, $contact)
3. In this function, do the check, return true or false
  could also use a class and a method ``` gate->define('update-contact','ContactACLChecker@updateContact');  ```
  
  
  
## The Gate Facade

* Simplest way to test against rule.*

```
If(Gate::allows('update-contact',$contact)){
  //Update contact

}

```

## The Authorise Middleware

* If you want to authorise entire routes you can use the Authorise middleware. (shortcut of can).

```
Route::get()->middleware('can:create-person');
```

## Controller Authorization

* Base controller imports AuthorizesRequests trait
  authorize();
  authorizeForUser();
  authorizeResource();
  
  This means that you can do
  
  ```
  
  $this->authorize('update-contact', $contact);
  
  ```
  
  
## Blade Checks

```
@can('edit-contact',$contact)
  

@endcan
```

## Intercepting Checks

## Policies

All above access controls required Eloquent models,

Used for access on a particular resource(model).


## How Do I Want To Use This?

### Amend AuthServiceProvider boot:

```

    public function boot(GateContract $gate)
    {
        $this->registerPolicies($gate);

        //These are the auth rules, normally they are for
        // a table and are obtained from the Web User Manager
        $gate->define('drawings', function($user){
            return $user->canDo('drawings');
        });
    }

```

I was getting: ```Class App\Providers\GateContract does not exist ```

So I added this:

```
use Illuminate\Foundation\Support\Providers\AuthServiceProvider as ServiceProvider;

```

### Add these to the index functions in the controllers:

```
if (Gate::denies('auth_codes', Image::class)) {
            return Redirect::back();
        }
```









# Laravel Version

Need to be on 5.3 and the labelling app I am working on is only 5.2.39.

Not sure I want to upgrade, will look at docs for 5.2 authentication.

Just added this to me ImagesController:


```
if (Gate::denies('maintain-images', Image::class)) {
          return Redirect::back();
      }

```






## Using with Datatables

This can de dropped into my DatatablesController

```
        if (Gate::denies($this->table, Image::class)) {
            return Redirect::back();
        }
```

Then add this to the AuthServiceProvider:

```
$gate->define('staff', function($user,$image){
            return $user->canDo('staff',$image);
        });


```

## How Am I Using in the Reporting Utility

Edit AuthServiceProvider.php
```
$gate->define('admin', function($user){
            return $user->canDo('admin');
        });

```

Maybe just protect the maintenance routes.







