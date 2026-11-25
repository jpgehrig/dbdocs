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

- **[Prev Class](OXQEntityLoader.md)**
- **[Next Class](OXQEntityResolver.md)**

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

## **Class OXQEntityLocator**

- **java.lang.Object**

- - **oracle.xml.xquery.OXQEntityLocator**

<!-- -->

-

  ------------------------------------------------------------------------

  **
  **

      public abstract class OXQEntityLocator
      extends java.lang.Object

  **The location of an entity to be [`resolved`](OXQEntityResolver.md). The locator provides location attributes common to most entities. The semantics and availability of the attributes depend on the kind of entity that is being resolved.**
  **Since:**
  **12.1**

  **See Also:**
  **[`OXQEntityResolver`](OXQEntityResolver.md)**

<!-- -->

-
  -

    ### **Method Summary**

    **All Methods[Instance Methods](javascript:show(2);)[Abstract Methods](javascript:show(4);)**

    | Modifier and Type           | Method and Description                                                                                    |
    |-----------------------------|-----------------------------------------------------------------------------------------------------------|
    | `abstract java.lang.Object` | `getExtension``()`<br>Gets extended location information about the entity.                                |
    | `abstract java.lang.String` | `getNamespace``()`<br>Gets the namespace of the entity.                                                   |
    | `abstract java.net.URI`     | `getNamespaceAsURI``()`<br>Retrieves the namespace of the entity as an instance of `java.net.URI`.        |
    | `abstract java.lang.String` | `getPublicId``()`<br>Gets the public identifier of the entity.                                            |
    | `abstract java.net.URI`     | `getPublicIdAsURI``()`<br>Retrieves the public identifier of the entity as an instance of `java.net.URI`. |
    | `abstract java.lang.String` | `getSystemId``()`<br>Gets the system identifier of the entity.                                            |
    | `abstract java.net.URI`     | `getSystemIdAsURI``()`<br>Retrieves the system identifier of the entity as an instance of `java.net.URI`. |

    - ### Methods inherited from class java.lang.Object

      `equals, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

<!-- -->

- - ### Method Detail

    - #### getNamespace

          public abstract java.lang.String getNamespace()

      Gets the namespace of the entity. The following table describes what this will return for the standard entity kinds:
      | Standard entity kind                       | Value                                                                                                            |
      |--------------------------------------------|------------------------------------------------------------------------------------------------------------------|
      | [`MODULE`](OXQEntityKind.md)               | The target namespace of the module if the `location` is not specified in the import statement, otherwise `null`. |
      | [`SCHEMA`](OXQEntityKind.md)               | The target namespace of the schema if the `location` is not specified in the import statement, otherwise `null`. |
      | [`DOCUMENT_TYPE`](OXQEntityKind.md)        | `null`                                                                                                           |
      | [`DOCUMENT`](OXQEntityKind.md)             | `null`                                                                                                           |
      | [`COLLECTION`](OXQEntityKind.md)           | `null`                                                                                                           |
      | [`URI_COLLECTION`](OXQEntityKind.md)       | `null`                                                                                                           |
      | [`XML_ENTITY`](OXQEntityKind.md)           | The namespace of the entity to resolve.                                                                          |
      | [`EXTERNAL_FUNCTION`](OXQEntityKind.md)    | `null`                                                                                                           |
      | [`UPD_PUT`](OXQEntityKind.md)              | `null`                                                                                                           |
      | [`XML_PARSER_FACTORY`](OXQEntityKind.md)   | `null`                                                                                                           |
      | [`DOM_FACTORY`](OXQEntityKind.md)          | `null`                                                                                                           |
      | [`COLLATION`](OXQEntityKind.md)            | `null`                                                                                                           |
      | [`TEXT`](OXQEntityKind.md)                 | `null`                                                                                                           |
      | [`ENVIRONMENT_VARIABLE`](OXQEntityKind.md) | `null`                                                                                                           |

      Returns:
      the namespace of the entity

    <!-- -->

    - #### getNamespaceAsURI

          public abstract java.net.URI getNamespaceAsURI()

      Retrieves the namespace of the entity as an instance of `java.net.URI`.
      Returns:
      namespace URI. `null` if it was not set or couldn't be converted to `java.net.URI`

    <!-- -->

    - #### getSystemId

          public abstract java.lang.String getSystemId()

      Gets the system identifier of the entity. The following table describes what this will return for the standard entity kinds:
      | Standard entity kind                       | Value                                                                                                                                                                                                                                                           |
      |--------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
      | [`MODULE`](OXQEntityKind.md)               | The absolute URI specified as location hint in the XQuery module import or `null` if no location hint was given. Note, the resolver will be called once per location hint if more than one was specified. The returned URI never contains a fragment component. |
      | [`SCHEMA`](OXQEntityKind.md)               | The absolute URI specified as location hint in the XQuery schema import or `null` if no location hint was given. Note, the resolver will be called once per location hint if more than one was specified. The returned URI never contains a fragment component. |
      | [`DOCUMENT_TYPE`](OXQEntityKind.md)        | The absolute URI that identifies the document, or `null` if the URI cannot be computed during static analysis phase.                                                                                                                                            |
      | [`DOCUMENT`](OXQEntityKind.md)             | The absolute URI that identifies the document.                                                                                                                                                                                                                  |
      | [`COLLECTION`](OXQEntityKind.md)           | The absolute URI that identifies the collection.                                                                                                                                                                                                                |
      | [`URI_COLLECTION`](OXQEntityKind.md)       | The absolute URI that identifies the URI collection.                                                                                                                                                                                                            |
      | [`XML_ENTITY`](OXQEntityKind.md)           | The system identifier of the external entity being referenced.                                                                                                                                                                                                  |
      | [`EXTERNAL_FUNCTION`](OXQEntityKind.md)    | `null`                                                                                                                                                                                                                                                          |
      | [`UPD_PUT`](OXQEntityKind.md)              | The absolute URI passed to the `fn:put` function.                                                                                                                                                                                                               |
      | [`XML_PARSER_FACTORY`](OXQEntityKind.md)   | `null`                                                                                                                                                                                                                                                          |
      | [`DOM_FACTORY`](OXQEntityKind.md)          | `null`                                                                                                                                                                                                                                                          |
      | [`COLLATION`](OXQEntityKind.md)            | The absolute URI that identifies the collation.                                                                                                                                                                                                                 |
      | [`TEXT`](OXQEntityKind.md)                 | The absolute URI that identifies the text resource.                                                                                                                                                                                                             |
      | [`ENVIRONMENT_VARIABLE`](OXQEntityKind.md) | The name of the environment variable which value is requested by `fn:environment-variable` or `null` if names of all available environment variables are requested (by `fn:available-environment-variables`)                                                    |

      Returns:
      the system identifier of the entity

    <!-- -->

    - #### getSystemIdAsURI

          public abstract java.net.URI getSystemIdAsURI()

      Retrieves the system identifier of the entity as an instance of `java.net.URI`.
      Returns:
      system identifier URI. `null` if it was not set or couldn't be converted to `java.net.URI`

    <!-- -->

    - #### getPublicId

          public abstract java.lang.String getPublicId()

      Gets the public identifier of the entity. The following table describes what this will return for the standard entity kinds:
      | Standard entity kind                       | Value                                                                                        |
      |--------------------------------------------|----------------------------------------------------------------------------------------------|
      | [`MODULE`](OXQEntityKind.md)               | `null`                                                                                       |
      | [`SCHEMA`](OXQEntityKind.md)               | `null`                                                                                       |
      | [`DOCUMENT_TYPE`](OXQEntityKind.md)        | `null`                                                                                       |
      | [`DOCUMENT`](OXQEntityKind.md)             | `null`                                                                                       |
      | [`COLLECTION`](OXQEntityKind.md)           | `null`                                                                                       |
      | [`URI_COLLECTION`](OXQEntityKind.md)       | `null`                                                                                       |
      | [`XML_ENTITY`](OXQEntityKind.md)           | The public identifier of the external entity being referenced, or null if none was supplied. |
      | [`EXTERNAL_FUNCTION`](OXQEntityKind.md)    | `null`                                                                                       |
      | [`UPD_PUT`](OXQEntityKind.md)              | `null`                                                                                       |
      | [`XML_PARSER_FACTORY`](OXQEntityKind.md)   | `null`                                                                                       |
      | [`DOM_FACTORY`](OXQEntityKind.md)          | `null`                                                                                       |
      | [`COLLATION`](OXQEntityKind.md)            | `null`                                                                                       |
      | [`TEXT`](OXQEntityKind.md)                 | `null`                                                                                       |
      | [`ENVIRONMENT_VARIABLE`](OXQEntityKind.md) | `null`                                                                                       |

      Returns:
      the public identifier of the entity

    <!-- -->

    - #### getPublicIdAsURI

          public abstract java.net.URI getPublicIdAsURI()

      Retrieves the public identifier of the entity as an instance of `java.net.URI`.
      Returns:
      public identifier URI. `null` if it was not set or couldn't be converted to `java.net.URI`

    <!-- -->

    - #### getExtension

          public abstract java.lang.Object getExtension()

      Gets extended location information about the entity. Certain entity kinds may require this additional information in order for a resolver to locate them. The following table describes what this will return for the standard entity kinds:
      | Standard entity kind                       | Value                                           |
      |--------------------------------------------|-------------------------------------------------|
      | [`MODULE`](OXQEntityKind.md)               | `null`                                          |
      | [`SCHEMA`](OXQEntityKind.md)               | `null`                                          |
      | [`DOCUMENT_TYPE`](OXQEntityKind.md)        | `null`                                          |
      | [`DOCUMENT`](OXQEntityKind.md)             | `null`                                          |
      | [`COLLECTION`](OXQEntityKind.md)           | `null`                                          |
      | [`URI_COLLECTION`](OXQEntityKind.md)       | `null`                                          |
      | [`XML_ENTITY`](OXQEntityKind.md)           | `null`                                          |
      | [`EXTERNAL_FUNCTION`](OXQEntityKind.md)    | [`OXQFunctionMetaData`](OXQFunctionMetaData.md) |
      | [`UPD_PUT`](OXQEntityKind.md)              | `null`                                          |
      | [`XML_PARSER_FACTORY`](OXQEntityKind.md)   | `null`                                          |
      | [`DOM_FACTORY`](OXQEntityKind.md)          | `null`                                          |
      | [`COLLATION`](OXQEntityKind.md)            | `null`                                          |
      | [`TEXT`](OXQEntityKind.md)                 | `null`                                          |
      | [`ENVIRONMENT_VARIABLE`](OXQEntityKind.md) | `null`                                          |

      Returns:
      the locator extension

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

- **[Prev Class](OXQEntityLoader.md)**
- **[Next Class](OXQEntityResolver.md)**

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
