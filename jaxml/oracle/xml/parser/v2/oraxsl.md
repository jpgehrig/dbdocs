Skip navigation links

- [Overview](../../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../../deprecated-list.md)
- [Index](../../../../index-all.md)
- [Help](../../../../help-doc.md)

**Oracle® Database XML Java API Reference
Release 19*c*
E96475-03
**

- **[Prev Class](oraxml.md)**
- **[Next Class](PrintDriver.md)**

<!-- -->

- **[Frames](../../../../index.md)**
- **No Frames**

<!-- -->

- **[All Classes](../../../../allclasses-noframe.md)**

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

**oracle.xml.parser.v2**

## **Class oraxsl**

- **java.lang.Object**

- - **oracle.xml.parser.v2.oraxsl**

<!-- -->

-

  ------------------------------------------------------------------------

  **
  **

      public class oraxsl
      extends java.lang.Object

  **The oraxsl class provides a command-line interface to applying stylesheets on multiple XML documents. It accepts a number of command-line options that dictate how it should behave. The following is its invocation syntax:**
           java oraxsl options* source? stylesheet? result?
                -w                          Show warnings
                -e <error log>              A file to write errors to
                -l <xml file list>          List of files to transform
                -d <directory>              Directory with files to transform
                -x <source extension>       Extensions to exclude
                -i <source extension>       Extensions to include
                -s <stylesheet>             Stylesheet to use
                -r <result extension>       Extension to use for results
                -o <result extension>       Directory to place results
                -p <param list>             List of Params
                -t <# of threads>           Number of threads to use
                -v                                Verbose mode
                -m <version number>         XSLT Version - 1 or 2


<!-- -->

-
  -

    ### **Constructor Summary**

    **Constructors**

    | Constructor and Description |
    |-----------------------------|
    | `oraxsl``()`                |

  <!-- -->

  -

    ### **Method Summary**

    **All Methods[Static Methods](javascript:show(1);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type | Method and Description                                         |
    |-------------------|----------------------------------------------------------------|
    | `static void`     | `main``(java.lang.String[] args)`<br>Invokes the oraxsl driver |

    - ### Methods inherited from class java.lang.Object

      `equals, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

<!-- -->

- - ### Constructor Detail

    - #### oraxsl

          public oraxsl()

  <!-- -->

  - ### Method Detail

    - #### main

          public static void main(java.lang.String[] args)

      Invokes the oraxsl driver
      Parameters:
      `args` - command line arguments

Skip navigation links

- [Overview](../../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../../deprecated-list.md)
- [Index](../../../../index-all.md)
- [Help](../../../../help-doc.md)

**Oracle® Database XML Java API Reference
Release 19*c*
E96475-03
**

- **[Prev Class](oraxml.md)**
- **[Next Class](PrintDriver.md)**

<!-- -->

- **[Frames](../../../../index.md)**
- **No Frames**

<!-- -->

- **[All Classes](../../../../allclasses-noframe.md)**

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
