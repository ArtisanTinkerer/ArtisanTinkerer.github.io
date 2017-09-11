---
layout: default
title: "Using Fetch and Merge instead of Pull"
date: 2017-09-11
---

[https://www.atlassian.com/git/tutorials/syncing#git-fetch](https://www.atlassian.com/git/tutorials/syncing#git-fetch)


I want more control when putting my code live, so I am going to start using GIT Fetch instead of Pull.

To download all the branches:

```
git fetch origin
```

To see the changes:

```
git log --oneline master..origin/master
```

Now we can merge with:

```
git merge origin/master

```

