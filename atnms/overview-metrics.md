Oracle Database QoS Management uses a standardized set of metrics, which are collected by all the servers in the system.

Oracle Database QoS Management bases its decisions on observations of how long work requests spend waiting for resources. Examples of resources that work requests can wait for include hardware resources, such as CPU cycles, disk I/O queues, and Global Cache blocks. Other waits can occur within the database, such as latches, locks, pins, and so on. Although the resource waits within the database are accounted for in the Oracle Database QoS Management metrics, they are not managed or specified by type.

The response time of a work request consists of execution time and a variety of wait times; changing or improving the execution time generally requires application source code changes. Oracle Database QoS Management therefore observes and manages only wait times.

There are two types of metrics used to measure the response time of work requests: performance metrics and resource metrics. These metrics enable direct observation of the wait time incurred by work requests in each Performance Class, for each resource requested, as the work request traverses the servers, networks, and storage devices that form the system. Another type of metric, the Performance Satisfaction Metric, measures how well the Performance Objectives for a Performance Class are being met.

- Performance Metrics
  Performance metrics give an overview of where time is spent in the system and enable comparisons of wait times across the system.
- Resource Metrics
  Resource metrics give an overview of where time is spent in the system for each resource requested.
- Performance Satisfaction Metrics
  A useful metric for analyzing workload performance is a common and consistent numeric measure of how work requests in a Performance Class are doing against the current Performance Objective for that Performance Class.
- Using Metrics to Identify Performance Issues
  Oracle Database QoS Management uses the metrics it collects to identify performance bottlenecks.

**Related Topics**

- [Using the Oracle Database QoS Management Dashboard](using-qos-management-dashboard.md)

**Parent topic:** [Introduction to Oracle Database QoS Management](introduction-oracle-database-qos-management.md)

### 6.5.1 Performance Metrics

Performance metrics give an overview of where time is spent in the system and enable comparisons of wait times across the system.

Performance metrics are collected at the entry point to each server in the system. Data is collected periodically and forwarded to a central point for analysis, decision making, and historical storage. See [Figure 6-6](overview-oracle-database-qos-management.md) for an illustration of how the system data are collected.

Performance metrics measure the response time (the difference between the time a request comes in and the time a response is sent out). The response time for all database client requests in a Performance Class is averaged and presented as the average response time, measured in seconds for a database request.

**Related Topics**

- [Reviewing Performance Metrics](reviewing-performance-metrics.md)

**Parent topic:** Overview of Metrics

### 6.5.2 Resource Metrics

Resource metrics give an overview of where time is spent in the system for each resource requested.

There are two resource metrics for each resource of interest in the system:

- Resource usage time: Measures how much time was spent using the resource for each work request

- Resource wait time: Measures the time spent waiting to get the resource

Resources are classified as CPU, Storage I/O, Global Cache, and Other (database waits). The data are collected from the Oracle RAC databases, Oracle Clusterware, and the operating system.

**Related Topics**

- [Viewing the Resource Wait Times Breakdown](reviewing-performance-metrics.md)

**Parent topic:** Overview of Metrics

### 6.5.3 Performance Satisfaction Metrics

A useful metric for analyzing workload performance is a common and consistent numeric measure of how work requests in a Performance Class are doing against the current Performance Objective for that Performance Class.

This numeric measure is called the Performance Satisfaction Metric.

Different performance objectives are used to measure the performance of workloads, as shown in the following table:

| Workload Type | Performance Objectives                        |
|:--------------|:----------------------------------------------|
| OLTP          | Response time, transactions per second        |
| Batch         | Velocity, throughput                          |
| DSS           | Read or cache hit ratio, duration, throughput |

Oracle Database QoS Management currently supports only OLTP workloads. For OLTP workloads, you can only configure a response time performance objective.

**Related Topics**

- [Interpreting the Performance Overview Graphs](using-qos-management-dashboard.md)

**Parent topic:** Overview of Metrics

### 6.5.4 Using Metrics to Identify Performance Issues

Oracle Database QoS Management uses the metrics it collects to identify performance bottlenecks.

The Oracle Database QoS Management metrics provide the information needed to systematically identify Performance Class bottlenecks in the system. When a Performance Class is violating its Performance Objective, the bottleneck for that Performance Class is the resource that contributes the largest average wait time for each work request in that Performance Class.

The Oracle Database QoS Management metrics are used to find a bottleneck for a Performance Class using the following steps:

1.  Oracle Database QoS Management selects the highest ranked Performance Class that is not meeting its Performance Objective.

2.  For that Performance Class, wait times for each resource are determined from the collected metrics.

3.  The resource with the highest wait time per request is determined to be the bottlenecked resource.

Analyzing the average wait for each database request and the total number of requests for each Performance Class provides the resource wait time component of the response times of each Performance Class. The largest such resource contribution (CPU, Storage I/O, Global Cache, or Other) is the current bottleneck for the Performance Class.

**Related Topics**

- [Viewing the Resource Wait Times Breakdown](reviewing-performance-metrics.md)

**Parent topic:** Overview of Metrics
