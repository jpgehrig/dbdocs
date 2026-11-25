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

- **[Prev Class](XQConnectionEventListener.md)**
- **[Next Class](XQDataFactory.md)**

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

**javax.xml.xquery**

## **Class XQConstants**

- **java.lang.Object**

- - **javax.xml.xquery.XQConstants**

<!-- -->

-

  ------------------------------------------------------------------------

  **
  **

      public final class XQConstants
      extends java.lang.Object

  **`XQConstants` class provides constants that can be used in the XQJ API.**

<!-- -->

-
  -

    ### **Field Summary**

    **Fields**

    | Modifier and Type                  | Field and Description                                                                                                                                                                                                                                                                                                                                    |
    |------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `static int`                       | `BINDING_MODE_DEFERRED`<br>The constant indicating the binding mode deferred, refer to `XQDynamicContext` for more information.                                                                                                                                                                                                                          |
    | `static int`                       | `BINDING_MODE_IMMEDIATE`<br>The constant indicating the binding mode immediate, refer to `XQDynamicContext` for more information.                                                                                                                                                                                                                        |
    | `static int`                       | `BOUNDARY_SPACE_PRESERVE`<br>The constant indicating the the boundary-space policy for expression evaluation is to preserve white spaces                                                                                                                                                                                                                 |
    | `static int`                       | `BOUNDARY_SPACE_STRIP`<br>The constant indicating the the boundary-space policy for expression evaluation is to strip white spaces                                                                                                                                                                                                                       |
    | `static int`                       | `CONSTRUCTION_MODE_PRESERVE`<br>The constant indicating that the type of a constructed element node is `xs:anyType`, and all attribute and element nodes copied during node construction retain their original types.                                                                                                                                    |
    | `static int`                       | `CONSTRUCTION_MODE_STRIP`<br>The constant indicating that the type of a constructed element node is `xs:untyped`; all element nodes copied during node construction receive the type `xs:untyped`, and all attribute nodes copied during node construction receive the type `xs:untypedAtomic`.                                                          |
    | `static javax.xml.namespace.QName` | `CONTEXT_ITEM`<br>Defines the `QName` for the context item.                                                                                                                                                                                                                                                                                              |
    | `static int`                       | `COPY_NAMESPACES_MODE_INHERIT`<br>The constant indicating that the inherit mode should be used in namespace binding assignement when an existing element node is copied by an element constructor, as described in [*3.7.1 Direct Element Constructors, XQuery 1.0: An XML Query Language*](http://www.w3.org/TR/xquery/#id_element_constructor)         |
    | `static int`                       | `COPY_NAMESPACES_MODE_NO_INHERIT`<br>The constant indicating that the no-inherit mode should be used in namespace binding assignement when an existing element node is copied by an element constructor, as described in [*3.7.1 Direct Element Constructors, XQuery 1.0: An XML Query Language*](http://www.w3.org/TR/xquery/#id_element_constructor)   |
    | `static int`                       | `COPY_NAMESPACES_MODE_NO_PRESERVE`<br>The constant indicating that the no-preserve mode should be used in namespace binding assignement when an existing element node is copied by an element constructor, as described in [*3.7.1 Direct Element Constructors, XQuery 1.0: An XML Query Language*](http://www.w3.org/TR/xquery/#id_element_constructor) |
    | `static int`                       | `COPY_NAMESPACES_MODE_PRESERVE`<br>The constant indicating that the preserve mode should be used in namespace binding assignement when an existing element node is copied by an element constructor, as described in [*3.7.1 Direct Element Constructors, XQuery 1.0: An XML Query Language*](http://www.w3.org/TR/xquery/#id_element_constructor)       |
    | `static int`                       | `DEFAULT_ORDER_FOR_EMPTY_SEQUENCES_GREATEST`<br>The constant indicating that ordering of empty sequences and NaN values as keys in an order by clause in a FLWOR expression is "greatest".                                                                                                                                                               |
    | `static int`                       | `DEFAULT_ORDER_FOR_EMPTY_SEQUENCES_LEAST`<br>The constant indicating that ordering of empty sequences and NaN values as keys in an order by clause in a FLWOR expression is "least".                                                                                                                                                                     |
    | `static int`                       | `HOLDTYPE_CLOSE_CURSORS_AT_COMMIT`<br>The constant indicating that the result sequences must be closed when the commit on the connection is called.                                                                                                                                                                                                      |
    | `static int`                       | `HOLDTYPE_HOLD_CURSORS_OVER_COMMIT`<br>The constant indicating that the result sequences must be preserved when the commit on the connection is called.                                                                                                                                                                                                  |
    | `static int`                       | `LANGTYPE_XQUERY`<br>The constant indicating that the expression language used in `XQConnection.prepareExpression` and `XQExpression.execute` is XQuery (any version).                                                                                                                                                                                   |
    | `static int`                       | `LANGTYPE_XQUERYX`<br>The constant indicating that the expression language used in `XQConnection.prepareExpression` and `XQExpression.execute` is XQueryX.                                                                                                                                                                                               |
    | `static int`                       | `ORDERING_MODE_ORDERED`<br>The constant indicating that ordered results are to be returned by certain path expressions, union, intersect, and except expressions, and FLWOR expressions that have no order by clause.                                                                                                                                    |
    | `static int`                       | `ORDERING_MODE_UNORDERED`<br>The constant indicating that unordered results are to be returned by certain path expressions, union, intersect, and except expressions, and FLWOR expressions that have no order by clause.                                                                                                                                |
    | `static int`                       | `SCROLLTYPE_FORWARD_ONLY`<br>The constant indicating that the result sequence can only be scrolled forward.                                                                                                                                                                                                                                              |
    | `static int`                       | `SCROLLTYPE_SCROLLABLE`<br>The constant indicating that the result sequence can be scrolled forward or backward and is insensitive to any updates done on the underlying objects                                                                                                                                                                         |

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

    - #### **HOLDTYPE_CLOSE_CURSORS_AT_COMMIT**

          public static final int HOLDTYPE_CLOSE_CURSORS_AT_COMMIT

      **The constant indicating that the result sequences must be closed when the commit on the connection is called.**
      **See Also:**
      **[Constant Field Values](../../../constant-values.md)**

    - #### **HOLDTYPE_HOLD_CURSORS_OVER_COMMIT**

          public static final int HOLDTYPE_HOLD_CURSORS_OVER_COMMIT

      **The constant indicating that the result sequences must be preserved when the commit on the connection is called.**
      **See Also:**
      **[Constant Field Values](../../../constant-values.md)**

    - #### **SCROLLTYPE_FORWARD_ONLY**

          public static final int SCROLLTYPE_FORWARD_ONLY

      **The constant indicating that the result sequence can only be scrolled forward.**
      **See Also:**
      **[Constant Field Values](../../../constant-values.md)**

    - #### **SCROLLTYPE_SCROLLABLE**

          public static final int SCROLLTYPE_SCROLLABLE

      **The constant indicating that the result sequence can be scrolled forward or backward and is insensitive to any updates done on the underlying objects**
      **See Also:**
      **[Constant Field Values](../../../constant-values.md)**

    - #### **LANGTYPE_XQUERY**

          public static final int LANGTYPE_XQUERY

      **The constant indicating that the expression language used in `XQConnection.prepareExpression` and `XQExpression.execute` is XQuery (any version).**
      **See Also:**
      **[Constant Field Values](../../../constant-values.md)**

    - #### **LANGTYPE_XQUERYX**

          public static final int LANGTYPE_XQUERYX

      **The constant indicating that the expression language used in `XQConnection.prepareExpression` and `XQExpression.execute` is XQueryX.**
      **See Also:**
      **[Constant Field Values](../../../constant-values.md)**

    - #### **BOUNDARY_SPACE_PRESERVE**

          public static final int BOUNDARY_SPACE_PRESERVE

      **The constant indicating the the boundary-space policy for expression evaluation is to preserve white spaces**
      **See Also:**
      **[Constant Field Values](../../../constant-values.md)**

    - #### **BOUNDARY_SPACE_STRIP**

          public static final int BOUNDARY_SPACE_STRIP

      **The constant indicating the the boundary-space policy for expression evaluation is to strip white spaces**
      **See Also:**
      **[Constant Field Values](../../../constant-values.md)**

    - #### **CONSTRUCTION_MODE_PRESERVE**

          public static final int CONSTRUCTION_MODE_PRESERVE

      **The constant indicating that the type of a constructed element node is `xs:anyType`, and all attribute and element nodes copied during node construction retain their original types.**
      **See Also:**
      **[Constant Field Values](../../../constant-values.md)**

    - #### **CONSTRUCTION_MODE_STRIP**

          public static final int CONSTRUCTION_MODE_STRIP

      **The constant indicating that the type of a constructed element node is `xs:untyped`; all element nodes copied during node construction receive the type `xs:untyped`, and all attribute nodes copied during node construction receive the type `xs:untypedAtomic`.**
      **See Also:**
      **[Constant Field Values](../../../constant-values.md)**

    - #### **ORDERING_MODE_ORDERED**

          public static final int ORDERING_MODE_ORDERED

      **The constant indicating that ordered results are to be returned by certain path expressions, union, intersect, and except expressions, and FLWOR expressions that have no order by clause.**
      **See Also:**
      **[Constant Field Values](../../../constant-values.md)**

    - #### **ORDERING_MODE_UNORDERED**

          public static final int ORDERING_MODE_UNORDERED

      **The constant indicating that unordered results are to be returned by certain path expressions, union, intersect, and except expressions, and FLWOR expressions that have no order by clause.**
      **See Also:**
      **[Constant Field Values](../../../constant-values.md)**

    - #### **DEFAULT_ORDER_FOR_EMPTY_SEQUENCES_GREATEST**

          public static final int DEFAULT_ORDER_FOR_EMPTY_SEQUENCES_GREATEST

      **The constant indicating that ordering of empty sequences and NaN values as keys in an order by clause in a FLWOR expression is "greatest". See [*3.8.3 Order By and Return Clauses, XQuery 1.0: An XML Query Language*](http://www.w3.org/TR/xquery/#id_orderby_return) for details.**
      **See Also:**
      **[Constant Field Values](../../../constant-values.md)**

    - #### **DEFAULT_ORDER_FOR_EMPTY_SEQUENCES_LEAST**

          public static final int DEFAULT_ORDER_FOR_EMPTY_SEQUENCES_LEAST

      **The constant indicating that ordering of empty sequences and NaN values as keys in an order by clause in a FLWOR expression is "least". See [*3.8.3 Order By and Return Clauses, XQuery 1.0: An XML Query Language*](http://www.w3.org/TR/xquery/#id_orderby_return) for details.**
      **See Also:**
      **[Constant Field Values](../../../constant-values.md)**

    - #### **COPY_NAMESPACES_MODE_PRESERVE**

          public static final int COPY_NAMESPACES_MODE_PRESERVE

      **The constant indicating that the preserve mode should be used in namespace binding assignement when an existing element node is copied by an element constructor, as described in [*3.7.1 Direct Element Constructors, XQuery 1.0: An XML Query Language*](http://www.w3.org/TR/xquery/#id_element_constructor)**
      **See Also:**
      **[Constant Field Values](../../../constant-values.md)**

    - #### **COPY_NAMESPACES_MODE_NO_PRESERVE**

          public static final int COPY_NAMESPACES_MODE_NO_PRESERVE

      **The constant indicating that the no-preserve mode should be used in namespace binding assignement when an existing element node is copied by an element constructor, as described in [*3.7.1 Direct Element Constructors, XQuery 1.0: An XML Query Language*](http://www.w3.org/TR/xquery/#id_element_constructor)**
      **See Also:**
      **[Constant Field Values](../../../constant-values.md)**

    - #### **COPY_NAMESPACES_MODE_INHERIT**

          public static final int COPY_NAMESPACES_MODE_INHERIT

      **The constant indicating that the inherit mode should be used in namespace binding assignement when an existing element node is copied by an element constructor, as described in [*3.7.1 Direct Element Constructors, XQuery 1.0: An XML Query Language*](http://www.w3.org/TR/xquery/#id_element_constructor)**
      **See Also:**
      **[Constant Field Values](../../../constant-values.md)**

    - #### **COPY_NAMESPACES_MODE_NO_INHERIT**

          public static final int COPY_NAMESPACES_MODE_NO_INHERIT

      **The constant indicating that the no-inherit mode should be used in namespace binding assignement when an existing element node is copied by an element constructor, as described in [*3.7.1 Direct Element Constructors, XQuery 1.0: An XML Query Language*](http://www.w3.org/TR/xquery/#id_element_constructor)**
      **See Also:**
      **[Constant Field Values](../../../constant-values.md)**

    - #### **CONTEXT_ITEM**

          public static final javax.xml.namespace.QName CONTEXT_ITEM

      **Defines the `QName` for the context item. This is used to bind values to the context item via the bind methods of `XQDynamicContext`.**

    - #### **BINDING_MODE_IMMEDIATE**

          public static final int BINDING_MODE_IMMEDIATE

      **The constant indicating the binding mode immediate, refer to `XQDynamicContext` for more information.**
      **See Also:**
      **[Constant Field Values](../../../constant-values.md)**

    - #### **BINDING_MODE_DEFERRED**

          public static final int BINDING_MODE_DEFERRED

      **The constant indicating the binding mode deferred, refer to `XQDynamicContext` for more information.**
      **See Also:**
      **[Constant Field Values](../../../constant-values.md)**

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

- **[Prev Class](XQConnectionEventListener.md)**
- **[Next Class](XQDataFactory.md)**

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
