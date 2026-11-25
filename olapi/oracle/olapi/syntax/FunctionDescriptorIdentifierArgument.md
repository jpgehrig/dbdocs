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

- [Prev Class](FunctionDescriptorGroupArgument.md)
- [Next Class](FunctionDescriptorKeywordArgument.md)

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

## Class FunctionDescriptorIdentifierArgument

- java.lang.Object

- - [oracle.olapi.syntax.FunctionDescriptorArgument](FunctionDescriptorArgument.md)

  - - oracle.olapi.syntax.FunctionDescriptorIdentifierArgument

<!-- -->

-

  ------------------------------------------------------------------------



      public final class FunctionDescriptorIdentifierArgument
      extends FunctionDescriptorArgument

  A `FunctionDescriptorArgument` for an function argument that is an `IdentifierArgument`.

<!-- -->

- - ### Field Summary

    **Fields**

    | Modifier and Type | Field and Description                                                                                                                                          |
    |-------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `static int`      | `LOSSLESS_TYPE`<br>A constant that indicates that the return type depends on the return types of the expression or expressions on which the function operates. |
    | `static int`      | `NO_EFFECT`<br>A constant that indicates that the argument has no effect on the return type of the function.                                                   |

  <!-- -->

  - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type  | Method and Description                                                                                                                                         |
    |--------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `java.lang.String` | `getArgumentName``()`<br>Gets a name that describes the argument for the function description.                                                                 |
    | `int`              | `getReturnTypeEffect``()`<br>Gets the value of one of the fields of this class, which indicates the effect of the argument on the return type of the function. |

    - ### Methods inherited from class oracle.olapi.syntax.[FunctionDescriptorArgument](FunctionDescriptorArgument.md)

      [`isOptional`](FunctionDescriptorArgument.md)`, `[`isRepeated`](FunctionDescriptorArgument.md)

    <!-- -->

    - ### Methods inherited from class java.lang.Object

      `clone, equals, finalize, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

<!-- -->

- - ### Field Detail

    - #### NO_EFFECT

          public static final int NO_EFFECT

      A constant that indicates that the argument has no effect on the return type of the function.
      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### LOSSLESS_TYPE

          public static final int LOSSLESS_TYPE

      A constant that indicates that the return type depends on the return types of the expression or expressions on which the function operates.
      See Also:
      [Constant Field Values](../../../constant-values.md)

  <!-- -->

  - ### Method Detail

    - #### getArgumentName

          public java.lang.String getArgumentName()

      Gets a name that describes the argument for the function description.
      Returns:
      A `String` that contains a name for the argument.

    <!-- -->

    - #### getReturnTypeEffect

          public int getReturnTypeEffect()

      Gets the value of one of the fields of this class, which indicates the effect of the argument on the return type of the function.
      Returns:
      An integer that represents the effect of the argument on the return type.

Skip navigation links

- [Overview](../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../deprecated-list.md)
- [Index](../../../index-all.md)
- [Help](../../../help-doc.md)

Copyright © 2002, 2018, Oracle. All rights reserved.

- [Prev Class](FunctionDescriptorGroupArgument.md)
- [Next Class](FunctionDescriptorKeywordArgument.md)

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
