This chapter contains the following topics:

- About Oracle Instant Client

- Install from ZIP Files, from RPMs, and from Oracle Universal Installer

- Environment Variables for Oracle Instant Client

- Database Connection Strings for Oracle Instant Client

- SDK for Oracle Instant Client

- About Oracle Instant Client Light

- About Patching Oracle Instant Client Shared Libraries on Linux or UNIX

- Regeneration of Data Shared Library and Zip and RPM Files

### 2.1 About Oracle Instant Client

Oracle Instant Client provides the necessary Oracle Database client-side files to create and run OCI, OCCI, ODBC, and JDBC OCI applications. Useful command-line utilities including SQL\*Plus, SQL\*Loader and Oracle Data Pump are also available. Oracle Instant Client simplifies the deployment of applications by eliminating the need for an Oracle home on the client machines.

The storage space requirement of an OCI application running in Instant Client mode is significantly reduced compared to the same application running in a full client-side installation. A minimal install of Instant Client shared libraries can occupy less than 10% of the space of a full client-side installation. Finally, the Instant Client is easy to install.

Why use Instant Client?

- Installation involves unzipping a few files, or installing RPM packages.

- The number of required files and the total disk storage are significantly reduced.

- There is no loss of functionality or performance for applications deployed using Instant Client.

- It is simple for independent software vendors to package applications.

A README file is included with the Instant Client installation. It describes the version, date and time, and the operating system the Instant Client was generated on.

OCI applications, by default, look for the OCI Data Shared Library, `libociei.so` (or `Oraociei19.dll` on Windows) in the runtime library search path (for example `LD_LIBRARY_PATH` on Linux, or `PATH` on Windows) to determine if the application should operate in the Instant Client mode. If this library is not found, then OCI tries to load the Instant Client Light Data Shared Library (see Table 2-3 and Table 2-4), `libociicus.so` (or `Oraociicus19.dll` on Windows). If the Instant Client Light library is found, then the application operates in the Instant Client Light mode. Otherwise, a full installation based on Oracle home is assumed.

For Instant Client, the following tables shows the Oracle Database client-side files required to deploy an OCI application for Linux and UNIX and Microsoft Windows. Other libraries and utilities get installed, but are not needed for OCI runtime use. For example, you can delete files such as `jdbc.jar`.

Table 2-1 Instant Client Shared Libraries for Linux and UNIX

| Linux and UNIX                                 | Description for Linux and UNIX            |
|:-----------------------------------------------|:------------------------------------------|
| `libclntsh.so.19.1`<br>`libclntshcore.so.19.1` | Client Code Library                       |
| `libociei.so`<sup>Foot 1</sup>                 | OCI Instant Client Data Shared Library    |
| `libnnz19.so`                                  | Security Library                          |
| `libons.so`                                    | Oracle Notification Service (ONS) library |
| `libmql1.so`                                   | Light Weight IPC Library                  |
| `libipc1.so`                                   | Message Queue Light Library               |

<sup>Footnote 1</sup>

The libraries must reside in the same directory in order to use Instant Client.

Table 2-2 Instant Client Shared Libraries for Microsoft Windows

| Microsoft Windows                                  | Description for Microsoft Windows                |
|:---------------------------------------------------|:-------------------------------------------------|
| `oci.dll`                                          | Forwarding functions that applications link with |
| `oraociei19.dll`                                   | Data and code                                    |
| `orannzsbb19.dll`                                  | Security Library                                 |
| `oraons.dll`                                       | ONS library used by OCI internally               |
| `oci.sym`<br>`oraociei19.sym`<br>`orannzsbb19.sym` | Symbol tables                                    |

On Microsoft Windows, a `.sym` file is provided for each dynamic-link library (DLL). When the `.sym` file is present in the same location as the DLL, a stack trace with function names is generated when a failure occurs in OCI on Microsoft Windows.

In general, all OCI functionality is available to an application being run using the Instant Client, except that the Instant Client is for client-side operation only. Therefore, server-side external procedures cannot use Instant Client libraries.

For development you can also use the Instant Client SDK.

**See Also:**

- SDK for Oracle Instant Client

- [Fault Diagnosability in OCI](build-and-configure-oci-applications.md)

### 2.2 Install from ZIP Files, from RPMs, and from Oracle Universal Installer

