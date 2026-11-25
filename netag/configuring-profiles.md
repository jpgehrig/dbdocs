## 12 Configuring Profiles

Learn how to configure client and server configuration parameters in profiles. A profile is a collection of parameters that specifies preferences for enabling and configuring Oracle Net features on the client or database server.

A profile is stored and implemented through the `sqlnet.ora` file.

- Overview of Profile Configuration
- Configuring the Profile During Installation
- Understanding Client Attributes for Names Resolution
- Settings for Database Access Control
- About Advanced Profile Information
  These are the advanced `sqlnet.ora` file settings that you can set.
- Configuring External Naming Methods
- Configuring Oracle Network Security
  Oracle network security features enable data encryption, integrity checking, enhanced authentication, and single sign-on. The features also provide centralized user management on LDAP-compliant directory servers and certificate-based single sign-on. This functionality relies on the Transport Layer Security (TLS) protocol.

**Parent topic:** [Configuration and Administration of Oracle Net Services](part-II-config-and-admin-of-oracle-net-services.md)

### 12.1 Overview of Profile Configuration

You can use a profile to do the following:

- Specify the client domain to append to unqualified names

- Prioritize naming methods

- Enable logging and tracing features

- Route connections through specific processes

- Configure parameters for an external procedure

- Configure Oracle Advanced Security

- Use protocol-specific parameters to restrict access to the database

**Parent topic:** Configuring Profiles

### 12.2 Configuring the Profile During Installation

Oracle Universal Installer launches [Oracle Net Configuration Assistant](glossary.md) after software installation on the client and server. Oracle Net Configuration Assistant configures the order of the naming methods that the computer uses to resolve a [connect identifier](glossary.md) to a [connect descriptor](glossary.md)

Configuration with the Oracle Net Configuration Assistant during installation results in an entry in the `sqlnet.ora` file similar to the following:

    NAMES.DIRECTORY_PATH=(ezconnect,tnsnames)

The NAMES.DIRECTORY_PATH parameter specifies the priority order of the naming methods to use to resolve connect identifiers. If the installed configuration is not adequate, then use [Oracle Net Manager](glossary.md) to change the `sqlnet.ora` configuration.

**Parent topic:** Configuring Profiles

### 12.3 Understanding Client Attributes for Names Resolution

The following sections describe available client configuration options:

- About the Default Domain for Clients
- Prioritizing Naming Methods
- Routing Connection Requests to a Process

**Parent topic:** Configuring Profiles

#### 12.3.1 About the Default Domain for Clients

In environments where the client often requests names from a specific domain, it is appropriate to set a default domain in the client `sqlnet.ora` file with the NAMES.DEFAULT_DOMAIN parameter. This parameter is available to the local and external naming methods.

When a default domain is set, it is automatically appended to any unqualified network service name given in the connect string, and then compared to network service names stored in a `tnsnames.ora` file.

For example, if the client `tnsnames.ora` file contains a network service name of `sales.us.example.com`, and the default domain is `us.example.com`, then the user can enter the following connect string:

    CONNECT scott@sales
    Enter password: password

In the preceding example, `sales` gets searched as `sales.us.example.com`.

If the connect string includes the domain extension, such as in `CONNECT scott@sales.us.example.com`, then the domain is not appended.

If a network service name in a `tnsnames.ora` file is not domain qualified and the NAMES.DEFAULT_DOMAIN parameter is set, then the network service name must be entered with a period (`.`) at the end of the name. For example, if the domain is set to `us.example.com` and the client `tnsnames.ora` file contains a network service name of `sales2`, then the user would enter the following connect string:

    CONNECT scott@sales2.
    Enter password: password

In the preceding example, the client would connect to `sales2`, not `sales2.us.example.com`.

- Specifying a Default Domain

**Parent topic:** Understanding Client Attributes for Names Resolution

##### 12.3.1.1 Specifying a Default Domain

The following procedure describes how to specify a default domain:

1.  Start Oracle Net Manager.

    **See Also:**

    "[Using Oracle Net Manager to Configure Oracle Net Services](managing-oracle-net-services.md)"

