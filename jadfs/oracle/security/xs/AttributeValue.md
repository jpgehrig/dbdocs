Skip navigation links

- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../deprecated-list.md)
- [Index](../../../index-all.md)
- [Help](../../../help-doc.md)

**Oracle® Database Real Application Security Java API Reference
Release 19c**
E96300-01

- [Prev Class](AclId.md)
- [Next Class](ExternalRole.md)

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

oracle.security.xs

## Class AttributeValue

- java.lang.Object

- - oracle.security.xs.AttributeValue

<!-- -->

-

  ------------------------------------------------------------------------



      public class AttributeValue
      extends java.lang.Object

  This class provides a name/value pair that is stored in session namespace. Both name and value are `String`.

<!-- -->

- - ### Constructor Summary

    **Constructors**

    | Constructor and Description                                                                                                                                              |
    |--------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `AttributeValue``(java.lang.String attributeName, java.lang.String attributeValue)`<br>Creates an `AttibuteValue` with the specified attribute name and attribute value. |

  <!-- -->

  - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type  | Method and Description                                           |
    |--------------------|------------------------------------------------------------------|
    | `java.lang.String` | `getName``()`<br>Returns the attribute name.                     |
    | `java.lang.String` | `getValue``()`<br>Returns the attribute value.                   |
    | `void`             | `setValue``(java.lang.String value)`<br>Sets the attribute value |
    | `java.lang.String` | `toString``()`                                                   |

    - ### Methods inherited from class java.lang.Object

      `equals, getClass, hashCode, notify, notifyAll, wait, wait, wait`

<!-- -->

- - ### Constructor Detail

    - #### AttributeValue

          public AttributeValue(java.lang.String attributeName,
                                java.lang.String attributeValue)

      Creates an `AttibuteValue` with the specified attribute name and attribute value.
      Parameters:
      `attributeName` -

      `attributeValue` -

  <!-- -->

  - ### Method Detail

    - #### getName

          public java.lang.String getName()

      Returns the attribute name.
      Returns:
      name of the attribute

    <!-- -->

    - #### getValue

          public java.lang.String getValue()

      Returns the attribute value.
      Returns:
      value of the attribute

    <!-- -->

    - #### setValue

          public void setValue(java.lang.String value)

      Sets the attribute value
      Parameters:
      `value,` - the given value to set

    <!-- -->

    - #### toString

          public java.lang.String toString()

      Overrides:
      `toString` in class `java.lang.Object`

Skip navigation links

- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../deprecated-list.md)
- [Index](../../../index-all.md)
- [Help](../../../help-doc.md)

**Oracle® Database Real Application Security Java API Reference
Release 19c**
E96300-01

- [Prev Class](AclId.md)
- [Next Class](ExternalRole.md)

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

Oracle and Java are registered trademarks of Oracle and/or its affiliates. Other names may be trademarks of their respective owners.
Copyright © 2016, 2019, Oracle and/or its affiliates. All rights reserved.
