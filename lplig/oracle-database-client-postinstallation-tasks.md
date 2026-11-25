This chapter describes how to complete postinstallation tasks after you have installed the Oracle Database Client software. It includes information about the following topics:

- Required Postinstallation Tasks

- Recommended Postinstallation Tasks

- Required Product-Specific Postinstallation Tasks

You must perform the tasks listed in "Required Postinstallation Tasks". Oracle recommends that you perform the tasks listed in "Recommended Postinstallation Tasks" after all installations.

If you install and intend to use any of the products listed in "Required Product-Specific Postinstallation Tasks", then you must perform the tasks listed in the product-specific subsections.

### Required Postinstallation Tasks

You must perform the tasks described in the following sections after completing an installation:

- Updating Instant Client

- Connecting with Instant Client

#### Updating Instant Client

To update Instant Client:

1.  Download Instant Client from Oracle Technology Network at
    [`http://www.oracle.com/technetwork/database/features/instant-client/index-097480.html`](http://www.oracle.com/technetwork/database/features/instant-client/index-097480.html)
2.  If you want to place the files in the existing directory, then ensure that the directory is empty.
    If you want to place the files into a different directory (and remove the previous files), ensure that you update the `PATH` environment variable setting to reflect the new location.

**Caution:**

The Instant Client and Instant Client Light installations do not create an inventory. Therefore, you cannot perform patch upgrades for these installations using the `opatch` utility.

#### Connecting with Instant Client

If you installed the Instant Client installation type, you can configure users' environments to enable dynamically linked client applications to connect to a database as follows:

1.  Set the appropriate shared library path environment variable for your platform to specify the directory that contains the Instant Client libraries. For the Instant Client installation type, this directory is the Oracle home directory that you specified during the installation, for example:
        Your_current_dir/instantclient_19_3
2.  Use one of the following methods to specify database connection information for the client application:
    - Specify a SQL connect URL string using the following format:

          //host:port/service_name

      For example:

          //shobeen:1521/sales_us

    - Set the `TNS_ADMIN` environment variable to specify the location of the `tnsnames.ora` file and specify a service name from that file.

    - Set the `TNS_ADMIN` and the `TWO_TASK` environment variables to specify a service name from the `tnsnames.ora` file.

**Note:**

It is not required that you specify the `ORACLE_HOME` environment variable.

### Recommended Postinstallation Tasks

Oracle recommends that you perform the tasks described in the following sections after completing an installation:

- Connecting Instant Client or Instant Client Light to an Oracle Database

- Setting the NLS_LANG Environment Variable

#### Connecting Instant Client or Instant Client Light to an Oracle Database

Before you can connect Instant Client (including Instant Client Light) to an Oracle database, ensure that the LD_LIBRARY_PATH environment variable specifies the directory that contains the Instant Client libraries. This directory is the ORACLE_HOME directory that you specified during installation.

For example, the shared libraries for Instant Client or Instant Client Light (if you have configured Instant Client Light), are in:

    Your_current_dir/instantclient_19_3

After checking the `LD_LIBRARY_PATH` environment variable, you can use any of the following methods to specify Oracle Database connection information for client applications:

- Specifying a Connection by Using the Easy Connect Naming Method

- Specifying a Connection Using an Empty Connect String and TWO_TASK

##### Specifying a Connection by Using the Easy Connect Naming Method

You can specify a connection address to an Oracle Database directly from a client application, without having to configure a `tnsnames` setting for the Instant Client. This method is convenient as you do not have to create and manage a `tnsnames.ora` file. However, the application users must specify the host name and port number when they want to log in to the application.

For example, if you run SQL\*Plus on the client computer and want to connect to the `sales_us` database, which is located on a server whose host name is `shobeen` and port number is `1521`, then you can log in as follows:

    Enter user-name: system@admin@//shobeen:1521/sales_us

Similarly, in the application code, you can use Oracle Call Interface net naming methods to create the Instant Client-to-Oracle Database connection. For example, the following formats in the `OCIServerAttach()` call specify the connection information:

- Specify a SQL connect URL string using the following format:

      //host[:port][/service_name]

  For example:

      //shobeen:1521/sales_us

- Alternatively, you can specify the SQL connect information as an Oracle Net keyword-value pair. For example:

      "(DESCRIPTION=(ADDRESS=(PROTOCOL=tcp) (HOST=shobeen) (PORT=1521))
      (CONNECT_DATA=(SERVICE_NAME=sales_us)))"

  **See Also:**

  [Oracle Call Interface Programmer's Guide](../lnoci/instant-client.md) for more information on using Oracle Call Interface Instant Client

##### Specifying a Connection Using an Empty Connect String and TWO_TASK

You can set the connect string to an empty connect string (""), and then set the `TWO_TASK` environment variable to one of the following values:

- A direct address, as described under "Specifying a Connection by Using the Easy Connect Naming Method".

- Oracle Net keyword-value pair.

- A `tnsnames.ora` entry and `TNS_ADMIN` is set to the location of `tnsnames.ora`.

- A `tnsnames.ora` entry and the following:

  - `tnsnames.ora` file located in `$ORACLE_HOME``/network/admin`.

  - The `ORACLE_HOME` environment variable set to this Oracle home.

This method allows the applications to specify internally a connection string if the application code itself uses an empty connection string. The benefit of an empty connect string is that the application itself does not have to specify the `tnsnames.ora` entry. Instead, when a user starts the application, the location of the database is determined by a script or the environment, depending on where you have set the `TWO_TASK` environment variable. The disadvantage of using empty strings is that you must configure this additional information in order for the application to connect to the database.

#### Setting the NLS_LANG Environment Variable

`NLS_LANG` is an environment variable that specifies the locale behavior for Oracle software. This variable sets the language and territory used by the client application and the database user session. It also declares the character set of the client, which is the character set of data entered or displayed by an Oracle client program, such as SQL\*Plus.

**Note:**

The character set of the data displayed is determined by the environment of the operating system, such as keyboard driver and fonts in use. The `NLS_LANG` character set should match the operating system.

See the "Setting Up a Globalization Support Environment" section in [Oracle Database Globalization Support Guide](../nlspg/setting-up-globalization-support-environment.md) for information about Globalization Support.

### Required Product-Specific Postinstallation Tasks

The following sections describe postinstallation tasks that you must perform if you install and intend to use Oracle Precompliers:

**Note:**

You must perform postinstallation tasks only for products that you intend to use.

#### Configuring Oracle Precompilers

This section describes postinstallation tasks for Pro\*C/C++.

**Note:**

All precompiler configuration files are located in the `$ORACLE_HOME/precomp/admin` directory.

##### Configuring Pro\*C/C++

Verify that the `PATH` environment variable setting includes the directory that contains the C compiler executable. The default directory for the `gcc` compiler executable is `/usr/bin`.

For more information about setting environment variables, see Pro\*C/C++ Programmer's Guide.

#### Configuring GCC as the Primary Compiler

You can configure GNU Compiler Collection (GCC) as the primary compiler if the primary supported compiler is not available. Configuring the primary compiler enables you to speed up the performance of PL/SQL modules such as packages by compiling them into native code that resides in shared libraries. This method translates the module into C code, compiles it with a C compiler, and then links it into the Oracle process. Remember that you must use one compiler to compile all your Oracle modules. You cannot compile some modules with the primary compiler and others with a different compiler.

If both, the primary supported compiler for the operating system and GCC are available, then use the primary supported compiler. However, if the primary supported compiler is not available, then use GCC.

To configure GCC as the primary compiler:

1.  Open the `spnc_commands` configuration file in a text editor. In a default installation, the `spnc_commands` file is located in the `$ORACLE_HOME/plsql` directory.

2.  Look for the following line of text and comment it out:

    `/usr/local/packages/vac/vac/$(VAC_VERSION)/bin/xlc -F$(ORACLE_HOME)/lib/xlc.cfg %(src) -O0 -qpic -q64 -I$(ORACLE_HOME)/plsql/include -I$(ORACLE_HOME)/plsql/public -s -qmkshrobj -o %(so)`

3.  Look for the following lines, which pertain to GCC, and uncomment them:

    `# /usr/bin/gcc -m64 -B/usr/bin/ %(src) -O1 -fPIC -I$(ORACLE_HOME)/plsql/include -I$(ORACLE_HOME)/plsql/public -s -shared -o %(so)`

4.  Save and close the `spnc_commands` configuration file.

**See Also:**

[Oracle Database PL/SQL User's Guide and Reference](../lnpls/compiling-pl-sql-units-native-execution.md) for more information on PL/SQL native compilation and the `spnc_commands` configuration file

##### Using the IBM XL C/C++ compiler for PL/SQL Native Compilation

By default, PL/SQL native compilation is configured to use the GCC compiler. If you want to use the IBM XL compiler (XLC) instead of the GCC compiler, then make the following changes in the `$ORACLE_HOME/plsql/spnc_commands` file:

1.  Comment out the lines for the GCC compiler.
2.  Uncomment the lines for IBM XL compiler.
