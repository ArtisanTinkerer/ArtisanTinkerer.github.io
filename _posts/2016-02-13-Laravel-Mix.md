---
layout: post
title: "Laravel Mix"
date: 2016-02-12
---


# Migrating from 5.3 - 5.4

This means moving from Laravel Elixir to Laravel Mix

I kept getting this error, when trying:

npm install webpack
npm install laravel-mix --save-dev



```
npm WARN optional Skipping failed optional dependency /chokidar/fsevents:
npm WARN notsup Not compatible with your operating system or architecture: fsevents@1.0.17
```


This may be OK:

"For example the package fsevents is often used as optional dependency but fails on linux as it is not needed there. (That was at least the reason why I saw the message in our project)"
[GitHub](https://github.com/npm/npm/issues/9204)

But when I run:``` npm run webpack```
I get:

```
npm ERR! missing script: webpack
```


Doh, realised that I need to run ```npm run dev```

This gives me a DONE message.


## Stylesheets



## JS

These need to reside in resources/assets/




# Gone back to Laravel 5.3.4 and Elixir
Not got time work on this the moment.



