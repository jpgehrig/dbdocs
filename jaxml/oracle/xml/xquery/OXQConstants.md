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

- **[Prev Class](OXQConnection.md)**
- **[Next Class](OXQDataFactory.md)**

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

## **Class OXQConstants**

- **java.lang.Object**

- - **oracle.xml.xquery.OXQConstants**

<!-- -->

-

  ------------------------------------------------------------------------

  **
  **

      public final class OXQConstants
      extends java.lang.Object

  **Constant values.**
  **Since:**
  **12.1**

  **See Also:**
  **[`XQConstants`](../../../javax/xml/xquery/XQConstants.md)**

<!-- -->

-
  -

    ### **Field Summary**

    **Fields**

    | Modifier and Type                  | Field and Description                                                                                                                                                                                                                                                  |
    |------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `static javax.xml.namespace.QName` | `ANY_NAME`<br>Defines a wildcard name for variable declarations.                                                                                                                                                                                                       |
    | `static int`                       | `BINDING_TYPE_CHECK_MODE_FULL`<br>An `OXQStaticContext` constant indicating that the XQuery processor must check whether an actual type of an external variable binding fully matches its declared type: both prime type and quantifier are checked.                   |
    | `static int`                       | `BINDING_TYPE_CHECK_MODE_PRIME`<br>An `OXQStaticContext` constant indicating that the XQuery processor should check whether an actual type of an external variable binding only partially matches its declared type: prime type is checked, quantifier is not checked. |
    | `static int`                       | `LANGTYPE_XPATH`<br>An `XQStaticContext` constant indicating that the expression language used in `XQConnection.prepareExpression` and `XQExpression.execute` is XPath                                                                                                 |
    | `static int`                       | `PROCESSING_FULL`<br>An `OXQStaticContext` constant indicating that queries should be fully processed for execution.                                                                                                                                                   |
    | `static int`                       | `PROCESSING_STATIC_ANALYSIS_ONLY`<br>An `OXQStaticContext` constant indicating that the compiler should perform static analysis only.                                                                                                                                  |
    | `static int`                       | `UPDATE_MODE_DISABLED`<br>An `OXQDynamicContext` constant indicating that XML may not be updated by the query.                                                                                                                                                         |
    | `static int`                       | `UPDATE_MODE_ENABLED`<br>An `OXQDynamicContext` constant indicating that XML may be updated by the query.                                                                                                                                                              |

  <!-- -->

  -

    ### **Method Summary**

    -

      ### **Methods inherited from class java.lang.Object**

      **`equals, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`**

<!-- -->

-
  -

    ### **Field Detail**

    - #### **BINDING_TYPE_CHECK_MODE_FULL**

          public static final int BINDING_TYPE_CHECK_MODE_FULL

      **An `OXQStaticContext` constant indicating that the XQuery processor must check whether an actual type of an external variable binding fully matches its declared type: both prime type and quantifier are checked.**
      **See Also:**
      **[`OXQStaticContext.getBindingTypeCheckMode()`](OXQStaticContext.md), [Constant Field Values](../../../constant-values.md)**

    - #### **BINDING_TYPE_CHECK_MODE_PRIME**

          public static final int BINDING_TYPE_CHECK_MODE_PRIME

      **An `OXQStaticContext` constant indicating that the XQuery processor should check whether an actual type of an external variable binding only partially matches its declared type: prime type is checked, quantifier is not checked.**
      **See Also:**
      **[`OXQStaticContext.getBindingTypeCheckMode()`](OXQStaticContext.md), [Constant Field Values](../../../constant-values.md)**

    - #### **PROCESSING_FULL**

          public static final int PROCESSING_FULL

      **An `OXQStaticContext` constant indicating that queries should be fully processed for execution.**
      **See Also:**
      **[`OXQStaticContext.getProcessingMode()`](OXQStaticContext.md), [Constant Field Values](../../../constant-values.md)**

    - #### **PROCESSING_STATIC_ANALYSIS_ONLY**

          public static final int PROCESSING_STATIC_ANALYSIS_ONLY

      **An `OXQStaticContext` constant indicating that the compiler should perform static analysis only.**
      **See Also:**
      **[`OXQStaticContext.getProcessingMode()`](OXQStaticContext.md), [Constant Field Values](../../../constant-values.md)**

    - #### **ANY_NAME**

          public static final javax.xml.namespace.QName ANY_NAME

      **Defines a wildcard name for variable declarations. Calling [`OXQStaticContext.declareVariable(QName, XQSequenceType)`](OXQStaticContext.md) with this name instructs XQuery compiler to automatically create external variable for all undeclared variables it finds in the query.**
      **See Also:**
      **[`OXQStaticContext.declareVariable(QName, XQSequenceType)`](OXQStaticContext.md)**

    - #### **LANGTYPE_XPATH**

          public static final int LANGTYPE_XPATH

      **An `XQStaticContext` constant indicating that the expression language used in `XQConnection.prepareExpression` and `XQExpression.execute` is XPath**
      **See Also:**
      **[`XQStaticContext.setQueryLanguageTypeAndVersion(int)`](../../../javax/xml/xquery/XQStaticContext.md), [Constant Field Values](../../../constant-values.md)**

    - #### **UPDATE_MODE_DISABLED**

          public static final int UPDATE_MODE_DISABLED

      **An `OXQDynamicContext` constant indicating that XML may not be updated by the query.**
      **See Also:**
      **[`OXQDynamicContext.setUpdateMode(int)`](OXQDynamicContext.md), [Constant Field Values](../../../constant-values.md)**

    - #### **UPDATE_MODE_ENABLED**

          public static final int UPDATE_MODE_ENABLED

      **An `OXQDynamicContext` constant indicating that XML may be updated by the query.**
      **See Also:**
      **[`OXQDynamicContext.setUpdateMode(int)`](OXQDynamicContext.md), [Constant Field Values](../../../constant-values.md)**

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

- **[Prev Class](OXQConnection.md)**
- **[Next Class](OXQDataFactory.md)**

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
