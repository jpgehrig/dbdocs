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

- **[Prev Class](OXQFunctionContext.md)**
- **[Next Class](OXQFunctionMetaData.md)**

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

## **Class OXQFunctionEvaluator**

- **java.lang.Object**

- - **oracle.xml.xquery.OXQFunctionEvaluator**

<!-- -->

-

  ------------------------------------------------------------------------

  **
  **

      public abstract class OXQFunctionEvaluator
      extends java.lang.Object

  **Extensions of this can be used to implement XQuery external functions. Users may return a class that extends this from an [`entity resolver`](OXQEntityResolver.md).**
  **Since:**
  **12.1**

  **See Also:**
  **[`OXQEntityKind.EXTERNAL_FUNCTION`](OXQEntityKind.md), [`OXQEntity`](OXQEntity.md)**

<!-- -->

-
  -

    ### **Method Summary**

    **All Methods[Instance Methods](javascript:show(2);)[Abstract Methods](javascript:show(4);)**

    | Modifier and Type                                                  | Method and Description                                                                                                                                                                                |
    |--------------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `abstract `[`XQSequence`](../../../javax/xml/xquery/XQSequence.md) | `evaluate``(`[`OXQFunctionContext`](OXQFunctionContext.md)` context, `[`XQSequence`](../../../javax/xml/xquery/XQSequence.md)`[] params)`<br>Called at runtime when the external function is invoked. |

    - ### Methods inherited from class java.lang.Object

      `equals, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

<!-- -->

- - ### Method Detail

    - #### evaluate

          public abstract XQSequence evaluate(OXQFunctionContext context,
                                              XQSequence[] params)
                                       throws XQException

      Called at runtime when the external function is invoked.
      Parameters:
      `context` - provides facilities that may be useful to the external function implementation

      `params` - input parameter bindings for the external function call

      Returns:
      the result of invoking the external function

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

- **[Prev Class](OXQFunctionContext.md)**
- **[Next Class](OXQFunctionMetaData.md)**

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
