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

- **[Prev Class](TypeConstraintException.md)**
- **[Next Class](Unmarshaller.md)**

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

## **Class UnmarshalException**

- **java.lang.Object**

- - **java.lang.Throwable**

  - - **java.lang.Exception**

    - - **[javax.xml.bind.JAXBException](JAXBException.md)**

      - - **javax.xml.bind.UnmarshalException**

<!-- -->

- **All Implemented Interfaces:**
  **java.io.Serializable**

  ------------------------------------------------------------------------

  **
  **

      public class UnmarshalException
      extends JAXBException

  **This exception indicates that an error has occured while performing an unmarshal operation.**
  **Since:**
  **JAXB1.0**

  **See Also:**
  **[`JAXBException`](JAXBException.md), [`Marshaller`](Marshaller.md), [Serialized Form](../../../serialized-form.md)**

<!-- -->

-
  -

    ### **Constructor Summary**

    **Constructors**

    | Constructor and Description                                                                                                                                                                                     |
    |-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `UnmarshalException``(java.lang.String message)`<br>Construct an UnmarshalException with the specified detail message.                                                                                          |
    | `UnmarshalException``(java.lang.String message, java.lang.String errorCode)`<br>Construct an UnmarshalException with the specified detail message and vendor specific errorCode.                                |
    | `UnmarshalException``(java.lang.String message, java.lang.String errorCode, java.lang.Throwable exception)`<br>Construct an UnmarshalException with the specified detail message and vendor specific errorCode. |
    | `UnmarshalException``(java.lang.String message, java.lang.Throwable exception)`<br>Construct an UnmarshalException with the specified detail message and linkedException.                                       |
    | `UnmarshalException``(java.lang.Throwable exception)`<br>Construct an UnmarshalException with a linkedException.                                                                                                |

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

    - #### **UnmarshalException**

          public UnmarshalException(java.lang.String message)

      **Construct an UnmarshalException with the specified detail message. The errorCode and linkedException will default to null.**
      **Parameters:**
      **`message` - a description of the exception**

    - #### **UnmarshalException**

          public UnmarshalException(java.lang.String message,
                                    java.lang.String errorCode)

      **Construct an UnmarshalException with the specified detail message and vendor specific errorCode. The linkedException will default to null.**
      **Parameters:**
      **`message` - a description of the exception**

      **`errorCode` - a string specifying the vendor specific error code**

    - #### **UnmarshalException**

          public UnmarshalException(java.lang.Throwable exception)

      **Construct an UnmarshalException with a linkedException. The detail message and vendor specific errorCode will default to null.**
      **Parameters:**
      **`exception` - the linked exception**

    - #### **UnmarshalException**

          public UnmarshalException(java.lang.String message,
                                    java.lang.Throwable exception)

      **Construct an UnmarshalException with the specified detail message and linkedException. The errorCode will default to null.**
      **Parameters:**
      **`message` - a description of the exception**

      **`exception` - the linked exception**

    - #### **UnmarshalException**

          public UnmarshalException(java.lang.String message,
                                    java.lang.String errorCode,
                                    java.lang.Throwable exception)

      **Construct an UnmarshalException with the specified detail message and vendor specific errorCode. The linkedException will default to null.**
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

- **[Prev Class](TypeConstraintException.md)**
- **[Next Class](Unmarshaller.md)**

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
