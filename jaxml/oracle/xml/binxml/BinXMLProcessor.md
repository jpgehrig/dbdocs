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

- **[Prev Class](BinXMLMetadataProviderFactory.md)**
- **[Next Class](BinXMLProcessorFactory.md)**

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

**oracle.xml.binxml**

## **Interface BinXMLProcessor**

-

  ------------------------------------------------------------------------

  **
  **

      public interface BinXMLProcessor

  **A top level interface which represents the Binary XML Processor. Defines APIs to be used for creating BinXMLStream object, registering schemas and DTDs and setting the metadata repository.**

<!-- -->

-
  -

    ### **Method Summary**

    **All Methods[Instance Methods](javascript:show(2);)[Abstract Methods](javascript:show(4);)**

    | Modifier and Type                 | Method and Description                                                                                                                                                                      |
    |-----------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | [`BinXMLStream`](BinXMLStream.md) | `createBinXMLStream``()`<br>Method to create a BinXMLStream object for encoding or decoding using default in memory storage for input and output                                            |
    | [`BinXMLStream`](BinXMLStream.md) | `createBinXMLStream``(java.sql.Blob blob)`<br>Method to create a BinXMLStream object for encoding or decoding                                                                               |
    | [`BinXMLStream`](BinXMLStream.md) | `createBinXMLStream``(byte[] array)`<br>Method to create a BinXMLStream object for encoding or decoding                                                                                     |
    | [`BinXMLStream`](BinXMLStream.md) | `createBinXMLStream``(java.io.File file)`<br>Method to create a BinXMLStream object for encoding or decoding                                                                                |
    | [`BinXMLStream`](BinXMLStream.md) | `createBinXMLStream``(java.io.InputStream in)`<br>Method to create a BinXMLStream object for encoding                                                                                       |
    | [`BinXMLStream`](BinXMLStream.md) | `createBinXMLStream``(java.io.OutputStream out)`<br>Method to create a BinXMLStream object for decoding                                                                                     |
    | [`BinXMLStream`](BinXMLStream.md) | `createBinXMLStream``(java.net.URL url)`<br>Method to create a BinXMLStream object for encoding or decoding                                                                                 |
    | `long`                            | `getTokenId``(java.lang.String namespace, java.lang.String localName, boolean isAttr)`<br>Fetch a token based on the namespace and localName provided by the user.                          |
    | `javax.xml.namespace.QName`       | `getTokenName``(long tokenId)`<br>Fetch a token name based on the tokenId provided by the user.                                                                                             |
    | `void`                            | `registerDTD``(`[`DTD`](../parser/v2/DTD.md)` dtd)`<br>Registers a DTD locally with the BinXMLProcessor                                                                                     |
    | `void`                            | `registerDTD``(java.net.URL dtd, java.lang.String rootName)`<br>Registers a DTD locally with the BinXMLProcessor                                                                            |
    | `void`                            | `registerSchema``(java.io.InputStream schema)`<br>Registers a XML schema locally with the BinXMLProcessor                                                                                   |
    | `void`                            | `registerSchema``(java.lang.String sschema, java.io.Reader reader)`<br>Registers a XML schema locally with the BinXMLProcessor                                                              |
    | `void`                            | `registerSchema``(java.net.URL schema)`<br>Registers a XML schema locally with the BinXMLProcessor                                                                                          |
    | `void`                            | `registerSchema``(java.net.URL schema, java.io.Reader reader)`<br>Registers a XML schema locally with the BinXMLProcessor                                                                   |
    | `void`                            | `setEntityResolver``(`[`EntityResolver`](../../../org/xml/sax/EntityResolver.md)` entResolver)`<br>Method to set entity resolver on the BinXMLProcessor.                                    |
    | `void`                            | `setMetadataRepository``(`[`BinXMLMetadataProvider`](BinXMLMetadataProvider.md)` provider)`<br>Users can plug in their own metadata repository that defines the MetadataProvider interface. |

