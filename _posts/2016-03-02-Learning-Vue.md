
---
layout: post
title: "Learning Vue"
date: 2016-03-02
---

# Declarative Rendering
```
<div id="app">
  {{ message }}
</div>
```


```
var app = new Vue({
  el: '#app',
  data: {
    message: 'Hello Vue!'
  }
})
```


Now, by modifying **app.message**, we can change the data. 
**The data and the DOM are now linked**



## v-bind ##
A Directive can bind elements to attributes:
```
<span v-bind:title="message">
```