2.  In the navigator pane, select Profile from the Local menu.

3.  From the list in the right pane, select Naming.

4.  Click the Methods tab.

5.  In the Default Domain field, enter the domain.

6.  Select Save Network Configuration from the File menu.

    The `sqlnet.ora` file should contain an entry that looks similar to the following:

        NAMES.DEFAULT_DOMAIN=us.example.com

**Parent topic:** About the Default Domain for Clients

#### 12.3.2 Prioritizing Naming Methods

After naming methods are configured, as described in [Configuring Naming Methods](configuring-naming-methods.md), they must be prioritized. Naming methods to resolve a connect identifier are tried in the order they appear in the list. If the first naming method in the list cannot resolve the connect identifier, then the second method in the list is used, and so on.

The following procedure describes how to specify the order of naming methods:

1.  Start Oracle Net Manager.

    **See Also:**

    "[Using Oracle Net Manager to Configure Oracle Net Services](managing-oracle-net-services.md)"

2.  In the navigator pane, select Profile from the Local menu.

3.  From the list in the right pane, select Naming.

4.  Click the Methods tab.

    Table 12-1 describes the naming method values listed in the Methods tab.

    Table 12-1 Naming Method Values

    | Naming Method Value | Description                                                                                                                                                                                                                                                                                                                                |
    |:--------------------|:-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | TNSNAMES            | Resolve a [network service name](glossary.md) through the `tnsnames.ora` file on the client.<br>See Also: "[Configuring the Local Naming Method](configuring-naming-methods.md)"                                                                                                                                                           |
    | LDAP                | Resolve a database service name, network service name, or [network service alias](glossary.md) through a [directory server](glossary.md).<br>See Also: "[Configuring the Directory Naming Method](configuring-naming-methods.md)"                                                                                                          |
    | EZCONNECT           | Enable clients to use a TCP/IP connect identifier, consisting of a host name and optional port and service name, or resolve a host name alias through an existing names resolution service or centrally maintained set of `/etc/hosts` files.<br>See Also: "[Understanding the Easy Connect Naming Method](configuring-naming-methods.md)" |
    | NIS                 | Resolve service information through an existing network information service (NIS).                                                                                                                                                                                                                                                         |

5.  Select naming methods from the Available Methods list, and then click the right-arrow button.

    The selected naming methods move to the Selected Methods list.

6.  Order the naming methods according to the order in which you want Oracle Net to try to resolve the network service name or database service name. Select a naming method in the Selected Methods list, and then click Promote or Demote to move the selection up or down in the list.

7.  Select Save Network Configuration from the File menu.

    The `sqlnet.ora` file updates with the NAMES.DIRECTORY_PATH parameter, such as the following:

        NAMES.DIRECTORY_PATH=(ldap, tnsnames)

**Parent topic:** Understanding Client Attributes for Names Resolution

#### 12.3.3 Routing Connection Requests to a Process

Clients and servers can be configured so connection requests are directed to a specific process. The following procedure describes how to route connection requests to a process:

1.  Start Oracle Net Manager.

    **See Also:**

    "[Using Oracle Net Manager to Configure Oracle Net Services](managing-oracle-net-services.md)"

2.  In the navigator pane, select Profile from the Local menu.

3.  From the list in the right pane, select General.

4.  Click the Routing tab.

5.  Select the preferred way for routing connections.

    **Note:**

    To configure all connections to use a particular server, you select the Always Use Dedicated Server option in Oracle Net Manager. This sets the USE_DEDICATED_SERVER parameter in the `sqlnet.ora` file to force the listener to spawn a dedicated server for all network sessions from the client. The result is a dedicated server connection, even if a shared server is configured.

6.  Choose Save Network Configuration from the File menu.

**See Also:**

Table 12-3 for a description of the fields and options

**Parent topic:** Understanding Client Attributes for Names Resolution

### 12.4 Settings for Database Access Control

You can configure the `sqlnet.ora` file to allow access to some clients and deny access to others. Table 12-2 describes the available settings.

Table 12-2 Access Control Settings in sqlnet.ora

