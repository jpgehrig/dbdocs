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

- [Prev Class](DefaultChunkColumnValue.md)
- [Next Class](DefaultDDLLCR.md)

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

## Class DefaultColumnValue

- java.lang.Object

- - oracle.streams.DefaultColumnValue

<!-- -->

- All Implemented Interfaces:
  [ColumnValue](ColumnValue.md)

  <!-- -->

  Direct Known Subclasses:
  [DefaultChunkColumnValue](DefaultChunkColumnValue.md)

  ------------------------------------------------------------------------



      public class DefaultColumnValue
      extends java.lang.Object
      implements ColumnValue

  The DefaultColumnValue class provides an Oracle default implementation of ColumnValue interface.
  See Also:
  [`RowLCR`](RowLCR.md)

<!-- -->

- - ### Field Summary

    - ### Fields inherited from interface oracle.streams.[ColumnValue](ColumnValue.md)

      [`BINARY_DOUBLE`](ColumnValue.md)`, `[`BINARY_FLOAT`](ColumnValue.md)`, `[`CHAR`](ColumnValue.md)`, `[`DATE`](ColumnValue.md)`, `[`INTERVALDS`](ColumnValue.md)`, `[`INTERVALYM`](ColumnValue.md)`, `[`NUMBER`](ColumnValue.md)`, `[`RAW`](ColumnValue.md)`, `[`TIMESTAMP`](ColumnValue.md)`, `[`TIMESTAMPLTZ`](ColumnValue.md)`, `[`TIMESTAMPTZ`](ColumnValue.md)

  <!-- -->

  - ### Constructor Summary

    **Constructors**

    | Constructor and Description                                                                                                                                                                                                                                     |
    |-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `DefaultColumnValue``(java.lang.String columnName, oracle.sql.Datum columnData)`<br>Constructs a DefaultColumnValue object with columnName and columnData.<br>This constructor can be used when columnData is not null.                                         |
    | `DefaultColumnValue``(java.lang.String columnName, oracle.sql.Datum columnData, int columnDataType)`<br>Constructs a DefaultColumnValue object with columnName, columnData, and columnDataType.<br>When columnData is NULL, a valid columnDataType is expected. |

  <!-- -->

  - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type  | Method and Description                                                                                    |
    |--------------------|-----------------------------------------------------------------------------------------------------------|
    | `int`              | `getCharsetId``()`<br>Gets the column character set identifier (ID).                                      |
    | `oracle.sql.Datum` | `getColumnData``()`<br>Gets the column data.                                                              |
    | `int`              | `getColumnDataType``()`<br>Gets the column data type as defined in ColumnValue interface.                 |
    | `java.lang.String` | `getColumnName``()`<br>Gets the column name.                                                              |
    | `boolean`          | `getTDEFlag``()`<br>Gets the Transparent Data Encryption (TDE) flag.                                      |
    | `boolean`          | `is32kData``()`<br>Indicates whether the column is an extended size column (maximum size of 32767 bytes). |
    | `void`             | `set32kData``(boolean is32kData)`<br>Sets the extended size column flag (maximum size of 32767 bytes).    |
    | `void`             | `setCharsetId``(int charsetId)`<br>Sets the Oracle character set ID for the column.                       |
    | `void`             | `setColumnData``(oracle.sql.Datum columnData, int columnDataType)`<br>Sets the column data.               |
    | `void`             | `setColumnName``(java.lang.String columnName)`<br>Sets the column name.                                   |
    | `void`             | `setTDEFlag``(boolean tdeFlag)`<br>Sets the TDE flag.                                                     |
    | `java.lang.String` | `toString``()`                                                                                            |

    - ### Methods inherited from class java.lang.Object

      `equals, getClass, hashCode, notify, notifyAll, wait, wait, wait`

<!-- -->

