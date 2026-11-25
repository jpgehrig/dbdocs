You can use PL/SQL to implement data cartridge methods. Methods are procedures and functions that define the operations permitted on data defined using the data cartridge.

### 4.1 Methods

A method is procedure or function that is part of the object type definition, and that can operate on the attributes of the type. Such methods are also called member methods, and they take the keyword `MEMBER` when you specify them as a component of the object type.

Consider simple examples for implementing a method, invoking a method, and referencing an attribute in a method.

**See Also:**

- [Oracle Database Concepts](../cncpt/introduction-to-oracle-database.md) for information about method specifications, names, and overloading

- [Oracle Database PL/SQL Language Reference](../lnpls/overview.md) for further explanation and examples

#### 4.1.1 Implementing Methods

To implement a method, create the PL/SQL code and specify it within a `CREATE` `TYPE` `BODY` statement. If an object type has no methods, no `CREATE` `TYPE` `BODY` statement for that object type is required.

Example 4-1demonstrates the definition of an object type `rational_type`.

The definition in Example 4-2 defines the function `gcd`, which is used in the definition of the `normalize` method in the `CREATE` `TYPE` `BODY` statement.

The statements in Example 4-3 implement the methods `rat_to_real`, `normalize`, and `plus` for the object type `rational_type`.

##### 4.1.1.1 Defining an Object Type

Example 4-1 Defining an Object Type

    CREATE TYPE rational_type AS OBJECT
    ( numerator INTEGER,
      denominator INTEGER,
      MAP MEMBER FUNCTION rat_to_real RETURN REAL,
      MEMBER PROCEDURE normalize,
      MEMBER FUNCTION plus (x rational_type)
           RETURN rational_type);

##### 4.1.1.2 Defining a “Greatest Common Divisor” Function

Example 4-2 Defining a "Greatest Common Divisor" Function

    CREATE FUNCTION gcd (x INTEGER, y INTEGER) RETURN INTEGER AS
    -- Find greatest common divisor of x and y. For example, if
    -- (8,12) is input, the greatest common divisor is 4.
    -- This normalizes (simplifies) fractions.
    -- (You need not try to understand how this code works, unless
    --  you are a math wizard. It does.)
    --
       ans INTEGER;
    BEGIN
       IF (y <= x) AND (x MOD y = 0) THEN
          ans := y;
       ELSIF x < y THEN
          ans := gcd(y, x);  -- Recursive call
       ELSE
          ans := gcd(y, x MOD y);  -- Recursive call
       END IF;
       RETURN ans;
    END;

##### 4.1.1.3 Implementing Methods for an Object Type

