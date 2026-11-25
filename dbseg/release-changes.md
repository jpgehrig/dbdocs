## Changes in This Release for Oracle Database Security Guide

This preface contains:

- Changes in Oracle Database Security 19c
- Updates to Oracle Database Security 19c

### Changes in Oracle Database Security 19c

Oracle Database Security Guide for Oracle Database 19c has new security features.

- Multi-Factor Authentication Now Available
  Starting with Oracle Database 19.28, multi-factor authentication can be enabled for native database users.
- Signature-Based Security for LOB Locators
  Starting with this release, you can configure signature-based security for large object (LOB) locators.
- Default User Accounts Now Schema Only
  Using the schema only account feature from Oracle Database release 18c, most of the Oracle Database supplied schemas (users) now have their passwords removed to prevent users from authenticating to these accounts.
- Privilege Analysis Documentation Moved to Oracle Database Security Guide
  The documentation for privilege analysis has moved from Oracle Database Vault Administrator’s Guide to Oracle Database Security Guide.
- Ability to Grant or Revoke Administrative Privileges to and from Schema-Only Accounts
  Administrative privileges such as `SYSOPER` and `SYSBACKUP` can now be granted to schema-only (passwordless) accounts.
- Automatic Support for Both SASL and Non-SASL Active Directory Connections
  Starting with this release, both Simple Authentication and Security Layer (SASL) and Transport Layer Security (TLS) binds are supported for Microsoft Active Directory connections.
- Support for Oracle Native Encryption and TLS Authentication for Different Users Concurrently
  In previous releases, Oracle Database prevented the use of both Oracle native encryption (also called Advanced Networking Option (ANO) encryption) and Transport Layer Security (TLS) authentication together.
- Support for Host Name-Based Partial DN Matching for Matching for Server Certificates
  This new support for partial DN matching adds the ability for the client to further verify the server certificate.
- Ability to Audit Only Top-Level SQL Statements
  The unified auditing top-level statements feature enables you to audit top level user (or, direct user) activities in the database but without collecting indirect user activity audit data.
- Improved Read Performance for the Unified Audit Trial
  The `AUDSYS.AUD$UNIFIED` system table, which stores the unified audit trail records, has been redesigned to use partition pruning to improve read performance.
- SYSLOG Destination for Common Unified Audit Policies
  Available with Oracle Database release 19.9, certain predefined columns of unified audit records from common unified audit policies can be written to the UNIX SYSLOG destination.
- PDB_GUID as Audit Record Field Name for SYSLOG and the Windows Event Viewer
  The audit record fields for `SYSLOG` and the Windows Event Viewer now have a new field, `PDB_GUID`, to identify the pluggable database associated with a unified audit trail record.

**Parent topic:** Changes in This Release for Oracle Database Security Guide

#### Multi-Factor Authentication Now Available

Starting with Oracle Database 19.28, multi-factor authentication can be enabled for native database users.

Oracle Database allows multi-factor authentication (MFA) configuration for native users in the form of either push notifications through Oracle Mobile Authenticator (OMA) or Cisco Duo, or certificate-based authentication.

**Related Topics**

- [Configuring Multi-Factor Authentication](configuring-authentication.md)

**Parent topic:** Changes in Oracle Database Security 19c

#### Signature-Based Security for LOB Locators

Starting with this release, you can configure signature-based security for large object (LOB) locators.

This feature strengthens the security of Oracle Database LOBs, particularly when instances of LOB data types (CLOB and BLOB) are used in distributed environments.

LOB signature keys can be in both multitenant PDBs or in standalone, non-multitenant databases. You can enable the encryption of the LOB signature key credentials by executing the `ALTER DATABASE DICTIONARY ENCRYPT CREDENTIALS` SQL statement; otherwise, the credentials are stored in obfuscated format. If you choose to store the LOB signature key in encrypted format, then the database or PDB must have an open TDE keystore.

**Related Topics**

- [Securing LOBs with LOB Locator Signatures](managing-security-for-application-developers.md)

**Parent topic:** Changes in Oracle Database Security 19c

#### Default User Accounts Now Schema Only

