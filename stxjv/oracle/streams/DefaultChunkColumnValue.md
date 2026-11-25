Skip navigation links

- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../deprecated-list.md)
- [Index](../../index-all.md)
- [Help](../../help-doc.md)

**Oracle® Database XStream Java API Reference
19c**
E96285-02

- [Prev Class](DDLLCR.md)
- [Next Class](DefaultColumnValue.md)

<!-- -->

- [Frames](../../index.md)
- No Frames

<!-- -->

- [All Classes](../../allclasses-noframe.md)

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

oracle.streams

## Class DefaultChunkColumnValue

- java.lang.Object

- - [oracle.streams.DefaultColumnValue](DefaultColumnValue.md)

  - - oracle.streams.DefaultChunkColumnValue

<!-- -->

- All Implemented Interfaces:
  [ChunkColumnValue](ChunkColumnValue.md), [ColumnValue](ColumnValue.md)

  ------------------------------------------------------------------------



      public class DefaultChunkColumnValue
      extends DefaultColumnValue
      implements ChunkColumnValue

  The DefaultChunkColumnValue class provides an Oracle default implementation of the ChunkColumnValue interface.
  See Also:
  [`RowLCR`](RowLCR.md)

<!-- -->

- - ### Field Summary

    - ### Fields inherited from interface oracle.streams.[ChunkColumnValue](ChunkColumnValue.md)

      [`BLOB`](ChunkColumnValue.md)`, `[`CLOB`](ChunkColumnValue.md)`, `[`LONG`](ChunkColumnValue.md)`, `[`LONGRAW`](ChunkColumnValue.md)`, `[`NCLOB`](ChunkColumnValue.md)`, `[`XMLTYPE`](ChunkColumnValue.md)

    <!-- -->

    - ### Fields inherited from interface oracle.streams.[ColumnValue](ColumnValue.md)

      [`BINARY_DOUBLE`](ColumnValue.md)`, `[`BINARY_FLOAT`](ColumnValue.md)`, `[`CHAR`](ColumnValue.md)`, `[`DATE`](ColumnValue.md)`, `[`INTERVALDS`](ColumnValue.md)`, `[`INTERVALYM`](ColumnValue.md)`, `[`NUMBER`](ColumnValue.md)`, `[`RAW`](ColumnValue.md)`, `[`TIMESTAMP`](ColumnValue.md)`, `[`TIMESTAMPLTZ`](ColumnValue.md)`, `[`TIMESTAMPTZ`](ColumnValue.md)

  <!-- -->

  - ### Constructor Summary

    **Constructors**

    | Constructor and Description                                                                                                                                                                                                                                 |
    |-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `DefaultChunkColumnValue``(java.lang.String columnName, oracle.sql.Datum columnData, int chunkType)`<br>Constructs a DefaultChunkColumnValue object with the column information.                                                                            |
    | `DefaultChunkColumnValue``(java.lang.String columnName, oracle.sql.Datum columnData, int chunkType, java.math.BigInteger chunkOffset, java.math.BigInteger chunkOperationSize)`<br>Constructs a DefaultChunkColumnValue object with the column information. |

  <!-- -->

  - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type      | Method and Description                                                                                                                                                                |
    |------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `int`                  | `getCharSetId``()`<br>Gets the chunk character set identifier (ID) for an XMLTYPE chunk<br>The character set ID indicates the character set used to interpret the XMLTYPE chunk data. |
    | `java.math.BigInteger` | `getChunkOffset``()`<br>Gets the chunk operation offset.                                                                                                                              |
    | `java.math.BigInteger` | `getChunkOperationSize``()`<br>Gets the chunk operation size.                                                                                                                         |
    | `int`                  | `getChunkType``()`<br>Gets the chunk type.                                                                                                                                            |
    | `boolean`              | `isEmptyChunk``()`<br>Indicates whether the chunk is empty.                                                                                                                           |
    | `boolean`              | `isEndOfRow``()`<br>Indicates whether the chunk is the end of the entire row change.                                                                                                  |
    | `boolean`              | `isLastChunk``()`<br>Indicates whether the chunk is the last one for the column.                                                                                                      |
    | `boolean`              | `isXMLDiff``()`<br>Indicates whether the chunk is an XMLDiff.                                                                                                                         |
    | `void`                 | `setCharSetId``(int charSetId)`<br>Sets the character set ID for an XMLTYPE chunk.                                                                                                    |
    | `void`                 | `setChunkOffset``(java.math.BigInteger chunkOffset)`<br>Sets the chunk operation offset.                                                                                              |
    | `void`                 | `setChunkOperationSize``(java.math.BigInteger chunkOperationSize)`<br>Sets the chunk operation size.                                                                                  |
    | `void`                 | `setChunkType``(int chunkType)`<br>Sets the chunk type.                                                                                                                               |
    | `void`                 | `setColumnData``(oracle.sql.Datum columnData)`<br>Sets the column data for a ChunkColumnValue.                                                                                        |
    | `void`                 | `setColumnData``(oracle.sql.Datum columnData, int columnDataType)`<br>Sets the column data.                                                                                           |
    | `void`                 | `setEmptyChunk``(boolean emptyChunk)`<br>Sets the empty chunk flag.                                                                                                                   |
    | `void`                 | `setEndOfRow``(boolean endOfRow)`<br>Sets the endOfRow chunk flag.                                                                                                                    |
    | `void`                 | `setLastChunk``(boolean lastChunk)`<br>Sets the last chunk flag.                                                                                                                      |
    | `void`                 | `setXMLDiff``(boolean xmlDiff)`<br>Sets the XMLDiff flag.                                                                                                                             |
    | `java.lang.String`     | `toString``()`                                                                                                                                                                        |

    - ### Methods inherited from class oracle.streams.[DefaultColumnValue](DefaultColumnValue.md)

      [`getCharsetId`](DefaultColumnValue.md)`, `[`getColumnData`](DefaultColumnValue.md)`, `[`getColumnDataType`](DefaultColumnValue.md)`, `[`getColumnName`](DefaultColumnValue.md)`, `[`getTDEFlag`](DefaultColumnValue.md)`, `[`is32kData`](DefaultColumnValue.md)`, `[`set32kData`](DefaultColumnValue.md)`, `[`setCharsetId`](DefaultColumnValue.md)`, `[`setColumnName`](DefaultColumnValue.md)`, `[`setTDEFlag`](DefaultColumnValue.md)

    <!-- -->

    - ### Methods inherited from class java.lang.Object

      `equals, getClass, hashCode, notify, notifyAll, wait, wait, wait`

    <!-- -->

    - ### Methods inherited from interface oracle.streams.[ColumnValue](ColumnValue.md)

      [`getCharsetId`](ColumnValue.md)`, `[`getColumnData`](ColumnValue.md)`, `[`getColumnDataType`](ColumnValue.md)`, `[`getColumnName`](ColumnValue.md)`, `[`getTDEFlag`](ColumnValue.md)`, `[`is32kData`](ColumnValue.md)`, `[`set32kData`](ColumnValue.md)`, `[`setCharsetId`](ColumnValue.md)`, `[`setColumnName`](ColumnValue.md)`, `[`setTDEFlag`](ColumnValue.md)

