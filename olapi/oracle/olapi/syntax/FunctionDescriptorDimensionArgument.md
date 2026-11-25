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

- [Prev Class](FunctionDescriptorConditionArgument.md)
- [Next Class](FunctionDescriptorGroupArgument.md)

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

## Class FunctionDescriptorDimensionArgument

- java.lang.Object

- - [oracle.olapi.syntax.FunctionDescriptorArgument](FunctionDescriptorArgument.md)

  - - oracle.olapi.syntax.FunctionDescriptorDimensionArgument

<!-- -->

-

  ------------------------------------------------------------------------



      public final class FunctionDescriptorDimensionArgument
      extends FunctionDescriptorArgument

  A `FunctionDescriptorArgument` for a function argument that is a `DimensionArgument`.

<!-- -->

- - ### Field Summary

    **Fields**

    | Modifier and Type | Field and Description                                                                      |
    |-------------------|--------------------------------------------------------------------------------------------|
    | `static int`      | `DIMENSION_LEVEL`<br>A constant that represents an `MdmDimensionLevel` as an argument.     |
    | `static int`      | `HIERARCHY_LEVEL`<br>A constant that represents an `MdmHierarchyLevel` as an argument.     |
    | `static int`      | `LEVEL_HIERARCHY`<br>A constant that represents an `MdmLevelHierarchy` as an argument.     |
    | `static int`      | `PRIMARY_DIMENSION`<br>A constant that represents an `MdmPrimaryDimension` as an argument. |
    | `static int`      | `VALUE_HIERARCHY`<br>A constant that represents an `MdmValueHierarchy` as an argument.     |

  <!-- -->

  - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type  | Method and Description                                                                         |
    |--------------------|------------------------------------------------------------------------------------------------|
    | `java.lang.String` | `getArgumentName``()`<br>Gets a name that describes the argument for the function description. |

    - ### Methods inherited from class oracle.olapi.syntax.[FunctionDescriptorArgument](FunctionDescriptorArgument.md)

      [`isOptional`](FunctionDescriptorArgument.md)`, `[`isRepeated`](FunctionDescriptorArgument.md)

    <!-- -->

    - ### Methods inherited from class java.lang.Object

      `clone, equals, finalize, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

<!-- -->

- - ### Field Detail

    - #### DIMENSION_LEVEL

          public static final int DIMENSION_LEVEL

      A constant that represents an `MdmDimensionLevel` as an argument.
      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### PRIMARY_DIMENSION

          public static final int PRIMARY_DIMENSION

      A constant that represents an `MdmPrimaryDimension` as an argument.
      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### HIERARCHY_LEVEL

          public static final int HIERARCHY_LEVEL

      A constant that represents an `MdmHierarchyLevel` as an argument.
      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### LEVEL_HIERARCHY

          public static final int LEVEL_HIERARCHY

      A constant that represents an `MdmLevelHierarchy` as an argument.
      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### VALUE_HIERARCHY

          public static final int VALUE_HIERARCHY

      A constant that represents an `MdmValueHierarchy` as an argument.
      See Also:
      [Constant Field Values](../../../constant-values.md)

  <!-- -->

  - ### Method Detail

    - #### getArgumentName

          public java.lang.String getArgumentName()

      Gets a name that describes the argument for the function description. For example, the name might be `dimension` or `level`.
      Returns:
      A `String` that contains a name for the argument.

Skip navigation links

- [Overview](../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../deprecated-list.md)
- [Index](../../../index-all.md)
- [Help](../../../help-doc.md)

Copyright © 2002, 2018, Oracle. All rights reserved.

- [Prev Class](FunctionDescriptorConditionArgument.md)
- [Next Class](FunctionDescriptorGroupArgument.md)

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