Using the schema only account feature from Oracle Database release 18c, most of the Oracle Database supplied schemas (users) now have their passwords removed to prevent users from authenticating to these accounts.

This enhancement does not affect the sample schemas. Sample schemas are still installed with their default passwords.

For the default schemas that are schema only, administrators can still alter these accounts with passwords if they need to authenticate to the schema, but Oracle recommends changing the schemas back to a schema-only account afterward.

The benefit of this feature is that administrators no longer have to periodically rotate the passwords for these Oracle Database-provided schemas. This feature also reduces the security risk of attackers using default passwords to hack into these accounts.

**Related Topics**

- [Predefined Schema User Accounts Provided by Oracle Database](managing-security-for-oracle-database-users.md)
- [Schema-Only Accounts](configuring-authentication.md)

**Parent topic:** Changes in Oracle Database Security 19c

#### Privilege Analysis Documentation Moved to Oracle Database Security Guide

The documentation for privilege analysis has moved from Oracle Database Vault Administrator’s Guide to Oracle Database Security Guide.

See Oracle Database Licensing Information User Manual for privilege analysis licensing information.

**Related Topics**

- [Performing Privilege Analysis to Identify Privilege Use](performing-privilege-analysis-identify-privilege-use.md)
- [Oracle Database Licensing Information User Manual](../dblic/Licensing-Information.md)

**Parent topic:** Changes in Oracle Database Security 19c

#### Ability to Grant or Revoke Administrative Privileges to and from Schema-Only Accounts

Administrative privileges such as `SYSOPER` and `SYSBACKUP` can now be granted to schema-only (passwordless) accounts.

Existing user accounts (active, rarely accessed, and unused users) that are currently granted administrative privileges can be altered to be schema-only accounts. This enhancement prevents administrators from having to manage the passwords of these accounts.

**Related Topics**

- [About Schema-Only Accounts](configuring-authentication.md)

**Parent topic:** Changes in Oracle Database Security 19c

#### Automatic Support for Both SASL and Non-SASL Active Directory Connections

Starting with this release, both Simple Authentication and Security Layer (SASL) and Transport Layer Security (TLS) binds are supported for Microsoft Active Directory connections.

For centrally managed users, the Oracle database will initially try to connect to Active Directory using SASL bind. If the Active Directory server rejects the SASL bind connection, then the Oracle database will automatically attempt the connection again without SASL bind but still secured with TLS.

The Active Directory administrator is responsible for configuring the connection parameters for Active Directory server, but does not need to configure the database to match this new Active Directory connection enhancement. The database will automatically adjust from using SASL to not using SASL bind.

**Related Topics**

- [About Configuring the Oracle Database-Microsoft Active Directory Connection](integrating_mads_with_oracle_database.md)

**Parent topic:** Changes in Oracle Database Security 19c

#### Support for Oracle Native Encryption and TLS Authentication for Different Users Concurrently

In previous releases, Oracle Database prevented the use of both Oracle native encryption (also called Advanced Networking Option (ANO) encryption) and Transport Layer Security (TLS) authentication together.

Starting with this release, you can set a new parameter, `SQLNET.IGNORE_ANO_ENCRYPTION_FOR_TCPS`, to `TRUE` to ignore the `SQLNET.ENCRYPTION_CLIENT` or `SQLNET.ENCRYPTION_SERVER` when there is a conflict between the use of a TCPS client and either of these two parameters are set to `required`.

**Related Topics**

- [Enabling Both Oracle Native Encryption and SSL Authentication for Different Users Concurrently](configuring-network-data-encryption-and-integrity.md)

**Parent topic:** Changes in Oracle Database Security 19c

#### Support for Host Name-Based Partial DN Matching for Matching for Server Certificates

This new support for partial DN matching adds the ability for the client to further verify the server certificate.

The earlier ability to perform a full DN match with the server certificate during the Transport Layer Security (TLS) handshake is still supported. The client supports both full and partial DN matching. If the server DN matching is enabled, then partial DN matching is the default.

Allowing partial and full DN matching for certificate verification enables more flexibility based on how the certificates were created.

**Related Topics**

