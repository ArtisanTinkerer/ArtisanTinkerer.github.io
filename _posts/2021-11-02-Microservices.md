---
title: "Microservices"
date: 2021-11-02
layout: default
---

https://laracasts.com/discuss/channels/general-discussion/microservices-2


https://gotopia.tech/bookclub/episodes/moving-to-microservices-with-sam-newman-and-martin-fowler

Independent deployability
Hiding information
Small interface

Why Independent Development?:

Easier to limit impact for each release.
As team size increases it gets harder to coordinate a deployment (people).

Look at books?

https://www.youtube.com/watch?v=xexLvQqAhiA&list=PLMdXHJK-lGoAepv_7mvIEuafrtO6N-3SZ&index=8


# Building Microservices - Sam Newman

## Part 1

###1 What are Microservices?
* Microservices are independently releasable services that are modeled around a busi‐
ness domain.
* They are a type of service-orientated architecture.
* Independent deployability.
* Treated as a black box.
* Technology agnostic.
* Each microservice encapsulates it's own db.
* Changes inside a microservice should not affect an upstream consumer.



* Microservices is a particular approach to SOA
* To ensure independent deployability microservices must be loosely coupled
* Stable interfaces
* Avoid shared databases - should get data from other ms
* a microservice should be kept to the size at which it can be easily understood.
* incremental migration to ms - turn up the dial gradually



* Distributed monolith if all services are deployed together.
* Microservice architecture gives concrete ownership boundaries
* Monolith is sensible default choice
* Log aggregation - use a single id for for related set of service calls


* how to handle network failure?
* can scale services which need it

* gradually increase use of new Technology



pg17





###2 How to Model Microservices.

###3 Spitting the Monolith.

###4 Microservice Communication Style

## Part 2

###5 Implementing Microservice Communication

###6 Workflow

###7 Build

###8 Deployment

###9 Testing

###10 From Monitoring to Observability

###11 Security

###12 Resilience

###13 Scaling



## Part 3 People

###14 User Interfaces

###15 Organizational Structures

###16 The Evolutionary Architect

Bringing it all together.
