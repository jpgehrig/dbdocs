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

- **[Prev Class](OXQEntityKind.md)**
- **[Next Class](OXQEntityLocator.md)**

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

## **Interface OXQEntityLoader**

-

  ------------------------------------------------------------------------

  **
  **

      public interface OXQEntityLoader

  **Manages the lifecycle of schemas and modules in the static context.**
  **Each [`OXQConnection`](OXQConnection.md) instance maintains one or two entity loaders depending on its configuration:**

  - **Connection-scoped entity loader**
  - **Expression-scoped entity loader**

  **Their properties are as follows:**

  | Property                                                      | Connection-scoped                                           | Expression-scoped                                                                                                                       |
  |---------------------------------------------------------------|-------------------------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------|
  | Availability                                                  | Always                                                      | Only when the connection is created from a data source with the flag [`OXQDataSource.IMPORT_SHARING`](OXQDataSource.md) set to `"true"` |
  | Accessing loaded modules/schemas from XQuery                  | Implicitly available, no need to import in the query prolog | Must be explicitly imported by query prolog                                                                                             |
  | Supports unloading schemas/modules with the `unload()` method | No                                                          | Yes                                                                                                                                     |

  **Since:**
  **12.1**

<!-- -->

-
  -

    ### **Method Summary**

    **All Methods[Instance Methods](javascript:show(2);)[Abstract Methods](javascript:show(4);)**

    | Modifier and Type                 | Method and Description                                                                                                                                                                                    |
    |-----------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `java.util.Set<java.lang.String>` | `list``(`[`OXQEntityKind`](OXQEntityKind.md)` entityKind)`<br>Returns the set of target namespaces of all entities of the given kind currently loaded into this context.                                  |
    | `void`                            | `load``(`[`OXQEntityKind`](OXQEntityKind.md)` entityKind, java.lang.String namespaceURI, java.lang.String... locations)`<br>Loads the specified entity (module or schema) into the corresponding context. |
    | `void`                            | `unload``(`[`OXQEntityKind`](OXQEntityKind.md)` entityKind, java.lang.String namespaceURI)`<br>Removes the loaded entity (module/schema) and transitively all other entities that depend on it.           |

<!-- -->

- - ### Method Detail

    - #### load

          void load(OXQEntityKind entityKind,
                    java.lang.String namespaceURI,
                    java.lang.String... locations)
             throws XQException

      Loads the specified entity (module or schema) into the corresponding context. The source of the schema/module is obtained from [`OXQEntityResolver`](OXQEntityResolver.md) associated with the connection and then parsed and loaded into memory.
      Parameters:
      `entityKind` - [`OXQEntityKind.MODULE`](OXQEntityKind.md) or [`OXQEntityKind.SCHEMA`](OXQEntityKind.md)

      `namespaceURI` - target namespace

      `locations` - locations where an entity could be found

      Throws:
      [`XQException`](../../../javax/xml/xquery/XQException.md) - if `namespaceURI` is not absolute, if entity was not found or couldn't be loaded for any reason, or if `entityKind` is not [`OXQEntityKind.MODULE`](OXQEntityKind.md) or [`OXQEntityKind.SCHEMA`](OXQEntityKind.md)

    <!-- -->

    - #### unload

          void unload(OXQEntityKind entityKind,
                      java.lang.String namespaceURI)
               throws XQException

      Removes the loaded entity (module/schema) and transitively all other entities that depend on it. The entity will be reread from the entity resolver if it is imported by a subsequent query.
      Parameters:
      `entityKind` - [`OXQEntityKind.MODULE`](OXQEntityKind.md) or [`OXQEntityKind.SCHEMA`](OXQEntityKind.md)

      `namespaceURI` - namespace URI of the entity

      Throws:
      [`XQException`](../../../javax/xml/xquery/XQException.md) - namespaceURI is not absolute or if `entityKind` is not [`OXQEntityKind.MODULE`](OXQEntityKind.md) or [`OXQEntityKind.SCHEMA`](OXQEntityKind.md)

      `java.lang.UnsupportedOperationException` - if context of this loader doesn't support removal operation for this entity kind

    <!-- -->

    - #### list

          java.util.Set<java.lang.String> list(OXQEntityKind entityKind)
                                        throws XQException

      Returns the set of target namespaces of all entities of the given kind currently loaded into this context.
      Parameters:
      `entityKind` - [`OXQEntityKind.MODULE`](OXQEntityKind.md) or [`OXQEntityKind.SCHEMA`](OXQEntityKind.md)

      Returns:
      set of namespace URIs

      Throws:
      [`XQException`](../../../javax/xml/xquery/XQException.md) - if `entityKind` is not [`OXQEntityKind.MODULE`](OXQEntityKind.md) or [`OXQEntityKind.SCHEMA`](OXQEntityKind.md)

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

- **[Prev Class](OXQEntityKind.md)**
- **[Next Class](OXQEntityLocator.md)**

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
