Materialized view support is available for relational tables that contain columns of an object, collection, or `REF` type. Such materialized views are called object-relational materialized views.

All user-defined types required by an object-relational materialized view must exist at the materialized view site as well as at the master site. They must have the same object type IDs and versions at both sites.

Topics:

- Object, Collection, or REF Type Columns

- Object Tables

### 9.9.1 Object, Collection, or REF Type Columns

To be updatable, a materialized view based on a table that contains an [object column](glossary.md) must select the column as an object in the query that defines the view: if the query selects only certain attributes of the column's object type, then the materialized view is read-only.

The view-definition query can also select columns of collection or `REF` type. `REF`s can be either primary-key based or have a system-generated key, and they can be either scoped or unscoped. Scoped `REF` columns can be rescoped to a different table at the site of the materialized view—for example, to a local materialized view of the master table instead of the original, remote table.

### 9.9.2 Object Tables

A materialized view based on an object table is called an object materialized view. Such a materialized view is itself an object table. An object materialized view is created by adding the `OF` `type` keyword to the `CREATE` `MATERIALIZED` `VIEW` statement. For example:

    CREATE MATERIALIZED VIEW customer OF cust_objtyp AS
     SELECT * FROM HR.Customer_objtab@dbs1;

As with an ordinary object table, each row of an object materialized view is an object instance, so the view-definition query that creates the materialized view must select entire objects from the master table: the query cannot select only a subset of the object type's attributes. For example, the following materialized view is not allowed:

    CREATE MATERIALIZED VIEW customer OF cust_objtyp AS
     SELECT CustNo FROM HR.Customer_objtab@dbs1;

You can create an object-relational materialized view from an object table by omitting the `OF` `type` keyword, but such a view is read-only: you cannot create an updatable object-relational materialized view from an object table.

For example, the following `CREATE` `MATERIALIZED` `VIEW` statement creates a read-only object-relational materialized view of an object table. Even though the view-definition query selects all columns and attributes of the object type, it does not select them as attributes of an object, so the view created is object-relational and read-only:

    CREATE MATERIALIZED VIEW customer AS
     SELECT * FROM HR.Customer_objtab@dbs1;

For both object-relational and object materialized views that are based on an object table, if the type of the master object table is not `FINAL`, the `FROM` clause in the materialized view definition query must include the `ONLY` keyword. For example:

    CREATE MATERIALIZED VIEW customer OF cust_objtyp AS
     SELECT CustNo FROM ONLY HR.Customer_objtab@dbs1;

Otherwise, the `FROM` clause must omit the `ONLY` keyword.
