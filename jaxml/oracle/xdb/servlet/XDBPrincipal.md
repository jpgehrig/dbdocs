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

- **[Prev Class](XDBCookie.md)**
- **[Next Class](XDBServletConfig.md)**

<!-- -->

- **[Frames](../../../index.md)**
- **No Frames**

<!-- -->

- **[All Classes](../../../allclasses-noframe.md)**

<!-- -->

- **Summary: **
- **Nested \| **
- **Field \| **
- **Constr \| **
- **Method**

<!-- -->

- **Detail: **
- **Field \| **
- **Constr \| **
- **Method**

**oracle.xdb.servlet**

## **Class XDBPrincipal**

- **java.lang.Object**

- - **oracle.xdb.servlet.XDBPrincipal**

<!-- -->

- **All Implemented Interfaces:**
  **java.security.Principal**

  ------------------------------------------------------------------------

  **
  **

      public class XDBPrincipal
      extends java.lang.Object
      implements java.security.Principal

  **Implementation of java.security.principal for database user.**

<!-- -->

-
  -

    ### **Method Summary**

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type  | Method and Description                                                        |
    |--------------------|-------------------------------------------------------------------------------|
    | `boolean`          | `equals``(java.lang.Object o)`<br>Compares the given object with this object. |
    | `java.lang.String` | `getName``()`<br>Return the user name.                                        |
    | `int`              | `hashCode``()`<br>Return the hash value of the user name.                     |
    | `java.lang.String` | `toString``()`<br>Return the string representation.                           |

    - ### Methods inherited from class java.lang.Object

      `getClass, notify, notifyAll, wait, wait, wait`

    <!-- -->

    - ### Methods inherited from interface java.security.Principal

      `implies`

<!-- -->

- - ### Method Detail

    - #### equals

          public final boolean equals(java.lang.Object o)

      Compares the given object with this object.
      Specified by:
      `equals` in interface `java.security.Principal`

      Overrides:
      `equals` in class `java.lang.Object`

      Parameters:
      `o` - the given object

      Returns:
      true if the given object is an instance of XDBPrincipal and has the same user id as this object.

    <!-- -->

    - #### getName

          public final java.lang.String getName()

      Return the user name.
      Specified by:
      `getName` in interface `java.security.Principal`

      Returns:
      the user name.

    <!-- -->

    - #### toString

          public final java.lang.String toString()

      Return the string representation.
      Specified by:
      `toString` in interface `java.security.Principal`

      Overrides:
      `toString` in class `java.lang.Object`

      Returns:
      the user name.

    <!-- -->

    - #### hashCode

          public final int hashCode()

      Return the hash value of the user name.
      Specified by:
      `hashCode` in interface `java.security.Principal`

      Overrides:
      `hashCode` in class `java.lang.Object`

      Returns:
      the hash value of the user name.

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

- **[Prev Class](XDBCookie.md)**
- **[Next Class](XDBServletConfig.md)**

<!-- -->

- **[Frames](../../../index.md)**
- **No Frames**

<!-- -->

- **[All Classes](../../../allclasses-noframe.md)**

<!-- -->

- **Summary: **
- **Nested \| **
- **Field \| **
- **Constr \| **
- **Method**

<!-- -->

- **Detail: **
- **Field \| **
- **Constr \| **
- **Method**

**Copyright © 2003, 2019, Oracle and/or its affiliates. All rights reserved.
Use is subject to license terms. Also see the documentation redistribution policy.
ORACLE CONFIDENTIAL
For authorized use only.
Do not distribute to third parties.**