| Oracle Net Manager Field/Option   | sqlnet.ora File Parameter | Description                                                                                                                                                                                                                                                                                                      |
|:----------------------------------|:--------------------------|:-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Check TCP/IP client access rights | TCP.VALIDNODE_CHECKING    | Specify whether to screen access to the database.<br>If this field is selected, then Oracle Net Manager checks the parameters TCP.EXCLUDED_NODES and TCP.INVITED_NODES to determine which clients to allow access to the database. If this field is deselected, then Oracle Net Manager does not screen clients. |
| Clients excluded from access      | TCP.EXCLUDED_NODES        | Specify which clients using the TCP/IP protocol are excluded access to the database.                                                                                                                                                                                                                             |
| Clients allowed access            | TCP.INVITED_NODES         | Specify which clients using the TCP/IP protocol are allowed access to the database.                                                                                                                                                                                                                              |

If the TCP.INVITED_NODES parameter does not include the listener node, then the Listener Control utility cannot connect to the listener. This will prevent start, stop and administration commands from being performed on the listener.

If there are invalid host names or IP addresses listed in the TCP.INVITED_NODES parameter or the TCP.EXCLUDED_NODES parameter, then the Listener Control utility cannot contact the listener.

- Configuring Database Access Control

**Parent topic:** Configuring Profiles

#### 12.4.1 Configuring Database Access Control

The following procedure describes how to configure database access control:

1.  Start Oracle Net Manager.

    **See Also:**

    "[Using Oracle Net Manager to Configure Oracle Net Services](managing-oracle-net-services.md)"

2.  In the navigator pane, select Profile from the Local menu.

3.  From the list in the right pane, select General.

4.  Click the Access Rights tab.

5.  Select the Check TCP/IP client access rights option.

6.  In the Clients allowed to access fields and Clients excluded from access field, enter either a host name or an IP address for a client that you want to include or exclude, using commas to delimit entries placed on the same line.

**Parent topic:** Settings for Database Access Control

### 12.5 About Advanced Profile Information

These are the advanced `sqlnet.ora` file settings that you can set.

Table 12-3 Advanced Settings in sqlnet.ora

