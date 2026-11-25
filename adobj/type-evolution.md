Type evolution is the process of changing a object type.

Topics:

- About Type Evolution

- Type Evolution and Dependent Schema Objects

- Options for Updating Data

- Effects of Structural Changes to Types

- Altering a Type by Adding and Dropping Attributes

- Altering a Type by Adding a Nested Table Attribute

- About Validating Types That Have Been Altered

- ALTER TYPE Statement for Type Evolution

- ALTER TABLE Statement for Type Evolution

### 8.3.1 About Type Evolution

You can make the following changes to evolve an object type:

- Add and drop attributes

- Add and drop methods

- Modify a numeric attribute to increase its length, precision, or scale

- Modify a varying length character attribute to increase its length

- Change the `FINAL` and `INSTANTIABLE` properties of a type

- Modify limit and size of `VARRAY`s

- Modify length, precision, and scale of collection elements

Changes to a type affect things that reference the type. For example, if you add a new attribute to a type, data in a column of that type must be presented so as to include the new attribute.

### 8.3.2 Type Evolution and Dependent Schema Objects

Dependent schema objects of a type are objects that directly or indirectly reference the type and are affected by a change to it.

A type can have these kinds of dependent schema objects: tables; types or subtypes; program units (PL/SQL blocks) such as procedures, functions, packages, and triggers; indextypes; views (including object views); function-based indexes; and operators.

How a dependent schema object is affected by a change to a type depends on the object and on the nature of the change.

- Dependent program units, views, operators, and indextypes are marked invalid when the type is modified. The next time one of these invalid schema objects is referenced, it is revalidated using the new type definition. If the object recompiles successfully, it becomes valid and can be used again.

- Dependent function-based indexes may be dropped or disabled, depending on the type change, and must be rebuilt.

- Dependent tables have one or more internal columns added for each attribute added to the type, depending on the attribute type. New attributes are added with `NULL` values. For each dropped attribute, the columns associated with that attribute are dropped. For each modified attribute, the length, precision, or scale of its associated column is changed accordingly.

These changes mainly involve updating the metadata of the tables and can be performed quickly. However, the data in those tables must be updated to the format of the new type version as well, as discussed in "Options for Updating Data".

### 8.3.3 Options for Updating Data

Depending on the amount of data, updating can be time-consuming, so the `ALTER TYPE` command has options to let you choose whether to convert all dependent table data immediately or to leave it in the old format to be converted piecemeal as it is updated in the course of business.

The `CASCADE` option for `ALTER TYPE` propagates a type change to dependent types and tables. `CASCADE` itself has the following options that let you choose whether or not to convert table data to the new type format as part of the propagation:

- `INCLUDING TABLE DATA`: converts the data (default)

- `NOT INCLUDING TABLE DATA` : does not convert data

By default, the `CASCADE` option converts the data. In either case, table data is always returned in the format of the latest type version. If the table data is stored in the format of an earlier type version, the database converts the data to the format of the latest version before returning it, even though the format in which the data is actually stored is not changed until the data is rewritten.

You can retrieve the definition of the latest type from the system view `USER_SOURCE`. You can view definitions of all versions of a type in the `USER_TYPE_VERSIONS` view.

**See Also:**

- "ALTER TYPE Statement for Type Evolution".

- See [Oracle Database PL/SQL Language Reference](../lnpls/CREATE-TYPE-statement.md) for details about type specification and body compilation

### 8.3.4 Effects of Structural Changes to Types

Structural changes to a type affect dependent data and require the data to be converted. This is not true for changes that are confined to method definitions or behavior (implementation) of the type.

These possible changes to a type are structural:

- Add or drop an attribute

- Modify the length, precision, or scale of an attribute

- Change the finality of a type from `FINAL` to `NOT FINAL` or the reverse

These changes result in new versions of the altered type and all its dependent types and require the system to add, drop, or modify internal columns of dependent tables as part of the process of converting to the new version.

