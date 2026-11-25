After the initial configuration, Oracle Database Quality of Service Management is an automated system. As a result, most of the problems you might encounter are related to configuring Oracle Database QoS Management.

The following sections illustrate the most common problems, and how to resolve them:

- Cannot Enable Oracle Database Quality of Service Management
- Cannot Enable Oracle Database QoS Management for a Database
  For a database to be managed by Oracle Database QoS Management, the database must be compliant, enabled, and Oracle Database QoS Management must be able to access `APPQOSSYS` database user:
- Oracle Database Resource Manager Not Enabled and Resource Plan Errors
  Oracle Database Quality of Service (QoS) Management requires Database Resource Manager to use a specific resource plan.
- Do Not Have Access to a Server Pool
  Server pools can be managed separately from the database by configuring special operating system groups.
- Server Pool Is Marked As Unmanageable
  A server pool is marked as unmanageable if Oracle Database QoS Management is not able to properly measure or predict the performance of Performance Classes deployed in that server pool.
- Metrics Are Missing For a Performance Class
  Metrics are captured by Oracle Database QoS Management by querying the managed database instances in the cluster.
- Oracle Database QoS Management is not Generating Recommendations
  Recommendations are generated once a minute when logged into the Oracle Database QoS Management Dashboard (the Dashboard).
- Recently Added Server was Placed in the Wrong Server Pool
  Servers are moved within a cluster by Oracle Clusterware, or as directed by an administrator.
- RMI Port Conflict Detected
  When you install Oracle Grid Infrastructure for a cluster, the port for the `qosmserver` resource might be set to 23792.

**Parent topic:** [Troubleshooting Oracle Database QoS Management](troubleshooting-oracle-database-qos-management.md)

### 10.1.1 Cannot Enable Oracle Database Quality of Service Management

Before you can enable Oracle Database QoS Management within a cluster, you must first create a Policy Set.

**Related Topics**

- [Create an Initial Policy Set](configuring-qos-management-manage-db-workloads.md)

**Parent topic:** Common Problems

### 10.1.2 Cannot Enable Oracle Database QoS Management for a Database

For a database to be managed by Oracle Database QoS Management, the database must be compliant, enabled, and Oracle Database QoS Management must be able to access `APPQOSSYS` database user:

- A compliant database is an Oracle RAC database that is running Oracle Database release 11.2.0.2 or greater.

- For a database to be enabled, Oracle Database QoS Management must be able to connect to the database. The connection is configured when you select the Enable Quality of Service Management link in the Oracle Enterprise Manager Cloud Control. When you select this link, you are prompted for the cluster credentials and the password for the `APPQOSSYS` account in the database. By default the `APPQOSSYS` account is expired. When you submit a password, the account is unlocked.

- If the password for the `APPQOSSYS` user is changed through other methods or the account is locked, then Oracle Database QoS Management is disabled for this database until this condition is corrected by selecting the Enable Quality of Service Management link again.

**Related Topics**

- [Enabling Oracle Database QoS Management for a Cluster](using-qos-management-dashboard.md)

**Parent topic:** Common Problems

### 10.1.3 Oracle Database Resource Manager Not Enabled and Resource Plan Errors

Oracle Database Quality of Service (QoS) Management requires Database Resource Manager to use a specific resource plan.

Oracle Database QoS Management installs a special Oracle Database Resource Manager plan, `APPQOS_PLAN`, whenever a database is enabled for management by Oracle Database QoS Management. Oracle Database QoS Management requires this resource plan to move Performance Classes to different levels of CPU scheduling. No other plan can be active while Oracle Database QoS Management is enabled on this database. If a resource plan is not enabled for the Oracle RAC database, then an error results when trying to enable the database for management by Oracle Database QoS Management. After a resource plan is enabled, then enabling the database for management by Oracle Database QoS Management succeeds.

To check that the required APPQOS_PLAN is active on the target database, connect using SQL\*Plus and issue the following statement:

    SQL> show parameter resource_manager_plan

You should see output similar to the following:

    NAME                                 TYPE        VALUE
    ------------------------------------ ----------- ------------------------------
    resource_manager_plan                string      FORCE:APPQOS_PLAN

If you are querying a Multitenant database, then the output is similar to the following:

    NAME                                 TYPE        VALUE
    ------------------------------------ ----------- ------------------------------
    resource_manager_plan                string      FORCE:ORA$QOS_CDB_PLAN

**Parent topic:** Common Problems

### 10.1.4 Do Not Have Access to a Server Pool

Server pools can be managed separately from the database by configuring special operating system groups.

By default, the user that installed Oracle Grid Infrastructure for a cluster can perform operations on server pools. If you use a separate operating system for the Oracle Database installation, then execute permissions on a server pool must be granted to the database software owner before a database can be deployed in that server pool. To grant this permission, you must use the CRSCTL utility to modify the server pool ACL attribute. A database administrator can also create server pools using Server Control (SRVCTL) or Oracle Enterprise Manager.

