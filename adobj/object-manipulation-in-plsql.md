This section describes how to manipulate object attributes and methods in PL/SQL.

This section includes the following topics:

- Accessing Object Attributes With Dot Notation

- Calling Object Constructors and Methods

- Updating and Deleting Objects

- Manipulating Object Manipulation with Ref Modifiers

### 3.2.1 Accessing Object Attributes With Dot Notation

You refer to an attribute by name. To access or change the value of an attribute, you use dot notation.

Attribute names can be chained, which lets you access the attributes of a nested object type. Example 3-3 uses dot notation and generates the same output as [Example 3-2](declaring-initializing-objects-in-plsql.md).

Example 3-3 Accessing Object Attributes

    -- Requires Ex. 3-1
    DECLARE
      emp employee_typ;
    BEGIN
      emp := employee_typ(315, 'Francis', 'Logan', 'FLOGAN',
            '415.555.0100', '01-MAY-04', 'SA_MAN', 11000, .15, 101, 110,
             address_typ('376 Mission', 'San Francisco', 'CA', '94222'));
      DBMS_OUTPUT.PUT_LINE(emp.first_name || ' '  || emp.last_name);
      DBMS_OUTPUT.PUT_LINE(emp.address.street);
      DBMS_OUTPUT.PUT_LINE(emp.address.city || ', '  ||emp. address.state || ' ' ||
                           emp.address.postal_code);
    END;
    /

### 3.2.2 Calling Object Constructors and Methods

Calls to a constructor are allowed wherever function calls are allowed.

A constructor, like all functions, is called as part of an expression, as shown in Example 3-3 and Example 3-4.

When you pass parameters to a constructor, the call assigns initial values to the attributes of the object being instantiated. When you call the default constructor to fill in all attribute values, you must supply a parameter for every attribute; unlike constants and variables, attributes cannot have default values. You can call a constructor using named notation instead of positional notation.

Example 3-4 Inserting Rows in an Object Table

    -- Requires Ex. 3-1
    DECLARE
      emp employee_typ;
    BEGIN
      INSERT INTO employee_tab VALUES (employee_typ(310, 'Evers', 'Boston', 'EBOSTON',
       '617.555.0100', '01-AUG-04', 'SA_REP', 9000, .15, 101, 110,
        address_typ('123 Main', 'San Francisco', 'CA', '94111')) );
      INSERT INTO employee_tab VALUES (employee_typ(320, 'Martha', 'Dunn', 'MDUNN',
        '650.555.0150', '30-SEP-04', 'AC_MGR', 12500, 0, 101, 110,
        address_typ('123 Broadway', 'Redwood City', 'CA', '94065')) );
    END;
    /
    SELECT VALUE(e) from employee_tab e;

### 3.2.3 Accessing Object Methods

Like packaged subprograms, methods are called using dot notation.

In Example 3-5, the `display_address` method is called to display attributes of an object. Note the use of the `VALUE` function which returns the value of an object. `VALUE` takes as its argument a correlation variable. In this context, a correlation variable is a row variable or table alias associated with a row in an object table.

Example 3-5 Accessing Object Methods

    -- Requires Ex. 3-1 and Ex. 3-4
    DECLARE
      emp employee_typ;
    BEGIN
      SELECT VALUE(e) INTO emp FROM employee_tab e WHERE e.employee_id = 310;
      emp.display_address();
    END;
    /

In SQL statements, calls to a parameterless method require an empty parameter list. In procedural statements, an empty parameter list is optional unless you chain calls, in which case it is required for all but the last call. Also, if you chain two function calls, the first function must return an object that can be passed to the second function.

If a PL/SQL function is used in place of an ADT constructor during a DML operation, the function may execute multiple times as part of the DML execution. For the function to execute only once per occurrence, it must be a deterministic function.

For static methods, calls use the notation `type_name``.``method_name` rather than specifying an instance of the type.

When you call a method using an instance of a subtype, the actual method that is executed depends on declarations in the type hierarchy. If the subtype overrides the method that it inherits from its supertype, the call uses the subtype implementation. Otherwise, the call uses the supertype implementation. This capability is known as dynamic method dispatch.

**See Also:**

"[Dynamic Method Dispatch](inheritance-in-sql-object-types.md)"

### 3.2.4 Updating and Deleting Objects

From inside a PL/SQL block you can modify and delete rows in an object table.

Example 3-6 Updating and Deleting Rows in an Object Table

    -- Requires Ex. 3-1 and 3-4
    DECLARE
      emp employee_typ;
    BEGIN
      INSERT INTO employee_tab VALUES (employee_typ(370, 'Robert', 'Myers', 'RMYERS',
       '415.555.0150', '07-NOV-04', 'SA_REP', 8800, .12, 101, 110,
        address_typ('540 Fillmore', 'San Francisco', 'CA', '94011')) );
      UPDATE employee_tab e SET e.address.street = '1040 California'
         WHERE e.employee_id = 370;
      DELETE FROM employee_tab e WHERE e.employee_id = 310;
    END;
    /
    SELECT VALUE(e) from employee_tab e;

### 3.2.5 Manipulating Object Manipulation with Ref Modifiers

You can retrieve `REF`s using the function `REF`, which takes as its argument a correlation variable or alias.

You can declare `REF`s as variables, parameters, fields, or attributes. You can use `REF`s as input or output variables in SQL data manipulation statements.

Example 3-7 Updating Rows in an Object Table With a REF Modifier

    -- Requires Ex. 3-1, 3-4, and 3-6
    DECLARE
      emp         employee_typ;
      emp_ref REF employee_typ;
    BEGIN
      SELECT REF(e) INTO emp_ref FROM employee_tab e WHERE e.employee_id = 370;
      UPDATE employee_tab e
        SET e.address = address_typ('8701 College', 'Oakland', 'CA', '94321')
        WHERE REF(e) = emp_ref;
    END;
    /

You cannot navigate through `REF`s in PL/SQL. For example, the assignment in Example 3-8 using a `REF` is not allowed. Instead, use the function `DEREF` or make calls to the package `UTL_REF` to access the object.

Example 3-8 Trying to Use DEREF in a SELECT INTO Statement, Incorrect

    -- Requires Ex. 3-1, 3-4, and 3-6
    DECLARE
      emp           employee_typ;
      emp_ref   REF employee_typ;
      emp_name      VARCHAR2(50);
    BEGIN
      SELECT REF(e) INTO emp_ref FROM employee_tab e WHERE e.employee_id = 370;
      -- the following assignment raises an error, not allowed in PL/SQL  emp := DEREF(emp_ref);  --  cannot use DEREF in procedural statements
      emp_name := emp.first_name || ' ' || emp.last_name;
      DBMS_OUTPUT.PUT_LINE(emp_name);
    END;
    /

This assignment raises an error as described below:

    not allowed in PL/SQL
    -- emp_name := emp_ref.first_name || ' ' || emp_ref.last_name;
    -- emp := DEREF(emp_ref); not allowed, cannot use DEREF in procedural statements

**See Also:**

- For information on the `REF` function, see [Oracle Database SQL Language Reference](../sqlrf/REF.md).

- For detailed information on the `DEREF` function, see [Oracle Database SQL Language Reference](../sqlrf/DEREF.md).
