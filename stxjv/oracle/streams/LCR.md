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

- [Prev Class](DefaultRowLCR.md)
- [Next Class](RowLCR.md)

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

## Interface LCR

- All Known Subinterfaces:
  [DDLLCR](DDLLCR.md), [RowLCR](RowLCR.md)

  <!-- -->

  All Known Implementing Classes:
  [AbstractLCR](AbstractLCR.md), [DefaultDDLLCR](DefaultDDLLCR.md), [DefaultRowLCR](DefaultRowLCR.md)

  ------------------------------------------------------------------------



      public interface LCR

  The LCR interface encapsulates information about the logical change record (LCR). An LCR describes a database change, either a data definition language (DDL) change or a change to the data in a single row that results from a data manipulation language (DML) statement or a LOB piecewise operation. Users can choose to have a customized implementation of LCR by implementing this interface.
  Note that the LCR attributes obtained from get methods are mutable. Please refer to Oracle Streams documentations for more information about LCR attributes.

  See Also:
  [`AbstractLCR`](AbstractLCR.md), [`RowLCR`](RowLCR.md), [`DDLLCR`](DDLLCR.md)

<!-- -->

- - ### Field Summary

    **Fields**

    | Modifier and Type         | Field and Description                                                                                              |
    |---------------------------|--------------------------------------------------------------------------------------------------------------------|
    | `static java.lang.String` | `ATTRIBUTE_ROOT_NAME`<br>The name of the root container in a consolidated database.                                |
    | `static java.lang.String` | `ATTRIBUTE_ROW_ID`<br>The rowid of the row changed in a row LCR.                                                   |
    | `static java.lang.String` | `ATTRIBUTE_SERIAL_NUM`<br>The serial number of the session that performed the change captured in the LCR.          |
    | `static java.lang.String` | `ATTRIBUTE_SESSION_NUM`<br>The identifier of the session that performed the change captured in the LCR.            |
    | `static java.lang.String` | `ATTRIBUTE_THREAD_NUM`<br>The thread number of the instance in which the change captured in the LCR was performed. |
    | `static java.lang.String` | `ATTRIBUTE_TX_NAME`<br>The name of the transaction that includes the LCR.                                          |
    | `static java.lang.String` | `ATTRIBUTE_USERNAME`<br>The name of the current user who performed the change captured in the LCR.                 |

  <!-- -->

  - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Abstract Methods](javascript:show(4);)**

    | Modifier and Type  | Method and Description                                                                                                                                                      |
    |--------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `java.lang.Object` | `getAttribute``(java.lang.Object attributeName)`<br>Gets the attribute by specifying the attribute name.                                                                    |
    | `java.lang.String` | `getCommandType``()`<br>Gets the LCR command type executed in the DML or DDL statement.                                                                                     |
    | `java.lang.String` | `getObjectName``()`<br>Gets the name of the object that is changed by the LCR.                                                                                              |
    | `java.lang.String` | `getObjectOwner``()`<br>Gets the owner of the object that is changed by the LCR.                                                                                            |
    | `byte[]`           | `getPosition``()`<br>Gets the position of the current LCR.                                                                                                                  |
    | `java.lang.String` | `getSourceDatabaseName``()`<br>Gets the global name of the source database.                                                                                                 |
    | `oracle.sql.DATE`  | `getSourceTime``()`<br>Gets the time when the LCR was created.                                                                                                              |
    | `byte[]`           | `getTag``()`<br>Gets the tag for the LCR.                                                                                                                                   |
    | `java.lang.String` | `getTransactionId``()`<br>Gets the transaction identifier of the LCR.                                                                                                       |
    | `void`             | `setAttribute``(java.lang.Object attributeName, java.lang.Object attributeValue)`<br>Sets attribute by providing the name and value pair; the name is used as the hash key. |
    | `void`             | `setCommandType``(java.lang.String commandType)`<br>Sets the command type in the LCR.                                                                                       |
    | `void`             | `setObjectName``(java.lang.String objectName)`<br>Sets the name of the object that is changed by the LCR.                                                                   |
    | `void`             | `setObjectOwner``(java.lang.String objectOwner)`<br>Sets the owner of the object that is changed by the LCR .                                                               |
    | `void`             | `setPosition``(byte[] position)`<br>Sets the position in the LCR.                                                                                                           |
    | `void`             | `setSourceDatabaseName``(java.lang.String name)`<br>Sets the source database name of the object that is changed by the LCR.                                                 |
    | `void`             | `setSourceTime``(oracle.sql.DATE sourceTime)`<br>Sets the source timestamp when the LCR was created.                                                                        |
    | `void`             | `setTag``(byte[] tag)`<br>Sets the tag for the LCR.                                                                                                                         |
    | `void`             | `setTransactionId``(java.lang.String transactionId)`<br>Sets the transaction identifier for the LCR.                                                                        |

