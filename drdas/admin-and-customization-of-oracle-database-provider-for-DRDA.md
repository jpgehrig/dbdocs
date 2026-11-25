Consider various administration and customization issues.

### 5.1 Migration Steps using Oracle Database Provider for DRDA

While migration of existing DB2 applications to Oracle Database is data- and target-specific, the general methodology has the following six steps:

1.  Installing and configuring Oracle Database Provider for DRDA software

2.  Installing Oracle Database Provider for DRDA objects in the Oracle Database

3.  Administering DRDA Package authority

4.  Migrating DB2 data

5.  Re-targeting the application

6.  Tuning SQL Translation and Datatypes

### 5.2 Considerations for Using Oracle Database Provider for DRDA

Before installing Oracle Database Provider for DRDA software, an organization must consider several operational and resource issues. Flexibility and performance of machine and network resources is paramount when determining whether an optimal installation is as a standalone Oracle home, an Oracle home within an existing Oracle Database, or on a machine that is entirely separate from the Oracle Database. Additionally, the nature of all possible DB2 clients that must use the installation is a determining factor; in this context, DB2 is considered a client.

**Related Topics**

- [Installing Oracle Database Provider for DRDA](install-and-configure-oracle-database-provider-for-DRDA.md)

### 5.3 Prerequisites to Installing Oracle Database Provider for DRDA

Before installing Oracle Database Provider for DRDA objects in the Oracle Database, one or more users must be designated as DRDA Administrators, and have the Administrator role.

Similarly, designate users who will be accessing the Oracle Database through Oracle Database Provider for DRDA or DB2 applications, and grant to them roles and privileges of DRDA User. Some aspects of setting the DRDA User's authority and configuration may need to be delayed until further in the migration process. This mostly concerns specific DRDA packages used by the application, and any specific SQL translations or datatype tuning. If the application's packages are identified before migration, these may be applied as part of the package authorization workflow.

**Related Topics**

- [Administrator Role](install-and-configure-oracle-database-provider-for-DRDA.md)
- [User Role](install-and-configure-oracle-database-provider-for-DRDA.md)

### 5.4 Administering DRDA Package Authority

In order to successfully access Oracle Database from DRDA or DB2 applications through Oracle Database Provider for DRDA, package authorization must be in place. At a minimum, the following information must be collected about the application and its users:

- package collection ID, such as `NULLID`

- package name, such as `DSNPBD3`

- package version name, if applicable, such as `01` or `NULL`

- name of the Oracle user who must access the database, such as `DRDAUSR`

A SQL Translation Profile Name must also be designated for the application represented by the package.

**Related Topics**

- [SQL Translator Interface Package](SQLtranslation-and-examples.md)
- [Packages](architecture-of-oracle-database-provider-for-DRDA.md)

### 5.5 Migrating DB2 Data

In DB2, objects may be created under an arbitrary schema, whereas schema names are not arbitrary in Oracle Database. Therefore, careful use of schemas must be considered when migrating data from DB2 to Oracle. In Oracle, all schema objects, such as tables, views, synonyms, and so on, must be allocated in a schema of an actual user. This obviously effects how these objects are named, created, and accessed.

Consider the following example: `USER1` creates tables `"USER1"."TABLE1"` and `"USER2"."TABLE2"`. In DB2, `TABLE1` and `TABLE2` are owned by `USER1`, because `USER1` is their creator. In Oracle, the table `"USER2"."TABLE2"` is owned by user `USER2`. Additionally, `USER1` could not have created `TABLE2` unless `USER1` has `CREATE ANY TABLE` privelege. Instead, `USER2` must create `TABLE2`, and then grant `USER1` access to it.

Data migrated from DB2 to Oracle must be defined also in terms of Oracle datatypes. While Oracle uses ANSI-defined datatype names, they do not necessarily have the same range limits or semantics as the DB2 implementation. To accurately model existing DB2 application datatypes, review the section Data Dictionary for Oracle Database Provider for DRDA.

After creating the schema and objects with appropriate datatypes, the data may be imported into Oracle.

