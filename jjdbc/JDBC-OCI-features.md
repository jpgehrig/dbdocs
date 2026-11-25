This chapter introduces the features specific to the Java Database Connectivity (JDBC) Oracle Call Interface (OCI) driver. It also describes the OCI Instant Client. This chapter contains the following sections:

- OCI Connection Pooling

- Transparent Application Failover

- OCI Native XA

- OCI Instant Client

- About Instant Client Light (English)

### 6.1 OCI Connection Pooling

The OCI connection pooling feature is an Oracle-designed extension. The connection pooling provided by the JDBC OCI driver enables applications to have multiple logical connections, all of which are using a small set of physical connections. Each call on a logical connection is routed on to the physical connection that is available at the given time.

**See Also:**

[OCI Connection Pooling](OCI-connection-pooling.md)

### 6.2 Transparent Application Failover

The Transparent Application Failover feature of JDBC OCI driver enables you to automatically reconnect to a database if the database instance to which the connection is made goes down. The new database connection, though created by a different node, is identical to the original.

**See Also:**

[Transparent Application Failover](transparent-application-failover.md)

### 6.3 OCI Native XA

The JDBC OCI driver also provides a feature called Native XA. This feature enables to use native APIs to send XA commands. The native APIs provide high performance gains as compared to non-native APIs.

**Related Topics**

- [OCI Native XA](distributed-transactions.md)

### 6.4 OCI Instant Client

This section covers the following topics:

- Overview of Instant Client

- OCI Instant Client Shared Libraries

- Benefits of Instant Client

- JDBC OCI Instant Client Installation Process

- Usage of Instant Client

- About Patching Instant Client Shared Libraries

- Regeneration of Data Shared Library and ZIP files

- Database Connection Names for OCI Instant Client

- Environment Variables for OCI Instant Client

#### 6.4.1 Overview of Instant Client

The Instant Client is packaged in a way that makes it extremely easy to deploy OCI, Oracle C++ Call Interface (OCCI), Open Database Connectivity (ODBC), and JDBC-OCI based customer applications, by eliminating the need for an Oracle home. The storage space requirement of a JDBC OCI application using the Instant Client is significantly reduced compared to the same application running on a full client-side installation. The Instant Client shared libraries occupy only about one-fourth the disk space used by a full client installation.

#### 6.4.2 OCI Instant Client Shared Libraries

You must have the Oracle client-side files required to deploy a JDBC OCI application. The library names mentioned in this table correspond to Oracle Database Release 19c. The number part of library names will change in future releases to agree with the release.

Table 6-1 OCI Instant Client Shared Libraries

| Linux and UNIX Systems                                          | Description for Linux and UNIX Systems                                    | Microsoft Windows  | Description for Microsoft Windows                                         |
|:----------------------------------------------------------------|:--------------------------------------------------------------------------|:-------------------|:--------------------------------------------------------------------------|
| `libclntsh.so.19.1`<br>`libclntshcore.so.19.1`<sup>Foot 1</sup> | Client Code Library                                                       | `oci.dll`          | Forwarding functions that applications link with                          |
| `libociei.so`<sup>Foot 2</sup>                                  | OCI Instant Client Data Shared Library                                    | `oraociei19.dll`   | Data and code                                                             |
| `libnnz19.so`                                                   | Security Library                                                          | `orannzsbb19.dll`  | Security Library                                                          |
| `libocijdbc19.so`                                               | OCI Instant Client JDBC Library                                           | `ocijdbc19.dll`    | OCI Instant Client JDBC Library                                           |
| ALL JDBC Java Archive (JAR) files                               | See Also: "[Checking the Environment Variables](JDBC-getting-started.md)" | All JDBC JAR files | See Also: "[Checking the Environment Variables](JDBC-getting-started.md)" |

<sup>Footnote 1</sup>

Beginning with Oracle Database 12c Release 1, the `libclntshcore.so.<release number>` library is separated from the `libclntsh.so.<release number>` library and the data shared library.

<sup>Footnote 2</sup>

