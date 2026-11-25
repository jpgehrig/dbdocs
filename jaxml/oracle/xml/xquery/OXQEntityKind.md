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

- **[Prev Class](OXQEntity.md)**
- **[Next Class](OXQEntityLoader.md)**

<!-- -->

- **[Frames](../../../index.md)**
- **No Frames**

<!-- -->

- **[All Classes](../../../allclasses-noframe.md)**

<!-- -->

- **Summary: **
- **Nested \| **
- **Enum Constants \| **
- **Field \| **
- **Method**

<!-- -->

- **Detail: **
- **Enum Constants \| **
- **Field \| **
- **Method**

**oracle.xml.xquery**

## **Enum OXQEntityKind**

- **java.lang.Object**

- - **java.lang.Enum\<OXQEntityKind\>**

  - - **oracle.xml.xquery.OXQEntityKind**

<!-- -->

- **All Implemented Interfaces:**
  **java.io.Serializable, java.lang.Comparable\<OXQEntityKind\>**

  ------------------------------------------------------------------------

  **
  **

      public enum OXQEntityKind
      extends java.lang.Enum<OXQEntityKind>

  **The kind of entity to be [`resolved`](OXQEntityResolver.md). The enumeration provides entity kinds for the common types of entities: modules, schemas, collections, documents, xml entities, and external functions. A user may control how the XQuery processor obtains these resources by implementing a custom `OXQEntityResolver`.**
  **Since:**
  **12.1**

  **See Also:**
  **[`OXQEntityResolver`](OXQEntityResolver.md)**

<!-- -->

