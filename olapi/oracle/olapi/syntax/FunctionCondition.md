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

- [Prev Class](FunctionArgument.md)
- [Next Class](FunctionDescriptor.md)

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

## Class FunctionCondition

- java.lang.Object

- - [oracle.olapi.syntax.SyntaxObject](SyntaxObject.md)

  - - [oracle.olapi.syntax.DataObject](DataObject.md)

    - - [oracle.olapi.syntax.Expression](Expression.md)

      - - [oracle.olapi.syntax.Condition](Condition.md)

        - - oracle.olapi.syntax.FunctionCondition

<!-- -->

- All Implemented Interfaces:
  [FunctionArgument](FunctionArgument.md)

  ------------------------------------------------------------------------



      public final class FunctionCondition
      extends Condition

  A `Condition` that represents a condition that evaluates a `FunctionArgument` that produces a Boolean value. For example, the following code creates a `FunctionCondition` for the `LNNVL` function.
        NumberExpression rhsArg = new NumberExpression(.2);
        StringExpression lhsArg = new StringExpression("commission_pct");
        ValueComparisonCondition funcArg =
              new ValueComparisonCondition(lhsArg,
                                           ValueComparisonCondition.LT,
                                           rhsArg);
        FunctionCondition fc = new FunctionCondition("LNNVL", funcArg);

  The `toSyntax` method of the `fc` object returns a `String` that contains the following:

       LNNVL('commission_pct' < 0.2)

  You can create the same `FunctionCondition` by using the `SyntaxObject.fromSyntax` method, as in the following, where `metadataProvider` is an `MdmMetadataProvider`:

       FunctionCondition fc = (FunctionCondition)
                              SyntaxObject.fromSyntax("LNNVL('commission_pct' < .2)",
                                                       metadataProvider);

<!-- -->

