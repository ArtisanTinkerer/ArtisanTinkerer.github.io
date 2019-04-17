---
title: "Relationships-Refresher"
date: 2018-04-17
layout: default
---

# Summary Table

|  Relationship | Relationship  | Inverse  | Retrieving  | Saving  |
|---|---|---|---|---|
|One2One   | hasOne  | belongsTo  | ``` $user->phone ```  | $user->phone()->save($phone);  |
|One2Many   | hasMany  | belongsTo  | ``` $post->comments```  |  ```$post->comments()->save($comment);``` |
| ManyToMany  | belongsToMany  | belongsToMany   | $user->roles()->attach($roleId);  |   |






# One-to-One

A User has one phone number.
A Phone belongs to a user.

## User.php
```
 public function phone()
 {
    return $this->hasOne('App\Phone');
 }
```
*Phone table must have user_id*


## Phone.php

```
public function user()
{
    return $this->belongsTo('App\User');
}
```


## Retrieving (as a dynamic property):

``` $user->phone ```



# One-to-Many
A blog post has many comments.
A comment belongs to a post.

## Post.php

```
 public function comments()
 {
     return $this->hasMany('App\Comment');
 }
 ```
 *Comment table must have a a post_id*



## Retrieving (as a dynamic property):

``` $post->comments```


## Comment.php

```
public function post()
 {
     return $this->belongsTo('App\Post');
 }
```

## Many-to-Many

A user belongs to many roles.
A role belongs to many users.

# Inserting and Updating

*Called as a method, not a dynamic property.*

```$post->comments()->save($comment);```

When using belongs to use associate:

```$user->account()->associate($account);```


```$user->account()->dissociate();```


Many to Many uses attach:

```$user->roles()->attach($roleId);```
```$user->roles()->detach($roleId);```