When you make any of these kinds of changes to a type that has dependent types or tables, the effects of propagating the change are not confined only to metadata but also affect data storage arrangements and require data conversion.

Besides converting data, you may also need to make other changes. For example, if a new attribute is added to a type, and the type body invokes the constructor of the type, then each constructor in the type body must be modified to specify a value for the new attribute. Similarly, if a new method is added, then the type body must be replaced to add the implementation of the new method. The type body can be modified by using the `CREATE OR REPLACE TYPE BODY` statement.

### 8.3.5 Altering a Type by Adding and Dropping Attributes

You can make a simple change to a type by adding one attribute and dropping another.

Example 8-5makes such a change to `person_type`. The `CASCADE` keyword propagates the type change to dependent types and tables, but the phrase `NOT` `INCLUDING` `TABLE` `DATA` prevents conversion of the related data.

Example 8-5 Altering an Object Type by Adding and Dropping an Attribute

    -- Drop person_typ and person_obj_table if they exist
    CREATE TYPE person_typ AS OBJECT (
      idno           NUMBER,
      name           VARCHAR2(30),
      phone          VARCHAR2(20));
    /
    CREATE TABLE person_obj_table OF person_typ;

    INSERT INTO person_obj_table
      VALUES (person_typ(12, 'Bob Jones', '650-555-0130'));

    SELECT value(p) FROM person_obj_table p;

    VALUE(P)(IDNO, NAME, PHONE)
    --------------------------------------------
    PERSON_TYP(12, 'Bob Jones', '650-555-0130')

You can add the email attribute and drop the phone attribute as follows:

    ALTER TYPE person_typ
      ADD ATTRIBUTE (email VARCHAR2(80)),
      DROP ATTRIBUTE phone CASCADE NOT INCLUDING TABLE DATA;

Then you can disconnect and reconnect to accommodate the type change:

    connect oe/oe;
    connect hr/<password>;
    ALTER SESSION SET PLSQL_WARNINGS = 'enable:all';
    -- The data of table person_obj_table has not been converted yet, but
    -- when the data is retrieved, Oracle returns the data based on
    -- the latest type version. The new attribute is initialized to NULL.
    SELECT value(p) FROM person_obj_table p;

    VALUE(P)(IDNO, NAME, EMAIL)
    ---------------------------------
    PERSON_TYP(12, 'Bob Jones', NULL)

During `SELECT` statements, even though column data may be converted to the latest type version, the converted data is not written back to the column. If you retrieve a particular user-defined type column in a table often, consider converting that data to the latest type version to eliminate redundant data conversions. Converting is especially beneficial if the column contains `VARRAY` attributes which typically take more time to convert than objects or nested table columns.

You can convert a column of data by issuing an `UPDATE` statement to set the column to itself, as indicated in the following code snippet, which is unrelated to previous code.

    UPDATE dept_tab SET emp_array_col = emp_array_col;

You can convert all columns in a table by using `ALTER` `TABLE` with the `UPGRADE` `INCLUDING` `DATA`. For example:

    ALTER TYPE person_typ ADD ATTRIBUTE (photo BLOB)
      CASCADE NOT INCLUDING TABLE DATA;
    ALTER TABLE person_obj_table UPGRADE INCLUDING DATA;

The `ALTER` `TABLE` line converts only the table listed. The `CASCADE` option prevents conversion of other tables or dependents.

### 8.3.6 Altering a Type by Adding a Nested Table Attribute

You can add a nested table attribute to an object type that is included in a nested table.

The following steps are required to make this complex change to a type.

The steps require this initial schema which is then altered by the code in Step 1.

Initial Schema

    -- Drop existing person_typ, department_type, people_typ objects or tables
    CREATE TYPE person_typ AS OBJECT (
      idno           NUMBER,
      name           VARCHAR2(30),
      phone          VARCHAR2(20));
    /
    -- creating a nested table type
    CREATE TYPE people_typ AS TABLE OF person_typ;/
    CREATE TYPE department_typ AS OBJECT (
      manager    person_typ,
      employee   people_typ);  // a nested table/
    CREATE TABLE department OF department_typ
      NESTED TABLE employee STORE AS employee_store_nt;

