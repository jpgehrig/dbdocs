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

- **[Prev Class](OXQOptions.md)**
- **[Next Class](OXQSequence.md)**

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

## **Interface OXQPreparedExpression**

- **All Superinterfaces:**
  **[OXQDynamicContext](OXQDynamicContext.md)**

  ------------------------------------------------------------------------

  **
  **

      public interface OXQPreparedExpression
      extends OXQDynamicContext

  **Extensions to [`javax.xml.xquery.XQPreparedExpression`](../../../javax/xml/xquery/XQPreparedExpression.md).**
  **Use method [`OXQView.getPreparedExpression(XQPreparedExpression)`](OXQView.md) to access these extensions. For example:**

       OXQDataSource ds = new OXQDataSource();
       XQConnection con = ds.getConnection();
       XQPreparedExpression expr = con.prepareExpression(query);
       OXQPreparedExpression oexpr = OXQView.getPreparedExpression(expr);
       ...


  **Since:**
  **12.1**

<!-- -->

-
  -

    ### **Field Summary**

    **Fields**

    | Modifier and Type | Field and Description                                                      |
    |-------------------|----------------------------------------------------------------------------|
    | `static int`      | `CATEGORY_SIMPLE`<br>Indicates that the expression category is simple.     |
    | `static int`      | `CATEGORY_UPDATING`<br>Indicates that the expression category is updating. |

  <!-- -->

  -

    ### **Method Summary**

    **All Methods[Instance Methods](javascript:show(2);)[Abstract Methods](javascript:show(4);)**

    | Modifier and Type                                                           | Method and Description                                                                                                                              |
    |-----------------------------------------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------|
    | `boolean`                                                                   | `createsNewNodes``()`<br>Indicates whether the expression creates new nodes using XQuery node constructors.                                         |
    | `javax.xml.namespace.QName[]`                                               | `getAllUnboundAndUsedExternalVariables``()`<br>Retrieves the names of all unbound external variables that are also used within the query.           |
    | `int`                                                                       | `getExpressionCategory``()`<br>Returns the expression category.                                                                                     |
    | [`XQStaticContext`](../../../javax/xml/xquery/XQStaticContext.md)           | `getExpressionStaticContext``()`<br>Retrieves the static context of the expression's main module.                                                   |
    | [`XQPreparedExpression`](../../../javax/xml/xquery/XQPreparedExpression.md) | `getXQView``()`<br>Returns the [`XQPreparedExpression`](../../../javax/xml/xquery/XQPreparedExpression.md) instance corresponding to this instance. |
    | `boolean`                                                                   | `isContextItemUnbound``()`<br>Indicates whether the context item is unbound.                                                                        |
    | `boolean`                                                                   | `isFunction``()`<br>Returns `true` if the expression is a function.                                                                                 |

    - ### Methods inherited from interface oracle.xml.xquery.[OXQDynamicContext](OXQDynamicContext.md)

      [`bindBigDecimal`](OXQDynamicContext.md)`, `[`bindBigInteger`](OXQDynamicContext.md)`, `[`bindBinary`](OXQDynamicContext.md)`, `[`bindCalendar`](OXQDynamicContext.md)`, `[`bindDocument`](OXQDynamicContext.md)`, `[`bindDuration`](OXQDynamicContext.md)`, `[`bindQName`](OXQDynamicContext.md)`, `[`getConnection`](OXQDynamicContext.md)`, `[`getDebugListener`](OXQDynamicContext.md)`, `[`getDefaultCollection`](OXQDynamicContext.md)`, `[`getDefaultResourceCollection`](OXQDynamicContext.md)`, `[`getPageManager`](OXQDynamicContext.md)`, `[`getUpdateMode`](OXQDynamicContext.md)`, `[`getUserExtension`](OXQDynamicContext.md)`, `[`setDebugListener`](OXQDynamicContext.md)`, `[`setDefaultCollection`](OXQDynamicContext.md)`, `[`setDefaultResourceCollection`](OXQDynamicContext.md)`, `[`setPageManager`](OXQDynamicContext.md)`, `[`setUpdateMode`](OXQDynamicContext.md)`, `[`setUserExtension`](OXQDynamicContext.md)`, `[`unbindAllExternalVariablesAndContextItem`](OXQDynamicContext.md)

