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

- **[Prev Class](OXQEntityLocator.md)**
- **[Next Class](OXQEntityResolverFactory.md)**

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

## **Class OXQEntityResolver**

- **java.lang.Object**

- - **oracle.xml.xquery.OXQEntityResolver**

<!-- -->

-

  ------------------------------------------------------------------------

  **
  **

      public abstract class OXQEntityResolver
      extends java.lang.Object

  **Used by the XQuery processor to obtain different kinds of resource entities. Users may extend this in order to provide schemas, modules, documents, etc. to the XQuery processor. An `OXQEntityResolver` may be set on the [`connection`](OXQConnection.md) or on the [`static context`](OXQStaticContext.md).**

  **Note: Implementations of `OXQEntityResolver` must be thread-safe if multiple expressions obtained from the same connection will be evaluated concurrently by different threads.**

  In general, the processor will not receive an entity unless an `OXQEntityResovler` is specified. For example, if no entity resolver is specified, a call to the `fn:doc` function will certainly fail no matter what the input URI is. However, there is an internal default entity resolver for certain entity kinds. The following sections describe what will be returned by the default entity resolver:

  #### Default Schema Resolution ([`OXQEntityKind.SCHEMA`](OXQEntityKind.md))

  The following table describes the schemas that will be returned by the default entity resolver given a target namespace and location:

  | Target namespace                       | System ID (location)                   | Schema returned                                                                                     |
  |----------------------------------------|----------------------------------------|-----------------------------------------------------------------------------------------------------|
  | `http://www.w3.org/XML/1998/namespace` | `http://www.w3.org/2001/xml.xsd`       | A schema that describes the XML namespace, in a form suitable for import by other schema documents. |
  | `http://www.w3.org/2001/XMLSchema`     | `http://www.w3.org/2001/XMLSchema.xsd` | The XML Schema schema for XML Schemas                                                               |

  #### Default Parser Factory Resolution ([`OXQEntityKind.XML_PARSER_FACTORY`](OXQEntityKind.md))

  The default entity resolver returns `javax.xml.stream.XMLInputFactory.newInstance()`.

  #### Default DOM Factory Resolution ([`OXQEntityKind.DOM_FACTORY`](OXQEntityKind.md))

  The default entity resolver returns `javax.xml.parsers.DocumentBuilderFactory.newInstance()`.

  #### Default Collation Resolution ([`OXQEntityKind.COLLATION`](OXQEntityKind.md))

  If the system ID is `"http://www.w3.org/2005/xpath-functions/collation/codepoint"` then the code point collator will be returned.

  If the system ID is `"http://xmlns.oracle.com/xdk/xquery/collation"`, a `java.text.Collator` corresponding to the JVM default `Locale` will be returned. Additionally, the following URI query parameters may be used to select a different `Collator`:

  - `language` - the ISO-639 language code. See `java.util.Locale`
  - `country` - the ISO-3166 country code. See `java.util.Locale`
  - `strength` - the strength of the Collator. Must be one of `"PRIMARY"`, `"SECONDARY"`, `"TERTIARY"`, or `"IDENTICAL"`. See `java.text.Collator#setStrength(int)`.
  - `decomposition` - the decomposition mode of the Collator. Must be one of `"NO_DECOMPOSITION"`, `"CANONICAL_DECOMPOSITION"`, `"FULL_DECOMPOSITION"`. See `java.text.Collator#setDecomposition(int)`.

  The parameter binding syntax is of the form `"NAME=VALUE"` where each binding may be separated by either `';'` or `'&'`. For example, `"http://xmlns.oracle.com/xdk/xquery/collation?language=de;strength=SECONDARY"` would return a German collator at `"SECONDARY"` strength.
  If the system ID is `"http://xmlns.oracle.com/xdk/xquery/collation/oracle"`, a `oracle.i18n.text.OraCollator` corresponding to the JVM default `Locale` will be returned. Additionally, the following URI query parameters may be used to select a different `OraCollator`.

  - `language` - the ISO-639 language code. See `java.util.Locale`
  - `country` - the ISO-3166 country code. See `java.util.Locale`
  - `sortRule` - Oracle sort rule name See `oracle.i18n.text.OraCollator#getInstance(String, String)`
  - `charSet` - Oracle database character set See `oracle.i18n.text.OraCollator#getInstance(String, String)`
  - `strength` - the strength of the collator. Must be one of `"PRIMARY"`, `"SECONDARY"`, or `"TERTIARY"`. See `oracle.i18n.text.OraCollator#setStrength(int)`
  - `composition` - the composition mode. Must be one of `"CANONICAL_COMPOSITION"` or `"NO_COMPOSITION"`. See `oracle.i18n.text.OraCollator#setComposition(int)`

  For example, `"http://xmlns.oracle.com/xdk/xquery/collation/oracle?sortRule=XGERMAN;strength=SECONDARY"` would return a German collator `"SECONDARY"` strength.
  Since:
  12.1

  See Also:
  [`OXQStaticContext.setEntityResolver(OXQEntityResolver)`](OXQStaticContext.md), [`OXQConnection.setEntityResolver(OXQEntityResolver)`](OXQConnection.md)

<!-- -->

- - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Abstract Methods](javascript:show(4);)**

    | Modifier and Type                      | Method and Description                                                                                                                                                                                                                                                                             |
    |----------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `abstract `[`OXQEntity`](OXQEntity.md) | `resolveEntity``(`[`OXQEntityKind`](OXQEntityKind.md)` kind, `[`OXQEntityLocator`](OXQEntityLocator.md)` locator, `[`OXQEntityResolverRequestOptions`](OXQEntityResolverRequestOptions.md)` options)`<br>Called by the XQuery processor to obtain an entity (e.g. schema, module, document, etc.). |

    - ### Methods inherited from class java.lang.Object

      `equals, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

<!-- -->

- - ### Method Detail

    - #### resolveEntity

          public abstract OXQEntity resolveEntity(OXQEntityKind kind,
                                                  OXQEntityLocator locator,
                                                  OXQEntityResolverRequestOptions options)
                                           throws XQException,
                                                  java.io.IOException

      Called by the XQuery processor to obtain an entity (e.g. schema, module, document, etc.). The entity `kind` parameter indicates what information will be present in the `locator` and what may be returned in the `OXQEntity`. For more details, see [`OXQEntityLocator`](OXQEntityLocator.md) and [`OXQEntity`](OXQEntity.md).
      Parameters:
      `kind` - The kind of entity to be resolved.

      `locator` - The location of the entity to be resolved.

      `options` - Additional options for resolving the entity.

      Returns:
      the entity or `null` if it could not be resolved

      Throws:
      `java.io.IOException`

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

- **[Prev Class](OXQEntityLocator.md)**
- **[Next Class](OXQEntityResolverFactory.md)**

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