<!-- -->

- - ### Field Detail

    - #### ATTRIBUTE_THREAD_NUM

          static final java.lang.String ATTRIBUTE_THREAD_NUM

      The thread number of the instance in which the change captured in the LCR was performed. Typically, the thread number is relevant only in an Oracle Real Application Clusters (Oracle RAC) environment. The type is oracle.sql.NUMBER.
      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### ATTRIBUTE_SESSION_NUM

          static final java.lang.String ATTRIBUTE_SESSION_NUM

      The identifier of the session that performed the change captured in the LCR. The type is oracle.sql.NUMBER.
      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### ATTRIBUTE_SERIAL_NUM

          static final java.lang.String ATTRIBUTE_SERIAL_NUM

      The serial number of the session that performed the change captured in the LCR. The type is oracle.sql.NUMBER.
      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### ATTRIBUTE_ROW_ID

          static final java.lang.String ATTRIBUTE_ROW_ID

      The rowid of the row changed in a row LCR. This attribute is not included in DDL LCRs, nor in row LCRs for index-organized tables. The type is oracle.sql.CHAR.
      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### ATTRIBUTE_USERNAME

          static final java.lang.String ATTRIBUTE_USERNAME

      The name of the current user who performed the change captured in the LCR. The type is oracle.sql.CHAR.
      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### ATTRIBUTE_TX_NAME

          static final java.lang.String ATTRIBUTE_TX_NAME

      The name of the transaction that includes the LCR. The type is oracle.sql.CHAR.
      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### ATTRIBUTE_ROOT_NAME

          static final java.lang.String ATTRIBUTE_ROOT_NAME

      The name of the root container in a consolidated database. The type is oracle.sql.CHAR.
      See Also:
      [Constant Field Values](../../constant-values.md)

  <!-- -->

  - ### Method Detail

    - #### setSourceDatabaseName

          void setSourceDatabaseName(java.lang.String name)

      Sets the source database name of the object that is changed by the LCR.

      The source database is the database where the change originated.
      Parameters:
      `name` - The source database name in String format. Set this parameter to a non-NULL value.

    <!-- -->

    - #### setCommandType

          void setCommandType(java.lang.String commandType)

      Sets the command type in the LCR.
      See Oracle Call Interface reference manual for complete command type definition.

      Parameters:
      `commandType` - The command type of an LCR. Set this parameter to a non-NULL value.

    <!-- -->

    - #### setObjectOwner

          void setObjectOwner(java.lang.String objectOwner)

      Sets the owner of the object that is changed by the LCR .
      Parameters:
      `objectOwner` - The object owner. Set this parameter to a non-NULL value.

    <!-- -->

    - #### setObjectName

          void setObjectName(java.lang.String objectName)

      Sets the name of the object that is changed by the LCR.
      Parameters:
      `objectName` - The name of the database object. Set this parameter to a non-NULL value.

    <!-- -->

    - #### setTag

          void setTag(byte[] tag)

      Sets the tag for the LCR.
      A binary tag that enables tracking of the LCR. For example, this tag can be used to determine the original source database of the DML or DDL statement when apply forwarding is used.
      See Oracle Streams Replication Administrator's Guide for more information about tags
      Parameters:
      `tag` - A binary tag that enables tracking of the LCR

    <!-- -->

    - #### setPosition

          void setPosition(byte[] position)

      Sets the position in the LCR.
      The position uniquely identifies each LCR in an LCR stream.
      Parameters:
      `position` - A byte array that represents the LCR position. Set this parameter to a non-NULL value and ensure that the position is byte comparable and is strictly increasing.

    <!-- -->

    - #### setTransactionId

          void setTransactionId(java.lang.String transactionId)

      Sets the transaction identifier for the LCR.
      See Oracle Call Interface reference manual for the format of transactionId.
      Parameters:
      `transactionId` - The identifier of the transaction

    <!-- -->

    - #### setSourceTime

          void setSourceTime(oracle.sql.DATE sourceTime)

      Sets the source timestamp when the LCR was created.
      The source time is the time when the change in an LCR captured by a capture process was generated in the redo log of the source database, or the time when a persistent LCR was created.
      Parameters:
      `sourceTime` - The srouce time in the form of oracle.sql.DATE

    <!-- -->

    - #### setAttribute

          void setAttribute(java.lang.Object attributeName,
                            java.lang.Object attributeValue)

      Sets attribute by providing the name and value pair; the name is used as the hash key.
      This method is used to set the attributes in an LCR. See valid attribute names defined in this class.
      Parameters:
      `attributeName` - The name of the attribute

      `attributeValue` - The value of the attribute

    <!-- -->

    - #### getSourceDatabaseName

          java.lang.String getSourceDatabaseName()

      Gets the global name of the source database.
      The source database is the database where the change originated.
      Returns:
      A string containing source database name

    <!-- -->

    - #### getCommandType

          java.lang.String getCommandType()

      Gets the LCR command type executed in the DML or DDL statement.
      See Oracle Call Interface reference manual for complete command type definition.

      Returns:
      A string containing comand type

    <!-- -->

    - #### getObjectOwner

          java.lang.String getObjectOwner()

      Gets the owner of the object that is changed by the LCR.
      The owner is the user who owns the object on which the row change ocurred or the DDL statement was executed.
      Returns:
      A string containing the owner

    <!-- -->

    - #### getObjectName

          java.lang.String getObjectName()

      Gets the name of the object that is changed by the LCR.
      The name of the database object on which the DDL or DML statement was executed.
      Returns:
      A string containing the name

    <!-- -->

    - #### getTag

          byte[] getTag()

      Gets the tag for the LCR.
      A binary tag that enables tracking of the LCR. For example, this tag can be used to determine the original source database of the DML or DDL statement when apply forwarding is used.
      Returns:
      A byte array that represents the tag

    <!-- -->

    - #### getPosition

          byte[] getPosition()

      Gets the position of the current LCR.
      A byte array that uniquely identifies an LCR in the stream and is in strictly increasing order.
      Returns:
      A byte array that represents the LCR position

    <!-- -->

    - #### getTransactionId

          java.lang.String getTransactionId()

      Gets the transaction identifier of the LCR.
      See Oracle Call Interface reference manual for the format of transactionId.
      Returns:
      A string containing the transaction ID

    <!-- -->

    - #### getAttribute

          java.lang.Object getAttribute(java.lang.Object attributeName)

      Gets the attribute by specifying the attribute name.
      This method is used to get the attributes in an LCR. See valid attribute names defined in this class.
      Parameters:
      `attributeName` - The attribute name

      Returns:
      The attribte value object

    <!-- -->

    - #### getSourceTime

          oracle.sql.DATE getSourceTime()

      Gets the time when the LCR was created.
      Source time is the timestamp when the LCR was generated at source database.
      Returns:
      The source time object, an instance of oracle.sql.DATE.

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

- [Prev Class](DefaultRowLCR.md)
- [Next Class](RowLCR.md)

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
