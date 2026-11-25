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

- Prev Class
- [Next Class](ChunkColumnValue.md)

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

## Class AbstractLCR

- java.lang.Object

- - oracle.streams.AbstractLCR

<!-- -->

- All Implemented Interfaces:
  [LCR](LCR.md)

  <!-- -->

  Direct Known Subclasses:
  [DefaultDDLLCR](DefaultDDLLCR.md), [DefaultRowLCR](DefaultRowLCR.md)

  ------------------------------------------------------------------------



      public abstract class AbstractLCR
      extends java.lang.Object
      implements LCR

  The AbstractLCR class provides an abstract implementation of the LCR interface. This class encapsulates the methods and attributes of the LCR message type defined by Oracle Streams. It is the super class for all Oracle Streams default LCR types, including DefaultRowLCR and DefaultDDLLCR.
  See Also:
  [`RowLCR`](RowLCR.md), [`DDLLCR`](DDLLCR.md)

<!-- -->

- - ### Field Summary

    - ### Fields inherited from interface oracle.streams.[LCR](LCR.md)

      [`ATTRIBUTE_ROOT_NAME`](LCR.md)`, `[`ATTRIBUTE_ROW_ID`](LCR.md)`, `[`ATTRIBUTE_SERIAL_NUM`](LCR.md)`, `[`ATTRIBUTE_SESSION_NUM`](LCR.md)`, `[`ATTRIBUTE_THREAD_NUM`](LCR.md)`, `[`ATTRIBUTE_TX_NAME`](LCR.md)`, `[`ATTRIBUTE_USERNAME`](LCR.md)

  <!-- -->

  - ### Constructor Summary

    **Constructors**

    | Constructor and Description |
    |-----------------------------|
    | `AbstractLCR``()`           |

  <!-- -->

  - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type    | Method and Description                                                                                                                                                      |
    |----------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `java.lang.Object`   | `getAttribute``(java.lang.Object attributeName)`<br>Gets the attribute by specifying the attribute name.                                                                    |
    | `java.lang.Object`   | `getAttributeName``(int index)`<br>Gets the attribute name in the LCR attributes list by position.                                                                          |
    | `java.lang.Object[]` | `getAttributesList``()`<br>Gets the list of attribute name and value pairs in the LCR.                                                                                      |
    | `java.lang.Object`   | `getAttributeValue``(int index)`<br>Gets the attribute value in the LCR attributes list by position.                                                                        |
    | `java.lang.String`   | `getCommandType``()`<br>Gets the LCR command type executed in the DML or DDL statement.                                                                                     |
    | `oracle.sql.NUMBER`  | `getCommitSCN``()`<br>Gets the LCR commit system change number (SCN) in the format of oracle.sql.NUMBER.                                                                    |
    | `java.lang.String`   | `getMessageTrackingLabel``()`<br>Gets the message tracking label of the LCR.                                                                                                |
    | `int`                | `getNumAttributes``()`<br>Gets the total number of attributes in the LCR.                                                                                                   |
    | `java.lang.String`   | `getObjectName``()`<br>Gets the name of the object that is changed by the LCR.                                                                                              |
    | `java.lang.String`   | `getObjectOwner``()`<br>Gets the owner of the object that is changed by the LCR.                                                                                            |
    | `byte[]`             | `getPosition``()`<br>Gets the position of the current LCR.                                                                                                                  |
    | `java.lang.String`   | `getRootName``()`<br>Gets the root name of the LCR.                                                                                                                         |
    | `oracle.sql.NUMBER`  | `getSCN``()`<br>Gets the SCN of the current LCR in the format of oracle.sql.NUMBER.                                                                                         |
    | `java.lang.String`   | `getSourceDatabaseName``()`<br>Gets the global name of the source database.                                                                                                 |
    | `oracle.sql.DATE`    | `getSourceTime``()`<br>Gets the time when the LCR was created.                                                                                                              |
    | `byte[]`             | `getTag``()`<br>Gets the tag for the LCR.                                                                                                                                   |
    | `java.lang.String`   | `getTransactionId``()`<br>Gets the transaction identifier of the LCR.                                                                                                       |
    | `void`               | `setAttribute``(java.lang.Object attributeName, java.lang.Object attributeValue)`<br>Sets attribute by providing the name and value pair; the name is used as the hash key. |
    | `void`               | `setCommandType``(java.lang.String commandType)`<br>Sets the command type in the LCR.                                                                                       |
    | `void`               | `setMessageTrackingLabel``(java.lang.String messageTrackingLabel)`<br>Sets the message tracking label of the LCR.                                                           |
    | `void`               | `setObjectName``(java.lang.String objectName)`<br>Sets the name of the object that is changed by the LCR.                                                                   |
    | `void`               | `setObjectOwner``(java.lang.String objectOwner)`<br>Sets the owner of the object that is changed by the LCR .                                                               |
    | `void`               | `setPosition``(byte[] position)`<br>Sets the position in the LCR.                                                                                                           |
    | `void`               | `setRootName``(java.lang.String rootName)`<br>Sets the root name of the LCR.                                                                                                |
    | `void`               | `setSourceDatabaseName``(java.lang.String name)`<br>Sets the source database name of the object that is changed by the LCR.                                                 |
    | `void`               | `setSourceTime``(oracle.sql.DATE sourceTime)`<br>Sets the source timestamp when the LCR was created.                                                                        |
    | `void`               | `setTag``(byte[] tag)`<br>Sets the LCR tag information.                                                                                                                     |
    | `void`               | `setTransactionId``(java.lang.String transactionId)`<br>Sets the transaction identifier for the LCR.                                                                        |

    - ### Methods inherited from class java.lang.Object

      `equals, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

<!-- -->

- - ### Constructor Detail

    - #### AbstractLCR

          public AbstractLCR()

  <!-- -->

  - ### Method Detail

    - #### setSourceDatabaseName

          public void setSourceDatabaseName(java.lang.String name)

      Sets the source database name of the object that is changed by the LCR.

      The source database is the database where the change originated.
      Specified by:
      [`setSourceDatabaseName`](LCR.md) in interface [`LCR`](LCR.md)

      Parameters:
      `name` - The source database name in String format. Set this parameter to a non-NULL value.

    <!-- -->

    - #### setCommandType

          public void setCommandType(java.lang.String commandType)

      Sets the command type in the LCR.
      See Oracle Call Interface reference manual for complete command type definition.

      Specified by:
      [`setCommandType`](LCR.md) in interface [`LCR`](LCR.md)

      Parameters:
      `commandType` - The command type of an LCR. Set this parameter to a non-NULL value.

    <!-- -->

    - #### setObjectOwner

          public void setObjectOwner(java.lang.String objectOwner)

      Sets the owner of the object that is changed by the LCR .
      Specified by:
      [`setObjectOwner`](LCR.md) in interface [`LCR`](LCR.md)

      Parameters:
      `objectOwner` - The object owner. Set this parameter to a non-NULL value.

    <!-- -->

    - #### setObjectName

          public void setObjectName(java.lang.String objectName)

      Sets the name of the object that is changed by the LCR.
      Specified by:
      [`setObjectName`](LCR.md) in interface [`LCR`](LCR.md)

      Parameters:
      `objectName` - The name of the database object. Set this parameter to a non-NULL value.

    <!-- -->

    - #### setTag

          public void setTag(byte[] tag)

      Sets the LCR tag information.
      A binary tag that enables tracking of the LCR. For example, this tag can be used to determine the original source database of the DML or DDL statement when apply forwarding is used.
      See "Oracle Streams Replication Administrator's Guide" for more information about tags
      Specified by:
      [`setTag`](LCR.md) in interface [`LCR`](LCR.md)

      Parameters:
      `tag` - A binary tag that enables tracking of the LCR.

    <!-- -->

    - #### setPosition

          public void setPosition(byte[] position)

      Sets the position in the LCR.
      The position uniquely identifies each LCR in an LCR stream.
      Specified by:
      [`setPosition`](LCR.md) in interface [`LCR`](LCR.md)

      Parameters:
      `position` - A byte array that represents the LCR position. Set this parameter to a non-NULL value and ensure that the position is byte comparable and is strictly increasing.

    <!-- -->

    - #### setTransactionId

          public void setTransactionId(java.lang.String transactionId)

      Sets the transaction identifier for the LCR.
      See Oracle Call Interface reference manual for the format of transactionId.
      Specified by:
      [`setTransactionId`](LCR.md) in interface [`LCR`](LCR.md)

      Parameters:
      `transactionId` - The identifier of the transaction

    <!-- -->

    - #### setSourceTime

          public void setSourceTime(oracle.sql.DATE sourceTime)

      Sets the source timestamp when the LCR was created.
      The source time is the time when the change in an LCR captured by a capture process was generated in the redo log of the source database, or the time when a persistent LCR was created.
      Specified by:
      [`setSourceTime`](LCR.md) in interface [`LCR`](LCR.md)

      Parameters:
      `sourceTime` - The srouce time in the form of oracle.sql.DATE

    <!-- -->

    - #### setAttribute

          public void setAttribute(java.lang.Object attributeName,
                                   java.lang.Object attributeValue)

      Sets attribute by providing the name and value pair; the name is used as the hash key.
      This method sets the attributes in an LCR.
      Specified by:
      [`setAttribute`](LCR.md) in interface [`LCR`](LCR.md)

      Parameters:
      `attributeName` - The name of the attribute

      `attributeValue` - The value of the attribute

    <!-- -->

    - #### setMessageTrackingLabel

          public void setMessageTrackingLabel(java.lang.String messageTrackingLabel)
                                       throws StreamsException

      Sets the message tracking label of the LCR.
      You can use the SET_MESSAGE_TRACKING procedure in the DBMS_STREAMS_ADM package to track an LCR as it flows through a stream. See Oracle Streams Replication Administrator's Guide for information about setting message tracking labels.
      Parameters:
      `messageTrackingLabel` - The message tracking label

      Throws:
      [`StreamsException`](StreamsException.md) - If error occurs when obtaining message tracking label

    <!-- -->

    - #### getSourceDatabaseName

          public java.lang.String getSourceDatabaseName()

      Gets the global name of the source database.
      The source database is the database where the change originated.
      Specified by:
      [`getSourceDatabaseName`](LCR.md) in interface [`LCR`](LCR.md)

      Returns:
      A string containing source database name

    <!-- -->

    - #### getCommandType

          public java.lang.String getCommandType()

      Gets the LCR command type executed in the DML or DDL statement. See Oracle Call Interface reference manual for complete command type definition.

      Specified by:
      [`getCommandType`](LCR.md) in interface [`LCR`](LCR.md)

      Returns:
      A string containing comand type

    <!-- -->

    - #### getObjectOwner

          public java.lang.String getObjectOwner()

      Gets the owner of the object that is changed by the LCR.
      The owner is the user who owns the object on which the row change ocurred or the DDL statement was executed.
      Specified by:
      [`getObjectOwner`](LCR.md) in interface [`LCR`](LCR.md)

      Returns:
      A string containing the owner

    <!-- -->

    - #### getObjectName

          public java.lang.String getObjectName()

      Gets the name of the object that is changed by the LCR.
      The name of the database object on which the DDL or DML statement was executed.
      Specified by:
      [`getObjectName`](LCR.md) in interface [`LCR`](LCR.md)

      Returns:
      A string containing the name

    <!-- -->

    - #### getTag

          public byte[] getTag()

      Gets the tag for the LCR.
      A binary tag that enables tracking of the LCR. For example, this tag can be used to determine the original source database of the DML or DDL statement when apply forwarding is used.
      Specified by:
      [`getTag`](LCR.md) in interface [`LCR`](LCR.md)

      Returns:
      A byte array that represents the tag

    <!-- -->

    - #### getPosition

          public byte[] getPosition()

      Gets the position of the current LCR.
      A byte array that uniquely identifies an LCR in the stream and is in strictly increasing order.
      Specified by:
      [`getPosition`](LCR.md) in interface [`LCR`](LCR.md)

      Returns:
      A byte array that represents the LCR position

    <!-- -->

    - #### getTransactionId

          public java.lang.String getTransactionId()

      Gets the transaction identifier of the LCR.
      See Oracle Call Interface reference manual for the format of transactionId.
      Specified by:
      [`getTransactionId`](LCR.md) in interface [`LCR`](LCR.md)

      Returns:
      A string containing the transaction id

    <!-- -->

    - #### getSourceTime

          public oracle.sql.DATE getSourceTime()

      Gets the time when the LCR was created.
      Source time is the timestamp when the LCR was generated at source database.
      Specified by:
      [`getSourceTime`](LCR.md) in interface [`LCR`](LCR.md)

      Returns:
      The source time object, an instance of oracle.sql.DATE.

    <!-- -->

    - #### getAttribute

          public java.lang.Object getAttribute(java.lang.Object attributeName)

      Gets the attribute by specifying the attribute name.
      This method gets the attributes in an LCR.
      Specified by:
      [`getAttribute`](LCR.md) in interface [`LCR`](LCR.md)

      Parameters:
      `attributeName` - The attribute name

      Returns:
      The attribte value object

    <!-- -->

    - #### getSCN

          public oracle.sql.NUMBER getSCN()

      Gets the SCN of the current LCR in the format of oracle.sql.NUMBER.
      The LCR SCN is the system change number when the LCR is generated at source database.
      Returns:
      The SCN in the format of oracle.sql.NUMBER.

    <!-- -->

    - #### getCommitSCN

          public oracle.sql.NUMBER getCommitSCN()

      Gets the LCR commit system change number (SCN) in the format of oracle.sql.NUMBER.
      The LCR commit SCN is the SCN when the transaction to which the LCR belongs committed at the source database.
      Returns:
      The commit SCN in the format of oracle.sql.NUMBER.

    <!-- -->

    - #### getNumAttributes

          public int getNumAttributes()

      Gets the total number of attributes in the LCR.
      Returns:
      The total number of attributes.

    <!-- -->

    - #### getAttributesList

          public java.lang.Object[] getAttributesList()

      Gets the list of attribute name and value pairs in the LCR.
      Returns:
      An array of attribute entries.

    <!-- -->

    - #### getAttributeName

          public java.lang.Object getAttributeName(int index)

      Gets the attribute name in the LCR attributes list by position.
      Parameters:
      `index` - The atribute name's index.

      Returns:
      The attribute name

    <!-- -->

    - #### getAttributeValue

          public java.lang.Object getAttributeValue(int index)

      Gets the attribute value in the LCR attributes list by position.
      Parameters:
      `index` - The atribute name's index.

      Returns:
      The attribute value

    <!-- -->

    - #### getMessageTrackingLabel

          public java.lang.String getMessageTrackingLabel()
                                                   throws StreamsException

      Gets the message tracking label of the LCR.
      You can use the SET_MESSAGE_TRACKING procedure in the DBMS_STREAMS_ADM package to track an LCR as it flows through a stream. See Oracle Streams Replication Administrator's Guide for information about setting message tracking labels.
      Returns:
      A string contains the message tracking label

      Throws:
      [`StreamsException`](StreamsException.md) - If error occurs when obtaining message tracking label

    <!-- -->

    - #### getRootName

          public java.lang.String getRootName()
                                       throws StreamsException

      Gets the root name of the LCR.
      Returns:
      A string contains the root name of the LCR.

      Throws:
      [`StreamsException`](StreamsException.md) - If error occurs when obtaining root name.

    <!-- -->

    - #### setRootName

          public void setRootName(java.lang.String rootName)
                           throws StreamsException

      Sets the root name of the LCR.
      Parameters:
      `rootName` - The message tracking label

      Throws:
      [`StreamsException`](StreamsException.md) - If error occurs when obtaining message tracking label

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

- Prev Class
- [Next Class](ChunkColumnValue.md)

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