The `libclntsh.so.19.1` library, the `libclntshcore.so.19.1` library, and the `libociei.so` library must reside in the same directory in order to operate in instant client mode.

**Note:**

To provide Native XA functionality, you must copy the JDBC XA class library. On UNIX systems, this library, `libheteroxa19.so`, is located in the `ORACLE_HOME``/jdbc/lib` directory. On Microsoft Windows, this library, `heteroxa19.dll`, is located in the `ORACLE_HOME``\bin` directory.

#### 6.4.3 Benefits of Instant Client

The benefits of Instant Client are the following:

- Installation involves copying a smaller number of files.

- The number of required files and the total disk storage on the Oracle client-side are significantly reduced.

- There is no loss of functionality or performance for applications deployed with the Instant Client.

- It is simple for independent software vendors to package applications.

#### 6.4.4 JDBC OCI Instant Client Installation Process

The Instant Client libraries can be installed by choosing the Instant Client option from Oracle Universal Installer. The Instant Client libraries can also be downloaded from the Oracle Technology Network Web site. The installation process is as follows:

1.  Download and install the Instant Client shared libraries and Oracle JDBC class libraries to a directory, such as `instantclient`.

2.  Set the library path environment variable to the directory from Step 1. For example, on UNIX systems, set the `LD_LIBRARY_PATH` environment variable to `instantclient`. On Microsoft Windows, set the `PATH` environment variable to locate the `instantclient` directory.

3.  Add the full path names of the JDBC class libraries to the `CLASSPATH` environment variable.

After completing these steps you are ready to run the JDBC OCI application.

When you use the Instant Client, the OCI and JDBC shared libraries are accessible through the library path environment variable for the JDBC OCI applications. In this case, there is no dependency on the `ORACLE_HOME` and none of the other code and data files provided in `ORACLE_HOME` is needed by JDBC OCI, except for the `tnsnames.ora` file.

Instant Client can be also installed from Oracle Universal Installer by selecting the Instant Client option. The Instant Client files should always be installed in an empty directory. As with the OTN installation, you must set the `LD_LIBRARY_PATH` environment variable to the Instant Client directory to use the Instant Client.

If you have done a complete client installation by choosing the `Admin` option, then the Instant Client shared libraries are also installed. The location of the Instant Client shared libraries and JDBC class libraries in a full client installation is:

On Linux or UNIX systems:

- `libociei.so` library is in `$ORACLE_HOME/instantclient`

- `libclnstsh.so.18.1`, `libocijdbc18.so`, and `libnnz18.so` are in `$ORACLE_HOME/lib`

- The JDBC class libraries are in `$ORACLE_HOME/jdbc/lib`

On Microsoft Windows:

- `oraociei18.dll` library is in `ORACLE_HOME\instantclient`

- `oci.dll`, `ocijdbc18.dll`, and `orannzsbb18.dll` are in `ORACLE_HOME\bin`

- The JDBC class libraries are in `ORACLE_HOME\jdbc\lib`

By copying these files to a different directory, setting the library path to locate this directory, and adding the path names of the JDBC class libraries to the `CLASSPATH` environment variable, you can enable running the JDBC OCI application to use the Instant Client.

**Note:**

- To provide Native XA functionality, you must copy the JDBC XA class library. On UNIX, this library, `libheteroxa18.so`, is located in `ORACLE_HOME``/jdbc/lib`. On Windows, this library, `heteroxa18.dll`, is located in `ORACLE_HOME``\bin`.

- All the libraries must be copied from the same `ORACLE_HOME` and must be placed in the same directory.

- On hybrid platforms, such as Sparc64, if the JDBC OCI driver needs to use the Instant Client libraries, then you must copy the `libociei.so` library from the `ORACLE_HOME``/instantclient32` directory. You must copy all other Sparc64 libraries needed for the JDBC OCI Instant Client from the `ORACLE_HOME``/lib32` directory.

- Only one set of Oracle libraries should be specified in the library path environment variable. That is, if you have multiple directories containing Instant Client libraries, then only one such directory should be specified in the library path environment variable.

