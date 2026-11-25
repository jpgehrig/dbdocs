This section describes SQL object types and references.

Topics:

- Null Objects and Attributes

- Character Length Semantics

- Defining Object Tables with Single Constraints

- Defining Indexes for Object Tables

- Defining Triggers for Object Tables

- Rules for REF Columns and Attributes

- Name Resolution

- Restriction on Using User-Defined Types with a Remote Database

You create Oracle SQL object types with the `CREATE` `TYPE` statement. A typical example of object type creation is shown in Example 2-1.

**See Also:**

- [Oracle Database PL/SQL Language Reference](../lnpls/CREATE-TYPE-statement.md) for information on the `CREATE` `TYPE` SQL statement

- [Oracle Database PL/SQL Language Reference](../lnpls/CREATE-TYPE-BODY-statement.md) for information on the `CREATE` `TYPE` `BODY` SQL statement

### 2.1.1 Null Objects and Attributes

An object whose value is `NULL` is called atomically null.

An [atomically null object](glossary.md) is different from an object that has null values for all its attributes.

In an object with null values, a table column, object attribute, collection, or collection element might be `NULL` if it has been initialized to `NULL` or has not been initialized at all. Usually, a `NULL` value is replaced by an actual value later on. When all the attributes are null, you can still change these attributes and call the object's subprograms or methods. With an atomically null object, you can do neither of these things.

Example 2-1 creates the `contacts` table and defines the `person_typ` object type and two instances of this type.

Example 2-1 Inserting NULLs for Objects in a Table

    CREATE OR REPLACE TYPE person_typ AS OBJECT (
      idno           NUMBER,
      name           VARCHAR2(30),
      phone          VARCHAR2(20),
      MAP MEMBER FUNCTION get_idno RETURN NUMBER,
      MEMBER PROCEDURE display_details ( SELF IN OUT NOCOPY person_typ ) );
    /

    CREATE OR REPLACE TYPE BODY person_typ AS
      MAP MEMBER FUNCTION get_idno RETURN NUMBER IS
      BEGIN
        RETURN idno;
      END;
      MEMBER PROCEDURE display_details ( SELF IN OUT NOCOPY person_typ ) IS
      BEGIN
        -- use the PUT_LINE procedure of the DBMS_OUTPUT package to display details
        DBMS_OUTPUT.PUT_LINE(TO_CHAR(idno) || ' - '  || name || ' - '  || phone);
      END;
    END;
    /
    CREATE TABLE contacts (
      contact        person_typ,
      contact_date   DATE );

    INSERT INTO contacts VALUES (
      person_typ (NULL, NULL, NULL), '24 Jun 2003' );

    INSERT INTO contacts VALUES (
      NULL, '24 Jun 2003' );

Two instances of `person_typ` are inserted into the table and give two different results. In both cases, Oracle Database allocates space in the `contacts` table for a new row and sets its `DATE` column to the value given. But in the first case, Oracle Database allocates space for an object in the `contact` column and sets each of the object's attributes to `NULL`. In the second case, Oracle Database sets the `person_typ` field itself to `NULL` and does not allocate space for an object.

In some cases, you can omit checks for null values. A table row or row object cannot be null. A nested table of objects cannot contain an element whose value is `NULL`.

A nested table or array can be null, so you do need to handle that condition. A null collection is different from an empty one, one that has no elements.

See "[How PL/SQL Treats Uninitialized Objects](declaring-initializing-objects-in-plsql.md)"

### 2.1.2 Character Length Semantics

Lengths for character types `CHAR` and `VARCHAR2` may be specified as a number of characters, instead of bytes, in object attributes and collections even if some of the characters consist of multiple bytes.

To specify character-denominated lengths for `CHAR` and `VARCHAR2` attributes, you add the qualifier `char` to the length specification.

Like `CHAR` and `VARCHAR2`, `NCHAR` and `NVARCHAR2` may also be used as attribute types in objects and collections. `NCHAR` and `NVARCHAR2` are always implicitly measured in terms of characters, so no `char` qualifier is used.

For example, the following statement creates an object with both a character-length `VARCHAR2` attribute and an `NCHAR` attribute:

Example 2-2 Creating the employee_typ Object Using a char Qualifier

    CREATE OR REPLACE TYPE employee_typ AS OBJECT (
      name        VARCHAR2(30 char),
      language    NCHAR(10),
      phone       VARCHAR2(20) );
    /

For `CHAR` and `VARCHAR2` attributes whose length is specified without a `char` qualifier, the `NLS_LENGTH_SEMANTICS` initialization parameter setting (`CHAR` or `BYTE`) indicates the default unit of measure.

[Oracle Database Globalization Support Guide](../nlspg/choosing-character-set.md) for information on character length semantics

### 2.1.3 Defining Object Tables with Single Constraints

You can define constraints on an object table just as you can on other tables.

You can define constraints on the [leaf-level scalar attribute](glossary.md)s of a column object, with the exception of `REF`s that are not scoped.

