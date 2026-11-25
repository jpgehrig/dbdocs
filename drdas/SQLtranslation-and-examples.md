SQL Translation is a new feature in Oracle Database 12c Release 2 (12.2). Oracle Provider for DRDA may be used without SQL Translation with earlier releases of Oracle Database.

For more information on SQL Translation, see [Oracle® Database Migration Guide](../drdaa/intro-to-tools-and-products-supporting-migraiton.md).

**Note:**

SQL Translation is an optional feature and recommended in cases where SQL used within the application is more DB2–centric syntax.

### 4.1 Overview of SQL Translation Process

Oracle Database Release 12c introduces the concept of SQL Translation. This feature enables the translation of 'foreign' SQL statements, such as DB2, into a SQL syntax that may be correctly used by Oracle Database. SQL Translation itself is implemented through a SQL Translator that is most often supplied by a third party to the translation. The SQL Translator inspects the input SQL, and sometimes alters it to adhere to Oracle SQL syntax. A SQL Translation Profile, which is specified through a SQL Translator Interface Package, specifies a SQL Translator that is used.

A SQL Translation Profile is a schema-level object of type `SQL TRANSLATION PROFILE`. It references a PL/SQL package through its `ATTR_TRANSLATOR` attribute; this package is known as the SQL Translator Interface Package. The package specifies the third-party SQL translator that performs the SQL translation when the SQL Translation Profile is active. Only one SQL Translation Profile may be enabled at a time.

SQL Translation Profiles may be shared among users. Commonly, all users share the same single SQL Translation Profile for a set of packages, but that is not necessary.

Note that each DB2 package may be associated with a SQL Translation profile through the attributes kept for that package. The SQL Translator associated with the SQL Translation Profile specified for the DB2 package is used when preparing SQL statements within that DB2 package.

#### 4.1.1 Implementing SQL Translation

In order for translation to proceed, the following sequence of events must take place:

1.  Acquisition of a SQL Translator.
2.  Creation of a SQL Interface Package that references that translator.
3.  Creation of a SQL Translation Profile that references the SQL Interface Package.
    This step may be done only once in the life of an instance. However, it must be performed at least once to use SQL Translation.

    In situations with multiple translators, or where different SQL Translation Profiles are necessary, this process may be repeated.
4.  Association of DB2 packages with a SQL Translation profile.
    This step must be completed for each package created.

    Note that a package does not have to be created before it is associated with the translation profile; only the name of the package is necessary. This step does not validate that a particular package already exists.
5.  At execution time, the user passes SQL text to Oracle Database Provider for DRDA through the package.
6.  When Oracle Database Provider for DRDA acquires SQL text, it checks if the package is associated with a SQL Translation Profile, and then sets that SQL Translation Profile to be in effect during the time when SQL text is parsed and executed.
7.  After Oracle Database Provider for DRDA prepares SQL text for execution, Oracle Database uses the current SQL Translation Profile to translate the SQL statements, and then executes them.

#### 4.1.2 Requirements for SQL Translation

Successful SQL translation may occur only in the following are true:

- A SQL Translation Profile must be enabled for the session, through the following command:

      ALTER SESSION SET SQL_TRANSLATION_PROFILE

- The process must specify that incoming SQL statements are in a foreign syntax, or in a non-Oracle SQL dialect. In all cases discussed here, these dialect are variants of DB2 SQL.

For Oracle Database Provider for DRDA product, the preceding two conditions are coupled; if a DB2 package is associated with a SQL Translation Profile, then the SQL statements are expected to be in a foreign syntax, and the SQL Translator associated with the SQL Translation Profile is called to translate any SQL in that package.

### 4.2 Specifics of Translating DB2-Specific SQL Syntax

While most of the SQL constructs that a client application submits to Oracle Database Provider for DRDA may be executed directly, some DB2 SQL constructs are not recognized by Oracle. Consider the known issues that occur when translating DB2 SQL statements issued by an application that is re-configured to use an Oracle Database instance.

