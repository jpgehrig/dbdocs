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

- **[Prev Class](JAXBException.md)**
- **[Next Class](Marshaller.md)**

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

**javax.xml.bind**

## **Class MarshalException**

- **java.lang.Object**

- - **java.lang.Throwable**

  - - **java.lang.Exception**

    - - **[javax.xml.bind.JAXBException](JAXBException.md)**

      - - **javax.xml.bind.MarshalException**

<!-- -->

- **All Implemented Interfaces:**
  **java.io.Serializable**

  ------------------------------------------------------------------------

  **
  **

      public class MarshalException
      extends JAXBException

  **This exception indicates that an error has occured while performing a marshal operation that the provider is unable to recover from.**
  **Since:**
  **JAXB1.0**

  **See Also:**
  **[`JAXBException`](JAXBException.md), [`Marshaller`](Marshaller.md), [Serialized Form](../../../serialized-form.md)**

<!-- -->

-
  -

    ### **Constructor Summary**

    **Constructors**

    | Constructor and Description                                                                                                                                                                                |
    |------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `MarshalException``(java.lang.String message)`<br>Construct a MarshalException with the specified detail message.                                                                                          |
    | `MarshalException``(java.lang.String message, java.lang.String errorCode)`<br>Construct a MarshalException with the specified detail message and vendor specific errorCode.                                |
    | `MarshalException``(java.lang.String message, java.lang.String errorCode, java.lang.Throwable exception)`<br>Construct a MarshalException with the specified detail message and vendor specific errorCode. |
    | `MarshalException``(java.lang.String message, java.lang.Throwable exception)`<br>Construct a MarshalException with the specified detail message and linkedException.                                       |
    | `MarshalException``(java.lang.Throwable exception)`<br>Construct a MarshalException with a linkedException.                                                                                                |

  <!-- -->

  -

    ### **Method Summary**

    -

      ### **Methods inherited from class javax.xml.bind.[JAXBException](JAXBException.md)**

      **[`getErrorCode`](JAXBException.md)`, `[`getLinkedException`](JAXBException.md)`, `[`printStackTrace`](JAXBException.md)`, `[`printStackTrace`](JAXBException.md)`, `[`setLinkedException`](JAXBException.md)`, `[`toString`](JAXBException.md)**

    <!-- -->

    -

      ### **Methods inherited from class java.lang.Throwable**

      **`addSuppressed, fillInStackTrace, getCause, getLocalizedMessage, getMessage, getStackTrace, getSuppressed, initCause, printStackTrace, setStackTrace`**

    <!-- -->

    -

      ### **Methods inherited from class java.lang.Object**

      **`equals, getClass, hashCode, notify, notifyAll, wait, wait, wait`**

<!-- -->

-
  -

    ### **Constructor Detail**

    - #### **MarshalException**

          public MarshalException(java.lang.String message)

      **Construct a MarshalException with the specified detail message. The errorCode and linkedException will default to null.**
      **Parameters:**
      **`message` - a description of the exception**

    - #### **MarshalException**

          public MarshalException(java.lang.String message,
                                  java.lang.String errorCode)

      **Construct a MarshalException with the specified detail message and vendor specific errorCode. The linkedException will default to null.**
      **Parameters:**
      **`message` - a description of the exception**

      **`errorCode` - a string specifying the vendor specific error code**

    - #### **MarshalException**

          public MarshalException(java.lang.Throwable exception)

      **Construct a MarshalException with a linkedException. The detail message and vendor specific errorCode will default to null.**
      **Parameters:**
      **`exception` - the linked exception**

    - #### **MarshalException**

          public MarshalException(java.lang.String message,
                                  java.lang.Throwable exception)

      **Construct a MarshalException with the specified detail message and linkedException. The errorCode will default to null.**
      **Parameters:**
      **`message` - a description of the exception**

      **`exception` - the linked exception**

    - #### **MarshalException**

          public MarshalException(java.lang.String message,
                                  java.lang.String errorCode,
                                  java.lang.Throwable exception)

      **Construct a MarshalException with the specified detail message and vendor specific errorCode. The linkedException will default to null.**
      **Parameters:**
      **`message` - a description of the exception**

      **`errorCode` - a string specifying the vendor specific error code**

      **`exception` - the linked exception**

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

- **[Prev Class](JAXBException.md)**
- **[Next Class](Marshaller.md)**

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
