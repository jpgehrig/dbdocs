Skip navigation links

- [Overview](../../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Use](class-use/UCPFormatter.md)
- [Tree](package-tree.md)
- [Deprecated](../../../../deprecated-list.md)
- [Index](../../../../index-files/index-1.md)
- [Help](../../../../help-doc.md)

**Oracle® Universal Connection Pool Java API Reference
19c Release**
E96461-04

- Prev Class
- Next Class

<!-- -->

- [Frames](../../../../index.md)
- No Frames

<!-- -->

- [All Classes](../../../../allclasses-noframe.md)

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

oracle.ucp.util.logging

## Class UCPFormatter

- java.lang.Object

- - java.util.logging.Formatter

  - - oracle.ucp.util.logging.UCPFormatter

<!-- -->

-

  ------------------------------------------------------------------------



      public class UCPFormatter
      extends java.util.logging.Formatter

  Universal Connection Pool custom formatter for log messages.
  This can be specified in a log property file passed as Java's `java.util.logging.config.file` command-line option.

<!-- -->

- - ### Constructor Summary

    **Constructors**

    | Constructor and Description |
    |-----------------------------|
    | `UCPFormatter``()`          |

  <!-- -->

  - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type  | Method and Description                      |
    |--------------------|---------------------------------------------|
    | `java.lang.String` | `format``(java.util.logging.LogRecord lr)`  |

    - ### Methods inherited from class java.util.logging.Formatter

      `formatMessage, getHead, getTail`

    <!-- -->

    - ### Methods inherited from class java.lang.Object

      `clone, equals, finalize, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

<!-- -->

- - ### Constructor Detail

    - #### UCPFormatter

          public UCPFormatter()

  <!-- -->

  - ### Method Detail

    - #### format

          public java.lang.String format(java.util.logging.LogRecord lr)

      Specified by:
      `format` in class `java.util.logging.Formatter`

      See Also:
      `Formatter.format(java.util.logging.LogRecord)`

Skip navigation links

- [Overview](../../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Use](class-use/UCPFormatter.md)
- [Tree](package-tree.md)
- [Deprecated](../../../../deprecated-list.md)
- [Index](../../../../index-files/index-1.md)
- [Help](../../../../help-doc.md)

**Oracle® Universal Connection Pool Java API Reference
19c Release**
E96461-04

- Prev Class
- Next Class

<!-- -->

- [Frames](../../../../index.md)
- No Frames

<!-- -->

- [All Classes](../../../../allclasses-noframe.md)

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

Copyright © 2007, 2022, Oracle and/or its affiliates.