The code example in Step 1 starts by creating a new object `tasks_typ` and a nested table type to hold it, `tasks_nttab`.

The following steps, both in the code example in Step 1, and in other programs, are necessary to add the nested table `tasks` as an attribute to the object type `person_typ`, which is already included in the nested table `people_typ`.

1.  .
    Altering an Object Type by Adding a Nested Table Attribute

        -- Requires Ex. 8-6
        CREATE TYPE tasks_typ AS OBJECT (
          priority       VARCHAR2(2),
          description    VARCHAR2(30));
        /

        CREATE TYPE tasks_nttab AS TABLE OF tasks_typ;
        /

        -- Propagate the change to employee_store_nt
        -- Specify a storage name for the new nested table
        ALTER TABLE employee_store_nt
          UPGRADE NESTED TABLE tasks STORE AS tasks_nt;
2.  Use `CREATE OR REPLACE TYPE BODY` for `person_typ` to update the corresponding type body to make it current with the new type definition, if necessary.
3.  Upgrade the dependent tables to the latest type version and convert the data in the tables. This validates the table and allow for data access again.
        ALTER TABLE department UPGRADE INCLUDING DATA;
4.  Alter dependent PL/SQL program units as needed to take account of changes to the type.
5.  Use Oracle Type Translator (OTT) to generate new header files for applications, depending on whether the application is written in C or Java.
    Adding a new attribute to a supertype also increases the number of attributes in all its subtypes because these inherit the new attribute. Inherited attributes always precede declared (locally defined) attributes, so adding a new attribute to a supertype causes the ordinal position of all declared attributes of any subtype to be incremented by one recursively.

    You must update the mappings of the altered type to include the new attributes. Use Oracle Type Translator (OTT) to do this. If you use another tool, you must be sure that the type headers are properly synchronized with the type definition in the server; otherwise, unpredictable behavior may result.
6.  Modify application code as needed and rebuild the application.

### 8.3.7 About Validating Types That Have Been Altered

When the system executes an `ALTER TYPE` statement, it first validates the requested type change syntactically and semantically to make sure it is legal.

The system performs the same validations as for a `CREATE TYPE` statement plus some additional ones. If the new specification of the target type or any of its dependent types fails the type validations, the `ALTER TYPE` statement aborts. No new type version is created, and all dependent objects remain unchanged.

If dependent tables exist, further checking ensures that restrictions relating to the tables and indexes are observed. For example, it ensures that an attribute being dropped is not used as a partitioning key. Again, if the `ALTER TYPE` statement fails the check of table-related restrictions, then the type change is aborted, and no new version of the type is created.

When a single `ALTER TYPE` statement adds multiple attributes, it is done in the order specified. Multiple type changes can be specified in the same `ALTER TYPE` statement, but no attribute name or method signature can be specified more than once in the statement. For example, adding and modifying the same attribute in a single statement is not allowed.

The following sections contain other notes on type changes including:

- Dropping an Attribute

- Modifying the Length, Precision, or Scale of an Attribute Type

- Dropping a Method

- Modifying the INSTANTIABLE Property

#### Dropping an Attribute

- Dropping all attributes from a root type is not allowed. Instead, you must drop the type. Because a subtype inherits all the attributes from its supertype, dropping all the attributes from a subtype does not reduce its attribute count to zero; therefore, dropping all attributes declared locally in a subtype is allowed.

- Only an attribute declared locally in the target type can be dropped. You cannot drop an inherited attribute from a subtype. Instead, drop the attribute from the type where it is locally declared.

- Dropping an attribute which is part of a table partitioning or sub-partitioning key in a table is not allowed.

- When an attribute is dropped, the column corresponding to the dropped attribute is dropped.

