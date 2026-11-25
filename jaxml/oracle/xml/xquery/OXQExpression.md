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

- **[Prev Class](OXQEntityResolverRequestOptions.md)**
- **[Next Class](OXQFileResolverFactory.md)**

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

## **Interface OXQExpression**

- **All Superinterfaces:**
  **[OXQDynamicContext](OXQDynamicContext.md)**

  ------------------------------------------------------------------------

  **
  **

      public interface OXQExpression
      extends OXQDynamicContext

  **Extensions to [`javax.xml.xquery.XQExpression`](../../../javax/xml/xquery/XQExpression.md).**
  **Use method [`OXQView.getExpression(XQExpression)`](OXQView.md) to access these extensions. For example:**

       OXQDataSource ds = new OXQDataSource();
       XQConnection con = ds.getConnection();
       XQExpression expr = con.createExpression();
       OXQExpression oexpr = OXQView.getExpression(expr);
       ...


  **Since:**
  **12.1**

<!-- -->

-
  -

    ### **Method Summary**

    **All Methods[Instance Methods](javascript:show(2);)[Abstract Methods](javascript:show(4);)**

    | Modifier and Type                                                   | Method and Description                                                                                                              |
    |---------------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------|
    | [`XQResultSequence`](../../../javax/xml/xquery/XQResultSequence.md) | `executeQuery``(`[`OXQEntity`](OXQEntity.md)` query)`<br>Executes a query expression.                                               |
    | [`XQExpression`](../../../javax/xml/xquery/XQExpression.md)         | `getXQView``()`<br>Returns the [`XQExpression`](../../../javax/xml/xquery/XQExpression.md) instance corresponding to this instance. |

    - ### Methods inherited from interface oracle.xml.xquery.[OXQDynamicContext](OXQDynamicContext.md)

      [`bindBigDecimal`](OXQDynamicContext.md)`, `[`bindBigInteger`](OXQDynamicContext.md)`, `[`bindBinary`](OXQDynamicContext.md)`, `[`bindCalendar`](OXQDynamicContext.md)`, `[`bindDocument`](OXQDynamicContext.md)`, `[`bindDuration`](OXQDynamicContext.md)`, `[`bindQName`](OXQDynamicContext.md)`, `[`getConnection`](OXQDynamicContext.md)`, `[`getDebugListener`](OXQDynamicContext.md)`, `[`getDefaultCollection`](OXQDynamicContext.md)`, `[`getDefaultResourceCollection`](OXQDynamicContext.md)`, `[`getPageManager`](OXQDynamicContext.md)`, `[`getUpdateMode`](OXQDynamicContext.md)`, `[`getUserExtension`](OXQDynamicContext.md)`, `[`setDebugListener`](OXQDynamicContext.md)`, `[`setDefaultCollection`](OXQDynamicContext.md)`, `[`setDefaultResourceCollection`](OXQDynamicContext.md)`, `[`setPageManager`](OXQDynamicContext.md)`, `[`setUpdateMode`](OXQDynamicContext.md)`, `[`setUserExtension`](OXQDynamicContext.md)`, `[`unbindAllExternalVariablesAndContextItem`](OXQDynamicContext.md)

<!-- -->

- - ### Method Detail

    - #### getXQView

          XQExpression getXQView()

      Returns the [`XQExpression`](../../../javax/xml/xquery/XQExpression.md) instance corresponding to this instance.
      Specified by:
      [`getXQView`](OXQDynamicContext.md) in interface [`OXQDynamicContext`](OXQDynamicContext.md)

      Returns:
      the expression

    <!-- -->

    - #### executeQuery

          XQResultSequence executeQuery(OXQEntity query)
                                 throws XQException

      Executes a query expression. This implicitly closes any previous result sequences obtained from this expression.
      Parameters:
      `query` - the XQuery expression. The permitted entity `data` is the same as what is permitted for [`MODULE`](OXQEntityKind.md) entities except that collections are not allowed. Cannot be `null`. See the [`OXQEntity`](OXQEntity.md) documentation for a description of what `data` may be for [`MODULE`](OXQEntityKind.md) entities.

      Returns:
      an `XQResultSequence` object containing the result of the query execution

      Throws:
      [`XQException`](../../../javax/xml/xquery/XQException.md) - if (1) there are errors when executing the query, (2) the expression is in a closed state, (3) the execution is cancelled, (4) the query parameter is `null`

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

- **[Prev Class](OXQEntityResolverRequestOptions.md)**
- **[Next Class](OXQFileResolverFactory.md)**

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
