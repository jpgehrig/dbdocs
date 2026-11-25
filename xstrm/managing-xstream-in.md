You can manage an XStream In configuration.

This chapter does not cover using rules, rule sets, or rule-based transformations with inbound servers. By default, an inbound server does not use rules or rule sets. Therefore, an inbound server applies all of the logical change records (LCRs) sent to it by an XStream client application. However, to filter the LCRs sent to an inbound server, you can add rules and rule sets to an inbound server using the `DBMS_XSTREAM_ADM` and `DBMS_RULE_ADM` packages. You can also specify rule-based transformations using the `DBMS_XSTREAM_ADM` package.

- About Managing XStream In
  You can modify the database components that are part of an XStream In configuration, such as inbound servers.
- Starting an Inbound Server
  A inbound server must be enabled for it to receive logical change records (LCRs) from an XStream client application and apply the LCRs. You run the `START_APPLY` procedure in the `DBMS_APPLY_ADM` package to start an existing inbound server.
- Stopping an Inbound Server
  You run the `STOP_APPLY` procedure in the `DBMS_APPLY_ADM` package to stop an existing inbound server. You might stop an inbound server when you are troubleshooting a problem in an XStream configuration.
- Setting an Apply Parameter for an Inbound Server
  Apply parameters control the way an inbound server operates. You set an apply parameter for an inbound server using the `SET_PARAMETER` procedure in the `DBMS_XSTREAM_ADM` package.
- Changing the Apply User for an Inbound Server
  An inbound server applies LCRs in the security domain of its apply user, and the client application must attach to the inbound server as the apply user. You can change the apply user for an inbound server with the `ALTER_INBOUND` procedure in the `DBMS_XSTREAM_ADM` package.
- Managing XStream In Conflict Detection and Resolution
  When more than one client modifies the same table row at approximately the same time, conflicts are possible. XStream In detects conflicts and provides methods for resolving conflicts.
- Managing Apply Errors
  Apply errors result when an inbound server tries to apply an LCR, and an error is raised.
- Conflict and Error Handling Precedence
  To resolve a conflict or error, an inbound server tries to find conflict handlers and error handlers.
- Dropping Components in an XStream In Configuration
  You can drop an inbound server with the `DROP_INBOUND` procedure in the `DBMS_XSTREAM_ADM` package.

**Parent topic:** [XStream In](xstream-in.md)

### 10.1 About Managing XStream In

You can modify the database components that are part of an XStream In configuration, such as inbound servers.

The main interface for managing XStream In database components is PL/SQL. Specifically, use the following Oracle supplied PL/SQL packages to manage XStream In:

- `DBMS_XSTREAM_ADM`

  The `DBMS_XSTREAM_ADM` package is the main package for managing XStream In. This package includes subprograms that enable you to configure, modify, or drop inbound servers. This package also enables you modify the rules, rule sets, and rule-based transformations used by inbound servers.

  **See Also:**

  [Oracle Database PL/SQL Packages and Types Reference](../arpls/DBMS_XSTREAM_ADM.md) for detailed information about this package

- `DBMS_XSTREAM_AUTH`

  The `DBMS_XSTREAM_AUTH` package enables you to configure and modify XStream administrators.

  **See Also:**

  - "[Configure an XStream Administrator](configuring-xstream-in.md)" for information about using this package to create an XStream administrator

  - [Oracle Database PL/SQL Packages and Types Reference](../arpls/DBMS_XSTREAM_AUTH.md) for detailed information about this package

- `DBMS_APPLY_ADM`

  The `DBMS_APPLY_ADM` package enables you modify inbound servers.

  **See Also:**

  [Oracle Database PL/SQL Packages and Types Reference](../arpls/DBMS_APPLY_ADM.md) for detailed information about this package

**Parent topic:** Managing XStream In

### 10.2 Starting an Inbound Server

A inbound server must be enabled for it to receive logical change records (LCRs) from an XStream client application and apply the LCRs. You run the `START_APPLY` procedure in the `DBMS_APPLY_ADM` package to start an existing inbound server.

#### To start an inbound server:

1.  Connect to the inbound server database as the XStream administrator.

    See [Oracle Database Administrator’s Guide](../admin/index.md) for information about connecting to a database in SQL\*Plus.

2.  Run the `START_APPLY` procedure in the `DBMS_APPLY_ADM` package, and specify the inbound server for the `apply_name` parameter.

The following example starts an inbound server named `xin`.

Example 10-1 Starting an Outbound Server Named xout

    BEGIN
      DBMS_APPLY_ADM.START_APPLY(
        apply_name => 'xin');
    END;
    /

**See Also:**

The Oracle Enterprise Manager Cloud Control online help for instructions about starting an apply process or an inbound server with Oracle Enterprise Manager Cloud Control

**Parent topic:** Managing XStream In

### 10.3 Stopping an Inbound Server

You run the `STOP_APPLY` procedure in the `DBMS_APPLY_ADM` package to stop an existing inbound server. You might stop an inbound server when you are troubleshooting a problem in an XStream configuration.

#### To stop an inbound server:

1.  Connect to the inbound server database as the XStream administrator.

    See [Oracle Database Administrator’s Guide](../admin/index.md) for information about connecting to a database in SQL\*Plus.

2.  Run the `STOP_APPLY` procedure in the `DBMS_APPLY_ADM` package, and specify the inbound server for the `apply_name` parameter.

The following example stops an inbound server named `xin`.

Example 10-2 Stopping an Inbound Server Named xout

    BEGIN
      DBMS_APPLY_ADM.STOP_APPLY(
        apply_name => 'xin');
    END;
    /

**See Also:**

The Oracle Enterprise Manager Cloud Control online help for instructions about stopping an apply process or an inbound server with Oracle Enterprise Manager Cloud Control

**Parent topic:** Managing XStream In

### 10.4 Setting an Apply Parameter for an Inbound Server

Apply parameters control the way an inbound server operates. You set an apply parameter for an inbound server using the `SET_PARAMETER` procedure in the `DBMS_XSTREAM_ADM` package.

#### To set an inbound server apply parameter:

1.  Connect to the outbound server database as the XStream administrator.

    See [Oracle Database Administrator’s Guide](../admin/index.md) for information about connecting to a database in SQL\*Plus.

2.  Run the `SET_PARAMETER` procedure in the `DBMS_XSTREAM_ADM` package, and specify the following parameters:

    - `streams_name` - Specify the name of the inbound server.

    - `streams_type` - Specify `apply`.

    - `parameter` - Specify the name of the apply parameter.

    - `value` - Specify the value for the apply parameter.

The following example sets the `parallelism` parameter for an inbound server named `xin` to `4`.

Example 10-3 Setting an Outbound Server Parameter

    BEGIN
      DBMS_XSTREAM_ADM.SET_PARAMETER(
        streams_name => 'xin',
        streams_type => 'apply',
        parameter    => 'parallelism',
        value        => '4');
    END;
    /

**Note:**

- The `value` parameter is always entered as a `VARCHAR2` value, even if the parameter value is a number.

- If the `value` parameter is set to `NULL` or is not specified, then the parameter is set to its default value.

**See Also:**

- The Oracle Enterprise Manager Cloud Control online help for instructions about setting an apply parameter with Oracle Enterprise Manager Cloud Control

- [Oracle Database PL/SQL Packages and Types Reference](../arpls/DBMS_APPLY_ADM.md) for information about apply parameters

**Parent topic:** Managing XStream In

### 10.5 Changing the Apply User for an Inbound Server

An inbound server applies LCRs in the security domain of its apply user, and the client application must attach to the inbound server as the apply user. You can change the apply user for an inbound server with the `ALTER_INBOUND` procedure in the `DBMS_XSTREAM_ADM` package.

You can change the apply user when a client application must connect to an inbound server as a different user or when you want to apply changes using the privileges associated with a different user. Ensure that the apply user is granted the required privileges.

**See Also:**

[Oracle Database PL/SQL Packages and Types Reference](../arpls/DBMS_XSTREAM_ADM.md) for information about the privileges required by an apply user.

#### To change the apply user for an inbound server:

1.  Connect to the inbound server database as the XStream administrator.

    The XStream administrator must be granted the `DBA` role to change the apply user for an inbound server.

    See [Oracle Database Administrator’s Guide](../admin/index.md) for information about connecting to a database in SQL\*Plus.

2.  Run the `ALTER_INBOUND` procedure in the `DBMS_XSTREAM_ADM` package, and specify the following parameters:

    - `server_name` - Specify the name of the inbound server.

    - `apply_user` - Specify the new apply user.

Example 10-4 Changing the Apply User for an Inbound Server

To change the apply user to `hr` for an inbound server named `xin`, run the following procedure:

    BEGIN
      DBMS_XSTREAM_ADM.ALTER_INBOUND(
        server_name => 'xin',
        apply_user  => 'hr');
    END;
    /

**See Also:**

- "[XStream In and Security](xstream-in-concepts.md)"

- [Oracle Database PL/SQL Packages and Types Reference](../arpls/DBMS_XSTREAM_ADM.md)

**Parent topic:** Managing XStream In

### 10.6 Managing XStream In Conflict Detection and Resolution

When more than one client modifies the same table row at approximately the same time, conflicts are possible. XStream In detects conflicts and provides methods for resolving conflicts.

- About DML Conflicts in an XStream Environment
  A conflict is a mismatch between the old values in an LCR and the data in a table.
- Conflict Types in an XStream Environment
  You can encounter several different types of conflicts when you share data at multiple databases.
- Conflicts and Transaction Ordering in an XStream Environment
  Ordering conflicts can occur in an XStream environment when three or more databases share data and the data is updated at two or more of these databases.
- Conflict Detection in an XStream Environment
  An inbound server detects conflicts automatically.
- Conflict Avoidance in an XStream Environment
  There are several ways to avoid data conflicts.
- Conflict Resolution in an XStream Environment
  After an update conflict has been detected, a conflict handler can attempt to resolve it.
