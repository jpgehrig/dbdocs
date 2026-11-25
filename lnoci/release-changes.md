This preface contains:

- Changes in Oracle Database release 19c, version 19.13

### Changes in Oracle Database Release 19c

The following are changes in this book for Oracle Database release 19c.

#### New Features

The following new features are included in this release:

- Identity Access Management Integration with Oracle Autonomous Cloud Databases:

  Available for Oracle Database release 19.13, Identity Access Management (IAM) users can log in to an Oracle Autonomous Database on Shared Exadata Infrastructure using either password or token-based authentication.

  An IAM ADMIN user can configure both the authentication and authorization of IAM users and IAM groups. The IAM user can log in to the Oracle Autonomous Database using tools such as SQL\*Plus or SQLcl.

  See
  - [Identity and Access Management (IAM) Token-Based Authentication](introduction.md)
  - [TAF Support for IAM Based Token Authentication in OCI](high-availability-in-oci.md)
  - [Failover Callback Structure and Parameters](high-availability-in-oci.md)
  - [Authentication Information Handle Attributes](handle-and-descriptor-attributes.md)

- TLS Support : The TCP/IP with Transport Layer Security (TLS) protocol enables an Oracle application on a client to communicate with remote databases through TCP/IP and TLS.

  Oracle Database supports mutual or two-way TLS (mTLS) and one-way TLS authentication.

  See [About TCP/IP with SSL Protocol](../netag/understanding-communication-layers.md)

<!-- -->

- Oracle Database release 19.16 supports the following:
  - Azure AD integration is now supported with ADBS (Oracle Autonomous Database on Shared Exadata Infrastructure), ADBD (Oracle Autonomous Database on Dedicated Exadata Infrastructure), Oracle Database (On-Premises).
  - Database Identity and Access Management (IAM) - (OCI IAM) is now supported with ADBS (Oracle Autonomous Database on Shared Exadata Infrastructure), ADBD (Oracle Autonomous Database on Dedicated Exadata Infrastructure), Oracle Base Database Service
