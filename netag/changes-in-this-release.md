## Changes in This Release for Oracle Database Net Services Administrator's Guide

Review the changes in Oracle Database Net Services Administrator's Guide for Oracle Database 19c.

- New Features
  These are the new features and enhancements available with Oracle Database 19c.
- Deprecated Features
  These features are deprecated in this release and may be desupported in a future release.

### New Features

These are the new features and enhancements available with Oracle Database 19c.

Identity and Access Management Integration with Additional Oracle Database Environments

Available for Oracle Database release 19.16, Oracle Cloud Infrastructure (OCI) Identity and Access Management (IAM) users can log in to additional Oracle Database Environments.

For a list of the supported Oracle Database environments, see [Oracle Database Security Guide](../dbseg/authenticating-and-authorizing-iam-users-oracle-dbaas-databases.md).

Ability to Use the IAM User Name and IAM Database Password to Retrieve a Database Token

Retrieving an IAM database token using the IAM user name and IAM database password or secure external password store (SEPS) is more secure than using the password verifier method of database access. You can configure the database client to request this token directly from an OCI IAM endpoint.

The new `sqlnet.ora` or `tnsnames.ora` parameters enable you to configure this authentication method and specify the IAM endpoint along with additional metadata. These parameters are `PASSWORD_AUTH`, `OCI_IAM_URL`, `OCI_TENANCY` along with optional `OCI_COMPARTMENT` and `OCI_DATABASE`.

See [Connecting to the Database](quick-start-oracle-net-services.md) and [Oracle Database Security Guide](../dbseg/authenticating-and-authorizing-iam-users-oracle-dbaas-databases.md).

Microsoft Azure Active Directory Integration with Additional Oracle Database Environments

Available for Oracle Database release 19.16, Microsoft Azure Active Directory (Azure AD) users can log in to additional Oracle Database environments with their Azure AD OAuth2 access token.

For a list of the supported Oracle Database environments, see [Oracle Database Security Guide](../dbseg/authenticating-and-authorizing-microsoft-entra-id-ms-ei-users-oracle-databases-oracle-exadata.md).

Azure AD Integration with Oracle Autonomous Cloud Databases

Available for Oracle Autonomous Database in June 2022, Azure AD users can log in to Oracle Cloud Infrastructure (OCI) Autonomous Database (Shared Infrastructure) with their Azure AD OAuth2 access token.

OCI Oracle Autonomous Database now can accept Azure AD OAuth2 tokens to access the database. Azure AD users can access the database directly using their Azure AD tokens, and applications can use their service tokens to access the database.

See [Connecting to the Database](quick-start-oracle-net-services.md) and [Oracle Database Security Guide](../dbseg/authenticating-and-authorizing-microsoft-entra-id-ms-ei-users-oracle-databases-oracle-exadata.md).

IAM Integration with Oracle Autonomous Cloud Databases

Available for Oracle Database release 19.13, IAM users can log in to Oracle Autonomous Database using either database password or token-based authentication.

An IAM ADMIN user can configure both the authentication and authorization of IAM users and IAM groups. An IAM user can log in to Oracle Autonomous Cloud Databases using tools, such as SQL\*Plus or SQLcl.

See [Connecting to the Database](quick-start-oracle-net-services.md) and [Oracle Database Security Guide](../dbseg/authenticating-and-authorizing-iam-users-oracle-dbaas-databases.md).

One-Way Transport Layer Security (TLS)

This feature allows you to configure one-way TLS (server authentication). With this method, only the database server authenticates to the client by presenting its certificate issued by Certificate Authority (CA) and the client verifies whether the database server certificate is valid.

An Oracle client wallet with the server certificate is not required if the database server certificate is signed by a trusted common root certificate that is already installed in the local system default certificate store.

See [About TCP/IP with TLS Protocol](understanding-communication-layers.md).

SQL\*Net: Auto-Detection of Support for Out-of-Band Breaks