- Managing DML Conflict Handlers
  You can set and remove a DML conflict handler. To modify an existing DML conflict handler, you must remove it and reset it.
- Stopping Conflict Detection for Non-Key Columns
  You can stop conflict detection for non-key columns by using the `COMPARE_OLD_VALUES` procedure in the `DBMS_APPLY_ADM` package.

**Parent topic:** Managing XStream In

#### 10.6.1 About DML Conflicts in an XStream Environment

A conflict is a mismatch between the old values in an LCR and the data in a table.

Conflicts can occur in an XStream environment that permits concurrent data manipulation language (DML) operations on the same data at multiple databases. In an XStream environment, DML conflicts can occur only when an inbound server is applying a row LCR that contains a row change resulting from a DML operation. An inbound server automatically detects conflicts caused by row LCRs.

For example, when two transactions originating at different databases update the same row at nearly the same time, a conflict can occur. When you configure an XStream environment, you must consider whether conflicts can occur. You can configure conflict resolution to resolve conflicts automatically, if your system design permits conflicts.

In general, it is best practice to design an XStream environment that avoids the possibility of conflicts. Using the conflict avoidance techniques discussed later in this chapter, most system designs can avoid conflicts in all or a large percentage of the shared data. However, many applications require that some percentage of the shared data be updatable at multiple databases at any time. If this is the case, then you must address the possibility of conflicts.

**Note:**

An inbound server does not detect DDL conflicts. Ensure that your environment avoids these types of conflicts.

**Related Topics**

- [Row LCRs](general-xstream-concepts.md)

**Parent topic:** Managing XStream In Conflict Detection and Resolution

#### 10.6.2 Conflict Types in an XStream Environment

You can encounter several different types of conflicts when you share data at multiple databases.

- Update Conflicts in an XStream Environment
  An **update conflict** occurs when an inbound server applies a row LCR containing an update to a row that conflicts with another update to the same row.
- Uniqueness Conflicts in an XStream Environment
  A **uniqueness conflict** occurs when an inbound server applies a row LCR containing a change to a row that violates a uniqueness integrity constraint, such as a `PRIMARY` `KEY` or `UNIQUE` constraint.
- Delete Conflicts in an XStream Environment
  A **delete conflict** occurs when two transactions originate at different databases, with one transaction deleting a row and another transaction updating or deleting the same row.
- Foreign Key Conflicts in an XStream Environment
  A **foreign key conflict** occurs when an inbound server applies a row LCR containing a change to a row that violates a foreign key constraint.

**Parent topic:** Managing XStream In Conflict Detection and Resolution

##### 10.6.2.1 Update Conflicts in an XStream Environment

An **update conflict** occurs when an inbound server applies a row LCR containing an update to a row that conflicts with another update to the same row.

Update conflicts can happen when two transactions originating from different databases update the same row at nearly the same time.

**Parent topic:** Conflict Types in an XStream Environment

##### 10.6.2.2 Uniqueness Conflicts in an XStream Environment

A **uniqueness conflict** occurs when an inbound server applies a row LCR containing a change to a row that violates a uniqueness integrity constraint, such as a `PRIMARY` `KEY` or `UNIQUE` constraint.

For example, consider what happens when two transactions originate from two different databases, each inserting a row into a table with the same primary key value. In this case, the transactions cause a uniqueness conflict.

**Parent topic:** Conflict Types in an XStream Environment

##### 10.6.2.3 Delete Conflicts in an XStream Environment

A **delete conflict** occurs when two transactions originate at different databases, with one transaction deleting a row and another transaction updating or deleting the same row.

In this case, the row referenced in the row LCR does not exist and therefore cannot be updated or deleted.

**Parent topic:** Conflict Types in an XStream Environment

##### 10.6.2.4 Foreign Key Conflicts in an XStream Environment

A **foreign key conflict** occurs when an inbound server applies a row LCR containing a change to a row that violates a foreign key constraint.

For example, in the `hr` schema, the `department_id` column in the `employees` table is a foreign key of the `department_id` column in the `departments` table. Consider what can happen when the following changes originate at two different databases (`A` and `B`) and are propagated to a third database (`C`):

- At database `A`, a row is inserted into the `departments` table with a `department_id` of `271`. This change is propagated to database `B` and applied there.

- At database `B`, a row is inserted into the `employees` table with an `employee_id` of `206` and a `department_id` of `271`.

If the change that originated at database `B` is applied at database `C` before the change that originated at database `A`, then a foreign key conflict results because the row for the department with a `department_id` of `271` does not yet exist in the `departments` table at database `C`.

**Parent topic:** Conflict Types in an XStream Environment

#### 10.6.3 Conflicts and Transaction Ordering in an XStream Environment

Ordering conflicts can occur in an XStream environment when three or more databases share data and the data is updated at two or more of these databases.

For example, consider a scenario in which three databases share information in the `hr.departments` table. The database names are `mult1.example.com`, `mult2.example.com`, and `mult3.example.com`. Suppose a change is made to a row in the `hr.departments` table at `mult1.example.com` that will be propagated to both `mult2.example.com` and `mult3.example.com`. The following series of actions might occur:

1.  The change is propagated to `mult2.example.com`.

2.  An inbound server at `mult2.example.com` applies the change from `mult1.example.com`.

3.  A different change to the same row is made at `mult2.example.com`.

4.  The change at `mult2.example.com` is propagated to `mult3.example.com`.

5.  An inbound server at `mult3.example.com` attempts to apply the change from `mult2.example.com` before another inbound server at `mult3.example.com` applies the change from `mult1.example.com`.

In this case, a conflict occurs because a column value for the row at `mult3.example.com` does not match the corresponding old value in the row LCR propagated from `mult2.example.com`.

In addition to causing a data conflict, transactions that are applied out of order might experience referential integrity problems at a remote database if supporting data has not been successfully propagated to that database. Consider the scenario where a new customer calls an order department. A customer record is created and an order is placed. If the order data is applied at a remote database before the customer data, then a referential integrity error is raised because the customer that the order references does not exist at the remote database.

If an ordering conflict is encountered, then you can resolve the conflict by reexecuting the transaction in the error queue after the required data has been propagated to the remote database and applied.

**Parent topic:** Managing XStream In Conflict Detection and Resolution

#### 10.6.4 Conflict Detection in an XStream Environment

An inbound server detects conflicts automatically.

- About Conflict Detection in an XStream Environment
  An inbound server detects update, uniqueness, delete, and foreign key conflicts.
- Control Over Conflict Detection for Non-Key Columns
  By default, an inbound server compares old values for all columns during conflict detection, but you can stop conflict detection for non-key columns using the `COMPARE_OLD_VALUES` procedure in the `DBMS_APPLY_ADM` package.
- Rows Identification During Conflict Detection in an XStream Environment
  To detect conflicts accurately, Oracle Database must be able to identify and match corresponding rows at different databases uniquely.

**Parent topic:** Managing XStream In Conflict Detection and Resolution

##### 10.6.4.1 About Conflict Detection in an XStream Environment

An inbound server detects update, uniqueness, delete, and foreign key conflicts.

An inbound server detects these conflicts as follows:

- An inbound server detects an update conflict if there is any difference between the old values for a row in a row LCR and the current values of the same row at the destination database.

- An inbound server detects a uniqueness conflict if a uniqueness constraint violation occurs when applying an LCR that contains an insert or update operation.

- An inbound server detects a delete conflict if it cannot find a row when applying an LCR that contains an update or delete operation, because the primary key of the row does not exist.

- An inbound server detects a foreign key conflict if a foreign key constraint violation occurs when applying an LCR.

A conflict can be detected when an inbound server attempts to apply an LCR directly or when an inbound server handler, such as a DML conflict handler, runs the `EXECUTE` member procedure for an LCR. A conflict can also be detected when either the `EXECUTE_ERROR` or `EXECUTE_ALL_ERRORS` procedure in the `DBMS_APPLY_ADM` package is run.

**Note:**

- If a column is updated and the column's old value equals its new value, then Oracle Database never detects a conflict for this column update.

- Any old LOB values in update LCRs, delete LCRs, and LCRs dealing with piecewise updates to LOB columns are not used by conflict detection.

**Parent topic:** Conflict Detection in an XStream Environment

##### 10.6.4.2 Control Over Conflict Detection for Non-Key Columns

By default, an inbound server compares old values for all columns during conflict detection, but you can stop conflict detection for non-key columns using the `COMPARE_OLD_VALUES` procedure in the `DBMS_APPLY_ADM` package.

Conflict detection might not be needed for some non-key columns.

**See Also:**

"Stopping Conflict Detection for Non-Key Columns"

**Parent topic:** Conflict Detection in an XStream Environment

##### 10.6.4.3 Rows Identification During Conflict Detection in an XStream Environment

To detect conflicts accurately, Oracle Database must be able to identify and match corresponding rows at different databases uniquely.

By default, Oracle Database uses the primary key of a table to identify rows in a table uniquely. When a table does not have a primary key, it is best practice to designate a substitute key. A substitute key is a column or set of columns that Oracle Database can use to identify uniquely rows in the table.

**Parent topic:** Conflict Detection in an XStream Environment

#### 10.6.5 Conflict Avoidance in an XStream Environment

There are several ways to avoid data conflicts.

- Use a Primary Database Ownership Model
  You can avoid the possibility of conflicts by limiting the number of databases that have simultaneous update access to the tables containing shared data.
- Avoid Specific Types of Conflicts
  If a primary database ownership model is too restrictive for your application requirements, then you can use a shared ownership data model, which means that conflicts might be possible. Even so, typically you can use some simple strategies to avoid specific types of conflicts.

**Parent topic:** Managing XStream In Conflict Detection and Resolution

##### 10.6.5.1 Use a Primary Database Ownership Model

You can avoid the possibility of conflicts by limiting the number of databases that have simultaneous update access to the tables containing shared data.

Primary ownership prevents all conflicts, because only a single database permits updates to a set of shared data. Applications can even use row and column subsetting to establish more granular ownership of data than at the table level. For example, applications might have update access to specific columns or rows in a shared table on a database-by-database basis.

