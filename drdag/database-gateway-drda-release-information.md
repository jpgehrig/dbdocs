The following sections describe release information specific to the Oracle Database Gateway for DRDA.

- Product Set

- Changes and Enhancements

- Product Migration

- Known Problems

- Known Restrictions

### Product Set

The following product components are included in the product installation media:

- Oracle Database Gateway for DRDA, 12c Release 2 (12.2)

- Oracle Net, 12c Release 2 (12.2)

### Changes and Enhancements

The following sections describe the changes and enhancements unique to this release of the gateway:

- Remote Insert Rowsource

- Gateway Password Encryption Tool

- [Result Sets and Stored Procedures](developing-applications.md)

#### Remote Insert Rowsource

A remote insert rowsource feature allows remote insert requiring local Oracle data to work through the Oracle database and Oracle Database Gateway. This functionality requires that the Oracle database and the Oracle Database Gateway to be version 12.2 or later.

By Oracle Database design, some distributed statement must be executed at the database link site. But in certain circumstances, there is data needed to execute these queries that must be fetched from the originating Oracle Database. Under homogeneous connections, the remote Oracle database would call back the source Oracle database for such data. But in heterogeneous connections, this is not viable, because this means that the Foreign Data Store would have to query call back functions, or data, that can only be provided by the Oracle instance that issued the query. In general, these kinds of statements are not something that can be supported through the Oracle Database Gateway.

The following categories of SQL statements results in a callback:

- Any DML with a sub-select, which refers to a table in Oracle database.

