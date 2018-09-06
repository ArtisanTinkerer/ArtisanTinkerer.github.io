---
title: "Eloquent-Resources"
date: 2018-09-06
layout: default
---

## Resources are for individual models.
```
php artisan make:resource User
```

## For collections use Resource Collections

**I think these are optional, just if you want additional metadata**

```
php artisan make:resource Users --collection
php artisan make:resource UserCollection
```

To use collections:

```
 UserResource::collection(User::all());
```

## Relationships

```
'email' => $this->email,
        'posts' => PostResource::collection($this->posts),
        'created_at' => $this->created_at,
```


## Data Wrapping

Default is in ```data``` but this can be disabled with withoutWrapping.

## Pagination

```UserCollection(User::paginate());```

this adds the ```meta``` and ```links``` keys.

## Conditional Attributes

```when``` can be used to conditionally add attributes:

```
'secret' => $this->when(Auth::user()->isAdmin(), 'secret-value'),
```

## Merging Conditional Attributes

```
      $this->mergeWhen(Auth::user()->isAdmin(), [
            'first-secret' => 'value',
            'second-secret' => 'value',
        ]),
```

## Conditional Relationships


## Adding Meta Data
