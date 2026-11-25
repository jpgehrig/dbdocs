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

- [Prev Class](ChunkColumnValue.md)
- [Next Class](DDLLCR.md)

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

## Interface ColumnValue

- All Known Subinterfaces:
  [ChunkColumnValue](ChunkColumnValue.md)

  <!-- -->

  All Known Implementing Classes:
  [DefaultChunkColumnValue](DefaultChunkColumnValue.md), [DefaultColumnValue](DefaultColumnValue.md)

  ------------------------------------------------------------------------



      public interface ColumnValue

  The ColumnValue interface encapsulates the information about a column in a RowLCR. The column data is in the form of oracle.sql.Datum.
  You can have a customized implementation of ColumnValue by using this interface.
  See Also:
  [`RowLCR`](RowLCR.md)

<!-- -->

- - ### Field Summary

    **Fields**

    | Modifier and Type | Field and Description |
    |-------------------|-----------------------|
    | `static int`      | `BINARY_DOUBLE`       |
    | `static int`      | `BINARY_FLOAT`        |
    | `static int`      | `CHAR`                |
    | `static int`      | `DATE`                |
    | `static int`      | `INTERVALDS`          |
    | `static int`      | `INTERVALYM`          |
    | `static int`      | `NUMBER`              |
    | `static int`      | `RAW`                 |
    | `static int`      | `TIMESTAMP`           |
    | `static int`      | `TIMESTAMPLTZ`        |
    | `static int`      | `TIMESTAMPTZ`         |

  <!-- -->

  - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Abstract Methods](javascript:show(4);)**

    | Modifier and Type  | Method and Description                                                                                    |
    |--------------------|-----------------------------------------------------------------------------------------------------------|
    | `int`              | `getCharsetId``()`<br>Gets the column character set identifier (ID).                                      |
    | `oracle.sql.Datum` | `getColumnData``()`<br>Gets the column data.                                                              |
    | `int`              | `getColumnDataType``()`<br>Gets the column data type as defined in this interface.                        |
    | `java.lang.String` | `getColumnName``()`<br>Gets the column name.                                                              |
    | `boolean`          | `getTDEFlag``()`<br>Gets the Transparent Data Encryption (TDE) flag.                                      |
    | `boolean`          | `is32kData``()`<br>Indicates whether the column is an extended size column (maximum size of 32767 bytes). |
    | `void`             | `set32kData``(boolean is32kData)`<br>Sets the extended size column flag (maximum size of 32767 bytes).    |
    | `void`             | `setCharsetId``(int charsetId)`<br>Sets the Oracle character set ID for the column.                       |
    | `void`             | `setColumnData``(oracle.sql.Datum columnData, int columnDataType)`<br>Sets the column data.               |
    | `void`             | `setColumnName``(java.lang.String columnName)`<br>Sets the column name.                                   |
    | `void`             | `setTDEFlag``(boolean tdeFlag)`<br>Sets the Transparent Data Encryption (TDE) flag.                       |

<!-- -->

- - ### Field Detail

    - #### CHAR

          static final int CHAR

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### NUMBER

          static final int NUMBER

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### DATE

          static final int DATE

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### RAW

          static final int RAW

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### TIMESTAMP

          static final int TIMESTAMP

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### TIMESTAMPTZ

          static final int TIMESTAMPTZ

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### TIMESTAMPLTZ

          static final int TIMESTAMPLTZ

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### BINARY_FLOAT

          static final int BINARY_FLOAT

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### BINARY_DOUBLE

          static final int BINARY_DOUBLE

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### INTERVALYM

          static final int INTERVALYM

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### INTERVALDS

          static final int INTERVALDS

      See Also:
      [Constant Field Values](../../constant-values.md)

  <!-- -->

  - ### Method Detail

    - #### getColumnName

          java.lang.String getColumnName()

      Gets the column name.
      Returns:
      a string contains the column name.

    <!-- -->

    - #### setColumnName

          void setColumnName(java.lang.String columnName)

      Sets the column name.
      Set this parameter to a non-NULL value.
      Parameters:
      `columnName` - The column name.

    <!-- -->

    - #### getColumnData

          oracle.sql.Datum getColumnData()

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
      Returns:
      a oracle.sql.Datum object contains the column data.

    <!-- -->

    - #### setColumnData

          void setColumnData(oracle.sql.Datum columnData,
                             int columnDataType)
                      throws StreamsException

      Sets the column data.
      When columnData is NULL, a valid columnDataType is expected. When columnData is not NULL, the columnDataType is ignored and the mapping is maintained internally.
      Parameters:
      `columnData` - The column data, an instance of oracle.sql.Datum subclass.

      `columnDataType` - The column data type as defined in this class.

      Throws:
      [`StreamsException`](StreamsException.md) - a StreamsException is thrown if the columnData is NULL and columnDataType is invalid.

    <!-- -->

    - #### getColumnDataType

          int getColumnDataType()

      Gets the column data type as defined in this interface.
      See the Oracle JDBC documentation for information about mapping between SQL data types and Oracle extensions.
      Returns:
      an interger that indicates the column data type.

    <!-- -->

    - #### getTDEFlag

          boolean getTDEFlag()

      Gets the Transparent Data Encryption (TDE) flag. This flag indicates whether TDE was enabled for this column.
      Returns:
      a boolean value indicates whether TDE was enabled.

    <!-- -->

    - #### setTDEFlag

          void setTDEFlag(boolean tdeFlag)

      Sets the Transparent Data Encryption (TDE) flag. This method sets the Transparent Data Encryption (TDE) flag for the column. When this flag is set, the column data is encrypted if the LCR is spilled or placed into an error queue.
      Parameters:
      `tdeFlag` - a boolean value indicates whether TDE Flag should be set.

    <!-- -->

    - #### is32kData

          boolean is32kData()

      Indicates whether the column is an extended size column (maximum size of 32767 bytes).
      Returns:
      a boolean flag that indicates if the column is an extended size column.

    <!-- -->

    - #### set32kData

          void set32kData(boolean is32kData)

      Sets the extended size column flag (maximum size of 32767 bytes).
      This flag indicates whether the column is an extended size column.
      Parameters:
      `is32kData` - The extended size column flag.

    <!-- -->

    - #### setCharsetId

          void setCharsetId(int charsetId)

      Sets the Oracle character set ID for the column.
      In a case such as an XMLTYPE column, the column contains character data but is stored in raw byte format (oracle.sql.RAW). The character set ID is required to interpret the character data properly.
      Parameters:
      `charsetId` - The character set ID

      See Also:
      `CharacterSet`

    <!-- -->

    - #### getCharsetId

          int getCharsetId()

      Gets the column character set identifier (ID).
      In a case such as an XMLTYPE column, the column contains character data but is stored in raw byte format (oracle.sql.RAW). The character set ID is required to interpret the character data properly.
      Returns:
      an interger that identifies the character set .

      See Also:
      `CharacterSet`

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

- [Prev Class](ChunkColumnValue.md)
- [Next Class](DDLLCR.md)

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