This feature automatically probes the network path between the client and the server in order to determine the status of out-of-band support, and automatically enable or disable it.

Out-of-band breaks were enabled by default for UNIX platforms in past releases. However, this configuration causes numerous problems when network devices on the path between the client and the server do not allow out-of-band data to pass through. This data may either be dropped or inlined leading to server-side problems such as Transparent Network Substrate (TNS) errors or data corruption. These problems are often very hard to diagnose. The solution is to turn off usage of out-of-band data manually by setting a `sqlnet.ora` parameter.

See [About Advanced Profile Information](configuring-profiles.md).

Oracle Network Log File Segmentation

This feature allows you to configure the maximum size and number of text log files for Oracle Network components, such as Oracle Net Listener, Connection Manager (CMAN), and global services manager. See [Oracle Network Log File Segmentation](troubleshooting-oracle-net-services.md).

Websocket Support for Database Client/Server Communication

The secure web socket connection establishment is designed to work over `HTTPS` to support `HTTPS` proxies and intermediary proxies. The Database client connection supports secure websocket protocol. This protocol offers a native connection to the database with minimum protocol overhead.

See [About Websocket Protocol](understanding-communication-layers.md).

Easy Connect Plus

The Easy Connect syntax that applications use to connect to Oracle Database has improved functionality. The new version is called Easy Connect Plus.

Easy Connect Plus simplifies Oracle Database application configuration and deployment for common use cases. With Easy Connect Plus, you no longer need to configure Oracle Net parameter files such as `tnsnames.ora` and `sqlnet.ora`. Easy Connect Plus also no longer requires you to set the `TNS_ADMIN` environment variable.

See [Support for Easy Connect Plus](configuring-naming-methods.md).

**Related Topics**

- [About Advanced Profile Information](configuring-profiles.md)
- [Oracle Network Log File Segmentation](troubleshooting-oracle-net-services.md)
- [About Websocket Protocol](understanding-communication-layers.md)
- [Support for Easy Connect Plus](configuring-naming-methods.md)

**Parent topic:** Changes in This Release for Oracle Database Net Services Administrator's Guide

### Deprecated Features

These features are deprecated in this release and may be desupported in a future release.

Deprecation of the SERVICE_NAMES Initialization Parameter

Starting with Oracle Database 19c, customer use of the `SERVICE_NAMES` parameter is deprecated. It can be desupported in a future release.

The use of the `SERVICE_NAMES` parameter is no longer actively supported. It must not be used for high availability (HA) deployments. It is not supported to use service names parameter for any HA operations. This restriction includes FAN, load balancing, `FAILOVER_TYPE`, `FAILOVER_RESTORE`, `SESSION_STATE_CONSISTENCY`, and any other uses.

To manage your services, Oracle recommends that you use the `SRVCTL` or `GDSCTL` command line utilities, or the `DBMS_SERVICE` package.

**Note:**

The `SERVICE_NAMES` parameter that is deprecated is different from the `SERVICE_NAME` parameter in Oracle Net connect strings. The `SERVICE_NAME` parameter is still valid.

Deprecation of Weak Native Network Encryption and Integrity Algorithms

The `DES`, `DES40`, `3DES112`, `3DES168`, `RC4_40`, `RC4_56`, `RC4_128`, `RC4_256`, and `MD5` algorithms are deprecated in this release.

As a result of this deprecation, Oracle recommends that you review your network encryption and integrity configuration to check if you have specified any of the deprecated weak algorithms.

To transition your Oracle Database environment to use stronger algorithms, download and install the patch described in My Oracle Support note [2118136.2](https://support.oracle.com/CSP/main/article?cmd=show&amp;type=NOT&amp;id=2118136.2).

**Related Topics**

- [Oracle Database Security Guide](../dbseg/configuring-network-data-encryption-and-integrity.md)

**Parent topic:** Changes in This Release for Oracle Database Net Services Administrator's Guide
