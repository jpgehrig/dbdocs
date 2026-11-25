Several functions and operators are particularly useful for working with objects and references to objects.

Examples are given throughout this book.

**Note:**

In PL/SQL the `VALUE`, `REF` and `DEREF` functions can appear only in a SQL statement. For information about SQL functions, see [Oracle Database SQL Language Reference](../sqlrf/Functions.md).

Topics:

- CAST

- CURSOR

- DEREF

- IS OF type

- REF

- SYS_TYPEID

- TABLE()

- TREAT

- VALUE

### 2.4.1 CAST

`CAST` converts one built-in data type or collection-typed value into another built-in data type or collection-typed value. For example:

Example 2-33 Using the CAST Function

    CREATE TYPE person_list_typ AS TABLE OF person_typ;/

    SELECT CAST(COLLECT(contact) AS person_list_typ)
      FROM contacts;

**See Also:**

For more information about the SQL `CAST` function, [Oracle Database SQL Language Reference](../sqlrf/CAST.md).

### 2.4.2 CURSOR

A `CURSOR` expression returns a nested cursor.

The cursor form of expression is equivalent to the PL/SQL `REF` `CURSOR` and can be passed as a `REF` `CURSOR` argument to a function.

**See Also:**

For more information about the SQL `CURSOR` expression, see [Oracle Database SQL Language Reference](../sqlrf/Expressions.md).

### 2.4.3 DEREF

The `DEREF` function in a SQL statement returns the object instance corresponding to a `REF`.

The object instance returned by `DEREF` may be of the declared type of the `REF` or any of its subtypes.

For example, the following statement returns `person_typ` objects from the table `contact_ref`.

Example 2-34 Using the DEREF Function

    -- Using the DEREF Function example, not sample schema

    SELECT DEREF(c.contact_ref), c.contact_date
      FROM contacts_ref c;

**See Also:**

- "[Dereferencing REFs](key-features-object-relational-model.md)"

- For more information about the SQL `DEREF` function, see [Oracle Database SQL Language Reference](../sqlrf/DEREF.md).

### 2.4.4 IS OF type

The `IS` `OF` `type` predicate tests object instances for the level of specialization of their type.

For example, the following query retrieves all student instances (including any subtypes of students) stored in the `person_obj_table` table.

Example 2-35 Using the IS OF type Operator to Query Value of a Subtype

    -- Using the IS OF type Operator to query Value of a subtype

    SELECT VALUE(p)
      FROM person_obj_table p
    WHERE VALUE(p) IS OF (student_typ);

For any object that is not of a specified subtype, or a subtype of a specified subtype, `IS` `OF` returns `FALSE`. Subtypes of a specified subtype are just more specialized versions of the specified subtype. If you want to exclude such subtypes, you can use the `ONLY` keyword. This keyword causes `IS` `OF` to return `FALSE` for all types except the specified types.

In the following example, the statement tests objects in object table `person_obj_table`, which contains persons, employees, and students, and returns `REF`s just to objects of the two specified person subtypes `employee_typ`, `student_typ`, and their subtypes, if any:

    -- Using the IS OF type Operator to query for multiple subtypes

    SELECT REF(p)
      FROM person_obj_table p
    WHERE VALUE(p) IS OF (employee_typ, student_typ);

Here is a similar example in PL/SQL. The code does something if the person is an employee or student:

    -- Using the IS OF type Operator with PL/SQL

    DECLARE
      var person_typ;
    BEGIN
      var := employee_typ(55, 'Jane Smith', '1-650-555-0144', 100, 'Jennifer Nelson');
      IF var IS OF (employee_typ, student_typ) THEN
         DBMS_OUTPUT.PUT_LINE('Var is an employee_typ or student_typ object.');
      ELSE
         DBMS_OUTPUT.PUT_LINE('Var is not an employee_typ or student_typ object.');
      END IF;
    END;
    /

The following statement returns only students whose most specific or specialized type is `student_typ`. If the table or view contains any objects of a subtype of `student_typ`, such as `part_time_student_typ`, these are excluded. The example uses the `TREAT` function to convert objects that are students to `student_typ` from the declared type of the view, `person_typ`:

    -- Using the IS OF type Operator to query for specific subtype only

    SELECT TREAT(VALUE(p) AS student_typ)
      FROM person_obj_table p
    WHERE VALUE(p) IS OF(ONLY student_typ);

To test the type of the object that a `REF` points to, you can use the `DEREF` function to dereference the `REF` before testing with the `IS` `OF` `type` predicate.