**Parent topic:** Conflict Avoidance in an XStream Environment

##### 10.6.5.2 Avoid Specific Types of Conflicts

If a primary database ownership model is too restrictive for your application requirements, then you can use a shared ownership data model, which means that conflicts might be possible. Even so, typically you can use some simple strategies to avoid specific types of conflicts.

- Avoid Uniqueness Conflicts in an XStream Environment
  You can avoid uniqueness conflicts by ensuring that each database uses unique identifiers for shared data.
- Avoid Delete Conflicts in an Oracle Replication Environment
  Always avoid delete conflicts in shared data environments.
- Avoid Update Conflicts in an XStream Environment
  After trying to eliminate the possibility of uniqueness and delete conflicts, you should also try to limit the number of possible update conflicts.

**Parent topic:** Conflict Avoidance in an XStream Environment

###### 10.6.5.2.1 Avoid Uniqueness Conflicts in an XStream Environment

You can avoid uniqueness conflicts by ensuring that each database uses unique identifiers for shared data.

There are three ways to ensure unique identifiers at all databases in an XStream environment.

- One way is to construct a unique identifier by executing the following select statement:

      SELECT SYS_GUID() OID FROM DUAL;

  This SQL operator returns a 16-byte globally unique identifier. The globally unique identifier appears in a format similar to the following:

      A741C791252B3EA0E034080020AE3E0A

- Another way to avoid uniqueness conflicts is to create a sequence at each of the databases that shares data and concatenate the database name (or other globally unique value) with the local sequence. This approach helps to avoid any duplicate sequence values and helps to prevent uniqueness conflicts.

- Finally, you can create a customized sequence at each of the databases that shares data so that no two databases can generate the same value. You can accomplish this by using a combination of starting, incrementing, and maximum values in the `CREATE` `SEQUENCE` statement. For example, you might configure the following sequences:

  Table 10-1 Customized Sequences

  | Parameter        | Database A            | Database B            | Database C            |
  |:-----------------|:----------------------|:----------------------|:----------------------|
  | `START` `WITH`   | 1                     | 3                     | 5                     |
  | `INCREMENT` `BY` | 10                    | 10                    | 10                    |
  | Range Example    | 1, 11, 21, 31, 41,... | 3, 13, 23, 33, 43,... | 5, 15, 25, 35, 45,... |

  Using a similar approach, you can define different ranges for each database by specifying a `START` `WITH` and `MAXVALUE` that would produce a unique range for each database.

**Parent topic:** Avoid Specific Types of Conflicts

###### 10.6.5.2.2 Avoid Delete Conflicts in an Oracle Replication Environment

Always avoid delete conflicts in shared data environments.

In general, it is best practice for applications that operate within a shared ownership data model to avoid deleting rows using `DELETE` statements. Instead, applications can mark rows for deletion and then configure the system to purge logically deleted rows periodically.

**Parent topic:** Avoid Specific Types of Conflicts

###### 10.6.5.2.3 Avoid Update Conflicts in an XStream Environment

After trying to eliminate the possibility of uniqueness and delete conflicts, you should also try to limit the number of possible update conflicts.

However, in a shared ownership data model, update conflicts cannot be avoided in all cases. If you cannot avoid all update conflicts, then you must understand the types of conflicts possible and configure the system to resolve them if they occur.

**Parent topic:** Avoid Specific Types of Conflicts

#### 10.6.6 Conflict Resolution in an XStream Environment

After an update conflict has been detected, a conflict handler can attempt to resolve it.

- About Conflict Resolution in an XStream Environment
  XStream provides prebuilt conflict handlers to resolve insert and update conflicts.
- Prebuilt DML Conflict Handlers
  There are several types of prebuilt DML conflict handlers available. Column lists and resolution columns are used in prebuilt DML conflict handlers.
- Types of Prebuilt DML Conflict Handlers
  Oracle provides the following types of prebuilt DML conflict handlers for an Oracle Replication environment: `RECORD`, `IGNORE`, `OVERWRITE`, `MAXIMUM`, `MINIMUM`, and `DELTA`.
- Column Lists
  Each time you specify a prebuilt DML conflict handler for a table, you must specify a column list.
- Resolution Columns
  The resolution column is the column used to identify a prebuilt DML conflict handler.
- Data Convergence
  When you share data between multiple databases, and you want the data to be the same at all of these databases, ensure that you use conflict resolution handlers that cause the data to converge at all databases.
- Collision Handling Without a DML Conflict Handler
  In the absence of a DML conflict handler for a table, you can enable basic collision handling using the `HANDLE_COLLISIONS` procedure in the `DBMS_APPLY_ADM` package.
- Custom Conflict Handlers
  You can create a PL/SQL procedure to use as a custom conflict handler.

**Parent topic:** Managing XStream In Conflict Detection and Resolution

##### 10.6.6.1 About Conflict Resolution in an XStream Environment

XStream provides prebuilt conflict handlers to resolve insert and update conflicts.

There are no prebuilt conflict handlers for delete, foreign key, or ordering conflicts. However, you can build your own custom conflict handler to resolve data conflicts specific to your business rules. Such a conflict handler can be part of a procedure DML handler or an error handler.

Whether you use prebuilt or custom conflict handlers, a conflict handler is applied as soon as a conflict is detected. If neither the specified conflict handler nor the relevant apply handler can resolve the conflict, then the conflict is logged in the error queue. You might want to use the relevant apply handler to notify the database administrator when a conflict occurs.

When a conflict causes a transaction to be moved to the error queue, sometimes it is possible to correct the condition that caused the conflict. In these cases, you can reexecute a transaction using the `EXECUTE_ERROR` procedure in the `DBMS_APPLY_ADM` package.

**See Also:**

[Oracle Database PL/SQL Packages and Types Reference](../arpls/DBMS_APPLY_ADM.md)for more information about the `EXECUTE_ERROR` procedure in the `DBMS_APPLY_ADM` package

**Parent topic:** Conflict Resolution in an XStream Environment

##### 10.6.6.2 Prebuilt DML Conflict Handlers

There are several types of prebuilt DML conflict handlers available. Column lists and resolution columns are used in prebuilt DML conflict handlers.

A column list is a list of columns for which the DML conflict handler is called when there is an insert or update conflict. The resolution column identifies a DML conflict handler. If you use a `MAXIMUM` or `MINIMUM` prebuilt DML conflict handler, then the resolution column is also the column used to resolve the conflict. The resolution column must be one of the columns in the column list for the handler.

Use the `SET_DML_CONFLICT_HANDLER` procedure in the `DBMS_APPLY_ADM` package to specify one or more DML conflict handlers for a particular table. There are no prebuilt DML conflict handlers for delete or foreign key conflicts.

**See Also:**

- "Managing DML Conflict Handlers" for instructions on setting and removing an DML conflict handler

- [Oracle Database PL/SQL Packages and Types Reference](../arpls/DBMS_APPLY_ADM.md) for more information about the `SET_DML_CONFLICT_HANDLER` procedure

- "Column Lists"

- "Resolution Columns"

**Parent topic:** Conflict Resolution in an XStream Environment

##### 10.6.6.3 Types of Prebuilt DML Conflict Handlers

Oracle provides the following types of prebuilt DML conflict handlers for an Oracle Replication environment: `RECORD`, `IGNORE`, `OVERWRITE`, `MAXIMUM`, `MINIMUM`, and `DELTA`.

The description for each type of handler later in this topic refers to the following conflict scenario:

1.  The following update is made at the `dbs1.example.com` source database:

        UPDATE hr.employees SET salary = 4900 WHERE employee_id = 200;
        COMMIT;

    This update changes the salary for employee `200` from `4400` to `4900`.

2.  At nearly the same time, the following update is made at the `dbs2.example.com` destination database:

        UPDATE hr.employees SET salary = 5000 WHERE employee_id = 200;
        COMMIT;

3.  A capture process captures the update at the `dbs1.example.com` source database and puts the resulting row LCR in a queue.

4.  A propagation propagates the row LCR from the queue at `dbs1.example.com` to a queue at `dbs2.example.com`.

5.  An apply process at `dbs2.example.com` attempts to apply the row LCR to the `hr.employees` table but encounters a conflict because the salary value at `dbs2.example.com` is `5000`, which does not match the old value for the salary in the row LCR (`4400`).

The following sections describe each prebuilt conflict handler and explain how the handler resolves this conflict.

##### RECORD

When a conflict occurs, the `RECORD` handler places the LCR into the error queue. The `RECORD` handler can be used for all conflict types, but it can only be specified for a column group that contains all the columns in the table.

If the `RECORD` handler is used for the `hr.employees` table at the `dbs2.example.com` destination database in the conflict example, then the row LCR from `dbs1.example.com` is placed in the error queue at `dbs1.example.com`, and its changes are not applied. Therefore, after the conflict is resolved, the salary for employee `200` is `5000` at `dbs2.example.com`.

##### IGNORE

When a conflict occurs, the `IGNORE` handler ignores the values in the LCR from the source database and retains the value at the destination database.

If the `IGNORE` handler is used for the `hr.employees` table at the `dbs2.example.com` destination database in the conflict example, then the new value in the row LCR is discarded. Therefore, after the conflict is resolved, the salary for employee `200` is `5000` at `dbs2.example.com`.

##### OVERWRITE

When a conflict occurs, the `OVERWRITE` handler replaces the current value at the destination database with the new value in the LCR from the source database.

If the `OVERWRITE` handler is used for the `hr.employees` table at the `dbs2.example.com` destination database in the conflict example, then the new value in the row LCR overwrites the value at `dbs2.example.com`. Therefore, after the conflict is resolved, the salary for employee `200` is `4900`.

##### MAXIMUM

When a conflict occurs, the `MAXIMUM` conflict handler compares the new value in the LCR from the source database with the current value in the destination database for a designated resolution column. If the new value of the resolution column in the LCR is greater than the current value of the column at the destination database, then the apply process resolves the conflict in favor of the LCR. If the new value of the resolution column in the LCR is less than the current value of the column at the destination database, then the apply process resolves the conflict in favor of the destination database.

