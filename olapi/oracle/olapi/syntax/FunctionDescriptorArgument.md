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

- [Prev Class](FunctionDescriptor.md)
- [Next Class](FunctionDescriptorCatalog.md)

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

## Class FunctionDescriptorArgument

- java.lang.Object

- - oracle.olapi.syntax.FunctionDescriptorArgument

<!-- -->

- Direct Known Subclasses:
  [FunctionDescriptorChoiceArgument](FunctionDescriptorChoiceArgument.md), [FunctionDescriptorConditionArgument](FunctionDescriptorConditionArgument.md), [FunctionDescriptorDimensionArgument](FunctionDescriptorDimensionArgument.md), [FunctionDescriptorGroupArgument](FunctionDescriptorGroupArgument.md), [FunctionDescriptorIdentifierArgument](FunctionDescriptorIdentifierArgument.md), [FunctionDescriptorKeywordArgument](FunctionDescriptorKeywordArgument.md), [FunctionDescriptorTypedExpressionArgument](FunctionDescriptorTypedExpressionArgument.md)

  ------------------------------------------------------------------------



      public abstract class FunctionDescriptorArgument
      extends java.lang.Object

  The abstract base for classes that represent descriptors for the arguments for a `FunctionDescriptor`. The subclasses of `FunctionDescriptorArgument` represent different types of arguments to an `Expression` function. Oracle OLAP creates `FunctionDescriptorArgument` objects when it creates `FunctionDescriptor` objects.
  See Also:
  [`FunctionDescriptor`](FunctionDescriptor.md)

<!-- -->

- - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type | Method and Description                                                                                                   |
    |-------------------|--------------------------------------------------------------------------------------------------------------------------|
    | `boolean`         | `isOptional``()`<br>Indicates whether this `FunctionDescriptorArgument` represents an optional argument to the function. |
    | `boolean`         | `isRepeated``()`<br>Indicates whether this `FunctionDescriptorArgument` represents a repeated argument to the function.  |

    - ### Methods inherited from class java.lang.Object

      `clone, equals, finalize, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

<!-- -->

- - ### Method Detail

    - #### isOptional

          public final boolean isOptional()

      Indicates whether this `FunctionDescriptorArgument` represents an optional argument to the function.
      Returns:
      A `boolean` that is `true` if this `FunctionDescriptorArgument` is optional or `false` if it is not.

    <!-- -->

    - #### isRepeated

          public final boolean isRepeated()

      Indicates whether this `FunctionDescriptorArgument` represents a repeated argument to the function.
      Returns:
      A `boolean` that is `true` if this is a repeated argument or `false` if it is not.

Skip navigation links

- [Overview](../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../deprecated-list.md)
- [Index](../../../index-all.md)
- [Help](../../../help-doc.md)

Copyright © 2002, 2018, Oracle. All rights reserved.

- [Prev Class](FunctionDescriptor.md)
- [Next Class](FunctionDescriptorCatalog.md)

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