- If you have an Oracle home on your computer, then you should not have the `ORACLE_HOME``/lib` and Instant Client directories in the library path environment variable simultaneously, regardless of the order in which they appear in the variable. That is, only one of `ORACLE_HOME``/lib` directory (for non-Instant Client operation) or Instant Client directory (for Instant Client operation) should be specified in the library path environment variable.

- Oracle recommends that you download Instant Client from Oracle Technology Network (OTN)

  [`https://www.oracle.com/technetwork/database/database-technologies/instant-client/overview/index.html`](https://www.oracle.com/technetwork/database/database-technologies/instant-client/overview/index.html)

#### 6.4.5 Usage of Instant Client

Instant Client is a deployment feature and should be used for running production applications. For development, a full installation is necessary to access demonstration programs and so on. In general, all JDBC OCI functionality is available to an application using the Instant Client, except that the Instant Client is for client-side operation only. Therefore, server-side external procedures cannot use the Instant Client.

#### 6.4.6 About Patching Instant Client Shared Libraries

The Instant Client is a deployment feature, so the emphasis is on reducing the number and size of files required to run a JDBC OCI application. Therefore, all files needed to patch Instant Client shared libraries are not available in an Instant Client deployment. An `ORACLE_HOME` based full client installation is needed to patch the Instant Client shared libraries. The `opatch` utility will take care of patching the Instant Client shared libraries.

**Note:**

On Microsoft Windows, you cannot patch the shared libraries.

After applying the patch in an `ORACLE_HOME` environment, copy the files listed in Table 6-1 to the instant client directory.

Instead of copying individual files, you can generate Instant Client ZIP files for OCI, OCCI, JDBC, and SQL\*Plus. Then, you can copy the ZIP files to the target computer and unzip them.

The `opatch` utility stores the patching information of the `ORACLE_HOME` installation in `libclnstsh.so.18.1`. This information can be retrieved by the following command:

    genezi -v

Note that if the computer from where Instant Client is deployed does not have the `genezi` utility, then it must be copied from the `ORACLE_HOME``/bin` directory on the computer that has the `ORACLE_HOME` installation.

**Related Topics**

- JDBC OCI Instant Client Installation Process

#### 6.4.7 Regeneration of Data Shared Library and ZIP files

The OCI Instant Client Data Shared Library, `libociei.so`, can be regenerated by performing the following steps in an Administrator Installation of `ORACLE_HOME`:

    mkdir -p $ORACLE_HOME/rdbms/install/instantclient/light
    cd $ORACLE_HOME/rdbms/lib
    make -f ins_rdbms.mk ilibociei

A new version of the `libociei.so` Data Shared Library based on the current files in the `ORACLE_HOME` is then placed in the `ORACLE_HOME``/rdbms/install/instantclient` directory.

Note that the location of the regenerated Data Shared Library, `libociei.so`, is different from that of the original Data Shared Library, `libociei.so`, which is located in the `ORACLE_HOME``/instantclient` directory. The preceding steps also generate Instant Client ZIP files for OCI, OCCI, JDBC, and SQL\*Plus.

Regeneration of data shared library and ZIP files is not available on Microsoft Windows platforms.

#### 6.4.8 Database Connection Names for OCI Instant Client

All Oracle Net naming methods that do not require the `ORACLE_HOME` or `TNS_ADMIN` environment variables to locate configuration files, such as `tnsnames.ora` or `sqlnet.ora`, use the Instant Client. In particular, the connection string can be specified in the following formats:

- A Thin-style connection string of the form:

      host:port:service_name

  For example:

      url="jdbc:oracle:oci:@example.com:5521:orcl"

- A SQL connection URL string of the form:

      //host:[port][/service_name]

  For example:

      url="jdbc:oracle:oci:@//example.com:5521/orcl"

- As an Oracle Net keyword-value pair. For example:

      url="jdbc:oracle:oci:@(DESCRIPTION=(ADDRESS=(PROTOCOL=tcp)
        (HOST=localhost) (PORT=5521))
        (CONNECT_DATA=(SERVICE_NAME=orcl)))"

