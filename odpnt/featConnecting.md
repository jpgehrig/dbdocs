Oracle Data Provider for .NET can connect to Oracle Database in a number of ways, such as using a user name and password, Windows Native Authentication, Kerberos, and Transport Layer Security/Secure Sockets Layer. This section describes `OracleConnection` provider-specific features, including:

- Connecting to Oracle Database Cloud Service

- Connection String Attributes

- Connection String Builder

- Specifying the Data Source Attribute

- Using Transport Layer Security and Secure Sockets Layer

- Using Secure External Password Store

- Using Kerberos

- Using Windows Native Authentication (NTS)

- Network Data Encryption and Integrity

- Schema Discovery

- Connection Pooling

- Connection Pool Management

- Connection Performance Counters

- Database Resident Connection Pooling

- Oracle Multitenant and Pluggable Databases

- Edition-Based Redefinition

- Operating System Authentication

- Privileged Connections

- Connection Pooling with OracleCredential

- Password Expiration

- Proxy Authentication

- Dynamic Distributed Transaction Enlistment

- Client Identifier and End-to-End Tracing

- Transparent Application Failover (TAF) Callback Support

### Connecting to Oracle Database Cloud Service

ODP.NET Core, managed, and unmanaged drivers all support connectivity with Oracle Database Cloud Services, including Oracle Autonomous Database.

#### Set-up Instructions

Oracle recommends using the latest ODP.NET version available when connecting to Oracle Database Cloud Services. You will find instructions about how to download, install, and configure ODP.NET and Oracle Developer Tools for Visual Studio below.

Oracle Autonomous Database: <https://www.oracle.com/technetwork/topics/dotnet/tech-info/default-5032178.html>

Oracle Database as a Service: <https://www.oracle.com/technetwork/topics/dotnet/dotnetdbaas-3208838.html>

### Connection String Attributes

Table 3-2 lists the supported connection string attributes.

Table 3-2 Supported Connection String Attributes

| Connection String Attribute | Description                                                                                                                                                                                                                                                                               | Default Value |
|:----------------------------|:------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|:--------------|
| `Application Continuity`    | Enables database requests to automatically replay transactional or non-transactional operations in a non-disruptive and rapid manner in the event of a severed database session, which results in a recoverable error.<br>Not Available in ODP.NET, Managed Driver and ODP.NET Core       | `true`        |
| `Connection Lifetime`       | Minimum life time (in seconds) of the connection.                                                                                                                                                                                                                                         | `0`           |
| `Connection Timeout`        | The time to wait (in seconds) for a new connection or an idle connection from the connection pool before a connection time out error can occur.                                                                                                                                           | `15`          |
| `Context Connection`        | Returns an implicit database connection if set to `true`.<br>Supported in a .NET stored procedure only                                                                                                                                                                                    | `false`       |
| `Data` `Source`             | Oracle Net Services Name, Connect Descriptor, or an easy connect naming that identifies the database to which to connect.                                                                                                                                                                 | empty string  |
| `DBA Privilege`             | Administrative privileges: `SYSDBA` or `SYSOPER`.                                                                                                                                                                                                                                         | empty string  |
| `Decr Pool Size`            | Number of connections that are closed when an excessive amount of established connections are unused.                                                                                                                                                                                     | `1`           |
| `Enlist`                    | Controls the enlistment behavior and capabilities of a connection in context of COM+ transactions or `System.Transactions`.                                                                                                                                                               | `true`        |
| `HA` `Events`               | Enables ODP.NET connection pool to proactively remove connections from the pool when an Oracle database service, service member, instance, or node goes down. Works with Oracle Global Data Services, including Oracle RAC, Data Guard, GoldenGate, and some single instance deployments. | `true`        |
| `Load` `Balancing`          | Enables ODP.NET connection pool to balance work requests across Oracle database instances based on the load balancing advisory and service goal. Works with Oracle Global Data Services, including Oracle RAC, Active Data Guard, and GoldenGate.                                         | `true`        |
| `Incr Pool Size`            | Number of new connections to be created when all connections in the pool are in use.                                                                                                                                                                                                      | `5`           |
| `Max Pool Size`             | Maximum number of connections in a pool.                                                                                                                                                                                                                                                  | `100`         |
| `Metadata` `Pooling`        | Caches metadata information.                                                                                                                                                                                                                                                              | `True`        |
| `Min` `Pool` `Size`         | Minimum number of connections in a pool.                                                                                                                                                                                                                                                  | `1`           |
| `Password`                  | Password for the user specified by `User` `Id`.                                                                                                                                                                                                                                           | empty string  |
| `Persist` `Security` `Info` | Retrieval of the password in the connection string.                                                                                                                                                                                                                                       | `false`       |
| `Pooling`                   | Connection pooling.                                                                                                                                                                                                                                                                       | `true`        |
| `Promotable` `Transaction`  | Indicates whether or not a transaction is local or distributed throughout its lifetime.                                                                                                                                                                                                   | promotable    |
| `Proxy` `User` `Id`         | User name of the proxy user.                                                                                                                                                                                                                                                              | empty string  |
| `Proxy` `Password`          | Password of the proxy user.                                                                                                                                                                                                                                                               | empty string  |
| `Self Tuning`               | Enables or disables self-tuning for a connection.                                                                                                                                                                                                                                         | `true`        |
| `Statement` `Cache` `Purge` | Statement cache purged when the connection goes back to the pool.                                                                                                                                                                                                                         | `false`       |
| `Statement` `Cache` `Size`  | Statement cache enabled and cache size, that is, the maximum number of statements that can be cached.                                                                                                                                                                                     | `0`           |
| `User` `Id`                 | Oracle user name.                                                                                                                                                                                                                                                                         | empty string  |
| `Validate` `Connection`     | Validation of connections coming from the pool.                                                                                                                                                                                                                                           | `false`       |

The following example uses connection string attributes to connect to Oracle Database:

    // C#

    using System;
    using Oracle.DataAccess.Client;

    class ConnectionSample
    {
      static void Main()
      {
        OracleConnection con = new OracleConnection();

        //using connection string attributes to connect to Oracle Database
        con.ConnectionString = "User Id=scott;Password=tiger;Data Source=oracle";
        con.Open();
        Console.WriteLine("Connected to Oracle" + con.ServerVersion);

        // Close and Dispose OracleConnection object
        con.Close();
        con.Dispose();
        Console.WriteLine("Disconnected");
      }
    }


**See Also:**

- "[OracleConnection Properties](ConnectionProperties.md)" for detailed information on connection attributes

- "[OracleCommand Object](featOraCommand.md)" for detailed information on statement caching

### Connection String Builder

The `OracleConnectionStringBuilder` class makes creating connection strings less error-prone and easier to manage.

Using this class, developers can employ a configuration file to provide the connection string and/or dynamically set the values though the key/value pairs. One example of a configuration file entry follows:

    <configuration>
       <connectionStrings>
    <add name="Publications" providerName="Oracle.DataAccess.Client"
               connectionString="User Id=scott;Password=tiger;Data Source=inst1" />
       </connectionStrings>
    </configuration>

Connection string information can be retrieved by specifying the connection string name, in this example, `Publications`. Then, based on the `providerName`, the appropriate factory for that provider can be obtained. This makes managing and modifying the connection string easier. In addition, this provides better security against string injection into a connection string.

**See Also:**

[OracleConnectionStringBuilder Class](OracleConnectionStringBuilderClass.md)

### Specifying the Data Source Attribute

This section describes different ways of specifying the data source attribute.

The following example shows a connect descriptor mapped to a TNS alias called `sales` in the `tnsnames.ora` file:

    sales=
     (DESCRIPTION=
      (ADDRESS= (PROTOCOL=tcp)(HOST=sales-server)(PORT=1521))
      (CONNECT_DATA=
         (SERVICE_NAME=sales.us.acme.com)))

The connection pool will maintain the full descriptor of an alias so that subsequent connection requests with the same connection string will not need to resolve the alias again. This applies to `tnsnames.ora`, .NET config data sources, and LDAP aliases. To flush out the cached full descriptor maintained by the connection pool, invoke `OracleDataSourceEnumerator.GetDataSources()` followed by `OracleConnection.ClearPool()` or `OracleConnection.ClearAllPools()`.

If connection pooling is not used, the alias will need to be resolved to the full descriptor for each request. In the case of LDAP, the LDAP server is contacted for each connection request.

#### Using the TNS Alias

To connect as `scott/tiger` using the TNS Alias, a valid connection appears as follows:

    "user id=scott;password=tiger;data source=sales";

#### Using the Connect Descriptor

ODP.NET also allows applications to connect without the use of the `tnsnames.ora` file. To do so, the entire connect descriptor can be used as the `"data` `source"`.

The connection string appears as follows:

    "user id=scott;password=tiger;data source=" +
         "(DESCRIPTION=(ADDRESS=(PROTOCOL=tcp)" +
         "(HOST=sales-server)(PORT=1521))(CONNECT_DATA="+
         "(SERVICE_NAME=sales.us.acme.com)))"

#### Easy Connect and Easy Connect Plus Naming Methods

The Easy Connect and Easy Connect Plus naming methods enable clients to connect to a database without any configuration.

To use the Easy Connect naming method, ensure that `EZCONNECT` is specified by the `NAMES.DIRECTORY_PATH` parameter in the `sqlnet.ora` file as follows:

    NAMES.DIRECTORY_PATH= (TNSNAMES, EZCONNECT)

With this enabled, ODP.NET allows applications to specify the `Data Source` attribute in the form of:

    //host:[port]/[service_name]

Using the same example, some valid connection strings follow:

    "user id=scott;password=tiger;data source=//sales-server:1521/sales.us.acme.com"
    "user id=scott;password=tiger;data source=//sales-server/sales.us.acme.com"
    "user id=scott;password=tiger;data source=sales-server/sales.us.acme.com"

If the port number is not specified, 1521 is used by default.

Easy Connect has been enhanced in ODP.NET 19c to support a wider application breadth, including clustered or cloud databases, and for ease of use. These improvements are called Easy Connect Plus and its features include:

- TCP/IP with SSL/TLS

- Any SQL\*Net description level parameter can be used

- Multiple hosts and ports

- A straightforward name-value pair format

The syntax uses the question mark symbol `?` to indicate the name-value pairs start and the ampersand symbol `&` to delimit each name-value pair. The entire connect string must be specified as a single string. Leading and trailing white spaces are ignored within parameter values. If whitespace is required as part of the value, it should be placed within double-quotes.

