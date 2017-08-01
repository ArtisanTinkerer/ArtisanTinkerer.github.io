---
layout: default
title: "TDD Day One"
date: 2017-07-31
---

Ok, no more delay. This is the first day of using TDD.

## Laravel Dusk and Vue.js

I still haven't figured how to get Dusk working, or how to test my Vue components but I'm going to get started with PHPUnit tests and aim to progress
from there.

## Laravel Up and Running ##

As usual I will be reading Matt's book as I go.

## Laracasts

I have also renewed my Laracasts subscription, it is the best way to keep my skills up-to-date. I have started watching some of this 
[https://laracasts.com/series/lets-build-a-forum-with-laravel] (Build A Forum)


## Starting Simple

I have added a couple of tests and am just visiting URLs and checking that I see some text:

```
   public function testReportScheduleLoads()
    {
        $this->visit('/reports/maintain')
             ->see('ch-datatable');
    }

```

## What else can I do?


## JSON Tests

These look pretty simple:

```
    $this->json('get','reports/78/edit');

    $this->seeJson(['name' => 'Datatable']);

```

** At the moment I have some stuff hardcoded, eventually these will go and I wll be creating models in these tests **

## Naming Tests

* filename must end in Test
* methods must start with name test (or docblock contains @test)


## The TestingEnvironment

.env is not loaded - phpunit.xml used instead


## The Testing Traits

### WithoutMiddleWare ###

### Database Migrations ###

This will run all the database migrations.
This is the way I want to go, maybe use an SQLLite DB in memory.

### Database Transactions ###

Expects DB to be 'ready', it wraps all the tests in transactions and rolls the back

## What else?

```
$this->call;
$this->followRedirects;
```

``` this->assertPageLoaded() ``` Just loads the page and returns a 200.

``` this->see() ``` and ``` this->dontSee() ```



``` this->seeLink() ``` and ``` this->dontSeeLink() ```

``` this->seeHeader() ```
``` this->seeCookie() ```
``` this->seeInField() ``` and ``` this->dontSeeInField() ``` - looks for a value in an input or text area

``` this->seeIsChecked() ``` and ``` this->dontSeeIsChecked() ``` - looks at a checkbox

``` this->seeIsSelected() ``` and ``` this->dontSeeIsSelected() ``` - for checking selects

``` this->seePageIs() ``` checs the loaded page

``` this->seeInDatabase() ```and  ``` this->dontSeeInDatabase() ``` - for checking db values exist

### Clicking and Forms - pg 275


I think that this will do for now, I will add more as I learn it.

Tried working through [https://laracasts.com/series/lets-build-a-forum-with-laravel](https://laracasts.com/series/lets-build-a-forum-with-laravel) but this is for 5.4.




















