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

- **[Prev Class](BinXMLProcessor.md)**
- **[Next Class](BinXMLSerializer.md)**

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

**oracle.xml.binxml**

## **Class BinXMLProcessorFactory**

- **java.lang.Object**

- - **oracle.xml.binxml.BinXMLProcessorFactory**

<!-- -->

-

  ------------------------------------------------------------------------

  **
  **

      public class BinXMLProcessorFactory
      extends java.lang.Object

  **Factory class to create a BinXMLProcessor object**

<!-- -->

-
  -

    ### **Method Summary**

    **All Methods[Static Methods](javascript:show(1);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type                                | Method and Description                                                                                                                                         |
    |--------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `static `[`BinXMLProcessor`](BinXMLProcessor.md) | `createProcessor``()`<br>Factory method to create a BinXMLProcessor, metadata info is stored in local cache.                                                   |
    | `static `[`BinXMLProcessor`](BinXMLProcessor.md) | `createProcessor``(`[`BinXMLMetadataProvider`](BinXMLMetadataProvider.md)` rep)`<br>Factory method to create a BinXMLProcessor based on a metadata repository. |

    - ### Methods inherited from class java.lang.Object

      `equals, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

<!-- -->

- - ### Method Detail

    - #### createProcessor

          public static BinXMLProcessor createProcessor(BinXMLMetadataProvider rep)
                                                 throws BinXMLException

      Factory method to create a BinXMLProcessor based on a metadata repository. Users can plug in their own metadata repository that defines the MetadataProvider interface. The DBMetadataProvider implementation to use the Oracle database as a metadata storage repository is available as part of this package. If a non-database repository is needed the user will need to define their own.
      Parameters:
      `rep` - - metdata provider implementation

      Throws:
      [`BinXMLException`](BinXMLException.md)

    <!-- -->

    - #### createProcessor

          public static BinXMLProcessor createProcessor()

      Factory method to create a BinXMLProcessor, metadata info is stored in local cache.

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

- **[Prev Class](BinXMLProcessor.md)**
- **[Next Class](BinXMLSerializer.md)**

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