Example 2-3 places a single constraint, an implicit `PRIMARY` `KEY` constraint, on the `office_id` column of the object table `office_tab`.

Example 2-3 Creating the office_tab Object Table with a Constraint

    -- requires Ex. 2-1
    CREATE OR REPLACE TYPE location_typ AS OBJECT (
      building_no  NUMBER,
      city         VARCHAR2(40) );
    /

    CREATE OR REPLACE TYPE office_typ AS OBJECT (
      office_id    VARCHAR(10),
      office_loc   location_typ,
      occupant     person_typ );/

    CREATE TABLE office_tab OF office_typ (
                 office_id      PRIMARY KEY );

The object type `location_typ` defined in Example 2-3 is the type of the `dept_loc` column in the `department_mgrs` table in Example 2-4.

### 2.1.4 Defining Object Tables with Multiple Constraints

You can define object tables with multiple constraints.

You can define object tables with multiple constraints.

Example 2-4 Creating the department_mgrs Table with Multiple Constraints

Example 2-4 defines constraints on scalar attributes of the `location_typ` objects in the table.

    -- requires Ex. 2-1 and 2-3
    CREATE TABLE department_mgrs (
      dept_no     NUMBER PRIMARY KEY,
      dept_name   CHAR(20),
      dept_mgr    person_typ,
      dept_loc    location_typ,
      CONSTRAINT  dept_loc_cons1
          UNIQUE (dept_loc.building_no, dept_loc.city),
      CONSTRAINT  dept_loc_cons2
           CHECK (dept_loc.city IS NOT NULL) );

    INSERT INTO department_mgrs VALUES
              ( 101, 'Physical Sciences',
               person_typ(65,'Vrinda Mills', '1-1-650-555-0125'),
               location_typ(300, 'Palo Alto'));

See "[Constraints on Objects](constraints-on-objects.md)"

### 2.1.5 Defining Indexes for Object Tables

You can define indexes on an object table or on the storage table for a nested table column or attribute just as you can on other tables.

Define indexes on [leaf-level scalar attribute](glossary.md)s of column objects. You can only define indexes on `REF` attributes or columns if the `REF` is scoped.

Example 2-5 Creating an Index on an Object Type in a Table

    -- requires Ex. 2-1, 2-3,
    CREATE TABLE department_loc (
      dept_no     NUMBER PRIMARY KEY,
      dept_name   CHAR(20),
      dept_addr   location_typ );

    CREATE INDEX  i_dept_addr1
              ON  department_loc (dept_addr.city);

    INSERT INTO department_loc VALUES
              ( 101, 'Physical Sciences',
               location_typ(300, 'Palo Alto'));
    INSERT INTO department_loc VALUES
              ( 104, 'Life Sciences',
               location_typ(400, 'Menlo Park'));
    INSERT INTO department_loc VALUES
              ( 103, 'Biological Sciences',
               location_typ(500, 'Redwood Shores'));

This example, Example 2-5, indexes `city`, which is a leaf-level scalar attribute of the column object `dept_addr`.

Wherever Oracle Database expects a column name in an index definition, you can also specify a scalar attribute of a column object.

For an example of an index on a nested table, see [Storing Elements of Nested Tables](collection-data-types.md).

### 2.1.6 Defining Triggers for Object Tables

You can define triggers on an object table just as you can on other tables.

You cannot define a trigger on the storage table for a nested table column or attribute. You cannot modify `LOB` values in a trigger body. Otherwise, there are no special restrictions on using object types with triggers.

Example 2-6 defines a trigger on the `office_tab` table defined in "Defining Object Tables with Single Constraints".

Example 2-6 Creating a Trigger on Objects in a Table

    -- requires Ex. 2-1 and 2-3
    CREATE TABLE movement (
         idno           NUMBER,
         old_office     location_typ,
         new_office     location_typ );

    CREATE TRIGGER trigger1
      BEFORE UPDATE
                 OF  office_loc
                 ON  office_tab
       FOR EACH ROW
               WHEN  (new.office_loc.city = 'Redwood Shores')
       BEGIN
         IF :new.office_loc.building_no = 600 THEN
          INSERT INTO movement (idno, old_office, new_office)
           VALUES (:old.occupant.idno, :old.office_loc, :new.office_loc);
         END IF;
       END;/
    INSERT INTO office_tab VALUES
        ('BE32', location_typ(300, 'Palo Alto' ),person_typ(280, 'John Chan',
           '415-555-0101'));

    UPDATE office_tab set office_loc =location_typ(600, 'Redwood Shores')
      where office_id = 'BE32';

    select * from office_tab;

    select * from movement;

See"[INSTEAD OF Triggers to Control Mutating and Validation](object-view-manipulations.md)"

### 2.1.7 Rules for REF Columns and Attributes

Rules for `REF` columns and attributes can be enforced by the use of constraints.

In Oracle Database, a `REF` column or attribute can be unconstrained or constrained using a `SCOPE` clause or a referential constraint clause. When a `REF` column is unconstrained, it may store object references to row objects contained in any object table of the corresponding object type.

