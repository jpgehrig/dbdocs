## Changes in This Release for Oracle Database Net Services Reference

Review the changes in Oracle Database Net Services Reference for Oracle Database 19c.

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

See [Oracle Database Security Guide](../dbseg/authenticating-and-authorizing-iam-users-oracle-dbaas-databases.md), [PASSWORD_AUTH](local-naming-parameters-in-tns-ora-file.md), [OCI_IAM_URL](local-naming-parameters-in-tns-ora-file.md), [OCI_TENANCY](local-naming-parameters-in-tns-ora-file.md), [OCI_COMPARTMENT](local-naming-parameters-in-tns-ora-file.md), and [OCI_DATABASE](local-naming-parameters-in-tns-ora-file.md).

Microsoft Azure Active Directory Integration with Additional Oracle Database Environments

Available for Oracle Database release 19.16, Microsoft Azure Active Directory (Azure AD) users can log in to additional Oracle Database environments with their Azure AD OAuth2 access token.

For a list of the supported Oracle Database environments, see [Oracle Database Security Guide](../dbseg/authenticating-and-authorizing-microsoft-entra-id-ms-ei-users-oracle-databases-oracle-exadata.md).

Azure AD Integration with Oracle Autonomous Cloud Databases

Available for Oracle Autonomous Database in June 2022, Azure AD users can log in to Oracle Cloud Infrastructure (OCI) Autonomous Database (Shared Infrastructure) with their Azure AD OAuth2 access token.

OCI Oracle Autonomous Database now can accept Azure AD OAuth2 tokens to access the database. Azure AD users can access the database directly using their Azure AD tokens, and applications can use their service tokens to access the database.

See [Oracle Database Net Services Administrator's Guide](../netag/quick-start-oracle-net-services.md) and [Oracle Database Security Guide](../dbseg/authenticating-and-authorizing-microsoft-entra-id-ms-ei-users-oracle-databases-oracle-exadata.md).

The `TOKEN_AUTH` parameter allows you to configure Azure AD token-based authentication for Oracle Autonomous Cloud Databases. You must also use the `TOKEN_LOCATION` parameter to specify the directory location where the Azure AD token is stored for authentication.

See [TOKEN_AUTH](local-naming-parameters-in-tns-ora-file.md) and [TOKEN_LOCATION](local-naming-parameters-in-tns-ora-file.md).

IAM Integration with Oracle Autonomous Cloud Databases

Available for Oracle Database release 19.13, IAM users can log in to Oracle Autonomous Database using either database password or token-based authentication.

An IAM ADMIN user can configure both the authentication and authorization of IAM users and IAM groups. An IAM user can log in to Oracle Autonomous Cloud Databases using tools, such as SQL\*Plus or SQLcl.

See [Oracle Database Net Services Administrator's Guide](../netag/quick-start-oracle-net-services.md) and [Oracle Database Security Guide](../dbseg/authenticating-and-authorizing-iam-users-oracle-dbaas-databases.md).

TOKEN_AUTH and TOKEN_LOCATION Parameters

The `sqlnet.ora` or `tnsnames.ora` parameter `TOKEN_AUTH` allows you to configure IAM token-based authentication for Oracle Autonomous Cloud Databases.

The `sqlnet.ora` or `tnsnames.ora` parameter `TOKEN_LOCATION` allows you to override the default directory where the database token and private key files are stored for authentication. This is an optional parameter.

See [TOKEN_AUTH](local-naming-parameters-in-tns-ora-file.md) and [TOKEN_LOCATION](local-naming-parameters-in-tns-ora-file.md).

One-Way Transport Layer Security (TLS)

This feature allows you to configure one-way TLS (server authentication). With this method, only the database server authenticates to the client by presenting its certificate issued by Certificate Authority (CA) and the client verifies whether the database server certificate is valid.

An Oracle client wallet with the server certificate is not required if the database server certificate is signed by a trusted common root certificate that is already installed in the local system default certificate store.

See [Oracle Database Net Services Administrator's Guide](../netag/understanding-communication-layers.md).

Security Update for Native Encryption

The following supported algorithms are improved:

- Encryption algorithms: `AES128`, `AES192`, and `AES256`
- Crypto-checksum algorithms: `SHA1`, `SHA256`, `SHA384`, and `SHA512`

The following algorithms are deprecated:

- Encryption algorithms: `DES`, `DES40`, `3DES112`, `3DES168`, `RC4_40`, `RC4_56`, `RC4_128`, and `RC4_256`
- Crypto-checksum algorithm: `MD5`

To transition your Oracle Database environment to use stronger algorithms, download and install the patch described in My Oracle Support note [2118136.2](https://support.oracle.com/CSP/main/article?cmd=show&amp;type=NOT&amp;id=2118136.2).

The new `sqlnet.ora` parameters `SQLNET.ALLOW_WEAK_CRYPTO` and `SQLNET.ALLOW_WEAK_CRYPTO_CLIENTS` enable you to review the specified encryption and crypto-checksum algorithms. This ensures that the connection does not encounter compatibility issues and your configuration uses supported strong algorithms.

See [Oracle Database Security Guide](../dbseg/configuring-network-data-encryption-and-integrity.md).

SQLNET.ALLOW_WEAK_CRYPTO Parameter

Use the `SQLNET.ALLOW_WEAK_CRYPTO` parameter to configure your client-side network connection by reviewing the specified encryption and crypto-checksum algorithms.

See [SQLNET.ALLOW_WEAK_CRYPTO](parameters-for-the-sqlnet.ora.md).

SQLNET.ALLOW_WEAK_CRYPTO_CLIENTS Parameter

Use the `SQLNET.ALLOW_WEAK_CRYPTO_CLIENTS` parameter to configure your server-side network connection by reviewing the specified encryption and crypto-checksum algorithms.

See [SQLNET.ALLOW_WEAK_CRYPTO_CLIENTS](parameters-for-the-sqlnet.ora.md).

COLOCATION_TAG Parameter

The `COLOCATION_TAG` parameter is an alphanumeric string that you can use with the `CONNECT_DATA` parameter of the TNS connect string. When you set the `COLOCATION_TAG` parameter, it attempts to route clients with the same `COLOCATION_TAG` to the same database instance.

Colocation of sessions on the same instance can help decrease inter-instance communication and thereby increase performance for workload that benefits from being executed in the same instance.

See [COLOCATION_TAG](local-naming-parameters-in-tns-ora-file.md).

KERBEROS5_PRINCIPAL Parameter

When you configure Kerberos authentication for an Oracle Database client, you can use the `KERBEROS5_PRINCIPAL` parameter to specify multiple Kerberos principals with a single Oracle Database client. This is an optional parameter. When specified, it is used to verify if the principal name in the credential cache matches the parameter value.

Use this parameter with the `CONNECT_DATA` parameter. Alternatively, you can specify `KERBEROS5_CC_NAME` in the connect string along with the `KERBEROS5_PRINCIPAL` parameter to connect as a different Kerberos principal. Each Kerberos principal must have a valid credential cache.

See [KERBEROS5_PRINCIPAL](local-naming-parameters-in-tns-ora-file.md) and [SQLNET.KERBEROS5_CC_NAME](parameters-for-the-sqlnet.ora.md).

**Parent topic:** Changes in This Release for Oracle Database Net Services Reference

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

**Parent topic:** Changes in This Release for Oracle Database Net Services Reference
