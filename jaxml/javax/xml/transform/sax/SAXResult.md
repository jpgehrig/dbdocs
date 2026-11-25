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

- **Prev Class**
- **[Next Class](SAXSource.md)**

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

**javax.xml.transform.sax**

## **Class SAXResult**

- **java.lang.Object**

- - **javax.xml.transform.sax.SAXResult**

<!-- -->

- **All Implemented Interfaces:**
  **[Result](../Result.md)**

  ------------------------------------------------------------------------

  **
  **

      public class SAXResult
      extends java.lang.Object
      implements Result

  **Acts as an holder for a transformation Result.**

<!-- -->

-
  -

    ### **Field Summary**

    **Fields**

    | Modifier and Type         | Field and Description                                                                                                                                                                                  |
    |---------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `static java.lang.String` | `FEATURE`<br>If [`TransformerFactory.getFeature(java.lang.String)`](../TransformerFactory.md) returns true when passed this value as an argument, the Transformer supports Result output of this type. |

    -

      ### **Fields inherited from interface javax.xml.transform.[Result](../Result.md)**

      **[`PI_DISABLE_OUTPUT_ESCAPING`](../Result.md)`, `[`PI_ENABLE_OUTPUT_ESCAPING`](../Result.md)**

  <!-- -->

  -

    ### **Constructor Summary**

    **Constructors**

    | Constructor and Description                                                                                                                      |
    |--------------------------------------------------------------------------------------------------------------------------------------------------|
    | `SAXResult``()`<br>Zero-argument default constructor.                                                                                            |
    | `SAXResult``(`[`ContentHandler`](../../../../org/xml/sax/ContentHandler.md)` handler)`<br>Create a SAXResult that targets a SAX2 ContentHandler. |

  <!-- -->

  -

    ### **Method Summary**

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type                                                 | Method and Description                                                                                                                            |
    |-------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------|
    | [`ContentHandler`](../../../../org/xml/sax/ContentHandler.md)     | `getHandler``()`<br>Get the ContentHandler that is the Result.                                                                                    |
    | [`LexicalHandler`](../../../../org/xml/sax/ext/LexicalHandler.md) | `getLexicalHandler``()`<br>Get a SAX2 LexicalHandler for the output.                                                                              |
    | `java.lang.String`                                                | `getSystemId``()`<br>Get the system identifier that was set with setSystemId.                                                                     |
    | `void`                                                            | `setHandler``(`[`ContentHandler`](../../../../org/xml/sax/ContentHandler.md)` handler)`<br>Set the target to be a SAX2 ContentHandler.            |
    | `void`                                                            | `setLexicalHandler``(`[`LexicalHandler`](../../../../org/xml/sax/ext/LexicalHandler.md)` handler)`<br>Set the SAX2 LexicalHandler for the output. |
    | `void`                                                            | `setSystemId``(java.lang.String systemId)`<br>Method setSystemId Set the systemID that may be used in association with the ContentHandler.        |

    - ### Methods inherited from class java.lang.Object

      `equals, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

<!-- -->

- - ### Field Detail

    - #### FEATURE

          public static final java.lang.String FEATURE

      If [`TransformerFactory.getFeature(java.lang.String)`](../TransformerFactory.md) returns true when passed this value as an argument, the Transformer supports Result output of this type.
      See Also:
      [Constant Field Values](../../../../constant-values.md)

  <!-- -->

  - ### Constructor Detail

    - #### SAXResult

          public SAXResult()

      Zero-argument default constructor.

    <!-- -->

    - #### SAXResult

          public SAXResult(ContentHandler handler)

      Create a SAXResult that targets a SAX2 ContentHandler.
      Parameters:
      `handler` - Must be a non-null ContentHandler reference.

  <!-- -->

  - ### Method Detail

    - #### setHandler

          public void setHandler(ContentHandler handler)

      Set the target to be a SAX2 ContentHandler.
      Parameters:
      `handler` - Must be a non-null ContentHandler reference.

    <!-- -->

    - #### getHandler

          public ContentHandler getHandler()

      Get the ContentHandler that is the Result.
      Returns:
      The ContentHandler that is to be transformation output.

    <!-- -->

    - #### setLexicalHandler

          public void setLexicalHandler(LexicalHandler handler)

      Set the SAX2 LexicalHandler for the output.
      This is needed to handle XML comments and the like. If the lexical handler is not set, an attempt should be made by the transformer to cast the ContentHandler to a LexicalHandler.

      Parameters:
      `handler` - A non-null LexicalHandler for handling lexical parse events.

    <!-- -->

    - #### getLexicalHandler

          public LexicalHandler getLexicalHandler()

      Get a SAX2 LexicalHandler for the output.
      Returns:
      A LexicalHandler, or null.

    <!-- -->

    - #### setSystemId

          public void setSystemId(java.lang.String systemId)

      Method setSystemId Set the systemID that may be used in association with the ContentHandler.
      Specified by:
      [`setSystemId`](../Result.md) in interface [`Result`](../Result.md)

      Parameters:
      `systemId` - The system identifier as a URI string.

    <!-- -->

    - #### getSystemId

          public java.lang.String getSystemId()

      Get the system identifier that was set with setSystemId.
      Specified by:
      [`getSystemId`](../Result.md) in interface [`Result`](../Result.md)

      Returns:
      The system identifier that was set with setSystemId, or null if setSystemId was not called.

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

- **Prev Class**
- **[Next Class](SAXSource.md)**

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