<!-- -->

- - ### Method Detail

    - #### createBinXMLStream

          BinXMLStream createBinXMLStream(java.sql.Blob blob)
                                   throws BinXMLException

      Method to create a BinXMLStream object for encoding or decoding
      Parameters:
      `blob` - The Blob to be used in creating a new BinXMLStream

      Returns:
      A BinXMLStream object associated with the specified argument

      Throws:
      [`BinXMLException`](BinXMLException.md) - Raised for any errors encountered

    <!-- -->

    - #### createBinXMLStream

          BinXMLStream createBinXMLStream(java.io.InputStream in)
                                   throws BinXMLException

      Method to create a BinXMLStream object for encoding
      Parameters:
      `in` - The InputStream to be used in creating a new BinXMLStream

      Returns:
      A BinXMLStream object associated with the specified argument

      Throws:
      [`BinXMLException`](BinXMLException.md) - Raised for any errors encountered

    <!-- -->

    - #### createBinXMLStream

          BinXMLStream createBinXMLStream(java.io.OutputStream out)
                                   throws BinXMLException

      Method to create a BinXMLStream object for decoding
      Parameters:
      `out` - The OutputStream to be used in creating a new BinXMLStream

      Returns:
      A BinXMLStream object associated with the specified argument

      Throws:
      [`BinXMLException`](BinXMLException.md) - Raised for any errors encountered

    <!-- -->

    - #### createBinXMLStream

          BinXMLStream createBinXMLStream(java.io.File file)
                                   throws BinXMLException

      Method to create a BinXMLStream object for encoding or decoding
      Parameters:
      `file` - The File to be used in creating a new BinXMLStream

      Returns:
      A BinXMLStream object associated with the specified argument

      Throws:
      [`BinXMLException`](BinXMLException.md) - Raised for any errors encountered

    <!-- -->

    - #### createBinXMLStream

          BinXMLStream createBinXMLStream(byte[] array)
                                   throws BinXMLException

      Method to create a BinXMLStream object for encoding or decoding
      Parameters:
      `array` - The byte array to be used in creating a new BinXMLStream

      Returns:
      A BinXMLStream object associated with the specified argument

      Throws:
      [`BinXMLException`](BinXMLException.md) - Raised for any errors encountered

    <!-- -->

    - #### createBinXMLStream

          BinXMLStream createBinXMLStream(java.net.URL url)
                                   throws BinXMLException

      Method to create a BinXMLStream object for encoding or decoding
      Parameters:
      `url` - The url to be used in creating a new BinXMLStream if the url is file:// protocol, treat as File in other cases, for decoding, treat as OutputStream; for encoding, treat as InputStream

      Returns:
      A BinXMLStream object associated with the specified argument

      Throws:
      [`BinXMLException`](BinXMLException.md) - Raised for any errors encountered

    <!-- -->

    - #### createBinXMLStream

          BinXMLStream createBinXMLStream()
                                   throws BinXMLException

      Method to create a BinXMLStream object for encoding or decoding using default in memory storage for input and output
      Returns:
      A BinXMLStream object using default storage

      Throws:
      [`BinXMLException`](BinXMLException.md) - Raised for any errors encountered

    <!-- -->

    - #### setEntityResolver

          void setEntityResolver(EntityResolver entResolver)
                          throws BinXMLException

      Method to set entity resolver on the BinXMLProcessor. The entity resolver can be used to redirect system URIs.
      Parameters:
      `entResolver` - Entity Resolver to be called when the processor needs to resolve system URIs.

      Throws:
      [`BinXMLException`](BinXMLException.md) - Raised for any errors encountered

    <!-- -->

    - #### registerSchema

          void registerSchema(java.net.URL schema)
                       throws BinXMLException

      Registers a XML schema locally with the BinXMLProcessor
      Parameters:
      `schema` - URL specifying the location of the XML Schema to be registered

      Throws:
      [`BinXMLException`](BinXMLException.md) - Raised for any errors encountered

    <!-- -->

    - #### registerSchema

          void registerSchema(java.io.InputStream schema)
                       throws BinXMLException

      Registers a XML schema locally with the BinXMLProcessor
      Parameters:
      `schema` - InputStream containing the contents of the XML Schema to be registered

      Throws:
      [`BinXMLException`](BinXMLException.md) - Raised for any errors encountered

    <!-- -->

    - #### registerSchema

          void registerSchema(java.net.URL schema,
                              java.io.Reader reader)
                       throws BinXMLException

      Registers a XML schema locally with the BinXMLProcessor
      Parameters:
      `schema` - URL of the XML Schema to be registered

      `reader` - containing the XML Schema contents to be registered

      Throws:
      [`BinXMLException`](BinXMLException.md) - Raised for any errors encountered

    <!-- -->

    - #### registerSchema

          void registerSchema(java.lang.String sschema,
                              java.io.Reader reader)
                       throws BinXMLException

      Registers a XML schema locally with the BinXMLProcessor
      Parameters:
      `sschema` - string representation of schema URL

      `reader` - containing the XML Schema contents to be registered

      Throws:
      [`BinXMLException`](BinXMLException.md) - Raised for any errors encountered

    <!-- -->

    - #### registerDTD

          void registerDTD(java.net.URL dtd,
                           java.lang.String rootName)
                    throws BinXMLException

      Registers a DTD locally with the BinXMLProcessor
      Parameters:
      `dtd` - URL for DTD to be registered

      `rootName` - specifies the root element

      Throws:
      [`BinXMLException`](BinXMLException.md) - Raised for any errors encountered

    <!-- -->

    - #### registerDTD

          void registerDTD(DTD dtd)
                    throws BinXMLException

      Registers a DTD locally with the BinXMLProcessor
      Parameters:
      `dtd` - input DTD to be registered

      Throws:
      [`BinXMLException`](BinXMLException.md) - Raised for any errors encountered

    <!-- -->

    - #### getTokenId

          long getTokenId(java.lang.String namespace,
                          java.lang.String localName,
                          boolean isAttr)
                   throws BinXMLException

      Fetch a token based on the namespace and localName provided by the user. Check local vocabulary cache; if the token is not available we fetch it from the metadata repository. If token is not found then it will throw a BinXMLException.
      Parameters:
      `namespace` - - namespace URL of the token to be fetched

      `localName` - - local name of the token to be fetched

      `isAttr` - - if true will return attribute id else returns element id

      Returns:
      token id

      Throws:
      [`BinXMLException`](BinXMLException.md) - Raised for any errors encountered

    <!-- -->

    - #### getTokenName

          javax.xml.namespace.QName getTokenName(long tokenId)
                                          throws BinXMLException

      Fetch a token name based on the tokenId provided by the user. Check local vocabulary cache, if there is no match, then fetch it from metadata repository. If tokenId is not found then throw a BinXMLException.
      Parameters:
      `tokenId` - - input token id

      Returns:
      token QName, with name and namespace, based on input tokenId

      Throws:
      [`BinXMLException`](BinXMLException.md) - Raised for any errors encountered

    <!-- -->

    - #### setMetadataRepository

          void setMetadataRepository(BinXMLMetadataProvider provider)
                              throws BinXMLException

      Users can plug in their own metadata repository that defines the MetadataProvider interface. The DBMetadataProvider implementation to use the Oracle database as a metadata storage repository is available as part of this package. If a non-database repository is needed the user will need to define their own.
      Parameters:
      `provider` - - metdata provider implementation

      Throws:
      [`BinXMLException`](BinXMLException.md) - Raised for any errors encountered

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

- **[Prev Class](BinXMLMetadataProviderFactory.md)**
- **[Next Class](BinXMLProcessorFactory.md)**

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