If the `MAXIMUM` handler is used for the `salary` column in the `hr.employees` table at the `dbs2.example.com` destination database in the conflict example, then the apply process does not apply the row LCR, because the salary in the row LCR is less than the current salary in the table. Therefore, after the conflict is resolved, the salary for employee `200` is `5000` at `dbs2.example.com`.

If you want to resolve conflicts based on the time of the transactions involved, then one way to do this is to add a column to a shared table that automatically records the transaction time with a trigger. You can designate this column as a resolution column for a `MAXIMUM` conflict handler, and the transaction with the latest (or greater) time would be used automatically.

The following is an example of a trigger that records the time of a transaction for the `hr.employees` table. Assume that the `job_id`, `salary`, and `commission_pct` columns are part of the column list for the conflict resolution handler. The trigger should fire only when an `UPDATE` is performed on the columns in the column list or when an `INSERT` is performed.

    ALTER TABLE hr.employees ADD (time TIMESTAMP WITH TIME ZONE);

    CREATE OR REPLACE TRIGGER hr.insert_time_employees
    BEFORE
      INSERT OR UPDATE OF job_id, salary, commission_pct ON hr.employees
    FOR EACH ROW
    BEGIN
       -- Consider time synchronization problems. The previous update to this
       -- row might have originated from a site with a clock time ahead of the
       -- local clock time.
       IF :OLD.TIME IS NULL OR :OLD.TIME < SYSTIMESTAMP THEN
         :NEW.TIME := SYSTIMESTAMP;
       ELSE
         :NEW.TIME := :OLD.TIME + 1 / 86400;
       END IF;
    END;
    /

If you use such a trigger for conflict resolution, then ensure that the trigger's firing property is “fire once,” which is the default. Otherwise, a new time might be marked when transactions are applied by an apply process, resulting in the loss of the actual time of the transaction.

##### MINIMUM

When a conflict occurs, the `MINIMUM` conflict handler compares the new value in the LCR from the source database with the current value in the destination database for a designated resolution column. If the new value of the resolution column in the LCR is less than the current value of the column at the destination database, then the apply process resolves the conflict in favor of the LCR. If the new value of the resolution column in the LCR is greater than the current value of the column at the destination database, then the apply process resolves the conflict in favor of the destination database.

If the `MINIMUM` handler is used for the `salary` column in the `hr.employees` table at the `dbs2.example.com` destination database in the conflict example, then the apply process resolves the conflict in favor of the row LCR, because the salary in the row LCR is less than the current salary in the table. Therefore, after the conflict is resolved, the salary for employee `200` is `4900`.

##### DELTA

When a conflict occurs, the `DELTA` conflict handler calculates the difference between the old value for the column and the new value for the column and adds the difference to the current value of the column. The `DELTA` conflict handler can only be used when the `conflict_type` is set to `ROW_EXISTS` and all of the columns in the column group are numbers.

If the `DELTA` handler is used for the `salary` column in the `hr.employees` table at the `dbs2.example.com` destination database in the conflict example, then the apply process resolves the conflict by calculating the difference between the old value for the column and the new value for the column (4900 – 4400 = 500) and adding it to the current value of the column (5000 + 500 = 5500). Therefore, after the conflict is resolved, the salary for employee `200` is `5500`.

##### MAX_AND_EQUALS

When a conflict occurs, apply the column list from in the LCR if the value of resolution column is greater than or equal to the value of the column in the database. Otherwise, discard the LCR.

If the `MAX_AND_EQUALS` handler is used for the `salary` column in the `hr.employees` table at the `dbs2.example.com` destination database in the conflict example, then the apply process resolves the conflict by discarding the LCR. Therefore, after the conflict is resolved, the salary for employee `200` is `5000`.

##### MIN_AND_EQUALS

When a conflict occurs, apply the column list from the LCR if the value of resolution column is less than or equal to the value of the column in the database. Otherwise, discard the LCR.

If the `MIN_AND_EQUALS` handler is used for the `salary` column in the `hr.employees` table at the `dbs2.example.com` destination database in the conflict example, then the apply process resolves the conflict by applying the LCR. Therefore, after the conflict is resolved, the salary for employee `200` is `4900`.

**Parent topic:** Conflict Resolution in an XStream Environment

##### 10.6.6.4 Column Lists

Each time you specify a prebuilt DML conflict handler for a table, you must specify a column list.

A column list is a list of columns for which the DML conflict handler is called. If an update conflict occurs for one or more of the columns in the list when an inbound server tries to apply a row LCR, then the DML conflict handler is called to resolve the conflict. The DML conflict handler is not called if a conflict occurs only in columns that are not in the list. The scope of conflict resolution is a single column list on a single row LCR.

You can specify multiple DML conflict handlers for a particular table, but the same column cannot be in more than one column list. For example, suppose you specify two prebuilt DML conflict handlers on `hr.employees` table:

- The first DML conflict handler has the following columns in its column list: `salary` and `commission_pct`.

- The second DML conflict handler has the following columns in its column list: `job_id` and `department_id`.

Also, assume that no other conflict handlers exist for this table. In this case, the following examples illustrate the outcomes for different scenarios:

- If a conflict occurs for the `salary` column when an inbound server tries to apply a row LCR, then the first DML conflict handler is called to resolve the conflict.

- If a conflict occurs for the `department_id` column, then the second DML conflict handler is called to resolve the conflict.

- If a conflict occurs for a column that is not in a column list for any conflict handler, then no conflict handler is called, and an error results. For instance, if a conflict occurs for the `manager_id` column in the `hr.employees` table, then an error results.

- If conflicts occur in more than one column list when a row LCR is being applied, and there are no conflicts in any columns that are not in a column list, then the appropriate DML conflict handler is invoked for each column list with a conflict.

Column lists enable you to use different handlers to resolve conflicts for different types of data. For example, numeric data is often suited for a maximum or minimum conflict handler, while an overwrite or discard conflict handler might be preferred for character data.

If a conflict occurs in a column that is not in a column list, then the error handler for the specific operation on the table attempts to resolve the conflict. If the error handler cannot resolve the conflict, or if there is no such error handler, then the transaction that caused the conflict is moved to the error queue.

Also, if a conflict occurs for a column in a column list that uses either the `OVERWRITE`, `MAXIMUM`, or `MINIMUM` prebuilt handler, and if the row LCR does not contain all of the columns in this column list, then the conflict cannot be resolved because all of the values are not available. In this case, the transaction that caused the conflict is moved to the error queue. If the column list uses the `DISCARD` prebuilt method, then the row LCR is discarded and no error results, even if the row LCR does not contain all of the columns in this column list.

If more than one column at the source database affects the column list at the destination database, then a conditional supplemental log group must be specified for the columns specified in a column list. Supplemental logging is specified at the source database and adds additional information to the LCR, which is needed to resolve conflicts properly. Typically, a conditional supplemental log group must be specified for the columns in a column list if there are multiple columns in the column list, but not if there is only one column in the column list.

However, in some cases, a conditional supplemental log group is required even if there is only one column in a column list. That is, an apply handler or custom rule-based transformation can combine multiple columns from the source database into a single column in the column list at the destination database. For example, a custom rule-based transformation can take three columns that store street, state, and postal code data from a source database and combine the data into a single address column at a destination database.

Also, in some cases, no conditional supplemental log group is required even if there are multiple columns in a column list. For example, an apply handler or custom rule-based transformation can separate one address column from the source database into multiple columns that are in a column list at the destination database. A custom rule-based transformation can take an address that includes street, state, and postal code data in one address column at a source database and separate the data into three columns at a destination database.

**Note:**

Prebuilt DML conflict handlers do not support LOB, `LONG`, `LONG` `RAW`, user-defined type, and Oracle-supplied type columns. Therefore, you should not include these types of columns in the `column_list` parameter when running the `SET_DML_CONFLICT_HANDLER` procedure.

**See Also:**

- "[If Required, Specify Supplemental Logging at the Source Database](configuring-xstream-in.md)"

- [Oracle Database SQL Language Reference](../sqlrf/Data-Types.md) for information about data types

**Parent topic:** Conflict Resolution in an XStream Environment

##### 10.6.6.5 Resolution Columns

The resolution column is the column used to identify a prebuilt DML conflict handler.

If you use a `MAXIMUM` or `MINIMUM` prebuilt DML conflict handler, then the resolution column is also the column used to resolve the conflict. The resolution column must be one of the columns in the column list for the handler.

For example, if the `salary` column in the `hr.employees` table is specified as the resolution column for a maximum or minimum conflict handler, then the `salary` column is evaluated to determine whether column list values in the row LCR are applied or the destination database values for the column list are retained.

In either of the following situations involving a resolution column for a conflict, the apply process moves the transaction containing the row LCR that caused the conflict to the error queue, if the error handler cannot resolve the problem. In these cases, the conflict cannot be resolved and the values of the columns at the destination database remain unchanged:

- The new LCR value and the destination row value for the resolution column are the same (for example, if the resolution column was not the column causing the conflict).

- Either the new LCR value of the resolution column or the current value of the resolution column at the destination database is `NULL`.

**Note:**

Although the resolution column is not used for `OVERWRITE` and `DISCARD` conflict handlers, you must specify a resolution column for these conflict handlers.

**Parent topic:** Conflict Resolution in an XStream Environment

##### 10.6.6.6 Data Convergence

When you share data between multiple databases, and you want the data to be the same at all of these databases, ensure that you use conflict resolution handlers that cause the data to converge at all databases.

If you allow changes to shared data at all of your databases, then data convergence for a table is possible only if all databases that are sharing data capture changes to the shared data and propagate these changes to all of the other databases that are sharing the data.

In such an environment, the `MAXIMUM` conflict resolution method can guarantee convergence only if the values in the resolution column are always increasing. If successive time stamps on a row are distinct, then a time-based resolution column meets this requirement. The `MINIMUM` conflict resolution method can guarantee convergence in such an environment only if the values in the resolution column are always decreasing.

