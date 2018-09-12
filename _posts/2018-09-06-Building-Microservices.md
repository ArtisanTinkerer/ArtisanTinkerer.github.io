
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
 
 
 # Sam Newman - Building Microservices
 
 ## Loose Coupling
 * Change to one should not require change to another.
 * A loosely coupled service knows as little as it needs to about the services with thich it collaborates.
 
 ## Synchronous Versus Asynchronous
 * Events versus request/response (could use callbacks)
 
 ###Two styles of architecture:
 
 #### Orchestration
 Central brain guides and drives the process.
 
 #### Choreography
 Inform each part of the system of it's job and let it work out the details (finding their way and reacting to others around them.
 ).
 
 
 Example: uses **Orchestration** and request/response, customer service is the brain and can therefore track where a customer is in the process.
 * Request/response means that we know if each stage has worked. 
 * Downside is that the brain can become too much of a central governing authority.
 
 With **choreographed** approach
 * Events from each stage in the process are listened for by other services.
 * Significantly more decoupled.
 
 ** I strongly prefer aiming for a choreographed
system, where each service is smart enough to understand its role in the whole dance. **

* Synchronous calls are simpler, and we get to know if things worked straightaway.

**Callbacks?**

## RPC

## REST

### Hypermedia As the Engine of Application State (HATEOAS)
* links to other pieces of content in a variety of formats
* the client looks for and navigates links to find what it needs.
*MB so, the JSON contains the links for the actions

 
 ### Implementing Asynchronous Event-Based Collaboration
 
 ### Complexities of Asynchronous Architectures
 
 * Maximum retries for jobs
 * and strongly consider the use of correlation IDs, which allow you to trace requests across process
 
 ### DRY and code reuse
 * Do not share code between services, if one service needs changing, all will be affected.
 
 ### Access by reference
 
 * Get to see what the customer looked like, when the request was made.
 * May have changed after.
 * **Could send URI for customer and order and look them up when they are needed.**
 * but be very wary of passing around data in requests when you don’t know its freshness.
 
 ### Versioning
 
 * Don't make breaking changes.
 * Limit fields sent - refer to by name.
 * Semantic versioning MAJOR.MINOR.PATCH
 * MAJOR - backward incompatability changes have been made
 * MINOR - new functionality should be backwards compatible
 * PATCH - bug fixes to existing functionality
 
 * Coexist different endpoints
 * Use multiple concurrent serice versions
 
 
 zzzz
 
 * Backends for Frontends - API Gateway
 
 
 ### Summary
 
 Prefer choreography over orchestration.
 
 
 ## Splitting the Monolith
 
 ### Example: Shared Static Data
 Country codes used by several services, options:
 
 1, Db with them in for each service - data consistency challenge
 2, Treat static data as code - property file or enum - same consistency challenge
 3, Static data in a service.
 **Page 160**
 
 
 ### Transactional Boundaries
 * these events either all happen together, or none of them happen.
 
 * Eventual consistency - accept that the system will get itself into a consistent
state at some point in the future.
 
 #### What to do?
 Eventual consistency is easier to build.
 
 ### Reporting
 * Reporting DB, keeps load from primary DB.
 1, reporting system pulls data/
 2, Data Pump - pull data fom db, then to reporting db (another app is now hitting main db)
 3, Event Data Pump - microservice emits events - subscriber pumps data into reporting db.
 4, 
 
 ### Cost of Change
 * CRC cards - name, responsibilities - who it communicates with
 
 ## Chapter 6 Deployment
 ## Chapter 7 Testing
 Mocking or stubbing - maybe my portal - azure tests are wrong (end-to-end tests?)
 * Flaky tests
 
 ## Chapter 8 Monitoring
 ## Chapter 9 Security
 ## Chapter 10 Conway's Law and System Design
 * Internal Open Source
 ## Chapter 11 Microservices at Scale
 
 Yawn
 
 
 
 
 
 
 
 
 
 Pakt press books
 
 
 
 
 
