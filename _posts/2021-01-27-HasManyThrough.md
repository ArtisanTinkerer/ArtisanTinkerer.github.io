---
title: "Has Many Through"
date: 2021-01-27
layout: default
---





users
id
affiliation_id

posts
id
user_id


affiliations


Add HasManyThrough  (Posts, Users) to Affiliation

Basically you get a:

SELECT * from posts p
  INNER JOIN users u  on u.id = posts.user_id
  WHERE affiliation_id = ?

  Getting posts through users.
  Where a user has many posts
  affiliation has many users
