## 5 Parameters for the sqlnet.ora File

This chapter provides a complete listing of the `sqlnet.ora` file configuration parameters.

- Overview of Profile Configuration File
- sqlnet.ora Profile Parameters
  These are the `sqlnet.ora` profile configuration parameters that you use to administer database clients and servers.
- ADR Diagnostic Parameters in sqlnet.ora
  Diagnostic data for critical errors is stored in the `sqlnet.ora` Automatic Diagnostic Repository (ADR).
- Non-ADR Diagnostic Parameters in sqlnet.ora Files
  Learn about `sqlnet.ora` parameters that you use when you disable ADR.

### 5.1 Overview of Profile Configuration File

The `sqlnet.ora` file is the profile configuration file. It resides on the client machines and the database server. Profiles are stored and implemented using this file. The database server can be configured with access control parameters in the `sqlnet.ora` file. These parameters specify whether clients are allowed or denied access based on the protocol.

The `sqlnet.ora` file enables you to do the following:

- Specify the client domain to append to unqualified names

- Prioritize naming methods

- Enable logging and tracing features

- Route connections through specific processes

- Configure parameters for external naming

- Configure Oracle Advanced Security

- Use protocol-specific parameters to restrict access to the database

By default, the `sqlnet.ora` file is located in the `ORACLE_HOME/network/admin` directory. The `sqlnet.ora` file can also be stored in the directory specified by the `TNS_ADMIN` environment variable.

**Note:**

- The settings in the `sqlnet.ora` file apply to all pluggable databases (PDBs) in a multitenant container database environment.

- Oracle Net Services supports the IFILE parameter in the `sqlnet.ora` file, with up to three levels of nesting. The parameter is added manually to the file. The following is an example of the syntax:

      IFILE=/tmp/listener_em.ora
      IFILE=/tmp/listener_cust1.ora
      IFILE=/tmp/listener_cust2.ora

  Refer to [Oracle Database Reference](../refrn/IFILE.md) for additional information.

- In the read-only Oracle home mode,, the `sqlnet.ora` file default location is `ORACLE_BASE_HOME``/network/admin`.

- In the read-only Oracle home mode, the parameters that default to `ORACLE_HOME` location change to default to `ORACLE_BASE_HOME` location.

**Parent topic:** Parameters for the sqlnet.ora File

### 5.2 sqlnet.ora Profile Parameters

These are the `sqlnet.ora` profile configuration parameters that you use to administer database clients and servers.

**Note:**

The SQLNET.ENCRYPTION_WALLET_LOCATION `sqlnet.ora` parameter is deprecated in Oracle Database 19c.

The `SQLNET.ENCRYPTION_WALLET_LOCATION` parameter defines the location of the software keystores for Transparent Data Encryption (TDE). To configure the software keystore location, instead of setting `SQLNET.ENCRYPTION_WALLET_LOCATION`, Oracle recommends that you set the `WALLET_ROOT` initialization parameter, and the `TDE_CONFIGURATION` dynamic initialization parameter.

These parameters are described in [Oracle Database Advanced Security Guide](../asoag/using-sqlnet-ora-to-configure-tde-keystores.md).

- ACCEPT_MD5_CERTS
  The `sqlnet.ora` profile parameter `ACCEPT_MD5_CERTS` accepts MD5 signed certificates.
- ACCEPT_SHA1_CERTS
- ADD_SSLV3_TO_DEFAULT
  The `sqlnet.ora` profile parameter `ADD_SSLV3_TO_DEFAULT` sets the Transport Layer Security (TLS) versions that your server accepts.
- BEQUEATH_DETACH
  Use the `sqlnet.ora` parameter to enable and disable signal handling on Linux and UNIX systems.
- DEFAULT_SDU_SIZE
  Use the `sqlnet.ora` profile parameter to specify the session data unit size (SDU) for connections.
- DISABLE_INTERRUPT
  Use the `sqlnet.ora` profile parameter `DISABLE_INTERRUPT` to disable Oracle Net handling of a `SIGINIT` signal in client applications.
- DISABLE_OOB
  DISABLE_OOB is a networking parameter of the sqlnet.ora file and is used to enable or disable Oracle Net to send or receive out-of-band break messages using urgent data provided by the underlying protocol.
- DISABLE_OOB_AUTO
  The `DISABLE_OOB_AUTO` networking parameter of the `sqlnet.ora` file checks the server path for out-of-band break messages support at the connection time.
- EXADIRECT_FLOW_CONTROL
- EXADIRECT_RECVPOLL
- IPC.KEYPATH
- MAX_CONDUITS
  Use the `sqlnet.ora` parameter `MAX_CONDUITS` to specify the maximum number of conduits between the listener and the broker or dispatcher for handing off client connections.
- NAMES.DEFAULT_DOMAIN
- NAMES.DIRECTORY_PATH
  Use the `sqlnet` parameter `NAMES.DIRECTORY_PATH` to specify the order of the naming methods for client name resolution lookups.
- NAMES.LDAP_AUTHENTICATE_BIND
- NAMES.LDAP_CONN_TIMEOUT
- NAMES.LDAP_PERSISTENT_SESSION
- NAMES.NIS.META_MAP
- OCI_COMPARTMENT
  Use the `OCI_COMPARTMENT` parameter to specify Oracle Cloud Identifier (OCID) of the compartment that holds database instances for client connections.
- OCI_DATABASE
  Use the `OCI_DATABASE` parameter to specify Oracle Cloud Identifier (OCID) of the database that you want to access for the client connection.
- OCI_IAM_URL
  Use the `OCI_IAM_URL` parameter to specify an endpoint URL that the database client must connect with to get the database token for authenticating Oracle Cloud Infrastructure (OCI) Identity and Access Management (IAM) users on OCI Database as a Service (DBaaS).
- OCI_TENANCY
  Use the `OCI_TENANCY` parameter to specify Oracle Cloud Identifier (OCID) of the user’s tenancy.
- PASSWORD_AUTH
  With this setting, client connections use the IAM user name and IAM database password for logging in users to the database.
- RECV_BUF_SIZE
  Use the `sqlnet.ora` parameter `RECV_BUF_SIZE` to specify buffer space limit for session receive operations.
- SDP.PF_INET_SDP
- SEC_USER_AUDIT_ACTION_BANNER
- SEC_USER_UNAUTHORIZED_ACCESS_BANNER
- SEND_BUF_SIZE
  Use the `sqlnet` parameter `SEND_BUF_SIZE` to specify the buffer space limit for session send operations.
- SQLNET.ALLOW_WEAK_CRYPTO
  Use the `sqlnet.ora` compatibility parameter `SQLNET.ALLOW_WEAK_CRYPTO` to configure your client-side network connection by reviewing the specified encryption and crypto-checksum algorithms.
- SQLNET.ALLOW_WEAK_CRYPTO_CLIENTS
  Use the `sqlnet.ora` compatibility parameter `SQLNET.ALLOW_WEAK_CRYPTO_CLIENTS` to configure your server-side network connection by reviewing the specified encryption and crypto-checksum algorithms.
- SQLNET.ALLOWED_LOGON_VERSION_CLIENT
  Use the `sqlnet` parameter `SQLNET.ALLOWED_LOGON_VERSION_CLIENT` to define minimum authentication protocols that servers acting as clients to other servers can use for connecting to Oracle Database instances.
- SQLNET.ALLOWED_LOGON_VERSION_SERVER
  Use the `sqlnet.ora` parameter `SQLNET.ALLOWED_LOGON_VERSION_SERVER` to set the minimum authentication protocol that is permitted when connecting to Oracle Database instances.
- SQLNET.AUTHENTICATION_SERVICES
  Use the `sqlnet.ora` parameter `SQLNET.AUTHENTICATION_SERVICES` to enable one or more authentication services.
- SQLNET.CLIENT_REGISTRATION
- SQLNET.CLOUD_USER
- SQLNET.COMPRESSION
- SQLNET.COMPRESSION_ACCELERATION
- SQLNET.COMPRESSION_LEVELS
- SQLNET.COMPRESSION_THRESHOLD
- SQLNET.CRYPTO_CHECKSUM_CLIENT
  Use the `sqlnet.ora` parameter `SQLNET.CRYPTO_CHECKSUM_CLIENT` to specify the desired data integrity behavior when this client or server acting as a client connects to a server.
- SQLNET.CRYPTO_CHECKSUM_SERVER
  Use the `sqlnet.ora` parameter `SQLNET.CRYPTO_CHECKSUM_SERVER` to specify the data integrity behavior when a client or another server acting as a client connects to this server.
- SQLNET.CRYPTO_CHECKSUM_TYPES_CLIENT
  Use the `sqlnet.ora` parameter `SQLNET.CRYPTO_CHECKSUM_TYPES_CLIENT` to specify a list of data integrity algorithms that this client or server acting as a client uses.
- SQLNET.CRYPTO_CHECKSUM_TYPES_SERVER
  Use the `sqlnet.ora` parameter `SQLNET.CRYPTO_CHECKSUM_TYPES_SERVER` to specify the data integrity algorithms that this server or client to another server uses, in order of intended use.
- SQLNET.DBFW_PUBLIC_KEY
- SQLNET.DOWN_HOSTS_TIMEOUT
- SQLNET.ENCRYPTION_CLIENT
  Use the `sqlnet.ora` parameter `SQLNET.ENCRYPTION_CLIENT` to set the encryption behavior when this client or server acting as a client connects to a server.
- SQLNET.ENCRYPTION_SERVER
  The `sqlnet.ora` parameter `SQLNET.ENCRYPTION_SERVER` specifies the encryption behavior when a client or a server acting as a client connects to this server.
- SQLNET.ENCRYPTION_TYPES_CLIENT
  Use the `sqlnet.ora` parameter `SQLNET.ENCRYPTION_TYPES_CLIENT` to list encryption algorithms for clients to use.
- SQLNET.ENCRYPTION_TYPES_SERVER
  Use the `sqlnet.ora` parameter `SQLNET.ENCRYPTION_TYPES_SERVER` to list the encryption algorithms for the database to use.
- SQLNET.EXPIRE_TIME
  Use the `sqlnet.ora` parameter `SQLNET.EXPIRE_TIME` to specify how often, in minutes, to verify that client and server connections are alive.
- SQLNET.IGNORE_ANO_ENCRYPTION_FOR_TCPS
  The `SQLNET.IGNORE_ANO_ENCRYPTION_FOR_TCPS` parameter is used on the server-side to ignore the value set in `SQLNET.ENCRYPTION_SERVER` for TCPS connections (effectively disabling ANO encryption on the TCPS listener).
- SQLNET.INBOUND_CONNECT_TIMEOUT
- SQLNET.FALLBACK_AUTHENTICATION
- SQLNET.KERBEROS5_CC_NAME
  Use the `sqlnet.ora` parameter `SQLNET.KERBEROS5_CC_NAME` to specify the complete path name to the Kerberos credentials cache file.
- SQLNET.KERBEROS5_CLOCKSKEW
- SQLNET.KERBEROS5_CONF
  Use the `sqlnet.ora` parameter `SQLNET.KERBEROS5_CONF` to specify the path name to the Kerberos configuration file that contains the realm for the default Key Distribution Center (KDC) and that maps realms to KDC hosts.
- SQLNET.KERBEROS5_CONF_LOCATION
- SQLNET.KERBEROS5_KEYTAB
- SQLNET.KERBEROS5_REALMS
- SQLNET.OUTBOUND_CONNECT_TIMEOUT
  Use the `sqlnet.ora` parameter `SQLNET.OUTBOUND_CONNECT_TIMEOUT` to specify the amount of time, in milliseconds, seconds, or minutes, in which clients must establish Oracle Net connections to database instances.
- SQLNET.RADIUS_ALTERNATE
- SQLNET.RADIUS_ALTERNATE_PORT
- SQLNET.RADIUS_ALTERNATE_RETRIES
- SQLNET.RADIUS_ALTERNATE_TIMEOUT
  Use the `sqlnet.ora` parameter `SQLNET.RADIUS_ALTERNATE_TIMEOUT` to set the time for an alternate RADIUS server to wait for a response.
- SQLNET.RADIUS_AUTHENTICATION
- SQLNET.RADIUS_AUTHENTICATION_INTERFACE
- SQLNET.RADIUS_AUTHENTICATION_PORT
- SQLNET.RADIUS_AUTHENTICATION_RETRIES
- SQLNET.RADIUS_AUTHENTICATION_TIMEOUT
- SQLNET.RADIUS_CHALLENGE_KEYWORD
  Use the `sqlnet.ora` parameter `SQLNET.RADIUS_CHALLENGE_KEYWORD` to set the keyword for requesting a challenge from the RADIUS server.
- SQLNET.RADIUS_CHALLENGE_RESPONSE
  Use the `sqlnet.ora` parameter `SQLNET.RADIUS_CHALLENGE_RESPONSE` to enable or disable challenge responses.
- SQLNET.RADIUS_CLASSPATH
  Use the `sqlnet.ora` parameter `SQLNET.RADIUS_CLASSPATH` to set the path for Java classes and JDK Java libraries.
- SQLNET.RADIUS_SECRET
- SQLNET.RADIUS_SEND_ACCOUNTING
- SQLNET.RECV_TIMEOUT
  Use the `sqlnet.ora` parameter `SQLNET.RECV_TIMEOUT` to specify the duration of time that a database client or server should wait for data from a peer after establishing a connection.
- SQLNET.SEND_TIMEOUT
  Use the `sqlnet.ora` parameter `SQLNET.SEND_TIMEOUT` to specify the duration of time for a database server to complete a send operation to clients after establishing a connection.
- SQLNET.URI
  `SQLNET.URI` networking parameter of the `sqlnet.ora` file specifies a database client URI mapping on the web server.
- SQLNET.USE_HTTPS_PROXY
- SQLNET.WALLET_OVERRIDE
  Use the `sqlnet.ora` parameter `SQLNET.WALLET_OVERRIDE` to determine whether a client should override strong authentication credentials with the password credential from the stored wallet.
- SSL_CERT_REVOCATION
  Use the `sqlnet.ora` parameter `SSL_CERT_REVOCATION` to configure revocation checks for certificates.
- SSL_CRL_FILE
  Use the `sqlnet.ora` parameter `SSL_CRL_FILE` to specify the name of the file in which you assemble the certificate revocation list (CRL) for client authentication.
- SSL_CRL_PATH
  Use the `sqlnet.ora` parameter `SSL_CRL_PATH` to specify the destination directory of the certificate revocation list (CRL) for client authentication.
- SSL_CIPHER_SUITES
  Use the `SSL_CIPHER_SUITES` parameter to control the combination of authentication, encryption, and data integrity algorithms used by Transport Layer Security (TLS).
- SSL_CLIENT_AUTHENTICATION
  Use the `SSL_CLIENT_AUTHENTICATION` parameter to specify whether a client is authenticated using Transport Layer Security (TLS).
- SSL_DISABLE_WEAK_EC_CURVES
  Use the `SSL_DISABLE_WEAK_EC_CURVES` parameter to disable the use of weak Elliptic Curve Cryptography (ECC) curves.
- SSL_EXTENDED_KEY_USAGE
- SSL_SERVER_DN_MATCH
  Use the `SSL_SERVER_DN_MATCH` parameter to enforce server-side certificate validation through distinguished name (DN) matching.
- SSL_VERSION
  Use the `SSL_VERSION` parameter to define valid Transport Layer Security (TLS) versions to be used for connections.
- TCP.CONNECT_TIMEOUT
- TCP.EXCLUDED_NODES
- TCP.INVITED_NODES
- TCP.NODELAY
- TCP.QUEUESIZE
- TCP.VALIDNODE_CHECKING
- TNSPING.TRACE_DIRECTORY
- TNSPING.TRACE_LEVEL
- TOKEN_AUTH
  Use the `TOKEN_AUTH` parameter to configure token-based authentication for Oracle Cloud Infrastructure (OCI) Identity and Access Management (IAM) or Microsoft Azure users of Microsoft Entra ID (previously called Microsoft Azure Active Directory).
- TOKEN_LOCATION
  Use the `TOKEN_LOCATION` parameter to specify the directory location where token file is stored for token-based authentication.
- USE_CMAN
- USE_DEDICATED_SERVER
- WALLET_LOCATION
  Use the `sqlnet.ora` parameter `WALLET_LOCATION` to specify the location of Oracle wallets.

**Parent topic:** Parameters for the sqlnet.ora File

#### 5.2.1 ACCEPT_MD5_CERTS

The `sqlnet.ora` profile parameter `ACCEPT_MD5_CERTS` accepts MD5 signed certificates.

##### Purpose

To enable `sqlnet` to accept MD5 signed certificates. In addition to `sqlnet.ora`, you must also set this parameter in `listener.ora`.

##### Default

`FALSE`

##### Values

- `TRUE` to accept MD5 signed certificates

- `FALSE` to not accept MD5 signed certficates

**Parent topic:** sqlnet.ora Profile Parameters

#### 5.2.2 ACCEPT_SHA1_CERTS

##### Purpose

To not accept SHA1 signed certificates, in addition to `sqlnet.ora`, this parameter must also be set in `listener.ora`.

##### Default

TRUE

##### Values

- `TRUE` to accept SHA1 signed certificates

- `FALSE` to not accept SHA1 signed certificates

**Parent topic:** sqlnet.ora Profile Parameters

#### 5.2.3 ADD_SSLV3_TO_DEFAULT

The `sqlnet.ora` profile parameter `ADD_SSLV3_TO_DEFAULT` sets the Transport Layer Security (TLS) versions that your server accepts.

##### Purpose

To set the TLS versions that your server accepts.

##### Usage Notes

To use `SSL_VERSION=3.0` in your `SSL_VERSION` default list, set the value to `TRUE`. In addition to setting this parameter in `sqlnet.ora`, you must also set this parameter in `listener.ora`.

##### Default

`FALSE`

##### Values

- If set to `TRUE` and `SSL_VERSION` is not specified or is set to "undetermined", then `SSL_VERSION` includes versions `1.2`, `1.1`, `1.0`, and `3.0`.

- If set to `FALSE` and `SSL_VERSION` is not specified or is set to "undetermined", then `SSL_VERSION` includes versions `1.2`, `1.1`, and `1.0`

**Parent topic:** sqlnet.ora Profile Parameters

#### 5.2.4 BEQUEATH_DETACH

Use the `sqlnet.ora` parameter to enable and disable signal handling on Linux and UNIX systems.

##### Purpose

To turn signal handling on or off for Linux and UNIX systems

##### Default

no

##### Values

- `yes` to turn signal handling off

- `no` to leave signal handling on

##### Example

`BEQUEATH_DETACH=yes`

**Parent topic:** sqlnet.ora Profile Parameters

#### 5.2.5 DEFAULT_SDU_SIZE

Use the `sqlnet.ora` profile parameter to specify the session data unit size (SDU) for connections.

##### Purpose

To specify the SDU size, in bytes, for connections.

##### Usage Notes

Oracle recommends setting this parameter in both the client-side and server-side `sqlnet.ora` files to ensure that the same SDU size is used throughout a connection. When the configured values of client and database server do not match for a session, the lower of the two values is used.

You can override this parameter for a particular client connection by specifying the SDU parameter in the connect descriptor for a client.

##### Default

`8192` bytes (8 KB)

##### Value

`512` to `2097152` bytes

Example 5-1 Example

`DEFAULT_SDU_SIZE=4096`

**Parent topic:** sqlnet.ora Profile Parameters

#### 5.2.6 DISABLE_INTERRUPT

Use the `sqlnet.ora` profile parameter `DISABLE_INTERRUPT` to disable Oracle Net handling of a `SIGINIT` signal in client applications.

##### Purpose

To disable Oracle Net handling of a `SIGINIT` signal in client applications.

##### Usage Notes

Oracle Net installs a signal handler to catch a `SIGINT` signal. By default, the action on receipt of a `SIGINIT` signal is to cancel the current operation. If you set this parameter to `TRUE`, then you can override the default behavior and ignore Oracle Net handling of `SIGINT` signals.

