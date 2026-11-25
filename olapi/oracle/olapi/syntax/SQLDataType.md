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

- [Prev Class](SolveStepCommand.md)
- [Next Class](StarArgument.md)

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

oracle.olapi.syntax

## Class SQLDataType

- java.lang.Object

- - [oracle.olapi.syntax.SyntaxObject](SyntaxObject.md)

  - - oracle.olapi.syntax.SQLDataType

<!-- -->

-

  ------------------------------------------------------------------------



      public final class SQLDataType
      extends SyntaxObject

  An object that represents an Oracle Database data type with precision information.

<!-- -->

- - ### Constructor Summary

    **Constructors**

    | Constructor and Description                                                                                                             |
    |-----------------------------------------------------------------------------------------------------------------------------------------|
    | `SQLDataType``(`[`DataType`](DataType.md)` type)`<br>Creates a `SQLDataType` that has the default precision of the specified data type. |
    | `SQLDataType``(java.lang.String sqlText)`<br>Creates a `SQLDataType` that is based on a SQL statement.                                  |

  <!-- -->

  - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type         | Method and Description                                                                                                                                                                                               |
    |---------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | [`DataType`](DataType.md) | `getDataType``()`<br>Gets the `DataType` that is associated with this `SQLDataType`.                                                                                                                                 |
    | `java.lang.String`        | `getSQLText``()`<br>Gets the SQL statement that is associated with this `SQLDataType`.                                                                                                                               |
    | `java.lang.Object`        | `visit``(`[`SyntaxObjectVisitor`](SyntaxObjectVisitor.md)` visitor, java.lang.Object context)`<br>Calls the appropriate method of a `SyntaxObjectVisitor` and passes that method the `SyntaxObject` and an `Object`. |

    - ### Methods inherited from class oracle.olapi.syntax.[SyntaxObject](SyntaxObject.md)

      [`equals`](SyntaxObject.md)`, `[`equals`](SyntaxObject.md)`, `[`fromSyntax`](SyntaxObject.md)`, `[`fromSyntax`](SyntaxObject.md)`, `[`fromSyntax`](SyntaxObject.md)`, `[`fromSyntax`](SyntaxObject.md)`, `[`fromSyntax`](SyntaxObject.md)`, `[`isValid`](SyntaxObject.md)`, `[`toSyntax`](SyntaxObject.md)`, `[`toSyntax`](SyntaxObject.md)`, `[`toSyntax`](SyntaxObject.md)`, `[`toSyntax`](SyntaxObject.md)`, `[`toSyntax`](SyntaxObject.md)`, `[`toSyntax`](SyntaxObject.md)

    <!-- -->

    - ### Methods inherited from class java.lang.Object

      `clone, equals, finalize, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

<!-- -->

- - ### Constructor Detail

    - #### SQLDataType

          public SQLDataType(java.lang.String sqlText)

      Creates a `SQLDataType` that is based on a SQL statement.
      Parameters:
      `sqlText` - A `String` that contains a SQL statement that defines a data type.

    <!-- -->

    - #### SQLDataType

          public SQLDataType(DataType type)

      Creates a `SQLDataType` that has the default precision of the specified data type.
      Parameters:
      `type` - The `DataType` to associate with the new `SQLDataType`.

  <!-- -->

  - ### Method Detail

    - #### visit

          public java.lang.Object visit(SyntaxObjectVisitor visitor,
                                        java.lang.Object context)

      Calls the appropriate method of a `SyntaxObjectVisitor` and passes that method the `SyntaxObject` and an `Object`.
      Specified by:
      [`visit`](SyntaxObject.md) in class [`SyntaxObject`](SyntaxObject.md)

      Parameters:
      `visitor` - A `SyntaxObjectVisitor`.

      `context` - An `Object`.

      Returns:
      The `Object` returned by the `visitClearCommand` method.

    <!-- -->

    - #### getDataType

          public DataType getDataType()

      Gets the `DataType` that is associated with this `SQLDataType`.
      Returns:
      The `DataType` associated with this `SQLDataType`.

    <!-- -->

    - #### getSQLText

          public java.lang.String getSQLText()

      Gets the SQL statement that is associated with this `SQLDataType`.
      Returns:
      A `String` that contains the SQL statement associated with this `SQLDataType`.

Skip navigation links

- [Overview](../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../deprecated-list.md)
- [Index](../../../index-all.md)
- [Help](../../../help-doc.md)

Copyright © 2002, 2018, Oracle. All rights reserved.

- [Prev Class](SolveStepCommand.md)
- [Next Class](StarArgument.md)

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
