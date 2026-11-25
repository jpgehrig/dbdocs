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

- **[Prev Class](OXQStackTraceElement.md)**
- **[Next Class](OXQStaticContext.md)**

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

**oracle.xml.xquery**

## **Interface OXQStackTraceVariable**

-

  ------------------------------------------------------------------------

  **
  **

      public interface OXQStackTraceVariable

  **Provides information about a variable binding in addition to what is provided by [`XQStackTraceVariable`](../../../javax/xml/xquery/XQStackTraceVariable.md).**
  **Since:**
  **12.1**

  **See Also:**
  **[`OXQStackTraceElement`](OXQStackTraceElement.md)**

<!-- -->

-
  -

    ### **Field Summary**

    **Fields**

    | Modifier and Type                  | Field and Description                                                                                 |
    |------------------------------------|-------------------------------------------------------------------------------------------------------|
    | `static javax.xml.namespace.QName` | `CONTEXT_ITEM`<br>The name of the variable bound to the context item.                                 |
    | `static javax.xml.namespace.QName` | `CONTEXT_POSITION`<br>The name of the variable bound to the context position.                         |
    | `static javax.xml.namespace.QName` | `CONTEXT_SEQUENCE`<br>The name of the variable bound to the context sequence.                         |
    | `static javax.xml.namespace.QName` | `CONTEXT_SIZE`<br>The name of the variable bound to the context size.                                 |
    | `static javax.xml.namespace.QName` | `RETURN_VAR`<br>The name of the variable bound to the result of a function or main module query body. |
    | `static java.lang.String`          | `XML_NS_OXQ_VARIABLE`<br>The namespace for the names of non-user variables.                           |

  <!-- -->

  -

    ### **Method Summary**

    **All Methods[Instance Methods](javascript:show(2);)[Abstract Methods](javascript:show(4);)**

    | Modifier and Type                                                           | Method and Description                                                                                                                              |
    |-----------------------------------------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------|
    | [`XQSequence`](../../../javax/xml/xquery/XQSequence.md)                     | `getValueSequence``()`<br>Gets the value bound to the variable.                                                                                     |
    | [`XQStackTraceVariable`](../../../javax/xml/xquery/XQStackTraceVariable.md) | `getXQView``()`<br>Returns the [`XQStackTraceVariable`](../../../javax/xml/xquery/XQStackTraceVariable.md) instance corresponding to this instance. |
    | `void`                                                                      | `setValueSequence``(`[`XQSequence`](../../../javax/xml/xquery/XQSequence.md)` value)`<br>Binds the variable to the specified value.                 |

<!-- -->

- - ### Field Detail

    - #### XML_NS_OXQ_VARIABLE

          static final java.lang.String XML_NS_OXQ_VARIABLE

      The namespace for the names of non-user variables. For example, `CONTEXT_POSITION`.

    <!-- -->

    - #### CONTEXT_ITEM

          static final javax.xml.namespace.QName CONTEXT_ITEM

      The name of the variable bound to the context item.
      See Also:
      [http://www.w3.org/TR/xquery/#dt-dynamic-context](http://www.w3.org/TR/xquery/#dt_dynamic_context)

    <!-- -->

    - #### CONTEXT_POSITION

          static final javax.xml.namespace.QName CONTEXT_POSITION

      The name of the variable bound to the context position.
      See Also:
      [http://www.w3.org/TR/xquery/#dt-dynamic-context](http://www.w3.org/TR/xquery/#dt_dynamic_context)

    <!-- -->

    - #### CONTEXT_SIZE

          static final javax.xml.namespace.QName CONTEXT_SIZE

      The name of the variable bound to the context size.
      See Also:
      [http://www.w3.org/TR/xquery/#dt-dynamic-context](http://www.w3.org/TR/xquery/#dt_dynamic_context)

    <!-- -->

    - #### CONTEXT_SEQUENCE

          static final javax.xml.namespace.QName CONTEXT_SEQUENCE

      The name of the variable bound to the context sequence.
      See Also:
      [http://www.w3.org/TR/xquery/#dt-dynamic-context](http://www.w3.org/TR/xquery/#dt_dynamic_context)

    <!-- -->

    - #### RETURN_VAR

          static final javax.xml.namespace.QName RETURN_VAR

      The name of the variable bound to the result of a function or main module query body. This is used to show intermediate results while debugging. Note, intermediate results are only available for certain types of queries.

  <!-- -->

  - ### Method Detail

    - #### getXQView

          XQStackTraceVariable getXQView()

      Returns the [`XQStackTraceVariable`](../../../javax/xml/xquery/XQStackTraceVariable.md) instance corresponding to this instance.
      Returns:
      the variable

    <!-- -->

    - #### getValueSequence

          XQSequence getValueSequence()

      Gets the value bound to the variable.
      Returns:
      the value bound to the variable

    <!-- -->

    - #### setValueSequence

          void setValueSequence(XQSequence value)
                         throws XQException

      Binds the variable to the specified value.
      Parameters:
      `value` - the value that will be bound to the variable. May not be `null`

      Throws:
      [`XQException`](../../../javax/xml/xquery/XQException.md)

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

- **[Prev Class](OXQStackTraceElement.md)**
- **[Next Class](OXQStaticContext.md)**

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
