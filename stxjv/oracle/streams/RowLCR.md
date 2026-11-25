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

- [Prev Class](LCR.md)
- [Next Class](StreamsException.md)

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

## Interface RowLCR

- All Superinterfaces:
  [LCR](LCR.md)

  <!-- -->

  All Known Implementing Classes:
  [DefaultRowLCR](DefaultRowLCR.md)

  ------------------------------------------------------------------------



      public interface RowLCR
      extends LCR

  The RowLCR interface encapsulates the information about a row logical change record (LCR). The row LCR is a logical change record that describes a change to the data in a single row that results from a data manipulation language (DML) statement or a piecewise LOB operation.
  You can choose to have a customized implementation of RowLCR by implementing this interface.
  See Also:
  [`AbstractLCR`](AbstractLCR.md), [`DDLLCR`](DDLLCR.md)

<!-- -->

- - ### Field Summary

    **Fields**

    | Modifier and Type         | Field and Description |
    |---------------------------|-----------------------|
    | `static java.lang.String` | `COMMIT`              |
    | `static java.lang.String` | `DELETE`              |
    | `static java.lang.String` | `INSERT`              |
    | `static java.lang.String` | `LOB_ERASE`           |
    | `static java.lang.String` | `LOB_TRIM`            |
    | `static java.lang.String` | `LOB_WRITE`           |
    | `static java.lang.String` | `UPDATE`              |

    - ### Fields inherited from interface oracle.streams.[LCR](LCR.md)

      [`ATTRIBUTE_ROOT_NAME`](LCR.md)`, `[`ATTRIBUTE_ROW_ID`](LCR.md)`, `[`ATTRIBUTE_SERIAL_NUM`](LCR.md)`, `[`ATTRIBUTE_SESSION_NUM`](LCR.md)`, `[`ATTRIBUTE_THREAD_NUM`](LCR.md)`, `[`ATTRIBUTE_TX_NAME`](LCR.md)`, `[`ATTRIBUTE_USERNAME`](LCR.md)

  <!-- -->

  - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Abstract Methods](javascript:show(4);)**

    | Modifier and Type                   | Method and Description                                                                                            |
    |-------------------------------------|-------------------------------------------------------------------------------------------------------------------|
    | [`ColumnValue`](ColumnValue.md)`[]` | `getNewValues``()`<br>Gets the list of new column values in a row LCR.                                            |
    | [`ColumnValue`](ColumnValue.md)`[]` | `getOldValues``()`<br>Gets the list of old column values in a row LCR.                                            |
    | `boolean`                           | `hasChunkData``()`<br>Indicates whether this LCR contains chunk data for LOB, LONG, or XMLTYPE columns.           |
    | `void`                              | `setChunkDataFlag``(boolean chunkDataFlag)`<br>Sets the chunkDataFlag.                                            |
    | `void`                              | `setNewValues``(`[`ColumnValue`](ColumnValue.md)`[] newValues)`<br>Sets the new column values list for a row LCR. |
    | `void`                              | `setOldValues``(`[`ColumnValue`](ColumnValue.md)`[] oldValues)`<br>Sets the old column values list for a row LCR. |

    - ### Methods inherited from interface oracle.streams.[LCR](LCR.md)

      [`getAttribute`](LCR.md)`, `[`getCommandType`](LCR.md)`, `[`getObjectName`](LCR.md)`, `[`getObjectOwner`](LCR.md)`, `[`getPosition`](LCR.md)`, `[`getSourceDatabaseName`](LCR.md)`, `[`getSourceTime`](LCR.md)`, `[`getTag`](LCR.md)`, `[`getTransactionId`](LCR.md)`, `[`setAttribute`](LCR.md)`, `[`setCommandType`](LCR.md)`, `[`setObjectName`](LCR.md)`, `[`setObjectOwner`](LCR.md)`, `[`setPosition`](LCR.md)`, `[`setSourceDatabaseName`](LCR.md)`, `[`setSourceTime`](LCR.md)`, `[`setTag`](LCR.md)`, `[`setTransactionId`](LCR.md)

<!-- -->

- - ### Field Detail

    - #### INSERT

          static final java.lang.String INSERT

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### UPDATE

          static final java.lang.String UPDATE

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### DELETE

          static final java.lang.String DELETE

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### COMMIT

          static final java.lang.String COMMIT

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### LOB_WRITE

          static final java.lang.String LOB_WRITE

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### LOB_ERASE

          static final java.lang.String LOB_ERASE

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### LOB_TRIM

          static final java.lang.String LOB_TRIM

      See Also:
      [Constant Field Values](../../constant-values.md)

  <!-- -->

  - ### Method Detail

    - #### getOldValues

          ColumnValue[] getOldValues()

      Gets the list of old column values in a row LCR.
      These are the column values for the row before the DML change.
      If the DML statement is an UPDATE or a DELETE statement, then this parameter contains the values of columns in the row before the DML statement.
      If the DML statement is an INSERT statement, then there are no old values and NULL is returned. Note that the returned ColumnValue\[\] is mutable.
      Returns:
      A ColumnValue array contains the old column value

    <!-- -->

    - #### getNewValues

          ColumnValue[] getNewValues()

      Gets the list of new column values in a row LCR.
      These are the column values for the row after the DML change.
      If the DML statement is an UPDATE or an INSERT statement, then this parameter contains the values of columns in the row after the DML statement.
      If the DML statement is a DELETE statement, then there are no new values and NULL is returned.
      Note that the returned ColumnValue\[\] is mutable.
      Returns:
      A ColumnValue array contains the new column value

    <!-- -->

    - #### setOldValues

          void setOldValues(ColumnValue[] oldValues)

      Sets the old column values list for a row LCR.
      If the DML statement is an UPDATE or a DELETE statement, then set this parameter to a non-NULL value.
      If the DML statement is an INSERT statement, then set this parameter to a NULL value.
      Parameters:
      `oldValues` - The old column value array

    <!-- -->

    - #### setNewValues

          void setNewValues(ColumnValue[] newValues)

      Sets the new column values list for a row LCR.
      If the DML statement is an UPDATE or an INSERT statement, then set this parameter to a non-NULL value.
      If the DML statement is a DELETE statement, then set this parameter to a NULL value.
      Parameters:
      `newValues` - The new column value array

    <!-- -->

    - #### hasChunkData

          boolean hasChunkData()

      Indicates whether this LCR contains chunk data for LOB, LONG, or XMLTYPE columns.
      If an LCR contains chunk data for LOB, LONG, or XMLTYPE columns and must use the XStreamOUT APIs for chunking, then call this method to check whether the LCR contains chunk data and invoke the XStreamOut APIs for chunking accordingly.
      Returns:
      A boolean flag indicates if this LCR contains chunk data.

    <!-- -->

    - #### setChunkDataFlag

          void setChunkDataFlag(boolean chunkDataFlag)

      Sets the chunkDataFlag.
      If an LCR contains chunk data for LOB, LONG, or XMLTYPE columns and must use the XStreamOUT APIs for chunking, then call this method to set the chunkDataFLag to true and invoke the XStreamOut APIs for chunking accordingly.
      Parameters:
      `chunkDataFlag` - indicates whether this LCR contains chunk data.

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

- [Prev Class](LCR.md)
- [Next Class](StreamsException.md)

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
