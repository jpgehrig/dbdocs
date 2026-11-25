## About Oracle Instant Client

Learn how Oracle Instant Client enables applications to connect to a local or remote Oracle Database for development and production deployment.

The Oracle Instant Client libraries provide the necessary network connectivity, as well as Oracle Database client-side files to create and run Oracle Call Interface (OCI), Oracle C++ Call Interface (OCCI), ODBC, and JDBC OCI applications to make full use of Oracle Database.

Oracle Instant Client is commonly used by the Oracle APIs of popular languages and environments including Python, Node.js, Go, Ruby, and PHP. Tools included in Oracle Instant Client, such as SQL\*Plus, SQL\*Loader, and Oracle Data Pump provide quick and convenient data access. Oracle Instant Client simplifies the deployment of applications by eliminating the need for an Oracle home on the client machines.

Oracle's standard client-server network interoperability allows connections between different versions of Oracle Instant Client and Oracle Database. For certified configurations, refer to [My Oracle Support note 207303.1](https://support.oracle.com/rs?type=doc&id=207303.1). Tools such as Data Pump may have other restrictions.

Oracle Instant Client supports the Federal Information Processing Standard (FIPS) for 140-2. For more information about configuring FIPS on Oracle Instant Client, see [Oracle Database Security Guide](../dbseg/oracle-database-fips-140-settings.md).

### Benefits of Oracle Instant Client

- Easy installation by extracting and installing zip files or RPM packages.
- Storage space requirement of applications running in Instant Client-mode is significantly reduced compared to the same application running in a full client-side installation.
- No loss of functionality or performance for applications deployed using Oracle Instant Client.
- Easy for independent software vendors to package applications.

### Oracle Instant Client Packages

Various Oracle Instant Client packages are available that help you run applications.

Table 6-1 Oracle Instant Client Packages

| Package Name        | Description                                                                                                                            |
|:--------------------|:---------------------------------------------------------------------------------------------------------------------------------------|
| Basic               | All files required to run Oracle Call Interface (OCI), OCCI, and JDBC-OCI applications for Oracle Database                             |
| Basic Light         | Smaller version of the Basic package, with only English error messages and Unicode, ASCII, and Western European character set support. |
| SDK                 | Additional header files and an example `makefile` for developing OCI and OCCI applications.                                            |
| SQL\*Plus           | Additional package providing the SQL\*Plus command-line tool for executing SQL and PL/SQL statements and scripts.                      |
| Tools               | Additional tools including Data Pump, SQL\*Loader and Workload Replay Client.                                                          |
| ODBC                | Additional libraries providing ODBC.                                                                                                   |
| Precompilers        | Additional tools and libraries providing the Pro\*C and Pro\*COBOL precompilers.                                                       |
| JDBC-OCI Supplement | Additional libraries to support Internationalization.                                                                                  |

### Oracle Instant Client Utilities

Oracle Instant Client and Oracle Instant Client Basic Light contain the following utilities:

- genezi: You can retrieve information about your Oracle Instant Client installation using the `genezi` utility. This utility displays information such as the time zone files that are part of the Oracle Instant Client data shared library. The timezone information shows either the embedded timezone files, or those specified by the ORA_TZFILE environment variable, if it is set.

  Run the `genezi -v command` to determine the client library information.

- adrci: Automatic Diagnostic Repository Command Interpreter (`adrci`) is a command-line tool that you can use to manage Oracle Database diagnostic data. `adrci` enables you to investigate problems, view health check reports, and package first-failure diagnostic data, all within a command-line environment.

- uidrvci: Do not use the `uidrvci.exe` file as it is used to access diagnostic data.

**Parent topic:** [Installing Oracle Instant Client](installing-instant-client.md)
