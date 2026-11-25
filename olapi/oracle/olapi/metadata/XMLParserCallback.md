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

- [Prev Class](XML11_2_ParserCallback.md)
- [Next Class](XMLWriterCallback.md)

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

## Interface XMLParserCallback

- All Known Subinterfaces:
  [XML11_2_ParserCallback](XML11_2_ParserCallback.md)

  ------------------------------------------------------------------------



      public interface XMLParserCallback

  An interface for an object that processes errors that occur as an `MdmMetadataProvider.importXML` method produces a metadata object from an XML object definition or as a `SyntaxObject.fromSyntax` method produces a `SyntaxObject`. An application passes an implementation of this interface to an `importXML` or `fromSyntax` method. If an error occurs, Oracle OLAP calls a method of the `XMLParserCallback`. The method processes the error and returns one of the constants defined by this interface.
  An application can also specify an `XMLParserCallback` for a `UserSession`. The Oracle OLAP server uses that `XMLParserCallback` if it gets a metadata object for the application and the metadata object is invalid. The `ERROR_BY_EXCEPTION` constant does not apply to an `XMLParserCallback` for a `UserSession`.

<!-- -->

- - ### Field Summary

    **Fields**

    | Modifier and Type | Field and Description                                                                                                       |
    |-------------------|-----------------------------------------------------------------------------------------------------------------------------|
    | `static int`      | `DEFAULT_ERROR_BY`<br>A constant that represents the default manner of handling error conditions.                           |
    | `static int`      | `ERROR_BY_EXCEPTION`<br>A constant that directs Oracle OLAP to throw an exception after returning from the callback method. |
    | `static int`      | `ERROR_BY_INVALIDATING`<br>A constant that directs Oracle OLAP to mark the property as invalid and to continue parsing.     |
    | `static int`      | `ERROR_BY_SET_TO_NULL`<br>A constant that directs Oracle OLAP to set the property to `null` and to continuing parsing.      |

  <!-- -->

  - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Abstract Methods](javascript:show(4);)**

    | Modifier and Type | Method and Description                                                                                                                                                                                                                                                                                   |
    |-------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `int`             | `processError``(java.lang.String objectID, java.lang.String attribute, java.lang.String value)`<br>Processes errors that occur as an `MdmMetadataProvider.importXML` method produces a metadata object from an XML object definition or as a `SyntaxObject.fromSyntax` method produces a `SyntaxObject`. |
    | `int`             | `processSyntaxIdentifiersError``(java.lang.String value, java.lang.String[] identifiers)`<br>Processes syntax identifier errors that occur as a `SyntaxObject.fromSyntax` method produces a `SyntaxObject`.                                                                                              |
    | `int`             | `processSyntaxIdentifiersError``(java.lang.String objectID, java.lang.String attribute, java.lang.String value, java.lang.String[] identifiers)`<br>Processes syntax identifier errors that occur as a `SyntaxObject.fromSyntax` method produces a `SyntaxObject`.                                       |

<!-- -->

- - ### Field Detail

    - #### DEFAULT_ERROR_BY

          static final int DEFAULT_ERROR_BY

      A constant that represents the default manner of handling error conditions.
      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### ERROR_BY_EXCEPTION

          static final int ERROR_BY_EXCEPTION

      A constant that directs Oracle OLAP to throw an exception after returning from the callback method.
      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### ERROR_BY_SET_TO_NULL

          static final int ERROR_BY_SET_TO_NULL

      A constant that directs Oracle OLAP to set the property to `null` and to continuing parsing.
      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### ERROR_BY_INVALIDATING

          static final int ERROR_BY_INVALIDATING

      A constant that directs Oracle OLAP to mark the property as invalid and to continue parsing. This option is valid only for the `processSyntaxIdentifiersError` methods.
      See Also:
      [Constant Field Values](../../../constant-values.md)

  <!-- -->

  - ### Method Detail

    - #### processError

          int processError(java.lang.String objectID,
                           java.lang.String attribute,
                           java.lang.String value)

      Processes errors that occur as an `MdmMetadataProvider.importXML` method produces a metadata object from an XML object definition or as a `SyntaxObject.fromSyntax` method produces a `SyntaxObject`.
      Parameters:
      `objectID` - A `String` that contains the identifier of an object.

      `attribute` - A `String` that contains an XML attribute of the object.

      `value` - A `String` that contains the value of the attribute.

      Returns:
      An integer that is any of the constants of this interface except `ERROR_BY_INVALIDATING`.

    <!-- -->

    - #### processSyntaxIdentifiersError

          int processSyntaxIdentifiersError(java.lang.String objectID,
                                            java.lang.String attribute,
                                            java.lang.String value,
                                            java.lang.String[] identifiers)

      Processes syntax identifier errors that occur as a `SyntaxObject.fromSyntax` method produces a `SyntaxObject`.
      Parameters:
      `objectID` - A `String` that contains the identifier of an object.

      `attribute` - A `String` that contains an XML attribute of the object.

      `value` - A `String` that contains the syntax expression.

      `identifiers` - An array of `String` objects that contain identifiers.

      Returns:
      An integer that is any of the constants of this interface.

    <!-- -->

    - #### processSyntaxIdentifiersError

          int processSyntaxIdentifiersError(java.lang.String value,
                                            java.lang.String[] identifiers)

      Processes syntax identifier errors that occur as a `SyntaxObject.fromSyntax` method produces a `SyntaxObject`.
      Parameters:
      `value` - A `String` that contains the syntax expression.

      `identifiers` - An array of `String` objects that contain identifiers.

      Returns:
      An integer that is any of the constants of this interface.

Skip navigation links

- [Overview](../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../deprecated-list.md)
- [Index](../../../index-all.md)
- [Help](../../../help-doc.md)

Copyright © 2002, 2018, Oracle. All rights reserved.

- [Prev Class](XML11_2_ParserCallback.md)
- [Next Class](XMLWriterCallback.md)

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
