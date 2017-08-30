---
layout: default
title: "Git Strategy"
date: 2016-02-17
---

# Laracasts Tips


## Fixing Mistakes

### If deployed

* fix
* add again
* commit

**or**

* copy the original commit - the one before

1, git reset --hard hfjdshfjkds
 
 gets rid of the commit and the changes
 reset everything to the way the code was
 go back to the original commit

2, git reset --soft hfjdshfjkds
reset the commit but keeps local changes (uncommited)



**or the correct way**

* git add
* git commit --amend

This will just fix the commit, with your changes. 

**Use the present tense for messages**

"If you can describe the change you have made, then your should commit it"

"when you hit a milestone"

git show will show the changes.


## Workflow
```
git add .
git commit

```

## Branching

* Separate Timeline

### Bugfix

Already working on a new feature - all over the place
New feature should be a new branch


git checkout a file will discard changes
One branch per bugfix
An easy fix could just be done on master

**Finished feature**
- checkout master
- merge feature

This created a commit

### Conflicts

```git branch -v```


If git merge reports conflicts.
Git status reports both modified
When the file is viewed:

<<<<< HEAD -- current branch


This is Laravel

======

Welcome to Laravel

>>>>>>> feature-branchg


Fix this manually, then .add the file.

Then ```git commit``` the resolved file.

### Git Aliases
git config --global alias.s status

Adds to the bottom of the .gitconfig file
**or**
the .bashrc



## Stash Away Changes

Not ready for a commit before swapping branch.
- could do a WIP commit, then a git reset soft
soft does not touch local modified files, hard will trash them all.


```git stash`` saves working directory
``` git stash list```
```git stash pop``` takes them off the list
```git stash apply```
you can have multiple stashes


## Pusing to GitHub

git push -u

## Rebasing
```git merge
git rebase <branch>```

git log --oneline --graph

git rebase master


## Interactive Rebasing








# Git Strategy


http://nvie.com/posts/a-successful-git-branching-model/

3 Branches

Master

Testing - checked out to test env

Develop - working


## Feature brnaches come from develop.

```

git checkout -b myfeature develop

```
## Release branches




## Finished features merged back in.
```
git checkout develop
git merge --no--ff myfeature (merges with a new commit object)
git branch -d myfeature
git push origin develop

```









# Pushing changes to master

1. git checkout master
2. git merge --no-ff develop    (This merges into thr current branch!)
3. git push origin master
  
# Delete branch

git branch -d crazy-experiment


# Sensible view of history

git log -p -2


git rm -f .idea/workspace.xml

# Fixing things

## Forced push:
http://stackoverflow.com/questions/20939648/issue-pushing-new-code-in-github
git push -f origin master


## Force Git to overwrite local files on pull
http://stackoverflow.com/questions/1125968/force-git-to-overwrite-local-files-on-pull
	
Important: If you have any local changes, they will be lost. With or without --hard option, any local commits that haven't been pushed will be lost.[*]
If you have any files that are not tracked by Git (e.g. uploaded user content), these files will not be affected.

I think this is the right way:

git fetch --all
git reset --hard origin/master


##Removing tracked files
http://source.kohlerville.com/2009/02/untrack-files-in-git/

git update-index --assume-unchanged [path]











