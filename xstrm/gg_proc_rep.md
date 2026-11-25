Procedural replication is configured mainly within Oracle GoldenGate. However, you can display the procedural replication configuration and complete some configuration tasks within the database.

- About Oracle GoldenGate Procedural Replication
  Oracle GoldenGate supports the replication of procedure calls in Oracle-supplied packages. You can monitor Oracle GoldenGate procedural replication in an Oracle database.
- Determining Whether Procedural Replication Is On
  Use the `GG_PROCEDURE_REPLICATION_ON` function in the `DBMS_GOLDENGATE_ADM` package to determine whether Oracle GoldenGate procedural replication is on or off.
- Excluding Objects from Procedural Replication
  Use the `INSERT_PROCREP_EXCLUSION_OBJ` procedure in the `DBMS_GOLDENGATE_ADM` package to exclude an object from Oracle GoldenGate procedural replication.
- Monitoring Oracle GoldenGate Procedural Replication
  A set of data dictionary views enable you to monitor Oracle GoldenGate procedural replication.

**See Also:**

The Oracle GoldenGate documentation for information about configuring procedural replication with Oracle GoldenGate.

**Parent topic:** [Oracle GoldenGate Capabilities in Oracle Database](gg_capabilities.md)

### 14.1 About Oracle GoldenGate Procedural Replication

Oracle GoldenGate supports the replication of procedure calls in Oracle-supplied packages. You can monitor Oracle GoldenGate procedural replication in an Oracle database.

**Note:**

The documentation in this book is for the procedural replication feature that is specific to Oracle Database 12c Release 2 (12.2) and later, which is configured in an Oracle database. It also requires Oracle GoldenGate version 12.3 and later.

Oracle GoldenGate administrators optionally can enable and disable procedural replication. With procedural replication, calls to procedures in Oracle-supplied packages at one database are replicated to one or more other databases and then executed at those databases.

For example, a call to subprograms in the `DBMS_REDEFINITION` package can perform an online redefinition of a table. If the table is replicated at several databases, and if you want the same online redefinition to be performed on the table at each database, then you can make the calls to the subprograms in the `DBMS_REDEFINITION` package at one database, and Oracle GoldenGate can replicate those calls to the other databases.

In addition, you can exclude specific database objects from procedural replication under the guidance of Oracle Support. To do so, use the `INSERT_PROCREP_EXCLUSION_OBJ` procedure in the `DBMS_GOLDENGATE_ADM` package.

Data dictionary views enable you to monitor Oracle GoldenGate procedural replication in an Oracle database. For example, you can query these views to list the packages and procedures supported by Oracle GoldenGate procedural replication. You can also list the database objects that have been excluded from procedural replication.

**See Also:**

The Oracle GoldenGate documentation for information about enabling and using procedural replication

**Parent topic:** Oracle GoldenGate Procedural Replication

### 14.2 Determining Whether Procedural Replication Is On

Use the `GG_PROCEDURE_REPLICATION_ON` function in the `DBMS_GOLDENGATE_ADM` package to determine whether Oracle GoldenGate procedural replication is on or off.

1.  Connect to the database as `sys` (`sqlplus`, `sqlcl`, `sqldeveloper`) not as an Oracle GoldenGate administrator.
2.  Run the `GG_PROCEDURE_REPLICATION_ON` function.

Example 14-1 Running the `GG_PROCEDURE_REPLICATION_ON` Function

    SET SERVEROUTPUT ON
    DECLARE
      on_or_off   NUMBER;
    BEGIN
      on_or_off := DBMS_GOLDENGATE_ADM.GG_PROCEDURE_REPLICATION_ON;
      IF on_or_off=1 THEN
        DBMS_OUTPUT.PUT_LINE('Oracle GoldenGate procedural replication is ON.');
      ELSE
        DBMS_OUTPUT.PUT_LINE('Oracle GoldenGate procedural replication is OFF.');
      END IF;
    END;
    /

**Parent topic:** Oracle GoldenGate Procedural Replication

### 14.3 Excluding Objects from Procedural Replication

Use the `INSERT_PROCREP_EXCLUSION_OBJ` procedure in the `DBMS_GOLDENGATE_ADM` package to exclude an object from Oracle GoldenGate procedural replication.

When a database object is on the exclusion list for Oracle GoldenGate procedural replication, execution of a subprogram in the package is not replicated if the subprogram operates on the excluded object.

**Note:**

Run the `INSERT_PROCREP_EXCLUSION_OBJ` procedure only under the direction of Oracle Support.

1.  Connect to the database as `sys` (`sqlplus`, `sqlcl`, `sqldeveloper`) not as an Oracle GoldenGate administrator.
2.  Run the `INSERT_PROCREP_EXCLUSION_OBJ` procedure and specify the database object to exclude.