Naming methods that require `TNS_ADMIN` to locate configuration files continue to work if the `TNS_ADMIN` environment variable is set.

**See Also:**

[Oracle Database Net Services Administrator's Guide](../netag/managing-network-address-information.md) for more information about connection formats

If the `TNS_ADMIN` environment variable is not set and `TNSNAMES` entries, such as `inst1`, are used, then the `ORACLE_HOME` environment variable must be set and the configuration files are expected to be in the `$ORACLE_HOME/network/admin `directory.

**Note:**

In this case, the `ORACLE_HOME` environment variable is used only for locating Oracle Net configuration files. No other component of Client Code Library uses the value of the `ORACLE_HOME` environment variable.

The empty connection string is not supported. However, an alternate way to use the empty connection string is to set the `TWO_TASK` environment variable on UNIX systems, or the `LOCAL` variable on Microsoft Windows, to either a `tnsnames.ora` entry or an Oracle Net keyword-value pair. If `TWO_TASK` or `LOCAL` is set to a `tnsnames.ora` entry, then the `tnsnames.ora` file must be loaded by the `TNS_ADMIN` or `ORACLE_HOME` setting.

##### Example

Consider that the `listener.ora` file on the database server contains the following information:

    LISTENER = (ADDRESS_LIST=(ADDRESS=(PROTOCOL=tcp)(HOST=server6)(PORT=5221)))

    SID_LIST_LISTENER = (SID_LIST=
                         (SID_DESC=(SID_NAME=rdbms3)
                         (GLOBAL_DBNAME=rdbms3.server6.com)
                         (ORACLE_HOME=/home/dba/rdbms3/oracle)))

You can connect to this server in one of the following ways:

    url = "jdbc:oracle:oci:@(DESCRIPTION=(ADDRESS=(PROTOCOL=tcp)
                         (HOST=server6)(PORT=5221))
                         (CONNECT_DATA=(SERVICE_NAME=rdbms3.server6.com)))"

or:

    url = "jdbc:oracle:oci:@//server6:5221/rdbms3.server6.com"

Alternatively, you can set the `TWO_TASK` environment variable to any of the connection strings and connect to the database server without specifying the connection string along with the `sqlplus` command. For example, set the `TWO_TASK` environment in one of the following ways:

    setenv TWO_TASK "(DESCRIPTION=(ADDRESS=(PROTOCOL=tcp)(HOST=server6)(PORT=5221))
                     (CONNECT_DATA=(SERVICE_NAME=rdbms3.server6.com)))"

or:

    setenv TWO_TASK //server6:5221/rdbms3.server6.com

Now, you can connect to the database server using the following URL:

    url = "jdbc:oracle:oci:@"

The connection string can also be stored in the `tnsnames.ora` file. For example, consider that the `tnsnames.ora` file contains the following:

    conn_str = (DESCRIPTION=(ADDRESS=(PROTOCOL=tcp)(HOST=server6)(PORT=5221))
                    (CONNECT_DATA=(SERVICE_NAME=rdbms3.server6.com)))

If this `tnsnames.ora` file is located in the `/home/webuser/instantclient` directory, then you can set the `TNS_ADMIN` environment variable (or `LOCAL` on Microsoft Windows) as follows:

    setenv TNS_ADMIN /home/webuser/instantclient

Now, you can connect as follows:

    url = "jdbc:oracle:oci:@conn_str"

**Note:**

The `TNS_ADMIN` environment variable specifies the directory where the `tnsnames.ora` file is located. However, `TNS_ADMIN` does not specify the full path of the `tnsnames.ora` file, instead it specifies the directory.

If this `tnsnames.ora` file is located in the `/network/server6/home/dba/oracle/network/admin` directory in the Oracle home, then instead of using `TNS_ADMIN` to locate the `tnsnames.ora` file, you can set the `ORACLE_HOME` environment variable as follows:

    setenv ORACLE_HOME /network/server6/home/dba/oracle

