2017-01-04-Eloquent-Collections.md

---
layout: post
title: "Can collections resolve this FusionCharts riddle"
date: 2016-01-14
---

# The Problem 

I'm still working om my amazing dashboard application. We need to display widgets which have both single series and multiple series datasets.

# Fusioncharts


This is the complexity:

Single datasets looks like this:


```
"data": [
                {
                    "label": "Jan",
                    "value": "420000"
                }
                
```




multiple look like this:

```
 "dataset": [
        {
            "seriesname": "2013",
            "data": [
                {
                    "value": "22400"
                },
                {
                    "value": "24800"
                },
                
            ]
        },
        {
            "seriesname": "2012",
            "data": [
                {
                    "value": "10000"
                },
                {
                    "value": "11500"
                }
                
            ]
        }
    ]

```


So, the question is, how do I make that from my database?


Maybe a collection and pluck out the series?

Here is what I am getting from a test table:

```
Illuminate\Support\Collection::__set_state(array(
   'items' => 
  array (
    0 => 
    stdClass::__set_state(array(
       'id' => 1,
       'label' => 'Jan',
       'series' => '2013',
       'extraType' => '',
       'value' => 123456,
    )),
    1 => 
    stdClass::__set_state(array(
       'id' => 2,
       'label' => 'Feb',
       'series' => '2013',
       'extraType' => '',
       'value' => 456789,
    )),
    2 => 
    stdClass::__set_state(array(
       'id' => 3,
       'label' => 'Jan',
       'series' => '2014',
       'extraType' => 'line',
       'value' => 123456,
    )),
    3 => 
    stdClass::__set_state(array(
       'id' => 4,
       'label' => 'Feb',
       'series' => '2014',
       'extraType' => 'line',
       'value' => 456,
    )),
  ),
))

```

So, I want to pull out a series, and that needs to be an element in a dataset element.


