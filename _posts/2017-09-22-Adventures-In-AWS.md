---
layout: default
title: "AWS"
date: 2017-09-22
---

# Adventures in AWS

I am considering taking some AWS certification. This is documenting that journey.





# A Cloud Guru

## AWS Tech Essentials

### Introduction ###

90% of the market.
AWS certificates are the most popular.
Number of certs makes you a partner.

Associate Exams.
3 Entry Level
2 Professional Tier
3 Speciality

Developer Associate is the easiset. 

### AWS - The History So Far ###

AWS - no cost for startups to build infratstructure.
Originally called SQS - 2004.
2013 - Certification was launched.

* 2016 re:Invent talk on YouTube.*

* Should subscribe to A Cloud Guru on youTube *
* Jeff Barrs Blogg *

###  10,000 Foot Overview 1 ###

What do you need for the * Certified Solutions Architect Associate Exam *.

Messaging
Desktop and App Streaming
Security and Identity
Management Tools
Storage
Databases
Networking and Content Delivery
Compute
AWS Global Infrastructure

A Region has Availability Zones. 
Region is a geographical area.
2 or more Availability Zones (Data Centres) in each region.
Edge Locations are CDN delivery End Points for CloudFront. - for caching large media files.
Lots more Edge locations that Regions - over 66
Some regions may not have certain sevices.

* VPC  Important *
Virtual Private Cloud - Virtual Data Centres in each Regions.
How to build from memory.

* Route 53 - 53 is the DNS Port*
DNS Servers - resolve URL to an IP address.

* Cloud Front *
Caching videos etc, storage.

* Direct Connect *
For connecting office to data centres over a dedicated line.

* EC2 - Elastic Compute Cloud *
Just VMs in a cloud

* EC2 Container Services  *
Supports Docker containers.
Not in the exam.

* Elastic Beanstalk *
If you dont know AWS you can just use EB and it will do the provisioning.
Quite a lot in the developer exam.

* Lambda *
Serverless 
Upload code and it will respond to events.
eg speaking to Alexa is speaking to Lambda
Not yet in the exam but certain to change.

* Lightsail *
Out of the box cloud - Wordpress.
No need for AWS skills.


###  10,000 Foot Overview 2 ###

#### Storage 

* S3 - Simple Storage Service *
Objects
Lots in the exams.
Virtual disk in the cloud for storing files.
Not somewhere to install code or db.
Dropbox was one of the first to use s3

* Glacier *
Place to archive files.
Regulatory bodies may require that files are kept. Low cost, not immediate access.

* EFS Elastic File Service *
Files can be shared - could install apps and databases

* Storage Gateway * 
A way of connecting S3 to on premise data centre, usually an onsite VM.

#### Datatabse

* RDS - Relational Database Sevices *
All types of db and Aurora.

* Dynamo DB *
Non relational databases. No SQL. Really scaleable.
Lots in developer exam.

* Redshift *
Data warehousing - big data.
Copy data here, then run big queries.

* Elasticcache *
For caching data in the cloud.
Eg vacuum cleaner is best seller, so cache this data.

#### Migration Services

* Snowball *
Started as import/export using disks. 
This is how to do this at the Enterprise level - a briefcase sized appliance which you load and send to Amazon.

Snowball Edge also has compute capacity, can be taken on premis.

* DMS - Database Migration Services*

Can move from different database types eg Oracle to Aurora feud.

* Server Migration Services *

For migrating VMs from on premise to AWS.

#### Analytics 

* Athena *

Allows you to execute SQL queries against S3 files. Like turning flat files into a db.

* EMR - Elastic Map Reduce *
Used to process large amounts of data. Hadoop, Apache Spark. 

* Cloud Search - Elastic Search *
Used to create search capabilities for websites

* Kinesis *
Streaming and analysing real-time data.
Financial transactions, social media streams. 

* Data Pipeline *
eg. Move data from s3 into dynamodb 

* Quick Sight *
Business Analytics Tool


###  10,000 Foot Overview 3 ###

#### Security and Identity 

Every single exam - fundamental component.

* Inspector *
Inspects VMs and reports.

* Certificate Manager *
SSL certificates

* Directory Service *
Connect AD to AWS.

* WAF *
Web Application Firewalls
CSRF
SQL Injection.

* Artifacts *
Compliance Documentation

#### Management Tools 

* CloudWatch *

* Cloud Formation *
Probably going to use.
Turn infrastructure into code.
A document which describes your environment.

* Cloud Trail *
Auditing.

* Opsworks *

* Config *

* Service Catalog *

* Trusted Advisor *
Tips on cost/performance.

#### Application Services

* Step Function *
Way to visualise what is going on.

* SWF - Simple Workflow *

* API Gateway *

A door for securing

* AppStream *

A way of streaming desktop applications to users.

* Elastic Transcoder *

Formats videos for all devices.


#### Developer Tools

* CodeCommit *

* CodeBuild *

For compiling code 

* CodeDeploy * 

* CodePipeline *

Not in the Developer exams yet!

#### Mobile Services

* Mobile Hub *

* Cognito * 

* Device Farm * 
 Testing applications.
 
 * Mobile Analytics *
 
 * Pinpoint *
 
 #### Business Productivity
 
 Mail and docs. 

### iOT

#### Desktop and App Streaming

* Workspaces *
OS in the cloud.

AppStream 2.0 

#### AI

###  10,000 Foot Overview 4 ###

* Alexa *

* Polly *
Text to voice

* Machine Learning *

Predict data based 

* Rekognition * 

Analyse images.

#### Messaging

* SNS *

* SQS *

Decoupling queue system.

* SES *

Email





* Look At *

CloudWatch LOgs


# Links

https://www.airpair.com/aws/posts/building-a-scalable-web-app-on-amazon-web-services-p1

https://wblinks.com/notes/aws-tips-i-wish-id-known-before-i-started/

https://www.youtube.com/watch?v=ccojvcQq858


# Thoughts

How to Deploy

Use Redis for cache?

Code on AMI or pulled?
How do we get he code on the box

Read Code Deploy

Centralised logging

Don't SSH






















