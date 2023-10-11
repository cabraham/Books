# [Designing Data-Intensive Applications: The Big Ideas Behind Reliable, Scalable, and Maintainable Systems](https://www.amazon.com/Designing-Data-Intensive-Applications-Reliable-Maintainable/dp/1449373321)


#### Terms

Data-Intensive 
: deals with amount of data, complexity of data, how fast the data is changing

Compute intensive
: CPU bound



### Applications of Data-intensive applications
- store data so that it can be found and used later (*databases*)
- remember the result of an expensive operation to speed up reads (*caches*)
- allow users to search data by keywords or filter it in various ways (*search indexes*)
- send a message to another process to be handled asynchronously (*stream processing*)
- periodically crunch a large amount of accumulated data (*batch processing*)

Prior abstractions had neat categories for different types of data-systems.  The lines are however being blurred.

Modern systems may take different data solutions and combine them to make a composite system.  Consumers of the data shouldn't have to worry about the implementation details so abstractions are built that hide the complexity behind a simpler facade.  This requires application level code which provides the linkage between the different types to provide the necessary guarantees (e.g. cache-update or invalidation so that consumers see correct results)


Three main concerns
#### *Reliability*
> The system should continue to work *correctly* even in the face of *adversity*

#### *Scalability*
> As the system grows (in data volume, traffic volume, or complexity), there should be reasonable ways of dealing with that growth

#### "Maintainability"
> Over time, many different people will work on the system (engineering and operations, both maintaing current behavior while also adapting to new use-cases).  They should be able to do so productively.

---
### Reliability

#### Terms

Fault
: things that can go wrong

Fault-tolerant or resilient
: ability to anticipate and cope with faults

Failure
: system as a whole stops providing the required service


#### Hardware Faults
Failure of hardware components due to wear over time.

These are typically addressed through redundant hardware (e.g. RAID, dual power supplies, etc)

With the advent of the cloud, using software fault-tolerance techniques, losing a VM or a container should be expected and anticipated.  The impact of such failures is much lower.

#### Software Errors
Examples: 
- Software bugs that cause every instance of an application to crash
- A runaway processes that takes away from shared resources
- A service that the system depends on becomes unresponsive or returns corrupted responses
- Cascading failures - where a small fault in one component triggers faults in other components in a chain reaction


#### Human Errors
Humans are inherently unreliable.  Most errors are caused by configuration errors made by operators.

How to address this? 
- Design systems in a way that minimizes opportunity for errors (simplified APIs and interfaces).  **Path of success**
- Decouple the places where people make the most mistakes from the places where they can cause failure.   Also provide sandbox environments.
- Test thoroughly at all levels (unit-tets, integration tests, manual tests)
- Allow for quick rollback from user-errors
- Setup detailed and clear monitoring
- Provide good training

> Reliability is one dimension.  At times, we may choose to sacrifice some reliability in order to reduce development costs (e.g. prototypes, testing unknown markets) or operational costs (for a service with very low profit margins)

---

### Scalability
Scalability
: a system's ability to cope with increased load

*Note*: Scalability is not a one-dimensional label.  

##### Questions we can ask are 
-  If the system grows in a particular way, what are our options for coping with the growth?
- How can we add computing resources to handle the additional load?

##### Describing Load
Load can be described with *load parameters*.  Examples of load parameters are: 
1. request per second to a web server
2. ratio of reads to writes in a database
3. the number of simultaneously active users in a chat room
4. the hit rate on a cache

**Latency** and **response time** are NOT the same.  

*Response time* 
: is what the client sees from end-to-end.
*this includes network delays, queueing delays, response processing and other factors*

*Latency*
: however is how long the request was *latent* (waiting to be processed).

##### Measuring response times
There is always a level of randomness and variability in each request, even if it's the same request over and over, often due to factors outside our control.  *(TCP retransmission, garbage collection, page fault, etc.)*

It's common for people to see the average response time.  This is generally not a good metric.  

It's usually better to use percentiles.  
- Take your list of response times and sort it from fastest to slowest. 
- Take the median.  
- This means half of the requests are faster than the median, and half are slowest.
- You can take this further by taking higher percentiles (95%, 99%, 99.99%).

Tail latencies
: high percentiles of response times (e.g. 99th percentile)

Sometimes you have to pay attention to the tail latencies because they can be driven by your most valued consumers (highest paying consumer may have the most data or requests).

Service level objectives (SLOs) and service level agreements (SLAs) are contracts that define the expected performance and availability of a service.

An end-user request that requires multiple back-end calls, even if run in parallel, will be bottlenecked by the slowest request.  

```mermaid
graph TD;
    User([User])
    style User fill:#0f0,stroke:#333,stroke-width:4px
    Web[WebApp]
    Backend1[Backend 1]
    Backend2[Backend 2]
    Backend3[Backend 3]
    Backend4[Backend 4]
    Backend5[Backend 5]

    User --> Web
    Web-- 92ms --> Backend1
    Web-- 101ms --> Backend2
    Web-- 57ms --> Backend3
    Web== 487ms ==> Backend4
    Web-- 133ms --> Backend5

    linkStyle 4 stroke:red;
``` 
*It takes just a single slow backend request to slow down the entire end-user request*


#### Approaches for Coping with Load

Scaling-up
: vertical scaling, moving to a more powerful machine

Scaling-out
: horizontal scaling, distributing the load across multiple smaller machines (a.k.a. *shared-nothing* architecture)

Elastic
: systems that can automatically add computing resources when they detect a load increase (whereas other systems are scaled manually)


> Horizontal scaling on a stateful system brings in lots of complexity.  This is why until recently, the common practice was to keep the state in one location and scale that up until the scalability requirements forces you to distribute.

*There is no magic architecture.*  The way one application scales can be vastly different from another.  
For example: Designing a system that handles 100,000 requests per second with requests of 1kb in size is vastly different than designing a system that handles 3 requests per minute, each 2 GB in size.  It's the same data-throughput but vastly different use-cases.


Operability
: Make it easy for operations teams to keep the system running smoothly

Simplicity
: Make it easy for new engineers to understand the system, by removing as much complexity as possible from the system.

Evolvability
: Make it easy for engineers to make changes to the system in the future, adapting it for unanticipated use cases as requirements change.  *(a.k.a. extensibility, modifiability, or plasticity)*


#### Operability: Making Life Easy for Operations

Operations teams are responsible for the following, and more: 
- monitoring the health of the system and quickly restoring service if it goes into a bad state
- tracking down the cause of problems, such as system failures or degraded performance
- keeping software and platforms up to date, including security patches
- keeping tabs on how different system affect each other, so that a problematic change can be avoided before it causes damage
- anticipating future problems and solving them before they occur
- establishing good practices and tools for deployment, configuration management, etc
- performing complex maintenance tasks, such as moving an application from one platform to another
- maintaining the security of the system as configuration changes are made
- defining processes that make operations predictable and help keep the production environment stable
- preserving the organization's knowledge about the system, even as individual people come and go

Good operability means making these routine tasks easy and allowing the operations team to focus their efforts on high-value activities.  We can do this by: 
- providing visibility into the runtime behavior with good monitoring
- providing good support for automation and integration with standard tools
- avoiding dependency on individual machines (allow machines to be taken down for maintenances while the system continues to operate uninterrupted)
- providing good documentation and an easy-to-understand operational model
- providing good default behavior, but also giving administrators the freedom to override defaults when needed
- self-healing where appropriate, but also giving admins manual control over the system state when needed
- exhibiting predictable behavior, minimizing surprises

