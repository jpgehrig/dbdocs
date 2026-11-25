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

- [Prev Class](SessionNamespace.md)
- [Next Class](SessionNamespaceAttribute.md)

<!-- -->

- [Frames](../../../index.md)
- No Frames

<!-- -->

- [All Classes](../../../allclasses-noframe.md)

<!-- -->

- Summary: 
- Nested \| 
- Enum Constants \| 
- Field \| 
- Method

<!-- -->

- Detail: 
- Enum Constants \| 
- Field \| 
- Method

oracle.security.xs

## Enum SessionNamespace.ATTR_EVENT_TYPE

- java.lang.Object

- - java.lang.Enum\<SessionNamespace.ATTR_EVENT_TYPE\>

  - - oracle.security.xs.SessionNamespace.ATTR_EVENT_TYPE

<!-- -->

- All Implemented Interfaces:
  java.io.Serializable, java.lang.Comparable\<SessionNamespace.ATTR_EVENT_TYPE\>

  <!-- -->

  Enclosing interface:
  [SessionNamespace](SessionNamespace.md)

  ------------------------------------------------------------------------



      public static enum SessionNamespace.ATTR_EVENT_TYPE
      extends java.lang.Enum<SessionNamespace.ATTR_EVENT_TYPE>

  The list of possible events an attribute can have.

<!-- -->

- - ### Enum Constant Summary

    **Enum Constants**

    | Enum Constant and Description |
    |-------------------------------|
    | `FIRST_READ`                  |
    | `MODIFY`                      |

  <!-- -->

  - ### Method Summary

    **All Methods[Static Methods](javascript:show(1);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type                           | Method and Description                                                                                       |
    |---------------------------------------------|--------------------------------------------------------------------------------------------------------------|
    | `static SessionNamespace.ATTR_EVENT_TYPE`   | `valueOf``(java.lang.String name)`<br>Returns the enum constant of this type with the specified name.        |
    | `static SessionNamespace.ATTR_EVENT_TYPE[]` | `values``()`<br>Returns an array containing the constants of this enum type, in the order they are declared. |

    - ### Methods inherited from class java.lang.Enum

      `compareTo, equals, getDeclaringClass, hashCode, name, ordinal, toString, valueOf`

    <!-- -->

    - ### Methods inherited from class java.lang.Object

      `getClass, notify, notifyAll, wait, wait, wait`

<!-- -->

- - ### Enum Constant Detail

    - #### FIRST_READ

          public static final SessionNamespace.ATTR_EVENT_TYPE FIRST_READ

    <!-- -->

    - #### MODIFY

          public static final SessionNamespace.ATTR_EVENT_TYPE MODIFY

  <!-- -->

  - ### Method Detail

    - #### values

          public static SessionNamespace.ATTR_EVENT_TYPE[] values()

      Returns an array containing the constants of this enum type, in the order they are declared. This method may be used to iterate over the constants as follows:
          for (SessionNamespace.ATTR_EVENT_TYPE c : SessionNamespace.ATTR_EVENT_TYPE.values())
              System.out.println(c);

      Returns:
      an array containing the constants of this enum type, in the order they are declared

    <!-- -->

    - #### valueOf

          public static SessionNamespace.ATTR_EVENT_TYPE valueOf(java.lang.String name)

      Returns the enum constant of this type with the specified name. The string must match *exactly* an identifier used to declare an enum constant in this type. (Extraneous whitespace characters are not permitted.)
      Parameters:
      `name` - the name of the enum constant to be returned.

      Returns:
      the enum constant with the specified name

      Throws:
      `java.lang.IllegalArgumentException` - if this enum type has no constant with the specified name

      `java.lang.NullPointerException` - if the argument is null

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

- [Prev Class](SessionNamespace.md)
- [Next Class](SessionNamespaceAttribute.md)

<!-- -->

- [Frames](../../../index.md)
- No Frames

<!-- -->

- [All Classes](../../../allclasses-noframe.md)

<!-- -->

- Summary: 
- Nested \| 
- Enum Constants \| 
- Field \| 
- Method

<!-- -->

- Detail: 
- Enum Constants \| 
- Field \| 
- Method

Oracle and Java are registered trademarks of Oracle and/or its affiliates. Other names may be trademarks of their respective owners.
Copyright © 2016, 2019, Oracle and/or its affiliates. All rights reserved.