Oracle Database does not ensure that the object references stored in such columns point to valid and existing row objects. Therefore, `REF` columns may contain object references that do not point to any existing row object. Such `REF` values are referred to as dangling references.

A `SCOPE` constraint can be applied to a specific object table. All the `REF` values stored in a column with a `SCOPE` constraint point at row objects of the table specified in the `SCOPE` clause. The `REF` values may, however, be dangling.

A `REF` column may be constrained with a `REFERENTIAL` constraint similar to the specification for foreign keys. The rules for referential constraints apply to such columns. That is, the object reference stored in these columns must point to a valid and existing row object in the specified object table.

`PRIMARY` `KEY` constraints cannot be specified for `REF` columns. However, you can specify `NOT` `NULL` constraints for such columns.

**See Also:**

- "[References to Row Objects](key-features-object-relational-model.md)"

- "[Substitution of REF Columns and Attributes](inheritance-in-sql-object-types.md)"

### 2.1.8 Name Resolution

There are several ways to resolve names in Oracle Database.

Oracle SQL lets you omit qualifying table names in some relational operations.

For example, if `dept_addr` is a column in the `department_loc` table and `old_office` is a column in the `movement` table, you can use the following:

    SELECT * FROM department_loc WHERE EXISTS
      (SELECT * FROM movement WHERE dept_addr = old_office);

Oracle Database determines which table each column belongs to.

Using dot notation, you can qualify the column names with table names or table aliases to make things more maintainable. For example:

Example 2-7 Using the Dot Notation for Name Resolution

    -- requires Ex. 2-1, 2-3, 2-5, and 2-6
    SELECT * FROM department_loc WHERE EXISTS
      (SELECT * FROM movement WHERE department_loc.dept_addr = movement.old_office);

    SELECT * FROM department_loc d WHERE EXISTS
      (SELECT * FROM movement m WHERE d.dept_addr = m.old_office);

In some cases, object-relational features require you to specify the table aliases.

#### 2.1.8.1 When Table Aliases Are Required

Table aliases can be required to avoid problems resolving references.

Oracle Database requires you to use a table alias to qualify any dot-notational reference to subprograms or attributes of objects, to avoid inner capture and similar problems resolving references.

Inner capture is a situation caused by using unqualified names. For example, if you add an `assignment` column to `depts` and forget to change the query, Oracle Database automatically recompiles the query so that the inner `SELECT` uses the `assignment` column from the `depts` table.

Use of a table alias is optional when referencing top-level attributes of an object table directly, without using the dot notation. For example, the following statements define two tables that contain the `person_typ` object type. `person_obj_table` is an object table for objects of type `person_typ`, and `contacts` is a relational table that contains a column of the object `person_typ`.

The following queries show some correct and incorrect ways to reference attribute `idno`:

**Note:**

These statements are not related to other examples in this chapter.

    #1 SELECT idno FROM person_obj_table; --Correct
    #2 SELECT contact.idno FROM contacts; --Illegal
    #3 SELECT contacts.contact.idno FROM contacts; --Illegal
    #4 SELECT p.contact.idno FROM contacts p; --Correct

- In \#1, `idno` is the name of a column of `person_obj_table`. It references this top-level attribute directly, without using the dot notation, so no table alias is required.

- In \#2, `idno` is the name of an attribute of the `person_typ` object in the column named `contact`. This reference uses the dot notation and so requires a table alias, as shown in \#4.

- \#3 uses the table name itself to qualify the reference. This is incorrect; a table alias is required.

You must qualify a reference to an object attribute or subprogram with a table alias rather than a table name even if the table name is itself qualified by a schema name.

For example, the following expression incorrectly refers to the `HR` schema, `department_loc` table, `dept_addr` column, and `city` attribute of that column. The expression is incorrect because `department_loc` is a table name, not an alias.

`HR.department_loc.dept_addr.city`

The same requirement applies to attribute references that use `REF`s.

Table aliases should uniquely pick out the same table throughout a query and should not be the same as schema names that could legally appear in the query.

**Note:**

Oracle recommends that you define table aliases in all `UPDATE`, `DELETE`, and `SELECT` statements and subqueries and use them to qualify column references whether or not the columns contain object types.

### 2.1.9 Restriction on Using User-Defined Types with a Remote Database

Objects or user-defined types (specifically, types declared with a SQL `CREATE` `TYPE` statement, as opposed to types declared within a PL/SQL package) are currently useful only within a single database.

Oracle Database restricts use of a database link as follows:

- You cannot connect to a remote database to select, insert, or update a user-defined type or an object `REF` on a remote table.

  You can use the `CREATE` `TYPE` statement with the optional keyword `OID` to create a user-specified object identifier (OID) that allows an object type to be used in multiple databases. See the discussion on assigning an OID to an object type in the [Oracle Database Data Cartridge Developer's Guide](../addci/defining-object-types-for-data-cartridges.md).

- You cannot use database links within PL/SQL code to declare a local variable of a remote user-defined type.

- You cannot convey a user-defined type argument or return value in a PL/SQL remote procedure call.