- [About Configuring the Server DN Matching and Using TCP/IP with TLS on the Client](configuring-secure-sockets-layer-authentication.md)

**Parent topic:** Changes in Oracle Database Security 19c

#### Ability to Audit Only Top-Level SQL Statements

The unified auditing top-level statements feature enables you to audit top level user (or, direct user) activities in the database but without collecting indirect user activity audit data.

You can use this feature to audit only the top-level user directly issued events, without the overhead of indirect SQL statements. Top-level statements are SQL statements that users directly issue. These statements can be important for both security and compliance. SQL statements run from within PL/SQL procedures or functions are not considered top level, so they may be less relevant for auditing purposes.

**Related Topics**

- [Auditing Only Top-Level Statements](configuring-audit-policies.md)

**Parent topic:** Changes in Oracle Database Security 19c

#### Improved Read Performance for the Unified Audit Trial

The `AUDSYS.AUD$UNIFIED` system table, which stores the unified audit trail records, has been redesigned to use partition pruning to improve read performance.

This redesign entailed the addition of a new column to the `AUDSYS.AUD$UNIFIED` table. The `UNIFIED_AUDIT_TRAIL` data dictionary view, which enables you to query the `AUDSYS.AUD$UNIFIED` table audit records, now has the `EVENT_TIMESTAMP_UTC` column to correspond with the new `AUDSYS.AUD$UNIFIED` table column. As part of this enhancement, the data type of the `EVENT_TIMESTAMP` column in the `GV$UNIFIED_AUDIT_TRAIL` view has changed `TIMESTAMP(6)`.

Oracle recommends that when you query the `UNIFIED_AUDIT_TRAIL` view, to include the `EVENT_TIMESTAMP_UTC` column in the `WHERE` clause to achieve partitioning pruning.

**Related Topics**

- [Best Practices for Querying the UNIFIED_AUDIT_TRAIL Data Dictionary View](keeping-your-oracle-database-secure.md)

**Parent topic:** Changes in Oracle Database Security 19c

#### SYSLOG Destination for Common Unified Audit Policies

Available with Oracle Database release 19.9, certain predefined columns of unified audit records from common unified audit policies can be written to the UNIX SYSLOG destination.

To enable this feature, you set `UNIFIED_AUDIT_COMMON_SYSTEMLOG`, a new CDB level `init.ora` parameter. This enhancement enables all audit records from common unified audit policies to be consolidated into a single destination.

This feature is available only on UNIX platforms, not Windows.

**Related Topics**

- [Enabling SYSLOG and Windows Event Viewer Captures for the Unified Audit Trail](administering-the-audit-trail.md)

**Parent topic:** Changes in Oracle Database Security 19c

#### PDB_GUID as Audit Record Field Name for SYSLOG and the Windows Event Viewer

The audit record fields for `SYSLOG` and the Windows Event Viewer now have a new field, `PDB_GUID`, to identify the pluggable database associated with a unified audit trail record.

In a multitenant database deployment, the pluggable database that generated a unified audit trail record must be identified in the audit trail. Starting with this release, the `SYSLOG` and Windows Event Viewer will have a new field, `PDB_GUID`, to capture this information. The data type is `VARCHAR2`.

**Related Topics**

- [About Writing the Unified Audit Trail Records to SYSLOG or the Windows Event Viewer](administering-the-audit-trail.md)

**Parent topic:** Changes in Oracle Database Security 19c

### Updates to Oracle Database Security 19c

Oracle Database release 19c has several updates from the last update of release 19c.

- Authenticating and Authorizing IAM Users to Oracle Autonomous Database on Dedicated Exadata Infrastructure
  Available for Oracle Database release 19.14, users now can authenticate and authorize IAM users to Oracle Autonomous Database on Dedicated Exadata Infrastructure.
- Enhancements for Identity and Access Management Integration with Oracle Database Environments
  Available for Oracle Database release 19.16 are enhancements to the integration of Identity and Access Management (IAM) users with Oracle Database Environments.
- Identity and Access Management Integration with Oracle Autonomous Cloud Databases
  Available for Oracle Database release 19.13, Identity and Access Management (IAM) users can log in to an Oracle Autonomous Database Serverless using either password or token-based authentication.