If a SQL Translation Profile is in place, the SQL Translator associated with the profile may be designed to alter these SQL statements so that the application performs equivalent or similar operations in Oracle SQL, and returns the expected results.

#### 4.2.1 DB2 Special Registers

Oracle Database does not support the `CURRENT TIME` special register construct, to get the current time of day. Calls to this construct, as in the following example, results in an `ORA-00936` error.

    SELECT CURRENT TIME FROM SYSIBM.SYSDUMMY1

#### 4.2.2 DB2 SQL Functions and Procedures

Oracle does not support some functions that are defined in DB2. For example, the `CEILING` function does not exist in Oracle; instead, Oracle SQL syntax includes a compatible `CEIL` function.

#### 4.2.3 DB2 Named Datatypes

Some elementary SQL datatypes, such as `BIGINT`, are not defined in Oracle. When the application runs against Oracle, casting a column value or constant as a `BIGINT` produces an error. The following example results in an `ORA-00902` error because `BIGINT` is not recognized as a valid Oracle datatype.

    SELECT CAST(12345678912 AS BIGINT) from SYSIBM.SYSDUMMY1

#### 4.2.4 DB2 Syntactic Statements

An `INSERT` statement in DB2 may contain syntactic clauses that are Oracle does not interpret. An example of such is the isolation clause, shown in the following code example.

    INSERT INTO SCOTT.DEPT VALUES(50, "FARMING", "SPRINGFIELD") WITH CHG

### 4.3 SQL Translator Interface Package

A SQL Translation Profile is a schema-level object of type `SQL TRANSLATION PROFILE` created through the `DBMS_SQL_TRANSLATOR.CREATE_PROFILE() `procedure. The SQL Translator Interface Package is a PL/SQL package of a certain format; it references the third-party-supplied translator objects and is, itself, referenced by the SQL Translation Profile. So the SQL Translator Interface Package connects the SQL Translation Profile and the third-party supplied SQL translator objects.

#### 4.3.1 About SQL Translator Interface Package

A SQL Translation Profile references a PL/SQL wrapper package that has a fixed format, the SQL Translator Interface Package. When a session sets a `SQL TRANSLATION PROFILE`, it specifies that all SQL is translated by the third-party SQL translator associated with the SQL Translator Interface Package. The procedure `translate_sql()` of the SQL Translator Interface Package performs the translation.

Note that Oracle does not provide a SQL Translator. Instead, a SQL Translator must be obtained from third-party vendors, or developed internally. Oracle provides various administrative scripts for creating and managing a SQL Translation Profile.

#### 4.3.2 Creating a SQL Translator Interface Package

Example 4-1 shows a simple SQL Translation Interface Package used with a SQL Translation Profile. The language and name specifications are relative to the language-type and callable-names in the third-party SQL translator. After logging into the Oracle Database with `SYSDBA` privileges, the following package declaration must be made. The package name is the value of the `TRANSLATOR_ATTR` attribute of the SQL Translation Profile.

Example 4-1 Creating a SQL Translator Interface Package

    create or replace package SYSIBM.DBTooSQLTranslator as
      procedure translate_sql(
        sql_text in CLOB,
       translated_text out CLOB);
      procedure translate_error(
        error_code in BINARY_INTEGER,
        translated_code out BINARY_INTEGER,
        translated_sqlstate out VARCHAR2);
    end;
    /
    create or replace package body SYSIBM.DBTooSQLTranslator as
      procedure translate_sql(
        sql_text in CLOB,
        translated_text out CLOB )
        as language JAVA
      name /* actually the "signature" of the third-party callable */
      /* procedure associated with translate_sql    */
       'DBTooSQLApiInterface.translateSQL(oracle.sql.CLOB, oracle.sql.CLOB[])';

       procedure translate_error(error_code in BINARY_INTEGER,
        translated_code out BINARY_INTEGER,
        translated_sqlstate out VARCHAR2) as
      language JAVA
      name /* actually the "signature" of the third-party callable */
      /* procedure associated with translate_error  */
     'DBTooSQLApiInterface.translateError(oracle.sql.CLOB, oracle.sql.CLOB[])';
     end;
     /

