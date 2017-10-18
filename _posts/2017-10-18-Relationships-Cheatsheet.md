---
layout: default
title: "Relationships-Cheatsheet"
date: 2017-10-18
---

## One to One

### User
```
 public function phone()
    {
        return $this->hasOne('App\Phone');
    }
    ```


### Phone
```
public function user()
    {
        return $this->belongsTo('App\User');
    }

```

Needs a user_id foreign key field.

## One to Many

### Post
```
  public function comments()
    {
        return $this->hasMany('App\Comment');
    }
    ```


### Comments
```
 public function post()
    {
        return $this->belongsTo('App\Post');
    }

```

Needs a post_id foreign key field.


## Many to Many

### Users
```
  public function roles()
    {
        return $this->belongsToMany('App\Role');
    ```


### Roles
```
 public function users()
    {
        return $this->belongsToMany('App\User');

```






