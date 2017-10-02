---
layout: default
title: "Laravel Security"
date: 2017-10-02
---

# Laravel Security 

Just a quick refresher on how Laravel handles security.
[http://www.easylaravelbook.com/blog/2015/07/22/laravel-key-security-features/]{http://www.easylaravelbook.com/blog/2015/07/22/laravel-key-security-features/}

## SQL Injection

Laravel uses PDO parameter binding

### CSRF

Laravel uses tokens to prevent this. 

### Cross-Site Scripting

Basically just JS places in form fields.

Laravel automatically escapes HTML entities.



