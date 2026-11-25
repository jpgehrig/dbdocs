Skip navigation links

- [Overview](../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../deprecated-list.md)
- [Index](../../../index-all.md)
- [Help](../../../help-doc.md)

**Oracle® OLAP Java API Reference
19c**
E96404-01

- [Prev Class](NAValueException.md)
- Next Class

<!-- -->

- [Frames](../../../index.md)
- No Frames

<!-- -->

- [All Classes](../../../allclasses-noframe.md)

<!-- -->

- Summary: 
- Nested \| 
- Field \| 
- Constr \| 
- Method

<!-- -->

- Detail: 
- Field \| 
- Constr \| 
- Method

oracle.express.spl

## Class SPLExecutor

- java.lang.Object

- - oracle.express.spl.SPLExecutor

<!-- -->

-

  ------------------------------------------------------------------------



      public class SPLExecutor
      extends java.lang.Object

  An object that accepts a `String` and sends it to Oracle OLAP for internal execution or evaluation.
  Using an `SPLExecutor`, an application can execute a command in the OLAP Data Manipulation Language (DML), which is also referred to as a Stored Procedure Language (SPL). Alternatively, an application can evaluate an expression in that language.

  Depending on the evaluation method that you use, the return value of the method is a `boolean`, `int`, `double`, or other data type. An executed command always returns a `String`. The length of the `String` returned by the `executeCommand` method is limited to 4,000 single-byte characters.

  For more information about the DML, see *Oracle OLAP DML Reference*.

<!-- -->