Now, you can connect with either of the `conn_str` connection strings, as specified previously.

If `tnsnames.ora` can be located by `TNS_ADMIN` or `ORACLE_HOME`, then `TWO_TASK` can be set to:

    setenv TWO_TASK conn_str

You can then connect with the following URL:

    url = "jdbc:oracle:oci:@"

#### 6.4.9 Environment Variables for OCI Instant Client

The `ORACLE_HOME` environment variable no longer determines the location of the NLS, CORE, and error message files. An OCI-only application does not require the `ORACLE_HOME` environment variable to be set. However, if the variable is set, then it does not have an impact on the operation of the OCI driver. OCI driver always obtains its data from the Data Shared Library. If the Data Shared Library is not available, only then the `ORACLE_HOME` environment variable is used and a full client installation is assumed. Even though the `ORACLE_HOME` environment variable is not required to be set, if it is set, then it must be set to a valid operating system path name that identifies a directory.

Environment variables `ORA_NLS10` and `ORA_NLSPROFILES33` are ignored while using the Instant Client.

If the `ORA_TZFILE` variable is not set, then the Instant Client uses the larger `timezlrg_n.dat` file from the Data Shared Library, which is the default setting. If the smaller `timezone_n.dat` file is to be used from the Data Shared Library, then set the `ORA_TZFILE` environment variable to the name of the file without any absolute or relative path names. That is:

On UNIX systems:

    setenv ORA_TZFILE timezone_n.dat

On Microsoft Windows:

    set ORA_TZFILE timezone_n.dat

In the examples above, n is the time zone data file version number.

If the OCI driver is not using the Instant Client because of nonavailability of the Data Shared Library, then the `ORA_TZFILE` variable, if set, names a complete path name, as it does in previous Oracle Database releases.

If `TNSNAMES` entries are used, then, as mentioned earlier, the `TNS_ADMIN` directory must contain the `TNSNAMES` configuration files, and if `TNS_ADMIN` is not set, then the `ORACLE_HOME/network/admin` directory must contain Oracle Net Services configuration files.

### 6.5 About Instant Client Light (English)

The lightweight version of Instant Client is called Instant Client Light (English). Instant Client Light is the short name. Instant Client Light is a significantly smaller version of Instant Client. This reduces the disk space requirements of the client installation by about 63 MB. This is achieved by the lightweight Data Shared Library, `libociicus.so` on UNIX systems, which is 4 MB in size and a subset of the data shared library, `libociei.so`, which is 67 MB in size.

The lightweight data shared library supports only a few character sets and error messages that are only in English. Therefore, the name Instant Client Light (English). Instant Client Light is designed for applications that require English-only error messages and use either US7ASCII, WE8DEC, or one of the Unicode character sets.

This section covers the following topics:

- Data Shared Library for Instant Client Light (English)

- Globalization Settings

- Operation

- Installing Instant Client Light (English)

#### 6.5.1 Data Shared Library for Instant Client Light (English)

Table 6-2 lists the names of the data shared libraries for Instant Client and Instant Client Light (English) on different platforms. The table also specifies the size of each data shared library in parentheses following the library file name.

Table 6-2 Data Shared Library for Instant Client and Instant Client Light (English)

| Platform          | Instant Client           | Instant Client Light (English) |
|:------------------|:-------------------------|:-------------------------------|
| Solaris           | `libociei.so` (67 MB)    | `libociicus.so` (4 MB)         |
| Linux             | `libociei.so` (67 MB)    | `libociicus.so` (4 MB)         |
| Microsoft Windows | `oraociei19.dll` (85 MB) | `oraociicus19.dll` (15 MB)     |

#### 6.5.2 Globalization Settings

The `NLS_LANG` setting determines the language, territory, and character set as `language``_``territory``.``characterset`. In Instant Client Light, `language` can only be `American`, `territory` can be any that is supported, and `characterset` can be any one of the following:

