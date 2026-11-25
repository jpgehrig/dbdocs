UCP JDBC connection pools provide a tight integration with various Oracle Real Application Clusters (Oracle RAC) Database features. The features include Fast Connection Failover (FCF), Run-Time Connection Load Balancing, and Connection Affinity. These features require the use of an Oracle JDBC driver, Oracle RAC database, and the Oracle Notification Service library (`ons.jar`) that is included with the Oracle Client software.

Applications use Oracle RAC features to maximize connection performance and availability and to mitigate down-time due to connection problems. Applications have different availability and performance requirements and should implement Oracle RAC features accordingly.

**Note:**

Starting from Oracle Database 11g Release 1 (11.2), FCF is also supported by Oracle Restart on a single instance database. Oracle Restart was previously known as Single-Instance High Availability (SIHA).

**See Also:**

- [Oracle Real Application Clusters Administration and Deployment Guide](../racad/workload-management-with-dynamic-database-services.md) for more information about these technologies

- [Oracle Database Administrator's Guide](../admin/configuring-automatic-restart-of-an-oracle-database.md) for more information about Oracle Restart

### Generic High Availability and Performance Features

The UCP APIs and connection pool properties include many high availability and performance features that do not require an Oracle RAC database. These features work well with both Oracle and non-Oracle connections and are discussed throughout this guide. For example: validating connections on borrow; setting timeout properties; setting maximum reuse properties; and connection pool manager operations are all used to ensure a high-level of connection availability and optimal performance.

**Note:**

Generic high availability and performance features work slightly better when using Oracle connections because UCP leverages Oracle JDBC internal APIs.

### Database Version Compatibility for Oracle RAC

The following table lists supported Database versions for various Oracle RAC features:

Table 9-1 Oracle RAC Version Compatibility

| Feature                            | Supported Database Version                                                     |
|:-----------------------------------|:-------------------------------------------------------------------------------|
| Fast Connection Failover           | Oracle Database 10.1.x and later versions                                      |
| Run-time Connection Load-Balancing | Oracle Database 10.2.x and later versions                                      |
| Web Session Affinity               | Oracle Database 11.1.x and later versions                                      |
| Transaction-Based Affinity         | Oracle Database 10.2.x and later versions (Oracle Database 11.1.x recommended) |

### Oracle JDBC Driver Version Compatibility for Oracle RAC

Oracle JDBC driver 10.1.x and later versions are supported with Oracle RAC features.
