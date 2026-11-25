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

- **[Prev Class](BinXMLException.md)**
- **[Next Class](BinXMLMetadataProviderFactory.md)**

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

## **Interface BinXMLMetadataProvider**

- **All Known Subinterfaces:**
  **[DBBinXMLMetadataProvider](DBBinXMLMetadataProvider.md)**

  <!-- -->

  **All Known Implementing Classes:**
  **[DBBinXMLMetadataProviderImpl](DBBinXMLMetadataProviderImpl.md)**

  ------------------------------------------------------------------------

  **
  **

      public interface BinXMLMetadataProvider

  **This interface defines APIs for users to plug in a metadata repository used for encoding and decoding. A database implementation of this API is provided , see DBBinXMLMetadataProvider interface.**

<!-- -->

-
  -

    ### **Method Summary**

    **All Methods[Instance Methods](javascript:show(2);)[Abstract Methods](javascript:show(4);)**

    | Modifier and Type                   | Method and Description                                                                                                                                                  |
    |-------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `java.io.Reader`                    | `getCompiledSchema``(`[`BinXMLVocabId`](BinXMLVocabId.md)` schemaId)`<br>Fetches the schema as a binary stream from the metadata repository based on the vocabulary id. |
    | `java.io.Reader`                    | `getCompiledSchema``(java.lang.String schemaURL)`<br>Fetches the schema as a binary stream from the metadata repository based on the schema URL.                        |
    | [`BinXMLStream`](BinXMLStream.md)   | `getDTD``(`[`BinXMLVocabId`](BinXMLVocabId.md)` dtdId)`<br>Fetches the DTD as a binary stream from the metadata repository based on the vocabulary id.                  |
    | [`BinXMLStream`](BinXMLStream.md)   | `getDTD``(java.lang.String dtdURL)`<br>Fetches the DTD as a binary stream from the metadata repository based on the DTD URL.                                            |
    | [`BinXMLStream`](BinXMLStream.md)   | `getTokenSet``(long tokenId)`<br>Fetches the Token Set as a binary stream in the metadata repository based on the input token id.                                       |
    | [`BinXMLStream`](BinXMLStream.md)   | `getTokenSet``(long tokenId, boolean isNS)`<br>Fetches the Token Set as a binary stream in the metadata repository based on the namespace of the input token Id.        |
    | [`BinXMLStream`](BinXMLStream.md)   | `getTokenSet``(java.lang.String namespaceURL, boolean isAttr)`<br>Fetches the Token Set as a binary stream in the metadata repository based on the namespace URL.       |
    | `boolean`                           | `isSchemaAnnotationAvailable``()`<br>Specifies whether the repository performs schema annotations or not.                                                               |
    | [`BinXMLVocabId`](BinXMLVocabId.md) | `saveCompiledSchema``(java.lang.String schemaURL)`<br>Saves the annotated schema as a binary stream in the metadata repository.                                         |
    | [`BinXMLVocabId`](BinXMLVocabId.md) | `saveDTD``(java.lang.String dtdURL)`<br>Saves the DTD as a binary stream in the metadata repository.                                                                    |
    | [`BinXMLVocabId`](BinXMLVocabId.md) | `saveSchema``(java.lang.String schemaURL)`<br>The repository accepts a non-annotated schema, annotates it and saves it as a binary stream in the metadata repository.   |
    | [`BinXMLVocabId`](BinXMLVocabId.md) | `saveTokenSet``(java.lang.String namespaceURL)`<br>Saves the Token Set as a binary stream in the metadata repository.                                                   |

<!-- -->