| Oracle Net Manager Field/Option       | sqlnet.ora File Parameter                                                      | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      |
|:--------------------------------------|:-------------------------------------------------------------------------------|:-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Send operation Time Out               | `SQLNET.SEND_TIMEOUT`                                                          | Specify the time, in ms, seconds, or minutes, for a database client or server to wait for data from the peer after establishing a connection.<br>Setting this parameter for clients ensure that receive operation is not left in wait state indefinitely or for a long period due to an unusual termination of server process or server busy state. If a client does not receive response data in time specified, then it logs `ORA-12535: TNS:operation timed out` and `ORA-12609: TNS: Receive timeout occurred ` errors in the `sqlnet.log` file.<br>You can also set this parameter on the server-side to specify the time, in ms, sec, or min, for a server to wait for client data after connection establishment. If a client does not send any data in the specified time, then the database server logs `ORA-12535: TNS:operation timed out `and `ORA-12609: TNS: Receive timeout occurred` messages to the `sqlnet.log` file. Without this parameter, the database server may continue to wait for data from clients that may be down or are experiencing difficulties. The server usually blocks on input from the client and gets these timeouts frequently if set to a low value.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   |
| Receive operation Time Out            | `SQLNET.RECV_TIMEOUT`                                                          | Specify the time, in seconds, for a database server to wait for client data after connection establishment. A client must send some data within the specified time interval.<br>Setting this parameter is recommended for environments in which clients shut down unusually. If a client does not send any data in the time specified, then the database server logs `ORA-12535: TNS:operation timed out` and `ORA-12609: TNS: Receive timeout occurred` errors to the `sqlnet.log` file.<br>Without this parameter, the database server continues to wait for data from clients that may be down or are experiencing difficulties.<br>You can also use this setting on the client side to specify the time, in seconds, for a client to wait for response data from the database server after connection establishment. Without this parameter, the client may wait for a long period of time for a response from a database server overwhelmed with requests.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  |
| Connection Time Out                   | `SQLNET.INBOUND_CONNECT_TIMEOUT`                                               | Specify the time, in seconds, for a client to connect with the database server and provide the necessary authentication information.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             |
| Total Send Buffer Size                | `SEND_BUF_SIZE`                                                                | Specify the buffer space limit for send operations of sessions.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  |
| Total Receive Buffer Size             | `RECV_BUF_SIZE`                                                                | Specify the buffer space limit for receive operations of sessions.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                               |
| TNS Time Out Value                    | `SQLNET.EXPIRE_TIME`                                                           | Specify the time interval, in minutes, to send a probe to verify that client/server connections are active. Setting a value greater than 0 ensures that connections are not left open indefinitely, due to an unusual client termination. If the probe finds a terminated connection, or a connection that is no longer in use, then it returns an error, causing the server process to exit. This setting is intended for the database server, which typically handles multiple connections at any one time.<br>Limitations on using this terminated connection detection feature are:<br>• It is not allowed on bequeathed connections.<br>• Even though it is very small, the probe packet generates additional traffic that may downgrade network performance.<br>• Depending on which operating system is in use, the server may need to perform additional processing to distinguish the connection probing event from other events that occur. This can also result in downgrading network performance.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   |
| Client Registration ID                | `SQLNET.CLIENT_REGISTRATION`                                                   | Specify a unique identifier for a client. This identifier is passed to the listener with any connection request. The identifier can be any string up to 128 characters long.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                     |
| Logon Authentication Protocol Version | `SQLNET.ALLOWED_LOGON_VERSION_CLIENT`<br>`SQLNET.ALLOWED_LOGON_VERSION_SERVER` | Define the minimum authentication protocol allowed when connecting to Oracle Database instances. The term `VERSION` in the parameter name refers to the version of the authentication protocol, not the Oracle Database release. If the client or server does not meet the minimum release specified by its partner, then authentication fails with an `ORA-28040` error.<br>Supported values include:<br>• `12a` for Oracle Database 12c authentication protocols (strongest protection)<br>• `12` for the critical patch updates CPUOct2012 and later Oracle Database 11g authentication protocols (recommended)<br>• `11` for Oracle Database 11g authentication protocols<br>• `10` for Oracle Database 10g authentication protocols<br>• `9` for Oracle9i Database authentication protocol<br>• `8` for Oracle8i Database authentication protocol<br>The default value is `12` or `12a`. Note the following implications of setting the value to `11` or `12`:<br>• The setting `SEC_CASE_SENSITIVE_LOGON=FALSE` must not be used. If it is set as `FALSE`, then user accounts and secure roles become unusable. The `SEC_CASE_SENSITIVE_LOGON` initialization parameter enables or disables case sensitivity for passwords.<br>• To take advantage of the password protections introduced in Oracle Database 11g, users must change their passwords.<br>• Releases of OCI clients before Oracle Database 10g and all versions of JDBC thin clients cannot authenticate to the Oracle database using password-based authentication.<br>When an Oracle Database 12c server has a database link to a server running an earlier Oracle Database release, set the value of the `SQLNET.ALLOWED_LOGON_VERSION_CLIENT` parameter on the Oracle Database 12c server to match the `SQLNET.ALLOWED_LOGON_VERSION` setting of the server running the earlier release. |
| Turn Off UNIX Signal Handling         | `BEQUEATH_DETACH`                                                              | Turn on or off UNIX signal handling.<br>Because the client application spawns a server process internally through the bequeath protocol as a child process, the client application becomes responsible for cleaning up the child process when it completes. When the server process completes its connection responsibilities, it becomes a terminated process. Signal handlers are responsible for cleaning up these terminated processes. Setting this parameter configures the client profile to pass this process to the UNIX initialization process by disabling signal handlers.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           |
| Disable Out-of-Band Break             | `DISABLE_OOB`                                                                  | Turn on or off out-of-band breaks.<br>If deselected or set to `off`, then Oracle Net can send and receive break messages using urgent data requests provided by the underlying protocol. Once enabled, this feature applies to all protocols used by this client.<br>If selected or set to `on`, then it disables the ability to send and receive break messages using urgent data requests of the underlying protocol.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          |
| Disable Out-of-Band Auto Break option | `DISABLE_OOB_AUTO`                                                             | Checks TCP OOB (Out of Band) support in client to server path at the connection time. The client enables OOB only if the server path supports OOB.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                               |