- Database Integration Support for Non-Default Domains for Identity and Access Management with Identity Domains
  Starting with this release, Oracle Database supports non-default domains in tenancies with Identity and Access Management (IAM) with Identity Domains.
- Microsoft Azure Active Directory Integration with Additional Oracle Database Environments Including On-Premises
  Available for Oracle Database release 19.16, Microsoft Azure Active Directory (Azure AD) users can log in to additional Oracle Database environments with their Azure AD `OAuth2` access token.
- Microsoft Azure Active Directory Integration with Oracle Cloud Infrastructure Autonomous Databases
  Available for Oracle Autonomous Database in June, 2022, Microsoft Azure Active Directory (Azure AD) users can log in to Oracle Cloud Infrastructure (OCI) Autonomous Database with their Azure AD `OAuth2` access token.
- Gradual Database Password Rollover for Applications
  Available for Oracle Database release 19.12, an application can change its database passwords without an administrator having to schedule downtime.
- Ability to Use Multiple Kerberos Principals with a Single Database Client
  Available for Oracle Database release 19.10, when you configure Kerberos authentication for an Oracle Database client, you can specify multiple Kerberos principals with a single Oracle Database client.
- Updated Support for Micro Edition Suite (MES) for FIPS 140.2
  Available for Oracle Database release 19.10, Oracle Database supports Micro Edition Suite (MES) version 4.5 for FIPS 140.2.
- Support for DBMS_CRYPTO Asymmetric Key Operations
  Available for Oracle Database release 19.9, the `DBMS_CRYPTO` PL/SQL package supports asymmetric key operations, in addition to the existing support for symmetric key operations.
- SYSLOG Destination for Common Unified Audit Policies
  Available with Oracle Database release 19.9, certain predefined columns of unified audit records from common unified audit policies can be written to the UNIX SYSLOG destination.
- Security Update for Native Encryption
  Oracle provides a patch that you can download to address necessary security enhancements that affect native network encryption environments in Oracle Database release 11.2 and later.
- Ability to Configure Transport Layer Security Connections without Client Wallets
  Available in Oracle Database release 19.14, an Oracle Database client will not be required to provide a wallet to hold well-known CA root certificates if they are available elsewhere in the local system.
- SSL_ALLOW_WEAK_DN_MATCH Parameter to Control the Behavior of SSL_SERVER_DN_MATCH
  Available with Oracle Database release 19.23, you can use the `SSL_ALLOW_WEAK_DN_MATCH` parameter to control how `SSL_SERVER_DN_MATCH` allows the service name for partial distinguished name matching and to only check the database server certificate.

**Parent topic:** Changes in This Release for Oracle Database Security Guide

#### Authenticating and Authorizing IAM Users to Oracle Autonomous Database on Dedicated Exadata Infrastructure

Available for Oracle Database release 19.14, users now can authenticate and authorize IAM users to Oracle Autonomous Database on Dedicated Exadata Infrastructure.

Additional enhancements are as follows:

- Applications can now connect to an Autonomous Database instance by using end-user, instance, and resource principals.
- IAM users can now proxy to an Autonomous Database by using a database user schema.
- Database links are supported for IAM connections.

**Related Topics**

- [Authenticating and Authorizing IAM Users for Oracle DBaaS Databases](authenticating-and-authorizing-iam-users-oracle-dbaas-databases.md)

**Parent topic:** Updates to Oracle Database Security 19c

#### Enhancements for Identity and Access Management Integration with Oracle Database Environments

Available for Oracle Database release 19.16 are enhancements to the integration of Identity and Access Management (IAM) users with Oracle Database Environments.

- Additional Oracle Database environments: The full list of supported Oracle Database environments is as follows:
  - Oracle Autonomous Database on Dedicated Exadata Infrastructure
  - Oracle Autonomous Database Serverless
  - Oracle Base Database Service
- Ability to use the IAM user name and password to retrieve an IAM token: Retrieving a token using an IAM user name and password or secure external password store (SEPS) is more secure than using the password verifier method of database access.