-
  -

    ### **Enum Constant Summary**

    **Enum Constants**

    | Enum Constant and Description                                                                                                                                             |
    |---------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `COLLATION`<br>The kind used to obtain a collation.                                                                                                                       |
    | `COLLECTION`<br>The kind used to obtain the documents that comprise a collection (used when there is a call to `fn:collection`).                                          |
    | `DOCUMENT`<br>The kind used to obtain a document for the `fn:doc` or `fn:collection` function.                                                                            |
    | `DOCUMENT_TYPE`<br>The kind used to obtain a document type for the `fn:doc` function.                                                                                     |
    | `DOM_FACTORY`<br>The kind used to obtain an implementation of the DOM factory: `javax.xml.parsers.DocumentBuilderFactory`                                                 |
    | `ENVIRONMENT_VARIABLE`<br>The kind used to obtain environment variable names and values for `fn:available-environment-variables` and `fn:environment-variable` functions. |
    | `EXTERNAL_FUNCTION`<br>The kind used to obtain an external function binding.                                                                                              |
    | `MODULE`<br>The kind used to resolve an XQuery module import.                                                                                                             |
    | `SCHEMA`<br>The kind used to resolve an XML Schema import.                                                                                                                |
    | `TEXT`<br>The kind used to obtain unparsed text for the `fn:unparsed-text` function.                                                                                      |
    | `UPD_PUT`<br>The kind used to obtain an implementation for the `fn:put` function.                                                                                         |
    | `URI_COLLECTION`<br>The kind used to obtain the URIs that will be returned by a call to `fn:uri-collection`.                                                              |
    | `XML_ENTITY`<br>The kind used when an internal XML parser needs to resolve an XML resource.                                                                               |
    | `XML_PARSER_FACTORY`<br>The kind used to obtain an implementation of the StAX parser factory: `XMLInputFactory`                                                           |

  <!-- -->

  -

    ### **Method Summary**

    **All Methods[Static Methods](javascript:show(1);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type        | Method and Description                                                                                       |
    |--------------------------|--------------------------------------------------------------------------------------------------------------|
    | `static OXQEntityKind`   | `valueOf``(java.lang.String name)`<br>Returns the enum constant of this type with the specified name.        |
    | `static OXQEntityKind[]` | `values``()`<br>Returns an array containing the constants of this enum type, in the order they are declared. |

    - ### Methods inherited from class java.lang.Enum

      `compareTo, equals, getDeclaringClass, hashCode, name, ordinal, toString, valueOf`

    <!-- -->

    - ### Methods inherited from class java.lang.Object

      `getClass, notify, notifyAll, wait, wait, wait`

<!-- -->

- - ### Enum Constant Detail

    - #### MODULE

          public static final OXQEntityKind MODULE

      The kind used to resolve an XQuery module import. The `OXQEntityResolver` may return one or more modules.

    <!-- -->

    - #### SCHEMA

          public static final OXQEntityKind SCHEMA

      The kind used to resolve an XML Schema import. The `OXQEntityResolver` may return one or more schemas.

    <!-- -->

    - #### DOCUMENT_TYPE

          public static final OXQEntityKind DOCUMENT_TYPE

      The kind used to obtain a document type for the `fn:doc` function.

    <!-- -->

    - #### DOCUMENT

          public static final OXQEntityKind DOCUMENT

      The kind used to obtain a document for the `fn:doc` or `fn:collection` function. In the case of `fn:collection`, it is used for each document in the collection.

    <!-- -->

    - #### COLLECTION

          public static final OXQEntityKind COLLECTION

      The kind used to obtain the documents that comprise a collection (used when there is a call to `fn:collection`).

    <!-- -->

    - #### URI_COLLECTION

          public static final OXQEntityKind URI_COLLECTION

      The kind used to obtain the URIs that will be returned by a call to `fn:uri-collection`.

    <!-- -->

    - #### XML_ENTITY

          public static final OXQEntityKind XML_ENTITY

      The kind used when an internal XML parser needs to resolve an XML resource.

    <!-- -->

    - #### EXTERNAL_FUNCTION

          public static final OXQEntityKind EXTERNAL_FUNCTION

      The kind used to obtain an external function binding.

    <!-- -->

    - #### UPD_PUT

          public static final OXQEntityKind UPD_PUT

      The kind used to obtain an implementation for the `fn:put` function. (more precisely, the put primitive)

    <!-- -->

    - #### XML_PARSER_FACTORY

          public static final OXQEntityKind XML_PARSER_FACTORY

      The kind used to obtain an implementation of the StAX parser factory: `XMLInputFactory`

    <!-- -->

    - #### DOM_FACTORY

          public static final OXQEntityKind DOM_FACTORY

      The kind used to obtain an implementation of the DOM factory: `javax.xml.parsers.DocumentBuilderFactory`

    <!-- -->

    - #### COLLATION

          public static final OXQEntityKind COLLATION

      The kind used to obtain a collation.

    <!-- -->

    - #### TEXT

          public static final OXQEntityKind TEXT

      The kind used to obtain unparsed text for the `fn:unparsed-text` function.

    <!-- -->

    - #### ENVIRONMENT_VARIABLE

          public static final OXQEntityKind ENVIRONMENT_VARIABLE

      The kind used to obtain environment variable names and values for `fn:available-environment-variables` and `fn:environment-variable` functions.

  <!-- -->

  - ### Method Detail

    - #### values

          public static OXQEntityKind[] values()

      Returns an array containing the constants of this enum type, in the order they are declared. This method may be used to iterate over the constants as follows:
          for (OXQEntityKind c : OXQEntityKind.values())
              System.out.println(c);

      Returns:
      an array containing the constants of this enum type, in the order they are declared

    <!-- -->

    - #### valueOf

          public static OXQEntityKind valueOf(java.lang.String name)

      Returns the enum constant of this type with the specified name. The string must match *exactly* an identifier used to declare an enum constant in this type. (Extraneous whitespace characters are not permitted.)
      Parameters:
      `name` - the name of the enum constant to be returned.

      Returns:
      the enum constant with the specified name

      Throws:
      `java.lang.IllegalArgumentException` - if this enum type has no constant with the specified name

      `java.lang.NullPointerException` - if the argument is null

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

- **[Prev Class](OXQEntity.md)**
- **[Next Class](OXQEntityLoader.md)**

<!-- -->

- **[Frames](../../../index.md)**
- **No Frames**

<!-- -->

- **[All Classes](../../../allclasses-noframe.md)**

<!-- -->

- **Summary: **
- **Nested \| **
- **Enum Constants \| **
- **Field \| **
- **Method**

<!-- -->

- **Detail: **
- **Enum Constants \| **
- **Field \| **
- **Method**

**Copyright © 2003, 2019, Oracle and/or its affiliates. All rights reserved.
Use is subject to license terms. Also see the documentation redistribution policy.
ORACLE CONFIDENTIAL
For authorized use only.
Do not distribute to third parties.**
