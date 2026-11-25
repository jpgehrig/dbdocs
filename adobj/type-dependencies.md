Type dependencies fall into two broad categories:

- Situations where types depend upon each other for their definitions, where one type might be part of the definition of another type.

- Situations where creating or dropping types is complicated by dependencies that the type has such, as tables or types.

This section covers the following topics:

- Creating Incomplete Types

- Completing Incomplete Types

- Recompiling a Type Manually

- Using CREATE OR REPLACE TYPE with Type and Table Dependencies

- Type Dependencies of Substitutable Tables and Columns

- The DROP TYPE FORCE Option

- [Creating a Type Synonym](synonyms-for-object-types.md)

- [Using a Type Synonym](synonyms-for-object-types.md)

### 7.2.1 Creating Incomplete Types

Types that depend on each other for their definitions, either directly or through intermediate types, are called mutually dependent. For example, you might want to define object types `employee` and `department` in such a way that one attribute of `employee` is the department the employee belongs to and one attribute of `department` is the employee who manages the department.

If you visualize a diagram with arrows showing the relationships among a set of mutually dependent types, the connections form a loop. To define such a circular dependency, you must use `REF`s for at least one segment of the circle.

For example, you can define the types shown in Example 7-7.

Example 7-7 Creating Dependent Object Types

    -- Requires Ex. 7-1 and password
    CONNECT user1
    -- Enter password
    ALTER SESSION SET PLSQL_WARNINGS = 'enable:all';

    CREATE TYPE department; // a placeholder
    /

    CREATE TYPE employee AS OBJECT (
      name    VARCHAR2(30),
      dept    REF department,
      supv    REF employee );
    /

    CREATE TYPE emp_list AS TABLE OF employee;
    /

    CREATE TYPE department AS OBJECT (
      name    VARCHAR2(30),
      mgr     REF employee,
      staff   emp_list );
    /

This is a legal set of mutually dependent types and a legal sequence of SQL DDL statements. Oracle database compiles it without errors.

Notice that the code in Example 7-7 creates the type `department` twice. The first statement is an optional, incomplete declaration of `department` that serves as a placeholder for the `REF` attribute of `employee` to point to. The declaration is incomplete in that it omits the `AS` `OBJECT` phrase and lists no attributes or methods. These are specified later in the full declaration that completes the type. In the meantime, `department` is created as an incomplete object type. This enables the compilation of `employee` to proceed without errors.

If you do not create incomplete types as placeholders, types that refer to the missing types still compile, but the compilation proceeds with errors. For example, if `department` did not exist at all, Oracle database would create it as an incomplete type and compile `employee` with errors. Then `employee` would be recompiled the next time that some operation accesses it. This time, if all the types it depends on have been created and its dependencies are satisfied, it compiles without errors.

Incomplete types also enable you to create types that contain `REF` attributes to a subtype that has not yet been created. To create such a supertype, first create an incomplete type of the subtype to be referenced. Create the complete subtype after you create the supertype.

### 7.2.2 Completing Incomplete Types

When you have created all the types referenced by an incomplete type, complete the declaration of the incomplete type, because there is no longer any need for it to remain incomplete.

Completing the type recompiles it and enables the system to release various locks. You complete the type with a `CREATE` `TYPE` statement.

- Execute a `CREATE` `TYPE` statement that specifies the attributes and methods of the type, as shown at the end of Example 7-7.

Also, you must complete any incomplete types that the database creates for you. If, as discussed in the preceding section, you did not explicitly create `department` as an incomplete type, then the database did. In this case, you still need to complete it.

You must complete an incomplete object type as an object type: you cannot complete an object type as a collection type (a nested table type or an array type). The only alternative is to drop the type.

### 7.2.3 Recompiling a Type Manually

If a type was created with compilation errors, and you attempt an operation on it, such as creating tables or inserting rows, you may receive an error. You need to recompile the type before attempting the operation. You recompile with an `ALTER` `TYPE` statement.

- Execute an `ALTER` `TYPE` `typename` `COMPILE` statement. After you have successfully compiled the type, attempt the operation again.

### 7.2.4 Using CREATE OR REPLACE TYPE with Type and Table Dependencies

The `CREATE` `OR` `REPLACE` `TYPE` statement throws an error if the type being replaced has table or type dependencies. This applies to objects, varrays, and nested table types. This also applies to type dependencies involving either inheritance or type composition (embedding one type into another). The latter might be a situation where one type is attribute of another.

Using the `FORCE` option with a `CREATE` `OR` `REPLACE` `TYPE` statement enables you to replace a type if it has type dependencies, but not table dependencies. Table dependencies still cause errors.

- Use the `FORCE` option with a `CREATE` `OR` `REPLACE` `TYPE` statement to replace a type if it has type dependencies.

