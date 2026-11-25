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

- [Prev Class](SolveCommand.md)
- [Next Class](SQLDataType.md)

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

## Class SolveStepCommand

- java.lang.Object

- - [oracle.olapi.syntax.SyntaxObject](SyntaxObject.md)

  - - [oracle.olapi.syntax.BuildCommand](BuildCommand.md)

    - - [oracle.olapi.syntax.SimpleCommand](SimpleCommand.md)

      - - oracle.olapi.syntax.SolveStepCommand

<!-- -->

- Direct Known Subclasses:
  [AggregationCommand](AggregationCommand.md)

  ------------------------------------------------------------------------



      public abstract class SolveStepCommand
      extends SimpleCommand

  An abstract `SimpleCommand` that specifes a function that is one step in the operations that calculate the data for the measures of an `MdmCube`. The methods of a `SolveStepCommand` return information about the function.

<!-- -->

- - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type                             | Method and Description                                                                                               |
    |-----------------------------------------------|----------------------------------------------------------------------------------------------------------------------|
    | [`FunctionArgument`](FunctionArgument.md)`[]` | `getArguments``()`<br>Gets the arguments for the function specified by the `SolveStepCommand`.                       |
    | [`FunctionDescriptor`](FunctionDescriptor.md) | `getFunctionDescriptor``()`<br>Gets the `FunctionDescriptor` for the function that the `SolveStepCommand` specifies. |
    | `java.lang.String`                            | `getFunctionName``()`<br>Gets the name of the function that the `SolveStepCommand` specifies.                        |

    - ### Methods inherited from class oracle.olapi.syntax.[SyntaxObject](SyntaxObject.md)

      [`equals`](SyntaxObject.md)`, `[`equals`](SyntaxObject.md)`, `[`fromSyntax`](SyntaxObject.md)`, `[`fromSyntax`](SyntaxObject.md)`, `[`fromSyntax`](SyntaxObject.md)`, `[`fromSyntax`](SyntaxObject.md)`, `[`fromSyntax`](SyntaxObject.md)`, `[`isValid`](SyntaxObject.md)`, `[`toSyntax`](SyntaxObject.md)`, `[`toSyntax`](SyntaxObject.md)`, `[`toSyntax`](SyntaxObject.md)`, `[`toSyntax`](SyntaxObject.md)`, `[`toSyntax`](SyntaxObject.md)`, `[`toSyntax`](SyntaxObject.md)`, `[`visit`](SyntaxObject.md)

    <!-- -->

    - ### Methods inherited from class java.lang.Object

      `clone, equals, finalize, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

<!-- -->

- - ### Method Detail

    - #### getArguments

          public FunctionArgument[] getArguments()

      Gets the arguments for the function specified by the `SolveStepCommand`.
      Returns:
      An array of the `FunctionArgument` objects of the `SolveStepCommand`.

    <!-- -->

    - #### getFunctionDescriptor

          public FunctionDescriptor getFunctionDescriptor()

      Gets the `FunctionDescriptor` for the function that the `SolveStepCommand` specifies.
      Returns:
      The `FunctionDescriptor` for the function of the `SolveStepCommand`.

    <!-- -->

    - #### getFunctionName

          public java.lang.String getFunctionName()

      Gets the name of the function that the `SolveStepCommand` specifies.
      Returns:
      A `String` that contains the name of the function of the `SolveStepCommand`.

Skip navigation links

- [Overview](../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../deprecated-list.md)
- [Index](../../../index-all.md)
- [Help](../../../help-doc.md)

Copyright © 2002, 2018, Oracle. All rights reserved.

- [Prev Class](SolveCommand.md)
- [Next Class](SQLDataType.md)

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