<!-- -->

- - ### Constructor Detail

    - #### DefaultChunkColumnValue

          public DefaultChunkColumnValue(java.lang.String columnName,
                                         oracle.sql.Datum columnData,
                                         int chunkType)
                                  throws StreamsException

      Constructs a DefaultChunkColumnValue object with the column information.
      Parameters:
      `columnName` - The column name, cannot be NULL

      `columnData` - The column data, can be NULL. If NULL is used, a valid chunk type must be specified.

      `chunkType` - The chunk type as defined in ChunkColumnValue

      Throws:
      [`StreamsException`](StreamsException.md) - is thrown if columnName is NULL

    <!-- -->

    - #### DefaultChunkColumnValue

          public DefaultChunkColumnValue(java.lang.String columnName,
                                         oracle.sql.Datum columnData,
                                         int chunkType,
                                         java.math.BigInteger chunkOffset,
                                         java.math.BigInteger chunkOperationSize)
                                  throws StreamsException

      Constructs a DefaultChunkColumnValue object with the column information. as well as the offset and size.
      Parameters:
      `columnName` - The column name, cannot be NULL

      `columnData` - The column data, can be NULL. If NULL is used, a valid chunk type must be specified.

      `chunkType` - The chunk type as defined in ChunkColumnValue

      `chunkOffset` - The chunk operation offset

      `chunkOperationSize` - The chunk operation size

      Throws:
      [`StreamsException`](StreamsException.md) - is thrown if chunkType is invalid

  <!-- -->

  - ### Method Detail

    - #### getChunkType

          public int getChunkType()

      Gets the chunk type.
      Chunk type indicates the type of the column for which data can be divided into multiple chunks. Valid values are BLOB, CLOB, NCLOB, or XMLTYPE.
      Specified by:
      [`getChunkType`](ChunkColumnValue.md) in interface [`ChunkColumnValue`](ChunkColumnValue.md)

      Returns:
      A integer contains the chunk type as defined in ChunkColumnValue

    <!-- -->

    - #### setChunkType

          public void setChunkType(int chunkType)
                            throws StreamsException

      Sets the chunk type.
      Chunk type is used to specify the type of the column for which data can be divided into mutliple chunks. Valid values are BLOB, CLOB, NCLOB, or XMLTYPE. See chunk type definition in ChunkColumnValue.
      Specified by:
      [`setChunkType`](ChunkColumnValue.md) in interface [`ChunkColumnValue`](ChunkColumnValue.md)

      Parameters:
      `chunkType` - The chunk type as defined in ChunkColumnValue

      Throws:
      [`StreamsException`](StreamsException.md) - is thrown if chunk type is unsupported

    <!-- -->

    - #### setColumnData

          public void setColumnData(oracle.sql.Datum columnData)

      Sets the column data for a ChunkColumnValue.
      Column data in a chunk can be an instance of either oracle.sql.CHAR or oracle.sql.RAW.
      Parameters:
      `columnData` - The column data, instance of oracle.sql.Datum subclass.

    <!-- -->

    - #### setColumnData

          public void setColumnData(oracle.sql.Datum columnData,
                                    int columnDataType)
                             throws StreamsException

      Sets the column data.
      This method overwrites the method defined in parent class ColumnValue.
      columnDataType is ignored in this class since the columnDataType can be derived from chunkType if it is a ChunkColumnValue object. The mapping is maintained internally.
      Specified by:
      [`setColumnData`](ColumnValue.md) in interface [`ColumnValue`](ColumnValue.md)

      Overrides:
      [`setColumnData`](DefaultColumnValue.md) in class [`DefaultColumnValue`](DefaultColumnValue.md)

      Parameters:
      `columnData` - The column data, instance of oracle.sql.Datum subclasses.

      `columnDataType` - The column data type as defined in ColumnValue.

      Throws:
      [`StreamsException`](StreamsException.md) - is thrown if the columnData is NULL and the columnDataType maintained internally is invalid.

    <!-- -->

    - #### getChunkOffset

          public java.math.BigInteger getChunkOffset()

      Gets the chunk operation offset.
      This method is used to obtain the offset information for piecewise LOB operations. For DML operations, NULL is returned.
      If there are multiple chunks for one LOB WRITE operation, only the offset of the first chunk is relevant.
      Specified by:
      [`getChunkOffset`](ChunkColumnValue.md) in interface [`ChunkColumnValue`](ChunkColumnValue.md)

      Returns:
      a BigInteger contains the chunk operation offset

    <!-- -->

    - #### getCharSetId

          public int getCharSetId()

      Gets the chunk character set identifier (ID) for an XMLTYPE chunk
      The character set ID indicates the character set used to interpret the XMLTYPE chunk data.
      Check oracle.sql.CharacterSet for the definition of Oracle CharacterSet Id.
      Specified by:
      [`getCharSetId`](ChunkColumnValue.md) in interface [`ChunkColumnValue`](ChunkColumnValue.md)

      Returns:
      An integer that indicates the character set

    <!-- -->

    - #### setChunkOffset

          public void setChunkOffset(java.math.BigInteger chunkOffset)

      Sets the chunk operation offset.
      Setting the chunk operation offset is required for a piecwise LOB operation in which the offset indicates the starting point for the LOB operation. The offset value starts at 1.
      Specified by:
      [`setChunkOffset`](ChunkColumnValue.md) in interface [`ChunkColumnValue`](ChunkColumnValue.md)

      Parameters:
      `chunkOffset` - The chunk operation offset

    <!-- -->

    - #### getChunkOperationSize

          public java.math.BigInteger getChunkOperationSize()

      Gets the chunk operation size.
      Use this method to obtain the size information for piecewise LOB operations. For DML operations, NULL is returned.
      Specified by:
      [`getChunkOperationSize`](ChunkColumnValue.md) in interface [`ChunkColumnValue`](ChunkColumnValue.md)

      Returns:
      A BigInteger contains the chunk operation size

    <!-- -->

    - #### setChunkOperationSize

          public void setChunkOperationSize(java.math.BigInteger chunkOperationSize)

      Sets the chunk operation size.
      Setting the chunk operation size is required for piecewise LOB ERASE and LOB TRIM operations. For LOB ERASE operations, the chunk operation size specifies the amount of data to erase. For LOB TRIM operations, the chunk operation size specified the amount of data to trim.
      Specified by:
      [`setChunkOperationSize`](ChunkColumnValue.md) in interface [`ChunkColumnValue`](ChunkColumnValue.md)

      Parameters:
      `chunkOperationSize` - The chunk operation size

    <!-- -->

    - #### isLastChunk

          public boolean isLastChunk()

      Indicates whether the chunk is the last one for the column.
      Specified by:
      [`isLastChunk`](ChunkColumnValue.md) in interface [`ChunkColumnValue`](ChunkColumnValue.md)

      Returns:
      a boolean flag indicates if this is the last chunk

    <!-- -->

    - #### isEmptyChunk

          public boolean isEmptyChunk()

      Indicates whether the chunk is empty. For a LOB column, an empty LOB is different from a column that contains a NULL.
      Specified by:
      [`isEmptyChunk`](ChunkColumnValue.md) in interface [`ChunkColumnValue`](ChunkColumnValue.md)

      Returns:
      a boolean flag indicates if this is an empty chunk

    <!-- -->

    - #### isXMLDiff

          public boolean isXMLDiff()

      Indicates whether the chunk is an XMLDiff.
      Specified by:
      [`isXMLDiff`](ChunkColumnValue.md) in interface [`ChunkColumnValue`](ChunkColumnValue.md)

      Returns:
      a boolean flag indicates if this is an XMLDiff

    <!-- -->

    - #### isEndOfRow

          public boolean isEndOfRow()

      Indicates whether the chunk is the end of the entire row change.
      A chunk is the end of the entire row change if it is the last chunk for the last column in an LCR.
      Specified by:
      [`isEndOfRow`](ChunkColumnValue.md) in interface [`ChunkColumnValue`](ChunkColumnValue.md)

      Returns:
      True if this is the end of row change.

    <!-- -->

    - #### setLastChunk

          public void setLastChunk(boolean lastChunk)

      Sets the last chunk flag.
      The last chunk flag indicates whether the chunk is the last one for the current column.
      Specified by:
      [`setLastChunk`](ChunkColumnValue.md) in interface [`ChunkColumnValue`](ChunkColumnValue.md)

      Parameters:
      `lastChunk` - The last chunk flag

    <!-- -->

    - #### setEmptyChunk

          public void setEmptyChunk(boolean emptyChunk)

      Sets the empty chunk flag.
      The empty chunk flag indicates if the chunk contains an empty LOB. For LOB columns, an empty LOB column is different from a column with a NULL value. Use this method to indicate whether the column contains an empty LOB.
      Specified by:
      [`setEmptyChunk`](ChunkColumnValue.md) in interface [`ChunkColumnValue`](ChunkColumnValue.md)

      Parameters:
      `emptyChunk` - The empty chunk flag

    <!-- -->

    - #### setXMLDiff

          public void setXMLDiff(boolean xmlDiff)

      Sets the XMLDiff flag.
      The XMLDiff flag indicates if the chunk contains an XMLDiff.
      Specified by:
      [`setXMLDiff`](ChunkColumnValue.md) in interface [`ChunkColumnValue`](ChunkColumnValue.md)

      Parameters:
      `xmlDiff` - The XMLDiff flag

    <!-- -->

    - #### setEndOfRow

          public void setEndOfRow(boolean endOfRow)

      Sets the endOfRow chunk flag.
      The endOfRow flag indicates whether the chunk is the last one for the last column in an LCR, which also indicates the end of the entire row change.
      Specified by:
      [`setEndOfRow`](ChunkColumnValue.md) in interface [`ChunkColumnValue`](ChunkColumnValue.md)

      Parameters:
      `endOfRow` - The endOfRow chunk flag

    <!-- -->

    - #### setCharSetId

          public void setCharSetId(int charSetId)

      Sets the character set ID for an XMLTYPE chunk.
      Check oracle.sql.CharacterSet for the definition of Oracle CharacterSet Id.
      Specified by:
      [`setCharSetId`](ChunkColumnValue.md) in interface [`ChunkColumnValue`](ChunkColumnValue.md)

      Parameters:
      `charSetId` - The character set id

    <!-- -->

    - #### toString

          public java.lang.String toString()

      Overrides:
      [`toString`](DefaultColumnValue.md) in class [`DefaultColumnValue`](DefaultColumnValue.md)

Skip navigation links

- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../deprecated-list.md)
- [Index](../../index-all.md)
- [Help](../../help-doc.md)

**Oracle® Database XStream Java API Reference
19c**
E96285-02

- [Prev Class](DDLLCR.md)
- [Next Class](DefaultColumnValue.md)

<!-- -->

- [Frames](../../index.md)
- No Frames

<!-- -->

- [All Classes](../../allclasses-noframe.md)

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

Copyright © 2001, 2019, Oracle and/or its affiliates. All Rights Reserved.
