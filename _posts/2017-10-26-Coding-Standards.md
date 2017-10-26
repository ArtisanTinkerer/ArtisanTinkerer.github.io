---
layout: default
title: "Coding Standards"
date: 2017-10-26
---

# Coding Standards

I try and do PHP The Right Way (PHPTRW) as much as possible [http://www.phptherightway.com/]{http://www.phptherightway.com/}, so I just thought I should
make a quick note on coding standards. Laravel Best Practices [http://www.laravelbestpractices.com/#code_style_guide]{http://www.laravelbestpractices.com/#code_style_guide}
suggests that we use PSR-1, PSR-2 and PSR-4. Let's summarise some of these:

## PSR-1
### Classes should be in StudlyCaps.
### Class constants - uppercase with underscores.
### Method names - camelCase.
### Must use UTF-8 without BOM
### Files should either declare (classes, functions, constants, etc.) or cause side effects but not both:

For example:

```
<?php
// side effect: change ini settings
ini_set('error_reporting', E_ALL);

// side effect: loads a file
include "file.php";

// side effect: generates output
echo "<html>\n";

// declaration
function foo()
{
    // function body
}

```

### Classes should be in there own files.

## PSR-2

### 4 spaces for indenting, not tabs.
### One blank line after namespace and use statements block.
### Opening and closing braces on the next line.
### Visibility on all methods, abstract and final before visibility, static after.
### Control structures braces like this:

```
if ($a === $b) {
    bar();
 } elseif ($a > $b) {
    $foo->bar($arg1);
 } else {
     BazClass::bar($arg2, $arg3);
 }
```
### Closing tag omitted from files containing only PHP.
### PHP Keywords must be in lower case, as well as true,false and null.
### One use statement per declaration.
### Visibility declared on all methods.
### Underscores should not be used to indicate protected or private.
### Method arguments - must be a space after comma, not before. Arguments with default parameters must be at the end.
```
public function foo($arg1, &$arg2, $arg3 = [])
```
### Do and While loops should look like this:

```
do {
    // structure body;
} while ($expr);

```

### For statements should look like this:

```
for ($i = 0; $i < 10; $i++) {
    // for body
}
```

### Foreach
```
foreach ($iterable as $key => $value) {
    // foreach body
}

```

### Try and Catch
```
try {
    // try body
} catch (FirstExceptionType $e) {
    // catch body
} catch (OtherExceptionType $e) {
    // catch body
}

```


## PSR-4 - Autoloading




# More from Laravel Best Practices

