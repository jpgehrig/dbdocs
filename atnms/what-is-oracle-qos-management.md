Oracle Database QoS Management is an automated, policy-based product that monitors the workload requests for an entire system.

Many companies are consolidating and standardizing their data center computer systems. Instead of using individual servers for each application, they run multiple applications on clustered databases. Also, the migration of applications to the Internet has introduced the problem of managing an [open workload](glossary.md). An open workload is subject to demand surges, which can overload a system, resulting in a new type of application failure that cannot be fully anticipated or planned for. To keep applications available and performing within their target service levels in this type of environment, you must:

- Pool resources.

- Have management tools that detect performance bottlenecks in real time.

- Reallocate resources to meet the change in demand.

Oracle Database QoS Management is an automated, policy-based product that monitors the workload requests for an entire system. Oracle Database QoS Management manages the resources that are shared across applications, and adjusts the system configuration to keep the applications running at the performance levels needed by your business. Oracle Database QoS Management responds gracefully to changes in system configuration and demand, thus avoiding additional oscillations in the performance levels of your applications.

Oracle Database QoS Management monitors the performance of each [work request](glossary.md) on a target system. Oracle Database QoS Management starts to track a work request from the time a work request requests a connection to the database using a database service. The amount of time required to complete a work request, or the response time (also known as the [end-to-end response time](glossary.md), or round-trip time), is the time from when the request for data was initiated and when the data request is completed. By accurately measuring the two components of response time, which are the time spent using resources and the time spent waiting to use resources, Oracle Database QoS Management can quickly detect bottlenecks in the system. Oracle Database QoS Management then makes suggestions to reallocate resources to relieve a [bottleneck](glossary.md), thus preserving or restoring service levels.

Oracle Database QoS Management manages the resources on your system so that:

- When sufficient resources are available to meet the demand, business-level performance requirements for your applications are met, even if the workload changes.

- When sufficient resources are not available to meet the demand, Oracle Database QoS Management attempts to satisfy performance requirements of more business-critical workloads at the expense of less business-critical workloads.

**Parent topic:** [Introduction to Oracle Database QoS Management](introduction-oracle-database-qos-management.md)
