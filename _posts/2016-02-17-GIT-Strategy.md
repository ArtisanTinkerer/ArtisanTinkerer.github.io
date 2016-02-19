---
layout: post
title: "Git Strategy"
date: 2016-02-17
---


Git Strategy
http://nvie.com/posts/a-successful-git-branching-model/

3 Branches

Master

Testing - checked out to test env

Develop - working


# Pushing changes to master

1. git checkout master
2. git merge --no--ff develop    (This merges into thr current branch!)
3. git push origin master
  
# Delete branch

git branch -d crazy-experiment


# Sensible view of history

git log -p -2


git rm -f .idea/workspace.xml


