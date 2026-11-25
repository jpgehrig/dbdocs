Skip navigation links

- [Overview](../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../deprecated-list.md)
- [Index](../../../index-all.md)
- [Help](../../../help-doc.md)

**Oracle® OLAP Java API Reference
19c**
E96404-01

- [Prev Class](PublicMetadataObject.md)
- [Next Class](XMLParserCallback.md)

<!-- -->

- [Frames](../../../index.md)
- No Frames

<!-- -->

- [All Classes](../../../allclasses-noframe.md)

<!-- -->

- Summary: 
- Nested \| 
- Field \| 
- Constr \| 
- Method

<!-- -->

- Detail: 
- Field \| 
- Constr \| 
- Method

oracle.olapi.metadata

## Interface XML11_2_ParserCallback

- All Superinterfaces:
  [XMLParserCallback](XMLParserCallback.md)

  ------------------------------------------------------------------------



      public interface XML11_2_ParserCallback
      extends XMLParserCallback

  An extension of the `XMLParserCallback` interface that adds methods for renaming an object and for suppressing attributes of objects.

<!-- -->

- - ### Field Summary

    - ### Fields inherited from interface oracle.olapi.metadata.[XMLParserCallback](XMLParserCallback.md)

      [`DEFAULT_ERROR_BY`](XMLParserCallback.md)`, `[`ERROR_BY_EXCEPTION`](XMLParserCallback.md)`, `[`ERROR_BY_INVALIDATING`](XMLParserCallback.md)`, `[`ERROR_BY_SET_TO_NULL`](XMLParserCallback.md)

  <!-- -->

  - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Abstract Methods](javascript:show(4);)**

    | Modifier and Type  | Method and Description                                                                                                                                                                                                                                                                          |
    |--------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `java.lang.String` | `renameObject``(java.lang.String objectID, java.lang.String currentName, java.lang.Class objectType)`<br>Gets a new name for an object that is being imported by an `MdmMetadataProvider.importXML` method or that is being produced by a `SyntaxObject.fromSyntax` method of a `SyntaxObject`. |
    | `boolean`          | `suppressXMLAttribute``(java.lang.String objectID, java.lang.Class objectType, java.lang.String attribute, java.lang.String value)`<br>Indicates whether or not the XML parser should suppress an XML attribute of an object so that it does not appear in the imported XML.                    |

    - ### Methods inherited from interface oracle.olapi.metadata.[XMLParserCallback](XMLParserCallback.md)

      [`processError`](XMLParserCallback.md)`, `[`processSyntaxIdentifiersError`](XMLParserCallback.md)`, `[`processSyntaxIdentifiersError`](XMLParserCallback.md)

<!-- -->

- - ### Method Detail

    - #### renameObject

          java.lang.String renameObject(java.lang.String objectID,
                                        java.lang.String currentName,
                                        java.lang.Class objectType)

      Gets a new name for an object that is being imported by an `MdmMetadataProvider.importXML` method or that is being produced by a `SyntaxObject.fromSyntax` method of a `SyntaxObject`.
      Parameters:
      `objectID` - A `String` that contains the identifier of an object.

      `currentName` - A `String` that contains the current name of the object.

      `objectType` - The `Class` of the type of object that the parser is processing.

      Returns:
      A `String` that contains a new name for the object.

    <!-- -->

    - #### suppressXMLAttribute

          boolean suppressXMLAttribute(java.lang.String objectID,
                                       java.lang.Class objectType,
                                       java.lang.String attribute,
                                       java.lang.String value)

      Indicates whether or not the XML parser should suppress an XML attribute of an object so that it does not appear in the imported XML. XML attributes are strings such as `ETViewName`, `ETKeyColumnName`, and `TablespaceName`.
      Parameters:
      `objectID` - A `String` that contains the identifier of the `BaseMetadataObject` that the parser is processing.

      `objectType` - The `Class` of the `BaseMetadataObject` being parsed.

      `attribute` - A `String` that contains the XML attribute being parsed.

      `value` - A `String` that contains the value of the attribute being parsed.

      Returns:
      A `boolean` that is `true` if you want the XML parser to suppress the attribute or `false` if you do not want the attribute suppressed.

Skip navigation links

- [Overview](../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../deprecated-list.md)
- [Index](../../../index-all.md)
- [Help](../../../help-doc.md)

Copyright © 2002, 2018, Oracle. All rights reserved.

- [Prev Class](PublicMetadataObject.md)
- [Next Class](XMLParserCallback.md)

<!-- -->

- [Frames](../../../index.md)
- No Frames

<!-- -->

- [All Classes](../../../allclasses-noframe.md)

<!-- -->

- Summary: 
- Nested \| 
- Field \| 
- Constr \| 
- Method

<!-- -->

- Detail: 
- Field \| 
- Constr \| 
- Method
