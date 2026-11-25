This appendix lists the steps involved in integrating Enterprise User Security with Microsoft Active Directory using kerberos for authentication. It includes the following sections:

- About Direct Integration with Microsoft Active Directory

- Set Up Synchronization Between Active Directory and Oracle Internet Directory

- Set Up Active Directory to Interoperate with Oracle Client

- Set Up Oracle Database to Interoperate with Microsoft Active Directory

- Set Up Oracle Database Client to Interoperate with Microsoft Active Directory

- Obtain an Initial Ticket for the Client

- Configure Enterprise User Security for Kerberos Authentication

### C.1 About Direct Integration with Microsoft Active Directory

Oracle Database release 18c, version 18.1 and later supports direct integration with Microsoft Active Directory (MSAD) using the new centrally managed users capability.

Beginning with Oracle Database release 18c, version 18.1, Oracle Database introduces centrally managed users to authenticate and authorize users directly with Microsoft Active Directory. With centrally managed users, users accessing the database can be centrally managed to improve an organization's security posture. An enterprise user (a user in Microsoft Active Directory) can be exclusively mapped to a database account, or many enterprise users (in an Microsoft Active Directory group) can be mapped to a shared account in the database. Microsoft Active Directory groups can also be mapped to a database global role, which provides users with additional privileges and roles above what their login account (exclusive or shared) is granted. With centrally managed users, users can be authenticated with passwords, and Kerberos and PKI certificates.

For organizations beginning new directory services projects that do not require some of the more complex Enterprise User Security features like trusted database links, centrally managed users with Microsoft Active Directory allows you to use their current Microsoft Active Directory service as their centralized user management and centralized database access authorization. For new directory services projects, this may be the preferred option in implementing directory services as this reduces complexity as well as costs of operation in terms of maintenance and development.

Enterprise users can also make use of Oracle Internet Directory, which is a part of the Oracle Identity Management infrastructure. If your organization uses a third party directory like Microsoft Active Directory to store and manage user entries, then you can integrate it with Oracle Internet Directory to manage Enterprise User Security. This may be your preferred option if your organization requires some of the more complex Enterprise User Security features like trusted database links.

**See Also:**

[Oracle Database Security Guide](../dbseg/integrating_mads_with_oracle_database.md) for details about configuring centrally managed users with Microsoft Active Directory.

### C.2 Set Up Synchronization Between Active Directory and Oracle Internet Directory

Oracle components make use of Oracle Internet Directory for centralized security administration. Your organization might have a Microsoft Windows domain that uses Microsoft Active Directory for centralized administration. You should set up synchronization between Oracle Internet Directory and Microsoft Active Directory before you configure Enterprise User Security to work with Microsoft Active Directory.

Synchronization profiles are used to synchronize the two directories. The profile contains configuration information required to synchronize the two directories. This includes direction of synchronization, mapping rules and formats, connection details of Microsoft Windows domain and the like. Mapping rules contain domain rules and attribute rules to map a domain and attributes in one directory to the other directory, optionally formatting the attributes.

**See Also:**

For step-by-step instructions on integrating Oracle Internet Directory with Microsoft Active Directory, refer to the [Oracle Identity Management Integration Guide](https://docs.oracle.com/pls/topic/lookup?ctx=en/database/oracle/oracle-database/19/dbimi&id=OIMIG1930)

### C.3 Set Up Active Directory to Interoperate with Oracle Client

The following tasks must be performed on the Windows domain controller:

1.  Create the Oracle Database Principal in Microsoft Active Directory.
    This creates a new user for the database in Microsoft Active Directory.
2.  Use the `okcreate` command-line utility to automate the creation of the service principal `keytab` file.
    Beginning with Oracle Database 12c Release 2 (12.2), the `okcreate` utility provides for automation of service principal keytab creation on the Key Distribution Center (KDC) to create all service keytabs that setup requires. To use an Active Directory as a KDC, this requires the `keytab` file. If the Oracle client does not have a `keytab` file in the location specified by `SQLNET.KERBEROS5_CONF`, it uses a generic `krb5.conf` file. In this case, it detects realm and KDC settings from DNS. This utility takes input about the keytabs to create and output them to a specified location. The inputs taken are the service name (defaults to oracle) and a list of hostnames on which the database server is installed.

**See Also:**

[Oracle Database Security Guide](../dbseg/configuring-kerberos-authentication.md) for a detailed listing of the preceding steps.

### C.4 Set Up Oracle Database to Interoperate with Microsoft Active Directory

The following task must be performed on the host computer where Oracle Database is installed:

- Update the `sqlnet.ora` file in the database with kerberos parameters

**See Also:**

[Oracle Database Security Guide](../dbseg/configuring-kerberos-authentication.md) for a detailed description of the preceding step.

### C.5 Set Up Oracle Database Client to Interoperate with Microsoft Active Directory

The following steps must be performed on the Oracle kerberos client:

1.  Create client kerberos configuration files
    The client kerberos configuration files refer to the Microsoft Active Directory as the kerberos KDC.
2.  Specify kerberos parameters in the client `sqlnet.ora` file
    You can either manually update the file or use Oracle Net Manager utility.

**See Also:**

[Oracle Database Security Guide](../dbseg/configuring-kerberos-authentication.md) for a detailed listing of the preceding steps.

### C.6 Obtain an Initial Ticket for the Client

Before a client can connect to the database, the client must request for an initial ticket. The initial ticket identifies the client as having the rights to ask for additional service tickets. An initial ticket is requested using the `okinit` command.

**See Also:**

[Oracle Database Security Guide](../dbseg/configuring-kerberos-authentication.md) for more details on requesting an initial ticket with `okinit`.

### C.7 Configure Enterprise User Security for Kerberos Authentication

To configure Enterprise User Security for Kerberos Authentication, use the following steps:

1.  Register the database in Oracle Internet Directory
    You can use Database Configuration Assistant for registering the database.
2.  Configure Enterprise User Security Objects in the database and Oracle Internet Directory
    Create global schemas and global roles in the database. Also create enterprise roles in the enterprise domain. Configure user schema mappings for the enterprise domain, add global database roles to enterprise roles and grant enterprise roles to enterprise users for database access.
3.  Configure the enterprise domain to accept kerberos authentication
    Use Oracle Enterprise Manager to enable kerberos authentication for your enterprise domain.
4.  Connect as kerberos authenticated enterprise user.
    Launch SQL\*Plus and use the command, `connect /@``net_service_name` to connect as a kerberos authenticated enterprise user.

**See Also:**

For detailed information on the preceding steps, refer to "[Configuring Enterprise User Security for Kerberos Authentication](enterprise-user-security-configuration-tasks-and-troubleshooting.md)" .
