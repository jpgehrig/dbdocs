Oracle Label Security supports the standard Oracle Database utilities, but certain restrictions apply, which may require extra steps to get the expected results.

- Oracle Data Pump Export Use with Oracle Label Security
  Oracle Data Pump enables high-speed movement of data and metadata from one database to another.
- Data Pump Import Use with Oracle Label Security
  Oracle Data Pump enables high-speed movement of data and metadata from one database to another.
- SQL\*Loader Use with Oracle Label Security
  SQL\*Loader moves data from external files into tables in Oracle Database.
- Performance Tips for Oracle Label Security
  You can achieve optimal performance with Oracle Label Security.
- Creation of Additional Databases After Installation
  You can create and configure additional databases after you install Oracle Label Security.
- Oracle Label Security Upgrades and Downgrades
  You should be aware of how to manage Oracle Label Security upgrades and downgrades.

**Parent topic:** [Administering an Oracle Label Security Application](part3.md)

### 15.1 Oracle Data Pump Export Use with Oracle Label Security

Oracle Data Pump enables high-speed movement of data and metadata from one database to another.

- Full Database Export
  Starting with Oracle Database 12c, Oracle Label Security metadata in the `LBACSYS` schema can be included when doing a full database export and import operation.
- Schema and Table-Level Export
  The Data Pump export utility functions in the standard way under Oracle Label Security.

**Parent topic:** Performing DBA Functions Under Oracle Label Security

#### 15.1.1 Full Database Export

Starting with Oracle Database 12c, Oracle Label Security metadata in the `LBACSYS` schema can be included when doing a full database export and import operation.

The source database can be Oracle Database 11g release 2 (11.2.0.3), or higher, but the target database must be Oracle Database 12c or higher.

Before starting the Data Pump import on the target database, you must enable Oracle Label Security.

**Parent topic:** Oracle Data Pump Export Use with Oracle Label Security

#### 15.1.2 Schema and Table-Level Export

The Data Pump export utility functions in the standard way under Oracle Label Security.

There are, however, a few differences resulting from the enforcement of Oracle Label Security policies.

**Note:**

You must have the `EXEMPT ACCESS POLICY` privilege in order to export all rows in the table, or else no rows are exported.

- For any tables protected by an Oracle Label Security policy, only rows with labels authorized for read access are exported. Unauthorized rows are not included in the export file. Consequently, to export all the data in protected tables, you must have a privilege (such as `FULL` or `READ`) that gives you complete access.

- SQL statements to reapply policies are exported along with tables and schemas that are exported. These statements are carried out during import to reapply policies with the same enforcement options as in the original database.

- The `HIDE` property is not exported. When protected tables are exported, the label columns in those tables are also exported (as numeric values). However, if a label column is hidden, then it is exported as a normal, unhidden column.

- The user must have `EXEMPT ACCESS POLICY` in order to export all rows in the table, or else no rows are exported.

**Parent topic:** Oracle Data Pump Export Use with Oracle Label Security

### 15.2 Data Pump Import Use with Oracle Label Security

Oracle Data Pump enables high-speed movement of data and metadata from one database to another.

- Full Database Import for the LBACSYS Schema Metadata
  Oracle Label Security metadata in the `LBACSYS` schema can be included when you perform a full database export and import operation.
- Schema and Table Level Import
  You can use the Oracle Data Pump Import utility functions under Oracle Label Security.

**Parent topic:** Performing DBA Functions Under Oracle Label Security

#### 15.2.1 Full Database Import for the LBACSYS Schema Metadata

Oracle Label Security metadata in the `LBACSYS` schema can be included when you perform a full database export and import operation.

The source database can be Oracle Database 11g release 2 (11.2.0.3), or higher, but the target database must be Oracle Database 12c release 1 (12.1) or higher.

Oracle Data Pump import utility, `impdp`, automatically imports Label Security metadata including policies, labels, user authorizations, schema and table policy enforcements. You must register and enable Oracle Label Security for the target database before beginning the import operation.

**Related Topics**

- [Checking if Oracle Label Security Has Been Registered and Enabled](getting-started-with-oracle-label-security.md)

**Parent topic:** Data Pump Import Use with Oracle Label Security

