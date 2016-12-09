---
layout: post
title: "Dashboard Project - My First API"
date: 2016-12-06
---

# Dashboard Project

## Background

My next project is to create a dashboard application. This needs to be as flexible as possible, so that we can display graphs and Datatables from multiple sources.


## Technology

I have made some good progress with the frontend, we really wanted resizable, drag and drop widgets (hate that word, but don't know what else to use)
. I have got this working, using Gridstack.js and Vue.js (also my first Vue project!).

##AJAX

Since I am now using Vue, I figured I should be using Axios, seems pretty simple so far:
```
 axios.get('/dashboardWidgets?dashboard=1')


                    .then(function (response) {
                        console.log(response);
                        alert('Done');
                    })
                    .catch(function (error) {
                        console.log(error);
                    });
```                   
                    

### Assets
I have also started to use Laravel Elixir (which uses gulp) to build and version my assets! This is a great step forward and will now do it in all my projects. 


###Vue.js

I am using Vue compponents for each type of dashboard widget;
```
  Vue.component('gauge-widget', {
            props: ['widget'],
            template:
            '<div class="grid-stack-item":data-gs-x="widget.x" :data-gs-y="widget.y" :data-gs-width="widget.width" :data-gs-height="widget.height" :id-for-save="widget.id">'+
            '<div class="grid-stack-item-content"  :id="widget.contentId"></div>'+
            '</div>'

        });
```


##Progress

I'm just refactoring the front end, the JS is all in the Blade template and I need to move it out now it is working.

I was watching some Laracon videos and saw in this [Amanda Folson - Laracon Talk](https://streamacon.com/video/laracon-us/amanda-folson-apis-with-lumen) that she suggested using Fractal, so I m currently trying to get that working.

##Refactoring

I have just refactored the front end and was really struggling with JS timings (what a surprise), my Datatable was not initialising because the table wasn't rendered at this point.

I have just got round this by using the Vue updated event instead of mounted.
```
    updated: function () {

        var self = this;
        self.tablesList.forEach(initialiseTable);

        alert('Bingo');

    },
```

This is working, just not sure this is the best place to put it.

All my Vue components are now Single File Components and Gulp Watch is running and working!