- When an attribute is dropped, any indexes, statistics, constraints, and referential integrity constraints that reference it are removed.

#### Modifying the Length, Precision, or Scale of an Attribute Type

- You are not allowed to expand the length of an attribute referenced in a function-based index, clustered key or domain index on a dependent table.

- You are not allowed to decrease the length, precision, or scale of an attribute.

#### Dropping a Method

- You can only drop a method from the type in which the method is defined (or redefined): You cannot drop an inherited method from a subtype, and you cannot drop an redefined method from a supertype.

- If a method is not redefined, dropping it using the `CASCADE` option removes the method from the target type and all subtypes. However, if a method is redefined in a subtype, the `CASCADE` will fail and roll back. For the `CASCADE` to succeed, you must first drop each redefined method from the subtype that defines it and then drop the method from the supertype.

  You can consult the `USER_DEPENDENCIES` table to find all the schema objects, including types, that depend on a given type. You can also run the `DBMS_UTILITY.GET_DEPENDENCY` utility to find the dependencies of a type.

- You can use the `INVALIDATE` option to drop a method that has been redefined, but the redefined versions in the subtypes must still be dropped manually. The subtypes will remain in an invalid state until they are explicitly altered to drop the redefined versions. Until then, an attempt to recompile the subtypes for revalidation will produce the error `Method does not override`.

  Unlike `CASCADE`, `INVALIDATE` bypasses all the type and table checks and simply invalidates all schema objects dependent on the type. The objects are revalidated the next time they are accessed. This option is faster than using `CASCADE`, but you must be certain that no problems occur when revalidating dependent types and tables. Table data cannot be accessed while a table is invalid; if a table cannot be validated, its data remains inaccessible.

#### Modifying the INSTANTIABLE Property

- Altering an object type from `INSTANTIABLE` to `NOT INSTANTIABLE` is allowed only if the type has no table dependents.

- Altering an object type from `NOT INSTANTIABLE` to `INSTANTIABLE` is allowed anytime. This change does not affect tables.

#### Modifying the FINAL Property

- Altering an object type from `NOT FINAL` to `FINAL` is only allowed if the target type has no subtypes.

- When you alter an object type from `FINAL` to `NOT FINAL` or vice versa, you must use `CASCADE` to convert data in dependent columns and tables immediately. You may not use the `CASCADE` option `NOT INCLUDING TABLE DATA` to defer converting data.

  - From `NOT FINAL` to `FINAL`, you must use `CASCADE INCLUDING TABLE DATA`.

  - From `FINAL` to `NOT FINAL`, you may use either `CASCADE INCLUDING TABLE DATA` or `CASCADE CONVERT TO SUBSTITUTABLE`.

    When you alter a type from `FINAL` to `NOT` `FINAL`, select the `CASCADE` option based on whether or not you want to insert new subtypes of the altered types into existing columns and tables.

  By default, altering a type from `FINAL` to `NOT` `FINAL` enables you to create new substitutable tables and columns of that type, but it does not automatically make existing columns (or object tables) of that type substitutable. In fact, just the opposite happens: existing columns and tables of the type are marked `NOT SUBSTITUTABLE` `AT` `ALL` `LEVELS`. If any embedded attribute of these columns is substitutable, an error is generated. New subtypes of the altered type cannot be inserted into these preexisting columns and tables.

  To alter an object type to `NOT` `FINAL` in a way that makes existing columns and tables of the type substitutable (assuming that they are not marked `NOT` `SUBSTITUTABLE`), use the `CASCADE` option `CONVERT TO SUBSTITUTABLE`.

  The following example shows the use of `CASCADE` with the option `CONVERT TO SUBSTITUTABLE`:

      CREATE TYPE shape AS OBJECT (
          name VARCHAR2(30),
          area NUMBER)
          FINAL;/
      ALTER TYPE shape NOT FINAL CASCADE CONVERT TO SUBSTITUTABLE;

  This `CASCADE` option marks each existing column as `SUBSTITUTABLE AT ALL LEVELS` and causes a new, hidden column to be added for the TypeId of instances stored in the column. The column can then store subtype instances of the altered type.

