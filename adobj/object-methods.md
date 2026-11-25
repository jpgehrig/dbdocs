Object methods implement behavior that objects of that type perform.

Topics:

- About Object Methods

- Member Methods

- Declaring and Invoking Static Methods

- Constructor Methods

- External Implemented Methods

### 2.2.1 About Object Methods

Object methods, also known as subprograms, are functions or procedures that you can declare in an object type definition to implement behavior that you want objects of that type to perform. An application calls the subprograms to invoke the behavior.

Subprograms can be written in PL/SQL or virtually any other programming language. Methods written in PL/SQL or Java are stored in the database. Methods written in other languages, such as C, are stored externally.

**Note:**

SQL requires parentheses for all subprogram calls, even those that do not have arguments. This is not true for PL/SQL.

**See Also:**

See "[Calling Object Constructors and Methods](object-manipulation-in-plsql.md)" for more information on invoking methods in PL/SQL.

### 2.2.2 Member Methods

Member methods provide an application with access to the data of an object instance.

You define a member method in the object type for each operation that you want an object of that type to be able to perform. Non-comparison member methods are declared as either `MEMBER` `FUNCTION` or `MEMBER` `PROCEDURE`. Comparison methods use `MAP` `MEMBER` `FUNCTION` or `ORDER` `MEMBER` `FUNCTION` as described in "Member Methods for Comparing Objects".

As an example of a member method, you might declare a function `get_sum()` that sums the total cost of a purchase order's line items. The following line of code calls this function for purchase order `po` and returns the amount into `sum_line_items`.

`sum_line_items:= po.get_sum();abo`

Dot notation specifies the current object and the method it calls. Parentheses are required even if there are no parameters.

Topics:

- Declaring SELF Parameters in Member Methods

- Member Methods for Comparing Objects

#### 2.2.2.1 Declaring SELF Parameters in Member Methods

Member methods have a built-in parameter named `SELF` that denotes the object instance currently invoking the method.

`SELF` can be explicitly declared, but that is not necessary. It is simpler to write member methods that reference the attributes and methods of `SELF` implicitly without the `SELF` qualifier. In Example 2-8, the code and comments demonstrate method invocations that use an implicit `SELF` parameter rather than qualify the attributes `hgt`, `len`, and `wth`.

Example 2-8 Creating a Member Method

    -- Ex. 2-8 Creating a Member Method
    CREATE OR REPLACE TYPE solid_typ AS OBJECT (
      len    INTEGER,
      wth    INTEGER,
      hgt    INTEGER,
      MEMBER FUNCTION surface RETURN INTEGER,
      MEMBER FUNCTION volume RETURN INTEGER,
      MEMBER PROCEDURE display (SELF IN OUT NOCOPY solid_typ) );
    /

    CREATE OR REPLACE TYPE BODY solid_typ AS
      MEMBER FUNCTION volume RETURN INTEGER IS
      BEGIN
        RETURN len * wth * hgt;
     -- RETURN SELF.len * SELF.wth * SELF.hgt; -- equivalent to previous line
      END;
      MEMBER FUNCTION surface RETURN INTEGER IS
      BEGIN -- not necessary to include SELF in following line
        RETURN 2 * (len * wth + len * hgt + wth * hgt);
      END;
      MEMBER PROCEDURE display (SELF IN OUT NOCOPY solid_typ) IS
      BEGIN
        DBMS_OUTPUT.PUT_LINE('Length: ' || len || ' - '  || 'Width: ' || wth
                              || ' - '  || 'Height: ' || hgt);
        DBMS_OUTPUT.PUT_LINE('Volume: ' || volume || ' - ' || 'Surface area: '
                              || surface);
      END;
    END;
    /

    CREATE TABLE solids of solid_typ;
    INSERT INTO solids VALUES(10, 10, 10);
    INSERT INTO solids VALUES(3, 4, 5);
    SELECT * FROM solids;
    SELECT s.volume(), s.surface() FROM solids s WHERE s.len = 10;
    DECLARE
      solid solid_typ;
    BEGIN -- PL/SQL block for selecting a solid and displaying details
      SELECT VALUE(s) INTO solid FROM solids s WHERE s.len = 10;
      solid.display();
    END;
    /

`SELF` is always the first parameter passed to the method.

