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

- [Prev Class](DefaultColumnValue.md)
- [Next Class](DefaultRowLCR.md)

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

## Class DefaultDDLLCR

- java.lang.Object

- - [oracle.streams.AbstractLCR](AbstractLCR.md)

  - - oracle.streams.DefaultDDLLCR

<!-- -->

- All Implemented Interfaces:
  [DDLLCR](DDLLCR.md), [LCR](LCR.md)

  ------------------------------------------------------------------------



      public class DefaultDDLLCR
      extends AbstractLCR
      implements DDLLCR

  The DefaultDDLLCR class provides an Oracle default implementation of the DDLLCR interface. A DDL LCR is a logical change record for a DDL operation.

<!-- -->

- - ### Field Summary

    - ### Fields inherited from interface oracle.streams.[LCR](LCR.md)

      [`ATTRIBUTE_ROOT_NAME`](LCR.md)`, `[`ATTRIBUTE_ROW_ID`](LCR.md)`, `[`ATTRIBUTE_SERIAL_NUM`](LCR.md)`, `[`ATTRIBUTE_SESSION_NUM`](LCR.md)`, `[`ATTRIBUTE_THREAD_NUM`](LCR.md)`, `[`ATTRIBUTE_TX_NAME`](LCR.md)`, `[`ATTRIBUTE_USERNAME`](LCR.md)

  <!-- -->

  - ### Constructor Summary

    **Constructors**

    | Constructor and Description                                                                                                                                                                                                                                                                      |
    |--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `DefaultDDLLCR``()`<br>Constructs a DDLLCR object with NULL values                                                                                                                                                                                                                               |
    | `DefaultDDLLCR``(java.lang.String sourceDatabaseName, java.lang.String commandType, java.lang.String objectOwner, java.lang.String objectName, java.lang.String transactionId, byte[] tag, byte[] position, oracle.sql.DATE sourceTime)`<br>Constructs a DDLLCR object with given LCR parameters |

  <!-- -->

  - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type  | Method and Description                                                               |
    |--------------------|--------------------------------------------------------------------------------------|
    | `java.lang.String` | `getBaseTableName``()`<br>Gets the base table name.                                  |
    | `java.lang.String` | `getBaseTableOwner``()`<br>Gets the base table owner.                                |
    | `java.lang.String` | `getCurrentSchema``()`<br>Gets the current schema name.                              |
    | `java.lang.String` | `getDDLText``()`<br>Gets the DDL statement text.                                     |
    | `java.lang.String` | `getEditionName``()`<br>Gets the edition name.                                       |
    | `java.lang.String` | `getLogonUser``()`<br>Gets the logon user name.                                      |
    | `java.lang.String` | `getObjectType``()`<br>Gets the object type.                                         |
    | `void`             | `setBaseTableName``(java.lang.String baseTableName)`<br>Sets the base table name.    |
    | `void`             | `setBaseTableOwner``(java.lang.String baseTableOwner)`<br>Sets the base table owner. |
    | `void`             | `setCurrentSchema``(java.lang.String currentSchema)`<br>Sets the current schema.     |
    | `void`             | `setDDLText``(java.lang.String ddlText)`<br>Sets the DDL statement text.             |
    | `void`             | `setEditionName``(java.lang.String editionName)`<br>Sets the edition name.           |
    | `void`             | `setLogonUser``(java.lang.String logonUser)`<br>Sets the logon user name.            |
    | `void`             | `setObjectType``(java.lang.String objectType)`<br>Sets the object type.              |

    - ### Methods inherited from class oracle.streams.[AbstractLCR](AbstractLCR.md)

      [`getAttribute`](AbstractLCR.md)`, `[`getAttributeName`](AbstractLCR.md)`, `[`getAttributesList`](AbstractLCR.md)`, `[`getAttributeValue`](AbstractLCR.md)`, `[`getCommandType`](AbstractLCR.md)`, `[`getCommitSCN`](AbstractLCR.md)`, `[`getMessageTrackingLabel`](AbstractLCR.md)`, `[`getNumAttributes`](AbstractLCR.md)`, `[`getObjectName`](AbstractLCR.md)`, `[`getObjectOwner`](AbstractLCR.md)`, `[`getPosition`](AbstractLCR.md)`, `[`getRootName`](AbstractLCR.md)`, `[`getSCN`](AbstractLCR.md)`, `[`getSourceDatabaseName`](AbstractLCR.md)`, `[`getSourceTime`](AbstractLCR.md)`, `[`getTag`](AbstractLCR.md)`, `[`getTransactionId`](AbstractLCR.md)`, `[`setAttribute`](AbstractLCR.md)`, `[`setCommandType`](AbstractLCR.md)`, `[`setMessageTrackingLabel`](AbstractLCR.md)`, `[`setObjectName`](AbstractLCR.md)`, `[`setObjectOwner`](AbstractLCR.md)`, `[`setPosition`](AbstractLCR.md)`, `[`setRootName`](AbstractLCR.md)`, `[`setSourceDatabaseName`](AbstractLCR.md)`, `[`setSourceTime`](AbstractLCR.md)`, `[`setTag`](AbstractLCR.md)`, `[`setTransactionId`](AbstractLCR.md)

    <!-- -->

    - ### Methods inherited from class java.lang.Object

      `equals, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

    <!-- -->

    - ### Methods inherited from interface oracle.streams.[LCR](LCR.md)

      [`getAttribute`](LCR.md)`, `[`getCommandType`](LCR.md)`, `[`getObjectName`](LCR.md)`, `[`getObjectOwner`](LCR.md)`, `[`getPosition`](LCR.md)`, `[`getSourceDatabaseName`](LCR.md)`, `[`getSourceTime`](LCR.md)`, `[`getTag`](LCR.md)`, `[`getTransactionId`](LCR.md)`, `[`setAttribute`](LCR.md)`, `[`setCommandType`](LCR.md)`, `[`setObjectName`](LCR.md)`, `[`setObjectOwner`](LCR.md)`, `[`setPosition`](LCR.md)`, `[`setSourceDatabaseName`](LCR.md)`, `[`setSourceTime`](LCR.md)`, `[`setTag`](LCR.md)`, `[`setTransactionId`](LCR.md)

<!-- -->

- - ### Constructor Detail

    - #### DefaultDDLLCR

          public DefaultDDLLCR()

      Constructs a DDLLCR object with NULL values

    <!-- -->

    - #### DefaultDDLLCR

          public DefaultDDLLCR(java.lang.String sourceDatabaseName,
                               java.lang.String commandType,
                               java.lang.String objectOwner,
                               java.lang.String objectName,
                               java.lang.String transactionId,
                               byte[] tag,
                               byte[] position,
                               oracle.sql.DATE sourceTime)

      Constructs a DDLLCR object with given LCR parameters
      Parameters:
      `sourceDatabaseName` - source database name.

      `commandType` - RowLCR command type.

      `objectOwner` - object owner.

      `objectName` - object name.

      `transactionId` - transaction identifier (ID).

      `tag` - LCR tag.

      `position` - LCR position

      `sourceTime` - source timestamp.

  <!-- -->

  - ### Method Detail

    - #### setCurrentSchema

          public void setCurrentSchema(java.lang.String currentSchema)

      Sets the current schema.
      The current schema is used if no schema is specified explicitly for the modified database objects in DDLText. If a schema is specified in DDLText that differs from the one specified for currentSchema, then the schema specified in DDLText is used.
      Specified by:
      [`setCurrentSchema`](DDLLCR.md) in interface [`DDLLCR`](DDLLCR.md)

      Parameters:
      `currentSchema` - A string contains the current schema. Ensure that this parameter is set to a non-NULL value

    <!-- -->

    - #### setDDLText

          public void setDDLText(java.lang.String ddlText)

      Sets the DDL statement text.
      Specified by:
      [`setDDLText`](DDLLCR.md) in interface [`DDLLCR`](DDLLCR.md)

      Parameters:
      `ddlText` - The DDL statement. Set this parameter to a non-NULL value.

    <!-- -->

    - #### setLogonUser

          public void setLogonUser(java.lang.String logonUser)

      Sets the logon user name.
      The logon user is the user whose session executed the DDL statement.
      Specified by:
      [`setLogonUser`](DDLLCR.md) in interface [`DDLLCR`](DDLLCR.md)

      Parameters:
      `logonUser` - The logon user name

    <!-- -->

    - #### setBaseTableOwner

          public void setBaseTableOwner(java.lang.String baseTableOwner)

      Sets the base table owner.
      If the DDL statement is related to a table (such as CREATE TABLE and ALTER TABLE), or if the DDL statement involves a table (such as creating a trigger on a table), then baseTableOwner specifies the owner of the table. Otherwise, set baseTableOwner to NULL.
      Specified by:
      [`setBaseTableOwner`](DDLLCR.md) in interface [`DDLLCR`](DDLLCR.md)

      Parameters:
      `baseTableOwner` - The base table owner

    <!-- -->

    - #### setBaseTableName

          public void setBaseTableName(java.lang.String baseTableName)

      Sets the base table name.
      If the DDL statement is related to a table (such as CREATE TABLE and ALTER TABLE), or if the DDL statement involves a table (such as creating a trigger on a table), then baseTableName specifies the name of the table. Otherwise, set baseTableName to NULL.
      Specified by:
      [`setBaseTableName`](DDLLCR.md) in interface [`DDLLCR`](DDLLCR.md)

      Parameters:
      `baseTableName` - The base table name

    <!-- -->

    - #### setObjectType

          public void setObjectType(java.lang.String objectType)

      Sets the object type.
      The type of object on which the DDL statement was executed. See Oracle Call Interface Programmer's Guide for more information.
      Specified by:
      [`setObjectType`](DDLLCR.md) in interface [`DDLLCR`](DDLLCR.md)

      Parameters:
      `objectType` - The object type

    <!-- -->

    - #### setEditionName

          public void setEditionName(java.lang.String editionName)
                              throws StreamsException

      Sets the edition name.
      The name of the edition in which the DDL statement was executed.
      Specified by:
      [`setEditionName`](DDLLCR.md) in interface [`DDLLCR`](DDLLCR.md)

      Parameters:
      `editionName` - The edition name.

      Throws:
      [`StreamsException`](StreamsException.md) - if error occurs when obtaining edition name

    <!-- -->

    - #### getCurrentSchema

          public java.lang.String getCurrentSchema()

      Gets the current schema name.
      The current schema is used if no schema is specified explicitly for the modified database objects in DDLText. If a schema is specified in DDLText that differs from the one specified for currentSchema, then the schema specified in DDLText is used.
      Specified by:
      [`getCurrentSchema`](DDLLCR.md) in interface [`DDLLCR`](DDLLCR.md)

      Returns:
      A string contains the current schema

    <!-- -->

    - #### getDDLText

          public java.lang.String getDDLText()

      Gets the DDL statement text.
      Specified by:
      [`getDDLText`](DDLLCR.md) in interface [`DDLLCR`](DDLLCR.md)

      Returns:
      a String contains the DDL statement

    <!-- -->

    - #### getLogonUser

          public java.lang.String getLogonUser()

      Gets the logon user name.
      The logon user is the user whose session executed the DDL statement.
      Specified by:
      [`getLogonUser`](DDLLCR.md) in interface [`DDLLCR`](DDLLCR.md)

      Returns:
      a String contains the logon user name

    <!-- -->

    - #### getBaseTableOwner

          public java.lang.String getBaseTableOwner()

      Gets the base table owner.
      If the DDL statement is related to a table (such as CREATE TABLE and ALTER TABLE), or if the DDL statement involves a table (such as creating a trigger on a table), then baseTableOowner specifies the owner of the table. Otherwise, NULL is returned.
      Specified by:
      [`getBaseTableOwner`](DDLLCR.md) in interface [`DDLLCR`](DDLLCR.md)

      Returns:
      a String contains the base table owner

    <!-- -->

    - #### getBaseTableName

          public java.lang.String getBaseTableName()

      Gets the base table name.
      If the DDL statement is related to a table (such as CREATE TABLE and ALTER TABLE), or if the DDL statement involves a table (such as creating a trigger on a table), then baseTableName specifies the name of the table. Otherwise, NULL is returned.
      Specified by:
      [`getBaseTableName`](DDLLCR.md) in interface [`DDLLCR`](DDLLCR.md)

      Returns:
      a String contains the base table name

    <!-- -->

    - #### getObjectType

          public java.lang.String getObjectType()

      Gets the object type.
      The type of object on which the DDL statement was executed. See Oracle Call Interface Programmer's Guide for more information.
      Specified by:
      [`getObjectType`](DDLLCR.md) in interface [`DDLLCR`](DDLLCR.md)

      Returns:
      a String contains the object type

    <!-- -->

    - #### getEditionName

          public java.lang.String getEditionName()
                                          throws StreamsException

      Gets the edition name.
      The name of the edition in which the DDL statement was executed.
      Specified by:
      [`getEditionName`](DDLLCR.md) in interface [`DDLLCR`](DDLLCR.md)

      Returns:
      a String contains the edition name

      Throws:
      [`StreamsException`](StreamsException.md) - if error occurs when obtaining edition name

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

- [Prev Class](DefaultColumnValue.md)
- [Next Class](DefaultRowLCR.md)

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
