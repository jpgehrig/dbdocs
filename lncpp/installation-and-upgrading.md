This chapter provides an overview of installation and upgrading for Oracle C++ Call Interface (OCCI).

This chapter contains these topics:

- About Installing Oracle C++ Call Interface

- About Upgrading Considerations

- About Determining the Oracle Database Versions

- About the Instant Client

- About Instant Client Light (English)

- About Using OCCI with Microsoft Visual C++

### 2.1 About Installing Oracle C++ Call Interface

OCCI is installed as part of the Oracle Database. To determine additional configuration requirements, you should refer to the Oracle Database Installation Guide and the Oracle Database Client Installation Guide that is specific to your platform.

### 2.2 About Upgrading Considerations

To use the new features available in this release, you must recompile and relink all OCCI applications, including classes generated through the Object Type Translator Utility, when upgrading from an earlier Oracle Client release.

### 2.3 About Determining the Oracle Database Versions

When an application uses several separate code paths with different server versions or client patchsets, you can verify these options both during compilation and at run time.

This sections includes the following topics:

- Determining the Oracle Client Version During Compilation

- About Determining the Oracle Client and Server Versions at Run Time

#### 2.3.1 Determining the Oracle Client Version During Compilation

The OCCI header files define `OCCI_MAJOR_VERSION` and `OCCI_MINOR_VERSION` macros. Example 2-1 illustrates one way to use these macros:

Example 2-1 How to Determine the Major Client Version and Set Performance Features

    #if (OCCI_MAJOR_VERSION > 9)
         env->setCacheSortedFlush(true);  // benefit of performance, if available
    #endif

#### 2.3.2 About Determining the Oracle Client and Server Versions at Run Time

During run time, you can check both the client and server versions of the current `Connection` by using the [getClientVersion()](connection-class.md), [getServerVersion()](connection-class.md), and [getServerVersionUString()](connection-class.md) methods.

### 2.4 About the Instant Client

The Instant Client feature makes it extremely easy and fast to deploy OCCI based customer application by eliminating the need for `ORACLE_HOME`. The storage space requirements are an additional benefit; Instant Client shared libraries occupy about one-fourth of the disk space required for a full client installation.

This section includes the following topics:

- About Benefits of Instant Client

- About Installing Instant Client Light (English)

- About Using the Instant Client

- Patching Instant Client Shared Libraries on UNIX

- Regenerating the Data Shared Library and Zip Files

- About Database Connection Names for Instant Client

- Setting Environment Variables for OCCI Instant Client

#### 2.4.1 About Benefits of Instant Client

- Installation involves copying only four files.

- Storage space requirement for the client is minimal

- No loss of functionality or performance exists for deployed applications

- Simplified packaging with ISV applications

The OCCI Instant Client capability simplifies OCCI installation. Even though OCCI is independent of `ORACLE_HOME` setting in the Instant Client mode, applications that rely on `ORACLE_HOME` settings can continue operation by setting it to the appropriate value. The activation of the Instant Client mode is only dependent on the ability to load the Instant Client data shared library. In particular, this feature allows interoperability with Oracle applications that use `ORACLE_HOME` for their data, but use a newer release of Oracle Client.

#### 2.4.2 About Installing the Instant Client

OCCI requires only four shared libraries (or dynamic link libraries, as they are called on some operating systems) to be loaded by the dynamic loader of the operating system. Oracle Database 12c Release 1 (12.1) library names are used; the number part of library names changes to remain consistent with future release numbers.

For clarity and ease of development, the library structure is changed starting with Oracle Database 12c Release 1 (12.1). The client shared library, `libclntsh.so.12.1`, depends on `libclntshcore.so.12.1`. The `libclntshcore.so.12.1` library contains the NLS and CORE functionality. Both of these libraries must be installed in the same directory.

- OCI Instant Client Data Shared Library (`libociei.so` on Linux and UNIX and `oraociei11.dll` on Windows); correct installation of this file determines if you are operating in Instant Client mode

- Client Code Library (`libclntsh.so.11.1` on Linux and UNIX and `oci.dll` on Windows)

- Security Library (`libnnz11.so` on Linux and UNIX and `orannzsbb11.dll` on Windows)

- OCCI Library (`libocci.so.11.1` on Linux and UNIX and `oraocci11.dll` on Windows)

