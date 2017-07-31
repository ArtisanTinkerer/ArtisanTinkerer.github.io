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



