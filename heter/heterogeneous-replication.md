Data can be replicated between a non-Oracle system and Oracle Database using materialized views.

**Note:**

There is another means of replicating information between Oracle and non-Oracle databases called Oracle GoldenGate.

For information about using Oracle GoldenGate, see the Oracle GoldenGate documentation.

Materialized views instantiate data captured from tables at the non-Oracle master site at a particular time. This instant is defined by a refresh operation, which copies this data to Oracle Database and synchronizes the copy on the Oracle system with the master copy on the non-Oracle system. The materialized data is then available as a view on Oracle Database.

Replication facilities provide mechanisms to schedule refreshes and to collect materialized views into replication groups to facilitate their administration. Refresh groups permit refreshing multiple materialized views as if they were a single object.

Heterogeneous replication support is necessarily limited to a subset of the full Oracle-to-Oracle replication functionality:

- Only the non-Oracle system can be the primary site. This is because materialized views can be created only on Oracle Database.

- Materialized views must use a complete refresh. This is because fast refresh would require Oracle-specific functionality in the non-Oracle system.

- Not all types of materialized views can be created to reference tables on a non-Oracle system. Primary key and subquery materialized views are supported, but `ROWID` and `OBJECT ID` materialized views are not supported. This is because there is no SQL standard for the format and contents of `ROWID`, and non-Oracle systems do not implement Oracle objects.

Other restrictions apply to any access to non-Oracle data through Oracle's Heterogeneous Services facilities. The most important of these are:

- Non-Oracle data types in table columns mapped to a fixed view must be compatible with (that is, have a mapping to or from) Oracle data types. This is usually true for data types defined by ANSI SQL standards.

- A subquery materialized view may not be able to use language features restricted by individual non-Oracle systems. In many cases, Heterogeneous Services supports such language features by processing queries within Oracle Database. Occasionally the non-Oracle systems impose limitations that cannot be detected until Heterogeneous Services attempts to execute the query.

The following examples illustrate basic setup and use of three materialized views to replicate data from a non-Oracle system to an Oracle data store.

**Note:**

For the following examples, `remote_db` refers to the non-Oracle system that you are accessing from Oracle Database.

Modify these examples for your environment. Do not try to execute them as they are written.

- Example: Creating Materialized Views for Heterogeneous Replication
  An example creating materialized views for Heterogeneous Replication.
- Example: Setting Up a Refresh Group for Heterogeneous Replication
  An example setting up a refresh group for Heterogeneous Replication.
- Example: Forcing Refresh of All Three Materialized Views
  An example forcing the refresh of materialized views.

**Parent topic:** [Features of Oracle Database Gateways](oracle-database-gateways-features.md)

### Example: Creating Materialized Views for Heterogeneous Replication

An example creating materialized views for Heterogeneous Replication.

This example creates three materialized views for Heterogeneous Replication. These materialized views are used in subsequent examples.

1.  Create a primary key materialized view of table `customer@remote_db`.
            CREATE MATERIALIZED VIEW pk_mv REFRESH COMPLETE AS
              SELECT * FROM customer@remote_db WHERE "zip" = 94555;
2.  Create a subquery materialized view of tables `orders@remote_db` and `customer@remote_db`.
            CREATE MATERIALIZED VIEW sq_mv REFRESH COMPLETE AS
              SELECT * FROM orders@remote_db o WHERE EXISTS
                (SELECT c."c_id" FROM customer@remote_db c
                   WHERE c."zip" = 94555 and c."c_id"  = o."c_id" );
3.  Create a complex materialized view of data from multiple tables on `remote_db``.`
            CREATE MATERIALIZED VIEW cx_mv
              REFRESH COMPLETE AS
              SELECT  c."c_id", o."o_id"
                FROM customer@remote_db c,
                     orders@remote_db o,
                     order_line@remote_db ol
                WHERE c."c_id" = o."c_id"
                AND o."o_id" = ol."o_id";

**Parent topic:** Heterogeneous Replication

### Example: Setting Up a Refresh Group for Heterogeneous Replication

An example setting up a refresh group for Heterogeneous Replication.

This example shows how to set up a refresh group for Heterogeneous Replication for the materialized views created in Example: Creating Materialized Views for Heterogeneous Replication.

    BEGIN
      dbms_refresh.make('refgroup1',
       'pk_mv, sq_mv, cx_mv',
       NULL, NULL);
     END;
     /

**Parent topic:** Heterogeneous Replication

### Example: Forcing Refresh of All Three Materialized Views

An example forcing the refresh of materialized views.

This example shows how to force a refresh of all three materialized views created in Example: Creating Materialized Views for Heterogeneous Replication.

    BEGIN
       dbms_refresh.refresh('refgroup1');
    END;
     /

**Parent topic:** Heterogeneous Replication