- In member functions, if `SELF` is not declared, its parameter mode defaults to `IN`.

- In member procedures, if `SELF` is not declared, its parameter mode defaults to `IN` `OUT`. The default behavior does not include the `NOCOPY` compiler hint.

**See Also:**

"[About Using SELF IN OUT NOCOPY with Member Procedures](design-considerations-for-methods.md)".

#### 2.2.2.2 Member Methods for Comparing Objects

To compare and order variables of an object type, you must specify a basis for comparing them.

The values of a scalar data type such as `CHAR` or `REAL` have a predefined order, which allows them to be compared. But an object type, such as a `person_typ`, which can have multiple attributes of various data types, has no predefined axis of comparison. You have the option to define a map method or an order method for comparing objects, but not both.

A map method maps object return values to scalar values and can order multiple values by their position on the scalar axis. An order method directly compares values for two particular objects.

##### 2.2.2.2.1 About Map Methods

Map methods return values that can be used for comparing and sorting.

Return values can be any Oracle built-in data types (except LOBs and `BFILE`s) and ANSI SQL types such as `CHARACTER` or `REAL`. See the specific sections in [Oracle Database SQL Language Quick Reference](../sqlrf/Data-Types.md).

Generally, map methods perform calculations on the attributes of the object to produce the return value.

Map methods are called automatically to evaluate such comparisons as `obj_1` \> `obj_2` and comparisons implied by the `DISTINCT`, `GROUP` `BY`, `UNION`, and `ORDER` `BY` clauses which require sorting by rows.

Where `obj_1` and `obj_2` are two object variables that can be compared using a map method `map()`, the comparison:

`obj_1 > obj_2`

is equivalent to:

`obj_1.map() > obj_2.map()`

Comparisons are similar for other relational operators.

Creating a Map Method defines a map method `area()` that provides a basis for comparing rectangle objects by their area:

##### 2.2.2.2.2 Creating a Map Method

You create maps using the `CREATE TYPE` statement.

Example 2-9 Creating a Map Method

    CREATE OR REPLACE TYPE rectangle_typ AS OBJECT (
      len NUMBER,
      wid NUMBER,
      MAP MEMBER FUNCTION area RETURN NUMBER);
    /

    CREATE OR REPLACE TYPE BODY rectangle_typ AS
      MAP MEMBER FUNCTION area RETURN NUMBER IS
      BEGIN
         RETURN len * wid;
      END area;
    END;
    /

##### 2.2.2.2.3 Invoking a Map Method

Map methods are invoked in the same manner as other member methods.

Example 2-10 Invoking a Map Method

    DECLARE
      po rectangle_typ;

    BEGIN
      po :=NEW rectangle_typ(10,5);

    DBMS_OUTPUT.PUT_LINE('AREA:' || po.area()); -- prints AREA:50
      END;
    /

A subtype can declare a map method only if its root supertype declares one.

See "[Comparing Equal and Not Equal Conditions](operations-on-collection-data-types.md) " for the use of map methods when comparing collections that contain object types.

##### 2.2.2.2.4 Order Methods

Order methods make direct one-to-one object comparisons.

Unlike map methods, order methods cannot determine the order of a number of objects. They simply tell you that the current object is less than, equal to, or greater than the object that it is being compared to, based on the criterion used.

An order method is a function for an object (`SELF`), with one declared parameter that is an object of the same type. The method must return either a negative number, zero, or a positive number. This value signifies that the object (the implicit undeclared `SELF` parameter) is less than, equal to, or greater than the declared parameter object.

As with map methods, an order method, if one is defined, is called automatically whenever two objects of that type need to be compared.

Order methods are useful where comparison semantics may be too complex to use a map method.

Example 2-11 shows an order method that compares locations by building number:

Example 2-11 Creating and Invoking an Order Method

    DROP TYPE location_typ FORCE;
    -- above necessary if you have previously created object
    CREATE OR REPLACE TYPE location_typ AS OBJECT (
      building_no  NUMBER,
      city         VARCHAR2(40),
      ORDER MEMBER FUNCTION match (l location_typ) RETURN INTEGER );/
    CREATE OR REPLACE TYPE BODY location_typ AS
      ORDER MEMBER FUNCTION match (l location_typ) RETURN INTEGER IS
      BEGIN
        IF building_no < l.building_no THEN
          RETURN -1;               -- any negative number will do
        ELSIF building_no > l.building_no THEN
          RETURN 1;                -- any positive number will do
        ELSE
          RETURN 0;
        END IF;
      END;
    END;/

    -- invoking match method
    DECLARE
    loc location_typ;
    secloc location_typ;
    a number;

    BEGIN
     loc :=NEW location_typ(300, 'San Francisco');
     secloc :=NEW location_typ(200, 'Redwood Shores');
     a := loc.match(secloc);

    DBMS_OUTPUT.PUT_LINE('order (1 is greater, -1 is lesser):' ||a); -- prints order:1
     END;
    /

Only a type that is not derived from another type can declare an order method; a subtype cannot define one.

##### 2.2.2.2.5 Guidelines for Comparison Methods

You can declare a map method or an order method but not both.

For map and order type methods, you can compare objects using SQL statements and PL/SQL procedural statements. However, if you do not declare one of these methods, you can only compare objects in SQL statements, and only for equality or inequality. Two objects of the same type are considered equal only if the values of their corresponding attributes are equal.

When sorting or merging a large number of objects, use a map method, which maps all the objects into scalars, then sorts the scalars. An order method is less efficient because it must be called repeatedly (it can compare only two objects at a time).

**See Also:**

"[Performance of Object Comparisons](performance-of-object-comparisons.md)"

##### 2.2.2.2.6 Comparison Methods in Type Hierarchies

In a type hierarchy, if the root type (supertype) does not specify a map or an order method, neither can the subtypes.

- Map Method in a Type Hierarchy

  If the root type specifies a map method, any of its subtypes can override it. If the root type does not specify a map method, no subtype can specify one either.

- Order Method in a Type Hierarchy

  Only the root type can define an order method. If the root type does not define one, its subtypes cannot add one.

### 2.2.3 Declaring and Invoking Static Methods

Static methods are invoked on the object type, not its instances. You use a static method for operations that are global to the type and do not need to reference the data of a particular object instance. A static method has no `SELF` parameter.

Static methods are declared using `STATIC` `FUNCTION` or `STATIC` `PROCEDURE`.

You invoke a static method by using dot notation to qualify the method call with the name of the object type, for example:

`type_name.method()`

**See Also:**

For information on design considerations, see "[Static Methods](design-considerations-for-methods.md)".

### 2.2.4 Constructor Methods

A constructor method is a function that returns a new instance of the user-defined type and sets up the values of its attributes.

Constructor methods are either system-defined or user-defined.

To invoke a constructor, the keyword `NEW` can be used, but is not required.

**See Also:**

See Example 2-10 and "[Calling Object Constructors and Methods](object-manipulation-in-plsql.md)"

#### 2.2.4.1 System-Defined Constructors

By default, the system implicitly defines a constructor function for all object types that have attributes.

A system-defined constructor is sometimes known as the attribute value constructor. For the `person_typ` object type defined in [Example 2-1](Sql-object-types-and-references.md) the name of the constructor method is the name of the object type, as shown in the following invocation:

`person_typ (1, 'John Smith', '1-650-555-0135'),`

#### 2.2.4.2 Defining User-Defined Constructors

You can define constructor functions of your own to create and initialize user-defined types.

Default system-defined constructors (or attribute value constructors) are convenient to use because they already exist, but user-defined constructors have some important advantages with respect to type evolution.

**See Also:**

- "[Advantages of User-Defined Constructors](system-defined-and-user-defined-constructors.md)"

- For information on user-defined constructors for collections, see "[Using the Constructor Method to Insert Values into a Nested Table](collection-data-types.md)".

#### 2.2.4.3 Literal Invocation of a Constructor Method

A [literal invocation](glossary.md) of a constructor method is a call to the constructor method in which arguments are either literals (as opposed to bind variables), or further literal invocations of constructor methods. For example:

    CREATE TABLE people_tab OF person_typ;

    INSERT INTO people_tab VALUES (
           person_typ(101, 'John Smith', '1-650-555-0135') );

### 2.2.5 External Implemented Methods

You can use PL/SQL to invoke external subprograms that have been written in other languages.

Using external methods provides access to the strengths and capabilities of those languages.

**See Also:**

[Object Support in Oracle Programming Environments](object-support-in-oracle-programming-environments.md)