The specified database object is placed on the exclusion list for Oracle GoldenGate procedural replication. To remove a database object from the exclusion list, run the `DELETE_PROCREP_EXCLUSION_OBJ` procedure.

Example 14-2 Excluding an Object from Oracle GoldenGate Procedural Replication

Assume you want to ensure that calls to the `DBMS_REDEFINITION.START_REDEF_TABLE` procedure for the `hr.employees` table are not replicated. This example adds the `hr.employees` table as an excluded database object for the `DBMS_REDEFINITION` package to accomplish this goal.

    BEGIN
      DBMS_GOLDENGATE_ADM.INSERT_PROCREP_EXCLUSION_OBJ(
        package_owner => 'SYS',
        package_name  => 'DBMS_REDEFINITION',
        object_owner  => 'hr',
        object_name   => 'employees');
    END;
    /

**Parent topic:** Oracle GoldenGate Procedural Replication

### 14.4 Monitoring Oracle GoldenGate Procedural Replication

A set of data dictionary views enable you to monitor Oracle GoldenGate procedural replication.

You can use the following views to monitor Oracle GoldenGate procedural replication:

Table 14-1 Oracle GoldenGate Procedural Replication Views

| View                           | Description                                                                                                                                                                                                                                                                                                                                                                                                                         |
|:-------------------------------|:------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `DBA_GG_SUPPORTED_PACKAGES`    | Provides details about supported packages for Oracle GoldenGate procedural replication.<br>When a package is supported and Oracle GoldenGate procedural replication is on, calls to subprograms in the package are replicated.                                                                                                                                                                                                      |
| `DBA_GG_SUPPORTED_PROCEDURES`  | Provides details about the procedures that are supported for Oracle GoldenGate procedural replication.                                                                                                                                                                                                                                                                                                                              |
| `DBA_GG_PROC_OBJECT_EXCLUSION` | Provides details about all database objects that are on the exclusion list for Oracle GoldenGate procedural replication.<br>A database object is added to the exclusion list using the `INSERT_PROCREP_EXCLUSION_OBJ` procedure in the `DBMS_GOLDENGATE_ADM` package. When a database object is on the exclusion list, execution of a subprogram n the package is not replicated if the subprogram operates on the excluded object. |

1.  Connect to the database as `sys` (`sqlplus`, `sqlcl`, `sqldeveloper`) not as an Oracle GoldenGate administrator.
2.  Query the views related to Oracle GoldenGate procedural replication.

- Displaying the Packages Supported for Oracle GoldenGate Procedural Replication
  The `DBA_GG_SUPPORTED_PACKAGES` view displays information about the supported packages for Oracle GoldenGate procedural replication.
- Listing the Procedures Supported for Oracle GoldenGate Procedural Replication
  The `DBA_GG_SUPPORTED_PROCEDURES` view displays information about the supported packages for Oracle GoldenGate procedural replication.
- Displaying Information About Database Objects Excluded from Oracle GoldenGate Procedural Replication
  The `DBA_GG_PROC_OBJECT_EXCLUSION` view provides details about all database objects that are on the exclusion list for Oracle GoldenGate procedural replication.

**Related Topics**

- Excluding Objects from Procedural Replication

**Parent topic:** Oracle GoldenGate Procedural Replication

#### 14.4.1 Displaying the Packages Supported for Oracle GoldenGate Procedural Replication

The `DBA_GG_SUPPORTED_PACKAGES` view displays information about the supported packages for Oracle GoldenGate procedural replication.

When a package is supported and Oracle GoldenGate procedural replication is on, calls to subprograms in the package are replicated, unless the package is excluded specifically.

1.  Connect to the database as `sys` (`sqlplus`, `sqlcl`, `sqldeveloper`) not as an Oracle GoldenGate administrator.
2.  Query the `DBA_GG_SUPPORTED_PACKAGES` view.

Example 14-3 Displaying Information About the Packages Supported for Oracle GoldenGate Procedural Replication

This query displays the following information about the packages:

- The owner of each package

- The name of each package

- The name of the feature to which the supported package belongs

- The minimum database release from which the package is supported

<!-- -->

    COLUMN OWNER FORMAT A10
    COLUMN NAME FORMAT A20
    COLUMN FEATURE FORMAT A20
    COLUMN MIN_DB_VERSION FORMAT A14

    SELECT OWNER,
           NAME,
           FEATURE,
           MIN_DB_VERSION
      FROM DBA_GG_SUPPORTED_PACKAGES;

