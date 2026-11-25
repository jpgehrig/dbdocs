Using object types in a PL/SQL block, subprogram, or package is a two-step process.

1.  You must define object types using the SQL statement `CREATE TYPE`, in SQL\*Plus or other similar programs.

    After an object type is defined and installed in the schema, you can use it in any PL/SQL block, subprogram, or package.

2.  In PL/SQL, you then declare a variable whose data type is the user-defined type or ADT that you just defined.

Objects or ADTs follow the usual scope and instantiation rules.

**See Also:**

"[About Object Types](key-features-object-relational-model.md)"

### 3.1.1 Defining Object Types

You can define object types using `CREATE TYPE`.

Example 3-1 provides two object types, and a table of object types. Subsequent examples show how to declare variables of those object types in PL/SQL and perform other operations with these objects.

Example 3-1 Working With Object Types

    CREATE TYPE address_typ AS OBJECT (
       street          VARCHAR2(30),
       city            VARCHAR2(20),
       state           CHAR(2),
       postal_code     VARCHAR2(6) );
    /
    CREATE TYPE employee_typ AS OBJECT (
      employee_id       NUMBER(6),
      first_name        VARCHAR2(20),
      last_name         VARCHAR2(25),
      email             VARCHAR2(25),
      phone_number      VARCHAR2(20),
      hire_date         DATE,
      job_id            VARCHAR2(10),
      salary            NUMBER(8,2),
      commission_pct    NUMBER(2,2),
      manager_id        NUMBER(6),
      department_id     NUMBER(4),
      address           address_typ,
      MAP MEMBER FUNCTION get_idno RETURN NUMBER,
      MEMBER PROCEDURE display_address ( SELF IN OUT NOCOPY employee_typ ) );
    /
    CREATE TYPE BODY employee_typ AS
      MAP MEMBER FUNCTION get_idno RETURN NUMBER IS
      BEGIN
        RETURN employee_id;
      END;
      MEMBER PROCEDURE display_address ( SELF IN OUT NOCOPY employee_typ ) IS
      BEGIN
        DBMS_OUTPUT.PUT_LINE(first_name || ' '  || last_name);
        DBMS_OUTPUT.PUT_LINE(address.street);
        DBMS_OUTPUT.PUT_LINE(address.city || ', '  || address.state || ' ' ||
                             address.postal_code);
      END;
    END;
    /
    CREATE TABLE employee_tab OF employee_typ;

### 3.1.2 Declaring Objects in a PL/SQL Block

You can use objects or ADTs wherever built-in types such as `CHAR` or `NUMBER` can be used.

- Declare objects in the same way you declare built-in types.

Example 3-2 declares object `emp` of type `employee_typ`. Then, the constructor for object type `employee_typ` initializes the object.

Example 3-2 Declaring Objects in a PL/SQL Block

    -- Requires Ex. 3-1
    DECLARE
      emp employee_typ; -- emp is atomically null
    BEGIN
    -- call the constructor for employee_typ
      emp := employee_typ(315, 'Francis', 'Logan', 'FLOGAN',
            '415.555.0100', '01-MAY-04', 'SA_MAN', 11000, .15, 101, 110,
             address_typ('376 Mission', 'San Francisco', 'CA', '94222'));
      DBMS_OUTPUT.PUT_LINE(emp.first_name || ' ' || emp.last_name); -- display details
      emp.display_address();  -- call object method to display details
    END;
    /

The formal parameter of a PL/SQL subprogram can have data types of user-defined types. Therefore, you can pass objects to stored subprograms and from one subprogram to another.

In the next code line, the object type `employee_typ` specifies the data type of a formal parameter:

`PROCEDURE open_acct (new_acct IN OUT employee_typ) IS ...`

In this code line, object type `employee_typ` specifies the return type of a function:

`FUNCTION get_acct (acct_id IN NUMBER) RETURN employee_typ IS ...`

### 3.1.3 How PL/SQL Treats Uninitialized Objects

User-defined types, just like collections, are atomically null, until you initialize the object by calling the constructor for its object type. That is, the object itself is null, not just its attributes.

Comparing a null object with any other object always yields `NULL`. Also, if you assign an atomically null object to another object, the other object becomes atomically null (and must be reinitialized). Likewise, if you assign the non-value `NULL` to an object, the object becomes atomically null.

In an expression, attributes of an uninitialized object evaluate to `NULL`. When applied to an uninitialized object or its attributes, the `IS` `NULL` comparison operator yields `TRUE`.

See [Example 2-1](Sql-object-types-and-references.md) for an illustration of null objects and objects with null attributes.
