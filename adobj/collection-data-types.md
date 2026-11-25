Oracle supports the varray and nested table collection data types.

- A varray is an ordered collection of elements.

- A nested table can have any number of elements and is unordered.

If you need to store only a fixed number of items, or loop through the elements in order, or often need to retrieve and manipulate the entire collection as a value, then use a varray.

If you need to run efficient queries on a collection, handle arbitrary numbers of elements, or perform mass insert, update, or delete operations, then use a nested table.

Topics:

- Creating a Collection Type

- Creating a Collection Type

- Creating an Instance of a VARRAY or Nested Table

- Using the Constructor Method to Insert Values into a Nested Table

- About Varrays

- Nested Tables

- Increasing the Size and Precision of VARRAY and Nested Table Elements

- Increasing VARRAY Limit Size

- Creating a Varray Containing LOB References

**See Also:**

For more information on using nested tables, see "[Design Considerations for Collections](design-considerations-for-collections.md)".

### 5.1.1 Creating a Collection Type

You use `CREATE TYPE` and `CREATE TYPE BODY` to create a nested table type.

Example 5-1 demonstrates creating a `person_typ` object and a `people_typ` as a nested table type of `person_typ` objects, which are both used in other examples.

Example 5-1 CREATE TYPE person_typ for Subsequent Examples

    CREATE TYPE person_typ AS OBJECT (
      idno           NUMBER,
      name           VARCHAR2(30),
      phone          VARCHAR2(20),
      MAP MEMBER FUNCTION get_idno RETURN NUMBER,
      MEMBER PROCEDURE display_details ( SELF IN OUT NOCOPY person_typ ) );
    /

    CREATE TYPE BODY person_typ AS
      MAP MEMBER FUNCTION get_idno RETURN NUMBER IS
      BEGIN
        RETURN idno;
      END;
      MEMBER PROCEDURE display_details ( SELF IN OUT NOCOPY person_typ ) IS
      BEGIN
        -- use the put_line procedure of the DBMS_OUTPUT package to display details
        DBMS_OUTPUT.put_line(TO_CHAR(idno) || ' - '  || name || ' - '  || phone);
      END;
    END;
    /

    CREATE TYPE people_typ AS TABLE OF person_typ; -- nested table type
    /

### 5.1.2 Creating an Instance of a VARRAY or Nested Table

You create an instance of a collection type by calling the constructor method of the type, in the same way that you create an instance of any other object type .

