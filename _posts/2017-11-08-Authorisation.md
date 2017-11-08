---
layout: default
title: "Authorisation"
date: 2017-11-08
---

Just thought brushing up on Laravel authorisation would be a good idea.

Based on the 5.5 documentation.

**There are two ways to authenticate: gates and policies**

Think of gates and policies like routes and controllers.

* Gates provide a simple closure based approach - not related to a model.
* Policies group their logic around a particular model or resource.


## Gates

* Typically defined n ```AuthServiceProvider``` using the Gate facade.
* They always receive a user instance - may have additional parameters.

```
 Gate::define('update-post', function ($user, $post) {
        return $user->id == $post->user_id;
    });

```
#### Resource Gates

They can also be defined using a resource method:

```
Gate::resource('posts', 'PostPolicy');
```

### Authorising Actions

Just use allow on denies like this:

```

if (Gate::allows('update-post', $post)) {
    // The current user can update the post...
}

```

## Policies

Organise authorization logic around a particular model or resource.
If you have a ```Post``` model, you will have a ```PostPolicy```.

```
php artisan make:policy PostPolicy  --model=Post
```


### Registering Policies

Policies need to be registered in ```AuthServiceProvider```.

```
   protected $policies = [
        Post::class => PostPolicy::class,
    ];
```

### Writing Policies

```
 public function update(User $user, Post $post)
    {
        return $user->id === $post->user_id;
    }
```

### PolicyFilters

These can be added, so that all policies are overwritten.

### Authorising Actions Using Policies

**Via the User model**
Two methods ```can``` and ```cant```.

```
if ($user->can('update', $post)) {
```

This calls the policy for the model which is registered. 

### Via Middleleware

Middleware can be used, to prevent actions even getting to the controller.

By default the ```Authorize``` middleware is assigned the ```can``` key in the ```Kernel``` class.

```
Route::put('/post/{post}', function (Post $post) {
    // The current user may update the post...
})->middleware('can:update,post');

```

### Via Controller Helpers

Laravel provide the ```authorize``` method for controllers.

```
 $this->authorize('update', $post);
```
 
### Via Blade Templates


```
@can('update', $post)
```






Now watch this:

[https://laracasts.com/series/lets-build-a-forum-with-laravel/episodes/24](Let's Build a Forum)