#### 4.3.3 Granting EXECUTE Access to SQL Translator Interface Package

Because the SQL Translator Interface Package is called at run-time, it must have `EXECUTE` access enabled. Example 4-2 shows how to grant this access.

Example 4-2 Granting EXECUTE access to SQL Translator Interface Package

    GRANT EXECUTE ON SYSIBM.DBTooSQLTranslator TO DRDAAS_USER_ROLE

#### 4.3.4 Creating a SQL Translation Profile

The SQL Translation Profile may be created and administered by any user who has the `CREATE SQL TRANSLATION PROFILE` authority and `TRANSLATE ANY SQL` authority. The section on Granting Required Authority to Users with `DRDAAS_TRANS_ADMIN` Role shows how to grant these two privileges to `DRDAAS_TRANS_ADMIN`. These privileges may be granted by a user with existing `SYSDBA` privileges.

The `ADMIN OPTION` clause enables `DRDAAS_TRANS_ADMIN` to `GRANT` the `TRANSLATE ANY SQL` authority to other Oracle users. In this manner, the `DRDAAS_TRANS_ADMIN` may allow many users with `DRDAAS_USER_ROLE` to use the translation facility, as demonstrated in the section Granting Translation Authority to Users with `DRDAAS_USER_ROLE`.

The actual SQL Translation Profile may be managed through a script provided in Creating and Managing the SQL Translation Profile. Note that the administering id must already have the required authority to perform `CREATE SQL TRANSLATION PROFILE`.

**Related Topics**

- Granting Translation Authority Through Administrator Role
- Granting Translation Authority Through User Role
- Creating and Managing SQL Translation Profile

##### 4.3.4.1 Granting Translation Authority Through Administrator Role

Example 4-3 Granting Required Authority to Users with DRDAAS_TRANS_ADMIN Role

    GRANT CREATE SQL TRANSLATION PROFILE TO DRDAAS_TRANS_ADMIN;
    GRANT TRANSLATE ANY SQL TO DRDAAS_TRANS_ADMIN WITH ADMIN OPTION;

##### 4.3.4.2 Granting Translation Authority Through User Role

Example 4-4 Granting Translation Authority to Users with DRDAAS_USER_ROLE

    GRANT TRANSLATE ANY SQL TO DRDAAS_USER_ROLE;

##### 4.3.4.3 Creating and Managing SQL Translation Profile

