---
title: "Modern-PHP-Cheatsheet"
date: 2021-11-02
layout: default
---


https://github.com/smknstd/modern-php-cheatsheet

### Type declaration
```
function myFunction(int $param)
```

### Return types

```
function myFunction() : int
```

When a function should not return anything:

```
function myFunction() : void

```

### Class property

```
Class Foo()
{
    public int $bar;
}
```

### Union types

```
function myFunction(string|int|array $param) : string|int|array
```


### Nullable types

If no type it can accept a null

```
function myFunction($param)
```

but as soon as it has a type it won't take a null.


You can make a type declaration explicitly nullable:
```
function myFunction(?string $param)
```

and return types:
```
function myFunction(?string $param) : ?string
```

### Destructuring arrays

```
list($a, $b, $c) = $array;
#assocs
list('foo' => $a, 'bar' => $b, 'baz' => $c) = $array;

```

### Null Coalescing
Fall back when nullable - or undefined
```
$b = $a ?? 'fallback';

# can chain
$c = $a ?? $b ?? 'fallback';


# and an assoc if that element is missing
$b = $a['foo'] ?? 'fallback';

# Null coalescing on object
# property cannot be found

$b = $a->baz ?? 'fallback';

# Or a method - which returns null
$b = $a->bar() ?? 'fallback';
# but error if method not found


```


### Nullsafe operator
s
```
$a = null;
$b = $a?->foo;

```


### Spread operator

```
function countParameters(string $param, string ...$options) : int
```

#### Argument unpacking
```
function add(int $a, int $b, int $c) : int
{
    return $a + $b + $c;
}
$array = [2, 3];
$r = add(1, ...$array);
```

### Array unpacking

```
$array1 = ['foo', 'bar'];
$array2 = ['baz', ...$array1];
```
