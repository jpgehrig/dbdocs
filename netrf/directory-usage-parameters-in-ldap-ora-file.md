## 9 Directory Usage Parameters in the ldap.ora File

This chapter provides a complete listing of the `ldap.ora` file configuration parameters.

- Overview of Directory Server Usage File
  The `ldap.ora` file contains directory usage configuration parameters created by Oracle Internet Directory Configuration Assistant, or Oracle Net Configuration Assistant. Do not modify these parameters or their settings.
- Directory Usage Parameters
  This section lists and describes the following `ldap.ora` file configuration parameters.

### 9.1 Overview of Directory Server Usage File

The `ldap.ora` file contains directory usage configuration parameters created by Oracle Internet Directory Configuration Assistant, or Oracle Net Configuration Assistant. Do not modify these parameters or their settings.

When created with Oracle Internet Directory Configuration Assistant, `ldap.ora` is located in the `ORACLE_HOME/ldap/admin` directory. When created with Oracle Net Configuration Assistant, the `ldap.ora` file is located in the `ORACLE_HOME/network/admin` directory. The `ldap.ora` file can also be stored in the directory specified by the `LDAP_ADMIN` or `TNS_ADMIN` environment variable.

**Related Topics**

- [Oracle Internet Directory](glossary.md)
- [Oracle Net Configuration Assistant](glossary.md)

**Parent topic:** Directory Usage Parameters in the ldap.ora File

### 9.2 Directory Usage Parameters

This section lists and describes the following `ldap.ora` file configuration parameters.

- DEFAULT_ADMIN_CONTEXT
  `DEFAULT_ADMIN_CONTEXT ldap.ora` file configuration parameter specifies the default directory for the creation, modification, or search of the connect identifiers.
- DIRECTORY_SERVER_TYPE
  `DIRECTORY_SERVER_TYPE` is a networking parameter of the`ldap.ora` file and it specifies the type of directory server that is being used.
- DIRECTORY_SERVERS
  `DIRECTORY_SERVERS` is a directory usage parameter and it lists the host names and port number of the primary and alternate LDAP directory servers.

**Parent topic:** Directory Usage Parameters in the ldap.ora File

#### 9.2.1 DEFAULT_ADMIN_CONTEXT

`DEFAULT_ADMIN_CONTEXT ldap.ora` file configuration parameter specifies the default directory for the creation, modification, or search of the connect identifiers.

##### Purpose

To specify the default directory entry that contains an Oracle Context from which connect identifiers can be created, modified, or looked up.

##### Values

Valid distinguished name (DN)

Example 9-1 Example

`DEFAULT_ADMIN_CONTEXT="o=OracleSoftware,c=US"`

**Parent topic:** Directory Usage Parameters

#### 9.2.2 DIRECTORY_SERVER_TYPE

`DIRECTORY_SERVER_TYPE` is a networking parameter of the`ldap.ora` file and it specifies the type of directory server that is being used.

##### Purpose

To specify the type of directory server that is being used.

##### Values

- `oid` for Oracle Internet Directory

- `ad` for Microsoft Active Directory

Example 9-2 Example

`DIRECTORY_SERVER_TYPE=oid`

**Parent topic:** Directory Usage Parameters

#### 9.2.3 DIRECTORY_SERVERS

`DIRECTORY_SERVERS` is a directory usage parameter and it lists the host names and port number of the primary and alternate LDAP directory servers.

##### Purpose

To list the host names and port number of the primary and alternate LDAP directory servers.

##### Values

host:port\[:sslport\]

Example 9-3 Example

`DIRECTORY_SERVERS=(ldap-server1:389:636, ldap-server2:389:636)`

**Parent topic:** Directory Usage Parameters