**Related Topics**

- [Data Dictionary Emulation in Oracle Database Provider for DRDA](data-dictionary.md)

### 5.6 Retargeting the Application to Use Oracle Database

The following example shows how to migrate DB2 z/OS applications. You would need to follow similar steps when migrating DB2/LUW or DB2/400 applications. Refer to IBM documentation for details of each product's equivalent steps.

**Note:**

This example is applicable only for DB2 for z/OS.

There are two general categories of applications: native applications and remote applications.

#### 5.6.1 Re-targeting Native Applications

Typical DB2 applications are called native because they interact with a local DB2 system directly, through an internal IPC mechanism. These applications use embedded SQL programming, and utilize the DB2 SQL PreProcessor. Pre-processing the source generates an execution plan that is stored in a Database Resource Module (DBRM). Users must upload, or bind the execution plan to the local DB2 instance before the program runs.

The execution plan contains all the static SQL embedded in the application source, as well as additional attributes such as location, also called the Current Server. By default, Current Server is blank; this indicates that the server is on the local DB2 instance. It is possible, however, to re-target the execution plan to run all operations on another server by setting a new value for the Current Server attribute.

The following steps should be performed by an IBM DB administrator.

1.  Create location entries in the DB2 Communications Database.
    DB2 has a internal communications system for connecting to remote DB2 instances. To address a remote instance, insert records into the `SYSIBM.IPNAMES` table, the `SYSIBM.LOCATIONS` table and, optionally, into the `SYSIBM.USERNAMES` table.

    See IBM DB2 documentation for a description of the DB2 Communications Database facility.

    The following command inserts a linkname `REMHOST`, a location entry `DRDAAS`, and an optional username mapping entry in the DB2 Communications Database. The linkname specifies the hostname or IP address of the computer that is running Oracle Database Provider for DRDA. The location specifies an RDB name that uses the linkname and the port number that Oracle Database Provider for DRDA is listening on. These correspond to Oracle Database Provider for DRDA configuration parameters `DATA_PORT` and `RDB_MAP`. Note that the location name must match exactly to the `RDB()` value specified in the `RDB_MAP` parameter.

        INSERT INTO SYSIBM.IPNAMES (LINKNAME,SECURITY_OUT,USERNAMES,IPADDR)
          VALUES ('REMHOST','P','O','remotehost.remotedomain.com');

        INSERT INTO SYSIBM.LOCATIONS (LOCATION,LINKNAME,PORT)
          VALUES ('DRDAAS','REHMOST','1446');

        INSERT INTO SYSIBM.USERNAMES (TYPE,AUTHID,LINKNAME,NEWAUTHID,PASSWORD)
          VALUES ('O',' ','REMHOST','DRDAUSER', 'userpwd' );
2.  Remotely bind the application Plan to Oracle Database Provider for DRDA.
    After the location entries are inserted, you must remotely bind the application execution plan. The following code binds plan `DSNPBD3` through the DSN command processor `IKJEFT01`. Note that location `DRDAAS` prefixes the collection Id.

        BIND PACKAGE(DRDAAS.NULLID) MEMBER(DSNPBD3) -
                    ACT(REP) ISO(CS) CURRENTDATA(YES) ENCODING(EBCDIC)
3.  Locally bind the package with current server.
    After the plan is bound remotely, re-bind the local plan using the current server option to re-target execution. The following code binds plan `DSNPBD3` through the DSN command processor `IKJEFT01`.

    Note that the plan must be referred to in the remote plan through the package list, `PKLIST`, and must specify both the location in the package reference, `DRDAAS.NULLID.DSNPBD3`, and specify the `CURRENTSERVER` option that contains the location.

        BIND PLAN(DSNPBD3) -
           PKLIST(DRDAAS.NULLID.DSNPBD3) -
           ACT(REP) ISO(CS) CURRENTDATA(YES) ENCODING(EBCDIC) -
           CURRENTSERVER(DRDAAS)
