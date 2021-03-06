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


Dev machine has AppSpec file (application specific).
Deploys to a Deployment Group.
* You can Auto Deploy to Auto Scaling Group *

### Blue/green deployment

Just creating a parallel environment before switching.

## CodeDeploy with Auto Scaling

http://docs.aws.amazon.com/codedeploy/latest/userguide/integrations-aws-auto-scaling.html

"When new Amazon EC2 instances are launched as part of an Auto Scaling group, AWS CodeDeploy can deploy your revisions to the new instances automatically"

https://aws.amazon.com/blogs/devops/under-the-hood-aws-codedeploy-and-auto-scaling-integration/

### Deep Dive 
https://www.youtube.com/watch?v=aX54mhZbN58



## Dev Ops
[http://docs.aws.amazon.com/devops/latest/gsg/setup-access.html](http://docs.aws.amazon.com/devops/latest/gsg/setup-access.html)

Looking a this one:

http://docs.aws.amazon.com/autoscaling/latest/userguide/as-register-lbs-with-asg.html



# Tutorial Linux

## Video 1

Create EC2 instance

## Video 2 

Stop instance.
Auto scaling group.

Deploying code to an auto scaling group.
Launch Configuration - bash script here could do a git pull?



## Links

[https://deliciousbrains.com/scaling-laravel-aws-elastic-beanstalk-part-1-setting-up-laravel/](https://deliciousbrains.com/scaling-laravel-aws-elastic-beanstalk-part-1-setting-up-laravel/)


## Where do we start?

Code Deploy

https://www.youtube.com/watch?v=qZa5JXmsWZs

Cloud Formation

## Application Templates

http://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/sample-templates-appframeworks-us-west-2.html

## Maybe just do this
Tutorial: Set Up a Scaled and Load-Balanced Application

http://docs.aws.amazon.com/autoscaling/latest/userguide/as-register-lbs-with-asg.html

http://docs.aws.amazon.com/autoscaling/latest/userguide/GettingStartedTutorial.html

# The Plan

Don't touch the current box.

1, Create a new box.
2, Use this to make an AMI.
3, Use this to setup a load balanced auto-scaling group.


# Box build


## To Do
Sessions
Logs - central AWS thing?
Code Deploy





# Architect Cert?

## AWS Technical Essentials 

https://acloud.guru/learn/aws-technical-essentials


## AWS Certified Solutions Architect - Associate

https://acloud.guru/learn/aws-certified-solutions-architect-associate

http://cantrill.io/certification/aws/2016/03/27/how-to-pass-AWS-certifications.html
Udemy - Ryan

Ryan Kroonenburg


Google Play app
Sorry forgot to tell you guys what it was:
https://play.google.com/store/apps/details?id=com.ionicframework.awsquiz543924

http://www.cardinalpath.com/autoscaling-your-website-with-amazon-web-services-part-1/




Immutable - Mutable
https://aws.amazon.com/answers/configuration-management/aws-ami-design/

https://www.quora.com/Whats-the-best-way-to-push-code-to-production-on-multiple-EC2-instances

set -e in Bash Scripts

https://3e8.io/2016/lessons-learned-using-aws-codedeploy-with-auto-scaling-groups/


# How to handle database migrations 

The biggest 


# What can I do on Free Tier?
https://www.infoworld.com/article/2613845/cloud-computing/free-amazon-web-services----and-how-to-make-the-most-of-them.html






# Big questions
How to pull the code
How to run database migrations - nothing to migrate?









