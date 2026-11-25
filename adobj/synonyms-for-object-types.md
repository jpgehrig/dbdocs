Just as you can create synonyms for tables, views, and various other schema objects, you can also define synonyms for object types.

Synonyms for types have the same advantages as synonyms for other kinds of schema objects: they provide a location-independent way to reference the underlying schema object. An application that uses public type synonyms can be deployed unaltered, in any schema of a database, without requiring a qualified type name with the schema name.

**See Also:**

[Oracle Database Administrator's Guide](../admin/managing-views-sequences-and-synonyms.md) for more information on synonyms in general

Topics:

- Creating a Type Synonym

- Using a Type Synonym

### 7.3.1 Creating a Type Synonym

You create a type synonym with a `CREATE` `SYNONYM` statement.

The user must have been granted `CREATE` `SYNONYM` and `CREATE` `PUBLIC SYNONYM` privileges.

For example, these statements create a type `typ1` and then create a synonym for it:

Example 7-11 CREATE TYPE / SYNONYM for user1

    -- Example requires Ex.7-1 which created user1 and granted it the CREATE SYNONYM
    -- and CREATE PUBLIC SYNONYM privileges
    -- connect as user1 if not already connected.

    CREATE TYPE typ1 AS OBJECT (x number);
    /
    CREATE SYNONYM syn1 FOR typ1;

Synonyms can be created for collection types, too. The following example creates a synonym for a nested table type:

    CREATE TYPE typ2 AS TABLE OF NUMBER;
    /
    CREATE SYNONYM syn2 FOR typ2;

You create a public synonym by using the `PUBLIC` keyword:

    CREATE TYPE shape AS OBJECT ( name VARCHAR2(10) );
    /
    CREATE PUBLIC SYNONYM pub_shape FOR shape;

With the `REPLACE` option you can make the synonym point to a different underlying type. For example, the following statement causes `syn1` to point to type `typ2` instead of the type it formerly pointed to:

    CREATE OR REPLACE SYNONYM syn1 FOR typ2;

### 7.3.2 Using a Type Synonym

You can use a type synonym anywhere that you can refer to a type. For instance, you can use a type synonym in a DDL statement to name the type of a table column or type attribute.

Example 7-12 uses synonym `syn1` to specify the type of an attribute in type `typ3`:

Example 7-12 Using a Type Synonym in a Create Statement

    -- Requires Ex 7-1 and connection as user1
    -- drop syn1 and typ1 if created for Ex. 7-12
    CREATE TYPE typ1 AS OBJECT (x number);
    /
    CREATE SYNONYM syn1 FOR typ1;

    CREATE TYPE typ3 AS OBJECT ( a syn1 );
    /

In the next statement, the type synonym `syn1` calls the constructor of the object type `typ1`, for which `syn1` is a synonym. The statement returns an object instance of `typ1`:

    SELECT syn1(0) FROM dual;

In the following, `syn2` is a synonym for a nested table type. The synonym replaces the actual type name in a `CAST` expression.

    SELECT CAST(MULTISET(SELECT eno FROM USER3.EMP) AS syn2) FROM dual;

This code returns the following output:

    SQL> -- Type synonym used to call a constructor / nested table
    SELECT syn1(0) FROM dual;
    SELECT CAST(MULTISET(SELECT eno FROM USER3.EMP) AS syn2) FROM
    dual;
    SQL> SYN1(0)(X)
    ----------------------------------------------------------------
    TYP1(0)
    SQL>
    CAST(MULTISET(SELECTENOFROMUSER3.EMP)ASSYN2)
    ----------------------------------------------------------------
    TYP2()

Type synonyms can be used in the following kinds of statements:

- DML statements: `SELECT`, `INSERT`, `UPDATE`, `DELETE`, `FLASHBACK` `TABLE`, `EXPLAIN` `PLAN`, and `LOCK` `TABLE`

- DDL statements: `AUDIT`, `NOAUDIT`, `GRANT`, `REVOKE`, and `COMMENT`

#### 7.3.2.1 Describing Schema Objects That Use Synonyms

If a type or table has been created using type synonyms, the `DESCRIBE` command shows the synonyms that the types represent.

You can query the catalog view `USER_SYNONYMS` to find out the underlying type of a type synonym.

- Use the `DESCRIBE` command to show the synonyms instead of the types they represent.

Similarly, catalog views, which show type names, such as `USER_TYPE_ATTRS`, show the type synonym names in their place.

**See Also:**

Chapter 2 of [Oracle Database Reference](../refrn/about-static-data-dictionary-views.md) for a complete list of the data dictionary catalog views

#### 7.3.2.2 Dependents of Type Synonyms

A type that directly or indirectly references a synonym in its type declaration is a dependent of that synonym. Thus, in the following line from Example 7-12, type `typ3` is a dependent type of synonym `syn1`.

    CREATE TYPE typ3 AS OBJECT ( a syn1 );
    /

Other kinds of schema objects that reference synonyms in their DDL statements also become dependents of those synonyms. An object that depends on a type synonym depends on both the synonym and the underlying type of the synonym.

The dependency relationships of a synonym affect your ability to drop or rename the synonym. Dependent schema objects are also affected by some operations on synonyms. The following sections describe these various ramifications.

#### 7.3.2.3 Restriction on Replacing a Type Synonym

You can replace a synonym only if it has no dependent tables or valid user-defined types. Replacing a synonym is equivalent to dropping it and then re-creating a new synonym with the same name.

#### 7.3.2.4 Dropping Type Synonyms

You drop a synonym with the `DROP` `SYNONYM` statement as shown in Example 7-13.

Example 7-13 Dropping Type Synonyms

    CREATE SYNONYM syn4 FOR typ1;

    DROP SYNONYM syn4;

You cannot drop a type synonym if it has table or valid object types as dependents unless you use the `FORCE` option. The `FORCE` option causes any columns that directly or indirectly depend on the synonym to be marked unused, just as if the actual types of the columns were dropped. (A column indirectly depends on a synonym if, for instance, the synonym is used to specify the type of an attribute of the declared type of the column.)

Any dependent schema objects of a dropped synonym are invalidated. They can be revalidated by creating a local object or a new public synonym with the same name as the dropped synonym.

Dropping the underlying base type of a type synonym has the same effect on dependent objects as dropping the synonym.

#### 7.3.2.5 Renaming Type Synonyms

You can rename a type synonym with the `RENAME` statement. Renaming a synonym is equivalent to dropping it and then re-creating it with a new name. You cannot rename a type synonym if it has dependent tables or valid object types. The following example fails because synonym `syn1` has a dependent object type:

    RENAME syn1 TO syn3 -- invalid statement;

#### 7.3.2.6 Public Type Synonyms and Local Schema Objects

You cannot create a local schema object that has the same name as a public synonym if the public synonym has a dependent table or valid object type in the local schema that will hold the new schema object. Nor can you create a local schema object that has the same name as a private synonym in the same schema.

For instance, in the following example, table `shape_tab` is a dependent table of public synonym `pub_shape` because the table has a column that uses the synonym in its type definition. Consequently, the attempt to create a table that has the same name as public synonym `pub_shape`, in the same schema as the dependent table, fails:

    -- Following uses public synonym pub_shape
    CREATE TABLE shape_tab ( c1 pub_shape );
    -- Following is not allowed
    CREATE TABLE pub_shape ( c1 NUMBER ) -- invalid statement;
