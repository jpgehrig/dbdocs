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

- **[Prev Class](BinXMLSerializer.md)**
- **[Next Class](BinXMLVocabId.md)**

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

## **Interface BinXMLStream**

-

  ------------------------------------------------------------------------

  **
  **

      public interface BinXMLStream

  **This interface represents the binary XML Stream object. A Decoder or Encoder can be created from the binary XML stream. Otherise its mostly an opaque object.**

<!-- -->

-
  -

    ### **Method Summary**

    **All Methods[Instance Methods](javascript:show(2);)[Abstract Methods](javascript:show(4);)**

    | Modifier and Type                   | Method and Description                                                                                           |
    |-------------------------------------|------------------------------------------------------------------------------------------------------------------|
    | `void`                              | `close``()`<br>Close internal data resources created by the stream.                                              |
    | `void`                              | `closeAll``()`<br>Close all data resources associate with this stream including external plug-in data resources. |
    | [`BinXMLDecoder`](BinXMLDecoder.md) | `getDecoder``()`<br>Factory method to get the BinXMLDecoder object associated with this binary stream.           |
    | [`BinXMLEncoder`](BinXMLEncoder.md) | `getEncoder``()`<br>Factory method to get the BinXMLEncoder object associated with this binary stream.           |

<!-- -->

- - ### Method Detail

    - #### getEncoder

          BinXMLEncoder getEncoder()
                            throws BinXMLException

      Factory method to get the BinXMLEncoder object associated with this binary stream. Only getEncoder() or getDecoder() can be called on a stream but not both.
      Returns:
      BinXMLEncoder object for encoding to this binary stream

      Throws:
      [`BinXMLException`](BinXMLException.md) - Raised for any errors encountered

    <!-- -->

    - #### getDecoder

          BinXMLDecoder getDecoder()
                            throws BinXMLException

      Factory method to get the BinXMLDecoder object associated with this binary stream. Only getEncoder() or getDecoder() can be called on a stream but not both.
      Returns:
      BinXMLDecoder object for decoding from this binary stream

      Throws:
      [`BinXMLException`](BinXMLException.md) - Raised for any errors encountered

    <!-- -->

    - #### close

          void close()

      Close internal data resources created by the stream. This method does not close external resources that are passed in to create this stream.

    <!-- -->

    - #### closeAll

          void closeAll()
                 throws java.io.IOException

      Close all data resources associate with this stream including external plug-in data resources.
      Throws:
      `java.io.IOException` - Raised for any IO errors encountered

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

- **[Prev Class](BinXMLSerializer.md)**
- **[Next Class](BinXMLVocabId.md)**

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
