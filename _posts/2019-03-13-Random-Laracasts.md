---
title: "Random-Laracasts"
date: 2018-03-13
layout: default
---
https://laracasts.com/series/how-do-i/episodes/18
# How to Cleanly Refactor Loops

1, foreach
* create an array
* perform operation
* return array



```
dueForReview = [];

foreach ($staff as $member) {
  //add to dueForReview if pass test
}


```

2, array_filter
```
$dueForReview = array_filter($staff, function($member)) {
  return $member->dueForReview();
})

```

3, use Laravel collection class

```
$dueForReview = collect($data)->flatten()->filter(function ($member) {
  return $member->dueForReview();
});

```

or even:

```
collect($data)
  ->flatten()
  ->filter(function ($member)){
    return $member->dueForReview();
  })
  ->each(function ($member) {
    $member->review();
  )};


```

or higher order collections:

```
collect($data)
  ->flatten()
  ->filter->dueForReview()
  ->each->review();
```



Collect, flatten, then filter.


