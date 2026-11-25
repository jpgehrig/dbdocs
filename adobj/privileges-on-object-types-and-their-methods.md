Privileges for object types exist at the system level and the schema object level.

Topics:

- System Privileges for Object Types

- Schema Object Privileges

- Types Used in New Types or Tables

- Example: Privileges on Object Types

- Access Privileges on Objects, Types, and Tables

### 7.1.1 System Privileges for Object Types

Oracle database defines the following system privileges for object types:

- `CREATE` `TYPE` enables you to create object types in your own schema

- `CREATE` `ANY` `TYPE` enables you to create object types in any schema

- `ALTER` `ANY` `TYPE` enables you to alter object types in any schema

- `DROP` `ANY` `TYPE` enables you to drop named types in any schema

- `EXECUTE` `ANY` `TYPE` enables you to use and reference named types in any schema

- `UNDER` `ANY` `TYPE` enables you to create subtypes under any non-final object types

- `UNDER` `ANY` `VIEW` enables you to create subviews under any object view

The following roles are helpful:

- The `RESOURCE` role includes the `CREATE` `TYPE` system privilege.

- The DBA role includes all of these privileges.

### 7.1.2 Schema Object Privileges

Two schema object privileges apply to object types:

- `EXECUTE` enables you to use the type to:

  - Define a table.

  - Define a column in a relational table.

  - Declare a variable or parameter of the named type.

  `EXECUTE` lets you invoke the methods of a type, including the constructor.

  Method execution and the associated permissions are the same as for stored PL/SQL procedures.

- `UNDER` enables you to create a subtype or subview under the type or view on which the privilege is granted.

  Only a grantor with the `UNDER` privilege `WITH` `GRANT` `OPTION` on the direct supertype or superview can grant the `UNDER` privilege on a subtype or subview.

The phrase `WITH` `HIERARCHY` `OPTION` grants a specified object privilege on all subtypes of the object. This option is meaningful only with the `SELECT` object privilege granted on an object view in an object view hierarchy. In this case, the privilege applies to all subviews of the view on which the privilege is granted.

### 7.1.3 Types Used in New Types or Tables

In addition to the permissions detailed in the previous sections, you need specific privileges to:

- Create types or tables that use types created by other users.

- Grant use of your new types or tables to other users.

You must have either the `EXECUTE` `ANY` `TYPE` system privilege or the `EXECUTE` object privilege for any type used to define a new type or table. You must have been granted these privileges explicitly, and not through a role.

To grant access to your new type or table to other users, you must have either the required `EXECUTE` object privileges with the `GRANT` option or the `EXECUTE` `ANY` `TYPE` system privilege with the option `WITH` `ADMIN` `OPTION`. You must have been granted these privileges explicitly, not through a role.

### 7.1.4 Example: Privileges on Object Types

This section presents several related examples, creating users or schemas and then granting privileges on them.

Example 7-1 creates three users or schemas, `USER1`, `USER2`, and `USER3`, and grants them the `CREATE` `SESSION` and `RESOURCE` roles. Some of the subsequent examples in this chapter use these schemas.

This example requires you to create and use several passwords. If you plan to run the example, make these changes to your SQL code first.

**Note:**

For simplicity, this example does not perform the password management techniques that a deployed system normally uses. In a production environment, follow the Oracle Database password management guidelines, and disable any sample accounts.

**See Also:**

See [Oracle Database Security Guide](../dbseg/managing-security-for-application-developers.md) for password management guidelines and other security recommendations.

Example 7-1 Creating User Schemas

    -- Requires passwords
    CONNECT SYSTEM
    -- Enter password
    CREATE USER user1 PROFILE default
       IDENTIFIED BY password DEFAULT TABLESPACE example ACCOUNT UNLOCK;
    GRANT CREATE SESSION TO user1;
    GRANT RESOURCE TO user1;
    GRANT CREATE SYNONYM TO user1;
    GRANT CREATE PUBLIC SYNONYM TO user1;
    GRANT DROP PUBLIC SYNONYM TO user1;
    CREATE USER user2 PROFILE default
       IDENTIFIED BY password DEFAULT TABLESPACE example ACCOUNT UNLOCK;
    GRANT CREATE SESSION TO user2;
    GRANT RESOURCE TO user2;
    CREATE USER user3  PROFILE default
       IDENTIFIED BY password DEFAULT TABLESPACE example ACCOUNT UNLOCK;
    GRANT CREATE SESSION TO user3;
    GRANT RESOURCE TO user3;

Example 7-2 requires the input of a password, `USER1` performs the `CREATE` and `GRANT` Data Definition Language (DDL) statements in the `USER1` schema:

Example 7-2 Granting Privileges on Object Types

    CREATE TYPE type1 AS OBJECT ( attr1 NUMBER );
    /
    CREATE TYPE type2 AS OBJECT ( attr2 NUMBER );
    /
    GRANT EXECUTE ON type1 TO user2;
    GRANT EXECUTE ON type2 TO user2 WITH GRANT OPTION;

In Example 7-3, `USER2` performs the `CREATE` DDL statement in the `USER2` schema:

Example 7-3 Performing DDL Statements in USER2 Schema

    -- Requires Ex. 7-1, 7-2 and password input
    CONNECT user2
    -- Enter password
    CREATE TABLE tab1 OF user1.type1;
    CREATE TYPE type3 AS OBJECT ( attr3 user1.type2 );
    /
    CREATE TABLE tab2 (col1 user1.type2 );

In Example 7-4, the first two statements succeed because `USER2` was granted the `EXECUTE` privilege with the `GRANT` option on `USER1`'s `TYPE2` in the last line of Example 7-2 and Example 7-3 created `type3` as an object using `attr3` `user1.type2`.

However, the last grant Example 7-4 fails because `USER2` has not been granted the `EXECUTE` privilege with the `GRANT` option on `USER1.TYPE1`.

Example 7-4 Performing Grants to USER3

    -- Requires Ex. 7-1, 7-2, and 7-3
    GRANT EXECUTE ON type3 TO user3;
    GRANT SELECT ON tab2 TO user3;

    -- Privileges on Object Types
    GRANT SELECT ON tab1 TO user3 -- incorrect statement;

In Example 7-5, `USER3` has the necessary privileges to perform the following actions:

Example 7-5 Creating Tables and Types

    -- Requires Ex. 7-1, 7-2, 7-3, and 7-4
    CONNECT user3
    -- Enter password
    CREATE TYPE type4 AS OBJECT (attr4 user2.type3);
    /
    CREATE TABLE tab3 OF type4;

### 7.1.5 Access Privileges on Objects, Types, and Tables

Object types only make use of the `EXECUTE` privilege.

However, object tables use all the same privileges as relational tables:

- `READ` or `SELECT` lets you access an object and its attributes from the table.

- `UPDATE` lets you modify attributes of objects in the table.

- `INSERT` lets you add new objects to the table.

- `DELETE` lets you delete objects from the table.

Similar table and column privileges regulate the use of table columns of object types.

Selecting columns of an object table does not require privileges on the type of the object table. Selecting the entire [row object](glossary.md), however, does.

Consider the schema and queries created below in Example 7-6:

Example 7-6 SELECT Privileges on Type Access

    -- Requires Ex. 7-1, 7-2, 7-3, 7-4, and 7-5
    CREATE TYPE emp_type AS OBJECT (
      eno     NUMBER,
      ename   VARCHAR2(36));
    /
    CREATE TABLE emp OF emp_type; // an object table
    GRANT SELECT on emp TO user1;
    SELECT VALUE(e) FROM emp e;
    SELECT eno, ename FROM emp;

For both queries, Oracle database checks the user's `SELECT` privilege for the object table `emp`. For the first query, the user needs to obtain the `emp_type` type information to interpret the data. When the query accesses the `emp_type` type, the database checks the user's `EXECUTE` privilege.

The second query, however, does not involve named types, so the database does not check type privileges.

Additionally, `USER3` can perform queries such as these:

    SELECT t.col1.attr2 from user2.tab2 t;
    SELECT t.attr4.attr3.attr2 FROM tab3 t;

Note that in both queries, `USER3` does not have explicit privileges on the underlying type. However, the statement succeeds because the type and table owners have the necessary privileges with the `GRANT` option.

Oracle database checks privileges on the following requests and returns an error if the requestor does not have the privilege for the action:

- Pinning an object in the object cache using its `REF` value causes the database to check the `READ` or `SELECT` privilege on the object table containing the object and the `EXECUTE` privilege on the object type.

- Modifying an existing object or flushing an object from the object cache causes the database to check the `UPDATE` privilege on the destination object table. Flushing a new object causes the database to check the `INSERT` privilege on the destination object table.

- Deleting an object causes the database to check the `DELETE` privilege on the destination table.

- Invoking a method causes the database to check the `EXECUTE` privilege on the corresponding object type.

Oracle database does not provide column level privileges for object tables.

**See Also:**

[Oracle Call Interface Programmer's Guide](../lnoci/oci-object-relational-programming.md) for tips and techniques for using OCI program effectively with objects
