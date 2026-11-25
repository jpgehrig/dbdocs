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

- **[Prev Class](OXQFileResolverFactory.md)**
- **[Next Class](OXQFunctionEvaluator.md)**

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

## **Interface OXQFunctionContext**

-

  ------------------------------------------------------------------------

  **
  **

      public interface OXQFunctionContext

  **The runtime context provided to extensions of [`OXQFunctionEvaluator`](OXQFunctionEvaluator.md). Users should not implement this interface.**
  **Since:**
  **12.1**

  **See Also:**
  **[`OXQFunctionEvaluator`](OXQFunctionEvaluator.md)**

<!-- -->

-
  -

    ### **Method Summary**

    **All Methods[Instance Methods](javascript:show(2);)[Abstract Methods](javascript:show(4);)**

    | Modifier and Type                                                   | Method and Description                                                   |
    |---------------------------------------------------------------------|--------------------------------------------------------------------------|
    | [`XQConnection`](../../../javax/xml/xquery/XQConnection.md)         | `getConnection``()`<br>Gets the connection.                              |
    | [`XQDynamicContext`](../../../javax/xml/xquery/XQDynamicContext.md) | `getDynamicContext``()`<br>Gets a read-only view of the dynamic context. |
    | [`OXQFunctionMetaData`](OXQFunctionMetaData.md)                     | `getMetaData``()`<br>Gets the metadata for the function being evaluated. |
    | [`XQStaticContext`](../../../javax/xml/xquery/XQStaticContext.md)   | `getStaticContext``()`<br>Gets a read-only view of the static context.   |

<!-- -->

- - ### Method Detail

    - #### getMetaData

          OXQFunctionMetaData getMetaData()

      Gets the metadata for the function being evaluated.
      Returns:
      the function metadata

    <!-- -->

    - #### getConnection

          XQConnection getConnection()

      Gets the connection. Note that `javax.xml.xquery.XQConnection` extends `javax.xml.xquery.XQDataFactory` so the connection is useful for constructing the return value of the function. This method is equivalent to `OXQView.getDynamicContext(getDynamicContext()).getConnection()`
      Returns:
      the connection

    <!-- -->

    - #### getDynamicContext

          XQDynamicContext getDynamicContext()

      Gets a read-only view of the dynamic context. Invoking any method on the dynamic context that would modify its state will throw an `java.lang.UnsupportedOperationException`.
      Returns:
      the dynamic context

    <!-- -->

    - #### getStaticContext

          XQStaticContext getStaticContext()

      Gets a read-only view of the static context. Invoking any method on the static context that would modify its state will throw an `java.lang.UnsupportedOperationException`.
      Returns:
      the static context

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

- **[Prev Class](OXQFileResolverFactory.md)**
- **[Next Class](OXQFunctionEvaluator.md)**

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
