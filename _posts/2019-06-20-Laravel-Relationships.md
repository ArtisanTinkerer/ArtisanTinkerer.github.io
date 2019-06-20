---
title: "Laravel-Relationships"
date: 2019-06-20
layout: default
---

## One To One
User has a phone number.

hasOne and belongsTo

## One To Many
A blog has many comments

hasMany and belongsTo

## Many To Many
A user has many roles (roles can also belong to many users)
belongsToMany and belongsToMany

### Intermediate Table Columns

```
$role->pivot->created_at
```

If you have extra columsn in your pivot, you need to do ```withPivot```

You can also filter by the pivot:

```return $this->belongsToMany('App\Role')->wherePivot('approved', 1);```


### Intermediate Table Models

```
return $this->belongsToMany('App\User')->using('App\RoleUser');

```
Extend the Pivot class:
```
class RoleUser extends Pivot
```


## Has One Through

```
users
    id - integer
    supplier_id - integer

suppliers
    id - integer

history
    id - integer
    user_id - integer
```


Can get to 

## Many Through


## Querying Resistance Existance

```
$posts = App\Post::has('comments')->get();

```

```
$posts = App\Post::doesntHave('comments')->get();
```