**Parent topic:** Conflict Resolution in an XStream Environment

##### 10.6.6.7 Collision Handling Without a DML Conflict Handler

In the absence of a DML conflict handler for a table, you can enable basic collision handling using the `HANDLE_COLLISIONS` procedure in the `DBMS_APPLY_ADM` package.

When you enable basic collision handling for an inbound server and a table, conflicts are resolved in the following ways:

- When a conflict is detected for a row that exists in the table, the data in the row LCR overwrites the data in the table.

  For example, if a row LCR contains an insert, but the row already exists in the table. The data in the row LCR overwrites the existing data in the table. If a row LCR contains an update, and an old value in the row does not match an old value in the row LCR, the data in the row LCR overwrites the data in the table.

- When a conflict is detected for a row that does not exist in the table, the data in the row LCR is ignored.

  For example, if a row LCR contains an update to a row, but the row does not exist in the table, the row LCR is ignored.

Example 10-5 Enabling Basic Collision Handling for a Table

This example enables basic collision handling for the `app_emp` inbound server and the `hr.employees` table.

    BEGIN
      DBMS_APPLY_ADM.HANDLE_COLLISIONS(
        apply_name => 'app_emp',
        enable     => TRUE,
        object     => 'hr.employees');
    END;
    /

To disable basic collision handling for this table, run the same procedure, but set the `enable` parameter to `FALSE`.

**Parent topic:** Conflict Resolution in an XStream Environment

##### 10.6.6.8 Custom Conflict Handlers

You can create a PL/SQL procedure to use as a custom conflict handler.

You use the `SET_DML_HANDLER` procedure in the `DBMS_APPLY_ADM` package to designate one or more custom conflict handlers for a particular table. Specifically, set the following parameters when you run this procedure to specify a custom conflict handler:

- Set the `object_name` parameter to the fully qualified name of the table for which you want to perform conflict resolution.

- Set the `object_type` parameter to `TABLE`.

- Set the `operation_name` parameter to the type of operation for which the custom conflict handler is called. The possible operations are the following: `INSERT`, `UPDATE`, `DELETE`, and `LOB_UPDATE`. You can also set the `operation_name` parameter to `DEFAULT` so that the handler is the default handler for all operations.

- If you want an error handler to perform conflict resolution when an error is raised, then set the `error_handler` parameter to `TRUE`. Or, if you want to include conflict resolution in your procedure DML handler, then set the `error_handler` parameter to `FALSE`.

  If you specify `FALSE` for this parameter, then, when you execute a row LCR using the `EXECUTE` member procedure for the LCR, the conflict resolution within the procedure DML handler is performed for the specified object and operation(s).

- Specify the procedure to resolve a conflict by setting the `user_procedure` parameter. This user procedure is called to resolve any conflicts on the specified table resulting from the specified type of operation.

If the custom conflict handler cannot resolve the conflict, then the inbound server moves the transaction containing the conflict to the error queue and does not apply the transaction.

If both a prebuilt DML conflict handler and a custom conflict handler exist for a particular object, then the prebuilt DML conflict handler is invoked only if both of the following conditions are met:

- The custom conflict handler executes the row LCR using the `EXECUTE` member procedure for the LCR.

- The `conflict_resolution` parameter in the `EXECUTE` member procedure for the row LCR is set to `TRUE`.

**See Also:**

[Oracle Database PL/SQL Packages and Types Reference](../arpls/DBMS_APPLY_ADM.md)for more information about the `SET_DML_HANDLER` procedure

**Parent topic:** Conflict Resolution in an XStream Environment

#### 10.6.7 Managing DML Conflict Handlers

You can set and remove a DML conflict handler. To modify an existing DML conflict handler, you must remove it and reset it.

- Setting a DML Conflict Handler
  Set a DML conflict handler using the `SET_DML_CONFLICT_HANDLER` procedure in the `DBMS_APPLY_ADM` package.
- Removing a DML Conflict Handler
  You can remove an existing DML conflict handler by running the `SET_DML_CONFLICT_HANDLER` procedure in the `DBMS_APPLY_ADM` package.

**Parent topic:** Managing XStream In Conflict Detection and Resolution

##### 10.6.7.1 Setting a DML Conflict Handler

Set a DML conflict handler using the `SET_DML_CONFLICT_HANDLER` procedure in the `DBMS_APPLY_ADM` package.

You can use one of the following prebuilt methods when you create a DML conflict resolution handler:

- `RECORD`

- `IGNORE`

- `OVERWRITE`

- `MAXIMUM`

- `MINIMUM`

- `DELTA`

- `MAX_AND_EQUALS`

- `MIN_AND_EQUALS`

To set a DML conflict handler:

1.  Connect to the inbound server database as the XStream administrator.
2.  Run the `SET_DML_CONFLICT_HANDLER` procedure in the `DBMS_APPLY_ADM` package.

Example 10-6 Setting DML Conflict Handlers

Suppose an XStream In client receives changes to be applied to the `hr.jobs` table at `dbs1.example.com`. In this environment, conflicts can occur because the changes from the external database that the client receives may not be coordinated with the changes to the target database `dbs1.example.com`. If there is a conflict for a particular DML insert or update, then the change from the external database must always overwrite the change at the target database. In this environment, you can accomplish this goal by specifying an `OVERWRITE` handler at the `dbs1.example.com` database. If there is a conflict because the row for a DML delete does not exist, then the row LCR is ignored.

This example specifies DML conflict handlers for the `hr.jobs` table at the `dbs1.example.com` database.

    DECLARE
      cols DBMS_UTILITY.LNAME_ARRAY;
      BEGIN
        cols(1) := 'job_title';
        cols(2) := 'min_salary';
        cols(3) := 'max_salary';
        DBMS_APPLY_ADM.SET_DML_CONFLICT_HANDLER(
          apply_name            => 'app_jobs',
          conflict_handler_name => 'jobs_handler_insert',
          object                => 'hr.jobs',
          operation_name        => 'INSERT',
          conflict_type         => 'ROW_EXISTS',
          method_name           => 'OVERWRITE',
          column_table          => cols);
        DBMS_APPLY_ADM.SET_DML_CONFLICT_HANDLER(
          apply_name            => 'app_jobs',
          conflict_handler_name => 'jobs_handler_update',
          object                => 'hr.jobs',
          operation_name        => 'UPDATE',
          conflict_type         => 'ROW_EXISTS',
          method_name           => 'OVERWRITE',
          column_table          => cols);
        DBMS_APPLY_ADM.SET_DML_CONFLICT_HANDLER(
          apply_name            => 'app_jobs',
          conflict_handler_name => 'jobs_handler_delete',
          object                => 'hr.jobs',
          operation_name        => 'DELETE',
          conflict_type         => 'ROW_MISSING',
          method_name           => 'IGNORE',
          column_list           => '*');
    END;
    /

The apply process `app_jobs` uses the specified DML conflict handlers.

**Note:**

- For the `jobs_handler_delete` DML conflict handler, the `column_list` parameter is set to `'*'` because all columns must be specified when the `operation_name` is set to `DELETE`.

- If the client is obtaining data from an Oracle database using XStream Out, then you must specify a conditional supplemental log group at the source database for all of the columns in the `column_list` at the destination database. In this example, you would specify a conditional supplemental log group including the `job_title`, `min_salary`, and `max_salary` columns in the `hr.jobs` table at the external database.

- Prebuilt DML conflict handlers do not support LOB, `LONG`, `LONG RAW`, user-defined type, and Oracle-supplied type columns. Therefore, do not include these types of columns in the `column_list` parameter when running the procedure `SET_DML_CONFLICT_HANDLER`.

**See Also:**

[Oracle Database SQL Language Reference](../sqlrf/Data-Types.md) for information about data types

**Parent topic:** Managing DML Conflict Handlers

##### 10.6.7.2 Removing a DML Conflict Handler

You can remove an existing DML conflict handler by running the `SET_DML_CONFLICT_HANDLER` procedure in the `DBMS_APPLY_ADM` package.

To remove an existing DML conflict handler, specify `NULL` for the method, and specify the same apply name and DML conflict handler name as the existing DML conflict handler.

To remove a DML conflict handler:

1.  Connect to the inbound server database as the XStream administrator.
2.  Run the `SET_DML_CONFLICT_HANDLER` procedure in the `DBMS_APPLY_ADM` package with `NULL` specified for the method, and specify the same apply name, DML conflict handler name, object name, conflict type, and resolution column as the existing DML conflict handler.

Example 10-7 Removing a DML Conflict Handler

To remove the DML conflict handler created in "Setting a DML Conflict Handler", run the following procedure:

    BEGIN
      DBMS_APPLY_ADM.SET_DML_CONFLICT_HANDLER(
         apply_name            => 'app_jobs',
         conflict_handler_name => 'jobs_handler_insert',
         method_name           => NULL);
      DBMS_APPLY_ADM.SET_DML_CONFLICT_HANDLER(
         apply_name            => 'app_jobs',
         conflict_handler_name => 'jobs_handler_update',
         method_name           => NULL);
      DBMS_APPLY_ADM.SET_DML_CONFLICT_HANDLER(
         apply_name            => 'app_jobs',
         conflict_handler_name => 'jobs_handler_delete',
         method_name           => NULL);
    END;
    /

**Parent topic:** Managing DML Conflict Handlers

#### 10.6.8 Stopping Conflict Detection for Non-Key Columns

You can stop conflict detection for non-key columns by using the `COMPARE_OLD_VALUES` procedure in the `DBMS_APPLY_ADM` package.

To stop conflict detection for non-key columns:

1.  Connect to the inbound server database as the XStream administrator.
2.  Run the `COMPARE_OLD_VALUES` procedure in the `DBMS_APPLY_ADM` package, and specify the non-key columns and `FALSE` for the `compare` parameter.

Example 10-8 Stopping Conflict Detection for Non-Key Columns