**Note:**

The `libclntshcore.so.12.1` file must now reside in the same library as the data shared library.

This section includes the following topics:

- About the Oracle Technology Network

- About the Complete Client Installation

- Running Oracle Universal Installer

- About the Instant Client CD

##### 2.4.2.1 About the Oracle Technology Network

The Instant Client libraries are also available on the Oracle Technology Network (OTN) Web site at:

[`https://www.oracle.com/technetwork/database/database-technologies/instant-client/overview/index.html`](https://www.oracle.com/technetwork/database/database-technologies/instant-client/overview/index.html)

If these four libraries are accessible through the directory on the Operating System Library Path variable (`LD_LIBRARY_PATH` on Linux and UNIX, and `PATH` on Windows), then OCCI operates in the Instant Client mode. In this mode, there is no dependency on `ORACLE_HOME` and none of the other code and data files provided in `ORACLE_HOME` are needed by OCCI.

If you are installing Instant Client from the Oracle Technology Network,

1.  Download and install the Instant Client libraries to an empty directory, such as `instantclient_12_1`.

2.  Set the operating system shared library path environment variable (`LD_LIBRARY_PATH` on Linux and UNIX and `PATH` on Windows) to the directory used in step 1, `instantclient_12_1`.

This section includes the following topic: About the Instant Client SDK.

###### 2.4.2.1.1 About the Instant Client SDK

Instant Client can also be downloaded as an SDK package. The SDK contains all necessary header files and a makefile for developing OCCI applications in an Instant Client environment. Once developed, these applications can be deployed in any client environment. The SDK has these additional features:

- It contains C++ demonstration programs.

- It includes libraries required to link applications on Windows, and a `Make.bat` file is provided to build demos.

- The Makefile `demo.mk` is provided to build the demos for Linux and UNIX. The `instantclient_12_1` directory must be on the `LD_LIBRARY_PATH` before linking the application. These programs require symbolic links for the Client Code Library and the OCCI library, `libclntsh.so.12.1` and `libocci.so.12.1` respectively, in the `instantclient_12_1` directory. The demo Makefile, `demo.mk`, generates these before the link step. These symbolic links can also be created in a shell script:

      cd instantclient_12_1
      ln -s libclntsh.so.11.1 libclntsh.so
      ln -s libocci.so.11.1 libocci.so

- The SDK also contains the Object Type Translator (OTT) utility and its classes to generate the application header files.

##### 2.4.2.2 About the Complete Client Installation

If you performed a complete client installation by choosing the Admin option,

- On Linux or UNIX platforms, the `libociei.so` library can be copied from the `$``ORACLE_HOME``/instantclient` directory. All the other libraries can be copied from the `$``ORACLE_HOME``/lib` directory in a full Oracle installation.

- On Windows, the `oraociei11.dll` library can be copied from the `ORACLE_HOME``\instantclient` directory. All other Windows libraries can be copied from the `ORACLE_HOME``\bin` directory.

##### 2.4.2.3 Running Oracle Universal Installer

If you did not install the database, you can install these libraries by choosing the Instant Client option from the Oracle Universal Installer. After completing these steps, you can begin running OCCI applications.

1.  Install the Instant Client shared libraries to a directory such as `instantclient_12_1`.
2.  Set the operating system shared library path environment variable to the directory from step 1. For example, on Linux or UNIX, set the `LD_LIBRARY_PATH` to `instantclient_12_1`. On Windows, set `PATH` to locate the `instantclient_12_1` directory.

##### 2.4.2.4 About the Instant Client CD

You can also install Instant Client from the Instant Client CD. You must install Instant Client either in an empty directory or on a different system.

There should be only one set of Oracle libraries on the operating system Library Path variable; if you have several directories or copies of Instant Client libraries, only one directory should be on the operating system Library Path.

Similarly, if you also have an installation on an `ORACLE_HOME` of the same system, do not place both the `ORACLE_HOME``/lib` and Instant Client directory on the operating system Library Path, regardless of the order in which they appear on the Library Path. Only one of `ORACLE_HOME``/lib` directory (for non-Instant Client operation) or Instant Client directory (for Instant Client operation) should be on the operating system Library Path variable.

#### 2.4.3 About Using the Instant Client

The Instant Client feature is designed for running production applications. For development, use either the Instant Client SDK or a full installation to access OCCI header files, makefiles, demonstration programs, and so on.

#### 2.4.4 Patching Instant Client Shared Libraries on UNIX

This feature is not available on Windows platforms.

Because Instant Client is primarily a deployment feature, one of its design objectives is to reduce the number and size of necessary files. Therefore, Instant Client deployment does not include all files for patching shared libraries. You should use the `OPATCH` utility on an `ORACLE_HOME`-based full client to patch the Instant Client shared libraries. The `OPATCH` utility stores the patching information of the `ORACLE_HOME` installation in `libclntsh.so.11.1` for Linux and UNIX. This information can be retrieved using the `genezi` utility:

    genezi -v

If the `genezi` utility is not installed on the system that deploys Instant Client, you can copy it from the `ORACLE_HOME``/bin` directory of the `ORACLE_HOME` system.

After applying the patch in an `ORACLE_HOME` environment, copy the files listed in"About Installing the Instant Client" to the Instant Client directory. Instead of copying individual files, you can generate Instant Client `*.zip` files, as described in "Regenerating the Data Shared Library and Zip Files". Then, instead of copying individual files, you can instead copy the zip files to the target system and unzip them.

#### 2.4.5 Regenerating the Data Shared Library and Zip Files

This feature is not available on Windows platforms.

The Instant Client Data Shared Library, `libociei.so`, can be regenerated in a Client Admin Install of `ORACLE_HOME`. Executing Example 2-2 creates a new `libociei.so` file based on current file in `ORACLE_HOME` and place it in the `ORACLE_HOME``/rdbms/install/instantclient` directory; the make target `ilibociei` generates `libociei.so`.

This location of the regenerated data shared library, `libociei.so`, is different from the original location of `ORACLE_HOME``/instantclient`

The script in Example 2-2 also creates a directory for About Instant Client Light (English)

Example 2-2 How to Regenerate the Data Shared Library Files

    mkdir -p $ORACLE_HOME/rdbms/install/instantclient/light
    cd $ORACLE_HOME/rdbms/lib
    make -f ins_rdbms.mk ilibociei

#### 2.4.6 About Database Connection Names for Instant Client

All Oracle net naming methods that do not require use of `ORACLE_HOME` or `TNS_ADMIN` to locate configuration files such as `tnsnames.ora` or `sqlnet.ora` work in the Instant Client mode.

The `connectString` parameter in the [createConnection()](connectionpool-class.md) call can be specified in the following formats:

- As an SQL Connect URL string, of the form:

      //host:[port][/service name]

  such as:

      //myserver111:5521/bjava21

- As an Oracle Net keyword-value pair. For example:

      (DESCRIPTION=(ADDRESS=(PROTOCOL=tcp) (HOST=myserver111) (PORT=5521))
      (CONNECT_DATA=(SERVICE_NAME=bjava21)))

- As a connection name that is resolved through Directory Naming when the site is configured for LDAP server discovery.

- As an entry in the `tnsnames.ora` file.

  If the `TNS_ADMIN` environment variable is not set, and `TNSNAMES` entries such as `inst1` are used, then the `ORACLE_HOME` variable must be set and the configuration files are expected to be in the `$``ORACLE_HOME``/network/admin` directory.

  Naming methods that require `TNS_ADMIN` to locate configuration files continue to work if the `TNS_ADMIN` environment variable is set.

  The `ORACLE_HOME` variable in this case is only used for locating Oracle Net configuration files, and no other component of OCCI Client Code Library uses the value of `ORACLE_HOME`.

The empty `connectString` parameter of [createConnection()](connectionpool-class.md) is supported by setting the environment variable (`TWO_TASK` on Linux and UNIX, and `LOCAL` on Windows) to one of the values described earlier.

**See Also:**

[Oracle Database Net Services Administrator's Guide](../netag/configuring-naming-methods.md) for more information on the connect descriptor.

#### 2.4.7 Setting Environment Variables for OCCI Instant Client

The `ORACLE_HOME` environment variable no longer determines the location of Globalization Support, CORE, and error message files. An OCCI-only application should not require `ORACLE_HOME` to be set. However, if it is set, it does not have an impact on OCCI's operation. OCCI always obtains its data from the Data Shared Library. If the Data Shared Library is not available, only then is `ORACLE_HOME` used and a full client installation is assumed. When set, `ORACLE_HOME` should be a valid operating system path name that identifies a directory.

Environment variables `ORA_NLS33`, `ORA_NLS32`, and `ORA_NLS` are ignored in the Instant Client mode.

In the Instant Client mode, if the `ORA_TZFILE` variable is not set, then the larger, default, `timezlrg_``n``.dat` file (where `n` is the version number of the file) from the Data Shared Library is used. If using the smaller `timezone`\_`n``.dat` file from the Data Shared Library, then set the `ORA_TZFILE` environment variable to the name of the file without any absolute or relative path names, as shown in Example 2-3.

If OCCI is not operating in the Instant Client mode because the Data Shared Library is not available, the `ORA_TZFILE` variable, if set, names a complete path name.

If `TNSNAMES` entries are used, then `TNS_ADMIN` directory must contain the `TNSNAMES` configuration files. If `TNS_ADMIN` is not set, the `ORACLE_HOME``/network/admin` directory must contain Oracle Net Services configuration files.

Example 2-3 How to set the ORA_TZFILE Environment Variable

On Linux and UNIX:

    setenv ORA_TZFILE timezone_n.dat

On Windows:

    set ORA_TZFILE timezone_n.dat

### 2.5 About Instant Client Light (English)

Instant Client Light (English) further reduces installation space requirements of the client installation over Instant Client by another 63 MB. Specifically, the installation of the Instant Client Light (English) shared library, `libociicus.so` on Linux and UNIX and `oraociicus11.dll` for Windows, occupies 4 MB on UNIX platforms, when the full Instant Client shared library, libociei.so, occupies 67 MB of disk space.

Instant Client Light (English), as the name implies, is geared toward applications that require English-only error messages and use either `US7ASCII`, `WE8DEC`, or a Unicode characterset. Instant Client Light (English) also has no restrictions on the `TERRITORY` field of the `NLS_LANG` setting. As a result, applications that meet these characterset and territory criteria can significantly reduce its footprint if they operate in the Instant Client Light (English) environment.

This section includes the following topics:

- About Globalization Settings for Instant Client Light (English)

- About Using Instant Client Light (English)

- About Installing Instant Client Light (English)

#### 2.5.1 About Globalization Settings for Instant Client Light (English)

Instant Client Light (English) supports the following character sets:

- Single-byte character sets include `US7ASCII`, `WE8DEC`, `WE8MSWIN1252`, and `WE8ISO8859P1`.

- Unicode character sets include `UTF8`, `AL16UTF16`, and `AL32UTF8`.

Instant Client Light (English) returns an error message if the application attempts to use a character set or a national character set not listed here, either on the client or on the database. The possible error messages, listed here, are only available in English:

- ORA-12734 Instant Client Light: unsupported client national character set (NLS_LANG value set)

- ORA-12735 Instant Client Light: unsupported client character set (NLS_LANG value set)

- ORA-12736 Instant Client Light: unsupported server national character set (NLS_LANG value set)

- ORA-12737 Instant Client Light: unsupported server character set (NLS_LANG value set)

When setting `NLS_LANG` parameters, use the following:

    American_territory.charset

where `territory` is any valid Territory that can be specified through `NLS_LANG`, and `charset` is a character set listed in this section.

**See Also:**

[Oracle Database Globalization Support Guide](../nlspg/setting-up-globalization-support-environment.md) for more information about NLS settings.

#### 2.5.2 About Using Instant Client Light (English)

To determine whether to operate in the Instant Client mode, OCCI applications look for the Data Shared Library on the `LD_LIBRARY_PATH` for Linux and UNIX and `PATH` on Windows. If this library is not found, OCCI attempts to load the Instant Client Light (English) Data Shared Library, `libociicus.so` for Linux and UNIX and `oraociicus11.dll` on Windows. If neither is found, a full `ORACLE_HOME` installation is assumed.

#### 2.5.3 About Installing Instant Client Light (English)

Note that all Instant Client and Instant Client Light (English) files should always be copied or installed into an empty directory to ensure that there are no incompatible binaries in the final installation.

There are three ways to install Instant Client Light (English) as described in the following topics:

- Downloading from Oracle Technology Network

- About Using the Client Admin Install

- Installing with Oracle Universal Installer

##### 2.5.3.1 Downloading from Oracle Technology Network

When installing Instant Client Light (English) from Oracle Technology Network (OTN), download and unzip the `basiclite.zip` package instead of the usual `basic.zip` package. You must ensure that the `instantclient_12_1` directory is empty before unzipping the libraries. The downloadable package is at the following URL on OTN:

    Oracle Instant Client

##### 2.5.3.2 About Using the Client Admin Install

Instead of copying the Instant Client Data Shared Library from the `ORACLE_HOME``/instantclient` directory, use the Instant Client Light (English) Data Shared Library, `libociicus.so for Linux and UNIX and oraociicus11.dll` for Windows, from the `ORACLE_HOME``/instantclient/light` directory. In other words, the Instant Client directory on the `LD_LIBRARY_PATH` for Linux and UNIX and `PATH` for Windows should contain the smaller Instant Client Light (English) Data Shared Libraries.

##### 2.5.3.3 Installing with Oracle Universal Installer

If the Instant Client option is selected from the Oracle Universal Installer (OUI), the full Instant Client is installed by default, but the libraries for Instant Client Light (English) are also installed. To operate in Instant Client Light (English) mode, the Instant Client Light (English) Data Shared Library must replace the Instant Client library. Therefore, you must place libociicus.so on the `LD_LIBRARY_PATH` for Linux and UNIX, and `oraociicus11.dll` on the `PATH` for Windows. This design ensures that the Instant Client Light (English) is not enabled by default.

The Instant Client Light (English) Data Shared Library is initially placed in the `ORACLE_HOME``/instantclient/light` directory. You must move it to the base directory of the installation, `ORACLE_HOME``/instantclient`, and remove the Instant Client Data Shared Library in that directory.

Example 2-4 Installing Instant Client Light (English) through Oracle Universal Installer

If the OUI has installed the Instant Client in `my_oraic_12_1` directory on the `LD_LIBRARY_PATH`, then the following commands would ensure operation in the Instant Client Light (English) mode. Note that to avoid use of incompatible binary files, all Instant Client files should be copied and installed in an empty directory.

    cd my_oraic_12_1
    rm libociei.so
    mv light/libociicus.so .

### 2.6 About Using OCCI with Microsoft Visual C++

The Oracle Database 12c Release 1 (12.1) includes OCCI libraries for developing applications with Microsoft Visual C++ version 10.0 (.NET 2010 SP1 10.0), Microsoft Visual C++ version 11.0 (.NET 2012 11.0), Microsoft Visual C++ version 12.0 (.NET 2013 12.0), and Intel 12.1 C compilers with Microsoft Visual Studio 2010 STLs. Microsoft Visual C++ version 8.0 and version 9.0 are no longer supported.

Microsoft Visual C++ version 10.0 libraries are installed in the following default locations:

    ORACLE_BASE\ORACLE_HOME\bin\oraocci12.dll
    ORACLE_BASE\ORACLE_HOME\oci\lib\msvc\oraocci12.lib

Copies of these two files are also installed under the directory:

    ORACLE_BASE\ORACLE_HOME\oci\lib\msvc\vc10

Microsoft Visual C++ 2012 OCCI libraries are installed in the following default location:

    ORACLE_BASE\ORACLE_HOME\oci\lib\msvc\vc11

When developing OCCI applications with MSVC++ 2012, ensure that the OCCI libraries are correctly selected from this directory for linking and executing.

Microsoft Visual C++ 2013 OCCI libraries are installed in the following default location:

    ORACLE_BASE\ORACLE_HOME\oci\lib\msvc\vc12

When developing OCCI applications with MSVC++ 2013, ensure that the OCCI libraries are correctly selected from this directory for linking and executing.

Applications should link with the appropriate OCCI library. You must ensure that the corresponding DLL is located in the Windows system PATH.

Applications that link to `MSVCRTD.DLL`, a debug version of Microsoft C-Runtime, `/MDd` compiler flag, should link with these specific OCCI libraries: `oraocci12d.lib` and `oraocci12d.dll`.

All Instant Client packages contain the versions of the OCCI DLLs that are compatible with Microsoft Visual C++ version 10.0.
