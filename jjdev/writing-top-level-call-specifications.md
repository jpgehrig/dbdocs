This section describes how to define top-level call specifications in SQL\*Plus.

In SQL\*Plus, you can define top-level call specifications interactively, using the following syntax:

    CREATE [OR REPLACE]
    { PROCEDURE procedure_name [(param[, param]...)]
    | FUNCTION function_name [(param[, param]...)] RETURN sql_type}
    [AUTHID {DEFINER | CURRENT_USER}]
    [PARALLEL_ENABLE]
    [DETERMINISTIC]
    {IS | AS} LANGUAGE JAVA
    NAME 'method_fullname (java_type_fullname[, java_type_fullname]...)
    [return java_type_fullname]';

where `param` is represented by the following syntax:

    parameter_name [IN | OUT | IN OUT] sql_type

The `AUTHID` clause determines the following:

- Whether a stored procedure runs with the privileges of its definer (`AUTHID DEFINER`) or invoker (`AUTHID CURRENT_USER`)

- Whether its unqualified references to schema objects are resolved in the schema of the definer or invoker

If you do not specify the `AUTHID`, then the default behavior is `DEFINER`, that is, the stored procedure runs with the privileges of its definer. You can override the default behavior by specifying the `AUTHID` as `CURRENT_USER`. However, you cannot override the `loadjava` option `-definer` by specifying `CURRENT_USER`.

The `PARALLEL_ENABLE` option declares that a stored function can be used safely in the worker sessions of parallel DML evaluations. The state of a main session is never shared with worker sessions. Each worker session has its own state, which is initialized when the session begins. The function result should not depend on the state of session variables. Otherwise, results might vary across sessions.

The `DETERMINISTIC` option helps the optimizer avoid redundant function calls. If a stored function was called previously with the same arguments, then the optimizer can decide to use the previous result. The function result should not depend on the state of session variables or schema objects. Otherwise, results can vary across calls. Only `DETERMINISTIC` functions can be called from a function-based index or a materialized view that has query-rewrite enabled.

The string in the `NAME` clause uniquely identifies the Java method. The fully-qualified Java names and the call specification parameters, which are mapped by position, must correspond. However, this rule does not apply to the `main()` method. If the Java method does not take any arguments, then write an empty parameter list for it, but not for the function or procedure.

Write fully-qualified Java names using the dot notation. The following example shows that the fully-qualified names can be broken across lines at dot boundaries:

    artificialIntelligence.neuralNetworks.patternClassification.
    RadarSignatureClassifier.computeRange()

### 6.3.1 Examples

This section provides the following examples:

- Example 6-1

- Example 6-2

- Example 6-3

- Example 6-4

Example 6-1 Publishing a Simple JDBC Stored Procedure

Assume that the executable for the following Java class has been loaded into the database:

    import java.sql.*;
    import java.io.*;
    import oracle.jdbc.*;

    public class GenericDrop
    {
      public static void dropIt(String object_type, String object_name)
                                                             throws SQLException
      {
        // Connect to Oracle using JDBC driver
        Connection conn = DriverManager.getConnection("jdbc:default:connection:");
        // Build SQL statement
        String sql = "DROP " + object_type + " " + object_name;
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

The `GenericDrop` class has one method, `dropIt()`, which drops any kind of schema object. For example, if you pass the `table` and `employees` arguments to `dropIt()`, then the method drops the database table `employees` from your schema.

The call specification for the `dropIt()` method is as follows:

    CREATE OR REPLACE PROCEDURE drop_it (obj_type VARCHAR2, obj_name VARCHAR2)
    AS LANGUAGE JAVA
    NAME 'GenericDrop.dropIt(java.lang.String, java.lang.String)';

Note that you must fully qualify the reference to `String`. The `java.lang` package is automatically available to Java programs, but must be named explicitly in the call specifications.

Example 6-2 Publishing the main() Method

As a rule, Java names and call specification parameters must correspond. However, that rule does not apply to the `main()` method. Its `String[]` parameter can be mapped to multiple `CHAR` or `VARCHAR2` call specification parameters. Consider the `main()` method in the following class, which displays its arguments:

    public class EchoInput
    {
      public static void main (String[] args)
      {
        for (int i = 0; i < args.length; i++)
          System.out.println(args[i]);
      }
    }

To publish `main()`, write the following call specification:

    CREATE OR REPLACE PROCEDURE echo_input(s1 VARCHAR2, s2 VARCHAR2, s3 VARCHAR2)
    AS LANGUAGE JAVA
    NAME 'EchoInput.main(java.lang.String[])';

You cannot impose constraints, such as precision, size, and `NOT NULL`, on the call specification parameters. As a result, you cannot specify a maximum size for the `VARCHAR2` parameters. However, you must do so for `VARCHAR2` variables, as in:

    DECLARE last_name VARCHAR2(20); -- size constraint required

Example 6-3 Publishing a Method That Returns an Integer Value

In the following example, the `rowCount()` method, which returns the number of rows in a given database table, is published:

    import java.sql.*;
    import java.io.*;
    import oracle.jdbc.*;

    public class RowCounter
    {
      public static int rowCount (String tabName) throws SQLException
      {
        Connection conn = DriverManager.getConnection("jdbc:default:connection:");
        String sql = "SELECT COUNT(*) FROM " + tabName;
        int rows = 0;
        try
        {
          Statement stmt = conn.createStatement();
          ResultSet rset = stmt.executeQuery(sql);
          while (rset.next())
          {
            rows = rset.getInt(1);
          }
          rset.close();
          stmt.close();
        }
        catch (SQLException e)
        {
          System.err.println(e.getMessage());
        }
        return rows;
      }
    }

`NUMBER` subtypes, such as `INTEGER`, `REAL`, and `POSITIVE`, are not allowed in a call specification. As a result, in the following call specification, the return type is `NUMBER` and not `INTEGER`:

    CREATE FUNCTION row_count (tab_name VARCHAR2) RETURN NUMBER
    AS LANGUAGE JAVA
    NAME 'RowCounter.rowCount(java.lang.String) return int';

Example 6-4 Publishing a Method That Switches the Values of Its Arguments

Consider the `swap()` method in the following `Swapper` class, which switches the values of its arguments:

    public class Swapper
    {
      public static void swap (int[] x, int[] y)
      {
        int hold = x[0];
        x[0] = y[0];
        y[0] = hold;
      }
    }

The call specification publishes the `swap()` method as a call specification, `swap()`. The call specification declares `IN OUT` formal parameters, because values must be passed in and out. All call specification `OUT` and `IN OUT` parameters must map to Java array parameters.

    CREATE PROCEDURE swap (x IN OUT NUMBER, y IN OUT NUMBER)
    AS LANGUAGE JAVA
    NAME 'Swapper.swap(int[], int[])';

**Note:**

A Java method and its call specification can have the same name.
