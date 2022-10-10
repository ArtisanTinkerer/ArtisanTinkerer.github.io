---
title: "Laracon Summer 2022"
date: 2022-09-26
layout: default
---

https://www.youtube.com/watch?v=f4QShF42c6E&ab_channel=LaraconOnline

# Matt Stauffer - Abstracting too early
YAGNI
We are bad at predicting the future.
* Welcome changing requirements, even late in development.
* When faced with multiple paths, choose the simplest.

Sandi Metx - refer duplication over the wrong abstraction

WET - write everything twice
* ony extract when you get to 3

## Part 3
### The Repostory Pattern
4:14
### Microservices
https://grugbrain.dev/
* only when really need one piece really needs to scale differently
* one piece of app could take down the system
* demonstrated need for different language

# Taylor
artisan about
artisan db:show
artisan db:monitor
10:01

# Aaron Francis 
Database Performance for Application Developers
## Schemas
* smallest colum types possible 
* simplest column type 
## Indexes
* B-tree or B-tree+
* separate data structure
* a copy of part of the data
* has a pointer back to the row (primary key)
* as many as you need
* as few as you can get away with
* consider the whole query, not just the where, grouping and ordering
instead of single column indexes, use composite indexes
```
$table->index(['first_name','last_name','birthday']);
```
* **left to right, no skipping** - stops at the first range (<> LIKE)
* where ('birthday') won't use index
* where ('first_name') will work
* index won't be used after you use a range (like) or skip a column
* use explain to see what key is used
* look at key_len - bytes used by key
* covering indexes -> the needs of the entire query
* indexes will not be used if you use functione like year(created_at) 
* select only what you need (maybe)
* subqueries are not bad
* 
06:27:39

## Queries
06:34 



