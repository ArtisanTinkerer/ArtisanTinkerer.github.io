---
layout: post
title: "Laravel redirect all mistyped URLS"
date: 2016-08-11
---

http://laraveldaily.com/routes-file-redirect-everything-else-to-homepage/


Route::any('{query}', 
  function() { return redirect('/'); })
  ->where('query', '.*