#### 15.2.2 Schema and Table Level Import

You can use the Oracle Data Pump Import utility functions under Oracle Label Security.

- Requirements for Import Under Oracle Label Security
  You can use the `impdp` under Oracle Label Security.
- Definition of Data Labels for Import
  The label definitions at the time of import must include all the policy labels used in the export file.
- Imports of Labeled Data Without Installing Oracle Label Security
  When data type for policy label columns is `NUMBER`, they can be imported into databases that do not have Oracle Label Security installed.
- Imports of Unlabeled Data
  You can import unlabeled data into an existing table protected by an Oracle Label Security policy.
- Importing Tables with Hidden Columns
  A hidden column is exported as a normal column, but the fact that it was hidden is lost.

**Parent topic:** Data Pump Import Use with Oracle Label Security

##### 15.2.2.1 Requirements for Import Under Oracle Label Security

You can use the `impdp` under Oracle Label Security.

To use the `impdp` under Oracle Label Security, you must prepare the import database and ensure that the import user has the proper authorizations.

- Preparing the Import Database
  Before you can use the Import utility with Oracle Label Security, you must prepare the import database.
- Verification of Import User Authorizations
  You must be authorized to run the import operation for labels required to insert data and labels in the export file.

**Parent topic:** Schema and Table Level Import

###### 15.2.2.1.1 Preparing the Import Database

Before you can use the Import utility with Oracle Label Security, you must prepare the import database.

1.  Ensure that Oracle Label Security is enabled. See [Checking if Oracle Label Security Has Been Registered and Enabled](getting-started-with-oracle-label-security.md).
2.  Create any Oracle Label Security policies that protect the data to be imported.
    Ensure that the policies use the same column names as in the export database.
3.  Define in the import database all of the label components and individual labels used in tables being imported.
    Ensure that the same tag values are assigned to the policy labels in each database. (Note that if you are importing into a database from which you exported, then the components are most likely already defined.)

**Parent topic:** Requirements for Import Under Oracle Label Security

###### 15.2.2.1.2 Verification of Import User Authorizations

You must be authorized to run the import operation for labels required to insert data and labels in the export file.

Errors will be raised upon import if you do not meet the following requirements.

- To import tables or schemas with Label Security policies on them, you must have execute privilege on the `SA_POLICY_ADMIN` package.

  To ensure that all rows can be imported, you must have the `policy``_DBA` role for all policies with data being imported. After each schema or table is imported, any policies from the export database are reapplied to the imported objects.

- You must also have the ability to write all rows that have been exported as follows:

  Requirement 2:

  - You can granted the `FULL` privilege or given sufficient authorization to write all labels contained in the import file.

  - A user-defined labeling function can be applied to the table.

**Parent topic:** Requirements for Import Under Oracle Label Security

##### 15.2.2.2 Definition of Data Labels for Import

The label definitions at the time of import must include all the policy labels used in the export file.