- Single-byte

  - US7ASCII

  - WE8DEC

  - WE8MSWIN1252

  - WE8ISO8859P1

- Unicode

  - UTF8

  - AL16UTF16

  - AL32UTF8

Specifying character set or national character set other than those listed as the client or server character set or setting the language in `NLS_LANG` on the client will throw one of the following errors:

- `ORA-12734`

- `ORA-12735`

- `ORA-12736`

- `ORA-12737`

With Instant Client Light, the error messages obtained are only in English. Therefore, the valid values for the `NLS_LANG` setting are of the type:

    American_territory.characterset

where, `territory` can be any valid and supported territory and `characterset` can be any one the previously listed character sets.

Instant Client Light can operate with the OCI environment handles created in the OCI_UTF16 mode.

**See Also:**

[Oracle Database Globalization Support Guide](../nlspg/setting-up-globalization-support-environment.md) for more information about NLS settings

#### 6.5.3 Operation

To use the Instant Client Light, an application must set the `LD_LIBARARY_PATH` environment variable in UNIX systems or the `PATH` environment variable in Microsoft Windows to a location containing the client and data shared libraries. OCI applications by default look for the OCI Data Shared Library, `libociei.so` in the `LD_LIBRARY_PATH` environment variable in UNIX systems or the `oraociei18.dll` Data Shared Library in the `PATH` environment variable in Microsoft Windows, to determine if the application should use the Instant Client. In case this library is not found, then OCI tries to load the Instant Client Light Data Shared Library, `libociicus.so` in UNIX systems or `libociicus18.dll` in Microsoft Windows. If this library is found, then the application uses the Instant Client Light. Otherwise, a non-Instant Client is used.

#### 6.5.4 Installing Instant Client Light (English)

Instant Client Light can be installed in one of the following ways:

- From OTN

  You can download the required file from

  [`https://www.oracle.com/technetwork/database/database-technologies/instant-client/overview/index.html`](https://www.oracle.com/technetwork/database/database-technologies/instant-client/overview/index.html)

  For Instant Client Light, instead of downloading and expanding the Basic package, download and unzip the Basic Light package. The directory in which the lightweight libraries are unzipped should be empty before unzipping the files.

- From Client Admin Install

  Instead of copying `libociei.so` or `oraociei18.dll` from the `ORACLE_HOME``/instantclient` directory, copy `libociicus.so` or `oraociic18.dll` from the `ORACLE_HOME``/instantclient/light` directory. That is, the Instant Client directory on the `LD_LIBRARY_PATH` environment variable, in UNIX systems, should contain the Instant Client Light Data Shared Library, `libociicus.so`, instead of the larger OCI Instant Client Data Shared Library, `libociei.so`. In Microsoft Windows, the `PATH` environment variable should contain `oraociicus18.dll` instead of `oraociei18.dll`.

- From Oracle Universal Installer

  If the Instant Client option is selected from Oracle Universal Installer, then `libociei.so` (or `oraociei18.dll` on Microsoft Windows) is installed in the base directory of the installation which is going to be placed on the `LD_LIBRARY_PATH` environment variable. This is so that Instant Client Light is not enabled by default. The Instant Client Light Data Shared Library, `libociicus.so` (or `oraociicus18.dll` on Microsoft Windows), is installed in the `light` subdirectory of the base directory. Therefore, to use in the Instant Client Light, the OCI Data Shared Library, `libociei.so` (or `oraociei18.dll` on Windows) must be deleted or renamed and the Instant Client Light Data Shared Library must be copied from the `light` subdirectory to the base directory of the installation.

  For example, if Oracle Universal Installer has installed the Instant Client in `my_oraic_18_1` directory on the `LD_LIBRARY_PATH` environment variable, then you must perform the following to use the Instant Client Light:

      cd my_oraic_18_1
      rm libociei.so
      mv light/libociicus.so .

  **Note:**

  All the Instant Client files should always be copied or installed in an empty directory. This is to ensure that no incompatible binaries exist in the installation.