Example 4-3 Implementing Methods for an Object Type

    CREATE TYPE BODY rational_type
    ( MAP MEMBER FUNCTION rat_to_real RETURN REAL IS
       -- The rat-to-real function converts a rational number to
       -- a real number. For example, 6/8 = 0.75
       BEGIN
          RETURN numerator/denominator;
       END;

       -- The normalize procedure simplifies a fraction.
       -- For example, 6/8 = 3/4
       MEMBER PROCEDURE normalize IS
          divisor INTEGER := gcd(numerator, denominator);
       BEGIN
          numerator := numerator/divisor;
          denominator := denominator/divisor;
       END;

       -- The plus function adds a specified value to the
       -- current value and returns a normalized result.
       -- For example, 1/2 + 3/4 = 5/4
       --
       MEMBER FUNCTION plus(x rational_type)
                RETURN rational_type IS
                -- Return sum of SELF + x
       BEGIN
          r = rational_type(numerator*x.demonimator +
                 x.numerator*denominator,
                 denominator*x.denominator);
                     -- Example adding 1/2 to 3/4:
                     -- (3*2 + 1*4) / (4*2)
          -- Now normalize (simplify). Here, 10/8 = 5/4
          r.normalize;
          RETURN r;
       END;
    END;

#### 4.1.2 Invoking Methods

To invoke a method, use the syntax in Example 4-4.

In SQL statements only, you can use the syntax in Example 4-5.

Example 4-6 shows how to invoke a method named `get_emp_sal` in PL/SQL.

An alternative way to invoke a method is by using the `SELF` built-in parameter. Because the implicit first parameter of each method is the name of the object on whose behalf the method is invoked, Example 4-7 performs the same action as the `salary := employee.get_emp_sal();` line in Example 4-6.

In Example 4-7, `employee` is the name of the object on whose behalf the `get_emp_sal()` method is invoked.

##### 4.1.2.1 General Syntax for Invoking Methods

Example 4-4 Invoking Methods; General Syntax

    object_name.method_name([parameter_list])

##### 4.1.2.2 SQL Syntax for Invoking Methods

Example 4-5 Invoking Methods; SQL Syntax

    correlation_variable.method_name([parameter_list])

##### 4.1.2.3 PL/SQL Syntax for Invoking Methods

Example 4-6 Invoking Methods; PL/SQL Syntax

    DECLARE
       employee employee_type;
       salary number;
       ...
    BEGIN
       salary := employee.get_emp_sal();
       ...
    END;

##### 4.1.2.4 Using the SELF Build-In Parameter

Example 4-7 Using the SELF Build-In Parameter

    salary := get_emp_sal(SELF => employee);

#### 4.1.3 Referencing Attributes in a Method

Because member methods can reference the attributes and member methods of the same object type without using a qualifier, a built-in reference, `SELF`, always identifies the object on whose behalf the method is invoked.

Consider Example 4-8, where two statements set the value of variable `var1` to `42`.

The statements `var1 := 42` and `SELF.var1 := 42` have the same effect. Because `var1` is the name of an attribute of the object type `a_type` and because `set_var1` is a member method of this object type, no qualification is required to access `var1` in the method code. However, for code readability and maintainability, you can use the keyword `SELF` in this context to make the reference to `var1` more clear.

##### 4.1.3.1 Setting Variable Values

Example 4-8 Setting Variable Values

    CREATE TYPE a_type AS OBJECT (
       var1 INTEGER,
       MEMBER PROCEDURE set_var1);
    CREATE TYPE BODY a_type (
       MEMBER PROCEDURE set_var1 IS
       BEGIN
          var1 := 42;
          SELF.var1 := 42;
       END set_var1;
    );

### 4.2 Debugging PL/SQL Code

One of the simplest ways to debug PL/SQL code is to try each method, block, or statement interactively using SQL\*Plus, and fix any problems before proceeding to the next statement. If you need more information on an error message, enter the statement `SHOW` `ERRORS`. Also. consider displaying statements for run-time debugging. You can debug stored procedures and packages using the `DBMS_OUTPUT` package, by inserting `PUT` and `PUTLINE` statements into the code to output the values of variables and expressions to your terminal, as demonstrated in Example 4-9.

A PL/SQL tracing tool provides more information about exception conditions in application code. You can use this tool to trace the execution of server-side PL/SQL statements. Object type methods cannot be traced directly, but you can trace any PL/SQL functions or procedures that a method calls. The tracing tool also provides information about exception conditions in the application code. The trace output is written to the Oracle server trace file. Note that only the database administrator has access to the file.

**See Also:**

- The [Oracle Database SQL Tuning Guide](../tgsql/performing-application-tracing.md) describes the tracing tool

- The [Oracle Database PL/SQL Packages and Types Reference](../arpls/DBMS_OUTPUT.md) and the [Oracle Database PL/SQL Language Reference](../lnpls/overview.md) describe the `DBMS_OUTPUT` package

Example 4-9 Outputing Variable Values to the Terminal, for Debugging

    Location in module: location
    Parameter name: name
    Parameter value: value

#### 4.2.1 Notes for C and C++ Developers of Data Cartridges

If you are a C or C++ programmer, several PL/SQL conventions and requirements may differ from your expectations.

- = means equal (not assign).

- := means assign (as in Algol).

- `VARRAYs` begin at index `1` (not `0`).

- Comments begin with two hyphens (--), not with `//` or `/*`.

- The `IF` statement requires the `THEN` keyword.

- The `IF` statement must be concluded with the `END` `IF` keyword (which comes after the `ELSE` clause, if there is one).

- There is no `PRINTF` statement. The comparable feature is the `DBMS_OUTPUT`.`PUT_LINE` statement. In this statement, literal and variable text is separated using the double vertical bar, `||`.

- A function must have a return value, and a procedure cannot have a return value.

- If you call a function, it must be on the right side of an assignment operator.

- Many PL/SQL keywords cannot be used as variable names.

#### 4.2.2 Common Potential Errors

Several kinds of errors that may occur while creating a data cartridge.

##### 4.2.2.1 Signature Mismatches

    13/19    PLS-00538: subprogram or cursor '<name>' is declared in an object
             type specification and must be defined in the object type body
    15/19    PLS-00539: subprogram '<name>' is declared in an object type body
             and must be defined in the object type specification

If you see either or both of these messages, you have made an error with the signature for a procedure or function. In other words, you have a mismatch between the function or procedure prototype that you entered in the object specification, and the definition in the object body.

Ensure that parameter orders, parameter spelling (including case), and function returns are identical. Use copy-and-paste to avoid errors in typing.

##### 4.2.2.2 RPC Time Out

    ORA-28576: lost RPC connection to external procedure agent
    ORA-06512: at "<name>", line <number>
    ORA-06512: at "<name>", line <number>
    ORA-06512: at line 34

This error might occur after you exit the debugger for the DLL. Restart the program outside the debugger.

##### 4.2.2.3 Package Corruption

    ERROR at line 1:
    ORA-04068: existing state of packages has been discarded
    ORA-04063: package body "<name>" has errors
    ORA-06508: PL/SQL: could not find program unit being called
    ORA-06512: at "<name>", line <number>
    ORA-06512: at line <number>

This error might occur if you are extending an existing data cartridge; it indicates that the package has been corrupted and must be recompiled.

Before you can perform the recompilation, you must delete all tables and object types that depend upon the package that you are recompiling. To find the dependents on a Windows NT system, use the Oracle Administrator toolbar. Click the Schema button, log in as `sys\<password>`, and find packages and tables that you created. Drop these packages and tables by entering SQL statements in the SQL\*Plus interface, as shown in Example 4-10:

Example 4-10 Dropping Packages and Tables

    Drop type type_name;
    Drop table table_name cascade constraints;

The recompilation can then be done using the SQL statements in Example 4-11:

Example 4-11 Recompiling Packages

    Alter type type_name compile body;
    Alter type type_name compile specification;
