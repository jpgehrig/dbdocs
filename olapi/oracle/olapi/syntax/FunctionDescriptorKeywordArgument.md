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

- [Prev Class](FunctionDescriptorIdentifierArgument.md)
- [Next Class](FunctionDescriptorTypedExpressionArgument.md)

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

## Class FunctionDescriptorKeywordArgument

- java.lang.Object

- - [oracle.olapi.syntax.FunctionDescriptorArgument](FunctionDescriptorArgument.md)

  - - oracle.olapi.syntax.FunctionDescriptorKeywordArgument

<!-- -->

-

  ------------------------------------------------------------------------



      public final class FunctionDescriptorKeywordArgument
      extends FunctionDescriptorArgument

  A `FunctionDescriptorArgument` for an function argument that is a `KeywordArgument`.

<!-- -->

- - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type                       | Method and Description                                                                      |
    |-----------------------------------------|---------------------------------------------------------------------------------------------|
    | [`KeywordArgument`](KeywordArgument.md) | `getKeyword``()`<br>Gets the keyword that is the argument for the function description.     |
    | [`DataType`](DataType.md)               | `getReturnDataType``()`<br>Gets the data type of the argument for the function description. |

    - ### Methods inherited from class oracle.olapi.syntax.[FunctionDescriptorArgument](FunctionDescriptorArgument.md)

      [`isOptional`](FunctionDescriptorArgument.md)`, `[`isRepeated`](FunctionDescriptorArgument.md)

    <!-- -->

    - ### Methods inherited from class java.lang.Object

      `clone, equals, finalize, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

<!-- -->

- - ### Method Detail

    - #### getKeyword

          public KeywordArgument getKeyword()

      Gets the keyword that is the argument for the function description.
      Returns:
      A `String` that contains the keyword for the argument.

    <!-- -->

    - #### getReturnDataType

          public DataType getReturnDataType()

      Gets the data type of the argument for the function description.
      Returns:
      A `DataType` that indicates the data type of the argument.

Skip navigation links

- [Overview](../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../deprecated-list.md)
- [Index](../../../index-all.md)
- [Help](../../../help-doc.md)

Copyright © 2002, 2018, Oracle. All rights reserved.

- [Prev Class](FunctionDescriptorIdentifierArgument.md)
- [Next Class](FunctionDescriptorTypedExpressionArgument.md)

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
