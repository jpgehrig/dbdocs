The SQL `CALL` statement lets you call Java methods, which are published at the top level, in PL/SQL packages, or in SQL object types. In SQL\*Plus, you can run the `CALL` statement interactively using the following syntax:

    CALL [schema_name.][{package_name | object_type_name}][@dblink_name]
      { procedure_name ([param[, param]...])
       | function_name ([param[, param]...]) INTO :host_variable};

where `param` is represented by the following syntax:

    {literal | :host_variable}

Host variables are variables that are declared in a host environment. They must be prefixed with a colon. The following examples show that a host variable cannot appear twice in the same `CALL` statement and that a subprogram without parameters must be called with an empty parameter list:

    CALL swap(:x, :x); -- illegal, duplicate host variables
    CALL balance() INTO :current_balance; -- () required

This section covers the following topics:

- Redirecting the Output

- Examples of Calling Java Stored Procedures From the Top Level

### 7.1.1 Redirecting the Output

On the server, the default output device is a trace file and not the user screen. As a result, `System.out` and `System.err` print output to the current trace files. To redirect output to the SQL\*Plus text buffer, you must call the `set_output()` procedure in the `DBMS_JAVA` package, as follows:

    SQL> SET SERVEROUTPUT ON
    SQL> CALL dbms_java.set_output(2000);

The minimum buffer size is 2,000 bytes, which is also the default size, and the maximum buffer size is 1,000,000 bytes. In the following example, the buffer size is increased to 5,000 bytes:

    SQL> SET SERVEROUTPUT ON SIZE 5000
    SQL> CALL dbms_java.set_output(5000);

The output is displayed when the stored procedure exits.

### 7.1.2 Examples of Calling Java Stored Procedures From the Top Level

This section provides the following examples

- Example 7-1

- Example 7-2

Example 7-1 A Simple JDBC Stored Procedure

In the following example, the `main()` method accepts the name of a database table, such as `employees`, and an optional `WHERE` clause specifying a condition, such as `salary > 1500`. If you omit the condition, then the method deletes all rows from the table, else it deletes only those rows that meet the condition.

    import java.sql.*;
    import oracle.jdbc.*;

    public class Deleter
    {
      public static void main (String[] args) throws SQLException
      {
        Connection conn = DriverManager.getConnection("jdbc:default:connection:");
        String sql = "DELETE FROM " + args[0];
        if (args.length > 1)
          sql += " WHERE " + args[1];
        try
        {
          Statement stmt = conn.createStatement();
          stmt.executeUpdate(sql);
          stmt.close();
        }
        catch (SQLException e)
        {
          System.err.println(e.getMessage());
        }
      }
    }

The `main()` method can take either one or two arguments. Usually, the `DEFAULT` clause is used to vary the number of arguments passed to a PL/SQL subprogram. However, this clause is not allowed in a call specification. As a result, you must overload two packaged procedures, as follows:

    CREATE OR REPLACE PACKAGE pkg AS
    PROCEDURE delete_rows (table_name VARCHAR2);
    PROCEDURE delete_rows (table_name VARCHAR2, condition VARCHAR2);
    END;

    CREATE OR REPLACE PACKAGE BODY pkg AS
    PROCEDURE delete_rows (table_name VARCHAR2)
    AS LANGUAGE JAVA
    NAME 'Deleter.main(java.lang.String[])';

    PROCEDURE delete_rows (table_name VARCHAR2, condition VARCHAR2)
    AS LANGUAGE JAVA
    NAME 'Deleter.main(java.lang.String[])';
    END;

Now, you can call the `delete_rows` procedure, as follows:

    SQL> CALL pkg.delete_rows('employees', 'salary > 1500');

    Call completed.

    SQL> SELECT first_name, salary FROM employees;

    FIRST_NAME  SALARY
    --------- --------
    SMITH          800
    WARD          1250
    MARTIN        1250
    TURNER        1500
    ADAMS         1100
    JAMES          950
    MILLER        1300

    7 rows selected.

**Note:**

You cannot overload top-level procedures.

Example 7-2 Fibonacci Sequence

Assume that the executable for the following Java class is stored in Oracle Database:

    public class Fibonacci
    {
      public static int fib (int n)
      {
        if (n == 1 || n == 2)
          return 1;
        else
          return fib(n - 1) + fib(n - 2);
      }
    }

The `Fibonacci` class has a method, `fib()`, which returns the nth Fibonacci number. The Fibonacci sequence, 1, 1, 2, 3, 5, 8, 13, 21, . . ., is recursive. Each term in the sequence, after the second term, is the sum of the two terms that immediately precede it. Because `fib()` returns a value, you must publish it as a function, as follows:

    CREATE OR REPLACE FUNCTION fib (n NUMBER) RETURN NUMBER
    AS LANGUAGE JAVA
    NAME 'Fibonacci.fib(int) return int';

Next, you declare two SQL\*Plus host variables and initialize the first one:

    SQL> VARIABLE n NUMBER
    SQL> VARIABLE f NUMBER
    SQL> EXECUTE :n := 7;

    PL/SQL procedure successfully completed.

Now, you can call the `fib()` function. In a `CALL` statement, host variables must be prefixed with a colon. The function can be called, as follows:

    SQL> CALL fib(:n) INTO :f;

    Call completed.

    SQL> PRINT f

    F
    ----------
    13