Suppose you configure a `time` column for conflict resolution for the `hr.employees` table. A trigger records the current time in this column for each change to the table. In this case, you can decide to stop conflict detection for the other non-key columns in the table. Add the columns in the `hr.employees` table to the column list for an update conflict handler:

    DECLARE
      cols  DBMS_UTILITY.NAME_ARRAY;
    BEGIN
      cols(1)  := 'first_name';
      cols(2)  := 'last_name';
      cols(3)  := 'email';
      cols(4)  := 'phone_number';
      cols(5)  := 'hire_date';
      cols(6)  := 'job_id';
      cols(7)  := 'salary';
      cols(8)  := 'commission_pct';
      cols(9)  := 'manager_id';
      cols(10) := 'department_id';
      cols(11) := 'time';
      DBMS_APPLY_ADM.SET_DML_CONFLICT_HANDLER(
        apply_name            => 'app_employees',
        conflict_handler_name => 'emp_handler',
        object                => 'hr.employees',
        operation_name        => 'UPDATE',
        conflict_type         => 'ROW_EXISTS',
        method_name           => 'MAXIMUM',
        column_list           => cols,
        resolution_column     => 'time');
    END;
    /

This example does not include the primary key for the table in the column list because it assumes that the primary key is never updated. However, other key columns are included in the column list.

To stop conflict detection for all non-key columns in the table for `UPDATE` operations, enter the following:

    DECLARE
      cols DBMS_UTILITY.LNAME_ARRAY;
      BEGIN
        cols(1) := 'first_name';
        cols(2) := 'last_name';
        cols(3) := 'email';
        cols(4) := 'phone_number';
        cols(5) := 'hire_date';
        cols(6) := 'job_id';
        cols(7) := 'salary';
        cols(8) := 'commission_pct';
      DBMS_APPLY_ADM.COMPARE_OLD_VALUES(
        object_name  => 'hr.employees',
        column_table => cols,
        operation    => '*',
        compare      => FALSE);
    END;
    /

The asterisk (\*) specified for the operation parameter means that conflict detection is stopped for `UPDATE` operations. After you run this procedure, all apply processes running on the database that apply changes to the specified table locally do not detect conflicts on the specified columns. Therefore, in this example, the `time` column is the only column used for conflict detection.

**Note:**

The example in this section sets an DML conflict handler before stopping conflict detection for non-key columns. However, a DML conflict handler is not required before you stop conflict detection for non-key columns.

**See Also:**

[Oracle Database PL/SQL Packages and Types Reference](../arpls/DBMS_APPLY_ADM.md) for more information about the `COMPARE_OLD_VALUES` procedure

**Parent topic:** Managing XStream In Conflict Detection and Resolution

### 10.7 Managing Apply Errors

Apply errors result when an inbound server tries to apply an LCR, and an error is raised.

When an apply error occurs, the LCR that caused the error and all of the other LCRs in the same transaction are moved to the error queue.

- Inbound Server Error Handling
  You can configure error handlers to handle specific types of errors.
- Retrying Apply Error Transactions
  You can retry a specific error transaction, or you can retry all error transactions for an inbound server.
- Deleting Apply Error Transactions
  You can delete a specific error transaction, or you can delete all error transactions for an inbound server.
- Managing Eager Errors Encountered by an Inbound Server
  As a performance optimization, an inbound server can use eager apply to begin to apply large transactions before it receives the commit LCR.

**See Also:**

- "[The Error Queue for an Inbound Server](xstream-in-concepts.md)"

- The Oracle Enterprise Manager Cloud Control online help for instructions on managing apply errors in Oracle Enterprise Manager Cloud Control

**Parent topic:** Managing XStream In

#### 10.7.1 Inbound Server Error Handling

You can configure error handlers to handle specific types of errors.

- About Error Handlers
  An error handler specifies a method for handling a specific error during apply.
- Setting and Unsetting an Error Handler
  You set an error handler with the `SET_REPERROR_HANDLER` procedure in the `DBMS_APPLY` package.

**Parent topic:** Managing Apply Errors

##### 10.7.1.1 About Error Handlers

An error handler specifies a method for handling a specific error during apply.

When an inbound server applies row LCRs, it can encounter errors. You can configure an error handler to handle a specific error using a designated method with the `SET_REPERROR_HANDLER` procedure in the `DBMS_APPLY` package. For example, you can set an error handler that handles ORA-26787 errors that occur when a row LCR tries to update or delete a row that does not exist in a table. In addition, you can configure a default error handling method without specifying a particular error.

You set an error handler for a specific apply process. You can set an error handler for a specific table or for all tables.

The following table describes each error handler method.

Table 10-2 Error Handler Methods

| Method               | Description                                                                                                                                                                                                |
|:---------------------|:-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `ABEND`              | Stop the inbound server when the error is encountered.                                                                                                                                                     |
| `RECORD`             | Move the row LCR that caused the error to the error queue when the error is encountered.                                                                                                                   |
| `IGNORE`             | Silently ignore the error, and do not apply the row LCR, when the error is encountered.                                                                                                                    |
| `RETRY`              | Retry the row LCR for the specified number of times when the error is encountered.<br>If retry fails, then the entire transaction is moved to the error queue.                                             |
| `RETRY_TRANSACTION`  | Retry the transaction for the specified number of times, with the specified delay before retry, when the error is encountered.<br>If retry fails, then the entire transaction is moved to the error queue. |
| `RECORD_TRANSACTION` | Move the entire transaction to the error queue when the error is encountered. `RECORD_TRANSACTION` is the default.                                                                                         |

**Parent topic:** Inbound Server Error Handling

##### 10.7.1.2 Setting and Unsetting an Error Handler

You set an error handler with the `SET_REPERROR_HANDLER` procedure in the `DBMS_APPLY` package.

You can use one of the following methods when you set an error handler:

- `ABEND`

- `RECORD`

- `IGNORE`

- `RETRY`

- `RETRY_TRANSACTION`

- `RECORD_TRANSACTION`

To unset an error handler, set the `method` parameter in the `SET_REPERROR_HANDLER` procedure to `NULL`.

To set or unset an error handler:

1.  Connect to the inbound server database as the XStream administrator.
2.  Run the `SET_REPERROR_HANDLER` procedure in the `DBMS_APPLY_ADM` package.

Example 10-9 Setting an Error Handler That Stops the Inbound Server for All Errors on a Specific Table

This example sets an error handler that stops the `app_oe` inbound server for any errors on the `oe.orders` table. The `0` setting for the `error_number` parameter specifies all errors. The `ABEND` setting for the `method` parameter specifies that the inbound server is stopped when an error is encountered.

    BEGIN
      DBMS_APPLY_ADM.SET_REPERROR_HANDLER(
        apply_name   => 'app_oe',
        object       => 'oe.orders',
        error_number => 0,
        method       => 'ABEND');
    END;
    /

Example 10-10 Setting an Error Handler That Ignores Row LCRs for a Specific Table and a Specific Error

This example sets an error handler that ignores row LCRs that raise the ORA-1403 error for the `app_oe` inbound server. The error handler applies to the `oe.orders` table.

    BEGIN
      DBMS_APPLY_ADM.SET_REPERROR_HANDLER(
        apply_name   => 'app_oe',
        object       => 'oe.orders',
        error_number => 1403,
        method       => 'IGNORE');
    END;
    /

Example 10-11 Unsetting an Error Handler

This example unsets an error handler that ignores row LCRs that raise the ORA-1403 error for the `app_oe` inbound server. The error handler was set for the `oe.orders` table.

    BEGIN
      DBMS_APPLY_ADM.SET_REPERROR_HANDLER(
        apply_name   => 'app_oe',
        object       => 'oe.orders',
        error_number => 1403,
        method       => NULL);
    END;
    /

**Parent topic:** Inbound Server Error Handling

#### 10.7.2 Retrying Apply Error Transactions

You can retry a specific error transaction, or you can retry all error transactions for an inbound server.

Before you retry error transactions, you might need to make DML or DDL changes to database objects to correct the conditions that caused one or more apply errors.

- Retrying a Specific Apply Error Transaction
  When you retry an error transaction, you can execute it immediately or send the error transaction to a user procedure for modifications before executing it.
- Retrying All Error Transactions for an Inbound Server
  After you correct the conditions that caused all of the apply errors for an inbound server, you can retry all of the error transactions by running the `EXECUTE_ALL_ERRORS` procedure in the `DBMS_APPLY_ADM` package.

**Parent topic:** Managing Apply Errors

##### 10.7.2.1 Retrying a Specific Apply Error Transaction

When you retry an error transaction, you can execute it immediately or send the error transaction to a user procedure for modifications before executing it.

- Retrying a Specific Apply Error Transaction Without a User Procedure
  After you correct the conditions that caused an apply error, you can retry the transaction by running the `EXECUTE_ERROR` procedure in the `DBMS_APPLY_ADM` package without specifying a user procedure. In this case, the transaction executes without any custom processing.
- Retrying a Specific Apply Error Transaction With a User Procedure
  You can retry an error transaction by running the `EXECUTE_ERROR` procedure in the `DBMS_APPLY_ADM` package and specify a user procedure to modify one or more LCRs in the transaction before the transaction is executed.

**See Also:**

[Oracle Database PL/SQL Packages and Types Reference](../arpls/DBMS_APPLY_ADM.md) for more information about the `EXECUTE_ERROR` procedure

**Parent topic:** Retrying Apply Error Transactions

###### 10.7.2.1.1 Retrying a Specific Apply Error Transaction Without a User Procedure

After you correct the conditions that caused an apply error, you can retry the transaction by running the `EXECUTE_ERROR` procedure in the `DBMS_APPLY_ADM` package without specifying a user procedure. In this case, the transaction executes without any custom processing.

When there are multiple error transactions, transaction ordering might be important when you execute them. In general, it is best practice to execute the oldest transaction first, and then each later transaction in order until you reach the newest transaction. The `SOURCE_COMMIT_POSITION` column in the `DBA_APPLY_ERROR` view shows the transaction time.