**Related Topics**

- [Authenticating and Authorizing IAM Users for Oracle DBaaS Databases](authenticating-and-authorizing-iam-users-oracle-dbaas-databases.md)

**Parent topic:** Updates to Oracle Database Security 19c

#### Identity and Access Management Integration with Oracle Autonomous Cloud Databases

Available for Oracle Database release 19.13, Identity and Access Management (IAM) users can log in to an Oracle Autonomous Database Serverless using either password or token-based authentication.

An IAM `ADMIN` user can configure both the authentication and authorization of IAM users and IAM groups. The IAM user can log in to the Oracle Autonomous Database using tools such as SQL\*Plus or SQLcl.

This enhancement provides the security advantages of both IAM and Oracle Database. For example, the Oracle Database gradual password rollover feature can be used in this configuration and update the application passwords without downtime.

**Related Topics**

- [Authenticating and Authorizing IAM Users for Oracle DBaaS Databases](authenticating-and-authorizing-iam-users-oracle-dbaas-databases.md)

**Parent topic:** Updates to Oracle Database Security 19c

#### Database Integration Support for Non-Default Domains for Identity and Access Management with Identity Domains

Starting with this release, Oracle Database supports non-default domains in tenancies with Identity and Access Management (IAM) with Identity Domains.

The following releases are supported:

- Oracle Autonomous Database Serverless
- Oracle Autonomous Database on Dedicated Exadata Infrastructure

This update allows IAM users in non-default IAM domains to access the database with IAM database password verifiers or IAM access tokens. IAM users in default domains are already supported.

In previous releases, the IAM integration only worked with users and groups from the default domain, and did not support users and groups from custom, non-default domains.

**Related Topics**

- [Authenticating and Authorizing IAM Users for Oracle DBaaS Databases](authenticating-and-authorizing-iam-users-oracle-dbaas-databases.md)

**Parent topic:** Updates to Oracle Database Security 19c

#### Microsoft Azure Active Directory Integration with Additional Oracle Database Environments Including On-Premises

Available for Oracle Database release 19.16, Microsoft Azure Active Directory (Azure AD) users can log in to additional Oracle Database environments with their Azure AD `OAuth2` access token.

The previous release supported Azure AD integration support for Oracle Cloud Infrastructure (OCI) Autonomous Databases. This release has expanded Azure AD integration support to on-premises Oracle Database release 19.16 and later, but not for Oracle Database 21c.

You can use Azure AD `OAuth2` tokens to access the database. Azure AD users can access the database directly using their Azure AD token, and applications can use their service tokens to access the database.

**Related Topics**

- [Authenticating and Authorizing Microsoft Azure Active Directory Users for Oracle Databases](authenticating-and-authorizing-microsoft-entra-id-ms-ei-users-oracle-databases-oracle-exadata.md)

**Parent topic:** Updates to Oracle Database Security 19c

#### Microsoft Azure Active Directory Integration with Oracle Cloud Infrastructure Autonomous Databases

Available for Oracle Autonomous Database in June, 2022, Microsoft Azure Active Directory (Azure AD) users can log in to Oracle Cloud Infrastructure (OCI) Autonomous Database with their Azure AD `OAuth2` access token.

OCI Oracle Autonomous Database now can accept Azure AD `OAuth2` tokens to access the database. Azure AD users can access the database directly using their Azure AD token, and applications can use their service tokens to access the database.

You can use Azure AD `OAuth2` tokens to access the database. Azure AD users can access the database directly using their Azure AD token, and applications can use their service tokens to access the database.

**Related Topics**

- [Authenticating and Authorizing Microsoft Azure Active Directory Users for Oracle Databases](authenticating-and-authorizing-microsoft-entra-id-ms-ei-users-oracle-databases-oracle-exadata.md)

**Parent topic:** Updates to Oracle Database Security 19c

#### Gradual Database Password Rollover for Applications

Available for Oracle Database release 19.12, an application can change its database passwords without an administrator having to schedule downtime.

