This chapter guides you through the basics of testing your Oracle SQLJ installation and configuration and running a simple application.

This chapter discusses the following topics:

- Assumptions and Requirements

- Checking the Installation and Configuration

- Testing the Setup

### 2.1 Assumptions and Requirements

This section discusses basic assumptions about your environment and requirements of your system so that you can run SQLJ, covering the following topics:

- Assumptions About Your Environment

- Requirements for Using the Oracle SQLJ Implementation

- SQLJ Environment

- Environment Considerations

- SQLJ Backward Compatibility

#### 2.1.1 Assumptions About Your Environment

The following assumptions are made about the system on which you will be running the Oracle SQLJ implementation:

- You have a standard Java environment that is operational on your system. This would typically be using a Sun Microsystems Java Development Kit (JDK), but other implementations of Java will work. Ensure that you can run Java (typically `java`) and the Java compiler (typically `javac`).

  To translate and run SQLJ applications on a standard JDK, you must use JDK 6 or JDK 7. You must use the JDBC driver of the same version as that of SQLJ, can be thin or OCI8 driver

  **See Also:**

  "SQLJ Environment"

**Note:**

A Java run-time environment (JRE), such as the one installed with Oracle Database 12c Release 2 (12.2), is not by itself sufficient for translating SQLJ programs. However, a JRE is sufficient for running SQLJ programs that have already been translated and compiled.

- You can already run JDBC applications in your environment.

  **See also:**

  [Oracle Database JDBC Developer’s Guide](../jjdbc/introducing-JDBC.md)

#### 2.1.2 Requirements for Using the Oracle SQLJ Implementation

The following are required to use the Oracle SQLJ implementation:

- A database system that is accessible using your JDBC driver

- Class files for the SQLJ translator

  Translator-related classes are available in the following file:

  `ORACLE_HOME``/sqlj/lib/translator.jar`

  **Note:**

  For more information about `translator.jar``,` refer to "Set the Path and Classpath".

- Class files for the SQLJ run time.

  `ORACLE_HOME``/sqlj/lib/runtime12.jar`

  **Note:**

  `runtime12ee.jar` has been deprecated since Oracle Database 11g Release 1. Use `runtime12.jar` instead.

#### 2.1.3 SQLJ Environment

To ensure that you have a fully working environment, you must consider several aspects of your environment: SQLJ and its code generation mode, JDBC, and the JDK.

**Note:**

Code generation is determined by the SQLJ `-codegen` option. Refer to "[Code Generation (-codegen)](translator-command-line-and-options.md)" for more information.

The following is a typical environment setup for Oracle-specific code generation:

- SQLJ code generation: `-codegen=oracle` (default)

- SQLJ translation library: `translator.jar`

- SQLJ run-time library: `runtime12.jar`

- JDBC drivers: Oracle Database 12c Release 2 (12.2)

- JDK version: 6 or 7

**Note:**

If you are running against different JDBC versions, then translate against the earlier version.

#### 2.1.4 Environment Considerations

You can run the application against a JDK version that is at least as high as the version you translated the code under.

**Note:**

For more information about `translator.jar``,` refer to "Set the Path and Classpath".

#### 2.1.5 SQLJ Backward Compatibility

You must keep in mind the following points regarding backward compatibility of the Oracle SQLJ implementation:

- Code generated with an earlier release of the SQLJ translator can continue to run and compile against current run-time libraries. However, this is subject to the cross-compatibility limitations discussed in "Environment Considerations".

- Oracle-specific translator output, that is, code generated with the default `-codegen=oracle` setting, must be created and executed using the `runtime12.jar` library. In addition:

  - Such code will be executable under future Oracle JDBC and SQLJ implementations.

  - Such code, however, will not be executable under earlier releases of Oracle JDBC drivers and Oracle SQLJ run time. In these circumstances, you will have to retranslate the code.

### 2.2 Checking the Installation and Configuration

After you have verified that the preceding assumptions and requirements are satisfied, you must check your SQLJ installation. Note that for Oracle Database 12c Release 2 (12.2), SQLJ and its demo applications are included with this installation. You must:

- Check for Installed Directories and Files

- Set the Path and Classpath

- Verify Installation of the sqljutl Package

#### 2.2.1 Check for Availability of SQLJ and Demo Applications

For Oracle Database 12c Release 2 (12.2), SQLJ and its demo applications are included with the installation.

#### 2.2.2 Check for Installed Directories and Files

Verify that the following directories have been installed and are populated:

##### Directories for JDBC

Refer to the [Oracle Database JDBC Developer’s Guide](../jjdbc/JDBC-getting-started.md)for information about JDBC files that should be installed on your system.

##### Directories for SQLJ

Installing the Oracle Database 12c Release 2 (12.2) Java environment includes, among other things, installing a `sqlj` directory under your `ORACLE_HOME` directory. The `sqlj` directory contains the following subdirectories:

- `demo` (demo applications, including some referenced in this chapter)

- `lib` (`.jar` files containing class files for SQLJ)

Check whether all these directories have been created and populated, especially `lib`.

The `ORACLE_HOME``/bin` directory contains utilities for all Java product areas, including the SQLJ executable files.

#### 2.2.3 Set the Path and Classpath

Ensure that the `PATH` and `CLASSPATH` environment variables have the necessary settings for the Oracle SQLJ implementation. Set the `PATH` and `CLASSPATH` environment variables as follows for the Oracle SQLJ implementation:

- Setting `PATH`

  To run the `sqlj` script, which invokes the SQLJ translator, without having to fully specify its path, verify that the `PATH` environment variable has been updated to include the following:

      ORACLE_HOME/bin

  Use backslash (\\ for Microsoft Windows. Replace `ORACLE_HOME` with your actual Oracle home directory.

- Setting `CLASSPATH`

  Update the `CLASSPATH` environment variable to include the current directory as well as the following:

      ORACLE_HOME/sqlj/lib/translator.jar

  Use backslash (\\ for Microsoft Windows. Replace `ORACLE_HOME` with your actual Oracle home directory.

  Include the following run-time library in the `CLASSPATH`:

      ORACLE_HOME/sqlj/lib/runtime12.jar

  In addition, you must include the following JDBC JAR files in the `CLASSPATH`:

      ORACLE_HOME/jdbc/lib/ojdbc6.jar
      ORACLE_HOME/jdbc/lib/ojdbc7.jar

  **Note:**

  - To translate or run SQLJ programs in JDK 6 environment, you should have `ojdbc6.jar` in the classpath and to translate or run SQLJ programs in JDK 7 environment, you should have `ojdbc7.jar` in the classpath. Ensure that the correct JDBC JAR is picked up at runtime for connecting to Oracle Database.

  - You will not be able to run the SQLJ translator if you do not add a run-time library. You must specify a run-time library as well as the translator library in the `CLASSPATH`.

    To see if SQLJ is installed correctly, and to see the version information for SQLJ, JDBC, and Java, run the following command:

        % sqlj -version-long

  **See Also:**

  "Requirements for Using the Oracle SQLJ Implementation"

#### 2.2.4 Verify Installation of the sqljutl Package

The `sqljutl` package is required for online checking of stored procedures and functions in Oracle Database instance. The package is installed automatically under the `SYS` schema during installation of the server-side Java virtual machine (JVM) for a Java-enabled database. If your database is not Java-enabled, then you will have to manually install this package.

If you want to verify the installation of `sqljutl`, then issue the following SQL command from SQL\*Plus:

    describe sys.sqljutl

This should result in a brief description of the package.

If you get a message indicating that the package cannot be found, or if you want to install an updated version of the package, then you can install it by using SQL\*Plus to run the `sqljutl.sql` script, which is located at:

    ORACLE_HOME/sqlj/lib/sqljutl.sql

### 2.3 Testing the Setup

You can test your database, JDBC, and SQLJ setup using demo applications defined in the following source files:

- `TestInstallCreateTable.java`

- `TestInstallJDBC.java`

- `TestInstallSQLJ.sqlj`

- `TestInstallSQLJChecker.sqlj`

There is also a Java properties file, `connect.properties`, that helps you set up your database connection. You must edit this file to set appropriate user, password, and URL values.

The demo applications discussed here are provided with your SQLJ installation in the `demo` directory:

    ORACLE_HOME/sqlj/demo

You may have to edit some of the source files and translate and compile them, as appropriate. The demo applications provided with the Oracle SQLJ implementation refer to tables on Oracle Database account with user name `HR` and password `hr`. Most Oracle Database installations have this account. You can substitute other values for `HR` and `hr` if desired.

**Note:**

Running the demo applications requires that the `demo` directory be the current directory, and that the current directory ("`.`") should be specified in the `CLASSPATH`.

This section covers the following topics:

- Set Up the Run-Time Connection

- Create a Table to Verify the Database

- Verify the JDBC Driver

- Verify the SQLJ Translator and Run Time

- Verify the SQLJ Translator Connection to the Database

**See Also:**

"Check for Availability of SQLJ and Demo Applications"

#### 2.3.1 Set Up the Run-Time Connection

This section describes how to update the `connect.properties` file to configure your Oracle connection for run time. The file is in the `demo` directory and looks something like the following:

**Note:**

In the Oracle Database 12c Release 2 (12.2) JDBC implementation, database URL connection strings using SIDs are deprecated. Following is an example, where `orcl` is the SID:

    jdbc:oracle:thin:@localhost:5221:orcl

This would now generate a warning, but not a fatal error. Instead, you are encouraged to use database service names, such as `myservice` in the following example:

    jdbc:oracle:thin:@localhost:5221/myservice

    # Users should uncomment one of the following URLs or add their own.
    # (If using Thin, edit as appropriate.)
    #sqlj.url=jdbc:oracle:thin:@localhost:5221/myservice
    #sqlj.url=jdbc:oracle:oci:@
    #
    # User name and password here
    sqlj.user=HR
    sqlj.password=hr

##### Connecting with an Oracle JDBC Driver

Use `oci` in the connection string for Oracle JDBC OCI driver in any new code. For backward compatibility, however, `oci8` is still accepted. Therefore, you do not have to change existing code.

If you are using the JDBC Thin driver, then uncomment the `thin` URL line in `connect.properties` and edit it as appropriate for your Oracle connection. Use the same URL that was specified when your JDBC driver was set up.

#### 2.3.2 Create a Table to Verify the Database

The following tests assume a table called `SALES`. Compile and run `TestInstallCreateTable` as follows:

    % javac TestInstallCreateTable.java
    % java TestInstallCreateTable

This will create the table for you if the database and the JDBC driver are working and the connection is set up properly in the `connect.properties` file.

**Note:**

If you already have a table called `SALES` in your schema and do not want it altered, edit `TestInstallCreateTable.java` to change the table name. Otherwise, your original table will be dropped and replaced.

If you do not want to use `TestInstallCreateTable`, then you can create the `SALES` table using the following SQL statement:

    CREATE TABLE SALES (
          ITEM_NUMBER NUMBER,
          ITEM_NAME CHAR(30),
          SALES_DATE DATE,
          COST NUMBER,
          SALES_REP_NUMBER NUMBER,
          SALES_REP_NAME CHAR(20));

#### 2.3.3 Verify the JDBC Driver

If you want to further test Oracle JDBC driver, then use the `TestInstallJDBC` demo. Verify that your connection is set up properly in `connect.properties`. Then, compile and run `TestInstallJDBC`, as follows:

    % javac TestInstallJDBC.java
    % java TestInstallJDBC

The program should print:

    Hello, JDBC!

#### 2.3.4 Verify the SQLJ Translator and Run Time

Now translate and run the `TestInstallSQLJ` demo, a SQLJ application that has functionality similar to that of `TestInstallJDBC`. Use the following command to translate the source:

    % sqlj TestInstallSQLJ.sqlj

Note that this command also compiles the application.

On a UNIX environment, the `sqlj` script is in `ORACLE_HOME``/bin`, which should already be in the `PATH`. On Windows, use the `sqlj.exe` executable in the `bin` directory. The SQLJ `translator.jar` file has the class files for the SQLJ translator and run time. It is located in `ORACLE_HOME``/sqlj/lib` and should already be in the `CLASSPATH`.

**See Also:**

"Set the Path and Classpath"

Now run the application as follows:

    % java TestInstallSQLJ

The program should print:

    Hello, SQLJ!

#### 2.3.5 Verify the SQLJ Translator Connection to the Database

If the SQLJ translator is able to connect to a database, then it can provide online semantics-checking of your SQL operations during translation. The SQLJ translator is written in Java and uses JDBC to get information it needs from a database connection that you specify. You provide the connection parameters for online semantics-checking using the `sqlj` script command line or using a SQLJ properties file, which is `sqlj.properties` by default.

While still in the `demo` directory, edit the `sqlj.properties` file and update, comment, or uncomment the `sqlj.password`, `sqlj.url`, and `sqlj.driver` lines, as appropriate, to reflect your database connection information. For assistance, refer to the comments in the `sqlj.properties` file.

Following is an example of what the appropriate driver, URL, and password settings might be if you are using Oracle JDBC OCI driver.

    sqlj.url=jdbc:oracle:oci:@
    sqlj.driver=oracle.jdbc.OracleDriver
    sqlj.password=hr

Online semantics-checking is enabled as soon as you specify a user name for the translation-time connection. You can specify the user name either by uncommenting the `sqlj.user` line in the `sqlj.properties` file or by using the `-user` command-line option. The `user`, `password`, `url`, and `driver` options all can be set either on the command line or in the properties file.

**See Also:**

"[Connection Options](translator-command-line-and-options.md)"

You can test online semantics-checking by translating the `TestInstallSQLJChecker.sqlj` file located in the `demo` directory, as follows (or using another user name, if appropriate):

    % sqlj -user=HR TestInstallSQLJChecker.sqlj

This should produce the following error message if you are using one of Oracle JDBC drivers:

    TestInstallSQLJChecker.sqlj:41: Warning: Unable to check SQL query. Error returned by database is: ORA-00904:
    invalid column name

Edit `TestInstallSQLJChecker.sqlj` to fix the error on line 41. The column name should be `ITEM_NAME` instead of `ITEM_NAMAE`. Once you make this change, you can translate and run the application without error using the following commands:

    % sqlj -user=HR TestInstallSQLJChecker.sqlj
    % java  TestInstallSQLJChecker

If everything works, then the following line is displayed:

    Hello, SQLJ Checker!