Your output looks similar to the following:

    OWNER      NAME                 FEATURE              MIN_DB_VERSION
    ---------- -------------------- -------------------- --------------
    SYS        DBMS_REDEFINITION    REDEFINITION         12.2
    SYS        DBMS_FGA             FGA                  12.2
    SYS        DBMS_RLS             RLS                  12.2
    .
    .
    .

**Related Topics**

- [Oracle Database Reference](../refrn/DBA_GG_SUPPORTED_PACKAGES.md)

**Parent topic:** Monitoring Oracle GoldenGate Procedural Replication

#### 14.4.2 Listing the Procedures Supported for Oracle GoldenGate Procedural Replication

The `DBA_GG_SUPPORTED_PROCEDURES` view displays information about the supported packages for Oracle GoldenGate procedural replication.

When a procedure is supported and Oracle GoldenGate procedural replication is on, calls to the procedure are replicated, unless the procedure is excluded specifically.

1.  Connect to the database as `sys` (`sqlplus`, `sqlcl`, `sqldeveloper`) not as an Oracle GoldenGate administrator.
2.  Query the `DBA_GG_SUPPORTED_PROCEDURES` view.

Example 14-4 Displaying Information About the Packages Supported for Oracle GoldenGate Procedural Replication

This query displays the following information about the packages:

- The owner of each package

- The name of each package

- The name of each procedure

- The minimum database release from which the procedure is supported

- Whether there is an exclusion rule that prevents the procedure from being replicated for some database objects

<!-- -->

    COLUMN OWNER FORMAT A10
    COLUMN PACKAGE_NAME FORMAT A15
    COLUMN PROCEDURE_NAME FORMAT A15
    COLUMN MIN_DB_VERSION FORMAT A14
    COLUMN EXCLUSION_RULE_EXISTS FORMAT A14

    SELECT OWNER,
           PACKAGE_NAME,
           PROCEDURE_NAME,
           MIN_DB_VERSION,
           EXCLUSION_RULE_EXISTS
      FROM DBA_GG_SUPPORTED_PROCEDURES;

Your output looks similar to the following:

    OWNER      PACKAGE_NAME    PROCEDURE_NAME  MIN_DB_VERSION EXCLUSION_RULE
    ---------- --------------- --------------- -------------- --------------
    XDB        DBMS_XDB_CONFIG ADDTRUSTMAPPING 12.2           NO
    CTXSYS     CTX_DDL         ALTER_INDEX     12.2           NO
    SYS        DBMS_FGA        DROP_POLICY     12.2           NO
    SYS        XS_ACL          DELETE_ACL      12.2           NO
    .
    .
    .

**Related Topics**

- [Oracle Database Reference](../refrn/DBA_GG_SUPPORTED_PROCEDURES.md)

**Parent topic:** Monitoring Oracle GoldenGate Procedural Replication

#### 14.4.3 Displaying Information About Database Objects Excluded from Oracle GoldenGate Procedural Replication

The `DBA_GG_PROC_OBJECT_EXCLUSION` view provides details about all database objects that are on the exclusion list for Oracle GoldenGate procedural replication.

A database object is added to the exclusion list using the `INSERT_PROCREP_EXCLUSION_OBJ` procedure in the `DBMS_GOLDENGATE_ADM` package. When a database object is on the exclusion list, execution of a subprogram in the package is not replicated if the subprogram operates on the excluded object.

1.  Connect to the database as `sys` (`sqlplus`, `sqlcl`, `sqldeveloper`) not as an Oracle GoldenGate administrator.
2.  Query the `DBA_GG_PROC_OBJECT_EXCLUSION` view.

Example 14-5 Displaying Information About Database Objects Excluded from Oracle GoldenGate Procedural Replication

This query displays the following information about the packages:

- The owner of each package

- The name of each package

- The owner of each excluded database object

- The name of each excluded database object

<!-- -->

    COLUMN PACKAGE_OWNER FORMAT A15
    COLUMN PACKAGE_NAME FORMAT A20
    COLUMN OBJECT_OWNER FORMAT A15
    COLUMN OBJECT_NAME FORMAT A15

    SELECT PACKAGE_OWNER,
           PACKAGE_NAME,
           OBJECT_OWNER,
           OBJECT_NAME
       FROM DBA_GG_PROC_OBJECT_EXCLUSION;

Your output looks similar to the following:

    PACKAGE_OWNER   PACKAGE_NAME         OBJECT_OWNER    OBJECT_NAME
    --------------- -------------------- --------------- ---------------
    SYS             DBMS_REDEFINITION    HR              EMPLOYEES

**Related Topics**

- Excluding Objects from Procedural Replication
- [Oracle Database Reference](../refrn/DBA_GG_PROC_OBJECT_EXCLUSION.md)

**Parent topic:** Monitoring Oracle GoldenGate Procedural Replication
