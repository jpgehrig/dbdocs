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

- [Prev Class](AbstractLCR.md)
- [Next Class](ColumnValue.md)

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

## Interface ChunkColumnValue

- All Superinterfaces:
  [ColumnValue](ColumnValue.md)

  <!-- -->

  All Known Implementing Classes:
  [DefaultChunkColumnValue](DefaultChunkColumnValue.md)

  ------------------------------------------------------------------------



      public interface ChunkColumnValue
      extends ColumnValue

  The ChunkColumnValue interface encapsulates the information about a LOB, LONG, or XMLTYPE column in a RowLCR. This interface allows large column data to be divided into small chunks and streamed.
  You can have a customized implementation of ChunkColumnValue by implementing this interface.
  See Also:
  [`RowLCR`](RowLCR.md)

<!-- -->

- - ### Field Summary

    **Fields**

    | Modifier and Type | Field and Description |
    |-------------------|-----------------------|
    | `static int`      | `BLOB`                |
    | `static int`      | `CLOB`                |
    | `static int`      | `LONG`                |
    | `static int`      | `LONGRAW`             |
    | `static int`      | `NCLOB`               |
    | `static int`      | `XMLTYPE`             |

    - ### Fields inherited from interface oracle.streams.[ColumnValue](ColumnValue.md)

      [`BINARY_DOUBLE`](ColumnValue.md)`, `[`BINARY_FLOAT`](ColumnValue.md)`, `[`CHAR`](ColumnValue.md)`, `[`DATE`](ColumnValue.md)`, `[`INTERVALDS`](ColumnValue.md)`, `[`INTERVALYM`](ColumnValue.md)`, `[`NUMBER`](ColumnValue.md)`, `[`RAW`](ColumnValue.md)`, `[`TIMESTAMP`](ColumnValue.md)`, `[`TIMESTAMPLTZ`](ColumnValue.md)`, `[`TIMESTAMPTZ`](ColumnValue.md)

  <!-- -->

  - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Abstract Methods](javascript:show(4);)**

    | Modifier and Type      | Method and Description                                                                               |
    |------------------------|------------------------------------------------------------------------------------------------------|
    | `int`                  | `getCharSetId``()`<br>Gets the chunk character set ID.                                               |
    | `java.math.BigInteger` | `getChunkOffset``()`<br>Gets the chunk operation offset.                                             |
    | `java.math.BigInteger` | `getChunkOperationSize``()`<br>Gets the chunk operation size.                                        |
    | `int`                  | `getChunkType``()`<br>Gets the chunk type.                                                           |
    | `boolean`              | `isEmptyChunk``()`<br>Indicates whether the chunk is empty.                                          |
    | `boolean`              | `isEndOfRow``()`<br>Indicates whether the chunk is the end of the entire row change.                 |
    | `boolean`              | `isLastChunk``()`<br>Indicates whether the chunk is the last one for the column.                     |
    | `boolean`              | `isXMLDiff``()`<br>Indicates whether the XMLType chunk is an XMLDiff.                                |
    | `void`                 | `setCharSetId``(int charSetId)`<br>Sets the character set ID for an XMLTYPE chunk.                   |
    | `void`                 | `setChunkOffset``(java.math.BigInteger chunkOffset)`<br>Sets the chunk operation offset.             |
    | `void`                 | `setChunkOperationSize``(java.math.BigInteger chunkOperationSize)`<br>Sets the chunk operation size. |
    | `void`                 | `setChunkType``(int chunkType)`<br>Sets the chunk type.                                              |
    | `void`                 | `setEmptyChunk``(boolean emptyChunk)`<br>Sets the empty chunk flag.                                  |
    | `void`                 | `setEndOfRow``(boolean endOfRow)`<br>Sets the endOfRow chunk flag.                                   |
    | `void`                 | `setLastChunk``(boolean lastChunk)`<br>Sets the last chunk flag.                                     |
    | `void`                 | `setXMLDiff``(boolean xmlDiff)`<br>Sets the XMLDiff flag.                                            |

    - ### Methods inherited from interface oracle.streams.[ColumnValue](ColumnValue.md)

      [`getCharsetId`](ColumnValue.md)`, `[`getColumnData`](ColumnValue.md)`, `[`getColumnDataType`](ColumnValue.md)`, `[`getColumnName`](ColumnValue.md)`, `[`getTDEFlag`](ColumnValue.md)`, `[`is32kData`](ColumnValue.md)`, `[`set32kData`](ColumnValue.md)`, `[`setCharsetId`](ColumnValue.md)`, `[`setColumnData`](ColumnValue.md)`, `[`setColumnName`](ColumnValue.md)`, `[`setTDEFlag`](ColumnValue.md)

<!-- -->

