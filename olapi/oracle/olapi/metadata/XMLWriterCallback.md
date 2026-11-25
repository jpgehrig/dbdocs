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

- [Prev Class](XMLParserCallback.md)
- Next Class

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

## Interface XMLWriterCallback

-

  ------------------------------------------------------------------------



      public interface XMLWriterCallback

  An interface for an object that Oracle OLAP calls to find out whether or not to exclude an attribute or an owner name from the XML that an `MdmMetadataProvider` is exporting. An application passes an implementation of this interface to an `exportFullXML` or an `exportIncrementalXML` method of the `MdmMetadataProvider`. As the Oracle OLAP XML writer exports the XML representations of the metadata objects, Oracle OLAP calls the methods of the `XMLWriterCallback`. The methods of the `XMLWriterCallback` return a `boolean` that tells the XML writer whether or not to exclude the attribute or owner name from the exported XML.

<!-- -->

- - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Abstract Methods](javascript:show(4);)**

    | Modifier and Type | Method and Description                                                                                                                                                                                                                                                                                                                       |
    |-------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `boolean`         | `suppressOwnerName``(`[`BaseMetadataObject`](BaseMetadataObject.md)` obj, java.lang.String attribute, `[`SyntaxObject`](../syntax/SyntaxObject.md)` syntaxValue, boolean defaultSuppression)`<br>Indicates whether or not the XML writer should suppress the name of the owner of the object so that it does not appear in the exported XML. |
    | `boolean`         | `suppressXMLAttribute``(`[`BaseMetadataObject`](BaseMetadataObject.md)` obj, java.lang.String attribute, java.lang.String value)`<br>Indicates whether or not the XML writer should suppress the XML attribute of the object so that it does not appear in the exported XML.                                                                 |

<!-- -->

- - ### Method Detail

    - #### suppressXMLAttribute

          boolean suppressXMLAttribute(BaseMetadataObject obj,
                                       java.lang.String attribute,
                                       java.lang.String value)

      Indicates whether or not the XML writer should suppress the XML attribute of the object so that it does not appear in the exported XML. XML attributes are strings such as `ETViewName`, `ETKeyColumnName`, and `TablespaceName`.
      Parameters:
      `obj` - The `BaseMetadataObject` to export to XML.

      `attribute` - A `String` that contains the XML attribute to suppress.

      `value` - A `String` that contains the value of the attribute.

      Returns:
      A `boolean` that is `true` if you want the XML writer to suppress the attribute or `false` if you do not want the attribute suppressed.

    <!-- -->

    - #### suppressOwnerName

          boolean suppressOwnerName(BaseMetadataObject obj,
                                    java.lang.String attribute,
                                    SyntaxObject syntaxValue,
                                    boolean defaultSuppression)

      Indicates whether or not the XML writer should suppress the name of the owner of the object so that it does not appear in the exported XML. XML attributes that can have a `SyntaxObject` as a value include a `KeyExpression` or a `Query` of an `ObjectMap`.
      One use for excluding the owner name is that you can export the table mappings that you created in a schema owned by one user and then import those mappings and apply them to a schema owned by a different user.

      Parameters:
      `obj` - The `BaseMetadataObject` to export to XML.

      `attribute` - A `String` that contains the XML attribute of the object that has a `SyntaxObject` as a value.

      `syntaxValue` - A `SyntaxObject` that includes the name of the owner.

      `defaultSuppression` - The value of the `includeOwnerString` parameter of the `exportFullXML` or `exportIncrementalXML` method that is exporting the XML.

      Returns:
      A `boolean` that is `true` if you want the XML writer to suppress the name of the owner or `false` if you do not want the owner name suppressed.

Skip navigation links

- [Overview](../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../deprecated-list.md)
- [Index](../../../index-all.md)
- [Help](../../../help-doc.md)

Copyright © 2002, 2018, Oracle. All rights reserved.

- [Prev Class](XMLParserCallback.md)
- Next Class

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