For example, if `contact_ref` is declared to be `REF` `person_typ`, you can get just the rows for students as follows:

    -- Using the IS OF type Operator with DEREF

    SELECT *
      FROM contacts_ref
    WHERE DEREF(contact_ref) IS OF (student_typ);

**See Also:**

For more information about the SQL `IS` `OF` `type` condition, see [Oracle Database SQL Language Reference](../sqlrf/Conditions.md).

### 2.4.5 REF

The `REF` function in a SQL statement takes as an argument a correlation name (or table alias) for an object table or view and returns a reference (a `REF`) to an object instance from that table or view.

The `REF` function may return references to objects of the declared type of the table, view, or any of its subtypes. For example, the following statement returns the references to all persons, including references to students and employees, whose `idno` attribute is 12:

Example 2-36 Using the REF Function

    -- Using the REF Function example, not sample schema

    SELECT REF(p)
      FROM person_obj_table p
      WHERE p.idno = 12;

**See Also:**

For more information about the SQL `REF` function, see [Oracle Database SQL Language Reference](../sqlrf/REF.md).

### 2.4.6 SYS_TYPEID

The `SYS_TYPEID` function can be used in a query to return the typeid (a hidden type) of the most specific type of the object instance passed as an argument.

The most specific type of an object instance is the type that the instance belongs to, that is, the farthest removed instance from the root type. For example, if Tim is a part-time student, he is also a student and a person, but his most specific type is part-time student.

The function returns the typeids from the hidden type-discriminant column that is associated with every substitutable column. The function returns a null typeid for a final, root type.

The syntax of the function is:

`SYS_TYPEID(object_type_value)`

Function `SYS_TYPEID` may be used only with arguments of an object type. Its primary purpose is to make it possible to build an index on a hidden type-discriminant column.

All types that belong to a type hierarchy are assigned a non-null typeid that is unique within the type hierarchy. Types that do not belong to a type hierarchy have a null typeid.

Every type except a final root type belongs to a type hierarchy. A final root type has no types related to it by inheritance:

- It cannot have subtypes derived from it because it is final.

- It is not itself derived from some other type because it is a root type, so it does not have any supertypes.

For an example of `SYS_TYPEID`, consider the substitutable object table `person_obj_table`, of `person_typ`. `person_typ` is the root type of a hierarchy that has `student_typ` as a subtype and `part_time_student_typ` as a subtype of `student_typ`. See [Example 2-20](inheritance-in-sql-object-types.md).

The following query uses `SYS_TYPEID`. It gets the `name` attribute and `typeid` of the object instances in the `person_obj_table` table. Each of the instances is of a different type:

Example 2-37 Using the SYS_TYPEID Function

    -- Using the SYS_TYPEID Function example, not sample schema

    SELECT name, SYS_TYPEID(VALUE(p)) typeid FROM person_obj_table p;

**See Also:**

- For information about the type-discriminant and other hidden columns, see "[Hidden Columns for Substitutable Columns and Object Tables](storage-of-objects.md)" .

- For more information about the SQL `SYS` `TYPEID` function, see [Oracle Database SQL Language Reference](../sqlrf/REF.md).

### 2.4.7 TABLE()

Table functions are functions that produce a collection of rows, a nested table or a varray, that can be queried like a physical database table or assigned to a PL/SQL collection variable.

You can use a table function like the name of a database table, in the `FROM` clause of a query, or like a column name in the `SELECT` list of a query.

A table function can take a collection of rows as input. An input collection parameter can be either a collection type, such as a `VARRAY` or a PL/SQL table, or a `REF` `CURSOR`.

Use `PIPELINED` to instruct Oracle Database to return the results of a table function iteratively. A table function returns a nested table or varray type. You query table functions by using the `TABLE` keyword before the function name in the `FROM` clause of the query.

**See Also:**

For information on `TABLE()` functions, see