- Any `DELETE`, `INSERT`, `UPDATE` or "`SELECT... FOR UPDATE..."` SQL statement containing SQL functions or statements that needs to be executed at the originating Oracle database.

  These SQL functions include `USER`, `USERENV`, and `SYSDATE`; and involve the selection of data from the originating Oracle database.

- Any SQL statement that involves a table in Oracle database, and a `LONG` or `LOB` column in a remote table.

An example of a remote `INSERT` statement that can work through the remote insert rowsource feature is as follows:

    INSERT INTO gateway_table@gateway_link select * from local_table;

#### Gateway Password Encryption Tool

The Gateway Password Encryption tool (`g4drpwd`) has been replaced by a generic feature that is now part of Heterogeneous Services. Refer to Chapter 15, "Security Considerations" in [Oracle Database Gateway Installation and Configuration Guide for IBM AIX on POWER Systems (64-Bit), Linux x86-64, Oracle Solaris on SPARC (64-Bit), Oracle Solaris on x86-64 (64-Bit) and HP-UX Itanium](../otgis/drda-gateway-security-consideration.md) or [Oracle Database Gateway Installation and Configuration Guide for Microsoft Windows](../otgiw/security-consideration-drda-gateway.md) for details.

#### Result Sets and Stored Procedures

The Oracle Database Gateway for DRDA provides support for stored procedures that return result sets. By default, all stored procedures and functions do not return a result set to the user. To enable result sets, set the `HS_FDS_RESULTSET_SUPPORT` parameter in the initialization parameter file.

**See Also:**

[Initialization Parameters](database-gateway-drda-initialization-parameters.md) for information about editing the initialization parameter file and the `HS_FDS_RESULTSET_SUPPORT` parameter. For further information about Oracle support for result sets in non-Oracle databases see [Oracle Database Heterogeneous Connectivity User's Guide](../heter/using-heterogeneous-services-agents.md).

**Note:**

If you set the `HS_FDS_RESULTSET_SUPPORT` gateway initialization parameter, you must change the syntax of the procedure execute statement for all existing stored procedures or errors will occur.

When accessing stored procedures with result sets through the Oracle Database Gateway for DRDA, you will be in the sequential mode of Heterogeneous Services. The gateway returns the following information to Heterogeneous Services during procedure description:

- All the input arguments of the remote stored procedure

- None of the output arguments

- One out argument of type ref cursor (corresponding to the first result set returned by the stored procedure)

Client programs have to use the virtual package function `DBMS_HS_RESULT_SET.GET_NEXT_RESULT_SET` to get the ref cursor for subsequent result sets. The last result set returned is the out argument from the procedure.

The limitations of accessing result sets are as follows:

- Result sets returned by a remote stored procedure have to be retrieved in the order in which they were placed on the wire.

- On execution of a stored procedure, all result sets returned by a previously executed stored procedure will be closed, regardless of whether the data has been completely retrieved or not.

In the following example, the UDB stored procedure is executed to fetch the contents of the `EMP` and `DEPT` tables from UDB:

    CREATE PROCEDURE REFCURPROC (IN STRIN VARCHAR(255), OUT STROUT VARCHAR(255) )
      RESULT SETS 3  LANGUAGE SQL
    BEGIN
      DECLARE TEMP CHAR (20);
     DECLARE C1 CURSOR WITH RETURN TO CALLER FOR
          SELECT * FROM TKHOEMP;
      DECLARE C2 CURSOR WITH RETURN TO CALLER FOR
         SELECT * FROM TKHODEPT;
     OPEN C1;
     OPEN C2;
     SET STROUT = STRIN;
     END

### Product Migration

Refer to [Oracle Database Gateway Installation and Configuration Guide for IBM AIX on POWER Systems (64-Bit), Linux x86-64, Oracle Solaris on SPARC (64-Bit), Oracle Solaris on x86-64 (64-Bit) and HP-UX Itanium](../otgis/drda-gateway-migration.md) or [Oracle Database Gateway Installation and Configuration Guide for Microsoft Windows](../otgiw/drda-gateway-migration.md) for information on migrating product configurations from previous releases for additional changes or requirements.

### Known Problems

The problems that are documented in the following section are specific to the Oracle Database Gateway for DRDA, and are known to exist in this release of the product. If you have any questions or concerns about these problems, contact Oracle Support Services.

A current list of problems is available online. Contact your local Oracle office for information about accessing this online information.

### Known Restrictions

The following restrictions are known to exist for the products in the 12c Release 2 (12.2). Restrictions are not scheduled to change in future releases. Refer to [Developing Applications](developing-applications.md), for information or limitations when developing your applications.

#### DB2 Considerations

The following considerations exist in the 12c Release 2 (12.2):

##### DD Basic Tables and Views

The owner of DD basic tables and views is `OTGDB2`. This cannot be changed.

##### SUBSTR Function Post-Processed

The `SUBSTR` function can be used with the Oracle database in ways that are not compatible with a DRDA server, such as DB2 UDB for z/OS. Therefore, the `SUBSTR` function is post-processed. However, it is possible to allow the server to process it natively using the "[Native Semantics](developing-applications.md)" feature. Refer to [Developing Applications](developing-applications.md), for details.

##### Data type Limitations

Refer to "[DRDA Data type to Oracle Data type Conversion](developing-applications.md) " for detailed information about data types. 

##### Null Values and Stored Procedures

Null values are not passed into, or returned from, calls to stored procedures through the gateway.

##### String Concatenation of Numbers

DB2 Universal Database does not support string concatenation of numbers. For example,

`SELECT 2||2 FROM table@dblink`

is not allowed.

##### GLOBAL_NAMES Initialization Parameter

If `GLOBAL_NAMES` is set to `TRUE` in the Oracle database `INIT.ORA` file, then in order to be able to connect to the gateway, you must specify the Heterogeneous Services (HS) initialization parameter, `HS_DB_DOMAIN`, in the Gateway Initialization Parameter file to match the value of the `DB_DOMAIN `parameter of the Oracle database. Refer to [Oracle Database Gateway Installation and Configuration Guide for IBM AIX on POWER Systems (64-Bit), Linux x86-64, Oracle Solaris on SPARC (64-Bit), Oracle Solaris on x86-64 (64-Bit) and HP-UX Itanium](../otgis/config-drda-gateway.md) or [Oracle Database Gateway Installation and Configuration Guide for Microsoft Windows](../otgiw/config-gateway-drda.md) , depending on your platform, for more information.

##### DRDA Package and DB2 considerations

The gateway utilizes a package for statement execution. This package will be implicitly bound upon the first time the gateway connects to the target DB2 system. Ensure that the user ID connecting to the DB2 system has the necessary privileges to bind a package. Refer to [Oracle Database Gateway Installation and Configuration Guide for IBM AIX on POWER Systems (64-Bit), Linux x86-64, Oracle Solaris on SPARC (64-Bit), Oracle Solaris on x86-64 (64-Bit) and HP-UX Itanium](../otgis/config-drda-gateway.md) or [Oracle Database Gateway Installation and Configuration Guide for Microsoft Windows](../otgiw/config-gateway-drda.md) , depending on your platform, for more information.

##### Date Arithmetic

In general, the following types of SQL expression forms do not work correctly with the gateway because of DB2 limitations:

    date + number
    number + date
    date - number
    date1 - date2

DB2 does not allow number addition or subtraction with date data types. The date and number addition and subtraction `(date + number, number + date, date - number)` forms are sent through to the DB2 where they are rejected.

Also, DB2 does not perform date subtraction consistently. When you subtract two dates `(date1 - date2)`, differing interpretations of date subtraction in DB2 cause the results to vary by server.

**Note:**

Avoid date arithmetic expressions in all gateway SQL expressions until date arithmetic problems are resolved.

##### Row Length Limitation

Because of a restriction of the DRDA architecture, rows with aggregate length exceeding 32 KB in DRDA representation cannot be stored or retrieved.

##### LONG Data type in SQL\*Plus

SQL\*Plus cannot fetch `LONG` columns from the Oracle Database Gateway for DRDA.

##### Stored Procedures and Transaction Integrity

IBM DB2 has introduced a feature called Commit on Return for stored procedures. This feature allows DB2 to perform an automatic commit after a stored procedure runs successfully. This feature is enabled when the procedure is created. To ensure data integrity, the Oracle Database Gateway for DRDA does not support this feature in a heterogeneous environment. When attempting to call a stored procedure that has this feature enabled, through the gateway, the gateway will return an error, `ORA-28526` or `PLS-00201` (identifier must be declared).

#### SQL Limitations

The SQL limitations for Oracle Database Gateway for DRDA are described in the following sections:

##### Oracle ROWID Column

The DB2 `ROWID` column is not compatible with the Oracle `ROWID` column. Because the `ROWID` column is not supported, the following restrictions apply:

- `UPDATE` and `DELETE` are not supported with the `WHERE CURRENT OF CURSOR` clause. To update or delete a specific row through the gateway, a condition style `WHERE` clause must be used. (Bug No. 205538)

  When `UPDATE` and `DELETE` statements are used in precompiler and PL/SQL programs, they rely internally on the Oracle `ROWID` function.

- Snapshots between Oracle database and DB2 are not supported.

  Snapshots rely internally on the Oracle `ROWID` column.

##### Oracle Bind Variables

Oracle bind variables become SQL parameter markers when used with the gateway. Therefore, the bind variables are subject to the same restrictions as SQL parameter markers.

For example, the following statements are not allowed:

    WHERE :x IS NULL
    WHERE :x = :y

##### CONNECT BY Is Not Supported

Oracle Database Gateway for DRDA does not support `CONNECT BY` in `SELECT` statements.