##### To retry a specific apply error transaction without a user procedure:

1.  In SQL\*Plus, connect to the database as the XStream administrator.

    See [Oracle Database Administrator’s Guide](../admin/index.md) for information about connecting to a database in SQL\*Plus.

2.  Run the `EXECUTE_ERROR` procedure in the `DBMS_APPLY_ADM` package, and specify the transaction identifier.

    To retry a transaction with the transaction identifier `5.4.312`, run the following procedure:

        BEGIN
          DBMS_APPLY_ADM.EXECUTE_ERROR(
            local_transaction_id => '5.4.312',
            execute_as_user      => FALSE,
            user_procedure       => NULL);
        END;
        /

If `execute_as_user` is `TRUE`, then the inbound server executes the transaction in the security context of the current user. If `execute_as_user` is `FALSE`, then the inbound server executes the transaction in the security context of the original receiver of the transaction. The original receiver is the user who was processing the transaction when the error was raised.

In either case, the user who executes the transaction must have privileges to perform DML and DDL changes on the apply objects and to run any apply handlers.

**Parent topic:** Retrying a Specific Apply Error Transaction

###### 10.7.2.1.2 Retrying a Specific Apply Error Transaction With a User Procedure

You can retry an error transaction by running the `EXECUTE_ERROR` procedure in the `DBMS_APPLY_ADM` package and specify a user procedure to modify one or more LCRs in the transaction before the transaction is executed.

The modifications should enable successful execution of the transaction.

For example, consider a case in which a conflict caused an apply error. Examination of the error transaction reveals that the old value for the `salary` column in a row LCR contained the wrong value. Specifically, the current value of the salary of the employee with `employee_id` of `197` in the `hr.employees` table did not match the old value of the salary for this employee in the row LCR. Assume that the current value for this employee is `3250` in the `hr.employees` table. The example in this section creates a procedure to resolve the error.

##### To retry a specific apply error transaction with a user procedure:

1.  In SQL\*Plus, connect to the database as the XStream administrator.

    See [Oracle Database Administrator’s Guide](../admin/index.md) for information about connecting to a database in SQL\*Plus.

2.  Given this scenario described previously, create the following user procedure to modify the salary in the row LCR that caused the error:

        CREATE OR REPLACE PROCEDURE xstrmadmin.modify_emp_salary(
          in_any                        IN      ANYDATA,
          error_record                  IN      ALL_APPLY_ERROR%ROWTYPE,
          error_message_number          IN      NUMBER,
          messaging_default_processing  IN OUT  BOOLEAN,
          out_any                       OUT     ANYDATA)
        AS
          row_lcr          SYS.LCR$_ROW_RECORD;
          row_lcr_changed  BOOLEAN := FALSE;
          res              NUMBER;
          ob_owner         VARCHAR2(32);
          ob_name          VARCHAR2(32);
          cmd_type         VARCHAR2(30);
          employee_id      NUMBER;
        BEGIN
          IF in_any.getTypeName() = 'SYS.LCR$_ROW_RECORD' THEN
            -- Access the LCR
            res := in_any.GETOBJECT(row_lcr);
            -- Determine the owner of the database object for the LCR
            ob_owner := row_lcr.GET_OBJECT_OWNER;
            -- Determine the name of the database object for the LCR
            ob_name := row_lcr.GET_OBJECT_NAME;
            -- Determine the type of DML change
            cmd_type := row_lcr.GET_COMMAND_TYPE;
            IF (ob_owner = 'HR' AND ob_name = 'EMPLOYEES' AND cmd_type = 'UPDATE') THEN
              -- Determine the employee_id of the row change
              IF row_lcr.GET_VALUE('old', 'employee_id') IS NOT NULL THEN
                employee_id := row_lcr.GET_VALUE('old', 'employee_id').ACCESSNUMBER();
                IF (employee_id = 197) THEN
                  -- error_record.message_number should equal error_message_number
                  row_lcr.SET_VALUE(
                  value_type => 'OLD',
                  column_name => 'salary',
                  column_value => ANYDATA.ConvertNumber(3250));
                  row_lcr_changed := TRUE;
                END IF;
              END IF;
            END IF;
          END IF;
          -- Specify that the inbound server continues to process the current message
          messaging_default_processing := TRUE;
          -- assign out_any appropriately
          IF row_lcr_changed THEN
            out_any := ANYDATA.ConvertObject(row_lcr);
          ELSE
            out_any := in_any;
          END IF;
        END;
        /

3.  Run the `EXECUTE_ERROR` procedure in the `DBMS_APPLY_ADM` package, and specify the transaction identifier and the user procedure.

    To retry a transaction with the transaction identifier `5.6.924` and process the transaction with the `modify_emp_salary` procedure in the `xstrmadmin` schema before execution, run the following procedure:

        BEGIN
          DBMS_APPLY_ADM.EXECUTE_ERROR(
            local_transaction_id => '5.6.924',
            execute_as_user      => FALSE,
            user_procedure       => 'xstrmadmin.modify_emp_salary');
        END;
        /

**Note:**

The user who runs the procedure must have `SELECT` privilege on the `ALL_APPLY_ERROR` data dictionary view.

**Parent topic:** Retrying a Specific Apply Error Transaction

##### 10.7.2.2 Retrying All Error Transactions for an Inbound Server

After you correct the conditions that caused all of the apply errors for an inbound server, you can retry all of the error transactions by running the `EXECUTE_ALL_ERRORS` procedure in the `DBMS_APPLY_ADM` package.

##### To retry all error transactions for an inbound server:

When there are multiple error transactions, the `EXECUTE_ALL_ERRORS` procedure executes the oldest transaction first, and then executes each later transaction in order up to the newest transaction.

1.  In SQL\*Plus, connect to the database as the XStream administrator.

    See [Oracle Database Administrator’s Guide](../admin/index.md) for information about connecting to a database in SQL\*Plus.

2.  Run the `EXECUTE_ALL_ERRORS` procedure in the `DBMS_APPLY_ADM` package, and specify the name of the inbound server.

    To retry all of the error transactions for an inbound server named `xin`, run the following procedure:

        BEGIN
          DBMS_APPLY_ADM.EXECUTE_ALL_ERRORS(
            apply_name       => 'xin',
            execute_as_user  => FALSE);
        END;
        /

**Note:**

If you specify `NULL` for the `apply_name` parameter, and you have multiple inbound servers, then all of the apply errors are retried for all of the inbound servers.

**Parent topic:** Retrying Apply Error Transactions

#### 10.7.3 Deleting Apply Error Transactions

You can delete a specific error transaction, or you can delete all error transactions for an inbound server.

- Deleting a Specific Apply Error Transaction
  If an error transaction should not be applied, then you can delete the transaction from the error queue using the `DELETE_ERROR` procedure in the `DBMS_APPLY_ADM` package.
- Deleting All Error Transactions for an Inbound Server
  If none of the error transactions should be applied, then you can delete all of the error transactions by running the `DELETE_ALL_ERRORS` procedure in the `DBMS_APPLY_ADM` package.

**Parent topic:** Managing Apply Errors

##### 10.7.3.1 Deleting a Specific Apply Error Transaction

If an error transaction should not be applied, then you can delete the transaction from the error queue using the `DELETE_ERROR` procedure in the `DBMS_APPLY_ADM` package.

##### To delete a specific apply error transaction:

1.  In SQL\*Plus, connect to the database as the XStream administrator.

    See [Oracle Database Administrator’s Guide](../admin/index.md) for information about connecting to a database in SQL\*Plus.

2.  Identify the transaction ID of the error transaction you want to delete.

    For example, run the following query to list the local apply error transactions:

        COLUMN APPLY_NAME FORMAT A11
        COLUMN SOURCE_DATABASE' FORMAT A10
        COLUMN LOCAL_TRANSACTION_ID FORMAT A11
        COLUMN ERROR_NUMBER FORMAT 99999999
        COLUMN ERROR_MESSAGE FORMAT A20
        COLUMN MESSAGE_COUNT FORMAT 99999999

        SELECT APPLY_NAME,
               SOURCE_DATABASE,
               LOCAL_TRANSACTION_ID,
               ERROR_NUMBER,
               ERROR_MESSAGE,
               MESSAGE_COUNT
          FROM DBA_APPLY_ERROR;

3.  Run the `DELETE_ERROR` procedure in the `DBMS_APPLY_ADM` package, and specify the transaction identifier.

    To delete a transaction with the transaction identifier `5.4.312`, run the following procedure:

        EXEC DBMS_APPLY_ADM.DELETE_ERROR(local_transaction_id => '5.4.312');

**Parent topic:** Deleting Apply Error Transactions

##### 10.7.3.2 Deleting All Error Transactions for an Inbound Server

If none of the error transactions should be applied, then you can delete all of the error transactions by running the `DELETE_ALL_ERRORS` procedure in the `DBMS_APPLY_ADM` package.

##### To delete all error transactions for an inbound server:

1.  In SQL\*Plus, connect to the database as the XStream administrator.

    See [Oracle Database Administrator’s Guide](../admin/index.md) for information about connecting to a database in SQL\*Plus.

2.  Run the `DELETE_ALL_ERRORS` procedure in the `DBMS_APPLY_ADM` package, and specify the name of the inbound server.

    To delete all of the error transactions for an inbound server named `xin`, run the following procedure:

        EXEC DBMS_APPLY_ADM.DELETE_ALL_ERRORS(apply_name => 'xin');

**Note:**

If you specify `NULL` for the `apply_name` parameter, and you have multiple inbound servers, then all of the apply errors are deleted for all of the inbound servers.

**Parent topic:** Deleting Apply Error Transactions

#### 10.7.4 Managing Eager Errors Encountered by an Inbound Server

As a performance optimization, an inbound server can use eager apply to begin to apply large transactions before it receives the commit LCR.

See "[Optimizing XStream In Performance for Large Transactions](xstream-in-concepts.md)" for information about eager apply.