- - ### Constructor Detail

    - #### DefaultColumnValue

          public DefaultColumnValue(java.lang.String columnName,
                                    oracle.sql.Datum columnData,
                                    int columnDataType)
                             throws StreamsException

      Constructs a DefaultColumnValue object with columnName, columnData, and columnDataType.
      When columnData is NULL, a valid columnDataType is expected. When columnData is not NULL, the columnDataType is ignored. The mapping is maintained internally.
      Parameters:
      `columnName` - The column name, cannot be NULL

      `columnData` - The column data.

      `columnDataType` - The column data type.

      Throws:
      [`StreamsException`](StreamsException.md) - is thrown if the columnName is NULL, or the columnData is NULL and the columnDataType is invalid

    <!-- -->

    - #### DefaultColumnValue

          public DefaultColumnValue(java.lang.String columnName,
                                    oracle.sql.Datum columnData)
                             throws StreamsException

      Constructs a DefaultColumnValue object with columnName and columnData.
      This constructor can be used when columnData is not null. The mapping between columnData and columnDataType is maintained internally.
      Parameters:
      `columnName` - the column name, cannot be NULL.

      `columnData` - the column data, cannot be NULL.

      Throws:
      [`StreamsException`](StreamsException.md) - is thrown if the columnData is NULL and the columnDataType is invalid.

  <!-- -->

  - ### Method Detail

    - #### getColumnName

          public java.lang.String getColumnName()

      Gets the column name.
      Specified by:
      [`getColumnName`](ColumnValue.md) in interface [`ColumnValue`](ColumnValue.md)

      Returns:
      A string contains the column name.

    <!-- -->

    - #### setColumnName

          public void setColumnName(java.lang.String columnName)

      Sets the column name.
      Specified by:
      [`setColumnName`](ColumnValue.md) in interface [`ColumnValue`](ColumnValue.md)

      Parameters:
      `columnName` - The column name.

    <!-- -->

    - #### getColumnData

          public oracle.sql.Datum getColumnData()

      Gets the column data.
      Column data can be an instance of one of the following oracle.sql.Datum subclasses:
      oracle.sql.CHAR
      oracle.sql.RAW
      oracle.sql.DATE
      oracle.sql.NUMBER
      oracle.sql.BINARY_FLOAT
      oracle.sql.BINARY_DOUBLE
      oracle.sql.TIMESTAMP
      oracle.sql.TIMESTAMPTZ
      oracle.sql.TIMESTAMPLTZ
      oracle.sql.INTERVALYM
      oracle.sql.INTERVALDS
      Specified by:
      [`getColumnData`](ColumnValue.md) in interface [`ColumnValue`](ColumnValue.md)

      Returns:
      A oracle.sql.Datum object that contains the column data.

    <!-- -->

    - #### setColumnData

          public void setColumnData(oracle.sql.Datum columnData,
                                    int columnDataType)
                             throws StreamsException

      Sets the column data.
      When columnData is NULL, columnDataType must be a valid non-NULL value. When columnData is non-NULL, the columnDataType is ignored. The mapping is maintained internally.
      Specified by:
      [`setColumnData`](ColumnValue.md) in interface [`ColumnValue`](ColumnValue.md)

      Parameters:
      `columnData` - the column data, instance of oracle.sql.Datum subclasses.

      `columnDataType` - the column data type as defined in ColumnValue.

      Throws:
      [`StreamsException`](StreamsException.md) - is thrown if the columnData is NULL and the columnDataType is invalid.

    <!-- -->

    - #### getColumnDataType

          public int getColumnDataType()

      Gets the column data type as defined in ColumnValue interface.
      Specified by:
      [`getColumnDataType`](ColumnValue.md) in interface [`ColumnValue`](ColumnValue.md)

      Returns:
      an integer that indicates the column data type.

    <!-- -->

    - #### getTDEFlag

          public boolean getTDEFlag()

      Gets the Transparent Data Encryption (TDE) flag. This flag indicates whether TDE was enabled for this column.
      Specified by:
      [`getTDEFlag`](ColumnValue.md) in interface [`ColumnValue`](ColumnValue.md)

      Returns:
      A boolean value indicates whether TDE was enabled.

    <!-- -->

    - #### setTDEFlag

          public void setTDEFlag(boolean tdeFlag)

      Sets the TDE flag. This method is used to set the TDE flag for the column. When this flag is set, the column data is encrypted if the LCR is spilled or put into an error queue.
      Specified by:
      [`setTDEFlag`](ColumnValue.md) in interface [`ColumnValue`](ColumnValue.md)

      Parameters:
      `tdeFlag` - A boolean value indicates whether TDE Flag should be set.

    <!-- -->

    - #### is32kData

          public boolean is32kData()

      Indicates whether the column is an extended size column (maximum size of 32767 bytes).
      Specified by:
      [`is32kData`](ColumnValue.md) in interface [`ColumnValue`](ColumnValue.md)

      Returns:
      a boolean flag that indicates if the column is an extended size column.

    <!-- -->

    - #### set32kData

          public void set32kData(boolean is32kData)

      Sets the extended size column flag (maximum size of 32767 bytes).
      This flag indicates whether the column is an extended size column.
      Specified by:
      [`set32kData`](ColumnValue.md) in interface [`ColumnValue`](ColumnValue.md)

      Parameters:
      `is32kData` - The extended size column flag.

    <!-- -->

    - #### setCharsetId

          public void setCharsetId(int charsetId)

      Sets the Oracle character set ID for the column.
      Some types of columns, such as XMLTYPE columns, contain character data stored in raw byte format (oracle.sql.RAW). The character set ID is required to interpret the character data properly.
      Specified by:
      [`setCharsetId`](ColumnValue.md) in interface [`ColumnValue`](ColumnValue.md)

      Parameters:
      `charsetId` - The character set ID.

      See Also:
      `CharacterSet`

    <!-- -->

    - #### getCharsetId

          public int getCharsetId()

      Gets the column character set identifier (ID).
      Some types of columns, such as XMLTYPE columns, contain character data stored in raw byte format (oracle.sql.RAW). The character set ID is required to interpret the character data properly.
      Specified by:
      [`getCharsetId`](ColumnValue.md) in interface [`ColumnValue`](ColumnValue.md)

      Returns:
      An interger that identifies the character set.

      See Also:
      `CharacterSet`

    <!-- -->

    - #### toString

          public java.lang.String toString()

      Overrides:
      `toString` in class `java.lang.Object`

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

- [Prev Class](DefaultChunkColumnValue.md)
- [Next Class](DefaultDDLLCR.md)

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