- - ### Constructor Summary

    **Constructors**

    | Constructor and Description                                                                                                                                                                                                                                                                                                                                |
    |------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `FunctionCondition``(java.lang.String functionName)`<br>Creates a `FunctionCondition` that has the specified function, which requires no arguments.                                                                                                                                                                                                        |
    | `FunctionCondition``(java.lang.String functionName, `[`FunctionArgument`](FunctionArgument.md)` arg1)`<br>Creates a `FunctionCondition` that has the specified function, which takes one argument.                                                                                                                                                         |
    | `FunctionCondition``(java.lang.String functionName, `[`FunctionArgument`](FunctionArgument.md)`[] args)`<br>Creates a `FunctionCondition` that has the specified function.                                                                                                                                                                                 |
    | `FunctionCondition``(java.lang.String functionName, `[`FunctionArgument`](FunctionArgument.md)` arg1, `[`FunctionArgument`](FunctionArgument.md)` arg2)`<br>Creates a `FunctionCondition` that has the specified function, which takes two arguments.                                                                                                      |
    | `FunctionCondition``(java.lang.String functionName, `[`FunctionArgument`](FunctionArgument.md)` arg1, `[`FunctionArgument`](FunctionArgument.md)` arg2, `[`FunctionArgument`](FunctionArgument.md)` arg3)`<br>Creates a `FunctionCondition` that has the specified function, which takes three arguments.                                                  |
    | `FunctionCondition``(java.lang.String functionName, `[`FunctionArgument`](FunctionArgument.md)` arg1, `[`FunctionArgument`](FunctionArgument.md)` arg2, `[`FunctionArgument`](FunctionArgument.md)` arg3, `[`FunctionArgument`](FunctionArgument.md)` arg4)`<br>Creates a `FunctionCondition` that has the specified function, which takes four arguments. |
    | `FunctionCondition``(java.lang.String functionName, java.util.List<`[`FunctionArgument`](FunctionArgument.md)`> args)`                                                                                                                                                                                                                                     |

  <!-- -->

  - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type                             | Method and Description                                                                                                                                                                                                                    |
    |-----------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | [`FunctionArgument`](FunctionArgument.md)`[]` | `getArguments``()`<br>Gets the arguments for this `FunctionCondition`.                                                                                                                                                                    |
    | [`FunctionDescriptor`](FunctionDescriptor.md) | `getFunctionDescriptor``()`<br>Gets the `FunctionDescriptor` for this `FunctionCondition`.                                                                                                                                                |
    | `java.lang.String`                            | `getFunctionName``()`<br>Gets the name of the function that this `FunctionCondition` represents.                                                                                                                                          |
    | `java.lang.Object`                            | `visit``(`[`SyntaxObjectVisitor`](SyntaxObjectVisitor.md)` visitor, java.lang.Object context)`<br>Calls the `visitFunctionCondition` method of the `SyntaxObjectVisitor` and passes that method this `FunctionCondition` and an `Object`. |

    - ### Methods inherited from class oracle.olapi.syntax.[Condition](Condition.md)

      [`and`](Condition.md)`, `[`isCompositeObject`](Condition.md)`, `[`not`](Condition.md)`, `[`or`](Condition.md)

    <!-- -->

    - ### Methods inherited from class oracle.olapi.syntax.[SyntaxObject](SyntaxObject.md)

      [`equals`](SyntaxObject.md)`, `[`equals`](SyntaxObject.md)`, `[`fromSyntax`](SyntaxObject.md)`, `[`fromSyntax`](SyntaxObject.md)`, `[`fromSyntax`](SyntaxObject.md)`, `[`fromSyntax`](SyntaxObject.md)`, `[`fromSyntax`](SyntaxObject.md)`, `[`isValid`](SyntaxObject.md)`, `[`toSyntax`](SyntaxObject.md)`, `[`toSyntax`](SyntaxObject.md)`, `[`toSyntax`](SyntaxObject.md)`, `[`toSyntax`](SyntaxObject.md)`, `[`toSyntax`](SyntaxObject.md)`, `[`toSyntax`](SyntaxObject.md)

    <!-- -->

    - ### Methods inherited from class java.lang.Object

      `clone, equals, finalize, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

<!-- -->

- - ### Constructor Detail

    - #### FunctionCondition

          public FunctionCondition(java.lang.String functionName,
                                   FunctionArgument[] args)

      Creates a `FunctionCondition` that has the specified function.
      Parameters:
      `functionName` - A `String` that contains the name of the function.

      `args` - An array of `FunctionArgument` objects that have the arguments required by the function.

    <!-- -->

    - #### FunctionCondition

          public FunctionCondition(java.lang.String functionName,
                                   java.util.List<FunctionArgument> args)

    <!-- -->

    - #### FunctionCondition

          public FunctionCondition(java.lang.String functionName)

      Creates a `FunctionCondition` that has the specified function, which requires no arguments.
      Parameters:
      `functionName` - A `String` that contains the name of the function.

    <!-- -->

    - #### FunctionCondition

          public FunctionCondition(java.lang.String functionName,
                                   FunctionArgument arg1)

      Creates a `FunctionCondition` that has the specified function, which takes one argument.
      Parameters:
      `functionName` - A `String` that contains the name of the function.

      `arg1` - A `FunctionArgument` that has the argument required by the function.

    <!-- -->

    - #### FunctionCondition

          public FunctionCondition(java.lang.String functionName,
                                   FunctionArgument arg1,
                                   FunctionArgument arg2)

      Creates a `FunctionCondition` that has the specified function, which takes two arguments.
      Parameters:
      `functionName` - A `String` that contains the name of the function.

      `arg1` - A `FunctionArgument` that has the first argument required by the function.

      `arg2` - A `FunctionArgument` that has the second argument required by the function.

    <!-- -->

    - #### FunctionCondition

          public FunctionCondition(java.lang.String functionName,
                                   FunctionArgument arg1,
                                   FunctionArgument arg2,
                                   FunctionArgument arg3)

      Creates a `FunctionCondition` that has the specified function, which takes three arguments.
      Parameters:
      `functionName` - A `String` that contains the name of the function.

      `arg1` - A `FunctionArgument` that has the first argument required by the function.

      `arg2` - A `FunctionArgument` that has the second argument required by the function.

      `arg3` - A `FunctionArgument` that has the third argument required by the function.

    <!-- -->

    - #### FunctionCondition

          public FunctionCondition(java.lang.String functionName,
                                   FunctionArgument arg1,
                                   FunctionArgument arg2,
                                   FunctionArgument arg3,
                                   FunctionArgument arg4)

      Creates a `FunctionCondition` that has the specified function, which takes four arguments.
      Parameters:
      `functionName` - A `String` that contains the name of the function.

      `arg1` - A `FunctionArgument` that has the first argument required by the function.

      `arg2` - A `FunctionArgument` that has the second argument required by the function.

      `arg3` - A `FunctionArgument` that has the third argument required by the function.

      `arg4` - A `FunctionArgument` that has the fourth argument required by the function.

  <!-- -->

  - ### Method Detail

    - #### visit

          public java.lang.Object visit(SyntaxObjectVisitor visitor,
                                        java.lang.Object context)

      Calls the `visitFunctionCondition` method of the `SyntaxObjectVisitor` and passes that method this `FunctionCondition` and an `Object`.
      Specified by:
      [`visit`](SyntaxObject.md) in class [`SyntaxObject`](SyntaxObject.md)

      Parameters:
      `visitor` - A `SyntaxObjectVisitor`.

      `context` - An `Object`.

      Returns:
      The `Object` returned by the `visitFunctionCondition` method.

    <!-- -->

    - #### getArguments

          public FunctionArgument[] getArguments()

      Gets the arguments for this `FunctionCondition`.
      Returns:
      An array of `FunctionArgument` objects that are the arguments for this `FunctionCondition`.

    <!-- -->

    - #### getFunctionDescriptor

          public FunctionDescriptor getFunctionDescriptor()

      Gets the `FunctionDescriptor` for this `FunctionCondition`.
      Returns:
      The `FunctionDescriptor` for this `FunctionCondition`.

    <!-- -->

    - #### getFunctionName

          public java.lang.String getFunctionName()

      Gets the name of the function that this `FunctionCondition` represents.
      Returns:
      A `String` that contains the name of the function.

Skip navigation links

- [Overview](../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../deprecated-list.md)
- [Index](../../../index-all.md)
- [Help](../../../help-doc.md)

Copyright © 2002, 2018, Oracle. All rights reserved.

- [Prev Class](FunctionArgument.md)
- [Next Class](FunctionDescriptor.md)

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
