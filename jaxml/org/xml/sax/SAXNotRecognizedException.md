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

- **[Prev Class](SAXException.md)**
- **[Next Class](SAXNotSupportedException.md)**

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

**org.xml.sax**

## **Class SAXNotRecognizedException**

- **java.lang.Object**

- - **java.lang.Throwable**

  - - **java.lang.Exception**

    - - **[org.xml.sax.SAXException](SAXException.md)**

      - - **org.xml.sax.SAXNotRecognizedException**

<!-- -->

- **All Implemented Interfaces:**
  **java.io.Serializable**

  ------------------------------------------------------------------------

  **
  **

      public class SAXNotRecognizedException
      extends SAXException

  **Exception class for an unrecognized identifier.**
  > ***This module, both source code and documentation, is in the Public Domain, and comes with **NO WARRANTY**.***

  **An XMLReader will throw this exception when it finds an unrecognized feature or property identifier; SAX applications and extensions may use this class for other, similar purposes.**

  **Since:**
  **SAX 2.0**

  **See Also:**
  **[`SAXNotSupportedException`](SAXNotSupportedException.md), [Serialized Form](../../../serialized-form.md)**

<!-- -->

-
  -

    ### **Constructor Summary**

    **Constructors**

    | Constructor and Description                                                                                  |
    |--------------------------------------------------------------------------------------------------------------|
    | `SAXNotRecognizedException``()`<br>Default constructor.                                                      |
    | `SAXNotRecognizedException``(java.lang.String message)`<br>Construct a new exception with the given message. |

  <!-- -->

  -

    ### **Method Summary**

    -

      ### **Methods inherited from class org.xml.sax.[SAXException](SAXException.md)**

      **[`getException`](SAXException.md)`, `[`getMessage`](SAXException.md)`, `[`toString`](SAXException.md)**

    <!-- -->

    -

      ### **Methods inherited from class java.lang.Throwable**

      **`addSuppressed, fillInStackTrace, getCause, getLocalizedMessage, getStackTrace, getSuppressed, initCause, printStackTrace, printStackTrace, printStackTrace, setStackTrace`**

    <!-- -->

    -

      ### **Methods inherited from class java.lang.Object**

      **`equals, getClass, hashCode, notify, notifyAll, wait, wait, wait`**

<!-- -->

-
  -

    ### **Constructor Detail**

    - #### **SAXNotRecognizedException**

          public SAXNotRecognizedException()

      **Default constructor.**

    - #### **SAXNotRecognizedException**

          public SAXNotRecognizedException(java.lang.String message)

      **Construct a new exception with the given message.**
      **Parameters:**
      **`message` - The text message of the exception.**

**Skip navigation links**

- **[Overview](../../../overview-summary.md)**
- **[Package](package-summary.md)**
- **Class**
- **[Tree](package-tree.md)**
- **[Deprecated](../../../deprecated-list.md)**
- **[Index](../../../index-all.md)**
- **[Help](../../../help-doc.md)**

**Oracle® Database XML Java API Reference
Release 19*c*
E96475-03
**

- **[Prev Class](SAXException.md)**
- **[Next Class](SAXNotSupportedException.md)**

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

**org.xml.sax, org.xml.sax.ext, and org.xml.sax.helpers are SAX packages, and are in the public domain. See <http://www.saxproject.org>.**