<!-- -->

- - ### Field Detail

    - #### CATEGORY_SIMPLE

          static final int CATEGORY_SIMPLE

      Indicates that the expression category is simple.
      See Also:
      `getExpressionCategory()`, [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### CATEGORY_UPDATING

          static final int CATEGORY_UPDATING

      Indicates that the expression category is updating.
      See Also:
      `getExpressionCategory()`, [Constant Field Values](../../../constant-values.md)

  <!-- -->

  - ### Method Detail

    - #### getXQView

          XQPreparedExpression getXQView()

      Returns the [`XQPreparedExpression`](../../../javax/xml/xquery/XQPreparedExpression.md) instance corresponding to this instance.
      Specified by:
      [`getXQView`](OXQDynamicContext.md) in interface [`OXQDynamicContext`](OXQDynamicContext.md)

      Returns:
      the expression

    <!-- -->

    - #### createsNewNodes

          boolean createsNewNodes()
                           throws XQException

      Indicates whether the expression creates new nodes using XQuery node constructors.
      Returns:
      `true` if the expression creates new nodes, `false` otherwise

      Throws:
      [`XQException`](../../../javax/xml/xquery/XQException.md) - if (1) the current expression is closed, (2) the method is not supported for this particular expression

    <!-- -->

    - #### isFunction

          boolean isFunction()
                      throws XQException

      Returns `true` if the expression is a function. In other words, returns `true` if the expression will return the same result given the same input (bindings).
      Returns:
      `true` if the current expression is a function, `false` otherwise

      Throws:
      [`XQException`](../../../javax/xml/xquery/XQException.md) - if the current expression is closed

    <!-- -->

    - #### isContextItemUnbound

          boolean isContextItemUnbound()
                                throws XQException

      Indicates whether the context item is unbound.
      Returns:
      `true` if the context item is unbound, `false` otherwise

      Throws:
      [`XQException`](../../../javax/xml/xquery/XQException.md) - if (1) the current expression is closed, (2) the method is not supported for this particular expression

    <!-- -->

    - #### getExpressionCategory

          int getExpressionCategory()
                             throws XQException

      Returns the expression category.
      Returns:
      The expression category. Must be either `CATEGORY_SIMPLE` or `CATEGORY_UPDATING`

      Throws:
      [`XQException`](../../../javax/xml/xquery/XQException.md) - if (1) the current expression is closed, or (2) the method is not supported for this particular query

    <!-- -->

    - #### getAllUnboundAndUsedExternalVariables

          javax.xml.namespace.QName[] getAllUnboundAndUsedExternalVariables()
                                                                     throws XQException

      Retrieves the names of all unbound external variables that are also used within the query. The standard XQJ [`XQPreparedExpression.getAllUnboundExternalVariables()`](../../../javax/xml/xquery/XQPreparedExpression.md) method returns all unbound external variables, even if they are not used in the query. This method is added to be able to retrieve only the used unbound external variables.
      Returns:
      the names of all the external variables defined in the prolog of a prepared expression that are yet to be bound with a value, and that are used in the query. If there are no such variables an empty array is returned

      Throws:
      [`XQException`](../../../javax/xml/xquery/XQException.md) - if the prepared expression is in a closed state

    <!-- -->

    - #### getExpressionStaticContext

          XQStaticContext getExpressionStaticContext()
                                              throws XQException

      Retrieves the static context of the expression's main module. The context exposes component values as overwritten or augmented by the prolog of the main module. This method is different than [`XQPreparedExpression.getStaticContext()`](../../../javax/xml/xquery/XQPreparedExpression.md) which returns the starting context used to create the expression. Also, unlike the context returned from `getStaticContext()`, the module context may not be used to prepare another expression.
      Returns:
      the static context of the main module

      Throws:
      [`XQException`](../../../javax/xml/xquery/XQException.md) - if the prepared expression is in a closed state

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

- **[Prev Class](OXQOptions.md)**
- **[Next Class](OXQSequence.md)**

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
