### action

A database session parameter that is set by an application to identify the action associated with a database request.

**Parent topic:** Glossary

### affinity

The word 'affinity' is used to describe any strategy that is expected to increase the probability that a work request finds the required data cached in the instance to which the work request is routed.

**Parent topic:** Glossary

### aggregation

Aggregation is the process of taking a collection of measurements, and combining them to produce an aggregate measure. For example, counting all the work requests that are completed by a given server in a given Performance Class is a form of aggregation. Totaling the CPU time used by all the work requests in a given Performance Class handled by a particular server during a time interval is another form of aggregation.

**Parent topic:** Glossary

### application

An application is software that runs on a system and provides one or more services to a user or a group of users. Oracle Talent Management, Oracle ERP, Oracle Asset Lifecycle Management, PeopleSoft Campus Solutions, and Oracle Manufacturing are all examples of applications.

An application usually consists of multiple components; there might be a database component, a J2EE component, a client PC component, a batch component, a web component, a Web Services component, and so on.

**Parent topic:** Glossary

### Automatic Provisioning

Automatic Provisioning attempts to automate, as much as possible, the activities involved in re-tasking a piece of hardware. For example, taking a piece of hardware that has been running with one operating system and one set of application components, and re-deploying the hardware with a different operating system and a different set of application components.

**Parent topic:** Glossary

### average response time

The average of the response times for all work requests for a Performance Class for a given time period, specified in seconds.

**Parent topic:** Glossary

### bottleneck

A component or resource that limits the performance of an application or an entire system.

**Parent topic:** Glossary

### capacity planning

Capacity planning is the act of determining the amount and type of hardware needed to service projected peak user loads. Capacity planning is often done as part of a larger capital equipment budgeting cycle, and usually involves making load projections months into the future.

**Parent topic:** Glossary

### classifiers

Value matching rules that are applied to attributes of the work request to map work requests to Performance Classes.

**Parent topic:** Glossary

### closed workload

The amount of work performed in a system in which a fixed number of users interact with the application and each of these users issues a succession of requests. A new request from a user is triggered only after the completion of a previous request by the same user. A user submits a request, waits for the response of that request, thinks for a certain time and then sends a new request. The average time elapsed between the response from a previous request and the submission of a new request by the same user is called the "think time".

A closed workload is also referred to as a session-based workload.

**Parent topic:** Glossary

### clusterware

Any software that enables groups, or clusters, of connected computers to operate or be controlled as a unit.

**Parent topic:** Glossary

### conditioned data

Conditioned data is created from raw data in a post-processing step of some kind. Taking averages, removing outliers, filtering, and parameter estimation procedures are all examples of the kind of post-processing that can be used to create conditioned data from raw data.

**Parent topic:** Glossary

### database services

A database service is a user-created service that is managed by Oracle Clusterware and serves as a database session connection point. A database service can be offered on one or more Oracle RAC instances, and managed on a for-instance basis (for starting and stopping the service).

**Parent topic:** Glossary

### demand

Demand is a measure of the amount of work being presented to the system and is usually measured in work requests or requests per second.

**Parent topic:** Glossary

### elapsed time

An elapsed time measurement (also known as a wall clock time measurement) is a measurement of a single, contiguous time interval. The elapsed time interval begins at some time `t1` and ends at another time `t2`, where both times are read from the same clock. The elapsed time measurement is the value of (`t2` - `t1`).

**Parent topic:** Glossary

### end-to-end response time

The expression end-to-end response time includes all time spent and all work done from the time a user request is received (for example, from clicking the Submit button in a browser), until the response is sent back to the user in its entirety. End-to-end response time includes time spent in application servers, Oracle Database, Oracle Automatic Storage Management, and traversing the internal networks of the data center.

**Parent topic:** Glossary

### entry point

The entry point is the initial point of contact between a work request and the Oracle Database QoS Management system. Work requests are initially classified and tagged at their entry point.

**Parent topic:** Glossary

### fair share scheduling

Fair share scheduling attempts to fairly allocate a resource such as a CPU among a collection of users, ensuring that each user gets a specified share of the available resource. Lottery based scheduling is one kind of fair share scheduling.

**Parent topic:** Glossary

### Free pool

A server pool that contains servers that are not assigned to any other server pool.

**Parent topic:** Glossary

### headroom

When a Performance Class is meeting its Performance Objectives, headroom refers to the difference between the actual response times and the required response times, or the surplus in performance.

**Parent topic:** Glossary

### layer

Layer and tier are synonymous.

**Parent topic:** Glossary

### Layer Active Time

Layer Active Time is the cumulative time that a work request is actively doing work at a layer, excluding time spent waiting on layers below. Layer Active Time includes time spent executing at the layer, and time spent waiting for layer local resources, such as the CPU, locally connected disks, memory, and so on.

**Parent topic:** Glossary

### Layer Response Time

Layer Response Time is the elapsed time for a work request to be completely handled by a specific layer. The layer response time includes the time spent executing the work request, and the time spent waiting for local and remote resources and servers.

**Parent topic:** Glossary

