---
layout: default
title: "Responsive Revision"
date: 2017-06-14
---

# The Viewport

The viewport is the user's visible area of a web page.

## Setting The Viewport

You should include the following <meta> viewport element in all your web pages:

```
<meta name="viewport" content="width=device-width, initial-scale=1.0">

```

This sets the width of the page to be the width screen nd the zoom.

## Size content to the Viewport
Setting large absolute CSS widths for page elements, will cause the element to be too wide for the viewport on a smaller device. 
Instead, consider using relative width values, such as width: 100%

# Grid view

Just use something like Bootstrap.

# Media queries?

It uses the @media rule to include a block of CSS properties only if a certain condition is true.

```
@media only screen and (max-width: 500px) {
    body {
        background-color: lightblue;
    }
}

```

## Media Queries

Media queries can help with that. We can add a breakpoint where certain parts of the design will behave differently 
on each side of the breakpoint.

Example:

When the screen (browser window) gets smaller than 768px, each column should have a width of 100%.


```
/* For desktop: */
.col-1 {width: 8.33%;}
.col-2 {width: 16.66%;}
.col-3 {width: 25%;}
.col-4 {width: 33.33%;}
.col-5 {width: 41.66%;}
.col-6 {width: 50%;}
.col-7 {width: 58.33%;}
.col-8 {width: 66.66%;}
.col-9 {width: 75%;}
.col-10 {width: 83.33%;}
.col-11 {width: 91.66%;}
.col-12 {width: 100%;}

@media only screen and (max-width: 768px) {
    /* For mobile phones: */
    [class*="col-"] {
        width: 100%;
    }
}
```


## Mobile First

Design for mobile first. This would mean reversing the rule above, so that all columns are 100% unless on desktop. 


