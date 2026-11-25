The gateway architecture involves multiple computer setups that have distinct security capabilities and limitations. This section provides information for planning and implementing your security system.

It contains the following sections:

- Security Overview

- Authenticating Application Logons

- Defining and Controlling Database Links

- Passwords in the Gateway Initialization File

### Security Overview

When you connect several different systems, generally the system with the strictest security requirements dictates and rules the system.

Gateway security involves two groups:

- Users and applications that are permitted access to a given gateway instance and DRDA database server

- Server database objects that users and applications are able to query and update

You can control access in the gateway architecture at several points. Each DRDA database server with `GRANT`s and related native authorization mechanisms based on user ID provides control over database object access.

When the gateway is involved in a SQL request, security mechanisms are in effect for each DRDA system component encountered by the gateway. The first system component encountered is the application tool or 3GL program. The last system component encountered is the DRDA database.

### Authenticating Application Logons

An application must connect to an Oracle database before using the gateway. The type of logon authentication that you use determines the resulting Oracle user ID and can affect gateway operation. There are two basic types of authentication:

- Oracle authentication: With Oracle authentication, each Oracle user ID has a password known to Oracle database. When an application connects to the server, it supplies a user ID and password. Oracle database confirms that the user ID exists and that the password matches the one kept in the database.

- Operating system authentication: With operating system authentication, the server's underlying operating system is responsible for authentication. An Oracle user ID that is created with the `IDENTIFIED EXTERNALLY` attribute, instead of a password, is accessed with operating system authentication. To log into such a user ID, the application supplies a forward slash ( / ) for a user ID and does not supply a password.

  To perform operating system authentication, the server determines the requester's operating system user ID, optionally adds a fixed prefix to it, and uses the result as the Oracle user ID. The server confirms that the user ID exists and is` IDENTIFIED EXTERNALLY`, but no password checking is done. The underlying assumption is that users were authenticated when they logged into the operating system.

  Operating system authentication is not available on all platforms and is not available in some `Oracle Net` (client-server) and multi-threaded server configurations. Refer to the Oracle Database Installation Guide 11g for UNIX Systems and Oracle Net documentation to determine the availability of this feature.

For more information about authenticating application logons, refer to the Oracle Database Reference.

### Defining and Controlling Database Links

The information here is specific to the gateway. For additional information on database links, refer to the Oracle Database Reference.

#### Link Accessibility

The database link should be accessible to a given user. Any user ID can use a public database link. Only the user who created it can use a private database link. The server makes no distinction regarding the type of use (such as read-only versus update or write) or accessibility of remote objects. The DRDA database, which is accessed, is responsible for these distinctions.

#### Links and CONNECT Clauses

The `CONNECT` clause is another security-related attribute of a database link. You can use the `CONNECT` clause to specify an explicit user ID and password, which can differ from the user's Oracle database user ID and password. This `CONNECT` user ID and password combination is sent to the gateway when the database link connection is first opened. Depending on gateway options, the gateway might send that user ID and password to the DRDA Server for validation.

If a database link is created without a `CONNECT` clause, then the user's Oracle database user ID and password are sent to the gateway when the connection is opened. If the user logs into the Oracle database with operating system authentication, then the gateway does not receive any user ID or password from the Oracle database. In this case, user ID mapping facilities at the DRDA Server can be used to make such a connection possible if all users on the same host can use the same DRDA database user ID.

### Passwords in the Gateway Initialization File

The gateway uses user IDs and passwords to access the information in the remote database on the DRDA Server. Some user IDs and passwords must be defined in the gateway initialization file to handle functions such as resource recovery. In the current security conscious environment, having plain‐text passwords that are accessible in the Initialization File is deemed insecure. An encryption feature has been added as part of Heterogeneous Services' generic connectivity to help make this more secure. This feature is accessible by this gateway. Initialization parameters that contain sensitive values might be stored in an encrypted form with it. Refer to [Section 4.2.3, 'Encrypting Initialization parameters'](../heter/initialization-parameters.md) in the Oracle Database Heterogeneous Connectivity User's Guide for more information about how to use the feature.

**See Also:**

The parameters `HS_FDS_RECOVERY_ACCOUNT` and `HS_FDS_RECOVERY_PWD` in [Initialization Parameters](init-param-gateway.md) as examples, for more information.
