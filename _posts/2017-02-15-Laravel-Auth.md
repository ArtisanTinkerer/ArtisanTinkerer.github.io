---
layout: default
title: "Laravel Auth"
date: 2017-02-15
---


# Authentication and Authorisation

## RegisterController

## LoginController

This is where we change th redirect after login:
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


* Using primary verves: can, cannot, allows and denies.

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

* Simplest way to test against rule.
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