### layer visit

Often, a single work request from an end user (for example, clicking a link in a browser) causes several requests to arrive at various layers of the system. Each time a request is handled by a layer is called a layer visit.

**Parent topic:** Glossary

### load shedding

Load shedding refers to the act of rejecting some work requests, so that other work requests can complete successfully. Rejecting requests gracefully might require modifications to your applications. For example, you might want the end user to see a customized rejection page. Alternatively, you might want to store information from the work request so you can reply to the requester at a later time.

**Parent topic:** Glossary

### lottery based scheduling

Lottery based scheduling is a scheduling algorithm that uses random numbers to apportion resources (such as a CPU) among a collection of users, according to a pre-set distribution.

**Parent topic:** Glossary

### memory pressure

A state indicating that there is a limited amount of available memory on a server.

**Parent topic:** Glossary

### metric

A metric is something that can be measured.

**Parent topic:** Glossary

### module

Module is the database session parameter that is set by an application, generally to identify the application module making the database request.

**Parent topic:** Glossary

### open workload

Work performed in a system in which new work requests to an application come from outside the system being managed. The work requests are independent of each other and the work request arrival rate is not influenced by the response time for previous requests, or the number of requests that have already arrived and are being processed. The number of work requests that the system might be asked to execute at any given time can range from zero to infinity. The system's resources or servers perform various activities to process a work request and the work request leaves the system when processing is complete.

Open workloads are also referred to as request-based workloads.

**Parent topic:** Glossary

### Oracle Grid Infrastructure for a cluster

A term assigned to the software stack comprising Oracle's generic Clusterware, Oracle Automatic Storage Management (Oracle ASM), Oracle RAC agents, and the Oracle RAC database management infrastructure layer.

**Parent topic:** Glossary

### Oracle Database Resource Manager

Oracle Database Resource Manager is a software component available with the Oracle Database. Oracle Database Resource Manager enables an administrator to establish Resource Plans that control how various resources (such as the CPU) are allocated to consumer groups, which are collections of work requests. The intent is very similar to Oracle Database QoS Management's Performance Class.

**Parent topic:** Glossary

### performance bottleneck

Oracle Database QoS Management attempts to identify performance bottlenecks due to Performance Classes waiting too long for required resources, such as CPU, Global Cache, or I/O.

**Parent topic:** Glossary

### Performance Class

A Performance Class is a group of related work requests. Performance Objectives are written for a Performance Class. All work requests that are grouped into a particular Performance Class have the same performance objective.

**Parent topic:** Glossary

### Performance Class ranks

The Performance Class rank represents the business criticalness of each Performance Class in a set of Performance Objectives that are in effect at a given time. When there are not enough resources available to service all applicable Performance Classes at the same time, Oracle Database QoS Management works to meet the Performance Objectives for the Performance Classes that are highest ranked at the expense of Performance Classes with a lesser rank. For example, Performance Classes with an rank of Lowest are sacrificed if necessary to ensure that Performance Classes of higher rank (Highest, High, Medium and Low) continue to meet their Performance Objectives.

**Parent topic:** Glossary

### performance objectives

Performance objectives refers to business level objectives for the system. A performance objective includes both Performance Objectives and availability objectives.

**Parent topic:** Glossary

### Performance Objectives

A Performance Objective defines a level of performance that is optimal for business purposes for a given Performance Class. For a particular Performance Class, a Performance Objective specifies the target average response time for that workload.

In high load situations, work of lower business criticalness can be deliberately starved for resources by the Oracle Database QoS Management system so that more important work can meet its Performance Objectives; in this circumstance the user might receive a "Server Busy" message instead of just experiencing very poor response times.

**Parent topic:** Glossary

### Performance Policy

A Performance Policy is a collection of Performance Objectives and Performance Class ranks that are intended to be in force at the same time. A Performance Policy must include at least one Performance Objective and Performance Class rank for each Performance Class, unless the Performance Class is marked Measure-Only. A Performance Policy optionally includes server pool directive overrides to set a baseline configuration of server resources for the time period in which the policy is active.

**Parent topic:** Glossary

### Performance Satisfaction Metric

A normalized numeric value that indicates how well a particular Performance Objective is being met, and which enables Oracle Database QoS Management to compare the performance of the system for widely differing Performance Objectives.

**Parent topic:** Glossary

### Policy Set

A Policy Set is a wizard-generated XML document that governs the operation of Oracle Database QoS Management. A Policy Set specifies server pools and their hosted Performance Classes, the collection of Performance Policies that specify the Performance Objectives for each Performance Class, and the server pool directive overrides for each Performance Policy.

**Parent topic:** Glossary

### program name

Program name is a database session attribute set by an application that is generally used to identify the program making the database request.

**Parent topic:** Glossary

### raw data

Raw data is data that has not been post-processed in any way. Counts, totals, and individual sample values are examples of raw data.

**Parent topic:** Glossary

### resource

A resource is a shared item that has limited quantity that is required to process a request. For example, CPU Time, threads, memory, I/O devices, slots in queues, network bandwidth, and temp space are all resources. Servers typically provide resources.

