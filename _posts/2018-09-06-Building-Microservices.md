
---
title: "Building-Microservices"
date: 2018-09-07
layout: default
---

https://martinfowler.com/articles/microservices.html

## Alternative to monolith
* change cycles tied together
* cannot scale parts, must scale entirety

## Microservices
* suites of services
* managed by different teams
 
 * using services as components
 * independently depolyable
 * services organised around business capability
 
 ### Smart endpoints and dumb pipes
 

 ### Decentralized Data Management
 
 * conceptual model of the world different between systems.
 * microservices prefer letting each service manage it's own DB
 * managing updates - transactions if across multiple resources
 * microservice architectures emphasize transactionless coordination between services
 * businesses handle a degree of inconsistency 
 
 ### Infrastructure Automation
 
 ### Design for failure
 * applications need to be designed so that they can tolerate failure of services
 * real time monitoring
 
 ### Evolutionary Design
 
 
 
