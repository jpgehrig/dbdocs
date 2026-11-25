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

- **[Prev Class](OXQFunctionMetaData.md)**
- **[Next Class](OXQItem.md)**

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

## **Interface OXQHttpResolverFactory**

- **All Superinterfaces:**
  **[OXQEntityResolverFactory](OXQEntityResolverFactory.md)**

  ------------------------------------------------------------------------

  **
  **

      public interface OXQHttpResolverFactory
      extends OXQEntityResolverFactory

  **The factory interface for creating entity resolvers for the HTTP protocol. The entity resolver created by this factory responds to all requests which satisfy the following conditions:**
  1.  **The requested entity kind is one of [`OXQEntityKind.SCHEMA`](OXQEntityKind.md), [`OXQEntityKind.MODULE`](OXQEntityKind.md), [`OXQEntityKind.DOCUMENT`](OXQEntityKind.md), [`OXQEntityKind.XML_ENTITY`](OXQEntityKind.md), or [`OXQEntityKind.TEXT`](OXQEntityKind.md)**
  2.  **The entity locator's [`system id`](OXQEntityLocator.md) is a 'http:' or 'https:' URI**
  3.  **The URI does not contain a fragment component (#fragment)**

  **Since:**
  **12.1**

<!-- -->

-
  -

    ### **Method Summary**

    **All Methods[Instance Methods](javascript:show(2);)[Abstract Methods](javascript:show(4);)**

    | Modifier and Type | Method and Description                                                                                                                                               |
    |-------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `void`            | `addExcludedURI``(java.net.URI uri)`<br>Specifies a URI that must be ignored by the entity resolver.                                                                 |
    | `boolean`         | `getContentTypeFromResponseHeader``()`<br>Retrieves whether the media type should be assigned based on the value of the HTTP 'Content-Type' response header.         |
    | `java.net.URI[]`  | `getExcludedURIs``()`<br>Retrieves the URIs that will be ignored by the entity resolver.                                                                             |
    | `boolean`         | `removeExcludedURI``(java.net.URI uri)`<br>Removes the given URI from the exclusion list.                                                                            |
    | `void`            | `setContentTypeFromResponseHeader``(boolean value)`<br>Sets whether the media type should be assigned based on the value of the HTTP 'Content-Type' response header. |

    - ### Methods inherited from interface oracle.xml.xquery.[OXQEntityResolverFactory](OXQEntityResolverFactory.md)

      [`createResolver`](OXQEntityResolverFactory.md)

<!-- -->

- - ### Method Detail

    - #### addExcludedURI

          void addExcludedURI(java.net.URI uri)

      Specifies a URI that must be ignored by the entity resolver.
      Parameters:
      `uri` - ignored URI, cannot be `null`

      Throws:
      `java.lang.NullPointerException` - if given URI is null

      See Also:
      `for URIs excluded by default`

    <!-- -->

    - #### removeExcludedURI

          boolean removeExcludedURI(java.net.URI uri)

      Removes the given URI from the exclusion list.
      Parameters:
      `uri` - URI, cannot be `null`

      Returns:
      `true` if given URI existed in the exclusion list, `false` otherwise

      Throws:
      `java.lang.NullPointerException` - if given URI is null

      See Also:
      `for URIs excluded by default`

    <!-- -->

    - #### getExcludedURIs

          java.net.URI[] getExcludedURIs()

      Retrieves the URIs that will be ignored by the entity resolver.
      By default some well-known URIs are automatically added to the exclusion list. The documents corresponding to those URIs are stored internally by the XQuery processor and resolved by the default entity resolver.

      The following URIs are excluded by default:

      1.  http://www.w3.org/2001/xml.xsd
      2.  http://www.w3.org/2001/XMLSchema.xsd

      Returns:
      array of URIs

    <!-- -->

    - #### setContentTypeFromResponseHeader

          void setContentTypeFromResponseHeader(boolean value)

      Sets whether the media type should be assigned based on the value of the HTTP 'Content-Type' response header. By default no media type is assigned.
      Parameters:
      `value` - `true` to assign media type from HTTP header, `false` otherwise.

    <!-- -->

    - #### getContentTypeFromResponseHeader

          boolean getContentTypeFromResponseHeader()

      Retrieves whether the media type should be assigned based on the value of the HTTP 'Content-Type' response header.
      Returns:
      `true` if media type is assigned by HTTP response header, `false` otherwise.

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

- **[Prev Class](OXQFunctionMetaData.md)**
- **[Next Class](OXQItem.md)**

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