- Setting the Advanced Features in the sqlnet.ora File Using Oracle Net Services

**See Also:**

- "[Limiting Resource Consumption by Unauthorized Users](optimizing-performance.md)" for complete information about configuring the SQLNET.INBOUND_CONNECT_TIMEOUT setting

- "[Configuring I/O Buffer Space](optimizing-performance.md) " for complete information about configuring the SEND_BUF_SIZE and RECV_BUF_SIZE settings

- [Oracle Database Security Guide](../dbseg/configuring-authentication.md) for additional information about the SQLNET.ALLOWED_LOGON_VERSION_CLIENT and SQLNET.ALLOWED_LOGON_VERSION_SERVER settings

- [Oracle Database Net Services Reference](../netrf/parameters-for-the-sqlnet.ora.md) for additional information about the SQLNET.ALLOWED_LOGON_VERSION_CLIENT and SQLNET.ALLOWED_LOGON_VERSION_SERVER settings

- Oracle operating system-specific documentation to determine if the protocol supports urgent data requests. TCP/IP is an example of a protocol that supports this feature.

**Parent topic:** Configuring Profiles

#### 12.5.1 Setting the Advanced Features in the sqlnet.ora File Using Oracle Net Services

The following procedure describes how to set advanced features in the `sqlnet.ora` file:

1.  Start Oracle Net Manager.

    **See Also:**

    "[Using Oracle Net Manager to Configure Oracle Net Services](managing-oracle-net-services.md)"

2.  In the navigator pane, select Profile from the Local menu.

3.  From the list in the right pane, select General.

4.  Click the Advanced tab.

5.  Enter the values for the fields or options you want to set.

6.  Select Save Network Configuration from the File menu.

**Parent topic:** About Advanced Profile Information

### 12.6 Configuring External Naming Methods

The `sqlnet.ora` file is used to configure required client parameters needed for Network Information Service (NIS) external naming. The following procedure describes how to configure the NIS parameter in the `sqlnet.ora` file:

1.  Start Oracle Net Manager.

    **See Also:**

    "[Using Oracle Net Manager to Configure Oracle Net Services](managing-oracle-net-services.md)"

2.  In the navigator pane, select Profile from the File menu.

3.  From the list in the right pane, select Naming.

4.  Click the External tab.

5.  Enter `NAMES.NIS.META_MAP` in the Meta Map field.

6.  Select Save Network Configuration from the File menu.

**Parent topic:** Configuring Profiles

### 12.7 Configuring Oracle Network Security

Oracle network security features enable data encryption, integrity checking, enhanced authentication, and single sign-on. The features also provide centralized user management on LDAP-compliant directory servers and certificate-based single sign-on. This functionality relies on the Transport Layer Security (TLS) protocol.

The following procedure describes how to configure a client or server to use Oracle network security features:

1.  Start Oracle Net Manager.

2.  In the navigator pane, select Profile from the Local menu.

3.  From the list in the right pane, select Network Security.

    Each Network Security tab page enables you to configure a separate set of parameters. The tab pages are as follows:

    - Authentication: For configuration of available authentication methods, such as KERBEROS5 and RADIUS.

    - Other Params: For configuration of the authentication service.

    - Integrity: For configuration of the type of integrity, checksum level and available methods.

    - Encryption: For configuration of the encryption type and method.

    - TLS: For setting the use of TLS.

4.  Select or edit options as applicable.

5.  Select Save Network Configuration from the File menu.

**Note:**

For additional details, refer to the help button on a tab page or the network security topics in the Oracle Net Manager online help. To access the network security topics, select Network Security, and then select the How To option.

**Related Topics**

- Configuring Oracle Network Security
- [Oracle Database Security Guide](../dbseg/keeping-your-oracle-database-secure.md)

**Parent topic:** Configuring Profiles
