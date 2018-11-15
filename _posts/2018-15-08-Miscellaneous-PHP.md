---
title: "Miscellaneous-PHP"
date: 2018-11-15
layout: default
---

# Anonymous Functions
https://phptherightway.com/pages/Functional-Programming.html

## Assigning to Variables

```
$addition=function($arg1,$arg2){

return 'sum = '.$arg1+$arg2;

};
```


## Using anonyomous function as a callback

```array_map``` can be passed a callback

```
$new_array = array_map(function($num){

return $num*$num;
}, $num_array);
```

## Creating Closures with anonymous functions

A closure is same as the lambda apart from it can access the variable which is created outside of its scope or are not in its perimeter.

```
//define a regular variable

$user='Peter';

//create a closure using anonymous function

$message=function() use ($user){

echo 'hello'. $user;

}

```

Altering the $user variable in the function will not change it outside.





# The Strategy Pattern
Define a family of algorithims.

Logger interface.
3 Different logging classes implement this interface.