- - ### Method Detail

    - #### isSchemaAnnotationAvailable

          boolean isSchemaAnnotationAvailable()
                                       throws BinXMLException

      Specifies whether the repository performs schema annotations or not. For example for the database (DBBinXMLMetadataProvider) will return true here. The Binary XML Processor calls this API to determine whether to call saveSchema for registering a schema in the repository where the annotations are performed by the repository or call saveCompiledSchema for saving a already annotated schema to the repository. Non-database repositories might typically return false here.
      Returns:
      true if the repository does schema annotations while saving schemas otherwise the repository returns false

      Throws:
      [`BinXMLException`](BinXMLException.md)

    <!-- -->

    - #### getCompiledSchema

          java.io.Reader getCompiledSchema(BinXMLVocabId schemaId)
                                    throws BinXMLException

      Fetches the schema as a binary stream from the metadata repository based on the vocabulary id.
      Parameters:
      `schemaId` - - vocabulary id of the schema to be fetched

      Returns:
      binary stream version of the annotated schema doc

      Throws:
      [`BinXMLException`](BinXMLException.md)

    <!-- -->

    - #### getCompiledSchema

          java.io.Reader getCompiledSchema(java.lang.String schemaURL)
                                    throws BinXMLException

      Fetches the schema as a binary stream from the metadata repository based on the schema URL.
      Parameters:
      `schemaURL` - - URL of the schema to be fetched

      Returns:
      binary stream version of the annotated schema doc

      Throws:
      [`BinXMLException`](BinXMLException.md)

    <!-- -->

    - #### saveSchema

          BinXMLVocabId saveSchema(java.lang.String schemaURL)
                            throws BinXMLException

      The repository accepts a non-annotated schema, annotates it and saves it as a binary stream in the metadata repository.
      Parameters:
      `schemaURL` - - URL of the schema to be saved

      Returns:
      the vocabulary id of the saved schema

      Throws:
      [`BinXMLException`](BinXMLException.md)

    <!-- -->

    - #### saveCompiledSchema

          BinXMLVocabId saveCompiledSchema(java.lang.String schemaURL)
                                    throws BinXMLException

      Saves the annotated schema as a binary stream in the metadata repository. s@param chemaURL - URL of the schema to be saved
      Returns:
      the vocabulary id saved schema

      Throws:
      [`BinXMLException`](BinXMLException.md)

    <!-- -->

    - #### getDTD

          BinXMLStream getDTD(BinXMLVocabId dtdId)
                       throws BinXMLException

      Fetches the DTD as a binary stream from the metadata repository based on the vocabulary id.
      Parameters:
      `dtdId` - - vocabulary id of the DTD to be fetched

      Returns:
      binary stream version of the DTD

      Throws:
      [`BinXMLException`](BinXMLException.md)

    <!-- -->

    - #### getDTD

          BinXMLStream getDTD(java.lang.String dtdURL)
                       throws BinXMLException

      Fetches the DTD as a binary stream from the metadata repository based on the DTD URL.
      Parameters:
      `dtdURL` - - URL of the DTD to be fetched

      Returns:
      binary stream version of the DTD

      Throws:
      [`BinXMLException`](BinXMLException.md)

    <!-- -->

    - #### saveDTD

          BinXMLVocabId saveDTD(java.lang.String dtdURL)
                         throws BinXMLException

      Saves the DTD as a binary stream in the metadata repository.
      Parameters:
      `dtdURL` - - URL of the DTD to be saved

      Returns:
      the vocabulary id of the DTD to be saved

      Throws:
      [`BinXMLException`](BinXMLException.md)

    <!-- -->

    - #### getTokenSet

          BinXMLStream getTokenSet(java.lang.String namespaceURL,
                                   boolean isAttr)
                            throws BinXMLException

      Fetches the Token Set as a binary stream in the metadata repository based on the namespace URL.
      Parameters:
      `namespaceURL` - - namespace URL of the Token Set to be fetched

      `isAttr` - - is the token set to be returned of type element or attr

      Returns:
      binary stream version of the Token Set

      Throws:
      [`BinXMLException`](BinXMLException.md)

    <!-- -->

    - #### getTokenSet

          BinXMLStream getTokenSet(long tokenId,
                                   boolean isNS)
                            throws BinXMLException

      Fetches the Token Set as a binary stream in the metadata repository based on the namespace of the input token Id.
      Parameters:
      `tokenId` - - token Id contained in the Token Set to be fetched

      `isNS` - - if this token is a namespace decl, then true, otherwise false

      Returns:
      binary stream version of the Token Set

      Throws:
      [`BinXMLException`](BinXMLException.md)

    <!-- -->

    - #### getTokenSet

          BinXMLStream getTokenSet(long tokenId)
                            throws BinXMLException

      Fetches the Token Set as a binary stream in the metadata repository based on the input token id.
      Parameters:
      `tokenId` - - token Id contained in the Token Set to be fetched

      Returns:
      binary stream version of the Token Set

      Throws:
      [`BinXMLException`](BinXMLException.md)

    <!-- -->

    - #### saveTokenSet

          BinXMLVocabId saveTokenSet(java.lang.String namespaceURL)
                              throws BinXMLException

      Saves the Token Set as a binary stream in the metadata repository.
      Parameters:
      `namespaceURL` - - namespace URL of the Token Set to be saved

      Returns:
      vocabulary id of the Token Set saved in the metadata repository

      Throws:
      [`BinXMLException`](BinXMLException.md)

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

- **[Prev Class](BinXMLException.md)**
- **[Next Class](BinXMLMetadataProviderFactory.md)**

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
