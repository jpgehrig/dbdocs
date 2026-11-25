Skip navigation links

- [Overview](../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../deprecated-list.md)
- [Index](../../../index-all.md)
- [Help](../../../help-doc.md)

**Oracle® Database XML Java API Reference
Release 19*c*
E96475-03
**

- **[Prev Class](DiffOp.md)**
- **[Next Class](DiffOpReceiver.md)**

<!-- -->

- **[Frames](../../../index.md)**
- **No Frames**

<!-- -->

- **[All Classes](../../../allclasses-noframe.md)**

<!-- -->

- **Summary: **
- **Nested \| **
- **Enum Constants \| **
- **Field \| **
- **Method**

<!-- -->

- **Detail: **
- **Enum Constants \| **
- **Field \| **
- **Method**

**oracle.xml.diff**

## **Enum DiffOp.Name**

- **java.lang.Object**

- - **java.lang.Enum\<DiffOp.Name\>**

  - - **oracle.xml.diff.DiffOp.Name**

<!-- -->

- **All Implemented Interfaces:**
  **java.io.Serializable, java.lang.Comparable\<DiffOp.Name\>**

  <!-- -->

  **Enclosing class:**
  **[DiffOp](DiffOp.md)**

  ------------------------------------------------------------------------

  **
  **

      public static enum DiffOp.Name
      extends java.lang.Enum<DiffOp.Name>

<!-- -->

-
  -

    ### **Enum Constant Summary**

    **Enum Constants**

    | Enum Constant and Description |
    |-------------------------------|
    | `DELETE`                      |
    | `INSERT_BEFORE_NODE`          |
    | `INSERT_BY_APPENDING`         |

  <!-- -->

  -

    ### **Method Summary**

    **All Methods[Static Methods](javascript:show(1);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type      | Method and Description                                                                                       |
    |------------------------|--------------------------------------------------------------------------------------------------------------|
    | `static DiffOp.Name`   | `valueOf``(java.lang.String name)`<br>Returns the enum constant of this type with the specified name.        |
    | `static DiffOp.Name[]` | `values``()`<br>Returns an array containing the constants of this enum type, in the order they are declared. |

    - ### Methods inherited from class java.lang.Enum

      `compareTo, equals, getDeclaringClass, hashCode, name, ordinal, toString, valueOf`

    <!-- -->

    - ### Methods inherited from class java.lang.Object

      `getClass, notify, notifyAll, wait, wait, wait`

<!-- -->

- - ### Enum Constant Detail

    - #### DELETE

          public static final DiffOp.Name DELETE

    <!-- -->

    - #### INSERT_BY_APPENDING

          public static final DiffOp.Name INSERT_BY_APPENDING

    <!-- -->

    - #### INSERT_BEFORE_NODE

          public static final DiffOp.Name INSERT_BEFORE_NODE

  <!-- -->

  - ### Method Detail

    - #### values

          public static DiffOp.Name[] values()

      Returns an array containing the constants of this enum type, in the order they are declared. This method may be used to iterate over the constants as follows:
          for (DiffOp.Name c : DiffOp.Name.values())
              System.out.println(c);

      Returns:
      an array containing the constants of this enum type, in the order they are declared

    <!-- -->

    - #### valueOf

          public static DiffOp.Name valueOf(java.lang.String name)

      Returns the enum constant of this type with the specified name. The string must match *exactly* an identifier used to declare an enum constant in this type. (Extraneous whitespace characters are not permitted.)
      Parameters:
      `name` - the name of the enum constant to be returned.

      Returns:
      the enum constant with the specified name

      Throws:
      `java.lang.IllegalArgumentException` - if this enum type has no constant with the specified name

      `java.lang.NullPointerException` - if the argument is null

Skip navigation links

- [Overview](../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../deprecated-list.md)
- [Index](../../../index-all.md)
- [Help](../../../help-doc.md)

**Oracle® Database XML Java API Reference
Release 19*c*
E96475-03
**

- **[Prev Class](DiffOp.md)**
- **[Next Class](DiffOpReceiver.md)**

<!-- -->

- **[Frames](../../../index.md)**
- **No Frames**

<!-- -->

- **[All Classes](../../../allclasses-noframe.md)**

<!-- -->

- **Summary: **
- **Nested \| **
- **Enum Constants \| **
- **Field \| **
- **Method**

<!-- -->

- **Detail: **
- **Enum Constants \| **
- **Field \| **
- **Method**

**Copyright © 2003, 2019, Oracle and/or its affiliates. All rights reserved.
Use is subject to license terms. Also see the documentation redistribution policy.
ORACLE CONFIDENTIAL
For authorized use only.
Do not distribute to third parties.**
