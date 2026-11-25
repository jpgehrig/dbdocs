This section contains the following subsections:

- Overview of Run-Time Connection Load Balancing

- Setting Up Run-Time Connection Load Balancing

### 9.3.1 Overview of Run-Time Connection Load Balancing

In an Oracle Real Application Clusters environment, a connection could belong to any instance that provides the relevant service. In the best case, all instances perform equally well and randomly retrieving a connection from the cache is appropriate. However, when one instance performs better than others, random selection of a connection is inefficient. The run-time connection load balancing feature enables routing of work requests to an instance that offers the best performance, minimizing the need to relocate work.

UCP JDBC connection pools leverage the load balancing functionality provided by an Oracle RAC database. Run-time connection load balancing requires the use of an Oracle JDBC driver and an Oracle RAC database.

**See Also:**

[Oracle Real Application Clusters Administration and Deployment Guide](../racad/introduction-to-oracle-rac.md)

Run-time connection load balancing is useful when:

- Traditional balancing of workload is not optimal

- Requests must be routed to make optimal use of resources in a clustered database

- Capacity within the cluster differs and is expected to change over time

- The need to avoid sending work to slow, hung, and dead nodes is required

UCP uses the Oracle RAC Load Balancing Advisory. The advisory is used to balance work across Oracle RAC instances and is used to determine which instances offer the best performance. Applications transparently receive connections from instances that offer the best performance. Connection requests are quickly diverted from instances that have slowed, are not responding, or that have failed.

Run-time connection load balancing provides the following benefits:

- Manages pooled connections for high performance and scalability

- Receives continuous recommendations on the percentage of work to route to database instances

- Adjusts distribution of work based on different back-end node capacities such as CPU capacity or response time

- Reacts quickly to changes in cluster reconfiguration, application workload, overworked nodes, or hangs

- Receives metrics from the Oracle RAC Load Balance Advisory. Connections to well performing instances are used most often. New and unused connections to under-performing instances will gravitate away over time. When distribution metrics are not received, connection are selected using a random choice.

### 9.3.2 Setting Up Run-Time Connection Load Balancing

Run-time connection load balancing requires that FCF is enabled and configured properly.

In addition, you must configure the Oracle RAC Load Balancing Advisory with service-level goals for each service for which load balancing is enabled:

- The service goal must be set to one of the following:

  - `DBMS_SERVICE.SERVICE_TIME`

  - `DBMS_SERVICE.THROUGHPUT`

  The service goal can be set using the `goal` parameter, and the connection balancing goal can be set using the `clb_goal` parameter.

- The connection balancing goal must be set to `SHORT`. For example,

      EXECUTE DBMS_SERVICE.MODIFY_SERVICE (service_name => 'sjob' -, goal =>
         DBMS_SERVICE.GOAL_THROUGHPUT -, clb_goal => DBMS_SERVICE.CLB_GOAL_SHORT);

  Or

      EXECUTE DBMS_SERVICE.MODIFY_SERVICE (service_name => 'sjob' -, goal =>
         DBMS_SERVICE.GOAL_SERVICE_TIME -, clb_goal => DBMS_SERVICE.CLB_GOAL_SHORT);

The connection balancing goal can also be set by calling the `DBMS_SERVICE.create_service` procedure.

**Note:**

You can set the connection balancing goal to `LONG`. However, this is mostly useful for closed workloads, that is, when the rate of completing work is equal to the rate of starting new work.

**Related Topics**

- [About Fast Connection Failover](fast-connection-failover.md)

**See Also:**

[Oracle Real Application Clusters Administration and Deployment Guide](../racad/introduction-to-oracle-rac.md)
