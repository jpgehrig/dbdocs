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

- [Prev Class](CollectionUtils.md)
- [Next Class](LongHashTable.md)

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

oracle.spatial.network.nfe.util

## Class FileUtils

- java.lang.Object

- - oracle.spatial.network.nfe.util.FileUtils

<!-- -->

-

  ------------------------------------------------------------------------



      public class FileUtils
      extends java.lang.Object

  Files utilities class.

<!-- -->

- - ### Constructor Summary

    **Constructors**

    | Constructor and Description |
    |-----------------------------|
    | `FileUtils``()`             |

  <!-- -->

  - ### Method Summary

    **All Methods[Static Methods](javascript:show(1);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type                               | Method and Description                                                                                                                          |
    |-------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------|
    | `static java.lang.String`                       | `readTxtFile``(java.lang.String filePath)`<br>Reads a text file.                                                                                |
    | `static java.util.Collection<java.lang.String>` | `readTxtFile``(java.lang.String filePath, java.lang.String split)`<br>Reads a text file and returns it in tokens split by the specified string. |

    - ### Methods inherited from class java.lang.Object

      `equals, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

<!-- -->

- - ### Constructor Detail

    - #### FileUtils

          public FileUtils()

  <!-- -->

  - ### Method Detail

    - #### readTxtFile

          public static java.lang.String readTxtFile(java.lang.String filePath)
                                              throws NFEIOException

      Reads a text file.
      Parameters:
      `filePath` - file path to read.

      Returns:
      An String object with the content of the file.

      Throws:
      [`NFEIOException`](../io/NFEIOException.md) - When there is a problem reading the file.

    <!-- -->

    - #### readTxtFile

          public static java.util.Collection<java.lang.String> readTxtFile(java.lang.String filePath,
                                                                           java.lang.String split)
                                                                    throws NFEIOException

      Reads a text file and returns it in tokens split by the specified string. Blank and empty tokens are not included.
      Parameters:
      `filePath` - file path to read.

      `split` - string to split the file.

      Returns:
      An array of String objects containing the tokens.

      Throws:
      [`NFEIOException`](../io/NFEIOException.md) - When there is a problem reading the file.

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

- [Prev Class](CollectionUtils.md)
- [Next Class](LongHashTable.md)

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