Easy Connect Plus syntax:

    [[protocol:]//]host1{,host12}[:port1]{,host2:port2}[/service_name][:server][/instance_name][?parameter_name=value{&parameter_name=value}]

Easy Connect Plus samples:

- tcps://salesserver1:1521/sales.us.example.com

- salesserver1:1521,salesserver2,salesserver3:1522/sales.us.example.com

- tcps://salesserver1:1521/sales.us.example.com?wallet_location=D:/oracle

- tcps://salesserver1:1521/sales.us.example.com?ssl_server_cert_dn=cn=sales,cn=OracleContext,dc=us,dc=example,dc=com

- tcps://salesserver1:1521/sales.us.example.com?https_proxy=www-proxy.mycompany.com&https_proxy_port=80

- salesserver1:1521/sales.us.example.com?connect_timeout=60&transport_connect_timeout=30&retry_count=3

**See Also:**

[Oracle Database Net Services Administrator's Guide](../netag/configuring-naming-methods.md) for details and requirements in the section Using Easy Connect Naming Method

#### Using LDAP

ODP.NET can connect with connect identifiers mapped to connect descriptors in an LDAP-compliant directory server, such as Oracle Internet Directory and Microsoft Active Directory.

To configure LDAP for ODP.NET, Unmanaged Driver, follow these Oracle documentation instructions in Configuring the Directory Naming Method in [Oracle Database Net Services Administrator's Guide](../netag/configuring-naming-methods.md).

To configure LDAP for ODP.NET, Managed Driver, follow the instructions in "[settings section](InstallManagedConfig.md)" and "[LDAPsettings section](InstallManagedConfig.md)."

Beginning with Oracle Database release 18c, version 18.1, organizations can use centrally managed users (CMUs) with Active Directory. This feature is designed for organizations who prefer to use Active Directory as their centralized identity management solution. Organizations can use Kerberos, PKI, or password authentication with CMU and Active Directory.

**See Also:**

[Oracle Database Net Services Administrator's Guide](../netag/configuring-naming-methods.md) and [Oracle Database Security Guide](../dbseg/configuring-authentication.md) for details and requirements in the section Using LDAP

#### Data Source Enumerator

The data source enumerator enables the application to generically obtain a collection of the Oracle data sources that the application can connect to.

**See Also:**

"[OracleDataSourceEnumerator Class](OracleDataSourceEnumeratorClass.md)"

### Using Transport Layer Security and Secure Sockets Layer

Transport Layer Security (TLS) and its predecessor, Secure Sockets Layer (SSL), are industry standard protocols for securing network connections. Both managed and unmanaged ODP.NET support SSL for database and transport authentication.

#### Secure Sockets Layer and Transport Layer Security Differences

Although SSL was primarily developed by Netscape Communications Corporation, the Internet Engineering Task Force (IETF) took over development of it, and renamed it Transport Layer Security (TLS).

Essentially, TLS is an incremental improvement to SSL version 3.0.

ODP.NET, Managed Driver supports SSL 3.0 and TLS 1.0, 1.1, and 1.2. ODP.NET, Unmanaged Driver supports the same SSL and TLS versions as the Oracle Database Client version it is certified with.

The SSL/TLS client can ensure that the distinguished name (DN) is correct for the database server it is trying to connect to. Parameters for DN Matching are `SSL_SERVER_DN_MATCH` (`sqlnet.ora`) and `SSL_SERVER_CERT_DN` (`tnsnames.ora`), which can be defined in the .NET config file as well.

To turn DN Match on, set `SSL_SERVER_DN_MATCH` to `True` (or `On` or `Yes`). `SSL_SERVER_CERT_DN` is optional. It allows the administrator to specify exactly the DN they want to match. If the `SSL_SERVER_CERT_DN` is not set, then the match is done by comparing the `SERVICE_NAME` value to the Common Name (CN) portion of the server certificate's DN.

**See Also:**

- The TLS Protocol Version 1.0 \[RFC 2246\] at the IETF Web site, which can be found at:

  [`http://www.ietf.org`](https://www.oracle.com/pls/topic/lookup?ctx=en/database/oracle/oracle-database/19/odpnt&id=ietff_org)

- `SSL_VERSION` in the "[settings section](InstallManagedConfig.md)."

**Note:**

To simplify the discussion, this section uses the term SSL where either SSL or TLS may be appropriate because SSL is the most widely recognized term. However, where distinctions occur between how you use or configure these protocols, this section specifies what is appropriate for either SSL or TLS.

#### ODP.NET Secure Sockets Layer Configuration

When you configure Secure Sockets Layer on the client, you must confirm that the wallet is created and use TCP/IP with SSL on the client. Optionally, you can perform additional steps to enhance the configuration.

##### SSL Configuration Topics:

- Step 1: Confirm Client Wallet Creation

- Step 2: Use TCP/IP with SSL on the Client

- Step 3: Specify Required Client SSL Configuration (Wallet Location)

- Step 4: Set the Required SSL Version on the Client (Optional)

- Step 5: Set SSL as an Authentication Service on the Client (Optional)

##### Step 1: Confirm Client Wallet Creation

Before proceeding to the next step, you must confirm that a wallet has been created on the client and that the client has a valid certificate.

ODP.NET, Managed Driver supports file and Microsoft Certificate Store (MCS) based wallets.

- For file-based wallets, use Oracle Wallet Manager to check that the wallet has been created. See Step 1A: Confirm Wallet Creation on the Server in [Oracle Database Security Guide](../dbseg/configuring-secure-sockets-layer-authentication.md) for information about checking a wallet.

- For MCS, the Windows domain credentials will be used for the client credentials. Thus, a valid domain logon must be used while running the ODP.NET application. ODP.NET, Managed Driver will retrieve the credentials from the MY or Personal certificate store. Note that the server must also be configured to use MCS wallets. See Microsoft Certificate Services in [Oracle Database Platform Guide for Microsoft Windows](../ntqrf/about-microsoft-certificate-services.md) for information about setting up the server for MCS.

##### Step 2: Use TCP/IP with SSL on the Client

The ODP.NET Data Source must be modified to use SSL. Specifically, the transport protocol must be changed to use TCP/IP with SSL or what Oracle calls "tcps". An example ODP.NET Data Source for use with SSL is:

    finance = (DESCRIPTION=
      (ADDRESS = (PROTOCOL=tcps) (HOST=finance_server) (PORT=1575) )
      (CONNECT_DATA = (SERVICE_NAME=Finance.us.example.com) ) )

##### Step 3: Specify Required Client SSL Configuration (Wallet Location)

Edit the `sqlnet.ora` or .NET application configuration to specify the wallet location.

- An example of setting the SSL wallet location for file based wallets, where `<wallet_location>` is the specified location where the client wallet is stored:

      wallet_location = (SOURCE=(METHOD= File)
                                (METHOD_DATA=(DIRECTORY=<wallet_location>)))

- An example of setting the SSL wallet location for MCS based wallets is:

      wallet_location = (SOURCE=(METHOD= MCS))

##### Step 4: Set the Required SSL Version on the Client (Optional)

The `SSL_VERSION` parameter can be set through the `sqlnet.ora` or the .NET `application.config`, `web.config`, or `machine.config` file. Normally, it is not necessary to set this parameter. The default setting for this parameter is `any`, which allows the database server to apply any necessary restrictions to the SSL version accepted. An example setting in the `sqlnet.ora` is:

    SSL_VERSION=3.0

##### Step 5: Set SSL as an Authentication Service on the Client (Optional)

Set the `SQLNET.AUTHENTICATION_SERVICES` parameter in the `sqlnet.ora` or `application.config`, `web.config`, or `machine.config` file to allow SSL to be used as a database external authentication methodology.

Note that SSL can be used as just a transport encryption vehicle. Hence, the "optional" designation for this setting.

If SSL is to be used as a database external Authentication Service, then a database externally authenticated user matching the client certificate must be created.

An example setting allowing SSL external authentication in the `sqlnet.ora` is:

    SQLNET.AUTHENTICATION_SERVICES = (TCPS)

**Note:**

Prior to ODAC 12c Release 4, ODP.NET, Managed Driver SSL connections would be redirected to dynamic (ephemeral) port on the database server machine. With ODAC 12c Release 4 and later, managed ODP.NET SSL connections will now continue to the original socket connection to the Oracle Listener. Hence, firewalls will now only need to allow access to the Oracle Listener's port (e.g., 1521).

**See Also:**

- Enabling Secure Sockets Layer in [Oracle Database Security Guide](../dbseg/configuring-secure-sockets-layer-authentication.md) for more information about TLS/SSL and configuration with Oracle database.

- Creating a User Who Is Authenticated Externally in [Oracle Database Security Guide](../dbseg/configuring-authentication.md) for more information about creating externally identified database users.

#### Troubleshooting TLS/SSL Setup

This section discusses commonly encountered issues and their typical resolution steps.

##### Common TLS/SSL Wallet Errors

Microsoft Windows now restricts wallets from using the MD5 algorithm. Oracle wallets may have been generated with this algorithm as that was the default option in Oracle Public Key Infrastructure (`orapki`) utility 12.1 and earlier.

Orapki refers to `orapki.exe`. This utility is part of full Oracle client (administrator) installations. It is not included with Oracle Instant Client. The utility is only needed to setup up the wallet; it is not necessary to deploy it with the wallet.

When you setup TLS/SSL and encounter an "ORA-0052: Failure during SSL handshake" error combined with a 0x80004005 error code and first inner exception "A SSPI-call failed" and second inner exception "A token sent to the function is invalid", then it is very likely that Microsoft Security Support Provider Interface (SSPI) rejected your Oracle Wallet, such as when MD5 is used. This is a failure on the handshake. You can resolve this error by using the SHA-2 algorithm instead.

If the second inner exception instead indicates "The credentials supplied to the package were not recognized", it is possible the user certificate was generated without a certificate authority (CA). You can resolve this error by using `orapki` to generate a CA/root certificate and then regenerating your user wallet/certificate to point to this new CA/root certificate.

The steps below will regenerate your Oracle Wallet using `orapki` and SHA-2. Any `orapki` version can be used to generate the wallet with these instructions.

1.  Create root wallet, for example, a CA wallet.

        orapki wallet create -wallet ./root -pwd <password>

2.  Add a self-signed certificate (CA certificate) to the root wallet.

        orapki wallet add -wallet ./root -dn 'CN=<my root>' -keysize 1024 -self_signed -validity 3650 -pwd <password> -sign_alg sha512

3.  Export the self-signed certificate from the wallet.

        orapki wallet export -wallet ./root -dn 'CN=<my root>' -cert ./root/b64certificate.txt -pwd <password>

4.  Create a user wallet, for example, a customer wallet.

        orapki wallet create -wallet ./user -pwd <password> -auto_login

5.  Add a certificate request.

        orapki wallet add -wallet ./user -dn 'CN=<client's hostname>' -keysize 1024 -pwd <password> -sign_alg sha512

6.  Export the certificate request.

        orapki wallet export -wallet ./user -dn 'CN=<client's hostname>' -request ./user/creq.txt -pwd <password>

7.  Create a certificate issued by a CA.

        orapki cert create -wallet ./root -request ./user/creq.txt -cert ./user/cert.txt -validity 3650 -pwd <password> -sign_alg sha512

8.  Add a trusted certificate (CA certificate) to the wallet. This example assumes the same CA for both the client and server wallets.

        orapki wallet add -wallet ./user -trusted_cert -cert ./root/b64certificate.txt -pwd <password>

9.  Add a user certificate.

        orapki wallet add -wallet ./user -user_cert -cert ./user/cert.txt -pwd <password> -sign_alg sha512

10. Display contents of user wallet.

        orapki wallet display -wallet ./user -pwd <password>

11. Create a server wallet.

        orapki wallet create -wallet ./server -pwd <password> -auto_login

12. Add a server certificate request.

        orapki wallet add -wallet ./server -dn 'CN=<server's hostname>' -keysize 1024 -pwd <password> -sign_alg sha512

13. Export the certificate request.

        orapki wallet export -wallet ./server -dn 'CN=<server's hostname>' -request ./server/creq.txt -pwd <password>

14. Create a server certificate issued by a CA.

        orapki cert create -wallet ./root -request ./server/creq.txt -cert ./server/cert.txt -validity 3650 -pwd <password> -sign_alg sha512

15. Add a trusted certificate (CA certificate) to the server wallet. This example assumes the same CA for both the client and server wallets.

        orapki wallet add -wallet ./server -trusted_cert -cert ./root/b64certificate.txt -pwd <password>

16. Add an `user_cert` certificate for the server wallet.

        orapki wallet add -wallet ./server -user_cert -cert ./server/cert.txt -pwd <password> -sign_alg sha512

17. Display contents of server wallet.

        orapki wallet display -wallet ./server -pwd <password>

#### HTTPS Proxy for Cloud Connections

ODP.NET supports HTTPS proxy configuration. The feature enables tunneling secure connections over forward HTTP proxy using the HTTP CONNECT method.

HTTPS proxy improves public cloud database service access as it eliminates requiring the client side firewall to open an outbound port.

This feature only works when using TCP/IP with SSL/TLS, which can be enabled in the connect descriptor (e.g. `PROTOCOL=TCPS` in` tnsnames.ora`). It is similar to the web browser setting for intranet users who connect to internet hosts.

To configure HTTPS proxy, use the following for each provider type:

- ODP.NET Core - `OracleConfiguration HttpsProxy`, `HttpsProxyPort`, and `UseHttpsProxy` properties

- Managed ODP.NET - .NET configuration file properties `HTTPS_PROXY`, `HTTPS_PROXY_PORT`, and `USE_HTTPS_PROXY`

- Unmanaged ODP.NET – modify the `tnsnames.ora`, `HTTPS_PROXY`, and `HTTPS_PROXY_PORT` values and `SQLNET.USE_HTTPS_PROXY` value, such as

      (DESCRIPTION=ADDRESS=(
      HTTPS_PROXY= www-proxy.mycompany.com)(HTTPS_PROXY_PORT=8080)(PROTOCOL=TCPS)(HOST=sales2-svr)(PORT=443))
      (CONNECT_DATA=(SERVICE_NAME=sales.us.example.com)))

  `SQLNET.USE_HTTPS_PROXY` should be set to `on`.

### Using Secure External Password Store

The Secure External Password Store (SEPS) is the use of a client-side wallet for securely storing the password credentials. Both ODP.NET, Managed Driver and Unmanaged Driver can be configured to use the external password store.

An Oracle wallet is a container that securely stores authentication and signing credentials. Wallets can simplify large-scale deployments that rely on password credentials for database connections. Applications no longer need embedded user names and passwords, which reduces security risk.

**Note:**

ODP.NET Core supports SEPS on Windows only.

#### Configuring Secure External Password Store (SEPS)

Steps for configuring SEPS:

- Step 1. Create the wallet file

- Step 2. Point the configuration to the client wallet

- Step 3. Turn on SEPS

##### Step 1. Create the wallet file

Use the `mkstore` utility to create the wallet file and insert the credentials.

Step 1a. Create a wallet on the client by using the following syntax at the command line:

    mkstore -wrl wallet_location -create

For example:

    mkstore -wrl c:\oracle\product\12.1.0\db_1\wallets -create
    Enter password: password

Step 1b. Create database connection credentials in the wallet by using the following syntax at the command line:

    mkstore -wrl wallet_location -createCredential db_connect_string username
    Enter password: password

For example:

    mkstore -wrl c:\oracle\product\12.1.0\db_1\wallets -createCredential orcl system
    Enter password: password

##### Step 2. Point the configuration to the client wallet

In the client `sqlnet.ora` file, enter the `WALLET_LOCATION` parameter and set it to the directory location of the wallet you created in Step 1.

For example, if you created the wallet in `$ORACLE_HOME/network/admin` and your Oracle home is set to `C:\app\client\``<user>``\product\``<version>``\client_1\`, then you need to enter the following into your client `sqlnet.ora` file:

    WALLET_LOCATION =
      (SOURCE =(METHOD = FILE)
               (METHOD_DATA =
                  (DIRECTORY = C:\app\client\<user>\product\<version>\client_1\Network\Admin) ) )

##### Step 3. Turn on SEPS

Step 3. Turn on SEPS

    SQLNET.WALLET_OVERRIDE = TRUE

This setting causes all `CONNECT /@db_connect_string` statements to use the information in the wallet at the specified location to authenticate to databases.

When external authentication is in use, an authenticated user with such a wallet can use the `CONNECT /@db_connect_string` syntax to access the previously specified databases without providing a user name and password. Note however, that the wallet file needs to be kept up to date with the database credentials. If the database credentials change, but the wallet file is not changed appropriately, then the connections will fail.

**See Also:**

- [Oracle Data Provider for .NET, Managed Driver Configuration](InstallManagedConfig.md) for more details about the wallet settings.

- Managing the Secure External Password Store for Password Credentials in [Oracle Database Security Guide](../dbseg/configuring-secure-sockets-layer-authentication.md) for more information about secure external password store and configuration with Oracle database.

### Using Kerberos

Kerberos is a network authentication service for security in distributed environments. ODP.NET applications can use Kerberos for single sign-on and centralized user authentication. ODP.NET, Unmanaged Driver and Managed Driver both support Kerberos for external authentication to the database server.

**Note:**

ODP.NET Core does not support Kerberos

Managed ODP.NET does not support Kerberos constrained delegation

#### File Based Credential Cache and MSLSA

ODP.NET supports both a file-based Kerberos client credential cache (CC) and the ability to use Windows logon credentials as Kerberos client credentials. The latter is called MSLSA-based Kerberos authentication.

In order to utilize a file based Kerberos client credential cache (CC), the following executables associated with the full Oracle Call Interface (OCI) install are needed:

- `okinit.exe`

- `oklist.exe`

- `okdstry.exe`

The executables are required in order to acquire the Kerberos5 credentials and store them in the file based credential cache (CC). However, after credential cache creation, as long as the credentials remain valid, the above executables are then unneeded by the ODP.NET application at run-time.

#### ODP.NET, Managed Driver Dependency on MIT Kerberos

To use Kerberos5 database authentication in conjunction with ODP.NET, Managed Driver, download and install MIT Kerberos for Windows 4.0.1 on the same machine as ODP.NET, Managed Driver from the following location:

[`http://web.mit.edu/kerberos/dist/`](https://www.oracle.com/pls/topic/lookup?ctx=en/database/oracle/oracle-database/19/odpnt&id=configuring_kerberos)

**See Also:**

Configuring Kerberos Authentication in [Oracle Database Security Guide](../dbseg/configuring-kerberos-authentication.md) for more information about Kerberos and configuration with Oracle database.

#### Configuring Kerberos Authentication with ODP.NET

Please reference the following "key" when viewing the below Kerberos configuration examples:

- `oracleclient` = Kerberos/Windows Domain user ID used by the Oracle database client program to represent the Oracle Client user on the domain

- `oracleserver` = Kerberos/Windows Domain user ID used by the Oracle database server

- `DOMAIN.COMPANY.COM` = Kerberos/Windows domain

- `dbhost.company.com` = Oracle database server machine hostname

- `kerberos_service_name` = Kerberos service name

- `dc.company.com` = hostname for Kerberos Key Distribution Center (KDC) and Windows Domain Controller

##### Configuring Kerberos Authentication Topics:

- Step 1. Update Windows services file to include a "kerberos5" entry

- Step 2. Create client and server Kerberos users (Windows domain users for MSLSA)

- Step 3. Associate the DB server's Kerberos principal name with the DB server's Kerberos Service (SPN mapping) and generate the server keytab file

- Step 4. Confirm the mapping of server user to service principal

- Step 5. Setup server sqlnet.ora to point to the keytab file generated in step 2

- Step 6. Create a kerberos configuration file that points to the Kerberos KDC (Windows Domain Controller for MSLSA)

- Step 7. Configure the Oracle database client and server sqlnet.ora or .NET config to point to the above Kerberos configuration file

- Step 8. Point the client sqlnet.ora or .NET config to a credential cache file or to MSLSA

- Step 9. Set the client and server authentication services in the sqlnet.ora or .NET config to Kerberos5

- Step 10. Setup an externally authenticated database user that matches the Kerberos client user setup in step 1 (note the case)

- Step 11. Login to the client machine via the Windows Domain client user (for MSLSA) or perform an okinit to authenticate the client Kerberos user (for file based CC):

##### Step 1. Update Windows services file to include a "kerberos5" entry

Change the Kerberos entry in the Windows service file (`C:\windows\system32\drivers\etc\services`) from:

    kerberos   88/tcp           krb5 kerberos-sec      #Kerberos

to:

    kerberos   88/tcp kerberos5 krb5 kerberos-sec      #Kerberos

##### Step 2. Create client and server Kerberos users (Windows domain users for MSLSA)

As noted in the above "key", we will use `oracleclient` and `oracleserver` as our client and server Kerberos user IDs, respectively.

ODP.NET supports MSLSA using Windows domain users which have the following attributes:

- "Kerberos DES" unchecked

- "Kerberos AES 128 bit" checked

- "Kerberos AES 256 bit" checked

- "Kerberos preauthentication not required" checked

##### Step 3. Associate the DB server's Kerberos principal name with the DB server's Kerberos Service (SPN mapping) and generate the server keytab file

Run the following commands on the Kerberos KDC (Windows Domain Controller for MSLSA) as an administrator:

    > ktpass -princ kerberos_service_name/dbhost.company.com@DOMAIN.COMPANY.COM /crypto all /mapuser oracleserver@DOMAIN.COMPANY.COM /pass <oracleserver password> /out v5srvtab

    > setspn -A kerberos_service_name/dbhost.company.com@DOMAIN.COMPANY.COM oracleserver

##### Step 4. Confirm the mapping of server user to service principal

Also on the Kerberos KDC, run the following command, noting the output:

    > setspn -L oracleserver

    Registered ServicePrincipalNames for CN=oracleserver,CN=Users,DC=domain,DC=company,DC=com:
            kerberos_service_name/dbhost.company.com
    kerberos_service_name/dbhost.company.com@DOMAIN.COMPANY.COM

##### Step 5. Setup server sqlnet.ora to point to the keytab file generated in step 2

Add the following line to the server `sqlnet.ora`:

    sqlnet.kerberos5_keytab = c:\krb\v5srvtab

##### Step 6. Create a kerberos configuration file that points to the Kerberos KDC (Windows Domain Controller for MSLSA)

An example kerberos configuration file (`krb.conf`):

    [libdefaults]
    default_realm = DOMAIN.COMPANY.COM

    [realms]
    DOMAIN.COMPANY.COM = {
      kdc = dc.company.com
     }

    [domain_realm]
    .domain.company.com = DOMAIN.COMPANY.COM
    domain.company.com = DOMAIN.COMPANY.COM
    .DOMAIN.COMPANY.COM = DOMAIN.COMPANY.COM
    DOMAIN.COMPANY.COM = DOMAIN.COMPANY.COM

##### Step 7. Configure the Oracle database client and server sqlnet.ora or .NET config to point to the above Kerberos configuration file

Edit the client or server `sqlnet.ora` to include:

    sqlnet.kerberos5_conf = C:\krb\krb.conf

Or edit the client application config to include (in the [settings section](InstallManagedConfig.md)):

    <setting name="sqlnet.kerberos5_conf" value="C:\krb\krb.conf" />

##### Step 8. Point the client sqlnet.ora or .NET config to a credential cache file or to MSLSA

Example pointing to Credential Cache file:

    sqlnet.kerberos5_cc_name = c:\krb\krb.cc

Example pointing to MSLSA:

    sqlnet.kerberos5_cc_name = MSLSA:

##### Step 9. Set the client and server authentication services in the sqlnet.ora or .NET config to Kerberos5

    sqlnet.authentication_services=(Kerberos5)

##### Step 10. Setup an externally authenticated database user that matches the Kerberos client user setup in step 1 (note the case)

    create user "ORACLECLIENT@DOMAIN.COMPANY.COM" identified externally;
    grant connect, create session to "ORACLECLIENT@DOMAIN.COMPANY.COM";

##### Step 11. Login to the client machine via the Windows Domain client user (for MSLSA) or perform an okinit to authenticate the client Kerberos user (for file based CC):

    okinit oracleclient

##### Step 12. Run the ODP.NET application

**Note:**

- After configuring the client and server, the last 2 steps are the only steps required on an ongoing basis to run the ODP.NET application.

- A Microsoft Visual C Run-Time Library (MSVCRT.DLL) bug can cause ODP.NET, Managed Driver's setting of the Kerberos5 configuration to be ignored by the Microsoft run-time. In such a case, you will encounter the error message:

      OracleInternal.Network.NetworkException (0x80004005): NA Kerberos5: Authentication handshake failure at stage: krb5_sname_to_principal: default realm not found. Please set SQLNET.Kerberos5_conf.

  To workaround this error, manually set `KRB5_CONFIG` in the ODP.NET application's run-time environment to point to the Kerberos5 configuration file pointed to by `SQLNET.Kerberos5_conf`. For example,

      set KRB5_CONFIG=c:\oracle\network\admin\krb5.ini

**See Also:**

Configuring Kerberos Authentication in [Oracle Database Security Guide](../dbseg/configuring-kerberos-authentication.md) for more information about Kerberos and configuration with Oracle database.

### Using Windows Native Authentication (NTS)

With the Windows native authentication adapter, Oracle users can authenticate to the database using just their Windows user login credentials. It provides a way to enable single sign-on and to simplify user and role credential management. Windows native authentication is also known as Windows Native authentication (NTS).

**Note:**

- ODP.NET Core supports Windows Native Authentication on Windows only

- Due to a limitation in the Microsoft .NET APIs, ODP.NET, Managed Driver only supports Windows Native authentication (NTS) via Microsoft NT LAN Manager (NTLM) instead of Kerberos-based credentials. Normally, this limitation would be invisible to the ODP.NET, Managed Driver application, since the Windows domain and the Oracle database server will transparently support both NTLM and Kerberos domain credentials by default.

#### Configuring Windows Native Authentication (NTS) for the ODP.NET Client

Steps in configuring the NTS for the ODP.NET Client:

- Step 1. Ensure OSAUTH_PREFIX_DOMAIN is set correctly

- Step 2. Setup the externally identified database user

- Step 3. Setup the client configuration to utilize NTS as the authentication methodology

##### Step 1. Ensure OSAUTH_PREFIX_DOMAIN is set correctly

Make sure `OSAUTH_PREFIX_DOMAIN` is set appropriately. If you desire the externally identified user ID to include the domain, set it to true, otherwise false. The parameter is a registry setting that can be found at `HKLM/software/oracle/HOME<ORACLE_SID>.` For example, if your `ORACLE_SID` is `r1`, it is located at `HKLM/software/oracle/HOMEr1`.

##### Step 2. Setup the externally identified database user

Assuming a Step 0 setting of true, use the following commands to setup the externally identified database user associated with the desired Windows domain user:

    create user "MYDOMAIN\MYUSER" identified externally;
    grant connect, create session to "MYDOMAIN\MYUSER";

##### Step 3. Setup the client configuration to utilize NTS as the authentication methodology

Edit the client sqlnet.ora or app config to add NTS to the s`qlnet.authentication_services`. For example.

    sqlnet.authentication_services = (NTS)

**Note:**

After configuring the client and server, the last 2 steps are the only steps required on an ongoing basis to run the ODP.NET application.

**See Also:**

Authenticating Database Users with Windows in [Oracle Database Platform Guide for Microsoft Windows](../ntqrf/authenticating-database-users-with-windows.md) for Windows for more information about Windows native authentication.

### Network Data Encryption and Integrity

ODP.NET enables data encryption and integrity over a network for both intranet and cloud deployments. This ensures that data is disguised to all, except authorized users, and guarantees the original message contents are not altered. In earlier releases, these features were known as Oracle Advanced Security Option (ASO) encryption. Starting with Oracle Database 12c, Oracle ASO is not required to use network data encryption and data integrity.

#### Using Data Encryption

Managed and unmanaged ODP.NET support the following encryption standards and algorithms:

- Advanced Encryption Standard (AES)

  - AES 128-bit

  - AES 192-bit

  - AES 256-bit

- Triple-DES (3DES)

  - 112-bit

  - 168-bit

ODP.NET, Managed Driver uses the following settings to configure network encryption:

- `SQLNET.ENCRYPTION_CLIENT`

- `SQLNET.ENCRYPTION_TYPES_CLIENT`

**See Also:**

[settings section](InstallManagedConfig.md) for definition and information on usage.

#### Using Data Integrity

Managed and unmanaged ODP.NET support the following data integrity algorithms:

- SHA-1

- SHA-2

  - SHA-256

  - SHA-384

  - SHA-512

**See Also:**

- For more information on network encryption and integrity or configuring them for ODP.NET, Unmanaged Driver, refer to the [Oracle Database Security Guide](../dbseg/configuring-network-data-encryption-and-integrity.md).

- To configure network encryption or data integrity in ODP.NET, Managed Driver, refer to the `SQLNET.CRYPTO_CHECKSUM_CLIENT` and `SQLNET.CRYPTO_CHECKSUM_TYPES_CLIENT` settings in "[Oracle Data Provider for .NET, Managed Driver Configuration](InstallManagedConfig.md)." On the database server machine, you will likely have to configure the `SQLNET.CRYPTO_CHECKSUM_SERVER` and `SQLNET.CRYPTO_CHECKSUM_TYPES_SERVER` parameters in the `sqlnet.ora` file.

### Schema Discovery

ADO.NET exposes five different types of metadata collections through the `OracleConnection.GetSchema` API. This permits application developers to customize metadata retrieval on an individual-application basis, for any Oracle data source. Thus, developers can build a generic set of code to manage metadata from multiple data sources.

The following types of metadata are exposed:

- `MetaDataCollections`

  A list of metadata collections that is available from the data source, such as tables, columns, indexes, and stored procedures.

- `Restrictions`

  The restrictions that apply to each metadata collection, restricting the scope of the requested schema information.

- `DataSourceInformation`

  Information about the instance of the database that is currently being used, such as product name and version.

- `DataTypes`

  A set of information about each data type that the database supports.

- `ReservedWords`

  Reserved words for the Oracle query language.

  **See Also:**

  [Oracle Schema Collections](schema-collections.md)

#### User Customization of Metadata

ODP.NET provides a comprehensive set of database schema information. Developers can extend or customize the metadata that is returned by the `GetSchema` method on an individual application basis.

To do this, developers must create a customized metadata file and provide the file name to the application as follows:

1.  Create a customized metadata file and put it in the `CONFIG` subdirectory where the .NET framework is installed. This is the directory that contains `machine.config` and the security configuration settings.

    This file must contain the entire set of schema configuration information, not just the changes. Developers provide changes that modify the behavior of the schema retrieval to user-specific requirements. For instance, a developer can filter out internal database tables and just retrieve user-specific tables

2.  Add an entry in the `app.config` file of the application, similar to the following, to provide the name of the metadata file, in name-value pair format.

        <oracle.dataaccess.client>
          <settings>
            <add name="MetaDataXml" value="CustomMetaData.xml" />
          </settings>
        </oracle.dataaccess.client>

When the `GetSchema` method is called, ODP.NET checks the `app.config` file for the name of the customized metadata XML file. First, the `GetSchema` method searches for an entry in the file with a element named after the provider, in this example, `oracle.dataaccess.client`. In this XML element, the value that corresponds to the name `MetaDataXml` is the name of the customized XML file, in this example, `CustomMetaData.xml`.

If the metadata file is not in the correct directory, then the application loads the default metadata XML file, which is part of ODP.NET.

**See Also:**

"[GetSchema](ConnectionGetSchemaOverloads.md)"

### Connection Pooling

ODP.NET connection pooling is enabled and disabled using the `Pooling` connection string attribute. By default, connection pooling is enabled. The following are `ConnectionString` attributes that control the behavior of the connection pooling service:

- `Connection` `Lifetime`

- `Connection` `Timeout`

- `Decr` `Pool` `Size `

- `HA` `Events`

- `Incr` `Pool` `Size`

- `Load` `Balancing`

- `Max` `Pool` `Size`

- `Min` `Pool` `Size `

- `Pooling`

- `Validate` `Connection`

#### Connection Pooling Example

The following example opens a connection using `ConnectionString` attributes related to connection pooling.

    // C#

    using System;
    using Oracle.DataAccess.Client;


    class ConnectionPoolingSample
    {
      static void Main()
      {
        OracleConnection con = new OracleConnection();

        //Open a connection using ConnectionString attributes
        //related to connection pooling.
        con.ConnectionString =
          "User Id=scott;Password=tiger;Data Source=oracle;" +
          "Min Pool Size=10;Connection Lifetime=100000;Connection Timeout=60;" +
          "Incr Pool Size=5; Decr Pool Size=2";
        con.Open();
        Console.WriteLine("Connection pool successfully created");

        // Close and Dispose OracleConnection object
        con.Close();
        con.Dispose();
        Console.WriteLine("Connection is placed back into the pool.");
      }
    }

#### Using Connection Pooling

When connection pooling is enabled (the default), the `Open` and `Close` methods of the `OracleConnection` object implicitly use the connection pooling service, which is responsible for pooling and returning connections to the application.

The connection pooling service creates connection pools by using the `ConnectionString` property as a signature, to uniquely identify a pool.

In managed and Core versions of ODP.NET, connection strings themselves must be an exact match in their entirety. If keywords are supplied in a different order or a space is added to the connection string, a new pool is created. If a pool already exists with the requested signature, a connection is returned to the application from that pool.

In unmanaged ODP.NET, a new pool is created only when connection string attribute values change. Extra spaces or changing keyword order do not create a new pool.

When a connection pool is created, the connection pooling service initially creates the number of connections defined by the `Min` `Pool` `Size` attribute of the `ConnectionString` property. This number of connections is always maintained by the connection pooling service for the connection pool, except when Fast Connection Failover removes invalid connections or Connection Lifetime is exceeded. In these two cases, the connection number could drop below the Min Pool Size. ODP.NET would then attempt to restore the minimum pool size level upon the next connection request.

At any given time, these connections are in use by the application or are available in the pool.

The `Incr` `Pool` `Size` attribute of the `ConnectionString` property defines the number of new connections to be created by the connection pooling service when more connections are needed in the connection pool.

When the application closes a connection, the connection pooling service determines whether or not the connection lifetime has exceeded the value of the `Connection Lifetime` attribute. If so, the connection pooling service destroys the connection; otherwise, the connection goes back to the connection pool. The connection pooling service enforces the `Connection Lifetime` only when `Close()` or `Dispose()` is invoked.

The `Max` `Pool` `Size` attribute of the `ConnectionString` property sets the maximum number of connections for a connection pool. If a new connection is requested, but no connections are available and the limit for `Max` `Pool` `Size` has been reached, then the connection pooling service waits for the time defined by the `Connection` `Timeout` attribute. If the `Connection` `Timeout` time has been reached, and there are still no connections available in the pool, the connection pooling service raises an exception indicating that the connection pool request has timed-out. Upon a connection timeout, ODP.NET distinguishes whether the timeout occurred due to the database server failing to deliver a connection in the allotted time or no connection being available in the pool due to the maximum pool size having been reached. The exception text returned will either be "Connection request timed out" in the case of the former or "Pooled connection request timed out" in the case of the latter.

The `Validate` `Connection` attribute validates connections coming out of the pool. This attribute should be used only when absolutely necessary, because it causes a round-trip to the database to validate each connection immediately before it is provided to the application. If invalid connections are uncommon, developers can create their own event handler to retrieve and validate a new connection, rather than using the `Validate` `Connection` attribute. This generally provides better performance.

The connection pooling service closes connections when they are not used; connections are closed every 3 minutes. The `Decr` `Pool` `Size` attribute of the `ConnectionString` property provides connection pooling service for the maximum number of connections that can be closed every 3 minutes.

Beginning with Oracle Data Provider for .NET release 11.1.0.6.20, enabling connection pooling by setting `"pooling=true"` in the connection string (which is the case by default) will also pool operating system authenticated connections.

### Connection Pool Management

ODP.NET connection pool management provides explicit connection pool control to ODP.NET applications. Applications can explicitly clear connections in a connection pool.

Using connection pool management, applications can do the following:

**Note:**

These APIs are not supported in a .NET stored procedure.

- Clear connections from connection pools using the `ClearPool` method.

- Clear connections in all the connection pools in an application domain, using the `ClearAllPools` method.

**See Also:**

- "[ClearPool](ConnectionClearPoolCtor1.md)"

- "[ClearAllPools](ConnectionClearAllPools.md)"

### Connection Performance Counters

Installing Oracle Data Provider for .NET creates a set of performance counters on the target system. All ODP.NET provider types (Core, managed, and unmanaged) publish these performance counters for each of their client applications. These performance counters can be viewed using Windows Performance Monitor (Perfmon) or the `PerformanceCounter` class in the `System.Diagnostics` namespace.

**Note:**

ODP.NET performance counters are available on Windows platforms only.

As ODP.NET performance counters are not enabled nor registered after installation, administrators must register the counters, then enable the specific counters of interest before being able to monitor them.

#### Registering Performance Counters

After installation, ODP.NET performance counters must be registered so that tools, such as `Perfmon`, can consume them. Registration requires running a PowerShell script for the respective provider.

ODP.NET installs six scripts for counters that must be run from PowerShell to take effect

- `register_odpc_perfmon_counters.ps1` – Registers ODP.NET Core counters

- `register_odpm_perfmon_counters.ps1` – Registers managed ODP.NET counters

- `register_odpu_perfmon_counters.ps1` – Registers unmanaged ODP.NET counters

- `unregister_odpc_perfmon_counters.ps1` – Unregisters ODP.NET Core counters

- `unregister_odpm_perfmon_counters.ps1` – Unregisters managed ODP.NET counters

- `unregister_odpu_perfmon_counters.ps1` – Unregisters unmanaged ODP.NET counters

These scripts are located in the `ORACLE_HOME\odp.net\PerfCounters` directory for Oracle Universal Installer and NuGet deployments, in the `<INSTALLATION_DIRECTORY>\odp.net\PerfCounters` directory for xcopy deployments, and `<VISUAL_STUDIO_SOLUTION_DIRECTORY>\packages\Oracle.ManagedDataAccess.<VERSION>\PerfCounters` directory for MSI deployments.

Windows Administrator privileges are required when running these PowerShell scripts.

To unregister, run the unregister PowerShell script that matches the ODP.NET provider type you wish to unregister.

Previously, the `OraProvCfg.exe` utility was included with ODP.NET for registering and unregistering counters. These PowerShell scripts replace the utility. If you registered ODP.NET counters with this utility, then unregister with the same `OraProvCfg.exe` version.

#### Enabling Performance Counters

ODP.NET enables monitoring many different connection counters, including pooled and non-pooled connections. These counters can be monitored individually or together. Developers can set which counters to monitor prior to application startup using the PerformanceCounters setting in the `<settings>` section of the .NET config file, which is available in managed and unmanaged ODP.NET, or Windows Registry, which is available in unmanaged ODP.NET only. For ODP.NET Core, developers can set the `OracleConfiguration.PerformanceCounters` property.

Table 3-3 lists the connection performance counters with their setting values.

Table 3-3 Performance Counters for Connection Pooling

| Performance Counter               | Valid Values | Description                                                                  |
|:----------------------------------|:-------------|:-----------------------------------------------------------------------------|
| None                              | `0`          | Not enabled (Default)                                                        |
| `HardConnectsPerSecond`           | `1`          | Number of sessions being established with the Oracle Database every second.  |
| `HardDisconnectsPerSecond`        | `2`          | Number of sessions being severed from the Oracle Database every second.      |
| `SoftConnectsPerSecond`           | `4`          | Number of active connections originating from connection pools every second. |
| `SoftDisconnectsPerSecond`        | `8`          | Number of active connections going back to the connection pool every second. |
| `NumberOfActiveConnectionPools`   | `16`         | Total number of active connection pools.                                     |
| `NumberOfInactiveConnectionPools` | `32`         | Number of inactive connection pools.                                         |
| `NumberOfActiveConnections`       | `64`         | Total number of connections in use.                                          |
| `NumberOfFreeConnections`         | `128`        | Total number of connections available for use in all the connection pools.   |
| `NumberOfPooledConnections`       | `256`        | Total number of pooled active and free connections.                          |
| `NumberOfNonPooledConnections`    | `512`        | Number of non-pooled active connections.                                     |
| `NumberOfReclaimedConnections`    | `1024`       | Number of connections which were garbage-collected implicitly.               |
| `NumberOfStasisConnections`       | `2048`       | No operation. This counter is no longer supported.                           |

These settings are bitwise ORed in order to monitor more than one counter. For example, to collect counters for `SoftConnectsPerSecond (4)`, `Soft DisconnectsPerSecond (8)`, and `NumberOfActiveConnectionPools (16)`, set `PerformanceCounters` to `28` (i.e. 4 + 8 + 12).

#### Setting Performance Counters in .NET Configuration Files

Performance counters can be set using an .NET configuration file, such as `web.config` or `app.config`, in managed and unmanaged ODP.NET only. Since .NET configuration entries take precedence over Windows Registry settings, they can be used for a specific application.

As earlier described, populating the `PerformanceCounters` setting in the `<settings>` section enables individual performance counters to be monitored. Windows Perfmon uses very long and not easily human readable application instance names. To make identifying each application easier administrators can assign an identifier name in the `<connectionPools>` section of the .NET configuration file. This section supports the following settings:

- `connectionString`: This setting identifies the connections or pool to monitor using the connection string as the unique identifier. The connection string entered here must match the target connection string to be monitored, but without the password attribute.

- `poolName` (optional): Connection strings can be very long and hard to read with many that look similar. `poolName` allows using an arbitrary string to easily identify which pool is being monitored.

The following examples show how to use these settings.

##### ODP.NET, Managed Driver

    <oracle.manageddataaccess.client>
     <version number="*">
      <connectionPools>
               .
               .
         <connectionPool connectionString="[connection string without password]" poolName="[Pool Name]">   </connectionPool>
               .
               .
      </connectionPools>
     </version>
    </oracle.manageddataaccess.client>

ODP.NET, Unmanaged Driver can use the same pool name setting and format as listed above by replacing the \<`oracle.manageddataaccess.client`\> tags with \<`oracle.unmanageddataaccess.client`\> tags. Alternatively, the legacy \<`oracle.dataaccess.client`\> format is available for unmanaged ODP.NET.

##### ODP.NET, Unmanaged Driver

    <configuration>
     <oracle.dataaccess.client>
      <settings>
               .
               .
          <add name="[connection string without password]" value="connectionPool name='[Pool Name]'"/>
              .
              .
        </settings>
      </oracle.dataaccess.client>
    </configuration>

#### Setting Performance Counters in Windows Registry

Publication of individual unmanaged ODP.NET performance counters is enabled or disabled using the Windows Registry value `PerformanceCounters` of type `REG_SZ`. This registry value is under:

`HKEY_LOCAL_MACHINE\SOFTWARE\ORACLE\ODP.NET\``Assembly_Version`

where `Assembly_Version` is the full assembly version number of `Oracle.DataAccess.dll`.

Similarly to the .NET config file, multiple performance counters can be obtained by adding the valid values. For example, if `PerformanceCounters` is set to 3, then both `HardConnectsPerSecond` and `HardDisconnectsPerSecond` are enabled.

#### Publishing Performance Counters

Commonly, ODP.NET performance counters are monitored using Perfmon. The counters are published under the following Category Names:

- ODP.NET, Core Driver

- ODP.NET, Managed Driver

- ODP.NET, Unmanaged Driver

Administrators can choose the individual ODP.NET counters to monitor after selecting one or more of these categories. PerfMon shows all ODP.NET counters, but only the explicitly enabled counters generate statistics.

After choosing the counters to monitor, administrators then select the running instance(s) to monitor. ODP.NET instances must be actively running for them to appear in PerfMon. Otherwise, no instances will appear available to monitor. After instance selection occurs, they are added to PerfMon as counters to monitor.

Performance counters can monitor at the application domain, pool, or database instance level. Database instance level monitoring only applies if load balancing or Fast Connection Failover features are enabled.

The instance name format is as follows:

`<Application Domain Name> [<Process Id>, <Application Domain Id>][<Connection String/Pool Name>][<Instance Name>]`. The entry is limited to 127 characters. There is a restriction length on every field in the instance name. The following table shows the maximum number of characters allocated for each field:

Table 3-4 Field Names of Performance Counters and Maximum Number of Characters

| Field Name                  | Maximum Number of Characters |
|:----------------------------|:-----------------------------|
| Application Domain          | 40                           |
| Pool Name/Connection String | 70                           |
| Database Instance Name      | 16                           |

When the length of a field value exceeds the length limit, the string is truncated and appended with "`...`" to fit within the length limit and indicate the continuation. For example, for a given application called `Program.exe` with a connection string `user id=hr;Password=<password>;data source=inst1;max pool size=125;min pool size=50`, one may see the following similar to the following for a process that has two application domains:

- `Program.exe [123, 1]`

- `Program.exe [123, 1][ user id=hr;data source=inst1;max pool siz...]`

- `Program.exe [123, 1][ user id=hr;data source=inst1;max pool siz...] [instA] `

- `Domain 2[123, 2]`

- `Domain 2[123, 2][ user id=hr;data source=inst1;max pool siz...]`

- `Domain 2[123, 2][ user id=hr;data source=inst1;max pool siz...] [instB]`

- `Domain 2[123, 2][ user id=hr;data source=inst1;max pool siz...] [instC]`

Since connection pool attributes can be similar in their first 70 characters, applications can set a Pool Name to uniquely identify each one in the monitoring tool. For example, when using Pool Name, the process will show up as follows:

    Domain 2[123, 2][Pool Name][instC]

### Database Resident Connection Pooling

Client side connection pooling can be very efficient for middle tier machines. However, it can consume a great deal of database server resources if there are numerous middle tier servers with idle connections. While the intent is to keep the number of idle connections to a minimum, it becomes difficult as the number of middle tier servers increase, each possibly having idle connections that cannot be shared across applications.

Database Resident Connection Pooling (DRCP) is intended to optimize resource usage by pooling connections at the database server level, which can then be shared across many applications. The benefit is better scalability and lower resource usage at the database server level.

Managed and unmanaged ODP.NET have been enhanced to support DRCP, which allows it to dispense and release DRCP connections to better utilize database server resources.

#### About DRCP

DRCP pools server processes, each of which is the equivalent to a dedicated server process and database session combined. These are called pooled servers. Pooled servers can be shared by multiple applications running on the same or multiple hosts.

When DRCP is configured for Oracle Database Real Application Clusters (Oracle RAC), the pool configuration is applied to each database instance. Starting or stopping the pool on one instance starts or stops the pool on all instances. 

#### DRCP and ODP.NET

DRCP is a server side pool that complements ODP.NET client side pooling. These two pools can be used together.

In a typical dedicated server mode, client side connection pooling saves both on server round trips and socket/session creation. In a connection open/close sequence, a server round trip is involved only upon the first `Open()`. For subsequent open/close sequences on the same connection, no client to server interaction is required because the connection is pooled locally in the client address space.

With DRCP enabled, when the client creates a connection, the connection is assigned a pooled server when needed. When the connection is closed, the database server releases the DRCP server session back to the server side pool, effectively making the DRCP server session available for reuse. This server session can be reused by the same pool or a different pool on the same or different middle tier hosts.

#### Configuring DRCP and ODP.NET

The following section describe how DRCP can be configured on the client side and the server side.

- Configuring DRCP on the Client Side

  ODP.NET developers can enable DRCP on the client side by using `(SERVER=POOLED)` in the connect descriptor.

  Sample Descriptor:

      (DESCRIPTION=(ADDRESS=(PROTOCOL=tcp)(HOST=myhost)(PORT=1521))(CONNECT_DATA=(SERVICE_NAME=sales.example.com)(SERVER=POOLED)))

- Configuring DRCP on the Server Side

  Oracle database includes a default connection pool called `SYS_DEFAULT_CONNECTION_POOL`. By default, this pool is created, but not started. To enable database resident connection pooling, you must explicitly start the connection pool.

  You must be a database administrator (DBA) and must log on as `SYSDBA` to start and end a pool.

      SQL> EXECUTE DBMS_CONNECTION_POOL.START_POOL();

  If an application will share the DRCP connection pool across multiple middle tier servers, then the application has the option of setting the `OracleConnection.DRCPConnectionClass` property to a string value that uniquely identifies the server pool. If a DRCP connection is opened with this property populated, ODP.NET will direct DRCP to use a connection from that specific server pool. This capability allows the database server to scale easily across multiple middle tier servers.

Example 3-1 Using Database Resident Connection Pooling: Sample Code

    // This application uses the following connect descriptor:
    // oracle = (DESCRIPTION=(ADDRESS=(PROTOCOL=tcp)(HOST=<hostname>)(PORT=1521))(CONNECT_DATA=(SERVICE_NAME=<service name>)(SERVER=POOLED)))

    using System;
    using Oracle.ManagedDataAccess.Client;

    class DRCP
    {
        static void Main()
          {
                string constr = “user id=hr;password=hr;data source=oracle";
                OracleConnection con = new OracleConnection(constr);
                con.DRCPConnectionClass = "GroupA";
                con.Open();

                con.Dispose();

          }
    }

**Note:**

To use DRCP with ODP.NET, Unmanaged Driver,:

- the .NET configuration setting, `CPVersion`, must be set to `2.0`, or,

- have `CPVersion` not set at all, but have `(SERVER=POOLED)` in the TNS full descriptor that is used by the application.

Refer to [settings section](InstallManagedConfig.md) for more information.

**See Also:**

[Oracle Database Administrator’s Guide](../admin/managing-processes.md) for more information on configuring the default connection pool or end pool.

#### DRCP for Oracle Multitenant

DRCP cannot be created on the PDB. DRCP can only be created on the CDB and is shared among all the PDBs.

ODP.NET has one DRCP for the entire CDB and it can be configured and managed (start, stop, or reconfigure) only by connecting to root container.

To configure, set a session to point to the CDB and start the DRCP pool. For example:

    alter session set container = cdb$root;
    execute dbms_connection_pool.configure_pool('SYS_DEFAULT_CONNECTION_POOL');
    execute dbms_connection_pool.start_pool();

#### DRCP for Oracle Real Application Clusters (RAC)

In an Oracle Real Application Clusters (RAC) environment, when a user creates a DRCP on an instance, that DRCP is replicated on all the instances of an Oracle RAC database and you can use any instance to manage the connection pool. Any changes you make to the pool configuration are applicable on all Oracle RAC instances.

#### DRCP Restrictions for ODP.NET

ODP.NET does not support the following features with DRCP:

- Open the proxy connection with end user authentication

- Open the `sysoper` connection

- Open using `OpenWithNewPassword`

- Set the `SQLNET.AUTHENTICATION_SERVICES` parameter value to `nts`, which enables Microsoft Windows native operating system authentication

- .NET Framework versions earlier than .NET Framework 4

### Oracle Multitenant and Pluggable Databases

Oracle Database 12c introduced Oracle Multitenant, which enables an Oracle database to contain a portable collection of schemas, schema objects, and nonschema objects that appears to ODP.NET as a separate database. This self-contained collection is called a pluggable database (PDB).

Oracle Multitenant is a database architecture that enables customers to easily consolidate multiple pluggable databases without changing their application. This architecture delivers all the benefits of managing many databases as one, yet retains the isolation and resource prioritization of separate databases. In addition, Oracle Multitenant enables rapid provisioning and upgrades, and fully complements other Oracle database options.

Managed and unmanaged ODP.NET fully support Oracle Multitenant. In addition to being able to connect to individual pluggable databases, ODP.NET has been enhanced so that applications can request and obtain connections to specific PDBs from the same connection pool. The application can connect to any of the PDBs that are part of the same container database (CDB) and they must have the same common user. Moreover, if connections span multiple instances, such as with Oracle Real Application Clusters, then every instance must uniformly have the same exact PDBs and services for the common user to connect to. If these conditions are met, then ODP.NET will be able to connect to or implicitly switch connections from one PDB to another within the same pool in a highly performant manner.

To obtain a connection to a specific PDB (as a common user) set the `OracleConnections` properties, `PDBName` and `ServiceName`, and then call `OracleConnection.Open()` to obtain the a connection to the specified PDB and Service name. `PDBName` and `ServiceName` identify the PDB and service that the connection needs to be established to or switched to if using an existing idle connection from the connection pool. They are the pluggable database name and database service name, respectively. If only the `PDBName` property is set and the service name is not set by the user, then the provider will return a connection that uses the default (administrative) service.

**Note:**

For ODP.NET, Unmanaged Driver to be able to switch PDB connections within the same pool:

- the .NET configuration setting, `CPVersion`, must be set to `2.0`, or,

- have `CPVersion` not set at all, but set `PDBName` and/or `ServiceName` to a non-null/non-empty value for the first connection request for a given connection string.

Refer to [settings section](InstallManagedConfig.md) for more information.

Example 3-2 Using Pluggable Database: Sample Code

    // C#
    using System;
    using Oracle.ManagedDataAccess.Client;

    class PDB
    {
        static void Main()
        {
                string constr = “user id=hr;password=hr;data source=oracle”;
                OracleConnection con = new OracleConnection(constr);
                con.PDBName = "pdb1";
                con.ServiceName = "db1.company.com";
                con.Open();
                con.Close();
        }
    }

ODP.NET keeps track of the `PDBName` and `ServiceName` to which the pooled connections are established to. Upon the application requesting for a connection with a specified `PDBName` and `ServiceName`, ODP.NET will return a connections that matches that request. However, if a matching connection is not found, ODP.NET will create a new connection and/or alter the session to switch to the requested `PDBName` and `ServiceName`. If the `PDBName` and/or `ServiceName` has been altered, then the `SwitchedConnection` property will return true if called with the `Open()` method invocation.

ODP.NET does not support usage of the `ALTER SESSION` statement to modify the Edition in Edition-Based Redefinition during the lifetime of a process. If using PDBs with Oracle Continuous Query Notification, you must connect to Oracle Database 12c Release 2 or higher. Hosting connections to multiple PDBs from the same pool requires ODP.NET for .NET Framework 4 or higher.

**Note:**

When the connection is implicitly being switched from one PDB/Service to another, Service Relocation Connection Timeout(SRCT) will not take effect.

**See Also:**

Managing Pluggable Databases in [Oracle Database Administrator's Guide](../multi/managing-a-multitenant-environment.md)

### Edition-Based Redefinition

Edition-based redefinition enables you to upgrade the database component of an application even while the application is being used. This minimizes or eliminates downtime for the application.

ODP.NET does not support usage of the `ALTER SESSION` statement to modify the Edition during the lifetime of a process.

Managed and unmanaged ODP.NET can connect to a database edition, and also have the ability to host connections to multiple Editions from within the same pool. An ODP.NET application can obtain a connection that is associated with a specified database edition by setting the `OracleConnection.DatabaseEditionName` property to the name of the database edition that the connection should be associated with. To use a single pool, the same user must be able to connect to both Editions. Applications will perform better and more efficiently when using Editions because ODP.NET can use the same connection pool and even share the same `OracleConnection` object by only changing Edition-specific properties.

Example 3-3 Using Edition-Based Redefinition: Sample Code

    using System;
    using Oracle.ManagedDataAccess.Client;

    class Editions
    {
        static void Main()
        {
               // Create a  connection
               string constr = “user id=hr;password=hr;data source=oracle”;
               OracleConnection con = new OracleConnection(constr);

               // Obtain a connection associated with EditionX
               con.DatabaseEditionName = "EditionX";
               con.Open();

               // Obtain a connection associated with EditionY
               con.Close();
               con.DatabaseEditionName = "EditionY";
               con.Open();
               con.Dispose();
        }
    }

Changing the edition name through `DatabaseEditionName` while the connection is open is not allowed. It must be changed while the connection is in a closed state.

ODP.NET supports Editions when connecting to Oracle Database 11g Release 2 or later. Hosting multiple Editions in the same pool is available only in ODP.NET for .NET Framework 4 and above.

**Note:**

To use this Edition-Based Redefinition feature with unmanaged ODP.NET connection pools:

- the .NET configuration setting, `CPVersion`, must be set to `2.0`, or,

- have `CPVersion` not set at all, but set the `DatabaseEditionName` property to a non-null/non-empty value for the first connection request for a given connection string.

Refer to [settings section](InstallManagedConfig.md) for more information.

Applications can specify an Edition at deployment time using the registry or configuration file. An application can create the following registry entry of type `REG_SZ`:

    HKLM\Software\Oracle\ODP.NET\version\Edition

Here `version` is the version of ODP.NET, and `Edition` is a valid Edition string value.

An application can alternatively use the `web.config` or `application.config` configuration file to specify the Edition at deployment time. The `machine.config` configuration file can be used to specify the Edition for all applications that use a particular version of the .NET framework.

The following example sets the Edition to `E1` in a .NET configuration file for ODP.NET, Unmanaged Driver:

    <?xml version="1.0" encoding="utf-8" ?>
    <configuration>
     <oracle.dataaccess.client>
      <settings>
       <add name="Edition" value="E1"/>
      </settings>
     </oracle.dataaccess.client>
    </configuration>

To summarize, the Edition name can be set by the `DatabaseEditionName` property, in the .NET configuration file, or in the Windows Registry. If `DatabaseEditionName` is set, then it takes precedence over the other two settings. If the .NET configuration file has an Edition set, then it takes precedence over the registry.

**See Also:**

For more information on Editions refer to the [Oracle Database Administrator’s Guide](../admin/managing-schema-objects.md) and [Oracle Database Development Guide](../adfns/editions.md)

### Operating System Authentication

Oracle Database can use Windows user login credentials to authenticate database users. To open a connection using Windows user login credentials, the `User` `Id` connection string attribute must be set to a slash (`/)`. If the `Password` attribute is provided, it is ignored.

**Note:**

Operating system authentication is not supported in a .NET stored procedure.

ODP.NET Core supports operating system authentication for Windows only.

All ODP.NET, Unmanaged Driver connections, including those using operating system authentication, can be pooled. ODP.NET, Managed Driver supports operating system authentication, except when the Windows domain is constrained to only support Kerberos-based domain authentication. Connections are pooled by default, and no configuration is required, as long as pooling is enabled.

The following example shows the use of operating system authentication:

    /* Create an OS-authenticated user in the database
       Assume init.ora has OS_AUTHENT_PREFIX set to "" and <OS_USER>
       is any valid OS or DOMAIN user.

         create user <OS_USER> identified externally;
         grant connect, resource to <OS_USER>;

       Login through OS Authentication and execute the sample.  See Oracle
       documentation for details on how to configure an OS-Authenticated user
    */

    // C#

    using System;
    using Oracle.DataAccess.Client;

    class OSAuthenticationSample
    {
      static void Main()
      {
        OracleConnection con = new OracleConnection();

        //Establish connection using OS Authentication
        con.ConnectionString = "User Id=/;Data Source=oracle;";
        con.Open();
        Console.WriteLine("Connected to Oracle" + con.ServerVersion);

        // Close and Dispose OracleConnection object
        con.Close();
        con.Dispose();
        Console.WriteLine("Disconnected");
      }
    }

**See Also:**

[Oracle Database Administrator’s Reference for Microsoft Windows](../ntqrf/overview-of-windows-native-authentication.md) for information on how to set up Oracle Database to authenticate database users using Windows user login credentials

### Privileged Connections

Oracle allows database administrators to connect to Oracle Database with either `SYSDBA` or `SYSOPER` privileges. This is done through the `DBA` `Privilege` attribute of the `ConnectionString` property.

The following example connects `scott`/`tiger` as `SYSDBA`:

    // C#

    using System;
    using Oracle.DataAccess.Client;

    class PrivilegedConnectionSample
    {
      static void Main()
      {
        OracleConnection con = new OracleConnection();

        //Connect scott/tiger as SYSDBA
        con.ConnectionString = "User Id=scott;Password=tiger;" +
          "DBA Privilege=SYSDBA;Data Source=oracle;";
        con.Open();
        Console.WriteLine("Connected to Oracle" + con.ServerVersion);

        // Close and Dispose OracleConnection object
        con.Close();
        con.Dispose();
        Console.WriteLine("Disconnected");
      }
    }

**See Also:**

DBA Privilege "[Table 6-47](ConnectionConnectionString.md)" for further information on privileged connections in the database

### Connection Pooling with OracleCredential

To better secure passwords, all ODP.NET applications can use `OracleCredential` to store user names and passwords outside of the connection string. `OracleCredential` mitigates the possibility of exposing user credentials in a page file swap or in a crash dump.

`OracleCredential` can be used with or without connection pooling.

When using the `OracleCredential` object, one should be aware of the connection pool algorithm that has been modified to take this new feature into consideration, when opening connection to the Oracle database. With earlier implementations of ODP.NET connection pool algorithm, the uniqueness of connection string attribute values were used to decide if a new connection pool needs to be created or an existing connection pool can be used to dispense connections. But with the introduction of `OracleCredential`, the reference of this object is also used to decide which connection pool that `OracleConnection` object is associated with.

The decision to create a new connection pool now depends on two factors, first is the uniqueness of connection string (as in earlier releases) and the second is the reference comparison of the `OracleCredential` provided to the `OracleConnection` object while opening a new connection. If either of these is different, a separate pool is used.

Here is an example to clarify the new algorithm:

    using System;
    using Oracle.DataAccess.Client;
    //using Oracle.ManagedDataAccess.Client;

    class Test
    {
      static void Main()
      {
        string connStr1 = “user id=hr; password=hr; data source=oracle”;
        string connStr2 = “data source=oracle”;

        SecureString secPwd = new SecureString();
        secPwd.AppendChar(‘h’);
        secPwd.AppendChar(‘r’);

        OracleCredential oc1 = new OracleCredential (“hr”, secPwd);
        OracleCredential oc2 = new OracleCredential (“hr”, secPwd);
        OracleCredential oc3 = new OracleCredential (“hr”, secPwd);

        // con1 and con2 are associated with the same connection pool since both are using the same
        // connection string and OracleCredential remains null in both cases.
        OracleConnection con1 = new OracleConnection (connStr1)
        OracleConnection con2 = new OracleConnection (connStr1, null)

        // con3 and con4 use the same connection string but different OracleCredential objects
        // (although same contents) so they are associated with different connection pools.
        OracleConnection con3 = new OracleConnection (connStr2, oc1)
        OracleConnection con4 = new OracleConnection (connStr2, oc2)

        // con5 and con6 use the same connection string and same OracleCredential object
        // so they are associated with the same connection pool.
        OracleConnection con5 = new OracleConnection (connStr2, oc3)
        OracleConnection con6 = new OracleConnection (connStr2, oc3)

        // Please note that con1, con3, con4, and con5 are all associated
        // with a different connection pool.
      }
    }

**Note:**

`OracleCredential` does not support double quotes around a `SecureString` password. Double quotes can be used within a password, however.

**See Also:**

[OracleCredential Class](OracleCredentialClass.md)

### Password Expiration

Oracle allows users passwords to expire. ODP.NET lets applications handle the password expiration by providing a new method, `OpenWithNewPassword`, that opens the connection with a new password.

The following example uses the `OracleConnection` `OpenWithNewPassword` method to connect with a new password of `panther`:

    /* Database Setup
    connect / as sysdba;
    drop user testexpire cascade;
    -- create user "testexpire" with password "testexpire"
    grant connect , resource to testexpire identified by testexpire;
    alter user testexpire password expire;
    */


    // C#

    using System;
    using Oracle.DataAccess.Client;

    class PasswordExpirationSample
    {
      static void Main()
      {
        OracleConnection con = new OracleConnection();

        try
        {
          con.ConnectionString =
            "User Id=testexpire;Password=testexpire;Data Source=oracle";
          con.Open();
          Console.WriteLine("Connected to Oracle" + con.ServerVersion);
        }
        catch (OracleException ex)
        {
          Console.WriteLine(ex.Message);

          //check the error number
          //ORA-28001 : the password has expired
          if (ex.Number == 28001)
          {
            Console.WriteLine("\nChanging password to panther");
            con.OpenWithNewPassword("panther");
            Console.WriteLine("Connected with new password.");
          }
        }
        finally
        {
          // Close and Dispose OracleConnection object
          con.Close();
          con.Dispose();
          Console.WriteLine("Disconnected");
        }
      }
    }

**Note:**

- The `OpenWithNewPassword` method should be used only when the user password has expired, not for changing the password.

- If connection pooling is enabled, then invoking the `OpenWithNewPassword` method also clears the connection pool. This closes all idle connections created with the old password.

**See Also:**

"[OpenWithNewPassword(String)](ConnectionOpenWithNewPassword1.md)"

### Proxy Authentication

With proper setup in the database, proxy authentication enables middle-tier applications to control the security by preserving database user identities and privileges, and auditing actions taken on behalf of these users. This is accomplished by creating and using a proxy database user that connects and authenticates against the database on behalf of a database user (that is, the real user) or database users.

Proxy authentication can then be used to provide better scalability with connection pooling. When connection pooling is used in conjunction with proxy authentication, the proxy authenticated connections can be shared among different real users. This is because only the connection and session established for the proxy is cached. An additional session is created for the real user when a proxy authenticated connection is requested, but it will be destroyed appropriately when the proxy authenticated connection is placed back into the pool. This design enables the application to scale well without sacrificing security.

ODP.NET applications can use proxy authentication by setting the `"Proxy` `User` `Id"` and `"Proxy` `Password"` attributes in the connection string. The real user is specified by the `"User` `Id"` attribute. Optionally, to enforce greater security, the real user's password can be provided through the `"Password"` connection string attribute. When using distributed transactions in conjunction with proxy authentication, the real user's password is no longer optional, and it must be supplied.

The following example illustrates the use of ODP.NET proxy authentication:

    /*  Log on as DBA (SYS or SYSTEM) that has CREATE USER privilege.
        Create a proxy user and modified scott to allow proxy connection.

         create user appserver identified by eagle;
         grant connect, resource to appserver;
         alter user scott grant connect through appserver;
    */

    // C#

    using System;
    using Oracle.DataAccess.Client;

    class ProxyAuthenticationSample
    {
      static void Main()
      {
        OracleConnection con = new OracleConnection();

        // Connecting using proxy authentication
        con.ConnectionString = "User Id=scott;Password=tiger;" +
          "Data Source=oracle;Proxy User Id=appserver;Proxy Password=eagle; ";
        con.Open();
        Console.WriteLine("Connected to Oracle" + con.ServerVersion);

        // Close and Dispose OracleConnection object
        con.Close();
        con.Dispose();
        Console.WriteLine("Disconnected");
      }
    }

**See Also:**

- [Oracle Database SQL Language Reference](../sqlrf/ALTER-USER.md) for the description and syntax of the proxy clause for the `ALTER` `USER` statement

- [Oracle Database Security Guide](../dbseg/configuring-audit-policies.md) for information about how auditing works for SQL statements and privileges in a multitier environment

### Dynamic Distributed Transaction Enlistment

For those applications that dynamically enlist in distributed transactions through the `EnlistDistributedTransaction` of the `OracleConnection` object, the `"Enlist"` connection string attribute must be set to a value of `"true"`. If `"Enlist=true"`, the connection enlists in a transaction when the `Open` method is called on the `OracleConnection` object, if it is within the context of a COM+ transaction or a `System.Transactions`. If not, the `OracleConnection` object does not enlist in a distributed transaction, but it can later enlist explicitly using the `EnlistDistributedTransaction` or the `EnlistTransaction` method. If "`Enlist`" is equal to "`false`" or "`dynamic`", the connection cannot enlist in the transaction. ODP.NET, Unmanaged Driver in ODAC 12c Release 3 first introduced this new behavior for "`Enlist=dynamic`".

**See Also:**

- "Connection String Attributes"

- "[EnlistDistributedTransaction](ConnectionEnlistDistributedTransaction.md)"

### Client Identifier and End-to-End Tracing

The client identifier is a predefined attribute from the Oracle application context namespace `USERENV`. It is similar to proxy authentication because it can enable tracking of user identities. However, client identifier does not require the creation of two sessions (one for the proxy user and another for the end user) as proxy authentication does. In addition, the client identifier does not have to be a database user. It can be set to any string. But most importantly, by using client identifier, ODP.NET developers can use application context and Oracle Label Security, and configure Oracle Virtual Private Database (VPD) more easily. To set the client identifier, ODP.NET applications can set the `ClientId` property on the `OracleConnection` object after opening a connection. If connection pooling is enabled in unmanaged ODP.NET, then the `ClientId` is reset to null whenever a connection is placed back into the pool. In managed ODP.NET, the `ClientId` is reset to null (assuming no new value is provided) upon the first database round trip after a connection is placed back into the pool.

The client identifier can also be used for end-to-end application tracing. End-to-end tracing simplifies the process of diagnosing performance problems in multitier environments. In multitier environments, a request from an end client is routed to different database sessions by the middle tier making it difficult to track a client across different database sessions. End-to-end tracing uses the client identifier to uniquely trace a specific end-client through all tiers to the database server.

ODP.NET exposes the `ActionName, ClientId, ``ClientInfo, `and `ModuleName` write-only properties on the `OracleConnection` object. These properties correspond to the following end-to-end tracing attributes:

- `Action` - Specifies an action, such as an `INSERT` or `UPDATE` operation, in a module

- `ClientId` - Specifies an end user based on the logon ID, such as `HR.HR`

- `Client info` - Specifies user session information

- `Module` - Specifies a functional block, such as Accounts Receivable or General Ledger, of an application

**See Also:**

- "[OracleConnection Properties](ConnectionProperties.md)"

- [Oracle Database SQL Tuning Guide](../tgsql/performing-application-tracing.md) for an overview of End-to-End Application Tracing

- [Oracle Database Security Guide](../dbseg/using-application-contexts-to-retrieve-user-information.md)

### Transparent Application Failover (TAF) Callback Support

[Transparent Application Failover (TAF)](glossary.md) is a feature in Oracle Database that provides high availability.

**Note:**

ODP.NET, Managed Driver and ODP.NET Core do not support TAF nor TAF callbacks.

TAF enables an application connection to automatically reconnect to another database instance if the connection gets severed. Active transactions roll back, but the new database connection, made by way of a different node, is identical to the original. This is true regardless of how the connection fails.

With TAF, a client notices no loss of connection as long as there is one instance left serving the application. The database administrator controls which applications run on which instances, and also creates a failover order for each application.

When a session fails over to another database, the NLS settings that were initially set on the original session are not carried over to the new session. Therefore, it is the responsibility of the application to set these NLS settings on the new session.

#### TAF Notification

Given the delays that failovers can cause, applications may wish to be notified by a TAF callback. ODP.NET supports the TAF callback function through the `Failover` event of the `OracleConnection` object, which allows applications to be notified whenever a failover occurs. To receive TAF callbacks, an event handler function must be registered with the `Failover` event.

#### When Failover Occurs

When a failover occurs, the `Failover` event is raised and the registered event handler is invoked several times during the course of reestablishing the connection to another Oracle instance.

The first call to the event handler occurs when Oracle Database first detects an instance connection loss. This allows the application to act accordingly for the upcoming delay for the failover.

If the failover is successful, the `Failover` event is raised again when the connection is reestablished and usable. At this time, the application can resynchronize the `OracleGlobalization` session setting and inform the application user that a failover has occurred. No significant database operation should occur immediately after a `FailoverEvent.Begin` event. SQL and major database operations should wait until the `FailoverEvent.End` event. `FailoverEvent.Begin` is primarily used to reject failover or to trace it.` FailoverEvent.Begin` can also be used for non-database application operations, such as informing the end user a failover is in progress and to wait until it completes before proceeding. Transactions can be used in the `FailoverEvent.End` callback phase, such as to file fault tickets or audit. These transactions must be committed before the callback completes.

If failover is unsuccessful, the `Failover` event is raised to inform the application that a failover did not take place.

The application can determine whether or not the failover is successful by checking the `OracleFailoverEventArgs` object that is passed to the event handler.

#### Registering an Event Handler for Failover

The following example registers an event handler method called `OnFailover`:

    // C#

    using System;
    using Oracle.DataAccess.Client;

    class TAFCallBackSample
    {
      public static FailoverReturnCode OnFailover(object sender,
                                                  OracleFailoverEventArgs eventArgs)
      {
        switch (eventArgs.FailoverEvent)
        {
          case FailoverEvent.Begin :
            Console.WriteLine(
              " \nFailover Begin - Failing Over ... Please standby \n");
            Console.WriteLine(
              " Failover type was found to be " + eventArgs.FailoverType);
            break;

          case FailoverEvent.Abort :
            Console.WriteLine(" Failover aborted. Failover will not take place.\n");
            break;

          case FailoverEvent.End :
            Console.WriteLine(" Failover ended ...resuming services\n");
            break;

          case FailoverEvent.Reauth :
            Console.WriteLine(" Failed over user. Resuming services\n");
            break;

          case FailoverEvent.Error :
            Console.WriteLine(" Failover error gotten. Sleeping...\n");
            return FailoverReturnCode.Retry;

          default :
            Console.WriteLine("Bad Failover Event: %d.\n", eventArgs.FailoverEvent);
            break;
        }
        return FailoverReturnCode.Success;
      } /* OnFailover */

      static void Main()
      {
        OracleConnection con = new OracleConnection();

        con.ConnectionString = "User Id=scott;Password=tiger;Data Source=oracle;";
        con.Open();
        con.Failover += new OracleFailoverEventHandler(OnFailover);
        Console.WriteLine("Event Handler is successfully registered");

        // Close and Dispose OracleConnection object
        con.Close();
        con.Dispose();
      }
    }

The `Failover` event invokes only one event handler. If multiple `Failover` event handlers are registered with the `Failover` event, only the event handler registered last is invoked.

**Note:**

Distributed transactions are not supported in an environment where failover is enabled.

**See Also:**

- [Oracle Database Net Services Administrator's Guide](../netag/enabling-advanced-features.md)

- "[OracleFailoverEventHandler Delegate](OracleFailoverEventHandlerDelegate.md)"

- "[OracleFailoverEventArgs Class](OracleFailoverEventArgsClass.md)"
