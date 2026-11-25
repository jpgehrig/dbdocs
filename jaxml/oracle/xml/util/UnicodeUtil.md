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

- **[Prev Class](RegExprEngine.md)**
- **[Next Class](XMLError.md)**

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

**oracle.xml.util**

## **Class UnicodeUtil**

- **java.lang.Object**

- - **oracle.xml.util.UnicodeUtil**

<!-- -->

-

  ------------------------------------------------------------------------

  **
  **

      public class UnicodeUtil
      extends java.lang.Object

<!-- -->

-
  -

    ### **Constructor Summary**

    **Constructors**

    | Constructor and Description |
    |-----------------------------|
    | `UnicodeUtil``()`           |

  <!-- -->

  -

    ### **Method Summary**

    **All Methods[Static Methods](javascript:show(1);)[Concrete Methods](javascript:show(8);)[Deprecated Methods](javascript:show(32);)**

    | Modifier and Type         | Method and Description                                                                                                       |
    |---------------------------|------------------------------------------------------------------------------------------------------------------------------|
    | `static java.lang.String` | `normalize2RFC2396``(java.lang.String s)`<br>normalize a string to RFC 2396 standards                                        |
    | `static char[]`           | `normalizeUnicode``(char[] ch, int start, int length, int mode)`<br>Deprecated.                                              |
    | `static java.lang.String` | `normalizeUnicode``(java.lang.String s, int mode)`<br>Deprecated.                                                            |
    | `static char[]`           | `normalizeUnicodeByJdkOrGdk``(char[] ch, int start, int length, int mode)`<br>normalize unicode char array based on the mode |
    | `static char[]`           | `normalizeUnicodeNFC``(char[] ch, int start, int length)`<br>Deprecated.                                                     |
    | `static java.lang.String` | `normalizeUnicodeNFC``(java.lang.String s)`<br>Deprecated.                                                                   |

    - ### Methods inherited from class java.lang.Object

      `equals, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

<!-- -->

- - ### Constructor Detail

    - #### UnicodeUtil

          public UnicodeUtil()

  <!-- -->

  - ### Method Detail

    - #### normalizeUnicodeNFC

          public static java.lang.String normalizeUnicodeNFC(java.lang.String s)

      Deprecated. 
      normalize unicode string based on NFC
      Parameters:
      `s` - - input string

      Returns:
      normalized string

    <!-- -->

    - #### normalizeUnicodeNFC

          public static char[] normalizeUnicodeNFC(char[] ch,
                                                   int start,
                                                   int length)

      Deprecated. 
      normalize unicode char array based on NFC
      Parameters:
      `ch` - - input char array

      `start` - - start position

      `length` - - total length

      Returns:
      normalized char array

    <!-- -->

    - #### normalizeUnicode

          public static java.lang.String normalizeUnicode(java.lang.String s,
                                                          int mode)

      Deprecated. 
      normalize unicode string based on the mode
      Parameters:
      `s` - - input string

      `mode` - - normalization mode

      Returns:
      normalized string

    <!-- -->

    - #### normalizeUnicode

          public static char[] normalizeUnicode(char[] ch,
                                                int start,
                                                int length,
                                                int mode)

      Deprecated. 
      normalize unicode char array based on the mode
      Parameters:
      `ch` - - input char array

      `start` - - start position

      `length` - - total length

      `mode` - - normalization mode

      Returns:
      normalized char array

    <!-- -->

    - #### normalizeUnicodeByJdkOrGdk

          public static char[] normalizeUnicodeByJdkOrGdk(char[] ch,
                                                          int start,
                                                          int length,
                                                          int mode)

      normalize unicode char array based on the mode
      Parameters:
      `ch` - - input char array

      `start` - - start position

      `length` - - total length

      `mode` - - normalization mode

      Returns:
      normalized char array

    <!-- -->

    - #### normalize2RFC2396

          public static java.lang.String normalize2RFC2396(java.lang.String s)

      normalize a string to RFC 2396 standards
      Parameters:
      `s` - - input string

      Returns:
      normalized string following RFC 2396 standards

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

- **[Prev Class](RegExprEngine.md)**
- **[Next Class](XMLError.md)**

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