- - ### Constructor Summary

    **Constructors**

    | Constructor and Description                                                                     |
    |-------------------------------------------------------------------------------------------------|
    | `SPLExecutor``(oracle.jdbc.OracleConnection connection)`<br>Creates a new `SPLExecutor` object. |

  <!-- -->

  - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type    | Method and Description                                                                                                                                                                                     |
    |----------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `boolean`            | `evaluateBooleanExpression``(java.lang.String expr)`<br>Interprets `expr` as a DML BOOLEAN expression, which Oracle OLAP evaluates, and returns the result as a `boolean`.                                 |
    | `java.util.Date`     | `evaluateDateExpression``(java.lang.String expr)`<br>Interprets `expr` as a DML DATE expression, which Oracle OLAP evaluates, and returns the result as a `Date`.                                          |
    | `double`             | `evaluateDecimalExpression``(java.lang.String expr)`<br>Interprets `expr` as a DML numeric expression, which Oracle OLAP evaluates as a DML DECIMAL, and returns the result as an `double` value.          |
    | `int`                | `evaluateIntegerExpression``(java.lang.String expr)`<br>Interprets `expr` as a DML numeric expression, which Oracle OLAP evaluates as a DML INTEGER, and returns the result as an `int` value.             |
    | `float`              | `evaluateShortDecimalExpression``(java.lang.String expr)`<br>Interprets `expr` as a DML numeric expression, which Oracle OLAP evaluates as a DML SHORTDECIMAL, and returns the result as an `float` value. |
    | `short`              | `evaluateShortIntegerExpression``(java.lang.String expr)`<br>Interprets `expr` as a DML numeric expression, which Oracle OLAP evaluates as a DML SHORTINTEGER, and returns the result as an `short` value. |
    | `java.lang.String`   | `evaluateStringExpression``(java.lang.String expr)`<br>Interprets `expr` as a DML TEXT expression, which Oracle OLAP evaluates, and returns the result as a `String`.                                      |
    | `java.lang.String[]` | `evaluateStringListExpression``(java.lang.String expr)`<br>Interprets `expr` as a DML TEXT expression, which Oracle OLAP evaluates, and returns the result as an array of `String` objects.                |
    | `java.lang.String`   | `executeCommand``(java.lang.String command)`<br>Interprets `command` as a DML command, which Oracle OLAP executes, and returns the result of the command.                                                  |
    | `void`               | `initialize``()`<br>Initializes the `SPLExecutor`.                                                                                                                                                         |

    - ### Methods inherited from class java.lang.Object

      `clone, equals, finalize, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

<!-- -->

- - ### Constructor Detail

    - #### SPLExecutor

          public SPLExecutor(oracle.jdbc.OracleConnection connection)

      Creates a new `SPLExecutor` object. After creating an `SPLExecutor`, call its `initialize` method.
      Parameters:
      `connection` - The `oracle.jdbc.OracleConnection` that you used to connect to the Oracle Database.

  <!-- -->

  - ### Method Detail

    - #### initialize

          public void initialize()
                          throws java.sql.SQLException

      Initializes the `SPLExecutor`. Always call this method after creating a new `SPLExecutor` object. This method throws a `java.sql.SQLException` if an error occurs when OLAP OLAP is preparing for its OLAP DML interactions.
      Throws:
      `java.sql.SQLException`

    <!-- -->

    - #### executeCommand

          public java.lang.String executeCommand(java.lang.String command)
                                          throws ObjectClosedException,
                                                 ExpressServerException

      Interprets `command` as a DML command, which Oracle OLAP executes, and returns the result of the command. The length of the `String` returned by this method is limited to 4,000 single-byte characters.
      Parameters:
      `command` - A `String` containing the DML command to execute.

      Returns:
      A `String` containing the execution log that results from the execution of the specified DML command. If the command was successful, then the log contains the return value of the command as a `String`. If the command was unsuccessful, then the `String` contains the resulting error report.

      Throws:
      [`ObjectClosedException`](../ObjectClosedException.md)

      [`ExpressServerException`](../ExpressServerException.md)

    <!-- -->

    - #### evaluateIntegerExpression

          public int evaluateIntegerExpression(java.lang.String expr)
                                        throws NAValueException,
                                               ObjectClosedException,
                                               ExpressServerException

      Interprets `expr` as a DML numeric expression, which Oracle OLAP evaluates as a DML INTEGER, and returns the result as an `int` value.
      Parameters:
      `expr` - A `String` that can be interpreted as a numeric expression by Oracle OLAP.

      Returns:
      The `int` value to which the expression evaluated.

      Throws:
      [`NAValueException`](NAValueException.md)

      [`ObjectClosedException`](../ObjectClosedException.md)

      [`ExpressServerException`](../ExpressServerException.md)

    <!-- -->

    - #### evaluateShortIntegerExpression

          public short evaluateShortIntegerExpression(java.lang.String expr)
                                               throws NAValueException,
                                                      ObjectClosedException,
                                                      ExpressServerException

      Interprets `expr` as a DML numeric expression, which Oracle OLAP evaluates as a DML SHORTINTEGER, and returns the result as an `short` value.
      Parameters:
      `expr` - A `String` that can be interpreted as a numeric expression by Oracle OLAP.

      Returns:
      The `short` value to which the expression evaluated.

      Throws:
      [`NAValueException`](NAValueException.md)

      [`ObjectClosedException`](../ObjectClosedException.md)

      [`ExpressServerException`](../ExpressServerException.md)

    <!-- -->

    - #### evaluateDecimalExpression

          public double evaluateDecimalExpression(java.lang.String expr)
                                           throws NAValueException,
                                                  ObjectClosedException,
                                                  ExpressServerException

      Interprets `expr` as a DML numeric expression, which Oracle OLAP evaluates as a DML DECIMAL, and returns the result as an `double` value.
      Parameters:
      `expr` - A `String` that can be interpreted as a numeric expression by Oracle OLAP.

      Returns:
      The `double` value to which the expression evaluated.

      Throws:
      [`NAValueException`](NAValueException.md)

      [`ObjectClosedException`](../ObjectClosedException.md)

      [`ExpressServerException`](../ExpressServerException.md)

    <!-- -->

    - #### evaluateShortDecimalExpression

          public float evaluateShortDecimalExpression(java.lang.String expr)
                                               throws NAValueException,
                                                      ObjectClosedException,
                                                      ExpressServerException

      Interprets `expr` as a DML numeric expression, which Oracle OLAP evaluates as a DML SHORTDECIMAL, and returns the result as an `float` value.
      Parameters:
      `expr` - A `String` that can be interpreted as a numeric expression by Oracle OLAP.

      Returns:
      The `float` value to which the expression evaluated.

      Throws:
      [`NAValueException`](NAValueException.md)

      [`ObjectClosedException`](../ObjectClosedException.md)

      [`ExpressServerException`](../ExpressServerException.md)

    <!-- -->

    - #### evaluateStringExpression

          public java.lang.String evaluateStringExpression(java.lang.String expr)
                                                    throws NAValueException,
                                                           ObjectClosedException,
                                                           ExpressServerException

      Interprets `expr` as a DML TEXT expression, which Oracle OLAP evaluates, and returns the result as a `String`.
      Parameters:
      `expr` - A `String` that can be interpreted as a TEXT expression by Oracle OLAP.

      Returns:
      The `String` to which the expression evaluated.

      Throws:
      [`NAValueException`](NAValueException.md)

      [`ObjectClosedException`](../ObjectClosedException.md)

      [`ExpressServerException`](../ExpressServerException.md)

    <!-- -->

    - #### evaluateStringListExpression

          public java.lang.String[] evaluateStringListExpression(java.lang.String expr)
                                                          throws NAValueException,
                                                                 ObjectClosedException,
                                                                 ExpressServerException

      Interprets `expr` as a DML TEXT expression, which Oracle OLAP evaluates, and returns the result as an array of `String` objects.
      Parameters:
      `expr` - A `String` that can be interpreted as a TEXT expression by Oracle OLAP.

      Returns:
      The array of `String` objects to which the expression evaluated.

      Throws:
      [`NAValueException`](NAValueException.md)

      [`ObjectClosedException`](../ObjectClosedException.md)

      [`ExpressServerException`](../ExpressServerException.md)

    <!-- -->

    - #### evaluateBooleanExpression

          public boolean evaluateBooleanExpression(java.lang.String expr)
                                            throws NAValueException,
                                                   ObjectClosedException,
                                                   ExpressServerException

      Interprets `expr` as a DML BOOLEAN expression, which Oracle OLAP evaluates, and returns the result as a `boolean`.
      Parameters:
      `expr` - A `String` that can be interpreted as a BOOLEAN expression by Oracle OLAP.

      Returns:
      The `boolean` value to which the expression evaluated.

      Throws:
      [`NAValueException`](NAValueException.md)

      [`ObjectClosedException`](../ObjectClosedException.md)

      [`ExpressServerException`](../ExpressServerException.md)

    <!-- -->

    - #### evaluateDateExpression

          public java.util.Date evaluateDateExpression(java.lang.String expr)
                                                throws NAValueException,
                                                       ObjectClosedException,
                                                       ExpressServerException

      Interprets `expr` as a DML DATE expression, which Oracle OLAP evaluates, and returns the result as a `Date`.
      Parameters:
      `expr` - A `String` that can be interpreted as a DATE expression by Oracle OLAP.

      Returns:
      The `Date` to which the expression evaluated.

      Throws:
      [`NAValueException`](NAValueException.md)

      [`ObjectClosedException`](../ObjectClosedException.md)

      [`ExpressServerException`](../ExpressServerException.md)

Skip navigation links

- [Overview](../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../deprecated-list.md)
- [Index](../../../index-all.md)
- [Help](../../../help-doc.md)

Copyright © 2002, 2018, Oracle. All rights reserved.

- [Prev Class](NAValueException.md)
- Next Class

<!-- -->

- [Frames](../../../index.md)
- No Frames

<!-- -->

- [All Classes](../../../allclasses-noframe.md)

<!-- -->

- Summary: 
- Nested \| 
- Field \| 
- Constr \| 
- Method

<!-- -->

- Detail: 
- Field \| 
- Constr \| 
- Method