- [Oracle Database Data Cartridge Developer's Guide](../addci/using-pipelined-and-parallel-table-functions.md)

- [Oracle Database PL/SQL Language Reference](../lnpls/plsql-language-elements.md)

### 2.4.8 TREAT

The `TREAT` function does a runtime check to confirm that an expression can be operated on as if it were of a different specified type in the hierarchy, normally a subtype of the declared type of the expression.

In other words, the `TREAT` function attempts to treat a supertype instance as a subtype instance, for example, to treat a person as a student. If the person is a student, then the person is returned as a student, with the additional attributes and methods that a student may have. If the person is not a student, `TREAT` returns `NULL` in SQL.

The two main uses of `TREAT` are:

- In narrowing assignments, to modify the type of an expression so that the expression can be assigned to a variable of a more specialized type in the hierarchy: that is, to set a supertype value into a subtype.

- To access attributes or methods of a subtype of the declared type of a row or column.

  A substitutable object table or column of type `T` has a hidden column for every attribute of every subtype of `T`. These hidden columns contain subtype attribute data, but you cannot list them with a `DESCRIBE` statement. `TREAT` enables you to access these columns.

#### 2.4.8.1 Using TREAT for Narrowing Assignments

The `TREAT` function is used for narrowing assignments, that is, assignments that set a supertype value into a subtype. For a comparison to widening assignments, see "[Assignments Across Types](inheritance-in-sql-object-types.md)".

In Example 2-38, `TREAT` returns all (and only) `student_typ` instances from `person_obj_table` of type `person_typ`, a supertype of `student_typ`. The statement uses `TREAT` to modify the type of `p` from `person_typ` to `student_typ`.

Example 2-38 Using the TREAT Function to Return a Specific Subtype in a Query

    -- Using the TREAT Function to Return a Specific Subtype in a Query example,

    -- not sample schema

    SELECT TREAT(VALUE(p) AS student_typ)
      FROM person_obj_table p;

For each `p`, the `TREAT` modification succeeds only if the most specific or specialized type of the value of `p` is `student_typ` or one of its subtypes. If `p` is a person who is not a student, or if `p` is `NULL`, `TREAT` returns `NULL` in SQL or, in PL/SQL, raises an exception.

You can also use `TREAT` to modify the declared type of a `REF` expression. For example:

    -- Using the TREAT Function to modify declared type of a REF example,

    -- not sample schema

    SELECT TREAT(REF(p) AS REF student_typ)
      FROM person_obj_table p;

The previous example returns `REF`s to all `student_typ` instances. In SQL it returns `NULL` `REF`s for all person instances that are not students, and in PL/SQL it raises an exception.

#### 2.4.8.2 Using the TREAT Function to Access Subtype Attributes or Methods

Perhaps the most important use of `TREAT` is to access attributes or methods of a subtype of a row or column's declared type. The following query retrieves the `major` attribute of all persons, students and part-time students, who have this attribute. `NULL` is returned for persons who are not students:

Example 2-39 Using the TREAT Function to Access Attributes of a Specific Subtype

    SELECT name, TREAT(VALUE(p) AS student_typ).major major
      FROM person_obj_table p;

The following query will not work because `major` is an attribute of `student_typ` but not of `person_typ`, the declared type of table `persons`:

    SELECT name, VALUE(p).major major FROM person_obj_table p -- incorrect;

The following is a PL/SQL example:

    DECLARE
      var person_typ;
    BEGIN
      var := employee_typ(55, 'Jane Smith', '1-650-555-0144', 100, 'Jennifer Nelson');
      DBMS_OUTPUT.PUT_LINE(TREAT(var AS employee_typ).mgr);
    END;
    /

**See Also:**

For more information about the SQL `TREAT` function, see [Oracle Database SQL Language Reference](../sqlrf/TREAT.md).

### 2.4.9 VALUE

In a SQL statement, the `VALUE` function takes as its argument a correlation variable (table alias) for an object table or object view and returns object instances corresponding to rows of the table or view.

The `VALUE` function may return instances of the declared type of the row or any of its subtypes.

Example 2-40 first creates a `part_time_student_typ`, and then shows a `SELECT` query returning all persons, including students and employees, from table `person_obj_table` of `person_typ`.

Example 2-40 Using the VALUE Function

    -- Requires Ex. 2-31 and 2-32
    CREATE TYPE part_time_student_typ UNDER student_typ (
      number_hours NUMBER);
    /
    SELECT VALUE(p) FROM person_obj_table p;

To retrieve only part time students, that is, instances whose most specific type is `part_time_student_typ`, use the `ONLY` keyword to confine the selection:

    SELECT VALUE(p) FROM person_obj_table p
      WHERE VALUE(p) IS OF (ONLY part_time_student_typ);

In the following example, `VALUE` is used to update a object instance in an object table:

    UPDATE person_obj_table p
       SET VALUE(p) = person_typ(12, 'Bob Jones', '1-650-555-0130')
       WHERE p.idno = 12;

**See Also:**

- [Example 5-22](operations-on-collection-data-types.md)

- For more information about the SQL `VALUE` function, see [Oracle Database SQL Language Reference](../sqlrf/VALUE.md).
