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

- **[Prev Class](OXQEntityResolver.md)**
- **[Next Class](OXQEntityResolverRequestOptions.md)**

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

## **Interface OXQEntityResolverFactory**

- **All Known Subinterfaces:**
  **[OXQCompositeResolverFactory](OXQCompositeResolverFactory.md), [OXQFileResolverFactory](OXQFileResolverFactory.md), [OXQHttpResolverFactory](OXQHttpResolverFactory.md), [OXQJavaResolverFactory](OXQJavaResolverFactory.md)**

  ------------------------------------------------------------------------

  **
  **

      public interface OXQEntityResolverFactory

  **A factory for creating instances of [`OXQEntityResolver`](OXQEntityResolver.md).**
  **Since:**
  **12.1**

<!-- -->

-
  -

    ### **Method Summary**

    **All Methods[Instance Methods](javascript:show(2);)[Abstract Methods](javascript:show(4);)**

    | Modifier and Type                           | Method and Description                              |
    |---------------------------------------------|-----------------------------------------------------|
    | [`OXQEntityResolver`](OXQEntityResolver.md) | `createResolver``()`<br>Creates an entity resolver. |

<!-- -->

- - ### Method Detail

    - #### createResolver

          OXQEntityResolver createResolver()
                                    throws XQException

      Creates an entity resolver.
      Returns:
      the entity resolver

      Throws:
      [`XQException`](../../../javax/xml/xquery/XQException.md) - if creating the entity resolver fails for any reason

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

- **[Prev Class](OXQEntityResolver.md)**
- **[Next Class](OXQEntityResolverRequestOptions.md)**

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