The name of a constructor method is simply the name of the type. You specify the elements of the collection as a comma-delimited list of arguments to the method, for example.

    ( person_typ(1, 'John Smith', '1-650-555-0135'),

Calling a constructor method with an empty list creates an empty collection of that type. Note that an empty collection is an actual collection that happens to be empty; it is not the same as a null collection. See "[Design Considerations for Nested Tables](design-considerations-for-collections.md)" for more information on using nested tables.

### 5.1.3 Using the Constructor Method to Insert Values into a Nested Table

You can use a constructor method in a SQL statement to insert values into a nested table.

Example 5-2 first creates a table that contains an instance of the nested table type `people_typ`, named `people_column`, and then shows how to use the constructor method in a SQL statement to insert values into `people_typ`. This example uses a literal invocation of the constructor method.

Example 5-2 Using the Constructor Method to Insert Values into a Nested Table

    -- Requires Ex. 5-1
    CREATE TABLE people_tab (
        group_no NUMBER,
        people_column people_typ )  -- an instance of nested table
        NESTED TABLE people_column STORE AS people_column_nt; -- storage table for NT

    INSERT INTO people_tab VALUES (
                100,
                people_typ( person_typ(1, 'John Smith', '1-650-555-0135'),
                            person_typ(2, 'Diane Smith', NULL)));

### 5.1.4 Invoking Constructors Literally to Specify Defaults

When you declare a table column to be of an object type or collection type, you can include a `DEFAULT` clause.

This provides a value to use in cases where you do not explicitly specify a value for the column.

The `DEFAULT` clause must contain a literal invocation of the constructor method for that object or collection.

Example 5-3 shows how to use literal invocations of constructor methods to specify defaults for the `person_typ` object and the `people_typ` nested table:

Example 5-3 Using Literal Invocations of Constructor Methods to Specify Defaults

    -- requires Ex. 5-1
    CREATE TABLE department_persons (
      dept_no    NUMBER PRIMARY KEY,
      dept_name  CHAR(20),
      dept_mgr   person_typ DEFAULT person_typ(10,'John Doe',NULL),
      dept_emps  people_typ DEFAULT people_typ() ) -- instance of nested table type
      NESTED TABLE dept_emps STORE AS dept_emps_tab;

    INSERT INTO department_persons VALUES
       ( 101, 'Physical Sciences', person_typ(65,'Vrinda Mills', '1-650-555-0125'),
               people_typ( person_typ(1, 'John Smith', '1-650-555-0135'),
                            person_typ(2, 'Diane Smith', NULL) ) );
    INSERT INTO department_persons VALUES
      ( 104, 'Life Sciences', person_typ(70,'James Hall', '1-415-555-0101'),
        people_typ() ); -- an empty people_typ table

Note that `people_typ()` is a literal invocation of the constructor method for an empty `people_typ` nested table.

The `department_persons` table can be queried in two ways as shown in [Example 5-16](operations-on-collection-data-types.md) and [Example 5-17](operations-on-collection-data-types.md).

### 5.1.5 About Varrays

A varray is an ordered set of data elements. All elements of a given varray are of the same data type or a subtype of the declared one. Each element has an index, which is a number corresponding to the position of the element in the array. The index number is used to access a specific element.

When you define a varray, you specify the maximum number of elements it can contain, although you can change this number later. The number of elements in an array is the size of the array.

The following statement creates an array type `email_list_arr` that has no more than ten elements, each of data type `VARCHAR2(80)`.

    CREATE TYPE email_list_arr AS VARRAY(10) OF VARCHAR2(80);
    /

### 5.1.6 Creating and Populating a VARRAY

Creating an array type, as with a SQL object type, does not allocate space.

It defines a data type, which you can use as:

- The data type of a column of a relational table.

- An object type attribute.

- The type of a PL/SQL variable, parameter, or function return value.

Example 5-4 creates a `VARRAY` type that is an array of an object type. The `phone_varray_typ` `VARRAY` type is used as a data type for a column in the `dept_phone_list` table. The `INSERT` statements show how to insert values into `phone_varray_typ` by invoking the constructors for the varray `phone_varray_typ` and the object `phone_typ`.

You can create a `VARRAY` type of `XMLType` or `LOB` type for procedural purposes, such as in PL/SQL or view queries. However, database storage for varrays of these types is not supported. Thus you cannot create an object table or an object type column of a varray type of `XMLType` or `LOB` type.

Example 5-4 Creating and Populating a VARRAY Data Type

    CREATE TYPE phone_typ AS OBJECT (
        country_code   VARCHAR2(2),
        area_code      VARCHAR2(3),
        ph_number      VARCHAR2(7));
    /
    CREATE TYPE phone_varray_typ AS VARRAY(5) OF phone_typ;
    /
    CREATE TABLE dept_phone_list (
      dept_no NUMBER(5),
      phone_list phone_varray_typ);

    INSERT INTO dept_phone_list VALUES (
       100,
       phone_varray_typ( phone_typ ('01', '650', '5550123'),
                          phone_typ ('01', '650', '5550148'),
                          phone_typ ('01', '650', '5550192')));

A varray is normally stored inline, that is, in the same tablespace as the other data in its row. If it is sufficiently large, Oracle stores it as a `BLOB`.

**See Also:**

- "[Storage Considerations for Varrays](design-considerations-for-collections.md)"

- See [Oracle Database SQL Language Reference](../sqlrf/CREATE-TABLE.md) for information and examples on the `STORE` `AS` `LOB` clause of the `CREATE` `TABLE` statement.

### 5.1.7 Nested Tables

A nested table is an unordered set of data elements, all of the same data type. No maximum is specified in the definition of the table, and the order of the elements is not preserved. You select, insert, delete, and update in a nested table just as you do with ordinary tables using the `TABLE` expression.

A nested table can be viewed as a single column. If the column in a nested table is an object type, the table can also be viewed as a multi-column table, with a column for each attribute of the object type.

Topics:

- Creating Nested Tables

- Storing Elements of Nested Tables

- Specifying a Tablespace When Storing a Nested Table

#### 5.1.7.1 Creating Nested Tables

To create nested table types, use the `CREATE` `TYPE` ... `AS` `TABLE` `OF` statement. For example:

    CREATE TYPE people_typ AS TABLE OF person_typ;

A table type definition does not allocate space. It defines a type, which you can use as:

- The data type of a column of a relational table.

- An object type attribute.

- A PL/SQL variable, parameter, or function return type.

#### 5.1.7.2 Storing Elements of Nested Tables

Elements of a nested table are actually stored in a separate storage table.

Oracle stores nested table data in a single storage table associated with the object table for both nested table types that are columns in a relational table or attributes in an object table. The storage table contains a column that identifies the parent table row or object that each element of the nested table belongs to. See [Figure 9-2](design-considerations-for-collections.md).

The `NESTED` `TABLE..STORE AS` clause specifies storage names for nested tables. Storage names are used to create an index on a nested table.

Example 5-5 demonstrates creating and populating a nested table, and specifying the nested table storage using the `person_typ` object and the `people_typ` nested table as defined in Example 5-1.

Example 5-5 Creating and Populating Simple Nested Tables

    -- Requires 5-1
    CREATE TABLE students (
       graduation DATE,
       math_majors people_typ, -- nested tables (empty)
       chem_majors people_typ,
       physics_majors people_typ)
      NESTED TABLE math_majors STORE AS math_majors_nt  -- storage tables
      NESTED TABLE chem_majors STORE AS chem_majors_nt
      NESTED TABLE physics_majors STORE AS physics_majors_nt;

    CREATE INDEX math_idno_idx ON math_majors_nt(idno);
    CREATE INDEX chem_idno_idx ON chem_majors_nt(idno);
    CREATE INDEX physics_idno_idx ON physics_majors_nt(idno);

    INSERT INTO students (graduation) VALUES ('01-JUN-03');
    UPDATE students
      SET math_majors =
            people_typ (person_typ(12, 'Bob Jones', '650-555-0130'),
                        person_typ(31, 'Sarah Chen', '415-555-0120'),
                        person_typ(45, 'Chris Woods', '415-555-0124')),
          chem_majors =
            people_typ (person_typ(51, 'Joe Lane', '650-555-0140'),
                        person_typ(31, 'Sarah Chen', '415-555-0120'),
                        person_typ(52, 'Kim Patel', '650-555-0135')),
       physics_majors =
            people_typ (person_typ(12, 'Bob Jones', '650-555-0130'),
                        person_typ(45, 'Chris Woods', '415-555-0124'))
    WHERE graduation = '01-JUN-03';

    SELECT m.idno math_id, c.idno chem_id, p.idno physics_id  FROM students s,
     TABLE(s.math_majors) m, TABLE(s.chem_majors) c, TABLE(s.physics_majors) p;

A convenient way to access the elements of a nested table individually is to use a nested cursor or the `TABLE` function. See "[Collection Querying](operations-on-collection-data-types.md)".

#### 5.1.7.3 Specifying a Tablespace When Storing a Nested Table

A nested table can be stored in a different tablespace than its parent table.

In Example 5-6, the nested table is stored in the `system` tablespace:

Example 5-6 Specifying a Different Tablespace for Storing a Nested Table

    -- Requires Ex. 5-1, must remove code in Ex. 5-2 if created
    CREATE TABLE people_tab (
        people_column people_typ )
        NESTED TABLE people_column STORE AS people_column_nt (TABLESPACE system);

If the `TABLESPACE` clause is not specified, then the storage table of the nested table is created in the tablespace where the parent table is created. For multilevel nested tables, Oracle creates the child table in the same tablespace as its immediately preceding parent table.

You can issue an `ALTER` `TABLE..` `MOVE` statement to move a table to a different tablespace. If you do this on a table with nested table columns, only the parent table moves; no action is taken on the storage tables of the nested table. To move a storage table for a nested table to a different tablespace, issue `ALTER` `TABLE..` `MOVE` on the storage table. For example:

    ALTER TABLE people_tab MOVE TABLESPACE system;  -- moving table
    ALTER TABLE people_column_nt MOVE TABLESPACE example; -- moving storage table

Now the `people_tab` table is in the `system` tablespace and the nested table storage is stored in the `example` tablespace.

### 5.1.8 Increasing the Size and Precision of VARRAY and Nested Table Elements

You can increase the size of the variable character or `RAW` type, or increase the precision of the numeric type when the element type of a `VARRAY` type or nested table type is a variable character, or a `RAW` or numeric type.

A new type version is generated for the `VARRAY` type or nested table type.

You make these changes using an `ALTER` `TYPE..MODIFY` statement, which has this option:

`CASCADE`: Propagates the change to its type and table dependents

**See Also:**

"[ALTER TYPE Statement for Type Evolution](type-evolution.md)" for further description of `CASCADE`

Example 5-7 increases the sizes of a `VARRAY` and a nested table element type.

Example 5-7 Increasing the Size of an Element Type in a VARRAY and Nested Table

    CREATE TYPE email_list_arr AS VARRAY(10) OF VARCHAR2(80);
    /
    ALTER TYPE email_list_arr MODIFY ELEMENT TYPE VARCHAR2(100) CASCADE;

    CREATE TYPE email_list_tab AS TABLE OF VARCHAR2(30);
    /
    ALTER TYPE email_list_tab MODIFY ELEMENT TYPE VARCHAR2(40) CASCADE;

### 5.1.9 Increasing VARRAY Limit Size

The `ALTER` `TYPE` ... `MODIFY` `LIMIT` syntax allows you to increase the number of elements of a `VARRAY` type.

If you increase the number of elements of a `VARRAY` type, a new type version is generated for the `VARRAY` type, and becomes part of the type change history.

The `ALTER` `TYPE` ... `MODIFY` `LIMIT` statement has these options:

- `INVALIDATE`: Invalidates all dependent objects

- `CASCADE`: Propagates the change to its type and table dependents

Example 5-8 Increasing the VARRAY Limit Size

    -- if you have already creating following types, drop them.
    DROP TYPE email_list_tab FORCE;
    DROP TYPE email_list_arr FORCE;
    CREATE TYPE email_list_arr AS VARRAY(10) OF VARCHAR2(80);
    /
    CREATE TYPE email_list_typ AS OBJECT (
        section_no   NUMBER,
        emails       email_list_arr);
    /

    CREATE TYPE email_varray_typ AS VARRAY(5) OF email_list_typ;
    /

    ALTER TYPE email_varray_typ MODIFY LIMIT 100 INVALIDATE;

When a `VARRAY` type is altered, changes are propagated to the dependent tables.

**See Also:**

"[About Propagating VARRAY Size Change](design-considerations-for-collections.md)".

### 5.1.10 Creating a Varray Containing LOB References

To create a varray of LOB references, first define a `VARRAY` type of type `REF`.

Note: The following example refers to `email_list_typ` which was defined in Example 5-8. This example creates a table `dept_email_list` and defines a column `email_addrs` of the array type in it.

Example 5-9 Creating a VARRAY Containing LOB References

    -- Requires Ex. 5-8
    CREATE TYPE ref_email_varray_typ AS VARRAY(5) OF REF email_list_typ;
    /

    CREATE TABLE dept_email_list (
      dept_no NUMBER,
      email_addrs ref_email_varray_typ)
      VARRAY email_addrs STORE AS LOB dept_emails_lob3;
