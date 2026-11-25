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

- **[Prev Class](OXQExpression.md)**
- **[Next Class](OXQFunctionContext.md)**

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

## **Interface OXQFileResolverFactory**

- **All Superinterfaces:**
  **[OXQEntityResolverFactory](OXQEntityResolverFactory.md)**

  ------------------------------------------------------------------------

  **
  **

      public interface OXQFileResolverFactory
      extends OXQEntityResolverFactory

  **The factory interface that creates resolvers for Java's 'file:' URIs. The entity resolver created by this factory responds to all requests which satisfy the following conditions:**
  1.  **The requested entity kind is one of [`OXQEntityKind.SCHEMA`](OXQEntityKind.md), [`OXQEntityKind.MODULE`](OXQEntityKind.md), [`OXQEntityKind.DOCUMENT`](OXQEntityKind.md), [`OXQEntityKind.XML_ENTITY`](OXQEntityKind.md), or [`OXQEntityKind.TEXT`](OXQEntityKind.md)**
  2.  **The entity locator's [`system id`](OXQEntityLocator.md) is a 'file:' URI**
  3.  **The URI does not contain a fragment component (#fragment)**

  **Since:**
  **12.1**

  **See Also:**
  **`File.toURI()`**

<!-- -->

-
  -

    ### **Method Summary**

    **All Methods[Instance Methods](javascript:show(2);)[Abstract Methods](javascript:show(4);)**

    | Modifier and Type              | Method and Description                                                                                                                                              |
    |--------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `javax.activation.FileTypeMap` | `getContentTypeMap``()`<br>Returns the content type map that will be used for media type assignment.                                                                |
    | `void`                         | `setContentTypeMap``(javax.activation.FileTypeMap contentTypeMap)`<br>Sets the content type map that will be used to associate a media type with each resolved URI. |

    - ### Methods inherited from interface oracle.xml.xquery.[OXQEntityResolverFactory](OXQEntityResolverFactory.md)

      [`createResolver`](OXQEntityResolverFactory.md)

<!-- -->

- - ### Method Detail

    - #### setContentTypeMap

          void setContentTypeMap(javax.activation.FileTypeMap contentTypeMap)

      Sets the content type map that will be used to associate a media type with each resolved URI. The default content type map is undefined and therefore no media type is assigned to the resolved content by default.
      Parameters:
      `contentTypeMap` - type map, or `null` to make it undefined

    <!-- -->

    - #### getContentTypeMap

          javax.activation.FileTypeMap getContentTypeMap()

      Returns the content type map that will be used for media type assignment.
      Returns:
      current type map, or `null` if undefined

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

- **[Prev Class](OXQExpression.md)**
- **[Next Class](OXQFunctionContext.md)**

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
