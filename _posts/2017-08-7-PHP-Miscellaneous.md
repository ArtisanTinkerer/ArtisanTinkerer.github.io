---
layout: default
title: "Miscellaneous PHP"
date: 2017-04-11
---

## PHP Security Cheatsheet

[PHP Security Cheat Sheet](https://www.owasp.org/index.php/PHP_Security_Cheat_Sheet)

* Use PDO
* CSRF

### Database

Never concatenate or interpolate data in SQL.
Use prepared statements instead.
Use an ORM.
USE UTF-8

### Authentication and Session Management

Bind session to IP address.

[UTF-8 All the Way](https://stackoverflow.com/questions/279170/utf-8-all-the-way-through)



[Filter Vars](https://www.w3schools.com/php/func_filter_var.asp)

## Security Basics

1, Validate (is_int etc) or cast?
2, check isset()
3, strip tags
4,  htmlentities() converts characters to html enteties to allow tags to be stored/displayed.
5, use preg_match() - true or false
 