### 8.3.8 ALTER TYPE Statement for Type Evolution

Table 8-1 lists some of the important options in the `ALTER` `TYPE` and `ALTER` `TYPE``...CASCADE` statements for altering the attribute or method definition of a type.

Table 8-1 ALTER TYPE Options for Type Evolution

| Option                                           | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    |
|:-------------------------------------------------|:-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `CASCADE `                                       | Propagates the type change to dependent types and tables. The statement aborts if an error is found in dependent types or tables unless the `FORCE` option is specified.<br>If `CASCADE` is specified without other options, then the `INCLUDING TABLE DATA` option for `CASCADE` is implied, and the database converts all table data to the latest type version.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             |
| `INCLUDING TABLE DATA `(Option of `CASCADE`)     | Converts data stored in all user-defined columns to the most recent version of the column type.<br>For each new attribute added to the column type, a new attribute is added to the data and is initialized to `NULL`. For each attribute dropped from the referenced type, the corresponding attribute data is removed from the table. All tablespaces containing the table data must be in read-write mode; otherwise, the statement will not succeed.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       |
| `NOT INCLUDING TABLE DATA `(Option of `CASCADE`) | Leaves column data as is, does not change type version. If an attribute is dropped from a type referenced by a table, the corresponding column of the dropped attribute is not removed from the table. However, the metadata of the column is marked unused. If the dropped attribute is stored out-of-line (for example, `VARRAY`, `LOB`, or nested table attribute), the out-of-line data is not removed. (Unused columns can be removed afterward by using an `ALTER TABLE DROP UNUSED COLUMNS` statement.)<br>This option is useful when you have many large tables and may run out of rollback segments if you convert them all in one transaction. This option enables you to convert the data of each dependent table later in a separate transaction (using an `ALTER TABLE UPGRADE INCLUDING DATA` statement).<br>Specifying this option speeds up the table upgrade because the table data remains in the format of the old type version. However, selecting data from this table requires converting the images stored in the column to the latest type version. This is likely to affect performance during subsequent `SELECT` statements.<br>Because this option only requires updating the table metadata, it does not require that all tablespaces be on-line in read/write mode for the statement to succeed. |
| `FORCE `(Option of `CASCADE`)                    | Forces the system to ignore errors from dependent tables and indexes. Errors are logged in a specified exception table so that they can be queried afterward. Use this option with caution because dependent tables can become inaccessible if some table errors occur.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                        |
| `CONVERT TO SUBSTITUTABLE `(Option of `CASCADE`) | For use when altering a type from `FINAL` to `NOT` `FINAL`: Converts data stored in all user-defined columns to the most recent version of the column type and then marks these existing columns and object tables of the type `SUBSTITUTABLE AT ALL LEVELS` so that they can store any newly created subtypes of the type.<br>If the type is altered to `NOT FINAL` without specifying this option, existing columns and tables of the type are marked `NOT SUBSTITUTABLE AT ALL LEVELS`, and new subtypes of the type cannot be stored in them. You can only store these subtypes in columns and tables created after the type was altered.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  |

**See Also:**

[Oracle Database SQL Language Reference](../sqlrf/ALTER-TYPE.md) for further information about `ALTER` `TYPE` options

### 8.3.9 ALTER TABLE Statement for Type Evolution

You can use `ALTER` `TABLE` to convert table data to the latest version of referenced types. For an example, see "Altering a Type by Adding a Nested Table Attribute".

**See Also:**

- Table 8-1 for a discussion of the `INCLUDING` `DATA` option.

- [Oracle Database SQL Language Reference](../sqlrf/SQL-Statements-ALTER-SYNONYM-to-COMMENT.md) for information about `ALTER` `TABLE` options
