---
layout: default
title: "Clone Laravel Project"
date: 2016-02-16
---


# How can I create a  test copy of my project?

1. Do a git clone.
git clone https://git-codecommit.us-east-1.amazonaws.com/v1/repos/glostselection selectionTestEnv

2. create the httpd entry /etc/httpd/conf

3. composer install

4. copy the .env 





# The MySQL Stuff
create database live_lookup;

GRANT SELECT, INSERT, DELETE, CREATE,AlTER ON live_lookup.* username IDENTIFIED BY 'blahblaf'

GRANT SELECT, INSERT, DELETE, CREATE,AlTER ON live_reporting.* to fdsafdsaf@'%' IDENTIFIED BY 'fdsaf'

php artisan migrate

# The Linux Stuff

sudo chown -R apache:www utils

# The GIT stuff
based on http://nvie.com/posts/a-successful-git-branching-model/

Develop Branch
-work on this, then merge to master - tag with a release (git hook)


Master Branch







