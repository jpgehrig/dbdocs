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

- **[Prev Class](JAXBContext.md)**
- **[Next Class](MarshalException.md)**

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

## **Class JAXBException**

- **java.lang.Object**

- - **java.lang.Throwable**

  - - **java.lang.Exception**

    - - **javax.xml.bind.JAXBException**

<!-- -->

- **All Implemented Interfaces:**
  **java.io.Serializable**

  <!-- -->

  **Direct Known Subclasses:**
  **[MarshalException](MarshalException.md), [PropertyException](PropertyException.md), [UnmarshalException](UnmarshalException.md), [ValidationException](ValidationException.md)**

  ------------------------------------------------------------------------

  **
  **

      public class JAXBException
      extends java.lang.Exception

  **This is the root exception class for all JAXB exceptions.**
  **Since:**
  **JAXB1.0**

  **See Also:**
  **[`JAXBContext`](JAXBContext.md), [`Marshaller`](Marshaller.md), [`Unmarshaller`](Unmarshaller.md), [Serialized Form](../../../serialized-form.md)**

<!-- -->

-
  -

    ### **Constructor Summary**

    **Constructors**

    | Constructor and Description                                                                                                                                                                          |
    |------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `JAXBException``(java.lang.String message)`<br>Construct a JAXBException with the specified detail message.                                                                                          |
    | `JAXBException``(java.lang.String message, java.lang.String errorCode)`<br>Construct a JAXBException with the specified detail message and vendor specific errorCode.                                |
    | `JAXBException``(java.lang.String message, java.lang.String errorCode, java.lang.Throwable exception)`<br>Construct a JAXBException with the specified detail message and vendor specific errorCode. |
    | `JAXBException``(java.lang.String message, java.lang.Throwable exception)`<br>Construct a JAXBException with the specified detail message and linkedException.                                       |
    | `JAXBException``(java.lang.Throwable exception)`<br>Construct a JAXBException with a linkedException.                                                                                                |

  <!-- -->

  -

    ### **Method Summary**

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type     | Method and Description                                                                                                                                                               |
    |-----------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `java.lang.String`    | `getErrorCode``()`<br>Get the vendor specific error code                                                                                                                             |
    | `java.lang.Throwable` | `getLinkedException``()`<br>Get the linked exception                                                                                                                                 |
    | `void`                | `printStackTrace``()`<br>Prints this JAXBException and its stack trace (including the stack trace of the linkedException if it is non-null) to `System.err`.                         |
    | `void`                | `printStackTrace``(java.io.PrintStream s)`<br>Prints this JAXBException and its stack trace (including the stack trace of the linkedException if it is non-null) to the PrintStream. |
    | `void`                | `setLinkedException``(java.lang.Throwable exception)`<br>Add a linked Exception.                                                                                                     |
    | `java.lang.String`    | `toString``()`<br>Returns a short description of this JAXBException.                                                                                                                 |

    - ### Methods inherited from class java.lang.Throwable

      `addSuppressed, fillInStackTrace, getCause, getLocalizedMessage, getMessage, getStackTrace, getSuppressed, initCause, printStackTrace, setStackTrace`

    <!-- -->

    - ### Methods inherited from class java.lang.Object

      `equals, getClass, hashCode, notify, notifyAll, wait, wait, wait`

<!-- -->

- - ### Constructor Detail

    - #### JAXBException

          public JAXBException(java.lang.String message)

      Construct a JAXBException with the specified detail message. The errorCode and linkedException will default to null.
      Parameters:
      `message` - a description of the exception

    <!-- -->

    - #### JAXBException

          public JAXBException(java.lang.String message,
                               java.lang.String errorCode)

      Construct a JAXBException with the specified detail message and vendor specific errorCode. The linkedException will default to null.
      Parameters:
      `message` - a description of the exception

      `errorCode` - a string specifying the vendor specific error code

    <!-- -->

    - #### JAXBException

          public JAXBException(java.lang.Throwable exception)

      Construct a JAXBException with a linkedException. The detail message and vendor specific errorCode will default to null.
      Parameters:
      `exception` - the linked exception

    <!-- -->

    - #### JAXBException

          public JAXBException(java.lang.String message,
                               java.lang.Throwable exception)

      Construct a JAXBException with the specified detail message and linkedException. The errorCode will default to null.
      Parameters:
      `message` - a description of the exception

      `exception` - the linked exception

    <!-- -->

    - #### JAXBException

          public JAXBException(java.lang.String message,
                               java.lang.String errorCode,
                               java.lang.Throwable exception)

      Construct a JAXBException with the specified detail message and vendor specific errorCode. The linkedException will default to null.
      Parameters:
      `message` - a description of the exception

      `errorCode` - a string specifying the vendor specific error code

      `exception` - the linked exception

  <!-- -->

  - ### Method Detail

    - #### getErrorCode

          public java.lang.String getErrorCode()

      Get the vendor specific error code
      Returns:
      a string specifying the vendor specific error code

    <!-- -->

    - #### getLinkedException

          public java.lang.Throwable getLinkedException()

      Get the linked exception
      Returns:
      the linked Exception, null if none exists

    <!-- -->

    - #### setLinkedException

          public void setLinkedException(java.lang.Throwable exception)

      Add a linked Exception.
      Parameters:
      `exception` - the linked Exception (A null value is permitted and indicates that the linked exception does not exist or is unknown).

    <!-- -->

    - #### toString

          public java.lang.String toString()

      Returns a short description of this JAXBException.
      Overrides:
      `toString` in class `java.lang.Throwable`

    <!-- -->

    - #### printStackTrace

          public void printStackTrace(java.io.PrintStream s)

      Prints this JAXBException and its stack trace (including the stack trace of the linkedException if it is non-null) to the PrintStream.
      Overrides:
      `printStackTrace` in class `java.lang.Throwable`

      Parameters:
      `s` - PrintStream to use for output

    <!-- -->

    - #### printStackTrace

          public void printStackTrace()

      Prints this JAXBException and its stack trace (including the stack trace of the linkedException if it is non-null) to `System.err`.
      Overrides:
      `printStackTrace` in class `java.lang.Throwable`

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

- **[Prev Class](JAXBContext.md)**
- **[Next Class](MarshalException.md)**

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