4.  After the plan is bound remotely and re-bound locally, the application runs using plan `DSNPBD3`, implicitly makes a remote connection through the local DB2 to Oracle Database Provider for DRDA, and executes all operations of the plan remotely. The local DB2 remains a pass through coordinator in this configuration.

#### 5.6.2 Re-targeting Remote Applications

Remote applications are typically not directly tied to the Local DB2. Such applications typically are referred to as being network-aware or network-oriented and have a remote server location configuration attribute that is used to specify what and where to connect to.

Such applications utilize Oracle Database Provider for DRDA through the network protocol. Re-targeting of this type of application is simple to configure, as the following steps show.

1.  Change the configuration options of the Application to use the hostname (or IP address), port number and RDB name of that configured in Oracle Database Provider for DRDA. An example of this is through ODBC, in which the DSN entry contains network parameters.
    In this example, the `Network` and `PortNumber` parameters correspond to the `Linkname` and `Location` entries inserted into the DB2 Communication Database example used earlier. The `Database` parameter corresponds to the `Location` name. All of which, again, correspond to the `DATA_PORT` and `RDB_MAP` parameters of the configured Oracle Database Provider for DRDA.

    Here is an example of an `odbc.ini` file.

        [DRDAAS]
               Network=remotehost.remotedomain.com
               PortNumber=1446
               Database=DRDAAS
2.  Execute the package resource binding operation for the application.
    Often this is handled implicitly by the application itself, or is documented as a one-time step to setting up the applications access and resource to a remote DB2 instance. Refer to the documentation for the specific application for Binding instructions.

### 5.7 Translating SQL Statement and Typing Datatypes

Some applications may have DB2-specific SQL that is beyond the automatic translation mechanism of SQL translation, or may be expecting a very specific datatype for a particular column in a query. In such cases it may be necessary to manually insert SQL substitution statements, or add item-specific datatype manipulations.

For example, suppose an application has a specific SQL statement that has the following DB2-specific syntax: `SELECT LOG2(COL1) FROM TABLE1`. To work correctly in Oracle, the SQL needs to be translated into this statement: `SELECT LOG10(COL1,2) FROM TABLE1`.

Through SQL Translation's Register facility, a direct translation may be registered for this SQL statement, as shown in the section Registering a SQL Substitution Statement. Note that this must be done by the user who is executing the SQL statement; remember that the SQL Translation Profile must created as a resource for that user.

After the SQL translator is registered, when the application issues the original SQL it is implicitly translated to the new SQL and processes.

In some very specific cases, application clients require the datatypes of select items in a query to be returned in a very specific format.

Let's say that the result of the translated query `SELECT LOG10(COL1,2) FROM TABLE1` returns a `DECFLOAT34` datatype, but the application is unable to process it, it is possible to implicitly coerce the datatype to another, compatible type.

If the application supports the `DOUBLE PRECISION` datatype, it is possible to use the `TYPEMAP` facility to add this specific coercion described in Registering an On-Demand Datatype Conversion.

#### 5.7.1 Registering a SQL Substitution Statement

Example 5-1 Registering a SQL Substitution Statement

The application's package has been assigned the Profile name `DB2ZOS`.

    connect DRDAUSER/userpwd
    execute dbms_sql_translator.register_sql_translation('DB2ZOS',
       'SELECT LOG2(COL1) FROM TABLE1',
       'SELECT LOG10(COL1,2) FROM TABLE1')

#### 5.7.2 Registering an On-Demand Datatype Conversion

Example 5-2 Registering an On-demand Datatype Conversion

    connect DRDAADM/adminpwd

    execute DBMS_DRDAAS_ADMIN.SET_TYPEMAP('NULLID', 'DSNPBD3', NULL,
       'TABLE1:LOG10(COL1,2)', 'NUMBER=DOUBLE')

    execute DBMS_DRDAAS_ADMIN.SET_TYPEMAP('NULLID', 'DSNPBD3', NULL,
       'TABLE1:LOG10(COL1,2)', 'NUMBER(0,-127)=DOUBLE')
