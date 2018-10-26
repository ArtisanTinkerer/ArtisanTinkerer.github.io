---
title: "Package Development"
date: 2018-10-26
layout: default
---

# Package Development

## A Note of Facades

When writing a package you will not have access to Laravel's testing helpers.
If you would like to be able to write your package tests as if you are using Laravel you may use **Orchestral Testbench**

https://github.com/orchestral/testbench

### What is a Facade

https://www.sitepoint.com/how-laravel-facades-work-and-how-to-use-them-elsewhere/

A facade is a class, wrapping a complex library to provide a simpler more readable interface.

<img src="/images/Facade.png" alt="missing" class="inline"/>

