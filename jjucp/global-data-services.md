This section describes the new Global Data Services (GDS) feature that can be used with Universal Connection Pool:

- Overview of Global Data Services

- Configuring an Application for Using GDS

### 9.5.1 Overview of Global Data Services

Global Data Services (GDS) feature is available since Oracle Database 12c Release 1 (12.1). Through this feature, Fast Connection Failover, Run-time Connection Load-Balancing, and Connection Affinity features that were available only in Oracle RAC, were extended to a set of replicated databases offering common services.

The set of databases may include Oracle RAC and single-instance Oracle databases interconnected through Data Guard, GoldenGate, or any other replication technology. A database service that can be provided by multiple databases is called a global service, so that it can be distinguished from the traditional service that can be provided only by a single database. This combination enables services to be deployed anywhere within this globally distributed configuration, supporting load balancing, high availability, database affinity, and so on.

**See Also:**

[Oracle Database Global Data Services Concepts and Administration Guide](../gsmug/intro-global-data-services.md)

### 9.5.2 Configuring an Application for Using GDS

UCP connects to Global Data Services in the same way that it connects to local services on an Oracle RAC. The service name in the connection string should be the name of the global service. The endpoint should be the endpoint of a GDS listener instead of the endpoint for the local, remote, or SCAN listener of a database.

A client must specify its region in the `REGION` parameter of the connection string. This is a new requirement for GDS. The region name is required because, in case of GDS, Run-time Load Balancing advisory is customized for particular regions. Following is an example of a typical connection string:

    (DESCRIPTION=
      (ADDRESS=(GDS_protocol_address_information))
      (CONNECT_DATA=
       (SERVICE_NAME=global_service_name)
       (REGION=region_name)))

Like with local services, UCP can specify multiple GDS listeners in the same connection string for listener failover, load balancing, or both.

**Note:**

SCAN is not supported for GDS listeners, therefore endpoint for each listener must be specified.

    (DESCRIPTION=
      (ADDRESS_LIST=
        (LOAD_BALANCE=ON)
        (FAILOVER=ON)
        (ADDRESS=(GDS_protocol_address_information))
        (ADDRESS=(GDS_protocol_address_information)))
      (CONNECT_DATA=
       (SERVICE_NAME=global_service_name)
       (REGION=region_name)))

The `REGION` parameter is optional if only global service managers from the local region are specified in the client connection string. This is the case when there is only one region in the GDS configuration, or can be the case when there are multiple regions. But, it is not feasible to change the connection string of the an existing client designed to work with a single database. If the `REGION` parameter is not specified, then the client's region is assumed to be the region of the global service manager used to connect to the global service.

**Note:**

Unless the `REGION` parameter is specified in the connection string, you can use a pre-12c thin JDBC client only with a GDS configuration that has a single region.

All GDS listeners in the preceding example belong to the same region where UCP is running, that is the local region. To provide high availability, when all GDSs in the local region are unavailable, you can specify the GDS listeners for the buddy region in additional `ADDRESS_LIST` descriptors.

    (DESCRIPTION=
      (FAILOVER=on)
      (ADDRESS_LIST=
        (LOAD_BALANCE=ON)
        (ADDRESS=(global_protocol_address_information))
        (ADDRESS=(global_protocol_address_information)))
      (ADDRESS_LIST=
        (LOAD_BALANCE=ON)
        (ADDRESS=(global_protocol_address_information))
        (ADDRESS=(global_protocol_address_information)))
      (CONNECT_DATA=
       (SERVICE_NAME=global_service_name)
       (REGION=region_name)))

You do not need manual ONS configuration because UCP automatically retrieves the ONS connection information that is optimally customized for the UCP region from GDS.

**Note:**

- To enable automatic ONS configuration for GDS, you must enable Fast Connection Failover (FCF) on UCP.

- Automatic ONS configuration works only with Oracle GDS and Oracle RAC. It does not work with single-instance Oracle Databases.

  Automatic ONS configuration does not support ONS wallet or keystore parameters. If your application requires any of these parameters, then you must configure ONS explicitly in either of the following two ways:

  - Calling the `PoolDataSource.setONSConfiguration(String)` method

  - Adding the ONS wallet or keystore parameters in the local ONS configuration file