**Parent topic:** Glossary

### resource allocation control

A resource allocation control (also informally known as a knob) is a parameter, or collection of parameters, to a resource allocation mechanism. Examples of a resource allocation control include:

- A Consumer Group for Oracle Database Resource Manager

- The number of servers in a server pool

**Parent topic:** Glossary

### resource allocation mechanism

A resource allocation mechanism is something that gives an external entity such as a person or Oracle Database QoS Management the ability to control how some collection of resources are allocated. Oracle Database Resource Manager is an example of a Resource Allocation Mechanism.

**Parent topic:** Glossary

### resource metric

A resource metric is a metric that can be measured for any resource. Examples include Resource Usage Time and Resource Wait Time.

**Parent topic:** Glossary

### Resource Usage Time

Resource usage time is the cumulative time that a work request had exclusive use of a resource.

**Parent topic:** Glossary

### resource use

Resource use is a measurement that accumulates a specified set of elapsed time measurements into a single number. For example, a measurement of the CPU time spent on a given work request on a given server is a resource measurement: the specified work request uses the CPU for many separate intervals of time as the work request is processed.

**Parent topic:** Glossary

### resource wait time

Resource wait time is the cumulative time spent waiting for a resource by a work request that is ready to use that resource.

**Parent topic:** Glossary

### response time

The time between the server receiving a transaction request and sending out a response after committing or aborting the transaction.

**Parent topic:** Glossary

### rogue work

A work request that uses significantly more resources than expected; for example, the work request might be in a non-terminating loop. In some systems, facilities are provided to stop or re-prioritize rogue work.

**Parent topic:** Glossary

### routing

Routing is the act of choosing the path that a work request takes through the system. This includes all choices made when picking an entity in another tier of the system to which to pass a work request.

**Parent topic:** Glossary

### server

A server is a shared computer, typically not dedicated to a single user. A server can be as simple as a single CPU blade, or as complex as a large server with many CPUs sharing memory.

**Parent topic:** Glossary

### server pools

A server pool is a collection of servers created by the cluster administrator using either Enterprise Manager Cloud Control or the Server Control (SRVCTL) utility. Server pools are contained within tiers; each service is assigned to run in a specific server pool.

**Parent topic:** Glossary

### server pool directive overrides

High availability guidelines for the cluster administrator server to keep the cluster highly available.

**Parent topic:** Glossary

### server pool importance

A number from 0 to 1000 (0 being least important) that ranks a server pool among all other server pools in a cluster.

**Parent topic:** Glossary

### server pool maximum

The maximum number of servers that the server pool should contain.

**Parent topic:** Glossary

### server pool minimum

The minimum number of servers that the server pool should contain.

**Parent topic:** Glossary

### service

A service provides a well-recognized value to a user (client) or group of users. A service is provided to an application, and runs on a system. For example, CollabSuite provides a set of services such as Files, Calendar, Web Conferences, and so on. See also database services.

Operational management decisions, such as the hours of operation, capacity planning, provisioning, placement, and so on, are made on a service-by-service basis.

**Parent topic:** Glossary

### service placement

The activities of starting, stopping, or relocating a database service

**Parent topic:** Glossary

### singleton services

Services within a server pool that has a size of one.

**Parent topic:** Glossary

### system

A shared collection of servers and their associated infrastructure (networks, firewalls, storage systems, and so on) over which a workload management instance operates.

**Parent topic:** Glossary

### system metric

System metrics are metrics that help us to connect the things that are happening at the different layers. They provide a framework within which the rest of the analysis can be done. Examples include request counts, Layer Response Time, Layer Active Time, and so on.

All tiers of the system must provide the same set of system metrics.

**Parent topic:** Glossary

### tag

When a work request is received by the system, an attempt is made to classify the type of work requested. The objective of classification is to determine which Performance Objective applies to this particular work request. The result of classification is a tag (the Performance Class name) that is carried with the work request as it proceeds through the system. The tag enables the work request to be associated with the Performance Objective for the workload (Performance Class).

**Parent topic:** Glossary

### tier

A tier is a logical processing component within a system. The tiers are stacked on top of each other to provide the end-to-end processing stack for a system. WebCache, OHS, OC4J, Oracle Database and Oracle Automatic Storage Management are examples of tiers.

There can be multiple entities in a given tier providing either redundancy or distinct functionality. For example, a system might include two OHS instances for higher availability and two databases, one for CRM, and the other for ERP.

**Parent topic:** Glossary

### uniform services

Services that must be offered on every node of a server pool.

**Parent topic:** Glossary

### UserName

The OCI_ATTR_USERNAME or the Oracle Database user that is used to authenticate to the database.

**Parent topic:** Glossary

### work request

A work request is the smallest atom of work that a user can initiate. A work request can be an HTTP request, a SOAP request, a SQL statement sent to the database, or the execution of a process. A work request arrives at a layer, perhaps from the outside world, perhaps from another layer. The work request is processed, and a response is generated; the response is sent back to the requester.

**Parent topic:** Glossary