Example 4-5 Creating and Managing the SQL Translation Profile

    declare
      PROFILE_DOES_NOT_EXIST exception;
      pragma EXCEPTION_INIT(PROFILE_DOES_NOT_EXIST, -24252);
      /* profile_name is the nsme of the SQL Translation Profile */
      /* created here.  */
      profile_name VARCHAR2(32) := 'DRDAAS_TRANS_ADMIN.MY_PROFILE';

      /* SYSIBM is the schema in which the SQL Translator Interface */
      /* package (viz., SYSIBM.DBTooSQLTranslator) is found.   */
      sql_trnsltr_intfc_schema VARCHAR2(32) := 'SYSIBM';

      /* DBTooTranslator is the unqualified package name of the SQL */
      /* Translator Interface Package */
      sql_trnsltr_intfc_pkgnm VARCHAR2(32) := 'DBTooSQLTranslator';

      sql_trnsltr_intfc_pkg VARCHAR2(128);
      grant_cmd VARCHAR2(256);
      cursor_id NUMBER;

    begin
      sql_trnsltr_intfc_pkg := sql_trnsltr_intfc_schema || '.'  ||
        sql_trnsltr_intfc_pkgnm;
      begin
        DBMS_SQL_TRANSLATOR.DROP_PROFILE(profile_name);
        exception
          WHEN PROFILE_DOES_NOT_EXIST THEN NULL; /* ignore if non-existant */
      end;
      /* Create SQL Translation Profile */
      DBMS_SQL_TRANSLATOR.CREATE_PROFILE(profile_name);
      /* Associate the SQL Translator Interface Package denoted by */
      /* sql_trnsltr_intfc_pkg with this profile    */
      DBMS_SQL_TRANSLATOR.SET_ATTRIBUTE(profile_name,
        DBMS_SQL_TRANSLATOR.ATTR_TRANSLATOR,
        sql_trnsltr_intfc_pkg);
      /* Mark this SQL Translation Profile as "registered" */
      DBMS_SQL_TRANSLATOR.SET_ATTRIBUTE(profile_name,
        DBMS_SQL_TRANSLATOR.ATTR_TRANSLATION_REGISTRATION,
        DBMS_SQL_TRANSLATOR.ATTR_VALUE_TRUE);
      /* The owner of the SQL Translator Interface Package must have */
      /* full authority for the SQL TRANSLATION PROFILE    */
      grant_cmd := 'GRANT ALL ON SQL TRANSLATION PROFILE ' ||
        profile_name || ' TO ' || sql_trnsltr_intfc_schema;
      cursor_id := DBMS_SQL.OPEN_CURSOR();
      DBMS_SQL.PARSE(cursor_id, grant_cmd, DBMS_SQL.NATIVE);
      DBMS_SQL.CLOSE_CURSOR(cursor_id);
      /* Let all with DRDAAS_USER_ROLE have access to the SQL Translation profile.  */
      grant_cmd := 'GRANT USE ON SQL TRANSLATION PROFILE ' ||
        profile_name || ' TO DRDAAS_USER_ROLE';
      cursor_id := DBMS_SQL.OPEN_CURSOR();
      DBMS_SQL.PARSE(cursor_id, grant_cmd, DBMS_SQL.NATIVE);
      DBMS_SQL.CLOSE_CURSOR(cursor_id);
    end;
    /

### 4.4 Using Third-Party SQL Translators

To use a third-party translator, its files and objects must be installed in the directory `$``ORACLE_HOME``/rdbms/drdaas/jlib`.

In case of difficulties, use `DBMS_JAVA.SET_OUTPUT()` procedure to redirect server-side error messages to `DBMS_OUTPUT`.

For more information on using Java in Oracle, refer Oracle® Database Java Developer's Guide.

#### 4.4.1 Using a Third-Party SQL Translator, Loaded as a Single Object

If the third-party SQL translator is in Java, Example 4-6 may be run in SQL\*Plus environment by a `SYSDBA` user. Example 4-6 uses `DBMS_JAVA.LOADJAVA()` procedure to load the objects into the `SYSIBM` schema; it loads a single third-party object, `DBTooSQLAPI.jar`.

Example 4-6 Loading a Third-Party SQL Translator; Single Object

    begin
      DBMS_JAVA.LOADJAVA('-definer -genmissing -schema SYSIBM ' || '
      ' rdbms/drdaas/jlib/DBTooSQLAPI.jar',
      '((* SYSIBM)(* PUBLIC)(* -))');
    end;
    /

#### 4.4.2 Using a Third-Party SQL Translator, Loaded as Multiple Objects

If the third-party translator consists of multiple objects, each component must be specified in the `LOADJAVA` call. Example 4-7 specifies two translator objects, `DBTooSQLAPI.jar` and `DBTooMainClass.class`.

Example 4-7 Loading a Third-Party SQL Translator; Multiple Objects

    begin
      DBMS_JAVA.LOADJAVA('-definer -genmissing -schema SYSIBM ' ||
      ' rdbms/drdaas/jlib/DBTooMainClass.class' ||
      ' rdbms/drdaas/jlib/DBTooSQLAPI.jar',
      '((* SYSIBM)(* PUBLIC)(* -))');
    end;
    /

### 4.5 Using a Translator Management Script

Oracle Database ships a `drdasqtt_translator_setup.sql` script, which manages translation profiles. The script must be invoked in SQL\*Plus by a user with `SYSDBA` privileges. It asks for the following inputs:

1.  SQL Translator Interface Package Schema, such as `SYSIBM`.
2.  SQL Translator Interface Package Name, such as `DBTooTranslator`.
3.  SQL Translation Profile Schema, such as `DRDAAS_TRANS_ADMIN`.
4.  SQL Translation Profile Name, such as `MY_PROFILE`.
5.  Language type of the third-party translator, such as Java.
6.  The names of files or objects supplied by the third-party vendor. If more than one is supplied, enclose the list in four (4) single quotes and separate the items by blank spaces, as in the following code:
        ''''rdbms/drdaas/jlib/DBTooMainClass.class rdbms/drdaas/jlib/DBTooSQLAPI.jar''''
7.  The signature (entry name plus argument descriptions) of the entry in the files or objects supplied by the third-party vendor that are used for translating SQL. For Java-based third-party code, the signature may be obtained through the` javap` program. Note that signatures that contain blank space must be enclosed within double quotes.
8.  The signature (entry name plus argument descriptions) for the entry in the files or objects supplied by the third-party vendor that are used for translating error codes. For Java-based third-party code, the signature may be obtained through the` javap` program. Note that signatures that contain blank space must be enclosed within double quotes.

### 4.6 Verifying the SQL Translator Profile

The following steps verify that the SQL Translation Profile is correctly installed and fully enabled.

#### To verify the SQL Translator Profile configuration:

1.  Log into Oracle Database with SYSDBA privileges
2.  Check that the translator profile is loaded into Oracle Database.
        SELECT * FROM ALL_SQL_TRANSLATION_PROFILES;
3.  Log in with an id that has `DRDAAS_USER_ROLE` privileges.
4.  Ensure that the role is set:
        SET ROLE DRDAAS_USER_ROLE;
5.  Set the SQL Translation Profile for of session to the value specified at the time the SQL Translation Profile was created.
        ALTER SESSION SET SQL_TRANSLATION_PROFILE = DRDAAS_TRANS_ADMIN.MY_PROFILE;
6.  Attempt the following commands:
        ALTER SESSION SET EVENTS = '10601 trace name context forever, level 32';
        SELECT CAST(1234567 AS BIGINT) FROM DUAL;
        ALTER SESSION SET EVENTS = '10601 trace name context off';
        SELECT CAST(1234567 AS BIGINT) FROM DUAL;

    The first `SELECT` should succeed, while the second should fail. The `ALTER SESSION SET EVENTS` commands specify that the following SQL is one of:

    - foreign syntax (trace name context forever, level 32)

    - native Oracle syntax (trace name context off)

    This works only when using SQL\*Plus.

### 4.7 Altering the SQL Translation Profile

At times, it becomes necessary to completely change the SQL Translation Profile, and make the `SQL TRANSLATION PROFILE` attribute of a DB2 package reference a new SQL Translation Profile.

DB2 packages usually come in sets, and the names of the DB2 packages are determined by the client. However, if the client uses ODBC to access Oracle Database Provider for DRDA, the ODBC driver determines the names of the packages.

Oracle supplies two scripts that may be used to set the SQL Translation Profile attribute for a set of packages.

- If the DataDirect ODBC driver accesses Oracle Database Provider for DRDA, use the `drdasqt_set_profile_dd.sql` script, in the `drdaas/admin` directory.

- If the IBM ODBC driver accesses Oracle Database Provider for DRDA, use the `drdasqt_set_profile_ibm.sql` script, in the `drdaas/admin` directory. Native client application may also use this script, but it may have to be extended.

These scripts may be copied and altered for use with other sets of DB2 packages.

Additionally, each of these scripts must be run in SQL\*Plus by a user with `DRDAAS_ADMIN_ROLE` privileges. The script prompts for the qualified name of the profile that is referenced by the various packages (such as `DRDAAS_TRANS_ADMIN.MY_PROFILE`). It also prompts for the default Package Collection schema, which is usually `NULLID`.
