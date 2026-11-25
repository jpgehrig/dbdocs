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

- **[Prev Class](XSLTransformerBeanInfo.md)**
- **[Next Class](XSLTransformerErrorListener.md)**

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

**oracle.xml.async**

## **Class XSLTransformerErrorEvent**

- **java.lang.Object**

- - **java.util.EventObject**

  - - **oracle.xml.async.XSLTransformerErrorEvent**

<!-- -->

- **All Implemented Interfaces:**
  **java.io.Serializable**

  ------------------------------------------------------------------------

  **
  **

      public class XSLTransformerErrorEvent
      extends java.util.EventObject

  **The error event object that XSLTransformer uses to notify all registered listeners about transformation error events.**
  **See Also:**
  **[Serialized Form](../../../serialized-form.md)**

<!-- -->

-
  -

    ### **Constructor Summary**

    **Constructors**

    | Constructor and Description                                                                                           |
    |-----------------------------------------------------------------------------------------------------------------------|
    | `XSLTransformerErrorEvent``(java.lang.Object p0, java.lang.Exception e)`<br>Constructor for XSLTransformerErrorEvent. |

  <!-- -->

  -

    ### **Method Summary**

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type     | Method and Description                                                                                 |
    |-----------------------|--------------------------------------------------------------------------------------------------------|
    | `java.lang.Exception` | `getException``()`<br>Returns the exception that XSLTransformer encountered object unique id.          |
    | `java.lang.String`    | `getMessage``()`<br>Returns the error message that describes the error that XSLTransformer encountered |

    - ### Methods inherited from class java.util.EventObject

      `getSource, toString`

    <!-- -->

    - ### Methods inherited from class java.lang.Object

      `equals, getClass, hashCode, notify, notifyAll, wait, wait, wait`

<!-- -->

- - ### Constructor Detail

    - #### XSLTransformerErrorEvent

          public XSLTransformerErrorEvent(java.lang.Object p0,
                                          java.lang.Exception e)

      Constructor for XSLTransformerErrorEvent.
      Parameters:
      `p0` - The `Object` that created this event

      `e` - The `Exception` raised.

  <!-- -->

  - ### Method Detail

    - #### getMessage

          public java.lang.String getMessage()

      Returns the error message that describes the error that XSLTransformer encountered
      Returns:
      The error message

    <!-- -->

    - #### getException

          public java.lang.Exception getException()

      Returns the exception that XSLTransformer encountered object unique id. Can be used to
      Returns:
      The transformation exception

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

- **[Prev Class](XSLTransformerBeanInfo.md)**
- **[Next Class](XSLTransformerErrorListener.md)**

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