An inbound server can encounter an error while eagerly applying a transaction. Because all of the LCRs are not available for the transaction, an `EAGER` `ERROR` is recorded for this failed transaction. In this case, an entry in the `ALL_APPLY_ERROR` view shows an eager error for the transaction, but the LCRs are not recorded in the error queue. If an error transaction is not an eager error transaction, then it is referred to as a normal error transaction.

Normal error transactions and eager error transactions must be managed differently. An inbound server moves a normal error transaction, including all of its LCRs, to the error queue, but an inbound server does not move an eager error transaction to the error queue.

An eager error causes the inbound server to stop. When it restarts, if the error queue has an `EAGER` `ERROR` for the restarting transaction, then the transaction is started as a normal transaction. That is, the LCRs in the large transaction spill to disk, and the inbound server begins to apply them only after the commit LCR is received.

The following statements apply to both normal error transactions and eager error transactions:

- The `ALL_APPLY_ERROR` and `ALL_APPLY_ERROR_MESSAGES` views contain information (metadata) about the error transaction.

- The inbound server does not apply the error transaction.

Table 10-3 explains the options for managing a normal error transaction.

Table 10-3 Options Available for Managing a Normal Error Transaction

| Action                        | Mechanisms                                                                                                       | Description                                                                                                                                                                                                                                       |
|:------------------------------|:-----------------------------------------------------------------------------------------------------------------|:--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Delete the error transaction  | `DBMS_APPLY_ADM.DELETE_ERROR`<br>`DBMS_APPLY_ADM.DELETE_ALL_ERRORS`<br>Oracle Enterprise Manager Cloud Control   | The error transaction is deleted from the error queue, and the metadata about the error transaction is deleted. An inbound server does not try to reexecute the transaction when the inbound server is restarted. The transaction is not applied. |
| Execute the error transaction | `DBMS_APPLY_ADM.EXECUTE_ERROR`<br>`DBMS_APPLY_ADM.EXECUTE_ALL_ERRORS`<br>Oracle Enterprise Manager Cloud Control | The error transaction in the error queue is executed. If there are no errors during execution, then the transaction is applied. If an LCR raises an error during execution, then the normal error transaction is moved back to the error queue.   |
| Retain the error transaction  | None. (The error transaction is retained automatically.)                                                         | The error transaction remains in the error queue even if the inbound server is restarted. The metadata about the error transaction is also retained. The transaction is not applied.                                                              |

Table 10-4 explains the options for managing an eager error transaction.

Table 10-4 Options Available for Managing an Eager Error Transaction

| Action                   | Mechanisms                                                                                                     | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       |
|:-------------------------|:---------------------------------------------------------------------------------------------------------------|:------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Delete error transaction | `DBMS_APPLY_ADM.DELETE_ERROR`<br>`DBMS_APPLY_ADM.DELETE_ALL_ERRORS`<br>Oracle Enterprise Manager Cloud Control | The metadata about the eager error transaction is deleted. When the inbound server is restarted, it attempts to execute the transaction as an eager transaction. If the inbound server does not encounter an error during execution, then the transaction is applied successfully. If the inbound server encounters an error during execution, then the eager error transaction is recorded.                                                                                                                                                                                                                                                                                                                                                                                                                      |
| Retain error transaction | None. (The metadata about the error transaction is retained automatically.)                                    | The metadata about the eager error transaction is retained. When the inbound server is restarted, it attempts to execute the transaction as a normal transaction.<br>Specifically, the inbound server spills the transaction to disk and attempts to execute the transaction. If the inbound server does not encounter an error during execution, then the transaction is applied successfully. If the inbound server encounters an error during execution, then the transaction becomes a normal error transaction. In this case, the LCR that raised the error and all of the other LCRs in the transaction are moved to the error queue. After the normal error transaction is moved to the error queue, you must manage the error transaction as a normal error transaction (not an eager error transaction). |

**Note:**

If you attempt to execute an eager error transaction manually using the `DBMS_APPLY_ADM` package or Oracle Enterprise Manager Cloud Control, then the following error is raised:

    ORA-26909: cannot reexecute an eager error

An eager error transaction cannot be executed manually. Instead, it is executed automatically when the inbound server is enabled.

##### To manage an eager error transaction encountered by an inbound server:

1.  Connect to the inbound server database as the XStream administrator.

    See [Oracle Database Administrator’s Guide](../admin/index.md) for information about connecting to a database in SQL\*Plus.

2.  Query the `ERROR_TYPE` column in the `ALL_APPLY_ERROR` data dictionary view:

        SELECT APPLY_NAME, ERROR_TYPE FROM ALL_APPLY_ERROR;

    Follow the appropriate instructions based on the error type:

    - If the `ERROR_TYPE` column shows `EAGER` `ERROR`, then proceed to Step 3.

    - If the `ERROR_TYPE` column shows `NULL`, then the apply error is not an eager error, and you cannot use the instructions in this section to manage it. Instead, use the instructions in "Retrying Apply Error Transactions" and "Deleting Apply Error Transactions".

3.  Examine the error message raised by the LCR, and determine the cause of the error.

    **See Also:**

    - "[Checking for Apply Errors](monitoring-xstream-in.md)" and "[Displaying Detailed Information About Apply Errors](monitoring-xstream-in.md)" for information about checking for apply errors using data dictionary views

    - Oracle Enterprise Manager Cloud Control online help for information about checking for apply errors using Oracle Enterprise Manager Cloud Control

4.  If possible, determine how to avoid the error, and make any changes necessary to avoid the error.

    **See Also:**

    "[Troubleshooting XStream In](troubleshooting-xstream-in.md)" for information about common apply errors and solutions for them

5.  Either retain the error transaction or delete the error transaction:

    - Delete the error transaction only if you have corrected the problem. The inbound server reexecutes the transaction when it is enabled.

      For example, to delete a transaction with the transaction identifier `5.4.312`, run the following procedure:

          EXEC DBMS_APPLY_ADM.DELETE_ERROR(local_transaction_id => '5.4.312');

    - Retain the error transaction if you cannot correct the problem now or if you plan to reexecute it in the future. No action is necessary to retain the error transaction. It remains in the error queue until it is reexecuted or deleted.

    See Table 10-4 for more information about these choices.

    **Note:**

    It might not be possible to recover a normal error transaction that is deleted. Before deleting the error transaction, ensure that the error type is `EAGER` `ERROR`.

    **See Also:**

    - "Deleting Apply Error Transactions" for more information about deleting an error transaction using the `DBMS_APPLY_ADM` package

    - See the Oracle Enterprise Manager Cloud Control online help for information about deleting an error transaction using Oracle Enterprise Manager Cloud Control.

6.  If the inbound server is disabled, then start the inbound server.

    Query the `STATUS` column in the `ALL_APPLY_ERROR` view to determine whether the inbound server is enabled or disabled.

    If the `disable_on_error` apply parameter is set to `Y` for the inbound server, then the inbound server becomes disabled when it encounters the error and remains disabled.

    If the `disable_on_error` apply parameter is set to `N` for the inbound server, then the inbound server stops and restarts automatically when it encounters the error.

    See Table 10-4 for information about how the inbound server handles the error transaction based on your choice in Step 5.

    **See Also:**

    - "Starting an Inbound Server" for information about starting an inbound server or apply process using the `DBMS_APPLY_ADM` package

    - Oracle Enterprise Manager Cloud Control online help for information about starting an inbound server or apply process using Oracle Enterprise Manager Cloud Control

**See Also:**

- [Oracle Database Reference](../refrn/ALL_APPLY_ERROR.md)

- [Oracle Database PL/SQL Packages and Types Reference](../arpls/DBMS_XSTREAM_ADM.md)

**Parent topic:** Managing Apply Errors

### 10.8 Conflict and Error Handling Precedence

To resolve a conflict or error, an inbound server tries to find conflict handlers and error handlers.

When an inbound server encounters a conflict or an error, it tries to resolve the problem by checking for the following types of handlers that apply to the error in the specified order:

1.  An update conflict handler set with the `SET_UPDATE_CONFLICT_HANDLER` procedure

2.  A custom conflict handler set with the `SET_DML_CONFLICT_HANDLER` procedure

3.  A collision handler set with the `HANDLE_COLLISIONS` procedure

4.  An error handler set with the `SET_REPERROR_HANDLER` procedure

5.  A custom conflict handler set with the `SET_DML_HANDLER` procedure

All of the procedures are in the `DBMS_APPLY_ADM` package.

If no handler applies to the conflict or error, then the transaction that caused the error is moved to the error queue.

**Parent topic:** Managing XStream In

### 10.9 Dropping Components in an XStream In Configuration

You can drop an inbound server with the `DROP_INBOUND` procedure in the `DBMS_XSTREAM_ADM` package.

This procedure always drops the specified inbound server. This procedure also drops the queue for the inbound server if both of the following conditions are met:

- One call to the `CREATE_INBOUND` procedure created the inbound server and the queue.

- The inbound server is the only subscriber to the queue.

If either one of the preceding conditions is not met, then the `DROP_INBOUND` procedure only drops the inbound server. It does not drop the queue.

#### To drop an inbound server:

1.  Connect to the inbound server database as the XStream administrator.

    See [Oracle Database Administrator’s Guide](../admin/index.md) for information about connecting to a database in SQL\*Plus.

2.  Run the `DROP_INBOUND` procedure.

If the inbound server's queue is not dropped automatically, then run the `REMOVE_QUEUE` procedure to drop it.

Example 10-12 Dropping an Inbound Server

To drop an inbound server named `xin`, run the following procedure:

    exec DBMS_XSTREAM_ADM.DROP_INBOUND('xin');

Example 10-13 Dropping an Inbound Server's Queue

To drop a queue named `xin_queue`, run the following procedure:

    exec DBMS_XSTREAM_ADM.REMOVE_QUEUE('xin_queue');

**See Also:**

[Oracle Database PL/SQL Packages and Types Reference](../arpls/DBMS_XSTREAM_ADM.md)

**Parent topic:** Managing XStream In