To accomplish this, a database administrator can associate a profile having a non-zero limit for the `PASSWORD_ROLLOVER_TIME` password profile parameter, new with this release, with an application schema. This allows the database password of the application user to be altered while allowing the older password to remain valid for the time specified by the `PASSWORD_ROLLOVER_TIME` limit. During the rollover period of time, the application instance can use either the old password or the new password to connect to the database server. When the rollover time expires, only the new password is allowed.

Before this enhancement, an administrator normally took the application down when the application database password was being rotated. This is because the password update requires changes on both the database and the application side. With the gradual database password rollover enhancement, the application can continue to use the older password until the new password is configured in the application.

In addition to the new clause `PASSWORD_ROLLOVER_TIME` in the `CREATE PROFILE` and `ALTER PROFILE` statements, the `ALTER USER` statement has a new clause, `EXPIRE PASSWORD ROLLOVER PERIOD`. The `ACCOUNT_STATUS` column of the `DBA_USERS` and `USER_USERS` data dictionary views have several new statuses indicating values to indicate rollover status.

**Related Topics**

- [Managing Gradual Database Password Rollover for Applications](configuring-authentication.md)

**Parent topic:** Updates to Oracle Database Security 19c

#### Ability to Use Multiple Kerberos Principals with a Single Database Client

Available for Oracle Database release 19.10, when you configure Kerberos authentication for an Oracle Database client, you can specify multiple Kerberos principals with a single Oracle Database client.

To enable this functionality, you will need to create a separate credential cache for each user in the client and then use the connect string to specify the user.

In previous releases, you were restricted to one Kerberos principal for each Oracle Database client.

**Related Topics**

- [Step 1C: Optionally, Specify Additional Kerberos Principals Using tnsnames.ora](configuring-kerberos-authentication.md)
- [Oracle Database Net Services Reference](../netrf/local-naming-parameters-in-tns-ora-file.md)

**Parent topic:** Updates to Oracle Database Security 19c

#### Updated Support for Micro Edition Suite (MES) for FIPS 140.2

Available for Oracle Database release 19.10, Oracle Database supports Micro Edition Suite (MES) version 4.5 for FIPS 140.2.

The Micro Edition Suite (MES) version 4.5 updates include four new CVEs in the RSA BSAFE MES library, support for the rules that FIPS 140.2 requires, and access to the updated NZ/ZT library from the Crypto Foundation.

This enhancement enables the Oracle Database FIPS 140.2 configuration to benefit from new features and security improvements available from the latest RSA BSAFE MES library.

**Related Topics**

- [Configuring FIPS 140-2 for Transparent Data Encryption and DBMS_CRYPTO](oracle-database-fips-140-settings.md)

**Parent topic:** Updates to Oracle Database Security 19c

#### Support for DBMS_CRYPTO Asymmetric Key Operations

Available for Oracle Database release 19.9, the `DBMS_CRYPTO` PL/SQL package supports asymmetric key operations, in addition to the existing support for symmetric key operations.

To implement the support for asymmetric key operations, the following procedures have been added to the `DBMS_CRYPTO` package:

- `PKENCRYPT`
- `PKDECRYPT`
- `SIGN`
- `VERIFY`

**Related Topics**

- [Asymmetric Key Operations with the DBMS_CRYPTO Package](manually-encrypting-data.md)
- [Oracle Database PL/SQL Packages and Types Reference](../arpls/index.md)

**Parent topic:** Updates to Oracle Database Security 19c

#### SYSLOG Destination for Common Unified Audit Policies

Available with Oracle Database release 19.9, certain predefined columns of unified audit records from common unified audit policies can be written to the UNIX SYSLOG destination.

To enable this feature, you set `UNIFIED_AUDIT_COMMON_SYSTEMLOG`, a new CDB level `init.ora` parameter. This enhancement enables all audit records from common unified audit policies to be consolidated into a single destination.

This feature is available only on UNIX platforms, not Windows.

**Related Topics**

- [Enabling SYSLOG and Windows Event Viewer Captures for the Unified Audit Trail](administering-the-audit-trail.md)

**Parent topic:** Updates to Oracle Database Security 19c

#### Security Update for Native Encryption

