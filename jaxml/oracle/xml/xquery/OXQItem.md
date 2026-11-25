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

- **[Prev Class](OXQHttpResolverFactory.md)**
- **[Next Class](OXQItemAccessor.md)**

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

## **Interface OXQItem**

- **All Superinterfaces:**
  **[OXQItemAccessor](OXQItemAccessor.md)**

  ------------------------------------------------------------------------

  **
  **

      public interface OXQItem
      extends OXQItemAccessor

  **Extensions to [`javax.xml.xquery.XQItem`](../../../javax/xml/xquery/XQItem.md). This currently only provides extensions indirectly by extending [`OXQItemAccessor`](OXQItemAccessor.md).**
  **Use method [`OXQView.getItem(XQItem)`](OXQView.md) to access the extensions. For example:**

       OXQDataSource ds = new OXQDataSource();
       XQConnection con = ds.getConnection();
       XQItem item = con.createItemFromDocument(...);
       OXQItem oitem = OXQView.getItem(item);
       ...


  **Since:**
  **12.1**

<!-- -->

-
  -

    ### **Method Summary**

    **All Methods[Instance Methods](javascript:show(2);)[Abstract Methods](javascript:show(4);)**

    | Modifier and Type                               | Method and Description                                                                                                  |
    |-------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------|
    | [`XQItem`](../../../javax/xml/xquery/XQItem.md) | `getXQView``()`<br>Returns the [`XQItem`](../../../javax/xml/xquery/XQItem.md) instance corresponding to this instance. |

    - ### Methods inherited from interface oracle.xml.xquery.[OXQItemAccessor](OXQItemAccessor.md)

      [`getAttributeValue`](OXQItemAccessor.md)`, `[`getItemAsInputStream`](OXQItemAccessor.md)`, `[`getItemKind`](OXQItemAccessor.md)`, `[`getNodeName`](OXQItemAccessor.md)`, `[`getTextValue`](OXQItemAccessor.md)

<!-- -->

- - ### Method Detail

    - #### getXQView

          XQItem getXQView()

      Returns the [`XQItem`](../../../javax/xml/xquery/XQItem.md) instance corresponding to this instance.
      Specified by:
      [`getXQView`](OXQItemAccessor.md) in interface [`OXQItemAccessor`](OXQItemAccessor.md)

      Returns:
      the item

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

- **[Prev Class](OXQHttpResolverFactory.md)**
- **[Next Class](OXQItemAccessor.md)**

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
