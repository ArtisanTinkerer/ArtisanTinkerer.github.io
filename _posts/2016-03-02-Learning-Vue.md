
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


## Conditionals and Loops ##

You can use **v-if** to show or hide, by modifying the data.

```
<p v-if="seen">Now you see me</p>


var app3 = new Vue({
  el: '#app-3',
  data: {
    seen: true
  }
})
```

You can use **v-for** to loop through an array from data. 


## Handling User Input ##

Use **v-on** to attach event listeners to invoke methods.

```
<button v-on:click="reverseMessage">Reverse Message</button>
```

# Components #

Register components.

```
Vue.component('todo-item', {
  template: '<li>This is a todo</li>'
})

<todo-item></todo-item>

```
** But this would render the same text for every todo **
So, we use props - to pass from parent scope to child 

Like this:
```
<todo-item v-for="item in groceryList" v-bind:todo="item"></todo-item>
```

** Props are used to pass from the HTML into each component




# Notes From Laracasts

Lesson 1 

** Bind data to input **
v-model is for form inputs only

```
v-model = "message"
{{message}}
data:{
  message:'sadsa'
  }
```

## computed properties