Oracle provides a patch that you can download to address necessary security enhancements that affect native network encryption environments in Oracle Database release 11.2 and later.

This patch is available in My Oracle Support note [2118136.2](https://support.oracle.com/CSP/main/article?cmd=show&amp;type=NOT&amp;id=2118136.2).

The supported algorithms that have been improved are as follows:

- Encryption algorithms: AES128, AES192 and AES256
- Checksumming algorithms: SHA1, SHA256, SHA384, and SHA512

Algorithms that are deprecated and should not be used are as follows:

- Encryption algorithms: DES, DES40, 3DES112, 3DES168, RC4_40, RC4_56, RC4_128, and RC4_256
- Checksumming algorithm: MD5

If your site requires the use of network native encryption, then you must download the patch that is described in My Oracle Support note [2118136.2](https://support.oracle.com/CSP/main/article?cmd=show&amp;type=NOT&amp;id=2118136.2). To enable a smooth transition for your Oracle Database installation, this patch provides two parameters that enable you to disable the weaker algorithms and start using the stronger algorithms. You will need to install this patch on both servers and clients in your Oracle Database installation.

An alternative to network native encryption is Transport Layer Security (TLS), which provides protection against person-in-the-middle attacks.

**Related Topics**

- [Choosing Between Native Network Encryption and Transport Layer Security](configuring-network-data-encryption-and-integrity.md)
- [Improving Native Network Encryption Security](configuring-network-data-encryption-and-integrity.md)

**Parent topic:** Updates to Oracle Database Security 19c

#### Ability to Configure Transport Layer Security Connections without Client Wallets

Available in Oracle Database release 19.14, an Oracle Database client will not be required to provide a wallet to hold well-known CA root certificates if they are available elsewhere in the local system.

Transport Layer Security (TLS) encryption requires either one-way authentication or two-way authentication. In one-way authentication (the default), which is commonly used for HTTPS connections, the server certificate is verified using well-known root CA certificates that are already available in local systems. Starting in this release, you will no longer need to install and configure a wallet to hold a well-known root certificate if it is already available in the local system.

This enhancement greatly simplifies the Oracle Database client installation and the use of TLS protocol to encrypt Oracle Database client-server communications.

**Related Topics**

- [Transport Layer Security Connection without a Client Wallet](configuring-secure-sockets-layer-authentication.md)

**Parent topic:** Updates to Oracle Database Security 19c

#### SSL_ALLOW_WEAK_DN_MATCH Parameter to Control the Behavior of SSL_SERVER_DN_MATCH

Available with Oracle Database release 19.23, you can use the `SSL_ALLOW_WEAK_DN_MATCH` parameter to control how `SSL_SERVER_DN_MATCH` allows the service name for partial distinguished name matching and to only check the database server certificate.

In this release, the behavior of the `SSL_SERVER_DN_MATCH` parameter has changed. Previously, only the database server certificate was checked for DN matching. With this release, the listener and server certificates are both checked. Also, the `SERVICE_NAME` setting in the connect string is not used to check during a partial DN match. The `HOSTNAME` setting can still be used for partial DN matching with the certificate DN and subject alternative name (SAN), on both the listener and server certificates. When set to `TRUE`, the `SSL_ALLOW_WEAK_DN_MATCH` parameter reverts `SSL_SERVER_DN_MATCH` to the older, pre-release 19c behavior and enables DN matching to only check the database server certificate (but not the listener) and enable the service name to be used for partial DN matching.

DN matching with both the listener and server certificates provides better security to ensure that the client is connecting to the correct database server. The service name setting is also removed from `SSL_SERVER_DN_MATCH` for better security and partial DN matching can still be performed with the host name connect string parameter with the certificate common names (CN) and subject alternative name (SAN) matching.

The `SSL_ALLOW_WEAK_DN_MATCH`, though new to this release, is marked as deprecated because it is considered a temporary solution.

**Related Topics**

- [Use of the SSL_ALLOW_WEAK_DN_MATCH Parameter to Control SSL_SERVER_DN_MATCH](configuring-secure-sockets-layer-authentication.md)

**Parent topic:** Updates to Oracle Database Security 19c
