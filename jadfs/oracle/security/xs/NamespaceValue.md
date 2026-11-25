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

- [Prev Class](InvalidXSUserException.md)
- [Next Class](NotAttachedException.md)

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

## Class NamespaceValue

- java.lang.Object

- - oracle.security.xs.NamespaceValue

<!-- -->

-

  ------------------------------------------------------------------------



      public class NamespaceValue
      extends java.lang.Object

  This class represents a namespace and its attributes, which are used in session namespace operations.

<!-- -->

- - ### Constructor Summary

    **Constructors**

    | Constructor and Description                                                                                                                                                             |
    |-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `NamespaceValue``(java.lang.String namespace, java.util.Collection<`[`AttributeValue`](AttributeValue.md)`> attributes)`<br>Creates a namespace with the specified name and attributes. |

  <!-- -->

  - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type                                               | Method and Description                                                                                               |
    |-----------------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------|
    | `java.util.Collection<`[`AttributeValue`](AttributeValue.md)`>` | `getAttributes``()`<br>Retrieves the list of attributes.                                                             |
    | `java.lang.String`                                              | `getNamespace``()`<br>Retrieves the namespace name.                                                                  |
    | `void`                                                          | `setAttributes``(java.util.List<`[`AttributeValue`](AttributeValue.md)`> attributes)`<br>Sets the list of attributes |
    | `void`                                                          | `setNamespace``(java.lang.String namespace)`<br>set namespace name                                                   |
    | `java.lang.String`                                              | `toString``()`                                                                                                       |

    - ### Methods inherited from class java.lang.Object

      `equals, getClass, hashCode, notify, notifyAll, wait, wait, wait`

<!-- -->

- - ### Constructor Detail

    - #### NamespaceValue

          public NamespaceValue(java.lang.String namespace,
                                java.util.Collection<AttributeValue> attributes)

      Creates a namespace with the specified name and attributes.
      Parameters:
      `namespace` -

      `attributes` -

  <!-- -->

  - ### Method Detail

    - #### setNamespace

          public void setNamespace(java.lang.String namespace)

      set namespace name
      Parameters:
      `namespace` -

    <!-- -->

    - #### getNamespace

          public java.lang.String getNamespace()

      Retrieves the namespace name.
      Returns:
      the namespace name

    <!-- -->

    - #### setAttributes

          public void setAttributes(java.util.List<AttributeValue> attributes)

      Sets the list of attributes
      Parameters:
      `attributes` -

    <!-- -->

    - #### getAttributes

          public java.util.Collection<AttributeValue> getAttributes()

      Retrieves the list of attributes.
      Returns:

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

- [Prev Class](InvalidXSUserException.md)
- [Next Class](NotAttachedException.md)

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
