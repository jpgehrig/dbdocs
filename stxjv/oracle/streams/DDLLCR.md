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

- [Prev Class](ColumnValue.md)
- [Next Class](DefaultChunkColumnValue.md)

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

## Interface DDLLCR

- All Superinterfaces:
  [LCR](LCR.md)

  <!-- -->

  All Known Implementing Classes:
  [DefaultDDLLCR](DefaultDDLLCR.md)

  ------------------------------------------------------------------------



      public interface DDLLCR
      extends LCR

  The DDLLCR interface encapsulates the information about a DDL LCR. A DDL LCR is a logical change record for a DDL operation. You can have a customized implementation of DDLLCR by using this interface.
  See Also:
  [`AbstractLCR`](AbstractLCR.md), [`RowLCR`](RowLCR.md)

<!-- -->

- - ### Field Summary

    - ### Fields inherited from interface oracle.streams.[LCR](LCR.md)

      [`ATTRIBUTE_ROOT_NAME`](LCR.md)`, `[`ATTRIBUTE_ROW_ID`](LCR.md)`, `[`ATTRIBUTE_SERIAL_NUM`](LCR.md)`, `[`ATTRIBUTE_SESSION_NUM`](LCR.md)`, `[`ATTRIBUTE_THREAD_NUM`](LCR.md)`, `[`ATTRIBUTE_TX_NAME`](LCR.md)`, `[`ATTRIBUTE_USERNAME`](LCR.md)

  <!-- -->

  - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Abstract Methods](javascript:show(4);)**

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

    - ### Methods inherited from interface oracle.streams.[LCR](LCR.md)

      [`getAttribute`](LCR.md)`, `[`getCommandType`](LCR.md)`, `[`getObjectName`](LCR.md)`, `[`getObjectOwner`](LCR.md)`, `[`getPosition`](LCR.md)`, `[`getSourceDatabaseName`](LCR.md)`, `[`getSourceTime`](LCR.md)`, `[`getTag`](LCR.md)`, `[`getTransactionId`](LCR.md)`, `[`setAttribute`](LCR.md)`, `[`setCommandType`](LCR.md)`, `[`setObjectName`](LCR.md)`, `[`setObjectOwner`](LCR.md)`, `[`setPosition`](LCR.md)`, `[`setSourceDatabaseName`](LCR.md)`, `[`setSourceTime`](LCR.md)`, `[`setTag`](LCR.md)`, `[`setTransactionId`](LCR.md)

<!-- -->

- - ### Method Detail

    - #### setCurrentSchema

          void setCurrentSchema(java.lang.String currentSchema)

      Sets the current schema.
      The current schema is used if no schema is specified explicitly for the modified database objects in DDLText. If a schema is specified in DDLText that differs from the one specified for currentSchema, then the schema specified in DDLText is used.
      Parameters:
      `currentSchema` - A string contains the current schema. Ensure that this parameter is set to a non-null value.

    <!-- -->

    - #### setDDLText

          void setDDLText(java.lang.String ddlText)

      Sets the DDL statement text.
      Parameters:
      `ddlText` - The DDL statement. Set this parameter to a non-NULL value.

    <!-- -->

    - #### setLogonUser

          void setLogonUser(java.lang.String logonUser)

      Sets the logon user name.
      The logon user is the user whose session executed the DDL statement.
      Parameters:
      `logonUser` - The logon user name

    <!-- -->

    - #### setBaseTableOwner

          void setBaseTableOwner(java.lang.String baseTableOwner)

      Sets the base table owner.
      If the DDL statement is related to a table (such as CREATE TABLE and ALTER TABLE), or if the DDL statement involves a table (such as creating a trigger on a table), then baseTableOwner specifies the owner of the table. Otherwise, set baseTableOwner to NULL.
      Parameters:
      `baseTableOwner` - The base table owner

    <!-- -->

    - #### setBaseTableName

          void setBaseTableName(java.lang.String baseTableName)

      Sets the base table name.
      If the DDL statement is related to a table (such as CREATE TABLE and ALTER TABLE), or if the DDL statement involves a table (such as creating a trigger on a table), then baseTableName specifies the name of the table. Otherwise, set baseTableName to NULL.
      Parameters:
      `baseTableName` - The base table name

    <!-- -->

    - #### setObjectType

          void setObjectType(java.lang.String objectType)

      Sets the object type.
      Parameters:
      `objectType` - The type of objec on which the DDL statement was executed. See Oracle Call Interface Programmer's Guide for more information.

    <!-- -->

    - #### setEditionName

          void setEditionName(java.lang.String editionName)
                       throws StreamsException

      Sets the edition name.
      The name of the edition in which the DDL statement was executed.
      Parameters:
      `editionName` - the edition name.

      Throws:
      [`StreamsException`](StreamsException.md) - if error occurs when obtaining edition name.

    <!-- -->

    - #### getCurrentSchema

          java.lang.String getCurrentSchema()

      Gets the current schema name.
      The current schema is used if no schema is specified explicitly for the modified database objects in DDLText. If a schema is specified in DDLText that differs from the one specified for currentSchema, then the schema specified in DDLText is used.
      Returns:
      A string contains the current schema

    <!-- -->

    - #### getDDLText

          java.lang.String getDDLText()

      Gets the DDL statement text.
      Returns:
      A string contains the DDL statement

    <!-- -->

    - #### getLogonUser

          java.lang.String getLogonUser()

      Gets the logon user name.
      The logon user is the user whose session executed the DDL statement.
      Returns:
      A string contains the logon user name

    <!-- -->

    - #### getBaseTableOwner

          java.lang.String getBaseTableOwner()

      Gets the base table owner.
      If the DDL statement is related to a table (such as CREATE TABLE and ALTER TABLE), or if the DDL statement involves a table (such as creating a trigger on a table), then baseTableOowner specifies the owner of the table. Otherwise, NULL is returned.
      Returns:
      A string contains the base table owner

    <!-- -->

    - #### getBaseTableName

          java.lang.String getBaseTableName()

      Gets the base table name.
      If the DDL statement is related to a table (such as CREATE TABLE and ALTER TABLE), or if the DDL statement involves a table (such as creating a trigger on a table), then baseTableName specifies the name of the table. Otherwise, NULL is returned.
      Returns:
      A string contains the base table name

    <!-- -->

    - #### getObjectType

          java.lang.String getObjectType()

      Gets the object type.
      The type of object on which the DDL statement was executed. See Oracle Call Interface Programmer's Guide for more information.
      Returns:
      A string contains the object type

    <!-- -->

    - #### getEditionName

          java.lang.String getEditionName()
                                   throws StreamsException

      Gets the edition name.
      The name of the edition in which the DDL statement was executed.
      Returns:
      A string contains the edition name

      Throws:
      [`StreamsException`](StreamsException.md) - if error occurs when obtaining edition name.

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

- [Prev Class](ColumnValue.md)
- [Next Class](DefaultChunkColumnValue.md)

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
