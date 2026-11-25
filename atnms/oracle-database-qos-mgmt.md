Oracle Database Quality of Service (QoS) Management manages the resources that are shared across applications.

Oracle Database Quality of Service (QoS) Management:

- Requires 12.1.0.2+ Oracle Grid Infrastructure

- Delivers Key Performance Indicators cluster-wide dashboard

- Phase in with Measure, Monitor, then Management Modes

Oracle Database Quality of Service (QoS) Management adjusts the system configuration to keep the applications running at the performance levels needed by your business.

Many companies are consolidating and standardizing their data center computer systems. Instead of using individual servers for each application, the companies run multiple applications on clustered databases. In addition, migration of applications to the Internet has introduced the problem of managing an **open workload**. An open workload is subject to demand surges that can overload a system. Over loading a system results in a new type of application failure that cannot be fully anticipated or planned for. To keep the applications available and performing within their target service levels in this type of environment, you must:

- Pool resources

- Have management tools that detect performance bottlenecks in real time

- Reallocate resources to meet the change in demand

Oracle Database QoS Management responds gracefully to changes in system configuration and demand, thus avoiding more oscillations in the performance levels of your applications.

Oracle Database QoS Management monitors the performance of each **work request** on a target system. Oracle Database QoS Management starts to track a work request from the time a work request tries to establish a connection to the database using a database service. The time required to complete a work request or the response time is the time from when the request for data was initiated and when the data request is completed. The response time is also known as the **end-to-end response time**, or **round-trip** time. By accurately measuring the two components of response time, Oracle Database QoS Management quickly detects bottlenecks in the system. Oracle Database QoS Management then suggests reallocating resources to relieve a **bottleneck**, thus preserving or restoring service levels.

Oracle Database QoS Management manages the resources on your system so that:

- When sufficient resources are available to meet the demand, business-level performance requirements for your applications are met, even if the workload changes

- When sufficient resources are not available to meet the demand, Oracle Database QoS Management attempts to satisfy the more critical business performance requirements at the expense of less critical performance requirements

**Related Topics**

- [Monitoring and Managing Database Workload Performance](oracle-database-qos-management.md)

**Parent topic:** [Components of Autonomous Health Framework](components-ahf.md)
