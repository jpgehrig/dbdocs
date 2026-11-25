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

- **[Prev Class](PrintConversionEvent.md)**
- **[Next Class](TypeConstraintException.md)**

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

## **Class PropertyException**

- **java.lang.Object**

- - **java.lang.Throwable**

  - - **java.lang.Exception**

    - - **[javax.xml.bind.JAXBException](JAXBException.md)**

      - - **javax.xml.bind.PropertyException**

<!-- -->

- **All Implemented Interfaces:**
  **java.io.Serializable**

  ------------------------------------------------------------------------

  **
  **

      public class PropertyException
      extends JAXBException

  **This exception indicates that an error was encountered while getting or setting a property.**
  **Since:**
  **JAXB1.0**

  **See Also:**
  **[`JAXBContext`](JAXBContext.md), [`Validator`](Validator.md), [`Unmarshaller`](Unmarshaller.md), [Serialized Form](../../../serialized-form.md)**

<!-- -->

-
  -

    ### **Constructor Summary**

    **Constructors**

    | Constructor and Description                                                                                                                      |
    |--------------------------------------------------------------------------------------------------------------------------------------------------|
    | `PropertyException``(java.lang.String message)`<br>Constructor for PropertyException.                                                            |
    | `PropertyException``(java.lang.String name, java.lang.Object value)`<br>Constructor for PropertyException.                                       |
    | `PropertyException``(java.lang.String message, java.lang.String errorCode)`<br>Constructor for PropertyException.                                |
    | `PropertyException``(java.lang.String message, java.lang.String errorCode, java.lang.Throwable exception)`<br>Constructor for PropertyException. |
    | `PropertyException``(java.lang.String message, java.lang.Throwable exception)`<br>Constructor for PropertyException.                             |
    | `PropertyException``(java.lang.Throwable exception)`<br>Constructor for PropertyException.                                                       |

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

    - #### **PropertyException**

          public PropertyException(java.lang.String message)

      **Constructor for PropertyException.**
      **Parameters:**
      **`message` -**

    - #### **PropertyException**

          public PropertyException(java.lang.String message,
                                   java.lang.String errorCode)

      **Constructor for PropertyException.**
      **Parameters:**
      **`message` -**

      **`errorCode` -**

    - #### **PropertyException**

          public PropertyException(java.lang.Throwable exception)

      **Constructor for PropertyException.**
      **Parameters:**
      **`exception` -**

    - #### **PropertyException**

          public PropertyException(java.lang.String message,
                                   java.lang.Throwable exception)

      **Constructor for PropertyException.**
      **Parameters:**
      **`message` -**

      **`exception` -**

    - #### **PropertyException**

          public PropertyException(java.lang.String message,
                                   java.lang.String errorCode,
                                   java.lang.Throwable exception)

      **Constructor for PropertyException.**
      **Parameters:**
      **`message` -**

      **`errorCode` -**

      **`exception` -**

    - #### **PropertyException**

          public PropertyException(java.lang.String name,
                                   java.lang.Object value)

      **Constructor for PropertyException.**
      **Parameters:**
      **`name` - the name of the property related to this exception**

      **`value` - the value of the property related to this exception**

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

- **[Prev Class](PrintConversionEvent.md)**
- **[Next Class](TypeConstraintException.md)**

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