Example 7-8 shows a `CREATE` `OR` `REPLACE` statement (second statement) that fails due to a type dependency.

Example 7-8 CREATE OR REPLACE Type and Table Failure

    SQL> CREATE type t1 AS OBJECT (a number) not final;
      2  /
    Type created.

    SQL> CREATE TYPE t2 UNDER t1 (b varchar(10));
      2  /
    Type created.

    SQL> CREATE OR REPLACE TYPE t1 AS OBJECT (c varchar(20));
      2  /
    CREATE OR REPLACE TYPE t1 AS OBJECT (c varchar(20));
    *
    ERROR at line 1:
    ORA-02303: cannot drop or replace a type with type or table dependents

### 7.2.5  Creating or Replacing Type with Force

A `CREATE` `OR` `REPLACE` `FORCE` statement fails if the type has a table dependency because a type with a table dependency cannot be replaced.

Example 7-9 shows code in which a `CREATE` `OR` `REPLACE` `FORCE` statement succeeds in replacing a type that has a type dependency and then creates a table using the parent type. However, the final `CREATE` `OR` `REPLACE` `FORCE` statement fails because the type now has a table dependency and even with the `FORCE` option, a type with a table dependency cannot be replaced.

**See Also:**

[Oracle Database PL/SQL Language Reference](../lnpls/CREATE-TYPE-statement.md) for details of the `CREATE` `OR REPLACE TYPE` SQL statement

Example 7-9 CREATE OR REPLACE with FORCE

    SQL> CREATE OR REPLACE TYPE t1 FORCE AS OBJECT (c varchar(20));
      2  /
    Type created.

    SQL> CREATE TABLE tb1 (c1 t1);
    Table created.

    SQL> CREATE OR REPLACE TYPE t1 FORCE AS OBJECT (d number);
      2  /
    CREATE OR REPLACE TYPE t1 FORCE AS OBJECT (d number);
    *
    ERROR at line 1:
    ORA-22866: cannot replace a type with table dependents

### 7.2.6 Type Dependencies of Substitutable Tables and Columns

A substitutable table or column of a specific type is dependent not only on that type but on all subtypes of the type as well.

This is because a hidden column is added to the table for each attribute added in a subtype of the type. The hidden columns are added even if the substitutable table or column contains no data of that subtype.

In Example 7-10, a `persons` table of type `person_typ` is dependent not only on `person_typ` but also on the `person_typ` subtypes `student_typ` and `part_time_student_typ`.

If you attempt to drop a subtype that has a dependent type, table, or column, the `DROP` `TYPE` statement returns an error and aborts. Consequently, trying to drop a `part_time_student_typ` raises an error because of the dependent `persons` table.

If dependent tables or columns exist but contain no data of the type being dropped, you can use the `VALIDATE` keyword to drop the type. The `VALIDATE` keyword causes Oracle database to check for actual stored instances of the specified type and to drop the type if none are found. This also removes hidden columns associated with attributes unique to the type.

In Example 7-10, the first `DROP` `TYPE` statement fails because `part_time_student_typ` has a dependent table (`persons`). But if `persons` contains no instances of `part_time_student_typ` (nor does any other dependent table or column), the `VALIDATE` keyword causes the second `DROP` `TYPE` statement to succeed.

Example 7-10 DROP TYPE with and without VALIDATE

    CREATE TYPE person_typ AS OBJECT (
      idno           NUMBER,
      name           VARCHAR2(30),
      phone          VARCHAR2(20))
      NOT FINAL;
    /
    CREATE TYPE student_typ UNDER person_typ (
        dept_id NUMBER,
        major VARCHAR2(30))
    NOT FINAL;
    /
    CREATE TYPE part_time_student_typ UNDER student_typ (number_hours NUMBER);
    /
    CREATE TABLE persons OF person_typ;
    -- Following generates an error due to presence of Persons table
    DROP TYPE part_time_student_typ -- incorrect statement;
    -- Following succeeds if there are no stored instances of part_time_student_typ
    DROP TYPE part_time_student_typ VALIDATE;

**Note:**

Oracle recommends that you always use the `VALIDATE` option while dropping subtypes.

**See Also:**

"[Type Substitution in a Type Hierarchy](inheritance-in-sql-object-types.md)" for further explanation of substitutability

### 7.2.7 The DROP TYPE FORCE Option

The `DROP` `TYPE` statement has a `FORCE` option that causes the type to be dropped even though it may have dependent types or tables.

Use the `FORCE` option with great care, because any dependent types or tables that do exist are marked invalid and become inaccessible when the type is dropped. Data in a table that is marked invalid for this reason can never be accessed again. The only action that can be performed on such a table is to drop it.

**See Also:**

See "[Type Evolution](type-evolution.md)" for information about how to alter a type.