The `DBA_SA_LABELS` data dictionary view lists data labels. You can use the views `DBA_SA_LEVELS`, `DBA_SA_COMPARTMENTS`, `DBA_SA_GROUPS`, and in the export database to design SQL scripts that re-create the label components and labels for each policy in the import database. The following example shows how to generate a PL/SQL block that re-creates the individual labels for the `HR` policy:

    set serveroutput on
    BEGIN
       dbms_output.put_line('BEGIN');
       FOR l IN (SELECT label_tag, label
                    FROM dba_sa_labels
                    WHERE policy_name='HR'
                    ORDER BY label_tag) LOOP
           dbms_output.put_line
               ('  SA_LABEL_ADMIN.CREATE_LABEL(''HR'', ' ||
                l.label_tag || ', ''' || l.label || ''');');
       END LOOP;
       dbms_output.put_line ('END;');
       dbms_output.put_line ('/');
    END;
    /

If the individual labels do not exist in the import database with the same numeric values and the same character string representations as in the export database, then the label values in the imported tables will be meaningless. The numeric label value in the table may refer to a different character string representation, or it may be a label value that has not been defined at all in the import database.

If a user attempts to access rows containing invalid numeric labels, then the operation will fail.

**Parent topic:** Schema and Table Level Import

##### 15.2.2.3 Imports of Labeled Data Without Installing Oracle Label Security

When data type for policy label columns is `NUMBER`, they can be imported into databases that do not have Oracle Label Security installed.

In this case, the values in the policy label column are imported as numbers. Without the corresponding Oracle Label Security label definitions, the numbers will not reference any specific label.

Note that errors will be raised during the import if Oracle Label Security is not installed, because the SQL statements to reapply the policy to the imported tables and schemas will fail.

**Parent topic:** Schema and Table Level Import

##### 15.2.2.4 Imports of Unlabeled Data

You can import unlabeled data into an existing table protected by an Oracle Label Security policy.

Either the `LABEL_DEFAULT` option or a labeling function must be specified for each table being imported, so that the labels for the rows can be automatically initialized as they are inserted into the table.

**Parent topic:** Schema and Table Level Import

##### 15.2.2.5 Importing Tables with Hidden Columns

A hidden column is exported as a normal column, but the fact that it was hidden is lost.

If you want to preserve the hidden property of the label column, then you must first create the table in the import database.

1.  Before you perform the import, create the table and apply the policy with the `HIDE` option. This adds the policy label column to the table as a hidden column.
2.  Remove the policy from the table, so that the enforcement options specified in the export file can be reapplied to the table during the import operation.
3.  Perform the import with `IGNORE=Y`. Setting the `IGNORE` parameter to `Y` ignores errors during import.
4.  Manually apply the policy to the table with the `HIDE` option.

**Parent topic:** Schema and Table Level Import

### 15.3 SQL\*Loader Use with Oracle Label Security

SQL\*Loader moves data from external files into tables in Oracle Database.

- Requirements for Using SQL\*Loader Under Oracle Label Security
  You can use SQL\*Loader with the conventional path to load data into a database protected by Oracle Label Security.
- Oracle Label Security Input to SQL\*Loader
  If the policy column for a table is hidden, then you must use the `HIDDEN` keyword to convey this information to SQL\*Loader.

**Parent topic:** Performing DBA Functions Under Oracle Label Security

#### 15.3.1 Requirements for Using SQL\*Loader Under Oracle Label Security

You can use SQL\*Loader with the conventional path to load data into a database protected by Oracle Label Security.

Because SQL\*Loader performs `INSERT` operations, all of the standard requirements apply when using SQL\*Loader on tables protected by Oracle Label Security policies.

**Parent topic:** SQL\*Loader Use with Oracle Label Security

#### 15.3.2 Oracle Label Security Input to SQL\*Loader

If the policy column for a table is hidden, then you must use the `HIDDEN` keyword to convey this information to SQL\*Loader.

To specify row labels in the input file, you must include the policy label column in the `INTO` `TABLE` clause in the control file.

To load policy labels along with the data for each row, you can specify the `CHAR_TO_LABEL` function or the `TO_DATA_LABEL` function in the SQL\*Loader control file.

**Note:**

When Oracle Label Security is installed to work with Oracle Internet Directory, dynamic label generation is not allowed, because labels are managed centrally in Oracle Internet Directory, using `olsadmintool` commands.

When Oracle Label Security is directory-enabled, then the function `TO_DATA_LABEL` is not available and generates an error message if used.

Table 15-1 shows the variations that you can use when you load Oracle Label Security data with SQL\*Loader.

Table 15-1 Input Choices for Oracle Label Security Input to SQL\*Loader

| Form of Data                           | Explanation of Results                                                                                                                                                                |
|:---------------------------------------|:--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `col1 hidden integer external`         | Hidden column loaded with tag value of data directly from data file                                                                                                                   |
| `col2 hidden char(5) "func(:col2)"`    | Hidden column loaded with character value of data from data `file.func()` used to translate between the character label and its tag value. Note: `func()` might be `char_to_label()`. |
| `col3 hidden "func(:col3)"`            | Same as in `col2`, field type defaults to char                                                                                                                                        |
| `col4 hidden expression "func(:col4)"` | Hidden column not mapped to input `data.func()` will be called to provide the label value. This could be a user function.                                                             |

For example, the following is a valid `INTO` `TABLE` clause in a control file that is loading data into the `DEPT` table:

    INTO TABLE dept
    (hr_label HIDDEN POSITION (1:22) CHAR "CHAR_TO_LABEL('HR',:hr_label)",
    deptno    POSITION (23:26) INTEGER EXTERNAL,
    dname     POSITION (27:40) CHAR,
    loc       POSITION(41,54)  CHAR)

The following could be an entry in the data file specified by this control file:

    HS:FN                  231 ACCOUNTING  REDWOOD SHORES

**Related Topics**

- [Command-line Tools for Label Security Using Oracle Internet Directory](command-line-tools-for-label-security-using-oracle-internet-directory.md)

**Parent topic:** SQL\*Loader Use with Oracle Label Security

### 15.4 Performance Tips for Oracle Label Security

You can achieve optimal performance with Oracle Label Security.

- Use of ANALYZE to Improve Oracle Label Security Performance
  You can run the `ANALYZE` statement on the Oracle Label Security data dictionary tables in the `LBACSYS` schema.
- Creation of Indexes on the Policy Label Column
  Creating the appropriate type of index on the policy label column improves the performance of user-raised queries on protected tables.
- Label Tag Strategy Plan to Enhance Performance
  For optimal performance, you can plan a strategy for assigning values to label tags.
- Partitioned Data Based on Numeric Label Tags
  Using a numeric ordering strategy with the numeric label tags applied to the labels can a basis for Oracle Database data partitioning.

**Parent topic:** Performing DBA Functions Under Oracle Label Security

#### 15.4.1 Use of ANALYZE to Improve Oracle Label Security Performance

You can run the `ANALYZE` statement on the Oracle Label Security data dictionary tables in the `LBACSYS` schema.

This enables the cost-based optimizer to improve execution plans on queries, which improves Oracle Label Security performance.

Running `ANALYZE` on application tables improves the application SQL performance.

**See Also:**

[Oracle Database SQL Language Reference](../sqlrf/ANALYZE.md) for the `ANALYZE` syntax

**Parent topic:** Performance Tips for Oracle Label Security

#### 15.4.2 Creation of Indexes on the Policy Label Column

Creating the appropriate type of index on the policy label column improves the performance of user-raised queries on protected tables.

If you have applied an Oracle Label Security policy on a database table in a particular schema, then you should compare the number of different labels to the amount of data. Based on this information, you can decide which type of index to create on the policy label column.

- If the cardinality of data in the policy label column (that is, the number of labels compared to the number of rows) is low, then consider creating a bitmapped index.

- If the cardinality of data in the policy label column is high, then consider creating a B-tree index.

Consider the following case, in which the `EMP` table is protected by an Oracle Label Security policy with the `READ_CONTROL` enforcement option set, and `HR_LABEL` is the name of the policy label column. A user raises the following query:

    SELECT COUNT (*) FROM SCOTT.EMP;

In this situation, Oracle Label Security adds a predicate based on the label column. For example:

    SELECT COUNT (*) FROM SCOTT.EMP
      WHERE hr_label=100;

In this way, Oracle Label Security uses the security label to restrict the rows that are processed, based on the user's authorizations. To improve performance of this query, you could create an index on the `HR_LABEL` column.

Consider a more complex query (once again, with `READ_CONTROL` applied to the EMP table):

    SELECT COUNT (*) FROM SCOTT.EMP
      WHERE deptno=10

Again, Oracle Label Security adds a predicate based on the label column:

    SELECT COUNT (*) FROM SCOTT.EMP
      WHERE deptno=10
      AND hr_label=100;

In this case, you might want to create a composite index based on the `DEPTNO` and `HR_LABEL` columns, to improve application performance.

**Parent topic:** Performance Tips for Oracle Label Security

#### 15.4.3 Label Tag Strategy Plan to Enhance Performance

For optimal performance, you can plan a strategy for assigning values to label tags.

In general, it is best to assign higher numeric values to labels with higher sensitivity levels.

This is because, typically, many more users can see data at comparatively low levels and fewer users at higher levels can see many levels of data.

In addition, with `READ_CONTROL` set, Oracle Label Security generates a predicate that uses a `BETWEEN` clause to restrict the rows to be processed by the query. As illustrated in the following example, if the higher-sensitivity labels do not have a higher label tag than the lower-sensitivity labels, then the query will potentially examine a larger set of rows. This will affect performance.

Table 15-2 shows a set of label tags assigned as follows:

Table 15-2 Label Tag Performance Example: Correct Values

| Label      | Label Tag |
|:-----------|:----------|
| `TS:A`,`B` | `100`     |
| `S:A`      | `50`      |
| `S`        | `20`      |
| `U:A`      | `10`      |

Here, a user whose maximum authorization is S:A can potentially access data at labels `S:A`, `S`, and `U:A`. Consider what happens when this user raises the following query:

    SELECT COUNT (*) FROM SCOTT.EMP

Oracle Label Security adds a predicate that includes a `BETWEEN` clause (based on the maximum and minimum authorizations) to restrict the set of rows this user can see:

    SELECT COUNT (*) FROM SCOTT.EMP
      WHERE hr_label BETWEEN 10 AND 50;

Performance improves, because the query examines only a subset of data based on the user's authorizations. It does not fruitlessly process rows that the user is not authorized to access.

Table 15-3 shows how unnecessary work is performed if the tag values were assigned as follows:

Table 15-3 Label Tag Performance Example: Incorrect Values

| Label      | Label Tag |
|:-----------|:----------|
| `TS:A`,`B` | `50`      |
| `S:A`      | `100`     |
| `S`        | `20`      |
| `U:A`      | `10`      |

In this case, the user with `S:A` authorization can see only some of the labels between 100 and 10. Although the user cannot see `TS:A`,`B` labels (that is, rows with a label tag of 50). A query would nonetheless pick up and process these rows, even though the user ultimately will not have access to them.

**Parent topic:** Performance Tips for Oracle Label Security

#### 15.4.4 Partitioned Data Based on Numeric Label Tags

Using a numeric ordering strategy with the numeric label tags applied to the labels can a basis for Oracle Database data partitioning.

Depending on the application, partitioning data based on label values may or may not be useful. Consider, for example, a business-hosting CRM application to which many companies subscribe. In the same `EMP` table, there might be rows (and labels) for Subscriber 1 and Subscriber 2. That is, information for both companies can be stored in the same table, as long as it is labeled differently. In this case, employees of Subscriber 1 will never need to access data for Subscriber 2, so it might make sense to partition based on label. You could put rows for Subscriber 1 in one partition, and rows for Subscriber2 in a different partition. When a query is raised, it will access only one or the other partition, depending on the label. Performance improves because partitions that are not relevant are not examined by the query.

The following example shows this is done. It places labels in the 2000 series on one partition, labels in the 3000 series on another partition, and labels in the 4000 series on a third partition.

    CREATE TABLE EMPLOYEE(
        EMPNO NUMBER(10) CONSTRAINT PK_EMPLOYEE PRIMARY KEY,
        ENAME VARCHAR2(10),
        JOB VARCHAR2(9),
        MGR NUMBER(4),
        HIREDATE DATE,
        SAL NUMBER(7,2),
        COMM NUMBER(7,2),
        DEPTNO NUMBER(4),
        HR_LABEL NUMBER(10))
        TABLESPACE PERF_DATA
        STORAGE (initial 2M
        NEXT 1M
        MINEXTENTS 1
        MAXEXTENTS unlimited)
        PARTITION BY RANGE (hr_label)
        (partition sx1 VALUES LESS THAN (2000) NOLOGGING,
         partition sx2 VALUES LESS THAN (3000),
         partition sx3 VALUES LESS THAN (4000)
     );

**Parent topic:** Performance Tips for Oracle Label Security

### 15.5 Creation of Additional Databases After Installation

You can create and configure additional databases after you install Oracle Label Security.

- About the Creation of Additional Databases After Installation
  When you install Oracle Database Enterprise Edition and Oracle Label Security, an initial Oracle database is created.
- Creating Additional Databases When the Label Security Schema Is in the Seed
  You can configure Oracle Label Security if the database was installed with the label security schema is in the seed database.
- Creating Additional Databases with the Custom Installation Option
  You can configure Oracle Label Security after a custom database installation.

**Parent topic:** Performing DBA Functions Under Oracle Label Security

#### 15.5.1 About the Creation of Additional Databases After Installation

When you install Oracle Database Enterprise Edition and Oracle Label Security, an initial Oracle database is created.

If you want to create additional databases, then you should do this using the Database Configuration Assistant. Alternatively, you can create additional databases by following the steps listed in [Oracle Database Administrator’s Guide](../admin/creating-and-configuring-an-oracle-database.md).

Each time you create a new database, you must install the Oracle Label Security data dictionary tables, views, and packages into it, and create the `LBACSYS` account.

For the first database, this is done automatically when you install Oracle Label Security, regardless of whether or not you choose the custom install. If you do not choose the custom install, then you are installing the database with the label security schema in the seed.

To create additional databases, there are different processes for configuring label security, depending on whether the first database was installed with the custom install or with the label security schema in the seed.

If you initially chose custom install, but did not install label security, you can install and configure label security using either process described in this section.

**Parent topic:** Creation of Additional Databases After Installation

#### 15.5.2 Creating Additional Databases When the Label Security Schema Is in the Seed

You can configure Oracle Label Security if the database was installed with the label security schema is in the seed database.

1.  Select the Oracle Label Security option in DBCA.
2.  Select the check box to configure Oracle Label Security.

**Parent topic:** Creation of Additional Databases After Installation

#### 15.5.3 Creating Additional Databases with the Custom Installation Option

You can configure Oracle Label Security after a custom database installation.

1.  Connect to the Oracle Database instance as user `SYS`, using the `AS SYSDBA` syntax.
2.  Run the script` $ORACLE_HOME/rdbms/admin/catols.sql`.
    This script installs the label-based framework, data dictionary, data types, and packages. After the script is run, the `LBACSYS` account exists, with the password `LBACSYS`. All the Oracle Label Security packages exist under this account.
3.  Change the default password of the `LBACSYS` user.

**Parent topic:** Creation of Additional Databases After Installation

### 15.6 Oracle Label Security Upgrades and Downgrades

You should be aware of how to manage Oracle Label Security upgrades and downgrades.

- About Oracle Label Security Upgrades and Downgrades
  Oracle provides preprocess scripts that perform upgrade and downgrade operations.
- Oracle Label Security Upgrades
  Oracle provides a preprocess script that you must run before you perform an upgrade.
- Oracle Label Security Downgrades
  Oracle provides a preprocess script that you must run before you downgrade.

**Parent topic:** Performing DBA Functions Under Oracle Label Security

#### 15.6.1 About Oracle Label Security Upgrades and Downgrades

Oracle provides preprocess scripts that perform upgrade and downgrade operations.

As a safety measure, before you run either the upgrade or downgrade preprocess script, Oracle recommends that you back up your audit records. To do this, you can archive the audit trail as described in [Oracle Database Security Guide](../dbseg/administering-the-audit-trail.md).

Before they run, the preprocess scripts check that there is enough space in the audit tablespace to copy all the audit records, and will exit without processing if there is not.

You may continue running your applications on the database while OLS preprocess scripts are running.

**See Also:**

[Oracle Database Upgrade Guide](../upgrd/requirements-upgrading-databases-that-use-oracle-label-security-and-oracle-database-vault.md) for requirements for upgrading databases that use Oracle Label Security and Oracle Database Vault

**Parent topic:** Oracle Label Security Upgrades and Downgrades

#### 15.6.2 Oracle Label Security Upgrades

Oracle provides a preprocess script that you must run before you perform an upgrade.

- About Oracle Label Security Upgrades
  You must upgrade Oracle Label Security for pre-Oracle Database 12c release 1 (12.1) databases.
- Running the Oracle Label Security Preprocess Script Before Upgrading
  You can run the Oracle Label Security preprocess script before upgrading.

**Parent topic:** Oracle Label Security Upgrades and Downgrades

##### 15.6.2.1 About Oracle Label Security Upgrades

You must upgrade Oracle Label Security for pre-Oracle Database 12c release 1 (12.1) databases.

**Note:**

Running the `olspreupgrade.sql` script before upgrading is mandatory for upgrading databases earlier than Oracle Database 12c release (12.1) that use Oracle Label Security or Database Vault.

After you have upgraded to Oracle Database release 12c or later, you do not need to run the Oracle Label Security preprocessing script when you patch or upgrade the database.

Before performing the OLS upgrade process, you must run the Oracle Label Security preprocess upgrade script, `olspreupgrade.sql`, to process the `AUD$` table contents. The OLS upgrade moves the `AUD$`table from the `SYSTEM` schema to the `SYS` schema. The `olspreupgrade.sql` script is a preprocessing script required for this move. It creates a temporary table, `PREUPG_AUD$`, in the `SYS` schema and moves the `SYSTEM.AUD$` records to `SYS.PREUPG_AUD$`. The moved records can no longer be viewed through the `DBA_AUDIT_TRAIL` view, but can be viewed by directly accessing the `SYS.PREUPG_AUD$` table, until the upgrade completes. Once the upgrade completes, the `SYS.PREUPG_AUD$` table is permanently deleted and all audit records, can be viewed through the `DBA_AUDIT_TRAIL` view.

**Parent topic:** Oracle Label Security Upgrades

##### 15.6.2.2 Running the Oracle Label Security Preprocess Script Before Upgrading

You can run the Oracle Label Security preprocess script before upgrading.

1.  Copy the `ORACLE_HOME``/rdbms/admin/olspreupgrade.sql` script from the newly installed Oracle home to the Oracle home of the database to be upgraded.
2.  Connect to the database to be upgraded. At the system prompt, enter:
        CONNECT SYS AS SYSDBA
        Enter password password
3.  Run the Oracle Label Security preprocess script:
        @$ORACLE_HOME/rdbms/admin/olspreupgrade.sql

**Note:**

The upgrade status for the Oracle Label Security component will be marked `INVALID` if the Oracle Label Security preprocess script reports an error. If this happens, you must correct the errors and then rerun the upgrade process. See [Oracle Database Upgrade Guide](../upgrd/rerunning-upgrades-oracle-database.md) for more information about rerunning the upgrade process for Oracle Database.

**Parent topic:** Oracle Label Security Upgrades

#### 15.6.3 Oracle Label Security Downgrades

Oracle provides a preprocess script that you must run before you downgrade.

- About Oracle Label Security Downgrades
  You can downgrade from an Oracle Database 12c release 1 (12.1) or later database that uses Oracle Label Security or Oracle Database Vault.
- Running the Oracle Label Security Preprocess Script Before Downgrading
  You must connect as `SYS` wth the `SYSDBA` administrative privilege before running the Oracle Label Security preprocess script for a downgrade.

**Parent topic:** Oracle Label Security Upgrades and Downgrades

##### 15.6.3.1 About Oracle Label Security Downgrades

You can downgrade from an Oracle Database 12c release 1 (12.1) or later database that uses Oracle Label Security or Oracle Database Vault.

To do this, you must run the OLS preprocessing script, `olspredowngrade.sql` to process the `AUD$` table contents. The OLS downgrade script moves the `AUD$` table from the `SYS` schema to the `SYSTEM` schema. The `olspredowngrade.sql` script is a processing script required in preparation for this move. It creates a temporary table, `PREDWG_AUD$`, in the `SYSTEM` schema and moves the `SYS.AUD$` records to `SYSTEM.PREDWG_AUD$`. The moved records can no longer be viewed through the `DBA_AUDIT_TRAIL` view, but you can view them by directly accessing the `SYSTEM.PREDWG_AUD$` table until the downgrade completes. Once the downgrade completes, the `SYSTEM.PREDWG_AUD$` table is permanently deleted. At this point, all audit records are available for viewing in the `DBA_AUDIT_TRAIL` data dictionary view.

**Parent topic:** Oracle Label Security Downgrades

##### 15.6.3.2 Running the Oracle Label Security Preprocess Script Before Downgrading

You must connect as `SYS` wth the `SYSDBA` administrative privilege before running the Oracle Label Security preprocess script for a downgrade.

1.  Connect to the database to be downgraded. At the system prompt, enter:
        CONNECT SYS AS SYSDBA
        Enter password password
2.  Run the OLS preprocess downgrade script:
        @$ORACLE_HOME/rdbms/admin/olspredowngrade.sql

**Parent topic:** Oracle Label Security Downgrades