For details on installing and uninstalling your own signal handlers in addition to Oracle Net, see [Oracle Database Administrator's Reference for Linux and UNIX-Based Operating Systems](../unxar/using-oracle-precompilers-and-oracle-call-interface.md).

##### Default

`FALSE`

##### Example

`DISABLE_INTERRUPT=TRUE`

**Parent topic:** sqlnet.ora Profile Parameters

#### 5.2.7 DISABLE_OOB

DISABLE_OOB is a networking parameter of the sqlnet.ora file and is used to enable or disable Oracle Net to send or receive out-of-band break messages using urgent data provided by the underlying protocol.

##### Purpose

To enable or disable Oracle Net to send or receive out-of-band break messages using urgent data provided by the underlying protocol.

##### Usage Notes

If turned `off`, then the parameter enables Oracle Net to send and receive break messages. If turned `on`, then the parameter disables the ability to send and receive break messages. Once enabled, this feature applies to all protocols used by this client.

##### Default

`off`

Example 5-2 Example

`DISABLE_OOB=on`

**Parent topic:** sqlnet.ora Profile Parameters

#### 5.2.8 DISABLE_OOB_AUTO

The `DISABLE_OOB_AUTO` networking parameter of the `sqlnet.ora` file checks the server path for out-of-band break messages support at the connection time.

##### Purpose

Disable automatic out-of-band (OOB) support checks the server path at connection time.

##### Usage Notes

By default, the client checks if the server path supports out-of-band break messages or not at the connection time. If this parameter is set to `TRUE`, then the client does not perform this check at the connection time.

##### Default

`FALSE`

Example 5-3 Example

`DISABLE_OOB_AUTO = TRUE`

**Parent topic:** sqlnet.ora Profile Parameters

#### 5.2.9 EXADIRECT_FLOW_CONTROL

##### Purpose

To enable or disable Exadirect flow control.

##### Usage Notes

If turned on, the parameter enables Oracle Net to broadcast available receive window to the sender. The sender limits the sends based on the receiver broadcast window.

##### Default

`off`

##### Example

`EXADIRECT_FLOW_CONTROL=on`

**Parent topic:** sqlnet.ora Profile Parameters

#### 5.2.10 EXADIRECT_RECVPOLL

##### Purpose

To specify the time that a receiver polls for incoming data.

##### Usage Notes

The parameter can be set to a fixed value or `AUTO` for auto tuning of the polling value.

##### Default

`0`

##### Example

`EXADIRECT_RECVPOLL = 10`

`EXADIRECT_RECVPOLL = AUTO`

**Parent topic:** sqlnet.ora Profile Parameters

#### 5.2.11 IPC.KEYPATH

##### Purpose

To specify the destination directory where the internal file is created for UNIX domain sockets.

##### Usage Notes

This parameter applies only to Oracle Net's usage of UNIX domain socket and does not apply to other usages of UNIX domain sockets in the database, such as clusterware. If `keypath` is used, then the same value should be used on both the client and the listener sides with version greater than 18.

##### Default

The directory path is either `/var/tmp/.oracle` for Oracle Linux, Oracle Solaris or `/tmp/.oracle` for other UNIX variants.

##### Example

`ipc.keypath=/home/oracleuser`.

**Parent topic:** sqlnet.ora Profile Parameters

#### 5.2.12 MAX_CONDUITS

Use the `sqlnet.ora` parameter `MAX_CONDUITS` to specify the maximum number of conduits between the listener and the broker or dispatcher for handing off client connections.

##### Purpose

To set the maximum number of conduits created between the listener and the broker or dispatcher processes over which client connections are handed off.

##### Usage Notes

Setting a higher value enables multiple connections to be handed off in parallel, which is particularly useful during a logon storm when there is a spike in incoming connections.

##### Default

50

##### Example

`MAX_CONDUITS=80`

**Parent topic:** sqlnet.ora Profile Parameters

#### 5.2.13 NAMES.DEFAULT_DOMAIN

##### Purpose

To set the domain from which the client most often looks up names resolution requests.

##### Usage Notes

When this parameter is set, the default domain name is automatically appended to any unqualified net service name or service name.

For example, if the default domain is set to `us.example.com`, then the connect string `CONNECT scott@sales` gets searched as `sales.us.example.com`. If the connect string includes the domain extension, such as `CONNECT scott@sales.us.example.com`, then the domain is not appended to the string.

##### Default

None

##### Example

    NAMES.DEFAULT_DOMAIN=example.com

**Parent topic:** sqlnet.ora Profile Parameters

#### 5.2.14 NAMES.DIRECTORY_PATH

Use the `sqlnet` parameter `NAMES.DIRECTORY_PATH` to specify the order of the naming methods for client name resolution lookups.

##### Purpose

To specify the order of the naming methods for client name resolution lookups.

##### Default

    NAMES.DIRECTORY_PATH=(tnsnames, ezconnect, ldap)

##### Values

The following table shows the NAMES.DIRECTORY_PATH values for the naming methods.

| Naming Method Value                                    | Description                                                                                                                  |
|:-------------------------------------------------------|:-----------------------------------------------------------------------------------------------------------------------------|
| `tnsnames` (local naming method)                       | Set to resolve a network service name through the `tnsnames.ora` file on the client.                                         |
| `ldap `(directory naming method)                       | Set to resolve a database service name, net service name, or network service alias through a directory server.               |
| `ezconnect` or `hostname` (Easy Connect naming method) | Select to enable clients to use a TCP/IP connect identifier that consists of a host name and optional port and service name. |
| `nis` (external naming method)                         | Set to resolve service information through an existing Network Information Service (NIS).                                    |

##### Example

    NAMES.DIRECTORY_PATH=(tnsnames)

**Parent topic:** sqlnet.ora Profile Parameters

#### 5.2.15 NAMES.LDAP_AUTHENTICATE_BIND

##### Purpose

To specify whether the LDAP naming adapter should attempt to authenticate using a specified wallet when it connects to the LDAP directory to resolve the name in the connect string.

##### Usage Notes

The parameter value is Boolean.

If the parameter is set to `TRUE`, then the LDAP connection is authenticated using a wallet whose location must be specified in the WALLET_LOCATION parameter.

If the parameter is set to `FALSE`, then the LDAP connection is established using an anonymous bind.

##### Default

false

##### Example

    NAMES.LDAP_AUTHENTICATE_BIND=true

**Parent topic:** sqlnet.ora Profile Parameters

#### 5.2.16 NAMES.LDAP_CONN_TIMEOUT

##### Purpose

To specify number of seconds for a non-blocking connect timeout to the LDAP server.

##### Usage Notes

The parameter value -1 is for infinite timeout.

##### Default

15 seconds

##### Values

Values are in seconds. The range is `-1` to the number of seconds acceptable for your environment. There is no upper limit.

##### Example

    names.ldap_conn_timeout = -1

**Parent topic:** sqlnet.ora Profile Parameters

#### 5.2.17 NAMES.LDAP_PERSISTENT_SESSION

##### Purpose

To specify whether the LDAP naming adapter should leave the session with the LDAP server open after name lookup is complete.

##### Usage Notes

The parameter value is Boolean.

If the parameter is set to `TRUE`, then the connection to the LDAP server is left open after the name lookup is complete. The connection will effectively stay open for the duration of the process. If the connection is lost, then it is re-established as needed.

If the parameter is set to `FALSE`, then the LDAP connection is terminated as soon as the name lookup completes. Every subsequent lookup opens the connection, performs the lookup, and closes the connection. This option prevents the LDAP server from having a large number of clients connected to it at any one time.

##### Default

false

##### Example

    NAMES.LDAP_PERSISTENT_SESSION=true

**Parent topic:** sqlnet.ora Profile Parameters

#### 5.2.18 NAMES.NIS.META_MAP

##### Purpose

To specify the [map](glossary.md) file to be used to map [Network Information Service (NIS)](glossary.md) attributes to an NIS mapname.

##### Default

sqlnet.maps

##### Example

    NAMES.NIS.META_MAP=sqlnet.maps

**Parent topic:** sqlnet.ora Profile Parameters

#### 5.2.19 OCI_COMPARTMENT

Use the `OCI_COMPARTMENT` parameter to specify Oracle Cloud Identifier (OCID) of the compartment that holds database instances for client connections.

##### Purpose

To define the scope of your database token request. This value instructs the database client to initiate a token request to databases within the specified compartment only.

##### Usage Notes

You can use this parameter along with the `PASSWORD_AUTH`, `OCI_IAM_URL`, and `OCI_TENANCY` parameters while configuring token-based authentication for Oracle Cloud Infrastructure (OCI) Identity and Access Management (IAM) users on OCI Database as a Service (DBaaS). You can also use the optional `OCI_DATABASE` parameter to specify a database instance within the compartment for your connection.

With this configuration, the database client can only request an IAM database token using the IAM user name and IAM database password. The client cannot request an IAM database token for an API-key, delegation token, security token, resource principal, service principal, or instance principal.

The `OCI_COMPARTMENT` parameter is optional if `OCI_DATABASE` is not set. If you choose to set `OCI_DATABASE`, then you must also set `OCI_COMPARTMENT` so that your token request is for the specified database in that compartment.

If you do not set both `OCI_COMPARTMENT` and `OCI_DATABASE`, then the entire tenancy is the scope of your token request.

Use this parameter under the `SECURITY` section of the `tnsnames.ora` file, `sqlnet.ora` file, or directly as part of the command-line connect string. The parameter value specified in the connect string takes precedence over the other specified values.

##### Default

None

##### Value

OCID for the IAM compartment to allow access for the database token. You can get the OCID value for your compartment from the Compartments information page in the OCI console.

The compartment OCID uses this syntax:

`OCI_COMPARTMENT=``compartment_OCID`

For details on the syntax options, see [Oracle Cloud IDs (OCIDs)](https://docs.oracle.com/en-us/iaas/Content/GSG/Tasks/contactingsupport_topic-Finding_the_OCID_of_a_Compartment.htm).

##### Examples

In the `tnsnames.ora` file:

    net_service_name=
      (DESCRIPTION=
         (ADDRESS=(PROTOCOL=tcps)(HOST=salesserver1)(PORT=1522))
         (SECURITY=
            (SSL_SERVER_DN_MATCH=TRUE)
            (SSL_SERVER_CERT_DN="C=US,O=example,CN=OracleContext")
            (PASSWORD_AUTH=OCI_TOKEN)
            (OCI_IAM_URL=https://auth.us-region-1.example.com/v1/actions/generateScopedAccessBearerToken)
            (OCI_TENANCY=ocid1.tenancy..12345)
            (OCI_COMPARTMENT=ocid1.compartment..12345)
            (OCI_DATABASE=ocid1.autonomousdatabase.oc1.12345))
         (CONNECT_DATA=(SERVICE_NAME=sales.us.example.com))
      )

In the `sqlnet.ora` file:

    SSL_SERVER_DN_MATCH=TRUE
    PASSWORD_AUTH=OCI_TOKEN
    OCI_IAM_URL=https://auth.us-region-1.example.com/v1/actions/generateScopedAccessBearerToken
    OCI_TENANCY=ocid1.tenancy..12345
    OCI_COMPARTMENT=ocid1.compartment..12345
    OCI_DATABASE=ocid1.autonomousdatabase.oc1.12345

**Related Topics**

- [Oracle Database Security Guide](../dbseg/authenticating-and-authorizing-iam-users-oracle-dbaas-databases.md)
- [PASSWORD_AUTH](local-naming-parameters-in-tns-ora-file.md)

**Parent topic:** sqlnet.ora Profile Parameters

#### 5.2.20 OCI_DATABASE

Use the `OCI_DATABASE` parameter to specify Oracle Cloud Identifier (OCID) of the database that you want to access for the client connection.

##### Purpose

To define the scope of your database token request. The database OCID value instructs the database client to initiate a token request to the specified database within your compartment.

##### Usage Notes

This parameter is optional. You can use this parameter along with the `PASSWORD_AUTH`, `OCI_IAM_URL`, `OCI_TENANCY`, and `OCI_COMPARTMENT` parameters while configuring token-based authentication for Oracle Cloud Infrastructure (OCI) Identity and Access Management (IAM) users on OCI Database as a Service (DBaaS).

With this configuration, the database client can only request an IAM database token using the IAM user name and IAM database password. The client cannot request an IAM database token for an API-key, delegation token, security token, resource principal, service principal, or instance principal.

The `OCI_DATABASE` value limits your token request to the specified database only. If you set `OCI_DATABASE`, then you must also set `OCI_COMPARTMENT` so that your token request is for the specified database in that compartment.

Use this parameter under the `SECURITY` section of the `tnsnames.ora` file, `sqlnet.ora` file, or directly as part of the command-line connect string. The parameter value specified in the connect string takes precedence over the other specified values.

##### Default

None

##### Value

OCID of the database that you want to access for the client connection. You can get the OCID value for your database from the Database details page in the OCI console.

The database OCID uses this syntax:

`OCI_DATABASE=``database_OCID`

For details on the syntax options, see [Oracle Cloud IDs (OCIDs)](https://docs.oracle.com/en-us/iaas/autonomous-database/doc/view-list-acds-compartment.html).

##### Examples

In the `tnsnames.ora` file:

    net_service_name=
      (DESCRIPTION=
         (ADDRESS=(PROTOCOL=tcps)(HOST=salesserver1)(PORT=1522))
         (SECURITY=
            (SSL_SERVER_DN_MATCH=TRUE)
            (SSL_SERVER_CERT_DN="C=US,O=example,CN=OracleContext")
            (PASSWORD_AUTH=OCI_TOKEN)
            (OCI_IAM_URL=https://auth.us-region-1.example.com/v1/actions/generateScopedAccessBearerToken)
            (OCI_TENANCY=ocid1.tenancy..12345)
            (OCI_COMPARTMENT=ocid1.compartment..12345)
            (OCI_DATABASE=ocid1.autonomousdatabase.oc1.12345))
         (CONNECT_DATA=(SERVICE_NAME=sales.us.example.com))
      )

In the `sqlnet.ora` file:

    SSL_SERVER_DN_MATCH=TRUE
    PASSWORD_AUTH=OCI_TOKEN
    OCI_IAM_URL=https://auth.us-region-1.example.com/v1/actions/generateScopedAccessBearerToken
    OCI_TENANCY=ocid1.tenancy..12345
    OCI_COMPARTMENT=ocid1.compartment..12345
    OCI_DATABASE=ocid1.autonomousdatabase.oc1.12345

**Related Topics**

- [Oracle Database Security Guide](../dbseg/authenticating-and-authorizing-iam-users-oracle-dbaas-databases.md)
- [PASSWORD_AUTH](local-naming-parameters-in-tns-ora-file.md)

**Parent topic:** sqlnet.ora Profile Parameters

#### 5.2.21 OCI_IAM_URL

Use the `OCI_IAM_URL` parameter to specify an endpoint URL that the database client must connect with to get the database token for authenticating Oracle Cloud Infrastructure (OCI) Identity and Access Management (IAM) users on OCI Database as a Service (DBaaS).

##### Purpose

To specify the IAM URL for your REST API requests. The database client connects to this URL to retrieve the database token from IAM.

##### Usage Notes

You set the `OCI_IAM_URL` parameter along with the `PASSWORD_AUTH` and `OCI_TENANCY` parameters while configuring IAM token-based authentication (using the IAM user name and IAM database password to retrieve the database token). These parameters are mandatory.

With this configuration, the database client can only request an IAM database token using the IAM user name and IAM database password. The client cannot request an IAM database token for an API-key, delegation token, security token, resource principal, service principal, or instance principal.

You can also set the optional `OCI_COMPARTMENT` and `OCI_DATABASE` parameters to specify the scope of your token request.

Use this parameter under the `SECURITY` section of the `tnsnames.ora` file, `sqlnet.ora` file, or directly as part of the command-line connect string. The parameter value specified in the connect string takes precedence over the other specified values.

##### Default

None

##### Value

OCI IAM endpoint URL that the database client must connect with to get the database token. This URL is specific to your region and uses this syntax:

    <authentication_regional_endpoint>/v1/actions/generateScopedAccessBearerToken

You can derive this value by replacing \<authentication_regional_endpoint\> with the API endpoint URL for your region. To obtain the appropriate API endpoint URL, see [Identity and Access Management Data Plane API](https://docs.oracle.com/en-us/iaas/api/#/en/identity-dp/v1/).

For example, if you want to use the URL as `https://auth.us-region-1.example.com`, then your OCI_IAM_URL value is:

    https://auth.us-region-1.example.com/v1/actions/generateScopedAccessBearerToken

##### Examples

In the `tnsnames.ora` file:

    net_service_name=
      (DESCRIPTION=
         (ADDRESS=(PROTOCOL=tcps)(HOST=salesserver1)(PORT=1522))
         (SECURITY=
            (SSL_SERVER_DN_MATCH=TRUE)
            (SSL_SERVER_CERT_DN="C=US,O=example,CN=OracleContext")
            (PASSWORD_AUTH=OCI_TOKEN)
            (OCI_IAM_URL=https://auth.us-region-1.example.com/v1/actions/generateScopedAccessBearerToken)
            (OCI_TENANCY=ocid1.tenancy..12345))
         (CONNECT_DATA=(SERVICE_NAME=sales.us.example.com))
      )

In the `sqlnet.ora` file:

    SSL_SERVER_DN_MATCH=TRUE
    PASSWORD_AUTH=OCI_TOKEN
    OCI_IAM_URL=https://auth.us-region-1.example.com/v1/actions/generateScopedAccessBearerToken
    OCI_TENANCY=ocid1.tenancy..12345

In these examples, the optional `OCI_COMPARTMENT` and `OCI_DATABASE` parameters are not specified and thus the entire tenancy is set as the scope of the token request.

**Related Topics**

- [Oracle Database Security Guide](../dbseg/authenticating-and-authorizing-iam-users-oracle-dbaas-databases.md)
- [PASSWORD_AUTH](local-naming-parameters-in-tns-ora-file.md)

**Parent topic:** sqlnet.ora Profile Parameters

#### 5.2.22 OCI_TENANCY

Use the `OCI_TENANCY` parameter to specify Oracle Cloud Identifier (OCID) of the user’s tenancy.

##### Purpose

To specify OCID of the user’s tenancy (root compartment).

##### Usage Notes

You set this parameter along with the mandatory `PASSWORD_AUTH` and `OCI_IAM_URL` parameters while configuring token-based authentication for Oracle Cloud Infrastructure (OCI) Identity and Access Management (IAM) users on OCI Database as a Service (DBaaS).

With this configuration, the database client can only request an IAM database token using the IAM user name and IAM database password. The client cannot request an IAM database token for an API-key, delegation token, security token, resource principal, service principal, or instance principal.

You can also set the optional `OCI_COMPARTMENT` and `OCI_DATABASE` parameters to specify the scope of your token request. If you do not set the `OCI_COMPARTMENT` and `OCI_DATABASE` parameter values, then the entire tenancy is the scope of your token request.

Use this parameter under the `SECURITY` section of the `tnsnames.ora` file, `sqlnet.ora` file, or directly as part of the command-line connect string. The parameter value specified in the connect string takes precedence over the other specified values.

##### Default

None

##### Value

OCID of the user’s tenancy. You can get the OCID value for your tenancy from the Tenancy information page in the OCI console.

The tenancy OCID uses this syntax:

`OCI_TENANCY=``tenancy_OCID`

For details on the syntax options, see [Oracle Cloud IDs (OCIDs)](https://docs.oracle.com/en-us/iaas/Content/General/Concepts/identifiers.htm#Resource_Identifiers).

##### Examples

In the `tnsnames.ora` file:

    net_service_name=
      (DESCRIPTION=
         (ADDRESS=(PROTOCOL=tcps)(HOST=salesserver1)(PORT=1522))
         (SECURITY=
            (SSL_SERVER_DN_MATCH=TRUE)
            (SSL_SERVER_CERT_DN="C=US,O=example,CN=OracleContext")
            (PASSWORD_AUTH=OCI_TOKEN)
            (OCI_IAM_URL=https://auth.us-region-1.example.com/v1/actions/generateScopedAccessBearerToken)
            (OCI_TENANCY=ocid1.tenancy..12345))
         (CONNECT_DATA=(SERVICE_NAME=sales.us.example.com))
      )

In the `sqlnet.ora` file:

    SSL_SERVER_DN_MATCH=TRUE
    PASSWORD_AUTH=OCI_TOKEN
    OCI_IAM_URL=https://auth.us-region-1.example.com/v1/actions/generateScopedAccessBearerToken
    OCI_TENANCY=ocid1.tenancy..12345

In these examples, the optional `OCI_COMPARTMENT` and `OCI_DATABASE` parameters are not specified and thus the entire tenancy is set as the scope of the token request.

**Related Topics**

- [Oracle Database Security Guide](../dbseg/authenticating-and-authorizing-iam-users-oracle-dbaas-databases.md)
- [PASSWORD_AUTH](local-naming-parameters-in-tns-ora-file.md)

**Parent topic:** sqlnet.ora Profile Parameters

#### 5.2.23 PASSWORD_AUTH

Use the `PASSWORD_AUTH` parameter to configure an authentication method for Oracle Cloud Infrastructure (OCI) Identity and Access Management (IAM) users on OCI Database as a Service (DBaaS). With this setting, client connections use the IAM user name and IAM database password for logging in users to the database.

##### Purpose

To configure either IAM database password verifier authentication or IAM token-based authentication, using the IAM user name and IAM database password for the access.

For password verifier authentication, the database server retrieves an IAM database password verifier from IAM. For token-based authentication, the database client requests a database token (`db-token`) from IAM.

##### Usage Notes

- Use this parameter under the `SECURITY` section of the `tnsnames.ora` file, `sqlnet.ora` file, or directly as part of the command-line connect string. The parameter value specified in the connect string takes precedence over the other specified values.

- This setting instructs the database client to either use the existing password login process with the database server (password verifier authentication) or to get a token with the IAM user name and IAM database password (token-based authentication). This IAM database password is different from the OCI console password. An IAM user can set this password from the OCI console.

  See [Create an OCI IAM password to use for Autonomous Databases User Authentication and Authorization](https://www.youtube.com/watch?v=Y0jYPPnO5Dwx).

- By default, this parameter is set to `PASSWORD_VERIFIER`. The `PASSWORD_AUTH=PASSWORD_VERIFIER` setting configures IAM database password verifier authentication. The database server retrieves an IAM database password verifier (an encrypted hash of password) from IAM to authenticate users.

  When an IAM user logs in with the IAM user name and IAM database password using `@connect_identifier`, the `PASSWORD_AUTH=PASSWORD_VERIFIER` setting along with `@connect_identifier` instructs the database client to follow the existing user name and password login process with the database server.

  You can use the `PASSWORD_AUTH` parameter to override the `tnsnames.ora` or `sqlnet.ora` setting by specifying a different value in the connect string.

- To configure IAM token-based authentication with the IAM user name and IAM database password, set `PASSWORD_AUTH=OCI_TOKEN`. The database client requests a database token (`db-token`) from IAM for the user to access the database.

  This `db-token` obtained by the client is a bearer token with an expiration time and scope, and does not come with a private key. These tokens are transmitted over secure channels. You must use only the TCP/IP with Transport Layer Security (TLS) protocol, otherwise an error message appears indicating that non-TLS connections are disallowed.

  When an IAM user logs in with the IAM user name and IAM database password using `/@connect_identifier`, the `PASSWORD_AUTH=OCI_TOKEN` setting along with `/@connect_identifier` instructs the database client to get the token directly from an OCI IAM endpoint using a REST API request. If the IAM user is mapped to a database schema (exclusively or shared), then the login is completed.

  For the database client to retrieve the token from IAM, you must set additional parameters so that the database client can find the IAM endpoint along with additional meta-data. The additional parameters are `OCI_IAM_URL` and `OCI_TENANCY` along with the optional `OCI_COMPARTMENT` and `OCI_DATABASE`. These values enable the database client to make appropriate calls to the specified endpoint.

  The `OCI_IAM_URL` parameter specifies the API endpoint URL that the database client must connect with. The `OCI_TENANCY` parameter specifies the OCID (Oracle Cloud Identifier) of the user’s tenancy. The optional `OCI_COMPARTMENT` and `OCI_DATABASE` parameters limit the scope of your request.

  This authentication method is more secure than using a password verifier because a password verifier is considered sensitive. Also, only the database client can retrieve the database token. Applications or tools cannot pass these types of tokens through the database client API.

**Note:**

You can also use other IAM user credentials (such as API-key, security token, resource principal, service principal, instance principal, or delegation token) to get the `db-token`. This `db-token` is a proof-of-possession (PoP) token. In this case, you use a different parameter setting (`TOKEN_AUTH=OCI_TOKEN`).

Unlike the IAM database password that can only be used by the database client to retrieve the token, these credentials require an application or tool to retrieve the token. See [TOKEN_AUTH](local-naming-parameters-in-tns-ora-file.md).

##### Default

`PASSWORD_VERIFIER`

##### Values and Examples

| Value                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                | Example                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         |
|:-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|:----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| For IAM database password verifier authentication:<br>`PASSWORD_AUTH=PASSWORD_VERIFIER`<br>Note: Use of IAM user name and IAM database password with the IAM database password verifier is the default configuration, and you do not need to set any additional parameters for the client.<br>However, if `PASSWORD_AUTH` is set to `OCI_TOKEN` in the client-side `sqlnet.ora` file, then the client tries to connect with OCI IAM to retrieve a database token using the IAM user name and IAM database password. In this case, you can override this setting for a particular connection using `PASSWORD_AUTH=PASSWORD_VERIFIER`. | In the `tnsnames.ora` file:<br>`net_service_name=`<br>`  (DESCRIPTION =`<br>`     (ADDRESS=(PROTOCOL=tcps)(HOST=sales-svr)(PORT=1521))`<br>`     (SECURITY=`<br>`        (SSL_SERVER_DN_MATCH=TRUE)`<br>`        (SSL_SERVER_CERT_DN="C=US,O=example,CN=OracleContext")`<br>`        (PASSWORD_AUTH=PASSWORD_VERIFIER))`<br>`     (CONNECT_DATA=(SERVICE_NAME=sales.us.example.com))`<br>`  ) `<br>In the `sqlnet.ora` file:<br>`PASSWORD_AUTH=PASSWORD_VERIFIER`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                               |
| For IAM token-based authentication with the IAM user name and IAM database password:<br>`PASSWORD_AUTH=OCI_TOKEN`<br>Note: You must configure the TCPS protocol (`PROTOCOL=tcps`) and set the `SSL_SERVER_DN_MATCH` parameter to `TRUE` for token-based authentication.                                                                                                                                                                                                                                                                                                                                                              | In the `tnsnames.ora` file:<br>`net_service_name=`<br>`  (DESCRIPTION=`<br>`     (ADDRESS=(PROTOCOL=tcps)(HOST=salesserver1)(PORT=1522))`<br>`     (SECURITY=`<br>`        (SSL_SERVER_DN_MATCH=TRUE)`<br>`        (SSL_SERVER_CERT_DN="C=US,O=example,CN=OracleContext")`<br>`        (PASSWORD_AUTH=OCI_TOKEN)`<br>`        (OCI_IAM_URL=https://auth.us-region-1.example.com/v1/actions/generateScopedAccessBearerToken)`<br>`        (OCI_TENANCY=ocid1.tenancy..12345))`<br>`     (CONNECT_DATA=(SERVICE_NAME=sales.us.example.com))  `<br>`  )`<br>In the `sqlnet.ora` file:<br>`SSL_SERVER_DN_MATCH=TRUE`<br>`PASSWORD_AUTH=OCI_TOKEN`<br>`OCI_IAM_URL=https://auth.us-region-1.example.com/v1/actions/generateScopedAccessBearerToken`<br>`OCI_TENANCY=ocid1.tenancy..12345`<br>In these examples, the optional `OCI_COMPARTMENT` and `OCI_DATABASE` parameters are not specified and thus the entire tenancy is set as the scope of the token request. |

**Related Topics**

- [Oracle Database Security Guide](../dbseg/authenticating-and-authorizing-iam-users-oracle-dbaas-databases.md)
- [OCI_IAM_URL](local-naming-parameters-in-tns-ora-file.md)
- [OCI_TENANCY](local-naming-parameters-in-tns-ora-file.md)
- [OCI_COMPARTMENT](local-naming-parameters-in-tns-ora-file.md)
- [OCI_DATABASE](local-naming-parameters-in-tns-ora-file.md)

**Parent topic:** sqlnet.ora Profile Parameters

#### 5.2.24 RECV_BUF_SIZE

Use the `sqlnet.ora` parameter `RECV_BUF_SIZE` to specify buffer space limit for session receive operations.

##### Purpose

To specify the buffer space limit for receive operations of sessions.

##### Usage Notes

You can override this parameter for a particular client connection by specifying the [RECV_BUF_SIZE](local-naming-parameters-in-tns-ora-file.md) parameter in the connect descriptor for a client.

This parameter is supported by the TCP/IP, TCP/IP with TLS, and SDP protocols.

**Note:**

Additional protocols might support this parameter on certain operating systems. Refer to the operating system-specific documentation for additional information about additional protocols that support this parameter.

##### Default

The default value for this parameter is operating system specific. The default for Linux 2.6 operating system is 87380 bytes.

##### Example

    RECV_BUF_SIZE=11784

**Related Topics**

- [Oracle Database Net Services Administrator's Guide](../netag/optimizing-performance.md)

**Parent topic:** sqlnet.ora Profile Parameters

#### 5.2.25 SDP.PF_INET_SDP

##### Purpose

To specify the protocol family or address family constant for the SDP protocol on your system.

##### Default

27

##### Values

Any positive integer

##### Example

    SDP.PF_INET_SDP=30

**Parent topic:** sqlnet.ora Profile Parameters

#### 5.2.26 SEC_USER_AUDIT_ACTION_BANNER

##### Purpose

To specify a text file containing the banner contents that warn the user about possible user action auditing.

##### Usage Notes

The complete path of the text file must be specified in the `sqlnet.ora` file on the server. Oracle Call Interface (OCI) applications can make use of OCI features to retrieve this banner and display it to the user.

##### Default

None

##### Values

Name of the file for which the database owner has read permissions.

##### Example

    SEC_USER_AUDIT_ACTION_BANNER=/opt/oracle/admin/data/auditwarning.txt

**Parent topic:** sqlnet.ora Profile Parameters

#### 5.2.27 SEC_USER_UNAUTHORIZED_ACCESS_BANNER

##### Purpose

To specify a text file containing the banner contents that warn the user about unauthorized access to the database.

##### Usage Notes

The complete path of the text file must be specified in the `sqlnet.ora` file on the server. OCI applications can make use of OCI features to retrieve this banner and display it to the user.

##### Default

None

##### Values

Name of the file for which the database owner has read permissions.

##### Example

    SEC_USER_UNAUTHORIZED_ACCESS_BANNER=/opt/oracle/admin/data/unauthwarning.txt

**Parent topic:** sqlnet.ora Profile Parameters

#### 5.2.28 SEND_BUF_SIZE

Use the `sqlnet` parameter `SEND_BUF_SIZE` to specify the buffer space limit for session send operations.

##### Purpose

To specify the buffer space limit for send operations of sessions.

##### Usage Notes

You can override this parameter for a particular client connection by specifying the [SEND_BUF_SIZE](local-naming-parameters-in-tns-ora-file.md) parameter in the connect descriptor for a client.

This parameter is supported by the TCP/IP, TCP/IP with TLS, and SDP protocols.

**Note:**

Additional protocols might support this parameter on certain operating systems. Refer to the operating system-specific documentation for additional information about additional protocols that support this parameter.

##### Default

The default value for this parameter is operating system specific. The default for Linux 2.6 operating system is 16 KB.

##### Example

    SEND_BUF_SIZE=11784

**Related Topics**

- [Oracle Database Net Services Administrator's Guide](../netag/optimizing-performance.md)

**Parent topic:** sqlnet.ora Profile Parameters

#### 5.2.29 SQLNET.ALLOW_WEAK_CRYPTO

Use the `sqlnet.ora` compatibility parameter `SQLNET.ALLOW_WEAK_CRYPTO` to configure your client-side network connection by reviewing the specified encryption and crypto-checksum algorithms.

##### Purpose

To configure your client-side network connection by reviewing the encryption and crypto-checksum algorithms enabled on the client and server. This ensures that the connection does not encounter compatibility issues and your configuration uses supported strong algorithms.

##### Usage Notes

- The `DES`, `DES40`, `3DES112`, `3DES168`, `RC4_40`, `RC4_56`, `RC4_128`, `RC4_256`, and `MD5` algorithms are deprecated in this release.

  As a result of this deprecation, Oracle recommends that you review your network encryption and integrity configuration to check if you have specified any of the deprecated weak algorithms.

  To transition your Oracle Database environment to use stronger algorithms, download and install the patch described in My Oracle Support note [2118136.2](https://support.oracle.com/CSP/main/article?cmd=show&amp;type=NOT&amp;id=2118136.2).

- If you set this parameter to `TRUE`, then you can specify deprecated algorithms for backward compatibility. This configuration allows patched clients to connect to unpatched servers, and thus such a connection is less secure.

- If you set this parameter to `FALSE`, then you can specify only supported algorithms so that clients and servers can communicate in a fully patched environment. The server enforces key fold-in for all Kerberos and JDBC thin clients. This configuration strengthens the connection between clients and servers by using strong native network encryption and integrity capabilities.

  Using this setting, if native network encryption or checksumming is enabled and a patched server or client attempts to communicate with an unpatched old client or server, then the connection fails with an error message.

##### Values

- `TRUE`
- `FALSE`

##### Default Value

`TRUE`

##### Recommended Value

`FALSE`

**Note:**

Before setting this parameter to `FALSE`, you must remove all deprecated algorithms listed in the server and client `sqlnet.ora` files.

##### Example

    SQLNET.ALLOW_WEAK_CRYPTO = FALSE

**Related Topics**

- [Oracle Database Security Guide](../dbseg/configuring-network-data-encryption-and-integrity.md)
- SQLNET.ENCRYPTION_TYPES_CLIENT
- SQLNET.CRYPTO_CHECKSUM_TYPES_CLIENT

**Parent topic:** sqlnet.ora Profile Parameters

#### 5.2.30 SQLNET.ALLOW_WEAK_CRYPTO_CLIENTS

Use the `sqlnet.ora` compatibility parameter `SQLNET.ALLOW_WEAK_CRYPTO_CLIENTS` to configure your server-side network connection by reviewing the specified encryption and crypto-checksum algorithms.

##### Purpose

To configure your server-side network connection by reviewing the encryption and crypto-checksum algorithms enabled on the client and server. This ensures that the connection does not encounter compatibility issues and your configuration uses supported strong algorithms.

##### Usage Notes

- The `DES`, `DES40`, `3DES112`, `3DES168`, `RC4_40`, `RC4_56`, `RC4_128`, `RC4_256`, and `MD5` algorithms are deprecated in this release.

  As a result of this deprecation, Oracle recommends that you review your network encryption and integrity configuration to check if you have specified any of the deprecated weak algorithms.

  To transition your Oracle Database environment to use stronger algorithms, download and install the patch described in My Oracle Support note [2118136.2](https://support.oracle.com/CSP/main/article?cmd=show&amp;type=NOT&amp;id=2118136.2).

- If you set this parameter to `TRUE`, then you can specify deprecated algorithms for backward compatibility. This configuration allows patched servers to connect to unpatched clients, and thus such a connection is less secure.

- If you set this parameter to `FALSE`, then you can specify only supported algorithms so that clients and servers can communicate in a fully patched environment. The server enforces key fold-in for all Kerberos and JDBC thin clients. This configuration strengthens the connection between clients and servers by using strong native network encryption and integrity capabilities.

  Using this setting, if native network encryption or checksumming is enabled and a patched server or client attempts to communicate with an unpatched old client or server, then the connection fails with an error message.

##### Values

- `TRUE`
- `FALSE`

##### Default Value

`TRUE`

##### Recommended Value

`FALSE`

**Note:**

Before setting this parameter to `FALSE`, you must remove all deprecated algorithms listed in the server and client `sqlnet.ora` files.

##### Example

    SQLNET.ALLOW_WEAK_CRYPTO_CLIENTS = FALSE

**Related Topics**

- [Oracle Database Security Guide](../dbseg/configuring-network-data-encryption-and-integrity.md)
- SQLNET.ENCRYPTION_TYPES_SERVER
- SQLNET.CRYPTO_CHECKSUM_TYPES_SERVER

**Parent topic:** sqlnet.ora Profile Parameters

#### 5.2.31 SQLNET.ALLOWED_LOGON_VERSION_CLIENT

Use the `sqlnet` parameter `SQLNET.ALLOWED_LOGON_VERSION_CLIENT` to define minimum authentication protocols that servers acting as clients to other servers can use for connecting to Oracle Database instances.

##### Purpose

To set the minimum authentication protocol allowed for clients when a server is acting as a client, such as connecting over a database link, when connecting to Oracle Database instances.

##### Usage Notes

The term `VERSION` in the parameter name refers to the version of the authentication protocol, not the Oracle Database release.

If the version does not meet or exceed the value defined by this parameter, then authentication fails with an `ORA-28040: No matching authentication protocol` error.

##### Values

- `12a` for Oracle Database 12c Release 1 (12.1.0.2) or later (strongest protection)

  **Note:**

  Using this setting, the clients can only authenticate using a de-optimized password version. For example, the `12C` password version.

- `12` for the critical patch updates CPUOct2012 and later Oracle Database 11g authentication protocols (stronger protection)

  **Note:**

  Using this setting, the clients can only authenticate using a verifier that uses salt. For example, the `11G` or `12C` password versions.

- `11` for Oracle Database 11g authentication protocols (default)

- `10` for Oracle Database 10g authentication protocols

- `8` for Oracle8i authentication protocol

##### Default

11

##### Examples

- If an Oracle Database 19c database hosts a database link to an Oracle Database 18c database, then set the `SQLNET.ALLOWED_LOGON_VERSION_CLIENT` parameter as follows for the database link connection to proceed:
      SQLNET.ALLOWED_LOGON_VERSION_CLIENT=12

  In this case, you cannot configure the more secure `SQLNET.ALLOWED_LOGON_VERSION_CLIENT` setting of `12a` on the 19c server hosting the database link because the account on the Oracle Database 18c database might not have its password changed and thus might only have the `11G` verifier.
- If an Oracle Database 19c database hosts a database link to an old server, such as Oracle Database 11g database, then set the `SQLNET.ALLOWED_LOGON_VERSION_CLIENT` parameter as follows to allow the database link connection to proceed using the `11G` verifier:
      SQLNET.ALLOWED_LOGON_VERSION_CLIENT=11

**Related Topics**

- [Oracle Database Reference](../refrn/DBA_USERS.md)
- [Oracle Database Security Guide](../dbseg/configuring-authentication.md)

**Parent topic:** sqlnet.ora Profile Parameters

#### 5.2.32 SQLNET.ALLOWED_LOGON_VERSION_SERVER

Use the `sqlnet.ora` parameter `SQLNET.ALLOWED_LOGON_VERSION_SERVER` to set the minimum authentication protocol that is permitted when connecting to Oracle Database instances.

##### Purpose

To set the minimum authentication protocol for connecting to Oracle Database instances.

##### Usage Notes

- Authentication Protocol Versions:

  The term `VERSION` in the parameter name refers to the version of the authentication protocol, not the Oracle Database release.

  A value that appears higher up in Table 5-1 is less compatible (in terms of the protocol that clients must understand in order to authenticate) but simultaneously more secure than a value that appears lower down. The server is also more restrictive in terms of the password version that must exist to authenticate any specific account. Whether a client can authenticate to a specific account depends on both the server's setting of its `SQLNET.ALLOWED_LOGON_VERSION_SERVER` parameter, as well as on the password versions which exist for the specified account. The list of password versions can be seen in `DBA_USERS.PASSWORD_VERSIONS`.

  The authentication fails with an `ORA-28040: No matching authentication protocol` or an `ORA-03134: Connections to this server version are no longer supported` error if the client does not have the ability listed in the "Ability Required of the Client" column corresponding to the row matching the value of the `SQLNET.ALLOWED_LOGON_VERSION_SERVER` parameter in Table 5-1.

  A setting of `12` (the default) enables only the `11G` and `12C` password versions. A setting of `12a` enables only the `12C` password version.

  Note the following implications of setting the value to `12` or `12a`:

  - A value of `FALSE` for the `SEC_CASE_SENSITIVE_LOGON` Oracle instance initialization parameter must not be used because password case insensitivity requires the use of the `10G` password version. If the `SEC_CASE_SENSITIVE_LOGON` Oracle instance initialization parameter is set to `FALSE`, then user accounts and secure roles become unusable because Exclusive Mode excludes the use of the `10G` password version. The `SEC_CASE_SENSITIVE_LOGON` Oracle instance initialization parameter enables or disables password case sensitivity. However, since Exclusive mode is enabled by default in this release, disabling the password case sensitivity is not supported.

    **Note:**

    - The use of the Oracle instance initialization parameter `SEC_CASE_SENSITIVE_LOGON` is deprecated in favor of setting the `SQLNET.ALLOWED_LOGON_VERSION_SERVER` parameter to `12` to ensure that passwords are treated in a case-sensitive fashion.

    - Disabling password case sensitivity is not supported in Exclusive mode (when `SQLNET.ALLOWED_LOGON_VERSION_SERVER` is set to `12` or `12a`.)

  - Releases of OCI clients earlier than Oracle Database 10g cannot authenticate to the Oracle database using password-based authentication.

  - If the client uses Oracle Database 10g, then the client will receive an `ORA-03134: Connections to this server version are no longer supported` error message. To allow the connection, set the `SQLNET.ALLOWED_LOGON_VERSION_SERVER` value to `8`. Ensure the `DBA_USERS.PASSWORD_VERSIONS` value for the account contains the value `10G`. It may be necessary to reset the password for that account.

  - To take advantage of the `12C` password version introduced in Oracle Database release 12.2, user passwords should be expired to encourage users to change their passwords and cause the new `12C` password version to be generated for their account. By default in this release, new passwords are treated in a case-sensitive fashion. When an account password is changed, the earlier `10G` case-insensitive password version and the `11G` password version are both automatically removed, and the new `12C` password version is generated.

  - JDBC Thin Client Support:

    In Oracle Database release 12.1.0.2 and later, if you set the `sqlnet.ora` parameter `SQLNET.ALLOWED_LOGON_VERSION_SERVER` to `12a` and you create a new account or change the password of an existing account, then only the new `12C` password version is generated. The `12C` password version is based on a `SHA-2 (Secure Hash Algorithm) SHA-512` salted cryptographic hash deoptimized using the `PBKDF2` (Password-Based Key Derivation Function 2) algorithm. When the database server is running with `ALLOWED_LOGON_VERSION_SERVER` set to `12a`, it is running in Exclusive Mode. In this mode, to log in using a JDBC client, the JRE version must be at least version 8. The JDBC client enables its `O7L_MR` capability flag only when it is running with at least version 8 of the JRE.

    **Note:**

    Check the `PASSWORD_VERSIONS` column of the `DBA_USERS` catalog view in [Oracle Database Reference](../refrn/DBA_USERS.md) to see the list of password versions for any given account.
    If you set the `sqlnet.ora` parameter `SQLNET.ALLOWED_LOGON_VERSION_SERVER` to `12`, the server runs in Exclusive Mode and only the `11G` and `12C` password versions (the `SHA-1` and `PBKDF2 SHA-2` based hashes of the password, respectively) are generated and allowed to be used. In such cases, fully-patched JDBC clients having the CPUOct2012 patch can connect because these JDBC clients provide the `O5L_NP` client ability.

    Older JDBC clients which do not have the CPUOct2012 containing the fix for the stealth password cracking vulnerability CVE-2012-3132, do not provide the `O5L_NP` client ability. Therefore, ensure that all the JDBC clients are patched properly.

- Client Capabilities:

  The client must support certain abilities of the authentication protocol before the server will authenticate. If the client does not support a specified authentication ability, then the server rejects the connection with an `ORA-28040: No matching authentication protocol` error message.

  The following is the list of all client abilities. Some clients do not have all the listed abilities. Clients that are more recent have all of the capabilities of the older clients, but older clients tend to have fewer abilities than more recent clients. An ability that appears at the top in this list is more recent and secure than an ability that appears lower toward the bottom:

  - `O8L_LI`: The ability to support long identifiers (user names up to 128 bytes).

  - `O7L_MR`: The ability to perform the Oracle Database 10g authentication protocol using the `12C` password version. For JDBC clients, only those running on at least JRE version 8 offer the O7L_MR capability.

  - `O5L_NP`: The ability to perform the Oracle Database 10g authentication protocol using the `11G` password version, and generating a session key encrypted for critical patch update CPUOct2012.

  - `O5L`: The ability to perform the Oracle Database 10g authentication protocol using the `10G` password version.

  - `O4L`: The ability to perform the Oracle9i database authentication protocol using the `10G` password version.

  - `O3L`: The ability to perform the Oracle8i database authentication protocol using the `10G` password version.

- Using the Gradual Database Password Rollover Feature

  When the gradual database password rollover feature is enabled for an account, the `LOGON_INFO` clause in the audit record enables you to see whether the user has logged in with the old password or whether an application has not yet been updated to log in using the new password.

  For example:
      (TYPE=(DATABASE));
      (CLIENT ADDRESS=((PROTOCOL=ipc)(HOST=0.0.0.0)));
      (LOGON_INFO=((VERIFIER=11G-OLD)(CLIENT_CAPABILITIES=O5L_NP,O7L_MR,O8L_LI)));

- Allowed Parameter Settings:

  The following table describes the allowed settings of the `SQLNET.ALLOWED_LOGON_VERSION_SERVER` parameter, its effect on the generated password versions when an account is created or a password is changed, the ability flag required of the client to authenticate while the server has this setting, and whether the setting is considered to be an Exclusive Mode.

  Table 5-1 SQLNET.ALLOWED_LOGON_VERSION_SERVER Settings

  | Value of the ALLOWED_LOGON_VERSION_SERVER Parameter | Generated Password Version | Ability Required of the Client | Meaning for Clients                                                                                                                                                                                                                                                                                 | Server Runs in Exclusive Mode                                              |
  |:----------------------------------------------------|:---------------------------|:-------------------------------|:----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|:---------------------------------------------------------------------------|
  | `12a`                                               | `12C`                      | `O7L_MR`                       | Only Oracle Database 12c release 1 (12.1.0.2 or later) clients can connect to the server.                                                                                                                                                                                                           | Yes because it excludes the use of both `10G` and `11G` password versions. |
  | `12`                                                | `11G`, `12C`               | `O5L_NP`                       | Oracle Database 11g release 2 (11.2.0.3 or later) clients can connect to the server.<br>Older clients need the critical patch update CPUOct2012 or later, to gain the O5L_NP ability.<br>Only older clients which have applied critical patch update CPUOct2012 or later can connect to the server. | Yes because it excludes the use of the `10G` password version.             |
  | `11`                                                | `10G`, `11G`, `12C`        | `O5L`                          | Clients using Oracle Database 10g and later can connect to the server.<br>Clients using releases earlier than Oracle Database release 11.2.0.3 that have not applied critical patch update CPUOct2012 or later patches must use the `10G` password version.                                         | No                                                                         |
  | `10`                                                | `10G`, `11G`, `12C`        | `O5L`                          | It has the same meaning as the earlier row.                                                                                                                                                                                                                                                         | No                                                                         |
  | `9`                                                 | `10G`, `11G`, `12C`        | `O4L`                          | It has the same meaning as the earlier row.                                                                                                                                                                                                                                                         | No                                                                         |
  | `8`                                                 | `10G`, `11G`, `12C`        | `O3L`                          | It has the same meaning as the earlier row.                                                                                                                                                                                                                                                         | No                                                                         |

##### Values

- `12a` for Oracle Database 12c release 12.1.0.2 or later authentication protocols (strongest protection)

- `12` for Oracle Database 12c release 12.1 authentication protocols (default and recommended value)

- `11` for Oracle Database 11g authentication protocols

- `10` for Oracle Database 10g authentication protocols

- `9` for Oracle9i Database authentication protocol

- `8` for Oracle8i Database authentication protocol

**Note:**

- Starting with Oracle Database 12c Release 2 (12.2), the default value is 12.

- For earlier releases, the value 12 can be used after the critical patch updates CPUOct2012 and later are applied.

##### Default

`12`

##### Example

    SQLNET.ALLOWED_LOGON_VERSION_SERVER=12

**Related Topics**

- [Ensuring Against Password Security Threats by Using the 12C Password Version](../dbseg/configuring-authentication.md)
- [Managing Gradual Database Password Rollover for Applications](../dbseg/configuring-authentication.md)

**Parent topic:** sqlnet.ora Profile Parameters

#### 5.2.33 SQLNET.AUTHENTICATION_SERVICES

Use the `sqlnet.ora` parameter `SQLNET.AUTHENTICATION_SERVICES` to enable one or more authentication services.

##### Purpose

To enable one or more authentication services. If you have installed authentication, then Oracle recommends that you set `SQLNET.AUTHENTICATION_SERVICES` to either `NONE` or to one of the listed authentication methods.

##### Usage Notes

- You can set this parameter in the `sqlnet.ora` file.

  You can also set this value in the `tnsnames.ora` file or directly as part of the connect string. The `SQLNET.AUTHENTICATION_SERVICES` parameter is equivalent to the `tnsnames.ora` parameter `AUTHENTICATION_SERVICE`. The parameter value specified in the connect string takes precedence.

- When you set `SQLNET.AUTHENTICATION_SERVICES` to `ALL`, the server attempts to authenticate using each of the following methods.

  1.  Authentication based on a service external to the database, such as a service on the network layer, Kerberos, or RADIUS.

  2.  Authentication based on the operating system user's membership in an administrative operating system group. Group names are platform-specific. This authentication applies to administrative connections only.

  3.  Authentication performed by the database.

  4.  Authentication based on credentials stored in a directory server.

  The server falls back to the authentication methods that appear further down on the list if attempts to use the authentication methods appearing higher on the list were unsuccessful.

- When using local database password authentication (no external authentication), set `SQLNET.AUTHENTICATION_SERVICES=(NONE)` for better client performance.

- Operating system authentication enables access to the database using any user name and any password when an administrative connection is attempted to the CDB root, such as using the `AS SYSDBA` clause when connecting using SQL\*Plus.

  An example of a connection to the CDB root is as follows.

      sqlplus ignored_username/ignored_password AS SYSDBA

  When the operating-system user who issued the preceding command is already a member of the appropriate administrative operating system group, then the connection is successful. This is because Oracle checks the group membership first, and thus the user name and password are ignored by the server.

##### Values

Authentication methods that are available with Oracle Net Services:

- `NONE` for no authentication methods, including Microsoft Windows native operating system authentication. When you set `SQLNET.AUTHENTICATION_SERVICES` to `NONE`, then the user can use a valid user name and password to access the database.

- `ALL` for all authentication methods.

- `BEQ` for native operating system authentication for operating systems other than Microsoft Windows.

- `KERBEROS5` for Kerberos authentication.

- `RADIUS` for Remote Authentication Dial-In User Service (RADIUS) authentication.

- `TCPS` for TLS authentication.

- `NTS` for Microsoft Windows native operating system authentication. In this case, the user must authenticate to the database (CDB root) with OS credentials using Windows native authentication. No external password is needed. NTS checks the group membership for an OS user. For example, if an OS user is a member of the `ORA_DBA` group, then the user can log in to the database as `SYSDBA`.

  **Note:**

  With the `SQLNET.AUTHENTICATION_SERVICES` value `NTS`, if you try to connect through SQL\*Plus using NTS authentication and specify an external password (for example, `SQL*Plus SYSTEM/``password`), then the connection fails with an `ORA-12638: credential retrieval failed` error. For regular user name and password based authentication, set the value to `NONE`.

##### Default

`TCPS`

**Note:**

When installing Oracle Database with Database Configuration Assistant (DBCA), you can set this parameter to `NTS` in the `sqlnet.ora` file.

##### Examples

When specifying multiple authentication services, you must enclose the values within parentheses as follows:

    SQLNET.AUTHENTICATION_SERVICES=(BEQ,KERBEROS5)

If you want to specify only a single authentication service, then parentheses are not required:

    SQLNET.AUTHENTICATION_SERVICES=KERBEROS5

**Related Topics**

- [Configuring Authentication](../dbseg/configuring-authentication.md)
- [Setting the SQLNET.AUTHENTICATION_SERVICES Parameter in sqlnet.ora](../dbseg/customizing-the-use-of-strong-authentication.md)
- [AUTHENTICATION_SERVICE](local-naming-parameters-in-tns-ora-file.md)

**Parent topic:** sqlnet.ora Profile Parameters

#### 5.2.34 SQLNET.CLIENT_REGISTRATION

##### Purpose

To set a unique identifier for the client computer.

##### Usage Notes

This identifier is passed to the listener with any connection request, and is included in the audit trail. The identifier can be any alphanumeric string up to 128 characters long.

##### Default

None

##### Example

    SQLNET.CLIENT_REGISTRATION=1432

**Parent topic:** sqlnet.ora Profile Parameters

#### 5.2.35 SQLNET.CLOUD_USER

##### Purpose

To specify a user name for the web server `HTTP` basic authentication.

##### Usage Notes

When secure websocket protocol is used, the client uses this user as the user name for authentication. The password for this user should be stored in a wallet using `mkstore` commands.

Configuration steps to use `HTTP` basic authentication with secure websockets:

1.  Create wallet using orapki utility.

    `orapki wallet create -wallet ``wallet_directory`

    Example

    `orapki wallet create -wallet /app/wallet`

2.  Add web server public certificate.

    `orapki wallet -wallet  ``wallet_directory``  -trusted_cert -cert  ``web_server_public_certificate_in_pem_format`

    Example

    `orapki wallet -wallet  /app/wallet  -trusted_cert -cert  server_cert.txt`

3.  Add web server user name to `sqlnet.ora`. This user name is only used for authenticating the web server. This is not a database user name. After web server authentication , the web server makes connection to the backend database server and usual database authentication happens.

    Example

    `sqlnet.cloud_user = dbuser1`

4.  Add web server user password to wallet.

    `mkstore -wrl ``wallet_location``  -createEntry ``username password`

    Example

    `mkstore -wrl  /app/wallet  -createEntry  dbuser1  Secretdb#`

5.  Make wallet auto login and protect this wallet directory using operating system file permissions or any other means, so that ONLY database client can have read access to it. Refer to the operating system utilities for information about changing file permissions.

    `orapki wallet create -wallet ``wallet_directory`` -auto_login`

    Example

    `orapki wallet create -wallet /app/wallet -auto_login`

6.  Update `sqlnet.ora` with wallet entry.

    Example

        wallet_location=(SOURCE=  (METHOD=file)  (METHOD_DATA=    (DIRECTORY=/app/wallet)))

##### Default

None

**Parent topic:** sqlnet.ora Profile Parameters

#### 5.2.36 SQLNET.COMPRESSION

##### Purpose

To enable or disable data compression. If both the server and client have this parameter set to `ON`, then compression is used for the connection.

**Note:**

The `SQLNET.COMPRESSION` parameter applies to all database connections, except for Oracle Data Guard streaming redo and SecureFiles LOBs (Large Objects).

##### Default

off

##### Values

- `on` to enable data compression.

- `off` to disable data compression.

##### Example

    SQLNET.COMPRESSION=on

**Parent topic:** sqlnet.ora Profile Parameters

#### 5.2.37 SQLNET.COMPRESSION_ACCELERATION

##### Purpose

To specify the use of hardware accelerated version of compression using this parameter if it is available for that platform.

##### Usage Notes

This parameter can be specified under Oracle Connection Manager alias description.

##### Default

on

##### Values

- `on`

- `off`

- `0`

- `1`

Example 5-4 Example

`compression_acceleration = on`

**Parent topic:** sqlnet.ora Profile Parameters

#### 5.2.38 SQLNET.COMPRESSION_LEVELS

##### Purpose

To specify the compression level.

##### Usage Notes

The compression levels are used at time of negotiation to verify which levels are used at both ends, and to select one level.

For Database Resident Connection Pooling (DRCP), only the compression level `low` is supported.

##### Default

low

##### Values

- `low` to use low CPU usage and low compression ratio.

- `high` to use high CPU usage and high compression ratio.

##### Example

    SQLNET.COMPRESSION_LEVELS=(high)

**Parent topic:** sqlnet.ora Profile Parameters

#### 5.2.39 SQLNET.COMPRESSION_THRESHOLD

##### Purpose

To specify the minimum data size, in bytes, for which compression is needed.

##### Usage Notes

Compression is not be done if the size of the data to be sent is less than this value.

##### Default

1024 bytes

##### Example

    SQLNET.COMPRESSION_THRESHOLD=1024

**Parent topic:** sqlnet.ora Profile Parameters

#### 5.2.40 SQLNET.CRYPTO_CHECKSUM_CLIENT

Use the `sqlnet.ora` parameter `SQLNET.CRYPTO_CHECKSUM_CLIENT` to specify the desired data integrity behavior when this client or server acting as a client connects to a server.

##### Purpose

To specify the checksum behavior for the client. The behavior partially depends on the `SQLNET.CRYPTO_CHECKSUM_SERVER` setting at the other end of the connection.

##### Default

`accepted`

##### Values

- `accepted` to enable the security service if required or requested by the other side.

- `rejected` to disable the security service, even if required by the other side.

- `requested` to enable the security service if the other side allows it.

- `required` to enable the security service and disallow the connection if the other side is not enabled for the security service.

##### Example

    SQLNET.CRYPTO_CHECKSUM_CLIENT=accepted

**Related Topics**

- [Oracle Database Security Guide](../dbseg/data-encryption-and-integrity-parameters.md)

**Parent topic:** sqlnet.ora Profile Parameters

#### 5.2.41 SQLNET.CRYPTO_CHECKSUM_SERVER

Use the `sqlnet.ora` parameter `SQLNET.CRYPTO_CHECKSUM_SERVER` to specify the data integrity behavior when a client or another server acting as a client connects to this server.

##### Purpose

To specify the checksum behavior for the database. The behavior partially depends on the `SQLNET.CRYPTO_CHECKSUM_CLIENT` setting at the other end of the connection.

##### Default

`accepted`

##### Values

- `accepted` to enable the security service if required or requested by the other side.

- `rejected` to disable the security service, even if required by the other side.

- `requested` to enable the security service if the other side allows it.

- `required` to enable the security service and disallow the connection if the other side is not enabled for the security service.

##### Example

    SQLNET.CRYPTO_CHECKSUM_SERVER=accepted

**Related Topics**

- [Oracle Database Security Guide](../dbseg/data-encryption-and-integrity-parameters.md)

**Parent topic:** sqlnet.ora Profile Parameters

#### 5.2.42 SQLNET.CRYPTO_CHECKSUM_TYPES_CLIENT

Use the `sqlnet.ora` parameter `SQLNET.CRYPTO_CHECKSUM_TYPES_CLIENT` to specify a list of data integrity algorithms that this client or server acting as a client uses.

##### Purpose

To specify a list of crypto-checksum algorithms for the client to use.

This list is used to negotiate a mutually acceptable algorithm with the other end of the connection. If an algorithm that is not installed on this side is specified, the connection terminates with the `ORA-12650: No common encryption or data integrity algorithm error` error message.

##### Default

All available algorithms

##### Values

- `MD5` for the RSA Data Security MD5 algorithm.

  The `MD5` algorithm is deprecated in this release. To transition your Oracle Database environment to use stronger algorithms, download and install the patch described in My Oracle Support note [2118136.2](https://support.oracle.com/CSP/main/article?cmd=show&amp;type=NOT&amp;id=2118136.2).

- `SHA1` for the Secure Hash Algorithm.

- `SHA256` for SHA-2 uses 256 bits with the hashing algorithm.

- `SHA384` for SHA-2 uses 384 bits with the hashing algorithm.

- `SHA512` for SHA-2 uses 512 bits with the hashing algorithm.

##### Example

    SQLNET.CRYPTO_CHECKSUM_TYPES_CLIENT=(SHA256, MD5)

**Related Topics**

- [Oracle Database Security Guide](../dbseg/data-encryption-and-integrity-parameters.md)

**Parent topic:** sqlnet.ora Profile Parameters

#### 5.2.43 SQLNET.CRYPTO_CHECKSUM_TYPES_SERVER

Use the `sqlnet.ora` parameter `SQLNET.CRYPTO_CHECKSUM_TYPES_SERVER` to specify the data integrity algorithms that this server or client to another server uses, in order of intended use.

##### Purpose

To specify a list of crypto-checksum algorithms for the database to use.

This list is used to negotiate a mutually acceptable algorithm with the other end of the connection. Each algorithm is checked against the list of available client algorithm types until a match is found. If an algorithm is specified that is not installed on this side, the connection terminates with the `ORA-12650: No common encryption or data integrity algorithm error` error message.

##### Default

All available algorithms

##### Values

- `MD5` for the RSA Data Security's MD5 algorithm

  The `MD5` algorithm is deprecated in this release. To transition your Oracle Database environment to use stronger algorithms, download and install the patch described in My Oracle Support note [2118136.2](https://support.oracle.com/CSP/main/article?cmd=show&amp;type=NOT&amp;id=2118136.2).

- `SHA1` for the Secure Hash algorithm.

- `SHA256` for SHA-2 uses 256 bits with the hashing algorithm.

- `SHA384` for SHA-2 uses 384 bits with the hashing algorithm.

- `SHA512` for SHA-2 uses 512 bits with the hashing algorithm.

##### Example

    SQLNET.CRYPTO_CHECKSUM_TYPES_SERVER=(SHA256, MD5)

**Related Topics**

- [Oracle Database Security Guide](../dbseg/data-encryption-and-integrity-parameters.md)

**Parent topic:** sqlnet.ora Profile Parameters

#### 5.2.44 SQLNET.DBFW_PUBLIC_KEY

##### Purpose

To provide Oracle Database Firewall public keys to Advanced Security Option (ASO) by specifying the file that stores the Oracle Database Firewall public keys.

##### Default

None

##### Values

Full path name of the operating system file that has the public keys.

##### Example

    SQLNET.DBFW_PUBLIC_KEY="/path_to_file/dbfw_public_key_file.txt"

**See Also:**

"SQLNET.ENCRYPTION_TYPES_SERVER"

**Parent topic:** sqlnet.ora Profile Parameters

#### 5.2.45 SQLNET.DOWN_HOSTS_TIMEOUT

##### Purpose

To specify the amount of time in seconds that information about the `down` state of server hosts is kept in client process cache.

##### Usage Notes

Clients discover the `down` state of server hosts when attempting connections. When a connection attempt fails, the information about the `down` state of the server host is added to the client process cache. Subsequent connection attempts by the same client process move the `down` hosts to the end of the address list, thereby reducing the priority of such hosts. When the time specified by the `SQLNET.DOWN_HOSTS_TIMEOUT` parameter has passed, the host is purged from the process cache, and its priority in the address list is restored.

##### Default

600 seconds (10 minutes)

##### Values

Any positive integer

##### Example

    SQLNET.DOWN_HOSTS_TIMEOUT=60

**Parent topic:** sqlnet.ora Profile Parameters

#### 5.2.46 SQLNET.ENCRYPTION_CLIENT

Use the `sqlnet.ora` parameter `SQLNET.ENCRYPTION_CLIENT` to set the encryption behavior when this client or server acting as a client connects to a server.

##### Purpose

To turn encryption on for the client. Setting the `tnsnames.ora` parameter `IGNORE_ANO_ENCRYPTION_FOR_TCPS` to `TRUE` disables `SQLNET.ENCRYPTION_CLIENT`.

The behavior of the client partially depends on the value set for `SQLNET.ENCRYPTION_SERVER` at the other end of the connection.

##### Default

`accepted`

##### Values

- `accepted` to enable the security service if required or requested by the other side.

- `rejected` to disable the security service, even if required by the other side.

- `requested` to enable the security service if the other side allows it.

- `required` to enable the security service and disallow the connection if the other side is not enabled for the security service.

##### Example

    SQLNET.ENCRYPTION_CLIENT=accepted

**Related Topics**

- [Oracle Database Security Guide](../dbseg/data-encryption-and-integrity-parameters.md)

**Parent topic:** sqlnet.ora Profile Parameters

#### 5.2.47 SQLNET.ENCRYPTION_SERVER

The `sqlnet.ora` parameter `SQLNET.ENCRYPTION_SERVER` specifies the encryption behavior when a client or a server acting as a client connects to this server.

##### Purpose

To turn encryption on for the database server. Setting `SQLNET.IGNORE_ANO_ENCRYPTION_FOR_TCPS` to `FALSE` disables `SQLNET.ENCRYPTION_SERVER`.

The behavior of the server partially depends on the `SQLNET.ENCRYPTION_CLIENT` setting at the other end of the connection.

##### Default

`accepted`

##### Values

- `accepted` to enable the security service if required or requested by the other side.

- `rejected` to disable the security service, even if required by the other side.

- `requested` to enable the security service if the other side allows it.

- `required` to enable the security service and disallow the connection if the other side is not enabled for the security service.

##### Example

    SQLNET.ENCRYPTION_SERVER=accepted

**Related Topics**

- [Oracle Database Security Guide](../dbseg/data-encryption-and-integrity-parameters.md)

**Parent topic:** sqlnet.ora Profile Parameters

#### 5.2.48 SQLNET.ENCRYPTION_TYPES_CLIENT

Use the `sqlnet.ora` parameter `SQLNET.ENCRYPTION_TYPES_CLIENT` to list encryption algorithms for clients to use.

##### Purpose

To specify a list of encryption algorithms for clients to use.

##### Default

All available algorithms.

##### Values

One or more of the following:

- `3des112` for triple DES with a two-key (112-bit) option

- `3des168` for triple DES with a three-key (168-bit) option

- `aes128` for AES (128-bit key size)

- `aes192` for AES (192-bit key size)

- `aes256` for AES (256-bit key size)

- `des` for standard DES (56-bit key size)

- `des40` for DES (40-bit key size)

- `rc4_40` for RSA RC4 (40-bit key size)

- `rc4_56` for RSA RC4 (56-bit key size)

- `rc4_128` for RSA RC4 (128-bit key size)

- `rc4_256` for RSA RC4 (256-bit key size)

  The `DES`, `DES40`, `3DES112`, `3DES168`, `RC4_40`, `RC4_56`, `RC4_128`, and `RC4_256` algorithms are deprecated in this release.

  To transition your Oracle Database environment to use stronger algorithms, download and install the patch described in My Oracle Support note [2118136.2](https://support.oracle.com/CSP/main/article?cmd=show&amp;type=NOT&amp;id=2118136.2).

##### Example

    SQLNET.ENCRYPTION_TYPES_CLIENT=(rc4_56)

**See Also:**

[Oracle Database Security Guide](../dbseg/data-encryption-and-integrity-parameters.md)

**Parent topic:** sqlnet.ora Profile Parameters

#### 5.2.49 SQLNET.ENCRYPTION_TYPES_SERVER

Use the `sqlnet.ora` parameter `SQLNET.ENCRYPTION_TYPES_SERVER` to list the encryption algorithms for the database to use.

##### Purpose

To specify a list of encryption algorithms for the database to use.

##### Default

All available algorithms.

##### Values

One or more of the following:

- `3des112` for triple DES with a two-key (112-bit) option

- `3des168` for triple DES with a three-key (168-bit) option

- `aes128` for AES (128-bit key size)

- `aes192` for AES (192-bit key size)

- `aes256` for AES (256-bit key size)

- `des` for standard DES (56-bit key size)

- `des40` for DES40 (40-bit key size)

- `rc4_40` for RSA RC4 (40-bit key size)

- `rc4_56` for RSA RC4 (56-bit key size)

- `rc4_128` for RSA RC4 (128-bit key size)

- `rc4_256` for RSA RC4 (256-bit key size)

  The `DES`, `DES40`, `3DES112`, `3DES168`, `RC4_40`, `RC4_56`, `RC4_128`, and `RC4_256` algorithms are deprecated in this release.

  To transition your Oracle Database environment to use stronger algorithms, download and install the patch described in My Oracle Support note [2118136.2](https://support.oracle.com/CSP/main/article?cmd=show&amp;type=NOT&amp;id=2118136.2).

##### Example

    SQLNET.ENCRYPTION_TYPES_SERVER=(rc4_56, des, ...)

**See Also:**

[Oracle Database Security Guide](../dbseg/data-encryption-and-integrity-parameters.md)

**Parent topic:** sqlnet.ora Profile Parameters

#### 5.2.50 SQLNET.EXPIRE_TIME

Use the `sqlnet.ora` parameter `SQLNET.EXPIRE_TIME` to specify how often, in minutes, to verify that client and server connections are alive.

##### Purpose

To specify time intervals, in minutes, for how often to verify that client and server connections are alive.

##### Usage Notes

Setting a value greater than 0 ensures that connections are not left open indefinitely due to an unusual client termination. If your environment supports TCP keepalive tuning, then Oracle Net Services automatically uses the enhanced detection model and tunes the TCP keepalive parameters.

If the verification check identifies a terminated connection or a connection that is no longer usable, then the check returns an error, causing the server process to exit.

The `sqlnet.ora` parameter `SQLNET.EXPIRE_TIME` is primarily intended for the database server, which typically handles multiple connections simultaneously.

You can also use this parameter for database clients to verify if the server connection is alive.

Limitations on using the terminated connection detection feature are:

- You cannot use it on bequeathed connections.

- Though very small, a probe packet generates additional traffic that may degrade your network performance.

- Depending on your operating system, the server may need to perform additional processing to distinguish the connection probing event from other events. This can also result in degraded network performance.

##### Default

0

##### Minimum Value

0

##### Recommended Value

10

##### Example

    SQLNET.EXPIRE_TIME=10

**Parent topic:** sqlnet.ora Profile Parameters

#### 5.2.51 SQLNET.IGNORE_ANO_ENCRYPTION_FOR_TCPS

The `SQLNET.IGNORE_ANO_ENCRYPTION_FOR_TCPS` parameter is used on the server-side to ignore the value set in `SQLNET.ENCRYPTION_SERVER` for TCPS connections (effectively disabling ANO encryption on the TCPS listener).

##### Purpose

Used on the server-side to ignore the value set in `SQLNET.ENCRYPTION_SERVER` for TCPS connections (effectively disabling ANO encryption on the TCPS listener).

##### Usage Notes

If you set the `SQLNET.ENCRYPTION_CLIENT` parameter on the client to `required` and `SQLNET.ENCRYPTION_SERVER` on the server to `required`, and if a TCPS listener is used, then the `ORA-12696 Double Encryption Turned On, login disallowed` error appears. Starting with this release, you can set a new parameter, `SQLNET.IGNORE_ANO_ENCRYPTION_FOR_TCPS`, to `TRUE` to ignore the `SQLNET.ENCRYPTION_CLIENT` or `SQLNET.ENCRYPTION_SERVER` when there is a conflict between the use of a TCPS client and these two parameters are set to `required`.

##### Default

`FALSE`

Example 5-5 Example

`SQLNET.IGNORE_ANO_ENCRYPTION_FOR_TCPS=TRUE`

**Parent topic:** sqlnet.ora Profile Parameters

#### 5.2.52 SQLNET.INBOUND_CONNECT_TIMEOUT

##### Purpose

To specify the time, in `ms`, `sec`, or `min`, for a client to connect with the database server and provide the necessary authentication information.

##### Usage Notes

If the client fails to establish a connection and complete authentication in the time specified, then the database server terminates the connection. In addition, the database server logs the IP address of the client and an `ORA-12170: TNS:Connect timeout occurred` error message to the `sqlnet.log` file. The client receives either an `ORA-12547: TNS:lost contact` or an `ORA-12637: Packet receive failed` error message.

The default value of this parameter is appropriate for typical usage scenarios. However, if you need to explicitly set a different value, then Oracle recommends setting this parameter in combination with the` INBOUND_CONNECT_TIMEOUT_``listener_name` parameter in the `listener.ora` file. When specifying the values for these parameters, note the following recommendations:

- Set both parameters to an initial low value.

- Set the value of the `INBOUND_CONNECT_TIMEOUT_``listener_name` parameter to a lower value than the `SQLNET.INBOUND_CONNECT_TIMEOUT` parameter.

It accepts different timeouts with or without space between the value and the unit. In case, no unit is mentioned, the default unit is `sec`. For example, you can set `INBOUND_CONNECT_TIMEOUT_``listener_name` to 2 seconds and `SQLNET.INBOUND_CONNECT_TIMEOUT` parameter to 3 seconds. If clients are unable to complete connections within the specified time due to system or network delays that are normal for the particular environment, then increment the time as needed.

##### Default

60 seconds

##### Example

    SQLNET.INBOUND_CONNECT_TIMEOUT=3ms

**Parent topic:** sqlnet.ora Profile Parameters

#### 5.2.53 SQLNET.FALLBACK_AUTHENTICATION

##### Purpose

To specify whether password-based authentication is going to be attempted if Kerberos authentication fails. This is relevant for direct connections as well as database link connections.

##### Default

`FALSE`

##### Example

    SQLNET.FALLBACK_AUTHENTICATION=TRUE

**See Also:**

[Oracle Database Security Guide](../dbseg/configuring-kerberos-authentication.md)

**Parent topic:** sqlnet.ora Profile Parameters

#### 5.2.54 SQLNET.KERBEROS5_CC_NAME

Use the `sqlnet.ora` parameter `SQLNET.KERBEROS5_CC_NAME` to specify the complete path name to the Kerberos credentials cache file.

##### Purpose

To specify the complete path name to the Kerberos CC file.

##### Usage Notes

You can set this parameter in the `sqlnet.ora` file.

You can also set this value in the `tnsnames.ora` file or directly as part of the connect string. The `SQLNET.KERBEROS5_CC_NAME` parameter is equivalent to the `tnsnames.ora` parameter `KERBEROS5_CC_NAME`. The parameter value specified in the connect string takes precedence.

##### Values and Examples

You can use the following formats to specify a value for `SQLNET.KERBEROS5_CC_NAME`:

- If the Oracle database is using a directory cache:
  - `SQLNET.KERBEROS5_CC_NAME=``complete_path_to_cc_file`

    For example:

    `SQLNET.KERBEROS5_CC_NAME=/tmp/kcache`

    `SQLNET.KERBEROS5_CC_NAME=D:\tmp\kcache`

  - `SQLNET.KERBEROS5_CC_NAME=FILE:``complete_path_to_cc_ file`

    For example:

    `SQLNET.KERBEROS5_CC_NAME=FILE:/tmp/kcache`
- If the Oracle database is using the native Windows cache:
  - `SQLNET.KERBEROS5_CC_NAME=OSMSFT://`

  - `SQLNET.KERBEROS5_CC_NAME=MSLSA:`

  The `OSMSFT` and `MSLSA` options specify that the file is on Microsoft Windows and is running Microsoft Kerberos Key Distribution Center (KDC).

**Note:**

If you want to authenticate multiple Kerberos principals, then you can specify additional Kerberos principals either through the connect string directly or in the `tnsnames.ora` file.

##### Default

The default value is operating system-dependent, as follows:

- On Linux and UNIX operating systems: `/tmp/krb5cc_userid`

- On Microsoft Windows operating systems: `c:\tmp\krbcache`

**Related Topics**

- [KERBEROS5_CC_NAME](local-naming-parameters-in-tns-ora-file.md)
- [KERBEROS5_PRINCIPAL](local-naming-parameters-in-tns-ora-file.md)
- [Oracle Database Security Guide](../dbseg/configuring-kerberos-authentication.md)

**Parent topic:** sqlnet.ora Profile Parameters

#### 5.2.55 SQLNET.KERBEROS5_CLOCKSKEW

##### Purpose

To specify how many seconds can pass before a Kerberos credential is considered out of date.

##### Default

300

##### Example

    SQLNET.KERBEROS5_CLOCKSKEW=1200

**See Also:**

[Oracle Database Security Guide](../dbseg/kerberos-ssl-and-radius-authentication-parameters.md)

**Parent topic:** sqlnet.ora Profile Parameters

#### 5.2.56 SQLNET.KERBEROS5_CONF

Use the `sqlnet.ora` parameter `SQLNET.KERBEROS5_CONF` to specify the path name to the Kerberos configuration file that contains the realm for the default Key Distribution Center (KDC) and that maps realms to KDC hosts.

##### Purpose

To specify the complete path name to the Kerberos configuration file that contains the realm for the default Key Distribution Center (KDC) and that also maps realms to KDC hosts.

##### Usage Notes

KDC maintains a list of user principals and is contacted through the `kinit` program for the user's initial ticket.

If you configure the `SQLNET.KERBEROS5_CONF` parameter, then the Kerberos 5 configuration file `krb.conf` is fetched from the directory path specified in the parameter. Alternately, you can skip configuring the `SQLNET.KERBEROS5_CONF` altogether and still ensure the discovery of your configuration file by placing the `krb.conf` file in one of the default search locations so as to allow for an automatic discovery by Kerberos authentication service.

**Note:**

If you choose to place the Kerberos configuration file in one of the default search paths, then it is optional to set the parameter value as `AUTO_DISCOVER`, as placing the `krb.conf` file in one of the default locations enables automatic discovery without having to set the `AUTO_DISCOVER` parameter.

##### Default

On Linux and UNIX operating systems, `krb.conf` is automatically searched in the below file paths in the specified order:

1.  `$ORACLE_BASE/network/admin/krb.conf`
2.  `$ORACLE_BASE_HOME/network/admin/krb.conf`
3.  `$ORACLE_HOME/network/admin/krb.conf`
4.  `/etc/krb.conf`

`c:\krb5\krb.conf` on Microsoft Windows operating systems

##### Values

- Directory path to `krb.conf` file

- `AUTO_DISCOVER`

##### Example

    SQLNET.KERBEROS5_CONF=/krb5/krb.conf

**See Also:**

[Oracle Database Security Guide](../dbseg/kerberos-ssl-and-radius-authentication-parameters.md)

**Parent topic:** sqlnet.ora Profile Parameters

#### 5.2.57 SQLNET.KERBEROS5_CONF_LOCATION

##### Purpose

To specify the directory for the Kerberos configuration file. The parameter also specifies the file is created by the system, and not by the client.

##### Usage Notes

The configuration file uses DNS lookup to obtain the realm for the default KDC, and maps realms to the KDC hosts. This option is supported for all operating systems with such a feature.

##### Default

`/krb5` on Linux and UNIX operating systems

`c:\krb5` on Microsoft Windows operating systems

##### Example

    SQLNET.KERBEROS5_CONF_LOCATION=/krb5

**Parent topic:** sqlnet.ora Profile Parameters

#### 5.2.58 SQLNET.KERBEROS5_KEYTAB

##### Purpose

To specify the complete path name to the Kerberos principal/secret key mapping file, which is used to extract keys and decrypt incoming authentication information.

##### Default

`/etc/v5srvtab` on Linux and UNIX operating systems

`c:\krb5\v5srvtab` on Microsoft Windows operating systems

##### Example

    SQLNET.KERBEROS5_KEYTAB=/etc/v5srvtab

**See Also:**

[Oracle Database Security Guide](../dbseg/kerberos-ssl-and-radius-authentication-parameters.md)

**Parent topic:** sqlnet.ora Profile Parameters

#### 5.2.59 SQLNET.KERBEROS5_REALMS

##### Purpose

To specify the complete path name to the Kerberos realm translation file, which provides a mapping from a host name or domain name to a realm.

##### Default

`/krb5/krb.realms` on Linux and UNIX operating systems

`c:\krb5\krb.realms` on Microsoft Windows operating systems

##### Example

    SQLNET.KERBEROS5_REALMS=/krb5/krb.realms

**See Also:**

[Oracle Database Security Guide](../dbseg/kerberos-ssl-and-radius-authentication-parameters.md)

**Parent topic:** sqlnet.ora Profile Parameters

#### 5.2.60 SQLNET.OUTBOUND_CONNECT_TIMEOUT

Use the `sqlnet.ora` parameter `SQLNET.OUTBOUND_CONNECT_TIMEOUT` to specify the amount of time, in milliseconds, seconds, or minutes, in which clients must establish Oracle Net connections to database instances.

##### Purpose

To specify the time, in `ms`, `sec`, or `min`, for a client to establish an Oracle Net connection to the database instance.

##### Usage Notes

If an Oracle Net connection is not established in the time specified, then the connect attempt is terminated. The client receives an `ORA-12170: TNS:Connect timeout occurred` error.

The outbound connect timeout interval is a superset of the TCP connect timeout interval, which specifies a limit on the time taken to establish a TCP connection. Additionally, the outbound connect timeout interval includes the time taken to be connected to an Oracle instance providing the requested service. It accepts different timeouts with or without space between the value and the unit.

Without this parameter, a client connection request to the database server may block for the default TCP connect timeout duration (60 `seconds`) when the database server host system is unreachable. In case, no unit is mentioned, the default unit is `sec`.

The outbound connect timeout interval is only applicable for TCP, TCP with TLS, and IPC transport connections.

This parameter is overridden by the `CONNECT_TIMEOUT` parameter in the address description.

##### Default

None

##### Example

    SQLNET.OUTBOUND_CONNECT_TIMEOUT=10 ms

**Related Topics**

- [CONNECT_TIMEOUT](local-naming-parameters-in-tns-ora-file.md)

**Parent topic:** sqlnet.ora Profile Parameters

#### 5.2.61 SQLNET.RADIUS_ALTERNATE

##### Purpose

To specify an alternate RADIUS server to use in case the primary server is unavailable.

##### Usage Notes

The value can be either the IP address or host name of the server.

##### Default

None

##### Example

    SQLNET.RADIUS_ALTERNATE=radius2

**See Also:**

[Oracle Database Security Guide](../dbseg/kerberos-ssl-and-radius-authentication-parameters.md)

**Parent topic:** sqlnet.ora Profile Parameters

#### 5.2.62 SQLNET.RADIUS_ALTERNATE_PORT

##### Purpose

To specify the listening port of the alternate RADIUS server.

##### Default

1645

##### Example

    SQLNET.RADIUS_ALTERNATE_PORT=1667

**See Also:**

[Oracle Database Security Guide](../dbseg/kerberos-ssl-and-radius-authentication-parameters.md)

**Parent topic:** sqlnet.ora Profile Parameters

#### 5.2.63 SQLNET.RADIUS_ALTERNATE_RETRIES

##### Purpose

To specify the number of times the database server should resend messages to the alternate RADIUS server.

##### Default

3

##### Example

    SQLNET.RADIUS_ALTERNATE_RETRIES=4

**See Also:**

[Oracle Database Security Guide](../dbseg/kerberos-ssl-and-radius-authentication-parameters.md)

**Parent topic:** sqlnet.ora Profile Parameters

#### 5.2.64 SQLNET.RADIUS_ALTERNATE_TIMEOUT

Use the `sqlnet.ora` parameter `SQLNET.RADIUS_ALTERNATE_TIMEOUT` to set the time for an alternate RADIUS server to wait for a response.

##### Purpose

To set the time, in seconds, for an alternate RADIUS server to wait for a response.

##### Syntax

    SQLNET.RADIUS_ALTERNATE_TIMEOUT=time_in_seconds

##### Default

`5`

##### Example

    SQLNET.RADIUS_ALTERNATE_TIMEOUT=5

**Related Topics**

- [Oracle Database Security Guide](../dbseg/configuring-radius-authentication.md)

**Parent topic:** sqlnet.ora Profile Parameters

#### 5.2.65 SQLNET.RADIUS_AUTHENTICATION

##### Purpose

To specify the location of the primary RADIUS server, either by its host name or IP address.

##### Default

Local host

##### Example

    SQLNET.RADIUS_AUTHENETICATION=officeacct

**See Also:**

[Oracle Database Security Guide](../dbseg/kerberos-ssl-and-radius-authentication-parameters.md)

**Parent topic:** sqlnet.ora Profile Parameters

#### 5.2.66 SQLNET.RADIUS_AUTHENTICATION_INTERFACE

##### Purpose

To specify the class containing the user interface used to interact with the user.

##### Default

DefaultRadiusInterface

##### Example

    SQLNET.RADIUS_AUTHENTICATION_INTERFACE=DefaultRadiusInterface

**See Also:**

[Oracle Database Security Guide](../dbseg/kerberos-ssl-and-radius-authentication-parameters.md)

**Parent topic:** sqlnet.ora Profile Parameters

#### 5.2.67 SQLNET.RADIUS_AUTHENTICATION_PORT

##### Purpose

To specify the listening port of the primary RADIUS server.

##### Default

1645

##### Example

    SQLNET.RADIUS_AUTHENTICATION_PORT=1667

**See Also:**

[Oracle Database Security Guide](../dbseg/kerberos-ssl-and-radius-authentication-parameters.md)

**Parent topic:** sqlnet.ora Profile Parameters

#### 5.2.68 SQLNET.RADIUS_AUTHENTICATION_RETRIES

##### Purpose

To specify the number of times the database server should resend messages to the primary RADIUS server.

##### Default

3

##### Example

    SQLNET.RADIUS_AUTHENTICATION_RETRIES=4

**See Also:**

[Oracle Database Security Guide](../dbseg/kerberos-ssl-and-radius-authentication-parameters.md)

**Parent topic:** sqlnet.ora Profile Parameters

#### 5.2.69 SQLNET.RADIUS_AUTHENTICATION_TIMEOUT

##### Purpose

To specify the time, in seconds, that the database server should wait for a response from the primary RADIUS server.

##### Default

5

##### Example

    SQLNET.RADIUS_AUTHENTICATION_TIMEOUT=10

**See Also:**

[Oracle Database Security Guide](../dbseg/kerberos-ssl-and-radius-authentication-parameters.md)

**Parent topic:** sqlnet.ora Profile Parameters

#### 5.2.70 SQLNET.RADIUS_CHALLENGE_KEYWORD

Use the `sqlnet.ora` parameter `SQLNET.RADIUS_CHALLENGE_KEYWORD` to set the keyword for requesting a challenge from the RADIUS server.

##### Purpose

To set the keyword for requesting a challenge from the RADIUS server. By setting the challenge keyword, you let the user avoid using a password on the client to verify identity.

##### Syntax

    SQLNET.RADIUS_CHALLENGE_KEYWORD=keyword

##### Default

`challenge`

##### Example

    SQLNET.RADIUS_CHALLENGE_KEYWORD=challenge

**Related Topics**

- [Oracle Database Security Guide](../dbseg/configuring-radius-authentication.md)

**Parent topic:** sqlnet.ora Profile Parameters

#### 5.2.71 SQLNET.RADIUS_CHALLENGE_RESPONSE

Use the `sqlnet.ora` parameter `SQLNET.RADIUS_CHALLENGE_RESPONSE` to enable or disable challenge responses.

##### Purpose

To turn the challenge responses on or off.

##### Default

`off`

##### Values

    on | off

##### Example

    SQLNET.RADIUS_CHALLENGE_RESPONSE=on

**Parent topic:** sqlnet.ora Profile Parameters

#### 5.2.72 SQLNET.RADIUS_CLASSPATH

Use the `sqlnet.ora` parameter `SQLNET.RADIUS_CLASSPATH` to set the path for Java classes and JDK Java libraries.

##### Purpose

To set the path for Java classes for a graphical interface, and to set the path to JDK Java libraries.

If you use the challenge-response authentication mode, then RADIUS displays a Java-based graphical interface. This interface first requests a password and then additional information, for example, a dynamic password that the user obtains from a token card.

##### Syntax

    SQLNET.RADIUS_CLASSPATH=path_to_GUI_Java_classes

##### Default

`$ORACLE_HOME/jlib/netradius.jar:$ORACLE_HOME/JRE/lib/sparc/native_threads`

##### Example

    SQLNET.RADIUS_CLASSPATH=/jre1.1

**Related Topics**

- [Oracle Database Security Guide](../dbseg/configuring-radius-authentication.md)

**Parent topic:** sqlnet.ora Profile Parameters

#### 5.2.73 SQLNET.RADIUS_SECRET

##### Purpose:

To specify the location of the RADIUS secret key.

##### Default

The `ORACLE_HOME``/network/security/radius.key` file.

##### Example

    SQLNET.RADIUS_SECRET=oracle/bin/admin/radiuskey

**See Also:**

[Oracle Database Security Guide](../dbseg/kerberos-ssl-and-radius-authentication-parameters.md)

**Parent topic:** sqlnet.ora Profile Parameters

#### 5.2.74 SQLNET.RADIUS_SEND_ACCOUNTING

##### Purpose

To turn accounting `on` and `off`. If enabled, then packets are sent to the active RADIUS server at listening port plus one.

##### Usage Notes

The default port is 1646.

##### Default

off

##### Values

    on | off

##### Example

    SQLNET.RADIUS_SEND_ACCOUNTING=on

**See Also:**

[Oracle Database Security Guide](../dbseg/kerberos-ssl-and-radius-authentication-parameters.md)

**Parent topic:** sqlnet.ora Profile Parameters

#### 5.2.75 SQLNET.RECV_TIMEOUT

Use the `sqlnet.ora` parameter `SQLNET.RECV_TIMEOUT` to specify the duration of time that a database client or server should wait for data from a peer after establishing a connection.

##### Purpose

To specify the time for a database client or server to wait for data from the peer after establishing a connection. The peer must send some data within the time interval.

You can specify the time in hours, minutes, seconds, or milliseconds by using the `hr`, `min`, `sec`, or `ms` keyword respectively. If you do not specify a unit of measurement, then the default unit is `sec`.

##### Usage Notes

Setting this parameter for clients ensure that receive operation is not left in wait state indefinitely or for a long period due to an unusual termination of server process or server busy state. If a client does not receive response data in time specified, then it logs`ORA-12535: TNS:operation timed out` and `ORA-12609: TNS: Receive timeout occurred` messages to the `sqlnet.log` file. If you choose to set the value, then set the value to an initial low value and adjust according to the system and network capacity. If necessary, use this parameter with the `SQLNET.SEND_TIMEOUT` parameter.

You can also set this parameter on the server-side to specify the time, in `ms`, `sec`, or `min`, for a server to wait for client data after connection establishment. If a client does not send any data in time specified, then the database server logs `ORA-12535: TNS:operation timed out` and `ORA-12609: TNS: Receive timeout occurred` messages to the `sqlnet.log` file. Without this parameter, the database server may continue to wait for data from clients that may be down or are experiencing difficulties. The server usually blocks on input from the client and gets these timeouts frequently if set to a low value.

##### Default Value

None

##### Minimum Value

`1 ms`

##### Allowed Range

Any number greater than the minimum value of `1 ms` up to `4294967295 ms`.

##### Example

    SQLNET.RECV_TIMEOUT=10 ms

**Related Topics**

- [Oracle Database Net Services Administrator's Guide](../netag/index.md)

**Parent topic:** sqlnet.ora Profile Parameters

#### 5.2.76 SQLNET.SEND_TIMEOUT

Use the `sqlnet.ora` parameter `SQLNET.SEND_TIMEOUT` to specify the duration of time for a database server to complete a send operation to clients after establishing a connection.

##### Purpose

To specify the time for a database server to complete a send operation to clients after establishing a connection.

You can specify the time in hours, minutes, seconds, or milliseconds by using the `hr`, `min`, `sec`, or `ms` keyword respectively. If you do not specify a unit of measurement, then the default unit is `sec`.

##### Usage Notes

Setting this parameter is recommended for environments in which clients shut down occasionally or unusually.

If the database server cannot complete a send operation in the time specified, then it logs `ORA-12535: TNS:operation timed out` and `ORA-12608: TNS: Send timeout occurred` messages to the `sqlnet.log` file. Without this parameter, the database server may continue to send responses to clients that are unable to receive data due to a downed computer or a busy state.

You can also set this parameter on the client-side to specify the time, in `ms`, `sec`, or `min` , for a client to complete send operations to the database server after connection establishment. It accepts different timeouts with or without space between the value and the unit. Without this parameter, the client may continue to send requests to a database server already saturated with requests. If you choose to set the value, then set the value to an initial low value and adjust according to system and network capacity.

If necessary, use this parameter with the SQLNET.RECV_TIMEOUT parameter.

##### Default Value

None

##### Minimum Value

`1 ms`

##### Allowed Range

Any number greater than the minimum value of `1 ms` up to `4294967295 ms`.

##### Example

    SQLNET.SEND_TIMEOUT=3 ms

**Related Topics**

- [Oracle Database Net Services Administrator's Guide](../netag/index.md)

**Parent topic:** sqlnet.ora Profile Parameters

#### 5.2.77 SQLNET.URI

`SQLNET.URI` networking parameter of the `sqlnet.ora` file specifies a database client URI mapping on the web server.

##### Purpose

To specify a database client URI mapping on the web server.

##### Usage Notes

You can use this parameter to customize URI for mapping the database websocket requests coming onto web server to the backend database server. Secure websocket handshaking requests are sent with this URI.

##### Default

`/sqlnet`

Example 5-6 Example

`sqlnet.uri="/my_uri_prefix/database/"`

**Parent topic:** sqlnet.ora Profile Parameters

#### 5.2.78 SQLNET.USE_HTTPS_PROXY

##### Purpose

To enable forward HTTP proxy tunneling client connections.

##### Usage Notes

If turned `on`, the clients can tunnel secure connections over forward HTTP proxy using HTTP CONNECT method. This helps in accessing the public cloud database service as it eliminates the requirement to open an outbound port on a client side firewall. 

This parameter is applicable with Oracle Connection Manager on the server side.

##### Default

`on`

##### Example

`SQLNET.USE_HTTPS_PROXY=on`

**Parent topic:** sqlnet.ora Profile Parameters

#### 5.2.79 SQLNET.WALLET_OVERRIDE

Use the `sqlnet.ora` parameter `SQLNET.WALLET_OVERRIDE` to determine whether a client should override strong authentication credentials with the password credential from the stored wallet.

##### Purpose

To determine whether a client should override strong authentication credentials with the password credential from the stored wallet to log in to a database.

**Note:**

This is a client-side parameter. The `SQLNET.WALLET_OVERRIDE=TRUE` setting on the database server may break external procedures.

##### Usage Notes

When you use wallets for authentication, the database credentials for user name and password are securely stored in an Oracle wallet. The auto-login feature of the wallet is enabled so that the database does not need a password to open the wallet. From the wallet, the database gets the credentials to access the database for the user.

Wallet use can simplify large-scale deployments that rely on password credentials for connecting to databases. When this feature is configured, application code, batch jobs, and scripts do not need embedded user names and passwords. Risk is reduced because such passwords are no longer exposed, and password management policies are enforced without changing application code whenever user names or passwords change.

Users connect using the `connect /@``database_name` command instead of specifying a user name and password explicitly. This simplifies the maintenance of the scripts and secures the password management for the applications.

Middle-tier applications create an Oracle Applications wallet during installation to store an application's identity. The password may be randomly generated rather than hardcoded. When an Oracle application accesses the database, it sets appropriate values for `SQLNET.AUTHENTICATION_SERVICES` and `WALLET_LOCATION`. The new wallet-based password authentication code uses the password credential in the Oracle Applications wallet to log in to the database.

##### Values

`true` \| `false`

##### Example

    SQLNET.WALLET_OVERRIDE=true

**Related Topics**

- [My Oracle Support Note 340559.1](https://support.oracle.com/rs?type=doc&id=340559.1)
- [Oracle Database Security Guide](../dbseg/configuring-authentication.md)

**Parent topic:** sqlnet.ora Profile Parameters

#### 5.2.80 SSL_CERT_REVOCATION

Use the `sqlnet.ora` parameter `SSL_CERT_REVOCATION` to configure revocation checks for certificates.

##### Purpose

To configure a revocation check for a certificate.

**See Also:**

[Oracle Database Security Guide](../dbseg/kerberos-ssl-and-radius-authentication-parameters.md)

##### Default

`none`

##### Values

- `none` disables certificate revocation status checking. This is the default value.
  **Note:**

  Oracle recommends that you do not set the `SSL_CERT_REVOCATION` parameter to `none` because this removes a critical component in certificate-based authentication. Without certificate revocation status checking, you cannot protect against stolen certificates that are used for authentication. Set the `none` value only in cases where mitigating controls safeguard the use of certificates for authentication, such as network access control lists or Oracle Database Vault policies that limit the database connection to trusted clients.

- `requested` to perform certificate revocation in case a Certificate Revocation List (CRL) is available. Reject TLS connection if the certificate is revoked. If no appropriate CRL is found to determine the revocation status of the certificate and the certificate is not revoked, then accept the TLS connection.

- `required` to perform certificate revocation when a certificate is available. If a certificate is revoked and no appropriate CRL is found, then reject the TLS connection. If no appropriate CRL is found to ascertain the revocation status of the certificate and the certificate is not revoked, then accept the TLS connection.

##### Example

    SSL_CERT_REVOCATION=required

**Parent topic:** sqlnet.ora Profile Parameters

#### 5.2.81 SSL_CRL_FILE

Use the `sqlnet.ora` parameter `SSL_CRL_FILE` to specify the name of the file in which you assemble the certificate revocation list (CRL) for client authentication.

##### Purpose

To specify the name of the file where you can assemble the CRL for client authentication.

##### Usage Notes

This file contains the PEM-encoded CRL files, in order of preference. You can use this file alternatively or in addition to the `SSL_CRL_PATH` parameter. This parameter is only valid if `SSL_CERT_REVOCATION` is set to either `requested` or `required`.

##### Syntax

    SSL_CRL_FILE=certificate_revocation_list_filename

##### Default

None

##### Example

    SSL_CRL_FILE=crl.txt

**Related Topics**

- SSL_CERT_REVOCATION
- SSL_CRL_PATH

**Parent topic:** sqlnet.ora Profile Parameters

#### 5.2.82 SSL_CRL_PATH

Use the `sqlnet.ora` parameter `SSL_CRL_PATH` to specify the destination directory of the certificate revocation list (CRL) for client authentication.

##### Purpose

To specify the destination directory of the CRL of certificate authority (CA).

##### Usage Notes

The files in this directory are hashed symbolic links created by Oracle Wallet Manager.

This parameter is only valid if `SSL_CERT_REVOCATION` is set to either `requested` or `required`.

##### Syntax

    SSL_CRL_PATH=certificate_revocation_list_path

##### Default

None

##### Example

    SSL_CRL_PATH=/home/user1/crldir

**Related Topics**

- SSL_CERT_REVOCATION
- SSL_CRL_FILE

**Parent topic:** sqlnet.ora Profile Parameters

#### 5.2.83 SSL_CIPHER_SUITES

Use the `SSL_CIPHER_SUITES` parameter to control the combination of authentication, encryption, and data integrity algorithms used by Transport Layer Security (TLS).

##### Purpose

To control the combination of authentication, encryption, and data integrity algorithms used by [Transport Layer Security (TLS)](glossary.md). By default, the strongest protocol and cipher are negotiated between the database client and server. Setting this parameter will override the default behavior. You must use this parameter only if you have internal security controls that dictate the usage of certain protocol versions.

##### Usage Notes

Enclose the `SSL_CIPHER_SUITES` parameter value in parentheses. Otherwise, the cipher suite setting does not parse correctly.

##### Default

None

##### Values

Approved ciphers compatible with TLS 1.2:

- `TLS_ECDHE_RSA_WITH_AES_256_GCM_SHA384`
- `TLS_ECDHE_RSA_WITH_AES_128_GCM_SHA256`
- `TLS_ECDHE_ECDSA_WITH_AES_256_GCM_SHA384`
- `TLS_ECDHE_ECDSA_WITH_AES_128_GCM_SHA256`
- `TLS_DHE_RSA_WITH_AES_256_GCM_SHA384`
- `TLS_DHE_RSA_WITH_AES_128_GCM_SHA256`

Deprecated ciphers compatible with TLS 1.2:

- `TLS_ECDHE_RSA_WITH_AES_256_CBC_SHA384`
- `TLS_ECDHE_RSA_WITH_AES_128_CBC_SHA256`
- `TLS_ECDHE_ECDSA_WITH_AES_256_CBC_SHA384`
- `TLS_ECDHE_ECDSA_WITH_AES_128_CBC_SHA256`
- `TLS_RSA_WITH_AES_256_GCM_SHA384`
- `TLS_RSA_WITH_AES_256_CBC_SHA256`
- `TLS_RSA_WITH_AES_128_GCM_SHA256`
- `TLS_RSA_WITH_AES_128_CBC_SHA256`
- `TLS_ECDH_RSA_WITH_AES_256_GCM_SHA384`
- `TLS_ECDH_RSA_WITH_AES_128_GCM_SHA256`
- `TLS_ECDH_RSA_WITH_AES_256_CBC_SHA384`
- `TLS_ECDH_RSA_WITH_AES_128_CBC_SHA256`
- `TLS_ECDH_ECDSA_WITH_AES_256_GCM_SHA384`
- `TLS_ECDH_ECDSA_WITH_AES_128_GCM_SHA256`
- `TLS_ECDH_ECDSA_WITH_AES_256_CBC_SHA384`
- `TLS_ECDH_ECDSA_WITH_AES_128_CBC_SHA256`
- `TLS_DHE_RSA_WITH_AES_256_CBC_SHA256`
- `TLS_DHE_RSA_WITH_AES_128_CBC_SHA256`
- `TLS_DH_anon_WITH_AES_256_GCM_SHA384`
- `TLS_DH_anon_WITH_AES_128_GCM_SHA256 `

Deprecated ciphers compatible with TLS 1.0, TLS 1.1, and TLS 1.2:

- `TLS_ECDHE_RSA_WITH_AES_256_CBC_SHA`
- `TLS_ECDHE_RSA_WITH_AES_128_CBC_SHA`
- `TLS_ECDHE_ECDSA_WITH_AES_256_CBC_SHA`
- `TLS_ECDHE_ECDSA_WITH_AES_128_CBC_SHA`
- `TLS_RSA_WITH_AES_256_CBC_SHA`
- `TLS_RSA_WITH_AES_128_CBC_SHA`
- `TLS_ECDH_RSA_WITH_AES_256_CBC_SHA`
- `TLS_ECDH_RSA_WITH_AES_128_CBC_SHA`
- `TLS_ECDH_ECDSA_WITH_AES_256_CBC_SHA`
- `TLS_ECDH_ECDSA_WITH_AES_128_CBC_SHA`
- `TLS_DHE_RSA_WITH_AES_256_CBC_SHA`
- `TLS_DHE_RSA_WITH_AES_128_CBC_SHA`
- `TLS_ECDHE_RSA_WITH_RC4_128_SHA`
- `TLS_ECDHE_ECDSA_WITH_RC4_128_SHA`
- `TLS_ECDH_RSA_WITH_RC4_128_SHA`
- `TLS_ECDH_ECDSA_WITH_RC4_128_SHA`
- `SSL_RSA_WITH_RC4_128_SHA`
- `SSL_RSA_WITH_RC4_128_MD5`
- `TLS_ECDHE_ECDSA_WITH_NULL_SHA`
- `TLS_ECDHE_RSA_WITH_NULL_SHA`
- `TLS_ECDH_ECDSA_WITH_NULL_SHA`
- `TLS_ECDH_RSA_WITH_NULL_SHA`
- `SSL_RSA_WITH_NULL_SHA`
- `SSL_RSA_WITH_NULL_MD5`
- `SSL_DH_anon_WITH_RC4_128_MD5`

Deprecated ciphers compatible with TLS 1.0 and TLS 1.1:

- `TLS_ECDHE_RSA_WITH_3DES_EDE_CBC_SHA`
- `TLS_ECDHE_ECDSA_WITH_3DES_EDE_CBC_SHA`
- `TLS_ECDH_ECDSA_WITH_3DES_EDE_CBC_SHA`
- `TLS_ECDH_RSA_WITH_3DES_EDE_CBC_SHA`
- `SSL_RSA_WITH_3DES_EDE_CBC_SHA`
- `SSL_DH_anon_WITH_3DES_EDE_CBC_SHA`

**Note:**

The `DH_anon` cipher suites do not provide authentication of the communicating parties, and can be vulnerable to man-in-the-middle attacks. Oracle recommends that you do not use these cipher suites to protect sensitive data.

##### Examples

    SSL_CIPHER_SUITES=(TLS_ECDHE_ECDSA_WITH_AES_256_GCM_SHA384)

    SSL_CIPHER_SUITES=(TLS_ECDHE_ECDSA_WITH_AES_256_GCM_SHA384, TLS_ECDHE_ECDSA_WITH_AES_128_GCM_SHA256)

**Related Topics**

- [Set the TLS Cipher Suites on the Server](../dbseg/configuring-secure-sockets-layer-authentication.md)
- [Set the TLS Cipher Suites on the Client](../dbseg/configuring-secure-sockets-layer-authentication.md)

**Parent topic:** sqlnet.ora Profile Parameters

#### 5.2.84 SSL_CLIENT_AUTHENTICATION

Use the `SSL_CLIENT_AUTHENTICATION` parameter to specify whether a client is authenticated using Transport Layer Security (TLS).

##### Purpose

To specify whether a client is authenticated using [Transport Layer Security (TLS)](glossary.md).

##### Usage Notes

The database server authenticates the client. Therefore, this value should be set to `false`. If this parameter is set to `true`, then the listener attempts to authenticate the client, which can result in a failure.

##### Default

true

##### Values

    true | false

##### Example

    SSL_CLIENT_AUTHENTICATION=false

**See Also:**

[Oracle Database Security Guide](../dbseg/kerberos-ssl-and-radius-authentication-parameters.md)

**Parent topic:** sqlnet.ora Profile Parameters

#### 5.2.85 SSL_DISABLE_WEAK_EC_CURVES

Use the `SSL_DISABLE_WEAK_EC_CURVES` parameter to disable the use of weak Elliptic Curve Cryptography (ECC) curves.

##### Purpose

To disable the use of weak ECC curves with key length less than 256 bits. You can set this parameter in the database server (`sqlnet.ora`), client (`sqlnet.ora` or `tnsnames.ora` connect string), or the listener (`listener.ora`).

##### Usage Notes

By default, this parameter is set to `FALSE` to enable the use of all ECC curves. If you want to enable the use of only Oracle approved curves with ECC curve key size of 256 bits or higher, then set this parameter to `TRUE`.

When set to `TRUE`, you can use only the following ECC curves:

- `secp256r1`

- `secp384r1`

- `secp521r1`

##### Values

- `TRUE` \| `ON` \| `YES` \| `1`: To enable only the Oracle approved ECC curves with minimum ECC curve key length of 256 bits

- `FALSE` \| `OFF` \| `NO` \| `0`: To enable all ECC curves

##### Default

`FALSE`

##### Examples

- In the `tnsnames.ora` file:

      net_service_name=
        (DESCRIPTION=
          (ADDRESS=(PROTOCOL=tcps)(HOST=sales-svr)(PORT=1521))
          (SECURITY=(SSL_DISABLE_WEAK_EC_CURVES=TRUE))
        )

- In the `sqlnet.ora` file or the `listener.ora` file:

      SSL_DISABLE_WEAK_EC_CURVES=TRUE

**Parent topic:** sqlnet.ora Profile Parameters

#### 5.2.86  SSL_EXTENDED_KEY_USAGE

##### Purpose

To specify the purpose of the key in the certificate.

##### Usage Notes

When this parameter is specified, the certificate with the matching extended key is used.

##### Values

`client authentication`

##### Example

    SSL_EXTENDED_KEY_USAGE="client authentication"

**Parent topic:** sqlnet.ora Profile Parameters

#### 5.2.87 SSL_SERVER_DN_MATCH

Use the `SSL_SERVER_DN_MATCH` parameter to enforce server-side certificate validation through distinguished name (DN) matching.

##### Purpose

To enforce server-side certification validation through [distinguished name (DN)](glossary.md) matching.

##### Usage Notes

If you enforce the DN matching, in addition to verifying the server's certificate chain, the client performs another check through DN matching.

You can configure either partial DN matching or full DN matching. Partial DN matching occurs if the server's CN contains its host name. Full DN matching occurs against the server's complete DN. Not enforcing the match allows the server to potentially fake its identity.

In addition to the `sqlnet.ora` file, configure the `tnsnames.ora` parameter [SSL_SERVER_CERT_DN](local-naming-parameters-in-tns-ora-file.md) to enable full DN matching.

##### Default

`NO`

##### Values

- `YES` \| `ON` \| `TRUE` \| `1`:

  To enforce partial or full DN matching. If the DN matches the service name, then the connection succeeds. If the DN does not match the service name, then the connection fails.

- `NO` \| `OFF` \| `FALSE` \| `0`:

  To not enforce DN matching. If the DN does not match the service name, then the connection is successful, but an error is logged to the `sqlnet.log` file.

##### Example

    SSL_SERVER_DN_MATCH=YES

**Related Topics**

- [Oracle Database Security Guide](../dbseg/kerberos-ssl-and-radius-authentication-parameters.md)

**Parent topic:** sqlnet.ora Profile Parameters

#### 5.2.88 SSL_VERSION

Use the `SSL_VERSION` parameter to define valid Transport Layer Security (TLS) versions to be used for connections.

##### Purpose

To define the version of TLS that must run on the systems with which the database server communicates. By default, the database server and client negotiate the strongest security protocol. Oracle does not recommend modifying this parameter, unless your security requirements mandate the usage of certain protocol versions.

##### Usage Notes

Clients, listeners, and database servers must use compatible versions. Modify this parameter only when necessary to enforce the use of the more secure TLS protocol and not allow clients that only work with the older TLS protocols. If you need to specify TLS 1.0 or TLS 1.1, then also include TLS 1.2 to allow more secure connections. The current default uses TLS 1.2, which is the version required for multiple security compliance requirements.

If you set `SSL_VERSION` to `undetermined`, then the most secure TLS protocol version is used. You can use the `SSL_VERSION=undetermined` setting in the connect string for a specific connection to override the `SSL_VERSION` value configured in the `sqlnet.ora` file.

If you do not set `SSL_VERSION` to any value, then all the supported TLS protocol versions are tried starting with the most secure version. This is typically the most common configuration, ensuring that the strongest protocol is chosen during TLS negotiation.

##### Default

`undetermined`

##### Values

`undetermined` \| `1.0` \| `1.1` \| `1.2`

The version numbers correspond to the TLS versions, such as TLSv1.0, TLSv1.1, and TLSv1.2.

**Note:**

The `sqlnet.ora` parameter `ADD_SSLV3_TO_DEFAULT` has no impact on this parameter.

##### Syntax and Examples

- To specify a single TLS version:
      SSL_VERSION=TLS_protocol_version

  For example:
      SSL_VERSION=1.2

- To specify multiple TLS versions, use the `or` operator as follows:

      SSL_VERSION=TLS_protocol_version1 or TLS_protocol_version2

  For example:
      SSL_VERSION=1.1 or 1.2

      SSL_VERSION=1.0 or 1.1 or 1.2

**Related Topics**

- [Set the Required TLS Version on the Server](../dbseg/configuring-secure-sockets-layer-authentication.md)
- [Set the Required TLS Version on the Client](../dbseg/configuring-secure-sockets-layer-authentication.md)

**Parent topic:** sqlnet.ora Profile Parameters

#### 5.2.89 TCP.CONNECT_TIMEOUT

##### Purpose

To specify the time, in `ms`, `sec`, or `min`, for a client to establish a TCP connection (`PROTOCOL=tcp` in the TNS connect address) to the database server.

##### Usage Notes

If a TCP connection to the database host is not established in the specified time, then the connection attempt is terminated. The client receives an `ORA-12170: TNS:Connect timeout occurred` error.

The timeout applies to each IP address that resolves to a host name. It accepts different timeouts with or without space between the value and the unit. For example, if a host name resolves to an IPv6 and an IPv4 address, and if the host is not reachable through the network, then the connection request times out twice because there are two IP addresses. In this example, the default timeout setting of 60 causes a timeout in 120 `seconds`. In case, no unit is mentioned, the default unit is `sec`.

##### Default

60

##### Example

    TCP.CONNECT_TIMEOUT=10 ms

**Parent topic:** sqlnet.ora Profile Parameters

#### 5.2.90 TCP.EXCLUDED_NODES

##### Purpose

To specify which clients are denied access to the database.

##### Usage Notes

This parameter is only valid when the TCP.VALIDNODE_CHECKING parameter is set to `yes`.

This parameter can use wildcards for IPv4 addresses and CIDR notation for IPv4 and IPv6 addresses.

##### Syntax

    TCP.EXCLUDED_NODES=(hostname | ip_address, hostname | ip_address, ...)

##### Example

    TCP.EXCLUDED_NODES=(finance.us.example.com, mktg.us.example.com, 192.0.2.25,
     172.30.*, 2001:DB8:200C:417A/32)

**Parent topic:** sqlnet.ora Profile Parameters

#### 5.2.91 TCP.INVITED_NODES

##### Purpose

To specify which clients are allowed access to the database. This list takes precedence over the `TCP.EXCLUDED_NODES` parameter if both lists are present.

##### Syntax

    TCP.INVITED_NODES=(hostname | ip_address, hostname | ip_address, ...)

##### Usage Notes

- This parameter is only valid when the TCP.VALIDNODE_CHECKING parameter is set to `yes`.

- This parameter can use wildcards for IPv4 addresses and CIDR notation for IPv4 and IPv6 addresses.

##### Example

    TCP.INVITED_NODES=(sales.us.example.com, hr.us.example.com, 192.0.*,
     2001:DB8:200C:433B/32)

**Parent topic:** sqlnet.ora Profile Parameters

#### 5.2.92 TCP.NODELAY

##### Purpose

To preempt delays in buffer flushing within the TCP/IP protocol stack.

##### Default

yes

##### Values

    yes | no

##### Example

    TCP.NODELAY=yes

**Parent topic:** sqlnet.ora Profile Parameters

#### 5.2.93 TCP.QUEUESIZE

##### Purpose

To configure the maximum length of the queue for pending connections on a TCP listening socket.

##### Default

System-defined maximum value. The defined maximum value for Linux is 128.

##### Values

Any integer value up to the system-defined maximum.

##### Examples

    TCP.QUEUESIZE=100

**Parent topic:** sqlnet.ora Profile Parameters

#### 5.2.94 TCP.VALIDNODE_CHECKING

##### Purpose

To enable and disable valid node checking for incoming connections.

##### Usage Notes

If this parameter is set to `yes`, then incoming connections are allowed only if they originate from a node that conforms to list specified by TCP.INVITED_NODES or TCP.EXCLUDED_NODES parameters.

The TCP.INVITED_NODES and TCP.EXCLUDED_NODES parameters are valid only when the TCP.VALIDNODE_CHECKING parameter is set to `yes`.

This parameter and the depending parameters, TCP.INVITED_NODES and TCP.EXCLUDED_NODES must be set in the `sqlnet.ora` file of the listener. This is important in an Oracle RAC environment where the listener runs out of the Oracle Grid Infrastructure home. Setting the parameter in the database home does not have any effect in Oracle RAC environments. In such environments, the address of all Single Client Access Name (SCANs), Virtual IPs (VIPs), local IP must be included in the TCP.INVITED_NODES list.

In VLAN environments, the `sqlnet.ora` file present in the Oracle Grid Infrastructure home should include all the addresses of all the VLANs. The VLANs perform the network segregation, whereas the INVITED_NODES allows or restricts access to databases within the VLANs.

If multiple databases within the same VLAN require different INVITED_NODE lists, then separate listeners are required.

##### Default

no

##### Values

    yes | no

##### Example

    TCP.VALIDNODE_CHECKING=yes

**Parent topic:** sqlnet.ora Profile Parameters

#### 5.2.95 TNSPING.TRACE_DIRECTORY

##### Purpose

To specify the destination directory for the TNSPING utility trace file, `tnsping.trc`.

##### Default

The `ORACLE_HOME/network/trace` directory.

##### Example

    TNSPING.TRACE_DIRECTORY=/oracle/traces

**Parent topic:** sqlnet.ora Profile Parameters

#### 5.2.96 TNSPING.TRACE_LEVEL

##### Purpose

To turn TNSPING utility tracing on at a specified level or to turn it off.

##### Default

off

##### Values

- `off` for no trace output

- `user` for user trace information

- `admin` for administration trace information

- `support` for Oracle Support Services trace information

##### Example

    TNSPING.TRACE_LEVEL=admin

**Parent topic:** sqlnet.ora Profile Parameters

#### 5.2.97 TOKEN_AUTH

Use the `TOKEN_AUTH` parameter to configure token-based authentication for Oracle Cloud Infrastructure (OCI) Identity and Access Management (IAM) or Microsoft Azure users of Microsoft Entra ID (previously called Microsoft Azure Active Directory).

##### Purpose

Token-based access enforces strong authentication, which enables a more secure access to the database. IAM users can connect to OCI Database as a Service (DBaaS) databases, and Azure users can connect to Oracle Databases (cloud or on-premises).

With this setting, the database client looks for a token file when a `/` (slash) login is used.

Use this parameter under the `SECURITY` section of the `tnsnames.ora` file, `sqlnet.ora` file, or directly as part of the command-line connect string. The parameter value specified in the connect string takes precedence over the other specified values.

##### Usage Notes for IAM

- OCI IAM token:

  An OCI IAM token (`db-token`), which is obtained from IAM using Oracle Cloud Infrastructure (OCI) Command Line Interface (CLI) or programmatically from the OCI Software Development Kit (SDK), is a proof-of-possession (PoP) token with an expiration time and scope.

  You can use one of the IAM user credentials, such as API-key, security token, resource principal, instance principal, or delegation token to retrieve the `db-token` and private key from IAM.

  These tokens are transmitted over secure channels. You must use only the TCP/IP with Transport Layer Security (TLS) protocol, otherwise an error message appears indicating that non-TLS connections are disallowed.

- Required setting for token-based authentication:

  You must configure the TCPS protocol (`PROTOCOL=tcps`) and set the `SSL_SERVER_DN_MATCH` parameter to `TRUE` for token-based authentication.

- Use a file location to send the token to Oracle Database:

  When an IAM user logs in using `/@``connect_identifier` (and `TOKEN_AUTH` is set to `OCI_TOKEN`), the `TOKEN_AUTH=OCI_TOKEN` setting along with `/@``connect_identifier` instructs the database client to get the `db-token` and private key from either the default directory or the location specified by `TOKEN_LOCATION` (using IAM token-based authentication).

- Use the client API to send the token to Oracle Database:

  If your client application is updated to retrieve tokens from IAM, then you can override the `TOKEN_AUTH=OCI_TOKEN` setting. The client application gets the `db-token` and private key from IAM and sends as attributes to the database client using the client API. In this case, you do not need to specify the `TOKEN_AUTH` and `TOKEN_LOCATION` parameters.

- General IAM token-based authentication process:

  1.  An IAM user or application in OCI first requests the `db-token` from IAM by using API-key, security token, resource principal, service principal, instance principal, or delegation token (delegation token is available only in the Cloud Shell).

      To use a security token, you need to generate it by completing the browser authentication process and then request the `db-token` using that security token. If the IAM policy that authorizes you to be issued the `db-token` exists, then the `db-token` is returned.

      You request the `db-token` using OCI CLI (or OCI SDK for applications). For example, run the following OCI CLI command to request the `db-token` by using an API-key (`apikey`):

          $ oci iam db-token get --profile scott

      The `profile` option specifies the profile for which you want to access the IAM user credentials and retrieve the `db-token`.

      For more information on using OCI CLI, see the `get` command details in [Oracle Cloud Infrastructure CLI Command Reference](https://docs.oracle.com/en-us/iaas/tools/oci-cli/latest/oci_cli_docs/cmdref/iam/db-token/get.html).

  2.  OCI CLI references the `config` file (that stores your IAM user credentials as part of the profile) and makes a call to IAM to get the `db-token`. The `db-token` and private key files are written at the default or specified token location.

  3.  You can specify the `TOKEN_LOCATION` parameter to override the default directory where the `db-token` and private key files are stored.

      The database client gets the `db-token` and private key from the default token location or the location specified by `TOKEN_LOCATION`, signs the `db-token` with the private key and sends it to the database server. The database server verifies the `db-token` and gets the group membership information for the user. If the IAM user is mapped to a database schema (exclusively or shared), then the login is completed.

**Note:**

You can also use another IAM credential, IAM database password, to request the `db-token` from IAM. This `db-token` is a bearer token and does not come with a private key. You can configure the database client to request this token using your IAM user name and IAM database password. An application cannot pass this type of `db-token` to the client. In this case, you use a different parameter setting (`PASSWORD_AUTH=OCI_TOKEN`).

Unlike the API-key, security token, resource principal, service principal, instance principal, and delegation token that require an application or tool to get a token, the IAM database password can only be used by the database client to retrieve the token. See [PASSWORD_AUTH](local-naming-parameters-in-tns-ora-file.md).

Table 5-2 Values and Examples for IAM

| Default | Value                  | Example                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                        |
|:--------|:-----------------------|:-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| None    | `TOKEN_AUTH=OCI_TOKEN` | In the `tnsnames.ora` file:<br>`net_service_name=`<br>`    (DESCRIPTION =`<br>`       (ADDRESS=(PROTOCOL=tcps)(HOST=sales-svr)(PORT=1521))`<br>`       (SECURITY=`<br>`          (SSL_SERVER_DN_MATCH=TRUE)`<br>`          (SSL_SERVER_CERT_DN="C=US,O=example,CN=OracleContext")`<br>`          (TOKEN_AUTH=OCI_TOKEN))`<br>`       (CONNECT_DATA=(SERVICE_NAME=sales.us.example.com))`<br>`     ) `<br>In the `sqlnet.ora` file:<br>`SSL_SERVER_DN_MATCH=TRUE`<br>`TOKEN_AUTH=OCI_TOKEN`<br>In these examples, the optional `TOKEN_LOCATION` parameter is not specified. Thus, the client automatically gets the `db-token` and private key from the default token location. |

##### Usage Notes for Entra ID

- Entra ID access token:

  An Entra ID OAuth2 access token is a bearer token with an expiration time and scope. This token follows the OAuth2.0 standard with Entra ID extensions. You can request these tokens from tools and scripts run on Linux, Microsoft PowerShell, or other environments. You can also request these tokens programmatically using the Microsoft SDKs.

  These tokens are transmitted over secure channels. You must use only the TCP/IP with Transport Layer Security (TLS) protocol, otherwise an error message appears indicating that non-TLS connections are disallowed.

- Required setting for token-based authentication:

  You must configure the TCPS protocol (`PROTOCOL=tcps`) and set the `SSL_SERVER_DN_MATCH` parameter to `TRUE` for token-based authentication.

- Use a file location to send the token to Oracle Database:

  When an Azure user logs in using `/@``connect_identifier`, then the `TOKEN_AUTH=OAUTH` setting instructs the database client to get the access token from the directory location specified by `TOKEN_LOCATION` if the token file is named `token`. If the token file name is different from `token`, then you must use the file name along with the directory location while specifying the `TOKEN_LOCATION` parameter.

  The `TOKEN_LOCATION` parameter is mandatory for Azure token-based authentication. The database client gets the token from this location and sends it to the database server.

- Use the client API to send the token to Oracle Database:

  If your client application is updated to retrieve tokens from Entra ID, then you can override the `TOKEN_AUTH=OAUTH` setting. Entra ID directly passes the `db-token` as an attribute to the database client using the client API. When the client receives this request, the client sends it to the database server.

  In this case, you do no need to specify the `TOKEN_AUTH` and `TOKEN_LOCATION` parameters.

- General Azure token-based authentication process:

  1.  An Azure user or application first requests the access token from Entra ID using one of the supported authentication flows (resource owner password credentials, authorization code, on-behalf-of (OBO) flow, or client credentials).

      An Azure user can connect using any supported utility to retrieve the token and store it in a local file directory.

      You can request the token from tools and scripts run on Linux, Microsoft PowerShell, or other environments. You can also request programmatically using the Microsoft SDKs.

      For detailed examples on how to retrieve an Entra ID OAuth2 access token, see [Oracle Database Security Guide](../dbseg/authenticating-and-authorizing-microsoft-entra-id-ms-ei-users-oracle-databases-oracle-exadata.md).

  2.  The database client then sends the token to the database server. The database server verifies the token (using the Entra ID public key) and extracts various claims from the token, including user name, app roles, and audience. If the Entra ID principal is mapped to a database schema (exclusively or shared), then the login is completed.

Table 5-3 Values and Examples for Entra ID

| Default                                                                                                                                | Value                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            | Example                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              |
|:---------------------------------------------------------------------------------------------------------------------------------------|:-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|:-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| None                                                                                                                                   | If the token file is named `token`:<br>`TOKEN_AUTH=OAUTH` `TOKEN_LOCATION="``token_file_directory``"`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            | In the `tnsnames.ora` file:<br>`net_service_name=`<br>`    (DESCRIPTION=`<br>`      (ADDRESS=(PROTOCOL=tcps)(HOST=salesserver1)(PORT=1522))`<br>`      (SECURITY=`<br>`          (SSL_SERVER_DN_MATCH=TRUE)`<br>`          (SSL_SERVER_CERT_DN="C=US,O=example,CN=OracleContext")`<br>`          (TOKEN_AUTH=OAUTH)`<br>`          (TOKEN_LOCATION="/home/dbuser1/access-token"))`<br>`      (CONNECT_DATA=(SERVICE_NAME=sales.us.example.com))`<br>`    )`<br>In the `sqlnet.ora` file:<br>`SSL_SERVER_DN_MATCH=TRUE`<br>`TOKEN_AUTH=OAUTH `<br>`TOKEN_LOCATION="/home/dbuser1/access-token"`<br>In these examples, the token file name is `token`. Thus, only the directory path (`/home/dbuser1/access-token`) is specified. The client automatically looks for the `token` file in the specified path and gets the access token. |
| If the token file name is different from `token`:<br>`TOKEN_AUTH=OAUTH` `TOKEN_LOCATION="``token_file_directory``/``token_filename``"` | In the `tnsnames.ora` file:<br>`net_service_name=`<br>`    (DESCRIPTION=`<br>`      (ADDRESS=(PROTOCOL=tcps)(HOST=salesserver1)(PORT=1522))`<br>`      (SECURITY=`<br>`          (SSL_SERVER_DN_MATCH=TRUE)`<br>`          (SSL_SERVER_CERT_DN="C=US,O=example,CN=OracleContext")`<br>`          (TOKEN_AUTH=OAUTH)`<br>`          (TOKEN_LOCATION="/home/dbuser1/access-token/mytoken"))`<br>`      (CONNECT_DATA=(SERVICE_NAME=sales.us.example.com))`<br>`    )`<br>In the `sqlnet.ora` file:<br>`SSL_SERVER_DN_MATCH=TRUE`<br>`TOKEN_AUTH=OAUTH `<br>`TOKEN_LOCATION="/home/dbuser1/access-token/mytoken"`<br>In these examples, the token file name is `mytoken`. Thus, both the file name and directory path (`/home/dbuser1/access-token`) are specified. The client gets the access token from the `mytoken` file in the specified path. |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      |

**Related Topics**

- [Authenticating and Authorizing IAM Users for Oracle DBaaS Databases](../dbseg/authenticating-and-authorizing-iam-users-oracle-dbaas-databases.md)
- [Authenticating and Authorizing Microsoft Azure Users for Oracle Databases](../dbseg/authenticating-and-authorizing-microsoft-entra-id-ms-ei-users-oracle-databases-oracle-exadata.md)
- [TOKEN_LOCATION](local-naming-parameters-in-tns-ora-file.md)

**Parent topic:** sqlnet.ora Profile Parameters

#### 5.2.98 TOKEN_LOCATION

Use the `TOKEN_LOCATION` parameter to specify the directory location where token file is stored for token-based authentication.

##### Purpose

To specify the token file directory location. You use this parameter while configuring token-based authentication for Oracle Cloud Infrastructure (OCI) Identity and Access Management (IAM) or Microsoft Azure users of Microsoft Entra ID. The database client gets the token from this location and sends it to the database server. For Entra ID, you can also specify the token file name along with the directory location.

Use this parameter along with the `TOKEN_AUTH` parameter in the `tnsnames.ora` file, `sqlnet.ora` file, or directly as part of the command-line connect string. The parameter values specified in the connect string take precedence over the other specified values.

##### Usage Notes for IAM

The `TOKEN_LOCATION` parameter is optional for IAM token-based authentication. You can use this parameter along with the `TOKEN_AUTH` parameter to override the default directory where the `db-token` and private key are stored. This location is used by the database client to retrieve the `db-token` and private key.

When an IAM user initiates a connection using `/@``connect_identifier` (and `TOKEN_AUTH` is set to `OCI_TOKEN`), the database client retrieves the `db-token` and private key from either the default directory or the location specified by `TOKEN_LOCATION`. The client then signs the `db-token` using the private key and sends the `db-token` to the database server.

##### Default Setting for IAM

- On Linux:

  `/home/``username``/.oci/db-token`

- On Windows:

  The database client searches for the default directory in this order:

  If the `USERPROFILE` environment variable is set, then the client searches in the `USERPROFILE` directory (for example, `C:\Users\``username`).

  If `USERPROFILE` is not set, then the client searches in `HOMEDRIVE` directory (for example, `C:`) with `HOMEPATH` (for example, `\Users\``username`).

  For example, the default token location directory on Windows is:

  `C:\Users\``username``\.oci\db-token`

##### Values and Examples for IAM

| Value                                       | Example                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  |
|:--------------------------------------------|:---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `TOKEN_LOCATION="``token_file_directory``"` | In the `tnsnames.ora` file:<br>`net_service_name=`<br>`    (DESCRIPTION =`<br>`       (ADDRESS=(PROTOCOL=tcps)(HOST=sales-svr)(PORT=1521))`<br>`       (SECURITY=`<br>`          (SSL_SERVER_DN_MATCH=TRUE)`<br>`          (SSL_SERVER_CERT_DN="C=US,O=example,CN=OracleContext")`<br>`          (TOKEN_AUTH=OCI_TOKEN)`<br>`          (TOKEN_LOCATION="/home/oracle/.oci/db-token"))`<br>`       (CONNECT_DATA=(SERVICE_NAME=sales.us.example.com))`<br>`     ) `<br>In the `sqlnet.ora` file:<br>`SSL_SERVER_DN_MATCH=TRUE`<br>`TOKEN_AUTH=OCI_TOKEN`<br>`TOKEN_LOCATION="/home/oracle/.oci/db-token"` |

##### Usage Notes for Entra ID

The `TOKEN_LOCATION` parameter is mandatory for Azure token-based authentication. You must use this parameter along with the `TOKEN_AUTH` parameter to specify the directory location where the Entra ID OAuth2 access token is stored. This location is used by the database client to get the access token.

If your token file is named `token`, then specify only the directory path. If the token file name is different from `token`, then you must use the file name along with the directory path.

When an Azure user initiates a connection using `/@``connect_identifier`, the database client retrieves the access token from the location specified by `TOKEN_LOCATION` and sends the token to the database server.

##### Default Setting for Entra ID

None

##### Values and Examples for Entra ID

| Value                                                                                                               | Example                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                        |
|:--------------------------------------------------------------------------------------------------------------------|:-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| If the token file is named `token`:<br>`TOKEN_LOCATION="``token_file_directory``"`                                  | In the `tnsnames.ora` file:<br>`net_service_name=`<br>`    (DESCRIPTION=`<br>`      (ADDRESS=(PROTOCOL=tcps)(HOST=salesserver1)(PORT=1522))`<br>`      (SECURITY=`<br>`          (SSL_SERVER_DN_MATCH=TRUE)`<br>`          (SSL_SERVER_CERT_DN="C=US,O=example,CN=OracleContext")`<br>`          (TOKEN_AUTH=OAUTH)(TOKEN_LOCATION="/home/dbuser1/access-token"))`<br>`      (CONNECT_DATA=(SERVICE_NAME=sales.us.example.com))`<br>`    )`<br>In the `sqlnet.ora` file:<br>`SSL_SERVER_DN_MATCH=TRUE`<br>`TOKEN_AUTH=OAUTH `<br>`TOKEN_LOCATION="/home/dbuser1/access-token"`<br>In these examples, the token file name is `token`. Thus, only the directory path (`/home/dbuser1/access-token`) is specified. The client automatically looks for the `token` file in the specified path and gets the access token.                           |
| If the token file name is different from `token`:<br>`TOKEN_LOCATION="``token_file_directory``/``token_filename``"` | In the `tnsnames.ora` file:<br>`net_service_name=`<br>`    (DESCRIPTION=`<br>`      (ADDRESS=(PROTOCOL=tcps)(HOST=salesserver1)(PORT=1522))`<br>`      (SECURITY=`<br>`          (SSL_SERVER_DN_MATCH=ON)`<br>`          (SSL_SERVER_CERT_DN="C=US,O=example,CN=OracleContext")`<br>`          (TOKEN_AUTH=OAUTH)`<br>`          (TOKEN_LOCATION="/home/dbuser1/access-token/mytoken"))`<br>`      (CONNECT_DATA=(SERVICE_NAME=sales.us.example.com))`<br>`    )`<br>In the `sqlnet.ora` file:<br>`SSL_SERVER_DN_MATCH=TRUE`<br>`TOKEN_AUTH=OAUTH `<br>`TOKEN_LOCATION="/home/dbuser1/access-token/mytoken"`<br>In these examples, the token file name is `mytoken`. Thus, both the file name and directory path (`/home/dbuser1/access-token`) are specified. The client gets the access token from the `mytoken` file in the specified path. |

**Related Topics**

- [Authenticating and Authorizing IAM Users for Oracle DBaaS Databases](../dbseg/authenticating-and-authorizing-iam-users-oracle-dbaas-databases.md)
- [Authenticating and Authorizing Microsoft Azure Users for Oracle Databases](../dbseg/authenticating-and-authorizing-microsoft-entra-id-ms-ei-users-oracle-databases-oracle-exadata.md)
- [TOKEN_AUTH](local-naming-parameters-in-tns-ora-file.md)

**Parent topic:** sqlnet.ora Profile Parameters

#### 5.2.99 USE_CMAN

##### Purpose

To specify client routing to Oracle Connection Manager.

##### Usage Notes

If set to `true`, then the parameter routes the client to a protocol address for Oracle Connection Manager.

If set to `false`, then the client picks one of the address lists at random and fails over to the other address list if the chosen `ADDRESS_LIST` fails. With `USE_CMAN`=`true`, the client always uses the first address list.

If no Oracle Connection Manager addresses are available, then connections are routed through any available listener address.

##### Default

false

##### Values

    true | false

##### Example

    USE_CMAN=true

**Parent topic:** sqlnet.ora Profile Parameters

#### 5.2.100 USE_DEDICATED_SERVER

##### Purpose

To append `(SERVER=dedicated)` to the `CONNECT_DATA` section of the connect descriptor used by the client.

##### Usage Notes

It overrides the current value of the [SERVER](local-naming-parameters-in-tns-ora-file.md) parameter in the `tnsnames.ora` file.

If set to `on`, then the parameter `USE_DEDICATED_SERVER` automatically appends `(SERVER=dedicated)` to the connect data for a connect descriptor. This way connections from this client use a [dedicated server](glossary.md) process, even if [shared server](glossary.md) is configured.

##### Default

off

##### Values

- `on` to append `(SERVER=dedicated)`

- `off` to send requests to existing server processes

##### Example

    USE_DEDICATED_SERVER=on

**See Also:**

[Oracle Database Net Services Administrator's Guide](../netag/configuring-profiles.md) for complete configuration information

**Parent topic:** sqlnet.ora Profile Parameters

#### 5.2.101 WALLET_LOCATION

Use the `sqlnet.ora` parameter `WALLET_LOCATION` to specify the location of Oracle wallets.

##### Purpose

To specify the directory path where you want to create and store an Oracle wallet. Wallets securely contain certificates, secrets, private keys, and trust points used by Oracle Database.

##### Usage Notes

- The password-protected wallet is stored in an `ewallet.p12` file. The auto-login and local auto-login wallets are stored in a `cwallet.sso` file.

  For example, if an Oracle wallet is stored in the Microsoft Windows registry and the wallet's key `(KEY)` is `SALESAPP`, then the storage location of the password-protected wallet is `HKEY_CURRENT_USER\SOFTWARE\ORACLE\WALLETS\SALESAPP\EWALLET.P12`. The storage location of the auto-login and local auto-login wallets is `HKEY_CURRENT_USER\SOFTWARE\ORACLE\WALLETS\SALESAPP\CWALLET.SSO`.

- The `WALLET_LOCATION` parameter is optional for TLS connections that do not use a client wallet. If `WALLET_LOCATION` is not included in `sqlnet.ora` or connect string, then the driver automatically picks up common root certificates from the client system's default certificate store (if the system is Linux or Windows). In this case, the database server certificate needs to be signed by a trusted root certificate that is already installed in the default certificate store. The default certificate store is located in `/etc/pki/tls/cert.pem` on Linux and Microsoft Certificate Store (MCS) on Windows.

  If `WALLET_LOCATION` is set in `sqlnet.ora` for all connections, then you can override this setting for a particular connection that does not need a client wallet by using `WALLET_LOCATION=SYSTEM` in the connect string (in `tnsnames.ora` or directly to the command line). The database client then uses common root certificates from the default certificate store (instead of the client wallet) to validate the database server certificate.
      net_service_name=
          (DESCRIPTION =
             (ADDRESS=(PROTOCOL=tcps)(HOST=sales-svr)(PORT=1234))
             (SECURITY=(WALLET_LOCATION=SYSTEM))
             (CONNECT_DATA=(SERVICE_NAME=sales.us.example.com))
           )

##### Additional Parameters

`WALLET_LOCATION` supports the following parameters:

- `SOURCE`: Type of storage for wallets (`METHOD`) and storage location (`METHOD_DATA`)

- `METHOD`: Type of storage

- `METHOD_DATA`: Storage location

- `DIRECTORY`: Location of wallet on the file system

- `KEY`: Wallet type and location in the Microsoft Windows registry

- `PROFILE`: Entrust profile file (`.epf`)

- `INIFILE`: Entrust initialization file (`.ini`)

##### Syntax and Examples

The syntax depends on the wallet as follows:

- Wallet on the file system:
      WALLET_LOCATION=
        (SOURCE=
          (METHOD=file)
          (METHOD_DATA=
             (DIRECTORY=directory)
             [(PKCS11=TRUE/FALSE)]))

  For example:
      WALLET_LOCATION=
        (SOURCE=
            (METHOD=file)
            (METHOD_DATA=
               (DIRECTORY=/etc/oracle/wallets/databases)))
- Microsoft certificate store:
      WALLET_LOCATION=
        (SOURCE=
           (METHOD=mcs))

  The key-value pair for MCS omits the `METHOD_DATA` parameter because MCS does not use wallets. Instead, Oracle PKI (public key infrastructure) applications obtain certificates, trust points and private keys directly from a user's profile.
- Wallet in the Microsoft Windows registry:
      WALLET_LOCATION=
         (SOURCE=
            (METHOD=reg)
            (METHOD_DATA=
               (KEY=registry_key)))

  For example:
      WALLET_LOCATION=
         (SOURCE=
           (METHOD=REG)
           (METHOD_DATA=
              (KEY=SALESAPP)))
- Entrust wallets:
      WALLET_LOCATION=
         (SOURCE=
            (METHOD=entr)
            (METHOD_DATA=
               (PROFILE=file.epf)
               (INIFILE=file.ini)))

  For example:
      WALLET_LOCATION=
         (SOURCE=
           (METHOD=entr)
           (METHOD_DATA=
             (PROFILE=/etc/oracle/wallets/example.epf)
             (INIFILE=/etc/oracle/wallets/example.ini)))

##### Default

None

**Related Topics**

- [Oracle Database Enterprise User Security Administrator's Guide](../dbimi/using-oracle-wallet-manager.md)
- [Oracle Database Security Guide](../dbseg/configuring-secure-sockets-layer-authentication.md)

**Parent topic:** sqlnet.ora Profile Parameters

### 5.3 ADR Diagnostic Parameters in sqlnet.ora

Diagnostic data for critical errors is stored in the `sqlnet.ora` Automatic Diagnostic Repository (ADR).

- About ADR Diagnostic Parameters
  You can use Automatic Diagnostic Repository (ADR) diagnostic parameters when ADR is enabled, which is the default. Oracle ignores non-ADR parameters in the `sqlnet.ora` file when you enable ADR.
- ADR_BASE
  It is a diagnostic parameter in the `sqlnet.ora` file and it specifies the base location of the ADR files.
- DIAG_ADR_ENABLED
  `DIAG_ADR_ENABLED` diagnostic parameter of the sqlnet.ora file specifies whether ADR tracing is enabled.
- TRACE_LEVEL_CLIENT
  The `TRACE_LEVEL_CLIENT` diagnostic parameter of the `sqlnet.ora` file turns client tracing on or off at a specified level.
- TRACE_LEVEL_SERVER
  The `TRACE_LEVEL_SERVER` diagnostic parameter of the `sqlnet.ora` file turns server tracing on or off at a specified level.
- TRACE_TIMESTAMP_CLIENT
  The `TRACE_TIMESTAMP_CLIENT` diagnostic parameter of the `sqlnet.ora` file adds a time stamp to every trace event in the client trace file.
- TRACE_TIMESTAMP_SERVER
  The `TRACE_TIMESTAMP_CLIENT` diagnostic parameter of the `sqlnet.ora` file adds a time stamp to every trace event in the database server trace file.

**Parent topic:** Parameters for the sqlnet.ora File

#### 5.3.1 About ADR Diagnostic Parameters

You can use Automatic Diagnostic Repository (ADR) diagnostic parameters when ADR is enabled, which is the default. Oracle ignores non-ADR parameters in the `sqlnet.ora` file when you enable ADR.

Since Oracle Database 11g, Oracle Database includes an advanced fault diagnostic infrastructure to prevent, detect, diagnose, and resolve problems. The problems might be critical errors such as those that are caused by database code bugs, metadata corruption, or customer data corruption.

When critical errors occur, they are assigned incident numbers. Diagnostic data for the errors, such as traces and dumps, are captured and tagged with the incident number. The data is then stored in ADR, which is a file-based repository outside the database.

The following `sqlnet.ora` parameters are used when you enable ADR (when `DIAG_ADR_ENABLED` is set to `on`):

**Parent topic:** ADR Diagnostic Parameters in sqlnet.ora

#### 5.3.2 ADR_BASE

It is a diagnostic parameter in the `sqlnet.ora` file and it specifies the base location of the ADR files.

##### Purpose

To specify the base directory into which tracing and logging incidents are stored when ADR is enabled.

##### Usage Notes

This parameter is applicable only to clients. On the server side, the ADR base location is defined by the `DIAGNOSTIC_DEST` initialization parameter in the `init.ora` file. See [DIAGNOSTIC_DEST](../refrn/DIAGNOSTIC_DEST.md) in Oracle Database Reference.

##### Default

`ORACLE_BASE` or `ORACLE_HOME/log` (if `ORACLE_BASE` is not defined)

##### Values

Any valid directory path to a directory with write permission.

##### Example

`ADR_BASE=/oracle/network/trace`

**Parent topic:** ADR Diagnostic Parameters in sqlnet.ora

#### 5.3.3 DIAG_ADR_ENABLED

`DIAG_ADR_ENABLED` diagnostic parameter of the sqlnet.ora file specifies whether ADR tracing is enabled.

##### Purpose

To specify whether ADR tracing is enabled.

##### Usage Notes

If the `DIAG_ADR_ENABLED` parameter is set to `OFF`, then non-ADR file tracing is used.

##### Default

`on`

##### Values

`on` \| `off`

Example 5-7 Example

`DIAG_ADR_ENABLED=on`

**Parent topic:** ADR Diagnostic Parameters in sqlnet.ora

#### 5.3.4 TRACE_LEVEL_CLIENT

The `TRACE_LEVEL_CLIENT` diagnostic parameter of the `sqlnet.ora` file turns client tracing on or off at a specified level.

##### Purpose

To turn client tracing on at a specified level or to turn it off.

##### Usage Notes

This parameter is also applicable when non-ADR tracing is used.

##### Default

off or 0

##### Values

- `off` or `0` for no trace output

- `user` or `4` for user trace information

- `admin` or `10` for administration trace information

- `support` or `16` for Oracle Support Services trace information

##### Example

    TRACE_LEVEL_CLIENT=user

**Parent topic:** ADR Diagnostic Parameters in sqlnet.ora

#### 5.3.5 TRACE_LEVEL_SERVER

The `TRACE_LEVEL_SERVER` diagnostic parameter of the `sqlnet.ora` file turns server tracing on or off at a specified level.

##### Purpose

To turn server tracing on at a specified level or to turn it off.

##### Usage Notes

This parameter is also applicable when non-ADR tracing is used.

##### Default

off or 0

##### Values

- `off` or `0` for no trace output

- `user` or `4` for user trace information

- `admin` or `10` for administration trace information

- `support` or `16` for Oracle Support Services trace information

##### Example

    TRACE_LEVEL_SERVER=admin

**Parent topic:** ADR Diagnostic Parameters in sqlnet.ora

#### 5.3.6 TRACE_TIMESTAMP_CLIENT

The `TRACE_TIMESTAMP_CLIENT` diagnostic parameter of the `sqlnet.ora` file adds a time stamp to every trace event in the client trace file.

##### Purpose

To add a time stamp in the form of `dd-mmm-yyyy hh:mm:ss:mil` to every trace event in the client trace file, which has a default name of `sqlnet.trc`.

##### Usage Notes

This parameter is also applicable when non-ADR tracing is used.

##### Default

on

##### Values

`on` or `true` \| `off` or `false`

##### Example

    TRACE_TIMESTAMP_CLIENT=true

**Parent topic:** ADR Diagnostic Parameters in sqlnet.ora

#### 5.3.7 TRACE_TIMESTAMP_SERVER

The `TRACE_TIMESTAMP_CLIENT` diagnostic parameter of the `sqlnet.ora` file adds a time stamp to every trace event in the database server trace file.

##### Purpose

To add a time stamp in the form of `dd-mmm-yyyy hh:mm:ss:mil` to every trace event in the database server trace file, which has a default name of `svr_``pid``.trc`.

##### Usage Notes

This parameter is also applicable when non-ADR tracing is used.

##### Default

on

##### Values

`on` or `true` \| `off` or `false`

##### Example

    TRACE_TIMESTAMP_SERVER=true

**Parent topic:** ADR Diagnostic Parameters in sqlnet.ora

### 5.4 Non-ADR Diagnostic Parameters in sqlnet.ora Files

Learn about `sqlnet.ora` parameters that you use when you disable ADR.

This section lists the `sqlnet.ora` parameters that are used when you disable ADR.

**Note:**

The default value of `DIAG_ADR_ENABLED` is `on`. Therefore, the `DIAG_ADR_ENABLED` parameter must explicitly be set to `off` to use non-ADR tracing.

- LOG_DIRECTORY_CLIENT
  Use the `sqlnet.ora` non-ADR diagnostic parameter `LOG_DIRECTORY_CLIENT` to specify the destination directory for client log files.
- LOG_DIRECTORY_SERVER
- LOG_FILE_CLIENT
- LOG_FILE_SERVER
- TRACE_DIRECTORY_CLIENT
  Use the non-ADR diagnostic `sqlnet.ora` parameter `TRACE_DIRECTORY_CLIENT` to specify the destination directory for client trace files.
- TRACE_DIRECTORY_SERVER
- TRACE_FILE_CLIENT
- TRACE_FILE_SERVER
- TRACE_FILEAGE_CLIENT
- TRACE_FILEAGE_SERVER
- TRACE_FILELEN_CLIENT
- TRACE_FILELEN_SERVER
- TRACE_FILENO_CLIENT
- TRACE_FILENO_SERVER
- TRACE_UNIQUE_CLIENT

**Parent topic:** Parameters for the sqlnet.ora File

#### 5.4.1 LOG_DIRECTORY_CLIENT

Use the `sqlnet.ora` non-ADR diagnostic parameter `LOG_DIRECTORY_CLIENT` to specify the destination directory for client log files.

##### Purpose

To specify the destination directory for the client log file. By default, the log file is created in the current working directory.

##### Usage Notes

Use this parameter when ADR is not enabled.

##### Values

Any valid directory path.

##### Example

    LOG_DIRECTORY_CLIENT=/oracle/network/log

**Parent topic:** Non-ADR Diagnostic Parameters in sqlnet.ora Files

#### 5.4.2 LOG_DIRECTORY_SERVER

##### Purpose

To specify the destination directory for the database server log file.

##### Usage Notes

Use this parameter when ADR is not enabled.

##### Default

    ORACLE_HOME/network/trace

##### Values

Any valid directory path to a directory with write permission.

##### Example

    LOG_DIRECTORY_SERVER=/oracle/network/trace

**Parent topic:** Non-ADR Diagnostic Parameters in sqlnet.ora Files

#### 5.4.3 LOG_FILE_CLIENT

##### Purpose

To specify the name of the log file for the client.

##### Usage Notes

Use this parameter when ADR is not enabled.

##### Default

    ORACLE_HOME/network/log/sqlnet.log

##### Values

The default value cannot be changed.

**Parent topic:** Non-ADR Diagnostic Parameters in sqlnet.ora Files

#### 5.4.4 LOG_FILE_SERVER

##### Purpose

To specify the name of the log file for the database server.

##### Usage Notes

Use this parameter when ADR is not enabled.

##### Default

    sqlnet.log

##### Values

Any valid directory path to a directory with write permission.

##### Example

    LOG_FILE_SERVER=svr.log

**Parent topic:** Non-ADR Diagnostic Parameters in sqlnet.ora Files

#### 5.4.5 TRACE_DIRECTORY_CLIENT

Use the non-ADR diagnostic `sqlnet.ora` parameter `TRACE_DIRECTORY_CLIENT` to specify the destination directory for client trace files.

##### Purpose

To specify the destination directory for the client trace file. By default, the trace file is created in the current working directory.

##### Usage Notes

Use this parameter when ADR is not enabled.

##### Values

Any valid directory path to a directory with write permission.

##### Example

    TRACE_DIRECTORY_CLIENT=/oracle/traces

**Parent topic:** Non-ADR Diagnostic Parameters in sqlnet.ora Files

#### 5.4.6 TRACE_DIRECTORY_SERVER

##### Purpose

To specify the destination directory for the database server trace file. Use this parameter when ADR is not enabled.

##### Default

     ORACLE_HOME/network/trace

##### Values

Any valid directory path to a directory with write permission.

##### Example

    TRACE_DIRECTORY_SERVER=/oracle/traces

**Parent topic:** Non-ADR Diagnostic Parameters in sqlnet.ora Files

#### 5.4.7 TRACE_FILE_CLIENT

##### Purpose

To specify the name of the client trace file.

##### Usage Notes

Use this parameter when ADR is not enabled.

##### Default

    ORACLE_HOME/network/trace/cli.trc

##### Values

Any valid file name.

##### Example

    TRACE_FILE_CLIENT=clientsqlnet.trc

**Parent topic:** Non-ADR Diagnostic Parameters in sqlnet.ora Files

#### 5.4.8 TRACE_FILE_SERVER

##### Purpose

To specify the destination directory for the database server trace output.

##### Usage Notes

Use this parameter when ADR is not enabled.

##### Default

    ORACLE_HOME/network/trace/svr_pid.trc

##### Values

Any valid file name. The process identifier (pid) is appended to the name automatically.

##### Example

    TRACE_FILE_SERVER=svrsqlnet.trc

**Parent topic:** Non-ADR Diagnostic Parameters in sqlnet.ora Files

#### 5.4.9 TRACE_FILEAGE_CLIENT

##### Purpose

To specify the maximum age of client trace files in minutes.

##### Usage Notes

When the age limit is reached, the trace information is written to the next file. The number of files is specified with the TRACE_FILENO_CLIENT parameter. Use this parameter when ADR is not enabled.

##### Default

Unlimited

This is the same as setting the parameter to `0`.

Example 5-8 Example

`TRACE_FILEAGE_CLIENT=60`

**Parent topic:** Non-ADR Diagnostic Parameters in sqlnet.ora Files

#### 5.4.10 TRACE_FILEAGE_SERVER

##### Purpose

To specify the maximum age of database server trace files in minutes.

##### Usage Notes

When the age limit is reached, the trace information is written to the next file. The number of files is specified with the TRACE_FILENO_SERVER parameter. Use this parameter when ADR is not enabled.

##### Default

Unlimited

This is the same as setting the parameter to`0`.

Example 5-9 Example

`TRACE_FILEAGE_SERVER=60`

**Parent topic:** Non-ADR Diagnostic Parameters in sqlnet.ora Files

#### 5.4.11 TRACE_FILELEN_CLIENT

##### Purpose

To specify the size of the client trace files in kilobytes (KB).

##### Usage Notes

When the size is met, the trace information is written to the next file. The number of files is specified with the TRACE_FILENO_CLIENT parameter. Use this parameter when ADR is not enabled.

##### Example

    TRACE_FILELEN_CLIENT=100

**Parent topic:** Non-ADR Diagnostic Parameters in sqlnet.ora Files

#### 5.4.12 TRACE_FILELEN_SERVER

##### Purpose

To specify the size of the database server trace files in kilobytes (KB).

##### Usage Notes

When the size is met, the trace information is written to the next file. The number of files is specified with the TRACE_FILENO_SERVER parameter. Use this parameter when ADR is not enabled.

##### Example

    TRACE_FILELEN_SERVER=100

**Parent topic:** Non-ADR Diagnostic Parameters in sqlnet.ora Files

#### 5.4.13 TRACE_FILENO_CLIENT

##### Purpose

To specify the number of trace files for client tracing.

##### Usage Notes

When this parameter is set with the TRACE_FILELEN_CLIENT parameter, trace files are used in a cyclical fashion. The first file is filled first, then the second file, and so on. When the last file has been filled, then the first file is re-used, and so on.

When this parameter is set with theTRACE_FILEAGE_CLIENT parameter, trace files are cycled based on their age. The first file is used until the age limit is reached, then the second file is used, and so on. When the last file's age limit is reached, the first file is re-used, and so on.

When this parameter is set with both the TRACE_FILELEN_CLIENT and TRACE_FILEAGE_CLIENT parameters, trace files are cycled when either the size limit or the age limit is reached.

The trace file names are distinguished from one another by their sequence number. For example, if the default trace file of `sqlnet.trc` is used, and this parameter is set to 3, then the trace files would be named `sqlnet1.trc`, `sqlnet2.trc` and `sqlnet3.trc`.

In addition, trace events in the trace files are preceded by the sequence number of the file. Use this parameter when ADR is not enabled.

##### Default

None

##### Example

    TRACE_FILENO_CLIENT=3

**Parent topic:** Non-ADR Diagnostic Parameters in sqlnet.ora Files

#### 5.4.14 TRACE_FILENO_SERVER

##### Purpose

To specify the number of trace files for database server tracing.

##### Usage Notes

When this parameter is set with the TRACE_FILELEN_SERVER parameter, trace files are used in a cyclical fashion. The first file is filled first, then the second file, and so on. When the last file has been filled, then the first file is re-used, and so on.

When this parameter is set with theTRACE_FILEAGE_SERVER parameter, trace files are cycled based on the age of the trace file. The first file is used until the age limit is reached, then the second file is used, and so on. When the last file's age limit is reached, the first file is re-used, and so on.

When this parameter is set with both the TRACE_FILELEN_SERVER and TRACE_FILEAGE_SERVER parameters, trace files are cycled when either the size limit or the age limit is reached.

The trace file names are distinguished from one another by their sequence number. For example, if the default trace file of `svr_``pid``.trc` is used, and this parameter is set to 3, then the trace files would be named `svr1_``pid``.trc`, `svr2_``pid``.trc` and `svr3_``pid``.trc`.

In addition, trace events in the trace files are preceded by the sequence number of the file. Use this parameter when ADR is not enabled.

##### Default

None

##### Example

    TRACE_FILENO_SERVER=3

**Parent topic:** Non-ADR Diagnostic Parameters in sqlnet.ora Files

#### 5.4.15 TRACE_UNIQUE_CLIENT

##### Purpose

To specify whether a unique trace file is created for each client trace session.

##### Usage Notes

When the value is set to `on`, a process identifier is appended to the name of each trace file, enabling several files to coexist. For example, trace files named `sqlnet``pid``.trc` are created if default trace file name `sqlnet.trc` is used. When the value is set to `off`, data from a new client trace session overwrites the existing file. Use this parameter when ADR is not enabled.

##### Default

on

##### Values

`on` or `off`

##### Example

    TRACE_UNIQUE_CLIENT=on

**Parent topic:** Non-ADR Diagnostic Parameters in sqlnet.ora Files
