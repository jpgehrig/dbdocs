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

- [Prev Class](BetweenCondition.md)
- [Next Class](BinaryOperatorExpression.md)

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

## Class BinaryOperatorCondition

- java.lang.Object

- - [oracle.olapi.syntax.SyntaxObject](SyntaxObject.md)

  - - [oracle.olapi.syntax.DataObject](DataObject.md)

    - - [oracle.olapi.syntax.Expression](Expression.md)

      - - [oracle.olapi.syntax.Condition](Condition.md)

        - - oracle.olapi.syntax.BinaryOperatorCondition

<!-- -->

- All Implemented Interfaces:
  [FunctionArgument](FunctionArgument.md)

  ------------------------------------------------------------------------



      public final class BinaryOperatorCondition
      extends Condition

  A `Condition` that represents a logical `AND` or `OR` condition that operates on two component `Condition` objects.

<!-- -->

- - ### Field Summary

    **Fields**

    | Modifier and Type         | Field and Description                                              |
    |---------------------------|--------------------------------------------------------------------|
    | `static java.lang.String` | `OP_AND`<br>A constant that represents the logical operator `AND`. |
    | `static java.lang.String` | `OP_OR`<br>A constant that represents the logical operator `OR`.   |

  <!-- -->

  - ### Constructor Summary

    **Constructors**

    | Constructor and Description                                                                                                                                                                                                                                               |
    |---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `BinaryOperatorCondition``(`[`Condition`](Condition.md)`[] arguments, java.lang.String operator)`<br>Creates a new `BinaryOperatorCondition` that has the specified arguments and operator.                                                                               |
    | `BinaryOperatorCondition``(`[`Condition`](Condition.md)` lhsArgument, java.lang.String operator, `[`Condition`](Condition.md)` rhsArgument)`<br>Creates a new `BinaryOperatorCondition` that has the specified left-hand-side and right-hand-side arguments and operator. |
    | `BinaryOperatorCondition``(java.util.List<`[`Condition`](Condition.md)`> arguments, java.lang.String operator)`<br>Creates a new `BinaryOperatorCondition` that has the specified arguments and operator.                                                                 |

  <!-- -->

  - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type               | Method and Description                                                                                                                                                                                                                                |
    |---------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | [`Condition`](Condition.md)`[]` | `getArguments``()`<br>Gets the arguments for this `BinaryOperatorCondition`.                                                                                                                                                                          |
    | `java.lang.String`              | `getOperator``()`<br>Gets the operator for this `BinaryOperatorCondition`, which is either `AND` or `OR`.                                                                                                                                             |
    | `java.lang.Object`              | `visit``(`[`SyntaxObjectVisitor`](SyntaxObjectVisitor.md)` visitor, java.lang.Object context)`<br>Calls the `visitBinaryOperatorCondition` method of the `SyntaxObjectVisitor` and passes that method this `BinaryOperatorCondition` and an `Object`. |

    - ### Methods inherited from class oracle.olapi.syntax.[Condition](Condition.md)

      [`and`](Condition.md)`, `[`isCompositeObject`](Condition.md)`, `[`not`](Condition.md)`, `[`or`](Condition.md)

    <!-- -->

    - ### Methods inherited from class oracle.olapi.syntax.[SyntaxObject](SyntaxObject.md)

      [`equals`](SyntaxObject.md)`, `[`equals`](SyntaxObject.md)`, `[`fromSyntax`](SyntaxObject.md)`, `[`fromSyntax`](SyntaxObject.md)`, `[`fromSyntax`](SyntaxObject.md)`, `[`fromSyntax`](SyntaxObject.md)`, `[`fromSyntax`](SyntaxObject.md)`, `[`isValid`](SyntaxObject.md)`, `[`toSyntax`](SyntaxObject.md)`, `[`toSyntax`](SyntaxObject.md)`, `[`toSyntax`](SyntaxObject.md)`, `[`toSyntax`](SyntaxObject.md)`, `[`toSyntax`](SyntaxObject.md)`, `[`toSyntax`](SyntaxObject.md)

    <!-- -->

    - ### Methods inherited from class java.lang.Object

      `clone, equals, finalize, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

<!-- -->

- - ### Field Detail

    - #### OP_AND

          public static final java.lang.String OP_AND

      A constant that represents the logical operator `AND`.
      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### OP_OR

          public static final java.lang.String OP_OR

      A constant that represents the logical operator `OR`.
      See Also:
      [Constant Field Values](../../../constant-values.md)

  <!-- -->

  - ### Constructor Detail

    - #### BinaryOperatorCondition

          public BinaryOperatorCondition(Condition[] arguments,
                                         java.lang.String operator)

      Creates a new `BinaryOperatorCondition` that has the specified arguments and operator.
      Parameters:
      `arguments` - An array of at least two `Condition` objects.

      `operator` - The operator to use, either `OP_AND` or `OP_OR`.

    <!-- -->

    - #### BinaryOperatorCondition

          public BinaryOperatorCondition(java.util.List<Condition> arguments,
                                         java.lang.String operator)

      Creates a new `BinaryOperatorCondition` that has the specified arguments and operator.
      Parameters:
      `arguments` - A list of at least two `Condition` objects.

      `operator` - The operator to use, either `OP_AND` or `OP_OR`.

    <!-- -->

    - #### BinaryOperatorCondition

          public BinaryOperatorCondition(Condition lhsArgument,
                                         java.lang.String operator,
                                         Condition rhsArgument)

      Creates a new `BinaryOperatorCondition` that has the specified left-hand-side and right-hand-side arguments and operator.
      Parameters:
      `lhsArgument` - The `Condition` to use as the left-hand-side argument.

      `operator` - The operator to use, either `OP_AND` or `OP_OR`.

      `rhsArgument` - The `Condition` to use as the right-hand-side argument.

  <!-- -->

  - ### Method Detail

    - #### visit

          public java.lang.Object visit(SyntaxObjectVisitor visitor,
                                        java.lang.Object context)

      Calls the `visitBinaryOperatorCondition` method of the `SyntaxObjectVisitor` and passes that method this `BinaryOperatorCondition` and an `Object`.
      Specified by:
      [`visit`](SyntaxObject.md) in class [`SyntaxObject`](SyntaxObject.md)

      Parameters:
      `visitor` - A `SyntaxObjectVisitor`.

      `context` - An `Object`.

      Returns:
      The `Object` returned by the `visitBinaryOperatorCondition` method.

    <!-- -->

    - #### getOperator

          public java.lang.String getOperator()

      Gets the operator for this `BinaryOperatorCondition`, which is either `AND` or `OR`.
      Returns:
      A `String` that contains `AND` or `OR`.

    <!-- -->

    - #### getArguments

          public Condition[] getArguments()

      Gets the arguments for this `BinaryOperatorCondition`.
      Returns:
      An array of `Condition` objects that are the left-hand-side and right-hand-side arguments for this `BinaryOperatorCondition`.

Skip navigation links

- [Overview](../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../deprecated-list.md)
- [Index](../../../index-all.md)
- [Help](../../../help-doc.md)

Copyright © 2002, 2018, Oracle. All rights reserved.

- [Prev Class](BetweenCondition.md)
- [Next Class](BinaryOperatorExpression.md)

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
