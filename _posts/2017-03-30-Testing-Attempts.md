---
layout: default
title: "Testing-Attempts"
date: 2017-03-30
---

# Testing the Process Loss Application

Ok, I promise, next application I will do TDD. 

I needed to get a demo out pretty quickly. This application is ready to show to the users.  

So I figured I should try and write some tests. I am using *Laravel Up & Running" as a guide.

Started by modifying the ExampleTest:

```
 public function testBasicExample()
    {
        $this->visit('/home')
             ->see('username');
    }

```

## Problem 1 - How to log in?

This seems to work:

```
$this->visit('/login')
            ->type('test', 'username')
            ->type('test', 'password')
            ->press('Login')
            ->seePageIs('/home');


```


To run tests: ```./vendor/bin/phpunit```


## Naming Tests

Anything in the testing directory gets run if names end in Test.
Methods also need to have the word test as a prefix.

Application environment is always testing.








