---
title: "Miscellaneous-PHP"
date: 2018-11-15
layout: default
---

# Anonymous Functions
https://phptherightway.com/pages/Functional-Programming.html

## Mick's example
```
public function test3()
    {
        $fixed = 27;
        $hi = 'hi';

        //the variable fixed is stored at the function at this point
        $addOneToFixed = function($hi) use ($fixed){
            if($hi === 'hi'){
                return $fixed +1;
            }
        };

        $fixed = 28000;
        dd($addOneToFixed($hi));

    }
```

The variable inside () is passed when the function is called, the variable in the use is actually fixed when the function is defined



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






# Laravel From Scratch 5.7
## 21 Service Container and Auto-Resolution
Auto resolving when type hinting - looks in the Service Container (basically a big list of key-value pairs).
Can use ```app(Filesystem::class) ```

Putting things into the toybox (Service Container):
```
app()->bind('example', function(){
  return new \App\Example;
});
```
if you want a singleton:
```
app()->singleton('example', function(){
  return new \App\Example;
});
```

to retrieve:

```
app('example')
```

You don't need to bind, if you use the class path:
```
app('App\Example');
```

If Example depends on a Foo, inject this into it's constructor. This will get auto resolved.



When to use the Service Container.

## 22 Service Providers


* need to be registered in ```app.php```
* ```register``` method is where you bind
* Laravel runs through all the service providers and calles ```register```
* It then runs through again and calls ```boot```


Can just add to ```AppServiceProvider``` or create a dedicated provider (must add to ```app.php```).

Can bind an interface to a class.








