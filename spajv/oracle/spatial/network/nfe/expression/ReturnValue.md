Skip navigation links

- [Overview](../../../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../../../deprecated-list.md)
- [Index](../../../../../index-all.md)
- [Help](../../../../../help-doc.md)

**Oracle® Spatial and Graph Java API Reference
Release 19.1, E94803-01**

- [Prev Class](NFEExpressionAnalyzer.md)
- Next Class

<!-- -->

- [Frames](../../../../../index.md)
- No Frames

<!-- -->

- [All Classes](../../../../../allclasses-noframe.md)

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

oracle.spatial.network.nfe.expression

## Class ReturnValue

- java.lang.Object

- - oracle.spatial.network.nfe.expression.ReturnValue

<!-- -->

-

  ------------------------------------------------------------------------



      public class ReturnValue
      extends java.lang.Object

  Defines the return value of the expression analyzer. The returned value can be a double or a boolean.

<!-- -->

- - ### Field Summary

    **Fields**

    | Modifier and Type         | Field and Description                  |
    |---------------------------|----------------------------------------|
    | `static java.lang.String` | `BOOLEAN_TYPE`<br>Boolean return type. |
    | `static java.lang.String` | `DOUBLE_TYPE`<br>Double return type.   |

  <!-- -->

  - ### Constructor Summary

    **Constructors**

    | Constructor and Description |
    |-----------------------------|
    | `ReturnValue``()`           |

  <!-- -->

  - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type  | Method and Description                                                 |
    |--------------------|------------------------------------------------------------------------|
    | `java.lang.String` | `getReturnType``()`<br>Returns return type.                            |
    | `java.lang.Object` | `getReturnValue``()`<br>Returns return value.                          |
    | `void`             | `setReturnType``(java.lang.String returnType)`<br>Sets return type.    |
    | `void`             | `setReturnValue``(java.lang.Object returnValue)`<br>Sets return value. |
    | `java.lang.String` | `toString``()`                                                         |

    - ### Methods inherited from class java.lang.Object

      `equals, getClass, hashCode, notify, notifyAll, wait, wait, wait`

<!-- -->

- - ### Field Detail

    - #### DOUBLE_TYPE

          public static final java.lang.String DOUBLE_TYPE

      Double return type.
      See Also:
      [Constant Field Values](../../../../../constant-values.md)

    <!-- -->

    - #### BOOLEAN_TYPE

          public static final java.lang.String BOOLEAN_TYPE

      Boolean return type.
      See Also:
      [Constant Field Values](../../../../../constant-values.md)

  <!-- -->

  - ### Constructor Detail

    - #### ReturnValue

          public ReturnValue()

  <!-- -->

  - ### Method Detail

    - #### getReturnType

          public java.lang.String getReturnType()

      Returns return type.
      Returns:
      one of the following constants: ReturnValue.DOUBLE_TYPE, ReturnValue.BOOLEAN_TYPE

    <!-- -->

    - #### setReturnType

          public void setReturnType(java.lang.String returnType)

      Sets return type.
      Parameters:
      `returnType` - return type

    <!-- -->

    - #### getReturnValue

          public java.lang.Object getReturnValue()

      Returns return value.
      Returns:
      return value

    <!-- -->

    - #### setReturnValue

          public void setReturnValue(java.lang.Object returnValue)

      Sets return value.
      Parameters:
      `returnValue` - return value

    <!-- -->

    - #### toString

          public java.lang.String toString()

      Overrides:
      `toString` in class `java.lang.Object`

Skip navigation links

- [Overview](../../../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../../../deprecated-list.md)
- [Index](../../../../../index-all.md)
- [Help](../../../../../help-doc.md)

**Oracle® Spatial and Graph Java API Reference
Release 19.1, E94803-01**

- [Prev Class](NFEExpressionAnalyzer.md)
- Next Class

<!-- -->

- [Frames](../../../../../index.md)
- No Frames

<!-- -->

- [All Classes](../../../../../allclasses-noframe.md)

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

Copyright © 2007, 2019, Oracle and/or its affiliates. All Rights Reserved.
