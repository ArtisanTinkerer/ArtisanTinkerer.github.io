---
layout: default
title: "Vue Knowledge Upgrade"
date: 2017-10-03
---

I'm trying to get a good sytem for editing complex REST forms. I think the answer is probably to use Vue more. 

I think I need to go through some of lessons again in [https://laracasts.com/series/learn-vue-2-step-by-step](https://laracasts.com/series/learn-vue-2-step-by-step).

# Named slots

<template>
  slot="header""
</template>

Single Use Components
Inline -template

How does Hot Module Replacement work with Laravel Mix

# Object-Orientated Forms 1. 

He has the form being handled in @submit.prevent="onSubmit"
onSubmit is in the main view instance
Store is POST to /projects.
POST with axios
axios.post('/projects', this.$data)
Server validation is OK
```
data:{
  errors: {}
}

axios...
.catch(error => this.errors = error.response.data)

```
```
<span class="help is-danger" v-text="errors.get('name')">  </span>
```

I could use this method for my validation errors. It does look neat.
9:05

 # Object-Orientated Forms 2. 

This could be good but the field names are hardcoded in app.js

He does this to preserve *this*

```
.then(this.onSuccess.bind(this))
```

He clones objects like this:
```
let data = Object.assign({},this);

```
Still not sure how I could use this.

# Object-Orientated Forms 3


# Webpack
Moving code out from app.js.

# Episode 23 Laravel Mix

Only in Laravel 5.4.

# Episode 24 Shared State 101

# Episode 25 Custom Input

Good for components which will be reused in a project.

# Episode 26 Vue SPA Essentials: Routing

Single Page Applications. 

# Episode 29 Dedicated Form Components








# Thoughts
Should I use more components in my edit form.
My ch-widget-editor is single use, maybe this should be done inline?

Google for Vue/Laravel resuable forms.
Hot module replacement in Laravel?