- - ### Field Detail

    - #### CLOB

          static final int CLOB

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### BLOB

          static final int BLOB

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### NCLOB

          static final int NCLOB

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### XMLTYPE

          static final int XMLTYPE

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### LONG

          static final int LONG

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### LONGRAW

          static final int LONGRAW

      See Also:
      [Constant Field Values](../../constant-values.md)

  <!-- -->

  - ### Method Detail

    - #### getChunkType

          int getChunkType()

      Gets the chunk type.
      The chunk type indicates the type of the column that contains data that can be split into multiple chunks. Valid values are: BLOB, CLOB, NCLOB, and XMLTYPE.
      Returns:
      an integer that contains the chunk type as defined in this interface

    <!-- -->

    - #### getChunkOffset

          java.math.BigInteger getChunkOffset()

      Gets the chunk operation offset.
      This method obtains the offset information for piecewise LOB operations. For DML operations, NULL is returned.
      If there are multiple chunks for one LOB WRITE operation, then only the offset of the first chunk is relevant.
      Returns:
      a BigInteger that contains the chunk operation offset

    <!-- -->

    - #### getChunkOperationSize

          java.math.BigInteger getChunkOperationSize()

      Gets the chunk operation size.
      This method obtains the size information for piecewise LOB operations LOB TRIM and LOB ERASE. For other operations, NULL is returned.
      The chunk operation size is the number of bytes(for BLOBs) or characters (for CLOBs or NCLOBs).
      Returns:
      a BigInteger that contains the chunk operation size

    <!-- -->

    - #### getCharSetId

          int getCharSetId()

      Gets the chunk character set ID. This is only for XMLTTPE chunk
      The character set ID indicates the character set used to interpret the XMLTYPE chunk data.
      Check oracle.sql.CharacterSet for definition of Oracle CharacterSet ID.
      Returns:
      an integer that indicates the character set

    <!-- -->

    - #### setChunkType

          void setChunkType(int chunkType)
                     throws StreamsException

      Sets the chunk type.
      The chunk type specifies the type of the column that contains data that can be split into mutliple chunks. Valid values are: BLOB, CLOB, NCLOB, and XMLTYPE.
      Parameters:
      `chunkType` - The chunk type as defined in this interface

      Throws:
      [`StreamsException`](StreamsException.md) - is thrown if chunk type is invalid.

    <!-- -->

    - #### setChunkOffset

          void setChunkOffset(java.math.BigInteger chunkOffset)

      Sets the chunk operation offset.
      Use this method for a piecewise LOB operation in which the operation offset indicates the starting point for the LOB operation. The offset value starts from 1.
      Parameters:
      `chunkOffset` - The chunk operation offset

    <!-- -->

    - #### setChunkOperationSize

          void setChunkOperationSize(java.math.BigInteger chunkOperationSize)

      Sets the chunk operation size.
      Use this method for a piecewise LOB operation where the size is the amount of data to be erased in the case of LOB ERASE or the trim size in the case of LOB TRIM. The chunk operation size is the number of bytes(for BLOBs) or characters (for CLOBs and NCLOBs).
      Parameters:
      `chunkOperationSize` - The chunk operation size

    <!-- -->

    - #### isLastChunk

          boolean isLastChunk()

      Indicates whether the chunk is the last one for the column.
      Returns:
      a boolean flag indicates if this is the last chunk

    <!-- -->

    - #### isEmptyChunk

          boolean isEmptyChunk()

      Indicates whether the chunk is empty. For a LOB column, an empty LOB is different than a column containing NULL value.
      Returns:
      a boolean flag indicates if this is an empty chunk

    <!-- -->

    - #### isXMLDiff

          boolean isXMLDiff()

      Indicates whether the XMLType chunk is an XMLDiff.
      Returns:
      a boolean flag indicates if this is an XMLDiff.

    <!-- -->

    - #### isEndOfRow

          boolean isEndOfRow()

      Indicates whether the chunk is the end of the entire row change.
      This indicates if the chunk is the last chunk for the last column in an LCR.
      Returns:
      a boolean flag indicates if this is the end of row change.

    <!-- -->

    - #### setEmptyChunk

          void setEmptyChunk(boolean emptyChunk)

      Sets the empty chunk flag.
      This flag indicates whether the chunk contains an empty LOB. For a LOB column, an empty LOB is different than a NULL value. Use this method to indicate whether this column contains an empty LOB.
      Parameters:
      `emptyChunk` - The empty chunk flag

    <!-- -->

    - #### setXMLDiff

          void setXMLDiff(boolean xmlDiff)

      Sets the XMLDiff flag.
      This flag indicates whether the XMLType chunk is an XMLDiff.
      Parameters:
      `xmlDiff` - The XMLDiff flag

    <!-- -->

    - #### setLastChunk

          void setLastChunk(boolean lastChunk)

      Sets the last chunk flag.
      This flag indicates whether the chunk is the last one for the current column.
      Parameters:
      `lastChunk` - The last chunk flag

    <!-- -->

    - #### setEndOfRow

          void setEndOfRow(boolean endOfRow)

      Sets the endOfRow chunk flag.
      This flag indicates whether the chunk is the last one for the last column in an LCR, which also indicates the end of entire row change.
      Parameters:
      `endOfRow` - The endOfRow chunk flag

    <!-- -->

    - #### setCharSetId

          void setCharSetId(int charSetId)

      Sets the character set ID for an XMLTYPE chunk.
      Check oracle.sql.CharacterSet for definition of Oracle CharacterSet ID.
      Parameters:
      `charSetId` - The character set id

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

- [Prev Class](AbstractLCR.md)
- [Next Class](ColumnValue.md)

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