**Related Topics**

- [Oracle Clusterware Administration and Deployment Guide](../cwadd/oracle-clusterware-control-crsctl-utility-reference.md)

**Parent topic:** Common Problems

### 10.1.5 Server Pool Is Marked As Unmanageable

A server pool is marked as unmanageable if Oracle Database QoS Management is not able to properly measure or predict the performance of Performance Classes deployed in that server pool.

A server pool can be considered unmanageable under the following conditions:

1.  The servers in the server pool have different physical CPU counts.

2.  The CPU count for every database instance could not be retrieved.

3.  The sum of the configured CPU counts for all database instances on a server is greater than its physical CPU count.

4.  Singleton services are deployed in a server pool with a maximum size larger than one.

5.  Oracle Database QoS Management is unable to collect the metrics for all Performance Classes, or the metrics collected do not contain valid data.

6.  The server pool has a database that is not enabled for Oracle Database QoS Management.

If a server is added to a server pool, then Oracle starts up instances and services on the new server for the policy-managed databases in the server pool. When an instance is started on the new server, Oracle checks the SPFILE of the existing instances for the `CPU_COUNT` setting, and uses this value for the new instance. By default, if there is no setting for `CPU_COUNT` in the SPFILE, then the instances on the new server will be started with `CPU_COUNT` set to the number of physical CPUs of the server. This is not a supported configuration and will result in the server pool being marked as unmanageable. Also, if you modify the `CPU_COUNT` parameter but do not store the change in the SPFILE, then the `CPU_COUNT` parameter might be set to the wrong value on the newly started instance resulting in a configuration violation.

Make sure the databases and database instances that you want to be managed by Oracle Database QoS Management conform to the requirements documented in "Supported Database Configurations".

**Related Topics**

- [Supported Database Configurations](supported-configurations-qos-management.md)

**Parent topic:** Common Problems

### 10.1.6 Metrics Are Missing For a Performance Class

Metrics are captured by Oracle Database QoS Management by querying the managed database instances in the cluster.

Metrics are not be displayed under the following circumstances:

1.  The database requests (work being done) do not match the classifiers defined for a specific Performance Class and "No demand" is displayed.

2.  A more general classifier of a Performance Class is evaluated first. As a result, the Performance Class with the more specific classifier is shown as having "No demand". For example, if the `sales_pc` Performance Class uses the classifier `service=Sales` and the `sales_search` Performance Class uses the classifier (`s``ervice=Sales and action=Search)`, then, if the `sales_pc` Performance Class was listed first in the Edit Policy Set Performance Class Order screen, then any work request that uses the `sales` service would be placed in the `sales_pc` Performance Class, including those that are performing the `Search` action. The `sales_search` Performance Class does not generate any metrics and "No demand" is displayed for that Performance Class.

3.  The database instance is over-utilized and the metrics query reaches the time out limit and "Incomplete data" is displayed.

4.  The database is not producing mutually consistent data for the Performance Class and "Nonconforming data" is displayed. For example a Performance Class that is classifying database requests that exceed one second will cause this response.

5.  The metrics collected through the query do not pass the sanity verification checks performed by Oracle Database QoS Management and "Nonconforming data" is displayed.

**Parent topic:** Common Problems

### 10.1.7 Oracle Database QoS Management is not Generating Recommendations

Recommendations are generated once a minute when logged into the Oracle Database QoS Management Dashboard (the Dashboard).

Recommendations do not appear on the Dashboard in the following cases:

1.  Oracle Database QoS Management is disabled.

2.  An action is in progress implementing a recommendation.

3.  During the first minute of enabling Oracle Database QoS Management, or when submitting a Policy Set or activating a Policy Set.

**Parent topic:** Common Problems

### 10.1.8 Recently Added Server was Placed in the Wrong Server Pool

Servers are moved within a cluster by Oracle Clusterware, or as directed by an administrator.

When a new server joins the cluster, Oracle Clusterware places the server in a server pool according to the placement algorithm and the state of the server pool attributes of Min, Max and Importance. See the Oracle Clusterware Administration and Deployment Guide for a complete description of this placement process.

**Related Topics**

- [Oracle Clusterware Administration and Deployment Guide](../cwadd/policy-based-cluster-and-capacity-management.md)

**Parent topic:** Common Problems

### 10.1.9 RMI Port Conflict Detected

When you install Oracle Grid Infrastructure for a cluster, the port for the `qosmserver` resource might be set to 23792.

This can cause a port conflict with Java Remote Method Invocation (RMI).

You should set the `qosmserver` resource to use an available port, then restart the `qosmserver` resource using the following commands:

    srvctl modify qosmserver -rmiport port
    srvctl stop qosmserver
    srvctl start qosmserver

**Parent topic:** Common Problems
