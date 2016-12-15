---
layout: post
title: "Git Strategy"
date: 2016-02-17
---

# Laracasts Tips

## Fixing Mistakes

* fix
* add again
* commit

**or**

* copy the original commit - the one before

1, git reset --hard hfjdshfjkds
 
 gets rid of the commit and the changes

2, git reset --soft hfjdshfjkds

gets rid of commit and code changes

**or**

* git add
* git commit --amend

This will just fix the commit, with your changes. 

**Use the present tense for messages**

"If you can describe the change you have made, then your should commit it"

"when you hit a milestone"







## Git Strategy
http://nvie.com/posts/a-successful-git-branching-model/

3 Branches

Master

Testing - checked out to test env

Develop - working


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











