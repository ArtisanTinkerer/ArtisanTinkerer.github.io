---
title: "PHP-Security"
date: 2021-11-02
layout: default
---





## Intro
Disable register_globals.
display_errors to off - log_errors to on - error_reporting to required level
Filter all input

### Escaping:
```htmlentities($string, ENT_QUOTES, 'UTF-8')``` to stop code executing
``` mysql_real_escape_string()``` or addslashes() with mysqli
Laravel : no need to clean because it uses PDO


## Forms and URLs
XSS = Cross-site scripting
CSRF = Cross-site request forgeries.

Tainted data =
* form data
* email
* XML

User can send data as:
* URL param GET
* request param POST
* HTTP header


## Semantic URL Attacks
modifying the URL

## File Upload Attacks

Danger when displaying.
Mime types.

## XSS - Cross-site scripting.
Any application which displays input is at risk.
Filter input and escape output.

## CSRF - Cross-site request forgeries

Using an image is common way to launch
Send the victim an image with a URL+params

### To mitigate
* use POST not params
GET is just for retrieval
Make the user use your own forms - add a token .


## Spoofed Form Submissions

## Spoofed HTTP Requests
Using telnet/PHP/Postman?

## Databases and SQL
All data from db must be filtered and all going to must be escaped.

### SQL Injection

* failure to filter as it enters app
* and failure to escape data when sent to db

Just use PDO.

## Sessions and Cookies
Cookie theft, exposed session data, session fixation and session hijacking.

HTTP is stateless.
Cookies invented for this reason.

### Cookie theft

This can lead to session hijacking
Probably with xss
Client side scripts have access to cookies.

### Exposed session data
SSL can help

### Session Fixation
Session identifier should be kept secret.
Make the victim use a session identifier chosen by the attacker.


Page 57?


_____________
Look at Laravel stuff now

Now this:

https://www.cloudways.com/blog/prevent-laravel-xss-exploits

# Prevent Laravel XSS Exploits Using Validation and User Input Sanitization

Check clean and filter data.

## Laravel Sanitization
```strip_tags```
can be added as middleware



Best 2021 Guide To Protect Against PHP SQL Injection Attacks

https://www.cloudways.com/blog/prevent-php-sql-injection/

This is quite good:

https://www.cloudways.com/blog/php-security/

Ultimate PHP Security Best Practices
* Keep PHP updated



Now upload!
