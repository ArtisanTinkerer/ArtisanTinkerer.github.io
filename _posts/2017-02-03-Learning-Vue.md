---
layout: default
title: "Learning Vue"
date: 2017-02-03
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

## Episode 7 

Slots can be filled from above:

```
 <ch-widget-editor widget-types="{{$widgetTypes}}" v-if="showModal" @close="showModal = false">

     <h3 slot="header">custom header</h3>

  </ch-widget-editor>

 <slot name="header">
      default header
  </slot>
```

## Axios

Episode 18

response.data
this.skills = reponse.data


## Object Orientated Forms
https://laracasts.com/series/learn-vue-2-step-by-step/episodes/19

Form @submit.prevent="onSubmit"

```
axios.post('projects'.{

  name: this.name 
  //or
  this.data
  
}
});

```

** add html required **

Laravel validation

"Just let the server do it"

### Errors

add errors: {} to data
```
class Errors{

  constructor(){
    this.errors = {};
  }
  
  get(field){
  
    if (this.errors[field]){
      retuen this.errors[field][0]
    }
    
  }





.catch(error => this.errors.record (error.response.data))


```


```
data:{

  errors: new Errors()

}

```

In the view:

```
<span class="help is-danger" v-text="errors.get('name')"></span>
```

 
## Communication Between Components

How do I pass my dashboards (and the id of the one to display) from my sidebar, to my dashboard component?

Actually maybe I just need to pass the ID.

[Laracasts](https://laracasts.com/series/learn-vue-2-step-by-step/episodes/12)

### Parent - child communication

HTML
```
  <coupon v-on:applied"onCouponApplied"> </coupon>

```


```
this.$emit('applied');



```

app.js - parent

```
  methods: {
        onCouponApplied(){

            alert('I am here');
        }
```


## Communication between components


*app.js*
```
window.Event = new Vue();

```

*component 1*
```
Event.$emit('applied');

```

*component 2*
```
created: function () {
        console.log('created');
        Event.$on('applied',() => alert('in dashboard'))
    },

```


So, I can use this, when I pass the dashboard id from the sidebar.vue to the dashboard.vue




