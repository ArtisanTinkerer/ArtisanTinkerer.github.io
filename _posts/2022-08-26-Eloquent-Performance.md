---
title: "Eloquent Performance"
date: 2022-08-26
layout: default
---


https://laracasts.com/series/eloquent-performance-patterns

## 01 Measure Performance
* debug bar?
* how many queries get run? n+1 eager loading
* how long does each query take - do we need an index
* memory usage - performance 
* look at the models tab - more eager loading?

## 02 Minimise Memory Usage
* memory usage roughly 4mb? - up to 20mb
* this was a select *

add a select:
```
$years = Post::query
  ->select('id', 'title')

```

strip down related:

```
->with('author')

//can be 

->with('author:id,name')

```

useful when we have a lot of records, look at metrics

## 03 Get one record from a has many relationship.
* looking for last_login_date
* look at memory again (14MB)
* use a subquery
* $users = User::query()
*   ->addSelect(Select['last_login_at' => Login::select('created_at')])
*   ->whereColumn('user_id', 'users.id')
*   ->latest()
*   ->take(1) //cam only return one column

