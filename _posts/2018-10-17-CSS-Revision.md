---
title: "CSS-Revision"
date: 2018-10-17
layout: default
---
# Revision

Notes from Learning PHP, MYSQL Javascript and CSS

## CSS Selectors
### Type
```p {color:red;}```

### The Descendant Selector
**All Children**

```p b {color:red;}```

### The Child Selector
**Only direct children**
```p > b {color:red;}```

### The Adjacent Sibling Selector
Makes a b red but only when it directly follows something in italics.
```i + b {color:red;}```


## Combinators
###  descendant selector (space)
All p inside a div:
```
div p {
```
### child selector (>)
Immediate children only:
```
div > p{
```

### The ID Selector
```#mydiv{ font-style:italic; }```

### The Class Selector
```.myclass {margin-left:10px }  ```

#### Narrowing class scope
Only paragraphs which have the class main
```p.main {} ```


### The Universal Selector
```#boxout * p {} ```


### Selecting a Group

Separate with a comma:

```p, #idanme {} ```

### Style Sheet Selectors
1 by id or individual attribute
2 in groups by a class
3 by element tags

This is how specificicity is calculated.

### The difference between <div> and <span>
  
```<div>```
Infinite width


```<span>```
Only as wide as the text it contains

### Measurements
Ems - part of current font size

### Fonts and Typography

font-family -> the font type
font-style -> norma,italic or oblique
font-size

text-decoration 

line-height

#### Alignment
left,right,center and justify

#### Transformation
text-transform:uppercase;

#### Indenting
text-indent:20px;

### CSS Colors
color
background-color
name, hex or RGB

#### Gradients


## Positioning Elements
### static 
* default

### absolute 
* removed from the page
* just sits at the given coordinates
```
#object{
  position: absolute;
  top: 100px;
  bottom: 200px;
}
```

### relative 
* moves the object relative to the position it would take
```
#object{
  position: relative;
  top: 10px;
  bottom: 10px;
}
```

### fixed 
* moves object to location but only in current viewport
* good for docked bars
```
#object{
  position: relative;
  top: 0px;
  bottom: 0px;
}
```


## Pseudoclasses
* used to classify elements using characteristics other than their,names, attributes or content.
first-line
first-child
first-letter
```
.bigfirst:first-letter {
  font-size:400%
}

```
hover
focus
active

## Pseudoelements
* adding content rather than style to an element

```
.offer:before {content-'Special Offer';}
```

## The Box Model and Layout

### Margins

* outermost level
* collapsing - when stacked on top of each other, only the largest margin is used

### Borders

### Padding

## Advanced CSS

### The box-sizing Property
Total size is including padding and borders
```
box-sizing:border-box;
```
or Only it's content
```
box-sizing:content-box;
```






### sibling selector (+)

### general sibling selector (~)

## Display Property

https://www.w3schools.com/cssref/tryit.asp?filename=trycss_display

### None

### Inline

In the flow.

### Block

Separated out with padding above and below.

### Inline-Block

Inserted but separated out into blocks.

### Table
After each other in rows

## Box Sizing

Allow us to include the padding and border in an element's total width and height.

* Without box-sizing padding (and border) is included.

```box-sizing: border-box;``` means that padding is applied internally



