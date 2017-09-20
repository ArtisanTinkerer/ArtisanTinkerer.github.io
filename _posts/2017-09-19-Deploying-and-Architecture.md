---
layout: default
title: "Deploying and Architecture"
date: 2017-09-19
---



Just trying to document how we move from 1 live server to a load balanced horizontally scaled architecture.

## Terminology

IAM - security
Route 53 - DNS
Key pairs - belong to an IAM user and are SSH keys.  .pem
Cloudfront - serves assets

Elastic beanstalk - for deploying and scaling

CodeDeploy - automates deployment

EC2 instance - virtual server (Elastic Compute Cloud)

EBS - Block Storage

S3 - File Storage

## EC2

Just for spinning up VMs

### Security on Virtual Private Cloud
Can also connect to on premise using hardware

## Elastic Beanstalk

Deploys, Manages and Scales.

Automatically scales.

You can tweak after.

## Cloud Formation

To create and manage AWS resources.

### Provisions based on a template (JSON file). 
Defines what resources are required to run the application.


### Or pre-built stack. 

Upload temmplate.

## Load Balancing

## Code Deploy

Coordinates deployment and updates across a fleet.


## Dev Ops
[http://docs.aws.amazon.com/devops/latest/gsg/setup-access.html](http://docs.aws.amazon.com/devops/latest/gsg/setup-access.html)

Looking a this one:

http://docs.aws.amazon.com/autoscaling/latest/userguide/as-register-lbs-with-asg.html




## Links

[https://deliciousbrains.com/scaling-laravel-aws-elastic-beanstalk-part-1-setting-up-laravel/](https://deliciousbrains.com/scaling-laravel-aws-elastic-beanstalk-part-1-setting-up-laravel/)


## Where do we start?

Code Deploy

Cloud Formation