Oracle Instant Client can be installed in several ways.

The Instant Client libraries can be installed by either choosing the Instant Client option from Oracle Universal Installer or by downloading and installing either the ZIP files or RPMs from the OCI page on the Oracle Technology Network website: [Oracle Instant Client](https://docs.oracle.com/pls/topic/lookup?ctx=en/database/oracle/oracle-database/19/lnoci&id=instant_client).

The following sections describe different ways to download and Install the Instant Client Libraries from the Oracle Technology Network Website:

- Installing from the ZIP filesInstalling from the RPM filesInstalling from the Oracle Universal Installer

#### 2.2.1 Installing from the ZIP files

This section describes how to install the Instant Client from the ZIP files.

1.  Download the desired Instant Client ZIP files. All installations require a Basic or Basic Light package.
2.  Run the following command to unzip the packages into a single directory such as `/opt/oracle/instantclient_19_3 `that is accessible to your application:
        cd /opt/oracle
          unzip instantclient-basic-linux.x64-19.3.0.0.0dbru.zip
3.  Run the following command for versions prior to 18.3 to create the appropriate links for the version of Instant Client:
        cd /opt/oracle/instantclient_12_2
          ln -s libclntsh.so.12.1 libclntsh.so
          ln -s libocci.so.12.1 libocci.so
4.  Install the `libaio` package. This is called `libaio1` on some Linux distributions.
    For example, on Oracle Linux, run the following command:
        sudo yum install libaio
5.  If Instant Client is the only Oracle software installed on this system then run the following command to update the runtime link path:
        sudo sh -c "echo /opt/oracle/instantclient_19_3 >/etc/ld.so.conf.d/oracle-instantclient.conf"
          sudo ldconfig

    Alternatively, run the following command to set the `LD_LIBRARY_PATH` environment variable prior to running the applications:

        export LD_LIBRARY_PATH=/opt/oracle/instantclient_19_3:$LD_LIBRARY_PATH

    The variable can be added optionally to the configuration files such as `~/.bash_profile` and to the application configuration files such as `/etc/sysconfig/httpd`.
6.  If you intend to co-locate the optional Oracle configuration files such as `tnsnames.ora`, `sqlnet.ora`, `ldap.ora`, or `oraaccess.xml` with Instant Client, then place them in the `network/admin` subdirectory. This needs to be created for 12.2 and earlier versions using the following command:
        mkdir -p /opt/oracle/instantclient_12_2/network/admin

    This is the default Oracle configuration directory for applications linked with the Instant Client.

    Alternatively, Oracle configuration files can be placed in another accessible directory and then set the environment variable `TNS_ADMIN` to that directory name.
7.  To use binaries such as sqlplus from the SQL\*Plus package, unzip the package to the same directory as the Basic package and then update the `PATH` environment variable as follows:
        export PATH=/opt/oracle/instantclient_19_3:$PATH
8.  Start your application.

#### 2.2.2 Installing from the RPM files

This section describes how to install the Instant Client from the RPM files.

1.  Download the desired Instant Client RPM files. All installations require a Basic or Basic Light package.
2.  Run the following command to install the packages with `yum`:
        sudo yum install oracle-instantclient19.3-basic-19.3.0.0.0-1.x86_64.rpm

    **Note:**

    Starting from version 19.3, by default only one version of the Instant Client RPM libraries can be installed at a time.
3.  For versions prior to 19, if Instant Client is the only Oracle software installed on the system, then run the following command to update the runtime link path:
        sudo sh -c "echo /usr/lib/oracle/18.3/client64/lib >/etc/ld.so.conf.d/oracle-instantclient.conf"
          sudo ldconfig

    **Note:**

    For Instant Client 19.3 RPM packages, these commands are run automatically.

    Alternatively, run the following command to set the `LD_LIBRARY_PATH` environment variable prior to running the applications:

        export LD_LIBRARY_PATH=/opt/oracle/instantclient_19_3:$LD_LIBRARY_PATH

    The variable can optionally be added to configuration files such as `~/.bash_profile` and to the application configuration files such as `/etc/sysconfig/httpd`.
4.  If you intend to co-locate the optional Oracle configuration files such as `tnsnames.ora`, `sqlnet.ora`, `ldap.ora`, or `oraaccess.xml` with Instant Client, then place them in the `network/admin` subdirectory. This needs to be created for 12.2 and earlier versions using the following command:
        sudo mkdir -p /usr/lib/oracle/12.2/client64/lib/network/admin

    This is the default Oracle configuration directory for applications linked with the Instant Client.

    Alternatively, Oracle configuration files can be placed in another accessible directory and then set the environment variable `TNS_ADMIN` to that directory name.
5.  To use binaries tools package, use `yum` to install the package to the same directory as the Basic package and then update the `PATH` environment variable as follows:
        export PATH=/opt/oracle/instantclient_19_3:$PATH
6.  Start your application.

#### 2.2.3 Installing from the Oracle Universal Installer

This section describes how to install Oracle Instant Client from the Oracle Universal Installer.

For installing Instant Client from Oracle Universal Installer, invoke the Oracle Universal Installer, select the Instant Client option and then install the Instant Client shared libraries to an empty directory, such as `instantclient_19_3`, for Oracle Database release 19c, version 19.3.

See Steps 5 and 6 in Installing from the ZIP files about setting the environment variables.

If you did a complete client installation (by choosing the `Admin` option in Oracle Universal Installer), the locations of the Instant Client shared libraries in a full client installation are:

On Linux or UNIX:

`libociei.so` library is in `$ORACLE_HOME/instantclient`

`libclntsh.so.19.1`, `libclntshcore.so.19.1`, and `libnnz19.so` are in `$ORACLE_HOME/lib`

On Windows:

`oraociei19.dll` library is in `ORACLE_HOME\instantclient`

`oci.dll`, `ociw32.dll`, and `orannzsbb19.dll` are in `ORACLE_HOME\bin`

To enable running the OCI application using Instant Client, copy the preceding libraries to a different directory and then set the operating system shared library path to locate this directory.

**Note:**

All the libraries must be copied from the same Oracle home and must be placed in the same directory. Co-location of symlinks to Instant Client libraries is not a substitute for physical co-location of the libraries.

There should be only one set of Oracle libraries on the operating system Library Path variable. That is, if you have multiple directories containing Instant Client libraries, then only one such directory should be on the operating system Library Path.

Similarly, if an Oracle home-based installation is performed on the same system, then you should not have `ORACLE_HOME/lib` and the Instant Client directory on the operating system Library Path simultaneously regardless of the order in which they appear on the Library Path. That is, either the `ORACLE_HOME/lib` directory (for non-Instant Client operation) or Instant Client directory (for Instant Client operation) should be on the operating system Library Path variable, but not both.

To enable other capabilities such as OCCI and JDBC OCI, you must copy a few additional files. To enable OCCI, you must install the OCCI Library (`libocci.so.19.1` on Linux or UNIX and `oraocci19.dll` on Windows) in the Instant Client directory. For the JDBC OCI driver, in addition to the three OCI shared libraries, you must also download OCI JDBC Library (for example `libocijdbc19.so` on Linux or UNIX and `ocijdbc19.dll` on Windows). Place all libraries in the Instant Client directory.

**Note:**

On hybrid platforms, such as Sparc64, to operate the JDBC OCI driver in the Instant Client mode, copy the `libociei.so` library from the `ORACLE_HOME/instantclient32` directory to the Instant Client directory. Copy all other Sparc64 libraries needed for the JDBC OCI Instant Client from the `ORACLE_HOME/lib32` directory to the Instant Client directory.

### 2.3 Environment Variables for Oracle Instant Client

The `ORACLE_HOME` environment variable no longer determines the location of NLS, CORE, and error message files.

An OCI-only application should not require `ORACLE_HOME` to be set. However, if it is set, it does not affect OCI. OCI always obtains its data from the Data Shared Library. If the Data Shared Library is not available, only then is `ORACLE_HOME` used and a full client installation is assumed. Though `ORACLE_HOME` is not required to be set, if it is set, then it must be set to a valid operating system path name that identifies a directory.

If Dynamic User callback libraries are to be loaded, then as this guide specifies, the callback package must reside in `ORACLE_HOME/lib` (`ORACLE_HOME\bin` on Windows). Set `ORACLE_HOME` in this case.

Environment variables `ORA_NLS10` and `ORA_NLS_PROFILE33` are ignored in the Instant Client mode.

Beginning with Oracle Database 12c Release 2 (12.2), when using Instant Client libraries, the Instant Client can use the `ORA_TZFILE` environment variable to read the time zone file from the file system when this environment variable is set. Otherwise, if the `ORA_TZFILE` variable is not set, then the larger, default, `timezlrg_``n``.dat` file from the Data Shared Library is used. If the smaller `timezone_``n``.dat` file is to be used from the Data Shared Library, then set the `ORA_TZFILE` environment variable to the name of the file without any absolute or relative path names. The file must be copied to subdirectory `oracore/zoneinfo` for (UNIX/LINUX) or `oracore\zoneinfo` for (Microsoft Windows) in the instant client directory. You can use the `genezi` utility with the `-v` option to verify that the time zone file and location is valid or run SQL\*Plus.

On Linux or UNIX:

    export ORA_TZFILE=timezone_n.dat

On Windows:

    set ORA_TZFILE=timezone_n.dat

In these examples, n is the time zone data file version number.

Be sure to create subdirectory `oracore/zoneinfo` for (UNIX/LINUX) or subdirectory `oracore\zoneinfo` for (Microsoft Windows) where `oracoei` or `oraociicus` DLL's are located (typically in the `instantclient_12_2` directory) and copy the `timezone_``n``.dat` file to this directory.

To determine the versions of small and large time zone files that are packaged in the Instant Client Data Shared Library, enter the following command to run the `genezi` utility:

    genezi -v

If OCI is not operating in the Instant Client mode (because the Data Shared Library is not available), then `ORA_TZFILE` variable, if set, names a complete path name as it does in previous Oracle Database releases.

If `TNSNAMES` local naming parameters are used, then, as mentioned earlier, `TNS_ADMIN` directory must contain the `TNSNAMES` configuration files. If `TNS_ADMIN` is not set, then the `ORACLE_HOME/network/admin` directory must contain Oracle Net Services configuration files.

### 2.4 Database Connection Strings for Oracle Instant Client

All Oracle Net naming methods that do not require use of `ORACLE_BASE_HOME`, or `ORACLE_HOME` (to locate configuration files such as `tnsnames.ora`, `sqlnet.ora`, or `oraaccess.xml`) work with the Instant Client mode.

You can use the `network/admin` to co-locate optional Oracle configuration files such as `tnsnames.ora`, `sqlnet.ora`, `ldap.ora`, or `oraaccess.xml` with Instant Client. Prior to release 18.1, the users had to create the `network/admin` directory manually.

See [Database Connection Strings](build-and-configure-oci-applications.md) for complete information about database connection strings.

**See Also:**

[Oracle Database Net Services Administrator's Guide](../netag/configuring-naming-methods.md) chapter on "Configuring Naming Methods" for more about connect descriptors

This section includes the following topic: [Examples of Oracle Database Connection String Connect Identifiers](build-and-configure-oci-applications.md).

### 2.5 SDK for Oracle Instant Client

The software development kit (SDK) is a set of development tools that allows the creation of applications can be downloaded from the Instant Client link URL on the Oracle Technology Network website:

[Oracle Instant Client](https://docs.oracle.com/pls/topic/lookup?ctx=en/database/oracle/oracle-database/19/lnoci&id=instant_client)

- The Instant Client SDK package has both C and C++ header files and a makefile for developing OCI and OCCI applications while in an Instant Client environment. Developed applications can be deployed in any client environment.

- The SDK contains C and C++ demonstration programs.

- On Windows, libraries required to link the OCI or OCCI applications are also included. `Make.bat` is provided to build the demos.

- On UNIX or Linux, the makefile `demo.mk` is provided to build the demos. The `instantclient_19` directory must be in the runtime library search path, for example `LD_LIBRARY_PATH` before linking the application. The OCI and OCCI programs require the presence of `libclntsh.so` and `libocci.so` symbolic links in the `instantclient_19` directory. Beginning with Oracle Database 18c, version 18.1, Instant Client Basic and Basic Light ZIP files on Linux, Unix, and macOS now have the `libclntsh` and `libocci` symbolic links precreated.

- The SDK also contains the Object Type Translator (OTT) utility and its classes to generate the application header files.

### 2.6 About Oracle Instant Client Light

The Instant Client Light version of Instant Client further reduces the disk space requirements of the client installation.

The size of the library has been reduced by removing error message files for languages other than English and leaving only a few supported character set definitions out of around 250.

This Instant Client Light version is geared toward applications that use either US7ASCII, WE8DEC, WE8ISO8859P1, WE8MSWIN1252, or a Unicode character set. There is no restriction on the `LANGUAGE` and the `TERRITORY` fields of the `NLS_LANG` setting, so the Instant Client Light operates with any language and territory settings. Because only English error messages are provided with the Instant Client Light, error messages generated on the client side, such as Net connection errors, are always reported in English, even if `NLS_LANG` is set to a language other than `AMERICAN`. Error messages generated by the database side, such as syntax errors in SQL statements, are in the selected language provided the appropriate translated message files are installed in the Oracle home of the database instance.

This section includes the following topics:

- Globalization Settings

- Libraries for Oracle Instant Client Light

- Install from ZIP Files, from RPMs, and from Oracle Universal Installer

#### 2.6.1 Globalization Settings

Instant Client Light supports the following client character sets:

Single-byte

- US7ASCII

- WE8DEC

- WE8MSWIN1252

- WE8ISO8859P1

Unicode

- UTF8

- AL16UTF16

- AL32UTF8

Instant Client Light can connect to databases having one of these database character sets:

- US7ASCII

- WE8DEC

- WE8MSWIN1252

- WE8ISO8859P1

- WE8EBCDIC37C

- WE8EBCDIC1047

- UTF8

- AL32UTF8

Instant Client Light returns an error if a character set other than those in the preceding lists is used as the client or database character set.

Instant Client Light can also operate with the OCI Environment handles created in the `OCI_UTF16` mode.

**See Also:**

[Oracle Database Globalization Support Guide](../nlspg/setting-up-globalization-support-environment.md) for more information about National Language Support (NLS) settings

#### 2.6.2 Libraries for Oracle Instant Client Light

OCI applications, by default, look for the OCI Data Shared Library, `libociei.so` (or `Oraociei119.dll` on Windows) in the runtime library search path (for example `LD_LIBRARY_PATH` on Linux, or `PATH` on Windows) to determine if the application should operate in the Instant Client mode.

If the OCI Data Shared Library is not found, then OCI tries to load the Instant Client Light Data Shared Library (see Table 2-3 and Table 2-4), `libociicus.so` (or `Oraociicus19.dll` on Windows). If the Instant Client Light library is found, then the application operates in the Instant Client Light mode. Otherwise, a full installation based on Oracle home is assumed.

Table 2-3 Instant Client Light Shared Libraries Linux and UNIX

| Linux and UNIX                             | Description for Linux and UNIX               |
|:-------------------------------------------|:---------------------------------------------|
| `libclntsh.so.19`<br>`libclntshcore.so.19` | Client Code Library                          |
| `libociicus.so`                            | OCI Instant Client Light Data Shared Library |
| `libnnz19.so`                              | Security Library                             |
| `libons.so`                                | Oracle Notification Service (ONS) library    |
| `libmql1.so`                               | Light Weight IPC Library                     |
| `libipc1.so`                               | Message Queue Light Library                  |

Table 2-4 Instant Client Light Shared Libraries for Microsoft Windows

| Microsoft Windows                                    | Description for Microsoft Windows                |
|:-----------------------------------------------------|:-------------------------------------------------|
| `oci.dll`                                            | Forwarding functions that applications link with |
| `oraociicus19.dll`                                   | Data and code                                    |
| `orannzsbb19.dll`                                    | Security Library                                 |
| `oci.sym`<br>`oraociicus19.sym`<br>`orannzsbb19.sym` | Symbol tables                                    |

**See Also:**

Instant Client Shared Libraries for Linux and UNIX Table 2-1

Instant Client Shared Libraries for Microsoft Windows Table 2-2

#### 2.6.3 Installing Oracle Instant Client Light

How can Instant Client Light can be installed.

Instant Client Light can be installed in one of these ways:

- Installed from Oracle Technology Network (OTN)

  The following URL is the Instant Client page on the Oracle Technology Network website: [Oracle Instant Client](https://docs.oracle.com/pls/topic/lookup?ctx=en/database/oracle/oracle-database/19/lnoci&id=instant_client)

  For Instant Client Light, download and unzip the `basiclite.zip` package in to an empty `instantclient_12_2` directory.

- Installed from an Instant Client Administrator installation

  From the `ORACLE_HOME/instantclient/light` subdirectory, copy `libociicus.so` (or `oraociicus12.dll` on Windows). The Instant Client directory on the `LD_LIBRARY_PATH` (`PATH` on Windows) should contain the Instant Client Light Data Shared Library, `libociicus.so` (`oraociicus12.dll` on Windows), instead of the larger OCI Instant Client Data Shared Library, `libociei.so` (`oraociei12.dll` on Windows).

- Installed from an Oracle Universal Installer installation

  When you select the Instant Client option from the Oracle Universal Installer, `libociei.so` (or `oraociei12.dll` on Windows) is installed in the base directory of the installation, which means these files are placed on the `LD_LIBRARY_PATH` (`PATH` on Windows).

  The Instant Light Client Data Shared Library, `libociicus.so` (or `oraociicus12.dll` on Windows), is installed in the `light` subdirectory of the base directory and not enabled by default. Therefore, to operate in the Instant Client Light mode, the OCI Data Shared Library, `libociei.so` (or `Oraociei12.dll` on Windows) must be deleted or renamed and the Instant Client Light library must be copied from the `light` subdirectory to the base directory of the installation.

  For example, if Oracle Universal Installer has installed the Instant Client in `my_oraic_12_2` directory on the `LD_LIBRARY_PATH` (`PATH` on Windows), then use the following command sequence to operate in the Instant Client Light mode:

      cd my_oraic_12_2
      rm libociei.so
      mv light/libociicus.so .

  **Note:**

  To ensure that no incompatible binaries exist in the installation, always copy and install the Instant Client files in to an empty directory.

### 2.7 About Patching Oracle Instant Client Shared Libraries on Linux or UNIX

Because Instant Client is a deployment feature, the number and size of files (client footprint) required to run an OCI application has been reduced.

Hence, all files needed to patch Instant Client shared libraries are not available in an Instant Client deployment. A complete client installation based on Oracle home is needed for patching. Use the `opatch` utility for patching.

After you apply the patch in an Oracle home environment, copy the files listed in About Oracle Instant Client to the instant client directory, as described in Install from ZIP Files, from RPMs, and from Oracle Universal Installer.

Instead of copying individual files, you can generate Instant Client zip and RPM files for OCI and OCCI, JDBC, and SQL\*Plus as described in Regeneration of Data Shared Library and Zip and RPM Files. Then, you can copy the zip and RPM files to the target system and unzip them as described in Install from ZIP Files, from RPMs, and from Oracle Universal Installer.

The `opatch` utility stores the patching information of the `ORACLE_HOME` installation in `libclntsh.so`. This information can be retrieved by the following command:

    genezi -v

If the Instant Client deployment system does not have the `genezi` utility, you can copy it from the `ORACLE_HOME``/bin` directory.

**Note:**

The `opatch` utility is not available on Windows.

### 2.8 Regeneration of Data Shared Library and Zip and RPM Files

The process to regenerate the data shared library and the zip and RPM files changed in Oracle Database 12c Release 1 (12.1).

Separate make file targets are used to create the data shared libraries, zip, and RPM files either individually or all at once. Currently, `ilibociei` builds only the zip and RPM files. Regeneration of data shared libraries requires both a compiler and linker, which may not be available on all installations. The sections that follow show the make file target used to regenerate data shared libraries, zip, and RPM files.

**Note:**

The regenerated Instant Client binaries contain only the Instant Client files installed in the Oracle Client Administrator Home from which the regeneration is done. Therefore, error messages, character set encodings, and time zone files that are present in the regeneration environment are the only ones that are packaged in the data shared libraries. Error messages, character set encodings, and time zone files depend on which national languages were selected for the installation of the Oracle Client Administrator Home.

Regeneration of the data shared library and the zip and RPM files is not available on Windows platforms.

This section includes the following topics:

- Regenerating Data Shared Library libociei.so

- Regenerating Data Shared Library libociicus.so

- Regenerating Data Shared Libraries libociei.so and libociicus.so in One Step

- Regenerating Zip and RPM Files for the Basic Package

- Regenerating Zip and RPM Files for the Basic Light Package

- Regenerating Zip and RPM Files for the JDBC Package

- Regenerating Zip and RPM Files for the ODBC Package

- Regenerating Zip and RPM Files for the SQL\*Plus Package

- Regenerating Zip and RPM Files for the Tools Package

- Regenerating Zip and RPM Files for All Packages

#### 2.8.1 Regenerating Data Shared Library libociei.so

The OCI Instant Client Data Shared Library (`libociei.so`) can be regenerated by using the following commands in an Administrator Install of `ORACLE_HOME`:

    cd $ORACLE_HOME/rdbms/lib
    make -f ins_rdbms.mk igenlibociei

The new regenerated `libociei.so` is placed in the `ORACLE_HOME``/instantclient` directory. The original existing `libociei.so` located in this same directory is renamed to `libociei.so0`.

#### 2.8.2 Regenerating Data Shared Library libociicus.so

To regenerate Instant Client Light data shared library (`libociicus.so`), use the following commands:

    mkdir -p $ORACLE_HOME/rdbms/install/instantclient/light
    cd $ORACLE_HOME/rdbms/lib
    make -f ins_rdbms.mk igenlibociicus

The newly regenerated `libociicus.so` is placed in the `ORACLE_HOME`/`instantclient`/`light` directory. The original existing `libociicus.so` located in this same directory is renamed to `libociicus.so0`.

#### 2.8.3 Regenerating Data Shared Libraries libociei.so and libociicus.so in One Step

To regenerate the data shared libraries `libociei.so` and libociicus.so, use the following commands:

    mkdir -p $ORACLE_HOME/rdbms/install/instantclient/light
    cd $ORACLE_HOME/rdbms/lib
    make -f ins_rdbms.mk igenliboci

The newly regenerated `libociei.so` is placed in the `ORACLE_HOME`/`instantclient` directory. The original existing `libociei.so` located in this same directory is renamed to `libociei.so0`.

The newly regenerated `libociicus.so` is placed in the `ORACLE_HOME`/`instantclient`/`light` directory. The original existing `libociicus.so` located in this same directory is renamed to `libociicus.so0`.

#### 2.8.4 Regenerating Zip and RPM Files for the Basic Package

To regenerate the zip and RPM files for the basic package, use the following commands:

    cd $ORACLE_HOME/rdbms/lib
    make -f ins_rdbms.mk ic_basic_zip

#### 2.8.5 Regenerating Zip and RPM Files for the Basic Light Package

To regenerate the zip and RPM files for the basic light package, use the following commands:

    cd $ORACLE_HOME/rdbms/lib
    make -f ins_rdbms.mk ic_basiclite_zip

#### 2.8.6 Regenerating Zip and RPM Files for the JDBC Package

To regenerate the zip and RPM files for the JDBC package, use the following commands:

    cd $ORACLE_HOME/rdbms/lib
    make -f ins_rdbms.mk ic_jdbc_zip

#### 2.8.7 Regenerating Zip and RPM Files for the ODBC Package

To regenerate the zip and RPM files for the ODBC package, use the following commands:

    cd $ORACLE_HOME/rdbms/lib
    make -f ins_rdbms.mk ic_odbc_zip

#### 2.8.8 Regenerating Zip and RPM Files for the SQL\*Plus Package

To regenerate the zip and RPM files for the SQL\*Plus package, use the following commands:

    cd $ORACLE_HOME/rdbms/lib
    make -f ins_rdbms.mk ic_sqlplus_zip

#### 2.8.9 Regenerating Zip and RPM Files for the Tools Package

To regenerate the zip and RPM files for the tools package, use the following commands:

    cd $ORACLE_HOME/rdbms/lib
    make -f ins_rdbms.mk ic_tools_zip

#### 2.8.10 Regenerating Zip and RPM Files for All Packages

To regenerate the zip and RPM files for all packages, use the following commands:

    cd $ORACLE_HOME/rdbms/lib
    make -f ins_rdbms.mk ilibociei

The new zip and RPM files are generated under the following directory:

`$ORACLE_HOME/rdbms/install/instantclient`

Regeneration of the data shared library and the zip and RPM files is not available on Windows platforms.
