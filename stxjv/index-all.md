Skip navigation links

- [Package](oracle/streams/package-summary.md)
- Class
- [Tree](overview-tree.md)
- [Deprecated](deprecated-list.md)
- Index
- [Help](help-doc.md)

**Oracle® Database XStream Java API Reference
19c**
E96285-02

- Prev
- Next

<!-- -->

- [Frames](index.md)
- No Frames

<!-- -->

- [All Classes](allclasses-noframe.md)

A B C D E F G H I L M N O P R S T U X 

## A

[AbstractLCR](oracle/streams/AbstractLCR.md) - Class in [oracle.streams](oracle/streams/package-summary.md)
The AbstractLCR class provides an abstract implementation of the LCR interface.

[AbstractLCR()](oracle/streams/AbstractLCR.md) - Constructor for class oracle.streams.[AbstractLCR](oracle/streams/AbstractLCR.md)
 

[attach(OracleConnection, String, String, int)](oracle/streams/XStreamIn.md) - Static method in class oracle.streams.[XStreamIn](oracle/streams/XStreamIn.md)
Attaches to an inbound server.

[attach(OracleConnection, String, String, int, int)](oracle/streams/XStreamIn.md) - Static method in class oracle.streams.[XStreamIn](oracle/streams/XStreamIn.md)
Attaches to an inbound server.

[attach(OracleConnection, String, byte\[\], int)](oracle/streams/XStreamOut.md) - Static method in class oracle.streams.[XStreamOut](oracle/streams/XStreamOut.md)
Attaches to outbound server.

[attach(OracleConnection, String, byte\[\], int, int, int)](oracle/streams/XStreamOut.md) - Static method in class oracle.streams.[XStreamOut](oracle/streams/XStreamOut.md)
Attaches to outbound server.

[ATTACH_APP_CONTAINER_MODE](oracle/streams/XStreamOut.md) - Static variable in class oracle.streams.[XStreamOut](oracle/streams/XStreamOut.md)
This attach mode captures application container statements.

[ATTACH_EXTENDED_ID_MODE](oracle/streams/XStreamOut.md) - Static variable in class oracle.streams.[XStreamOut](oracle/streams/XStreamOut.md)
This attach mode returns transaction ID using extended format, "pdb_id.nn.nn.nn".

[ATTRIBUTE_ROOT_NAME](oracle/streams/LCR.md) - Static variable in interface oracle.streams.[LCR](oracle/streams/LCR.md)
The name of the root container in a consolidated database.

[ATTRIBUTE_ROW_ID](oracle/streams/LCR.md) - Static variable in interface oracle.streams.[LCR](oracle/streams/LCR.md)
The rowid of the row changed in a row LCR.

[ATTRIBUTE_SERIAL_NUM](oracle/streams/LCR.md) - Static variable in interface oracle.streams.[LCR](oracle/streams/LCR.md)
The serial number of the session that performed the change captured in the LCR.

[ATTRIBUTE_SESSION_NUM](oracle/streams/LCR.md) - Static variable in interface oracle.streams.[LCR](oracle/streams/LCR.md)
The identifier of the session that performed the change captured in the LCR.

[ATTRIBUTE_THREAD_NUM](oracle/streams/LCR.md) - Static variable in interface oracle.streams.[LCR](oracle/streams/LCR.md)
The thread number of the instance in which the change captured in the LCR was performed.

[ATTRIBUTE_TX_NAME](oracle/streams/LCR.md) - Static variable in interface oracle.streams.[LCR](oracle/streams/LCR.md)
The name of the transaction that includes the LCR.

[ATTRIBUTE_USERNAME](oracle/streams/LCR.md) - Static variable in interface oracle.streams.[LCR](oracle/streams/LCR.md)
The name of the current user who performed the change captured in the LCR.

## B

[BINARY_DOUBLE](oracle/streams/ColumnValue.md) - Static variable in interface oracle.streams.[ColumnValue](oracle/streams/ColumnValue.md)
 

[BINARY_FLOAT](oracle/streams/ColumnValue.md) - Static variable in interface oracle.streams.[ColumnValue](oracle/streams/ColumnValue.md)
 

[BLOB](oracle/streams/ChunkColumnValue.md) - Static variable in interface oracle.streams.[ChunkColumnValue](oracle/streams/ChunkColumnValue.md)
 

## C

[CHAR](oracle/streams/ColumnValue.md) - Static variable in interface oracle.streams.[ColumnValue](oracle/streams/ColumnValue.md)
 

[ChunkColumnValue](oracle/streams/ChunkColumnValue.md) - Interface in [oracle.streams](oracle/streams/package-summary.md)
The ChunkColumnValue interface encapsulates the information about a LOB, LONG, or XMLTYPE column in a RowLCR.

[CLOB](oracle/streams/ChunkColumnValue.md) - Static variable in interface oracle.streams.[ChunkColumnValue](oracle/streams/ChunkColumnValue.md)
 

[ColumnValue](oracle/streams/ColumnValue.md) - Interface in [oracle.streams](oracle/streams/package-summary.md)
The ColumnValue interface encapsulates the information about a column in a RowLCR.

[COMMIT](oracle/streams/RowLCR.md) - Static variable in interface oracle.streams.[RowLCR](oracle/streams/RowLCR.md)
 

[convertSCNToPosition(NUMBER)](oracle/streams/XStreamUtility.md) - Static method in class oracle.streams.[XStreamUtility](oracle/streams/XStreamUtility.md)
Converts the given SCN to a XStream position.

[convertSCNToPosition(NUMBER, int)](oracle/streams/XStreamUtility.md) - Static method in class oracle.streams.[XStreamUtility](oracle/streams/XStreamUtility.md)
Converts the given SCN to a XStream position.

[createChunk()](oracle/streams/XStreamLCRCallbackHandler.md) - Method in interface oracle.streams.[XStreamLCRCallbackHandler](oracle/streams/XStreamLCRCallbackHandler.md)
The callback method for constructing chunk data that is sent to an XStream inbound server.

[createLCR()](oracle/streams/XStreamLCRCallbackHandler.md) - Method in interface oracle.streams.[XStreamLCRCallbackHandler](oracle/streams/XStreamLCRCallbackHandler.md)
The callback method for creating an LCR and sending it to an XStream inbound server.

## D

[DATE](oracle/streams/ColumnValue.md) - Static variable in interface oracle.streams.[ColumnValue](oracle/streams/ColumnValue.md)
 

[DDLLCR](oracle/streams/DDLLCR.md) - Interface in [oracle.streams](oracle/streams/package-summary.md)
The DDLLCR interface encapsulates the information about a DDL LCR.

[DEFAULT_BATCH_INTERVAL](oracle/streams/XStreamIn.md) - Static variable in class oracle.streams.[XStreamIn](oracle/streams/XStreamIn.md)
XStreamIn default batch interval value for batch processing

[DEFAULT_BATCH_INTERVAL](oracle/streams/XStreamOut.md) - Static variable in class oracle.streams.[XStreamOut](oracle/streams/XStreamOut.md)
XStreamOut default acknowledge interval value for batch processing

[DEFAULT_IDLE_TIMEOUT](oracle/streams/XStreamOut.md) - Static variable in class oracle.streams.[XStreamOut](oracle/streams/XStreamOut.md)
XStreamOut default timeout value for idle processing

[DEFAULT_MODE](oracle/streams/XStreamIn.md) - Static variable in class oracle.streams.[XStreamIn](oracle/streams/XStreamIn.md)
XStreamIn default mode

[DEFAULT_MODE](oracle/streams/XStreamOut.md) - Static variable in class oracle.streams.[XStreamOut](oracle/streams/XStreamOut.md)
XStreamOut default mode

[DefaultChunkColumnValue](oracle/streams/DefaultChunkColumnValue.md) - Class in [oracle.streams](oracle/streams/package-summary.md)
The DefaultChunkColumnValue class provides an Oracle default implementation of the ChunkColumnValue interface.

[DefaultChunkColumnValue(String, Datum, int)](oracle/streams/DefaultChunkColumnValue.md) - Constructor for class oracle.streams.[DefaultChunkColumnValue](oracle/streams/DefaultChunkColumnValue.md)
Constructs a DefaultChunkColumnValue object with the column information.

[DefaultChunkColumnValue(String, Datum, int, BigInteger, BigInteger)](oracle/streams/DefaultChunkColumnValue.md) - Constructor for class oracle.streams.[DefaultChunkColumnValue](oracle/streams/DefaultChunkColumnValue.md)
Constructs a DefaultChunkColumnValue object with the column information.

[DefaultColumnValue](oracle/streams/DefaultColumnValue.md) - Class in [oracle.streams](oracle/streams/package-summary.md)
The DefaultColumnValue class provides an Oracle default implementation of ColumnValue interface.

[DefaultColumnValue(String, Datum, int)](oracle/streams/DefaultColumnValue.md) - Constructor for class oracle.streams.[DefaultColumnValue](oracle/streams/DefaultColumnValue.md)
Constructs a DefaultColumnValue object with columnName, columnData, and columnDataType.
When columnData is NULL, a valid columnDataType is expected.

[DefaultColumnValue(String, Datum)](oracle/streams/DefaultColumnValue.md) - Constructor for class oracle.streams.[DefaultColumnValue](oracle/streams/DefaultColumnValue.md)
Constructs a DefaultColumnValue object with columnName and columnData.
This constructor can be used when columnData is not null.

[DefaultDDLLCR](oracle/streams/DefaultDDLLCR.md) - Class in [oracle.streams](oracle/streams/package-summary.md)
The DefaultDDLLCR class provides an Oracle default implementation of the DDLLCR interface.

[DefaultDDLLCR()](oracle/streams/DefaultDDLLCR.md) - Constructor for class oracle.streams.[DefaultDDLLCR](oracle/streams/DefaultDDLLCR.md)
Constructs a DDLLCR object with NULL values

[DefaultDDLLCR(String, String, String, String, String, byte\[\], byte\[\], DATE)](oracle/streams/DefaultDDLLCR.md) - Constructor for class oracle.streams.[DefaultDDLLCR](oracle/streams/DefaultDDLLCR.md)
Constructs a DDLLCR object with given LCR parameters

[DefaultRowLCR](oracle/streams/DefaultRowLCR.md) - Class in [oracle.streams](oracle/streams/package-summary.md)
The DefaultRowLCR class provides an Oracle default implementation of the RowLCR interface.

[DefaultRowLCR(String, String, String, String, String, byte\[\], byte\[\], DATE)](oracle/streams/DefaultRowLCR.md) - Constructor for class oracle.streams.[DefaultRowLCR](oracle/streams/DefaultRowLCR.md)
Constructs a RowLCR object with given LCR parameters.

[DefaultRowLCR()](oracle/streams/DefaultRowLCR.md) - Constructor for class oracle.streams.[DefaultRowLCR](oracle/streams/DefaultRowLCR.md)
Constructs a RowLCR object with NULL values.

[DELETE](oracle/streams/RowLCR.md) - Static variable in interface oracle.streams.[RowLCR](oracle/streams/RowLCR.md)
 

[detach(int)](oracle/streams/XStreamIn.md) - Method in class oracle.streams.[XStreamIn](oracle/streams/XStreamIn.md)
Detaches from an inbound server.

[detach(int)](oracle/streams/XStreamOut.md) - Method in class oracle.streams.[XStreamOut](oracle/streams/XStreamOut.md)
Detaches from outbound server.

## E

[EXECUTING](oracle/streams/XStreamIn.md) - Static variable in class oracle.streams.[XStreamIn](oracle/streams/XStreamIn.md)
XStreamIn batch processing status EXECUTING, which indicates the the batch is in progress

[EXECUTING](oracle/streams/XStreamOut.md) - Static variable in class oracle.streams.[XStreamOut](oracle/streams/XStreamOut.md)
XStreamOut batch processing status EXECUTING, which indicates the the batch is in progress

## F

[FINISHED](oracle/streams/XStreamIn.md) - Static variable in class oracle.streams.[XStreamIn](oracle/streams/XStreamIn.md)
XStreamIn batch processing status FINISHED, which is the default status

[FINISHED](oracle/streams/XStreamOut.md) - Static variable in class oracle.streams.[XStreamOut](oracle/streams/XStreamOut.md)
XStreamOut batch processing status FINISHED, which is the default status

[flush(int)](oracle/streams/XStreamIn.md) - Method in class oracle.streams.[XStreamIn](oracle/streams/XStreamIn.md)
Flushes the network.

## G

[getAttribute(Object)](oracle/streams/AbstractLCR.md) - Method in class oracle.streams.[AbstractLCR](oracle/streams/AbstractLCR.md)
Gets the attribute by specifying the attribute name.

[getAttribute(Object)](oracle/streams/LCR.md) - Method in interface oracle.streams.[LCR](oracle/streams/LCR.md)
Gets the attribute by specifying the attribute name.

[getAttributeName(int)](oracle/streams/AbstractLCR.md) - Method in class oracle.streams.[AbstractLCR](oracle/streams/AbstractLCR.md)
Gets the attribute name in the LCR attributes list by position.

[getAttributesList()](oracle/streams/AbstractLCR.md) - Method in class oracle.streams.[AbstractLCR](oracle/streams/AbstractLCR.md)
Gets the list of attribute name and value pairs in the LCR.

[getAttributeValue(int)](oracle/streams/AbstractLCR.md) - Method in class oracle.streams.[AbstractLCR](oracle/streams/AbstractLCR.md)
Gets the attribute value in the LCR attributes list by position.

[getBaseTableName()](oracle/streams/DDLLCR.md) - Method in interface oracle.streams.[DDLLCR](oracle/streams/DDLLCR.md)
Gets the base table name.

[getBaseTableName()](oracle/streams/DefaultDDLLCR.md) - Method in class oracle.streams.[DefaultDDLLCR](oracle/streams/DefaultDDLLCR.md)
Gets the base table name.

[getBaseTableOwner()](oracle/streams/DDLLCR.md) - Method in interface oracle.streams.[DDLLCR](oracle/streams/DDLLCR.md)
Gets the base table owner.

[getBaseTableOwner()](oracle/streams/DefaultDDLLCR.md) - Method in class oracle.streams.[DefaultDDLLCR](oracle/streams/DefaultDDLLCR.md)
Gets the base table owner.

[getBatchStatus()](oracle/streams/XStreamOut.md) - Method in class oracle.streams.[XStreamOut](oracle/streams/XStreamOut.md)
Gets batch status.

[getBinds()](oracle/streams/DefaultRowLCR.md) - Method in class oracle.streams.[DefaultRowLCR](oracle/streams/DefaultRowLCR.md)
Gets the bind values that bind the SQL statement generated using getStatement().

[getCharSetId()](oracle/streams/ChunkColumnValue.md) - Method in interface oracle.streams.[ChunkColumnValue](oracle/streams/ChunkColumnValue.md)
Gets the chunk character set ID.

[getCharsetId()](oracle/streams/ColumnValue.md) - Method in interface oracle.streams.[ColumnValue](oracle/streams/ColumnValue.md)
Gets the column character set identifier (ID).

[getCharSetId()](oracle/streams/DefaultChunkColumnValue.md) - Method in class oracle.streams.[DefaultChunkColumnValue](oracle/streams/DefaultChunkColumnValue.md)
Gets the chunk character set identifier (ID) for an XMLTYPE chunk
The character set ID indicates the character set used to interpret the XMLTYPE chunk data.

[getCharsetId()](oracle/streams/DefaultColumnValue.md) - Method in class oracle.streams.[DefaultColumnValue](oracle/streams/DefaultColumnValue.md)
Gets the column character set identifier (ID).

[getChunkOffset()](oracle/streams/ChunkColumnValue.md) - Method in interface oracle.streams.[ChunkColumnValue](oracle/streams/ChunkColumnValue.md)
Gets the chunk operation offset.

[getChunkOffset()](oracle/streams/DefaultChunkColumnValue.md) - Method in class oracle.streams.[DefaultChunkColumnValue](oracle/streams/DefaultChunkColumnValue.md)
Gets the chunk operation offset.

[getChunkOperationSize()](oracle/streams/ChunkColumnValue.md) - Method in interface oracle.streams.[ChunkColumnValue](oracle/streams/ChunkColumnValue.md)
Gets the chunk operation size.

[getChunkOperationSize()](oracle/streams/DefaultChunkColumnValue.md) - Method in class oracle.streams.[DefaultChunkColumnValue](oracle/streams/DefaultChunkColumnValue.md)
Gets the chunk operation size.

[getChunkType()](oracle/streams/ChunkColumnValue.md) - Method in interface oracle.streams.[ChunkColumnValue](oracle/streams/ChunkColumnValue.md)
Gets the chunk type.

[getChunkType()](oracle/streams/DefaultChunkColumnValue.md) - Method in class oracle.streams.[DefaultChunkColumnValue](oracle/streams/DefaultChunkColumnValue.md)
Gets the chunk type.

[getColumnData()](oracle/streams/ColumnValue.md) - Method in interface oracle.streams.[ColumnValue](oracle/streams/ColumnValue.md)
Gets the column data.

[getColumnData()](oracle/streams/DefaultColumnValue.md) - Method in class oracle.streams.[DefaultColumnValue](oracle/streams/DefaultColumnValue.md)
Gets the column data.

[getColumnDataType()](oracle/streams/ColumnValue.md) - Method in interface oracle.streams.[ColumnValue](oracle/streams/ColumnValue.md)
Gets the column data type as defined in this interface.

[getColumnDataType()](oracle/streams/DefaultColumnValue.md) - Method in class oracle.streams.[DefaultColumnValue](oracle/streams/DefaultColumnValue.md)
Gets the column data type as defined in ColumnValue interface.

[getColumnName()](oracle/streams/ColumnValue.md) - Method in interface oracle.streams.[ColumnValue](oracle/streams/ColumnValue.md)
Gets the column name.

[getColumnName()](oracle/streams/DefaultColumnValue.md) - Method in class oracle.streams.[DefaultColumnValue](oracle/streams/DefaultColumnValue.md)
Gets the column name.

[getCommandType()](oracle/streams/AbstractLCR.md) - Method in class oracle.streams.[AbstractLCR](oracle/streams/AbstractLCR.md)
Gets the LCR command type executed in the DML or DDL statement.

[getCommandType()](oracle/streams/LCR.md) - Method in interface oracle.streams.[LCR](oracle/streams/LCR.md)
Gets the LCR command type executed in the DML or DDL statement.

[getCommitSCN()](oracle/streams/AbstractLCR.md) - Method in class oracle.streams.[AbstractLCR](oracle/streams/AbstractLCR.md)
Gets the LCR commit system change number (SCN) in the format of oracle.sql.NUMBER.

[getCommitSCNFromPosition(byte\[\])](oracle/streams/XStreamUtility.md) - Static method in class oracle.streams.[XStreamUtility](oracle/streams/XStreamUtility.md)
Gets the commit system change number (SCN) from a position.

[getCurrentSchema()](oracle/streams/DDLLCR.md) - Method in interface oracle.streams.[DDLLCR](oracle/streams/DDLLCR.md)
Gets the current schema name.

[getCurrentSchema()](oracle/streams/DefaultDDLLCR.md) - Method in class oracle.streams.[DefaultDDLLCR](oracle/streams/DefaultDDLLCR.md)
Gets the current schema name.

[getDateFormat()](oracle/streams/DefaultRowLCR.md) - Method in class oracle.streams.[DefaultRowLCR](oracle/streams/DefaultRowLCR.md)
Gets the date format of a row LCR.

[getDDLText()](oracle/streams/DDLLCR.md) - Method in interface oracle.streams.[DDLLCR](oracle/streams/DDLLCR.md)
Gets the DDL statement text.

[getDDLText()](oracle/streams/DefaultDDLLCR.md) - Method in class oracle.streams.[DefaultDDLLCR](oracle/streams/DefaultDDLLCR.md)
Gets the DDL statement text.

[getEditionName()](oracle/streams/DDLLCR.md) - Method in interface oracle.streams.[DDLLCR](oracle/streams/DDLLCR.md)
Gets the edition name.

[getEditionName()](oracle/streams/DefaultDDLLCR.md) - Method in class oracle.streams.[DefaultDDLLCR](oracle/streams/DefaultDDLLCR.md)
Gets the edition name.

[getErrorCode()](oracle/streams/StreamsException.md) - Method in exception oracle.streams.[StreamsException](oracle/streams/StreamsException.md)
Gets the Oracle-specific error code.

[getFetchLowWatermark()](oracle/streams/XStreamOut.md) - Method in class oracle.streams.[XStreamOut](oracle/streams/XStreamOut.md)
Gets fetch low watermark.

[getLastPosition()](oracle/streams/XStreamIn.md) - Method in class oracle.streams.[XStreamIn](oracle/streams/XStreamIn.md)
Gets last position.

[getLogonUser()](oracle/streams/DDLLCR.md) - Method in interface oracle.streams.[DDLLCR](oracle/streams/DDLLCR.md)
Gets the logon user name.

[getLogonUser()](oracle/streams/DefaultDDLLCR.md) - Method in class oracle.streams.[DefaultDDLLCR](oracle/streams/DefaultDDLLCR.md)
Gets the logon user name.

[getMessageTrackingLabel()](oracle/streams/AbstractLCR.md) - Method in class oracle.streams.[AbstractLCR](oracle/streams/AbstractLCR.md)
Gets the message tracking label of the LCR.

[getNewValues()](oracle/streams/DefaultRowLCR.md) - Method in class oracle.streams.[DefaultRowLCR](oracle/streams/DefaultRowLCR.md)
Gets the list of new column values in a row LCR.

[getNewValues()](oracle/streams/RowLCR.md) - Method in interface oracle.streams.[RowLCR](oracle/streams/RowLCR.md)
Gets the list of new column values in a row LCR.

[getNumAttributes()](oracle/streams/AbstractLCR.md) - Method in class oracle.streams.[AbstractLCR](oracle/streams/AbstractLCR.md)
Gets the total number of attributes in the LCR.

[getObjectName()](oracle/streams/AbstractLCR.md) - Method in class oracle.streams.[AbstractLCR](oracle/streams/AbstractLCR.md)
Gets the name of the object that is changed by the LCR.

[getObjectName()](oracle/streams/LCR.md) - Method in interface oracle.streams.[LCR](oracle/streams/LCR.md)
Gets the name of the object that is changed by the LCR.

[getObjectOwner()](oracle/streams/AbstractLCR.md) - Method in class oracle.streams.[AbstractLCR](oracle/streams/AbstractLCR.md)
Gets the owner of the object that is changed by the LCR.

[getObjectOwner()](oracle/streams/LCR.md) - Method in interface oracle.streams.[LCR](oracle/streams/LCR.md)
Gets the owner of the object that is changed by the LCR.

[getObjectType()](oracle/streams/DDLLCR.md) - Method in interface oracle.streams.[DDLLCR](oracle/streams/DDLLCR.md)
Gets the object type.

[getObjectType()](oracle/streams/DefaultDDLLCR.md) - Method in class oracle.streams.[DefaultDDLLCR](oracle/streams/DefaultDDLLCR.md)
Gets the object type.

[getOldestPosition()](oracle/streams/XStreamIn.md) - Method in class oracle.streams.[XStreamIn](oracle/streams/XStreamIn.md)
Gets the oldest position.

[getOldValues()](oracle/streams/DefaultRowLCR.md) - Method in class oracle.streams.[DefaultRowLCR](oracle/streams/DefaultRowLCR.md)
Gets the list of old column values in a row LCR.

[getOldValues()](oracle/streams/RowLCR.md) - Method in interface oracle.streams.[RowLCR](oracle/streams/RowLCR.md)
Gets the list of old column values in a row LCR.

[getPosition()](oracle/streams/AbstractLCR.md) - Method in class oracle.streams.[AbstractLCR](oracle/streams/AbstractLCR.md)
Gets the position of the current LCR.

[getPosition()](oracle/streams/LCR.md) - Method in interface oracle.streams.[LCR](oracle/streams/LCR.md)
Gets the position of the current LCR.

[getProcessedLowWatermark()](oracle/streams/XStreamIn.md) - Method in class oracle.streams.[XStreamIn](oracle/streams/XStreamIn.md)
Gets the processed low watermark.

[getRootName()](oracle/streams/AbstractLCR.md) - Method in class oracle.streams.[AbstractLCR](oracle/streams/AbstractLCR.md)
Gets the root name of the LCR.

[getSCN()](oracle/streams/AbstractLCR.md) - Method in class oracle.streams.[AbstractLCR](oracle/streams/AbstractLCR.md)
Gets the SCN of the current LCR in the format of oracle.sql.NUMBER.

[getSCNFromPosition(byte\[\])](oracle/streams/XStreamUtility.md) - Static method in class oracle.streams.[XStreamUtility](oracle/streams/XStreamUtility.md)
Gets the SCN from a position.

[getSourceDatabaseName()](oracle/streams/AbstractLCR.md) - Method in class oracle.streams.[AbstractLCR](oracle/streams/AbstractLCR.md)
Gets the global name of the source database.

[getSourceDatabaseName()](oracle/streams/LCR.md) - Method in interface oracle.streams.[LCR](oracle/streams/LCR.md)
Gets the global name of the source database.

[getSourceTime()](oracle/streams/AbstractLCR.md) - Method in class oracle.streams.[AbstractLCR](oracle/streams/AbstractLCR.md)
Gets the time when the LCR was created.

[getSourceTime()](oracle/streams/LCR.md) - Method in interface oracle.streams.[LCR](oracle/streams/LCR.md)
Gets the time when the LCR was created.

[getStatement(boolean)](oracle/streams/DefaultRowLCR.md) - Method in class oracle.streams.[DefaultRowLCR](oracle/streams/DefaultRowLCR.md)
Generates a SQL statement from the row LCR.

[getTag()](oracle/streams/AbstractLCR.md) - Method in class oracle.streams.[AbstractLCR](oracle/streams/AbstractLCR.md)
Gets the tag for the LCR.

[getTag()](oracle/streams/LCR.md) - Method in interface oracle.streams.[LCR](oracle/streams/LCR.md)
Gets the tag for the LCR.

[getTDEFlag()](oracle/streams/ColumnValue.md) - Method in interface oracle.streams.[ColumnValue](oracle/streams/ColumnValue.md)
Gets the Transparent Data Encryption (TDE) flag.

[getTDEFlag()](oracle/streams/DefaultColumnValue.md) - Method in class oracle.streams.[DefaultColumnValue](oracle/streams/DefaultColumnValue.md)
Gets the Transparent Data Encryption (TDE) flag.

[getTimeStampFormat()](oracle/streams/DefaultRowLCR.md) - Method in class oracle.streams.[DefaultRowLCR](oracle/streams/DefaultRowLCR.md)
Gets the timestamp format.

[getTransactionId()](oracle/streams/AbstractLCR.md) - Method in class oracle.streams.[AbstractLCR](oracle/streams/AbstractLCR.md)
Gets the transaction identifier of the LCR.

[getTransactionId()](oracle/streams/LCR.md) - Method in interface oracle.streams.[LCR](oracle/streams/LCR.md)
Gets the transaction identifier of the LCR.

[getWhereClause(boolean)](oracle/streams/DefaultRowLCR.md) - Method in class oracle.streams.[DefaultRowLCR](oracle/streams/DefaultRowLCR.md)
Gets a WHERE clause for the change that is encapsulated in the row LCR.

[getWhereClauseBinds()](oracle/streams/DefaultRowLCR.md) - Method in class oracle.streams.[DefaultRowLCR](oracle/streams/DefaultRowLCR.md)
Gets the bind array to be used with the WHERE clause generated by getWhereClause().

## H

[hasChunkData()](oracle/streams/DefaultRowLCR.md) - Method in class oracle.streams.[DefaultRowLCR](oracle/streams/DefaultRowLCR.md)
Indicates whether this LCR contains chunk data for LOB, LONG, or XMLTYPE columns.

[hasChunkData()](oracle/streams/RowLCR.md) - Method in interface oracle.streams.[RowLCR](oracle/streams/RowLCR.md)
Indicates whether this LCR contains chunk data for LOB, LONG, or XMLTYPE columns.

[hasIDKeyColumnsOnly()](oracle/streams/DefaultRowLCR.md) - Method in class oracle.streams.[DefaultRowLCR](oracle/streams/DefaultRowLCR.md)
Indicates whether the LCR only has identification key columns.

## I

[INSERT](oracle/streams/RowLCR.md) - Static variable in interface oracle.streams.[RowLCR](oracle/streams/RowLCR.md)
 

[INTERVALDS](oracle/streams/ColumnValue.md) - Static variable in interface oracle.streams.[ColumnValue](oracle/streams/ColumnValue.md)
 

[INTERVALYM](oracle/streams/ColumnValue.md) - Static variable in interface oracle.streams.[ColumnValue](oracle/streams/ColumnValue.md)
 

[is32kData()](oracle/streams/ColumnValue.md) - Method in interface oracle.streams.[ColumnValue](oracle/streams/ColumnValue.md)
Indicates whether the column is an extended size column (maximum size of 32767 bytes).

[is32kData()](oracle/streams/DefaultColumnValue.md) - Method in class oracle.streams.[DefaultColumnValue](oracle/streams/DefaultColumnValue.md)
Indicates whether the column is an extended size column (maximum size of 32767 bytes).

[isEmptyChunk()](oracle/streams/ChunkColumnValue.md) - Method in interface oracle.streams.[ChunkColumnValue](oracle/streams/ChunkColumnValue.md)
Indicates whether the chunk is empty.

[isEmptyChunk()](oracle/streams/DefaultChunkColumnValue.md) - Method in class oracle.streams.[DefaultChunkColumnValue](oracle/streams/DefaultChunkColumnValue.md)
Indicates whether the chunk is empty.

[isEndOfRow()](oracle/streams/ChunkColumnValue.md) - Method in interface oracle.streams.[ChunkColumnValue](oracle/streams/ChunkColumnValue.md)
Indicates whether the chunk is the end of the entire row change.

[isEndOfRow()](oracle/streams/DefaultChunkColumnValue.md) - Method in class oracle.streams.[DefaultChunkColumnValue](oracle/streams/DefaultChunkColumnValue.md)
Indicates whether the chunk is the end of the entire row change.

[isLastChunk()](oracle/streams/ChunkColumnValue.md) - Method in interface oracle.streams.[ChunkColumnValue](oracle/streams/ChunkColumnValue.md)
Indicates whether the chunk is the last one for the column.

[isLastChunk()](oracle/streams/DefaultChunkColumnValue.md) - Method in class oracle.streams.[DefaultChunkColumnValue](oracle/streams/DefaultChunkColumnValue.md)
Indicates whether the chunk is the last one for the column.

[isSequenceLCR()](oracle/streams/DefaultRowLCR.md) - Method in class oracle.streams.[DefaultRowLCR](oracle/streams/DefaultRowLCR.md)
Indicates whether the LCR is a sequence LCR, which is generated by accessing NEXTVAL of an Oracle sequence.

[isXMLDiff()](oracle/streams/ChunkColumnValue.md) - Method in interface oracle.streams.[ChunkColumnValue](oracle/streams/ChunkColumnValue.md)
Indicates whether the XMLType chunk is an XMLDiff.

[isXMLDiff()](oracle/streams/DefaultChunkColumnValue.md) - Method in class oracle.streams.[DefaultChunkColumnValue](oracle/streams/DefaultChunkColumnValue.md)
Indicates whether the chunk is an XMLDiff.

## L

[LCR](oracle/streams/LCR.md) - Interface in [oracle.streams](oracle/streams/package-summary.md)
The LCR interface encapsulates information about the logical change record (LCR).

[LOB_ERASE](oracle/streams/RowLCR.md) - Static variable in interface oracle.streams.[RowLCR](oracle/streams/RowLCR.md)
 

[LOB_TRIM](oracle/streams/RowLCR.md) - Static variable in interface oracle.streams.[RowLCR](oracle/streams/RowLCR.md)
 

[LOB_WRITE](oracle/streams/RowLCR.md) - Static variable in interface oracle.streams.[RowLCR](oracle/streams/RowLCR.md)
 

[LONG](oracle/streams/ChunkColumnValue.md) - Static variable in interface oracle.streams.[ChunkColumnValue](oracle/streams/ChunkColumnValue.md)
 

[LONGRAW](oracle/streams/ChunkColumnValue.md) - Static variable in interface oracle.streams.[ChunkColumnValue](oracle/streams/ChunkColumnValue.md)
 

## M

[MAX_POS_LENGTH](oracle/streams/XStreamUtility.md) - Static variable in class oracle.streams.[XStreamUtility](oracle/streams/XStreamUtility.md)
 

## N

[NCLOB](oracle/streams/ChunkColumnValue.md) - Static variable in interface oracle.streams.[ChunkColumnValue](oracle/streams/ChunkColumnValue.md)
 

[NEW_COLUMN_ONLY_MODE](oracle/streams/XStreamOut.md) - Static variable in class oracle.streams.[XStreamOut](oracle/streams/XStreamOut.md)
This column list mode allows users to receive LCRs with only new columns in the new value list.

[NUMBER](oracle/streams/ColumnValue.md) - Static variable in interface oracle.streams.[ColumnValue](oracle/streams/ColumnValue.md)
 

## O

[oracle.streams](oracle/streams/package-summary.md) - package oracle.streams
 

## P

[POS_LENGTH_V1](oracle/streams/XStreamUtility.md) - Static variable in class oracle.streams.[XStreamUtility](oracle/streams/XStreamUtility.md)
 

[POS_LENGTH_V2](oracle/streams/XStreamUtility.md) - Static variable in class oracle.streams.[XStreamUtility](oracle/streams/XStreamUtility.md)
 

[POS_VERSION_V1](oracle/streams/XStreamUtility.md) - Static variable in class oracle.streams.[XStreamUtility](oracle/streams/XStreamUtility.md)
 

[POS_VERSION_V2](oracle/streams/XStreamUtility.md) - Static variable in class oracle.streams.[XStreamUtility](oracle/streams/XStreamUtility.md)
 

[processChunk(ChunkColumnValue)](oracle/streams/XStreamLCRCallbackHandler.md) - Method in interface oracle.streams.[XStreamLCRCallbackHandler](oracle/streams/XStreamLCRCallbackHandler.md)
The callback method for processing chunk data received from an XStream outbound server for an LCR received through the processLCR callback method.

[processLCR(LCR)](oracle/streams/XStreamLCRCallbackHandler.md) - Method in interface oracle.streams.[XStreamLCRCallbackHandler](oracle/streams/XStreamLCRCallbackHandler.md)
The callback method for processing an LCR recevied from an XStream outbound server.

## R

[RAW](oracle/streams/ColumnValue.md) - Static variable in interface oracle.streams.[ColumnValue](oracle/streams/ColumnValue.md)
 

[receiveChunk(int)](oracle/streams/XStreamOut.md) - Method in class oracle.streams.[XStreamOut](oracle/streams/XStreamOut.md)
Receives chunk data in non-callback mode.

[receiveLCR(int)](oracle/streams/XStreamOut.md) - Method in class oracle.streams.[XStreamOut](oracle/streams/XStreamOut.md)
Receives one LCR in non-callback mode.

[receiveLCRCallback(XStreamLCRCallbackHandler, int)](oracle/streams/XStreamOut.md) - Method in class oracle.streams.[XStreamOut](oracle/streams/XStreamOut.md)
Receives a stream of LCRs in callback mode.

[RowLCR](oracle/streams/RowLCR.md) - Interface in [oracle.streams](oracle/streams/package-summary.md)
The RowLCR interface encapsulates the information about a row logical change record (LCR).

## S

[SCN_START_V1](oracle/streams/XStreamUtility.md) - Static variable in class oracle.streams.[XStreamUtility](oracle/streams/XStreamUtility.md)
 

[SCN_START_V2](oracle/streams/XStreamUtility.md) - Static variable in class oracle.streams.[XStreamUtility](oracle/streams/XStreamUtility.md)
 

[sendChunk(ChunkColumnValue, int)](oracle/streams/XStreamIn.md) - Method in class oracle.streams.[XStreamIn](oracle/streams/XStreamIn.md)
Sends chunk data in non-callback mode.

[sendLCR(LCR, int)](oracle/streams/XStreamIn.md) - Method in class oracle.streams.[XStreamIn](oracle/streams/XStreamIn.md)
Sends one LCR in non-callback mode.

[sendLCRCallback(XStreamLCRCallbackHandler, int)](oracle/streams/XStreamIn.md) - Method in class oracle.streams.[XStreamIn](oracle/streams/XStreamIn.md)
Sends a stream of LCRs in callback mode.

[set32kData(boolean)](oracle/streams/ColumnValue.md) - Method in interface oracle.streams.[ColumnValue](oracle/streams/ColumnValue.md)
Sets the extended size column flag (maximum size of 32767 bytes).

[set32kData(boolean)](oracle/streams/DefaultColumnValue.md) - Method in class oracle.streams.[DefaultColumnValue](oracle/streams/DefaultColumnValue.md)
Sets the extended size column flag (maximum size of 32767 bytes).

[setAttribute(Object, Object)](oracle/streams/AbstractLCR.md) - Method in class oracle.streams.[AbstractLCR](oracle/streams/AbstractLCR.md)
Sets attribute by providing the name and value pair; the name is used as the hash key.

[setAttribute(Object, Object)](oracle/streams/LCR.md) - Method in interface oracle.streams.[LCR](oracle/streams/LCR.md)
Sets attribute by providing the name and value pair; the name is used as the hash key.

[setBaseTableName(String)](oracle/streams/DDLLCR.md) - Method in interface oracle.streams.[DDLLCR](oracle/streams/DDLLCR.md)
Sets the base table name.

[setBaseTableName(String)](oracle/streams/DefaultDDLLCR.md) - Method in class oracle.streams.[DefaultDDLLCR](oracle/streams/DefaultDDLLCR.md)
Sets the base table name.

[setBaseTableOwner(String)](oracle/streams/DDLLCR.md) - Method in interface oracle.streams.[DDLLCR](oracle/streams/DDLLCR.md)
Sets the base table owner.

[setBaseTableOwner(String)](oracle/streams/DefaultDDLLCR.md) - Method in class oracle.streams.[DefaultDDLLCR](oracle/streams/DefaultDDLLCR.md)
Sets the base table owner.

[setCharSetId(int)](oracle/streams/ChunkColumnValue.md) - Method in interface oracle.streams.[ChunkColumnValue](oracle/streams/ChunkColumnValue.md)
Sets the character set ID for an XMLTYPE chunk.

[setCharsetId(int)](oracle/streams/ColumnValue.md) - Method in interface oracle.streams.[ColumnValue](oracle/streams/ColumnValue.md)
Sets the Oracle character set ID for the column.

[setCharSetId(int)](oracle/streams/DefaultChunkColumnValue.md) - Method in class oracle.streams.[DefaultChunkColumnValue](oracle/streams/DefaultChunkColumnValue.md)
Sets the character set ID for an XMLTYPE chunk.

[setCharsetId(int)](oracle/streams/DefaultColumnValue.md) - Method in class oracle.streams.[DefaultColumnValue](oracle/streams/DefaultColumnValue.md)
Sets the Oracle character set ID for the column.

[setChunkDataFlag(boolean)](oracle/streams/DefaultRowLCR.md) - Method in class oracle.streams.[DefaultRowLCR](oracle/streams/DefaultRowLCR.md)
Sets the chunkDataFlag.

[setChunkDataFlag(boolean)](oracle/streams/RowLCR.md) - Method in interface oracle.streams.[RowLCR](oracle/streams/RowLCR.md)
Sets the chunkDataFlag.

[setChunkOffset(BigInteger)](oracle/streams/ChunkColumnValue.md) - Method in interface oracle.streams.[ChunkColumnValue](oracle/streams/ChunkColumnValue.md)
Sets the chunk operation offset.

[setChunkOffset(BigInteger)](oracle/streams/DefaultChunkColumnValue.md) - Method in class oracle.streams.[DefaultChunkColumnValue](oracle/streams/DefaultChunkColumnValue.md)
Sets the chunk operation offset.

[setChunkOperationSize(BigInteger)](oracle/streams/ChunkColumnValue.md) - Method in interface oracle.streams.[ChunkColumnValue](oracle/streams/ChunkColumnValue.md)
Sets the chunk operation size.

[setChunkOperationSize(BigInteger)](oracle/streams/DefaultChunkColumnValue.md) - Method in class oracle.streams.[DefaultChunkColumnValue](oracle/streams/DefaultChunkColumnValue.md)
Sets the chunk operation size.

[setChunkType(int)](oracle/streams/ChunkColumnValue.md) - Method in interface oracle.streams.[ChunkColumnValue](oracle/streams/ChunkColumnValue.md)
Sets the chunk type.

[setChunkType(int)](oracle/streams/DefaultChunkColumnValue.md) - Method in class oracle.streams.[DefaultChunkColumnValue](oracle/streams/DefaultChunkColumnValue.md)
Sets the chunk type.

[setColumnData(Datum, int)](oracle/streams/ColumnValue.md) - Method in interface oracle.streams.[ColumnValue](oracle/streams/ColumnValue.md)
Sets the column data.

[setColumnData(Datum)](oracle/streams/DefaultChunkColumnValue.md) - Method in class oracle.streams.[DefaultChunkColumnValue](oracle/streams/DefaultChunkColumnValue.md)
Sets the column data for a ChunkColumnValue.

[setColumnData(Datum, int)](oracle/streams/DefaultChunkColumnValue.md) - Method in class oracle.streams.[DefaultChunkColumnValue](oracle/streams/DefaultChunkColumnValue.md)
Sets the column data.

[setColumnData(Datum, int)](oracle/streams/DefaultColumnValue.md) - Method in class oracle.streams.[DefaultColumnValue](oracle/streams/DefaultColumnValue.md)
Sets the column data.

[setColumnName(String)](oracle/streams/ColumnValue.md) - Method in interface oracle.streams.[ColumnValue](oracle/streams/ColumnValue.md)
Sets the column name.

[setColumnName(String)](oracle/streams/DefaultColumnValue.md) - Method in class oracle.streams.[DefaultColumnValue](oracle/streams/DefaultColumnValue.md)
Sets the column name.

[setCommandType(String)](oracle/streams/AbstractLCR.md) - Method in class oracle.streams.[AbstractLCR](oracle/streams/AbstractLCR.md)
Sets the command type in the LCR.

[setCommandType(String)](oracle/streams/LCR.md) - Method in interface oracle.streams.[LCR](oracle/streams/LCR.md)
Sets the command type in the LCR.

[setCurrentSchema(String)](oracle/streams/DDLLCR.md) - Method in interface oracle.streams.[DDLLCR](oracle/streams/DDLLCR.md)
Sets the current schema.

[setCurrentSchema(String)](oracle/streams/DefaultDDLLCR.md) - Method in class oracle.streams.[DefaultDDLLCR](oracle/streams/DefaultDDLLCR.md)
Sets the current schema.

[setDateFormat(String)](oracle/streams/DefaultRowLCR.md) - Method in class oracle.streams.[DefaultRowLCR](oracle/streams/DefaultRowLCR.md)
Sets the date format that is used to convert a DATE value to a String value.

[setDDLText(String)](oracle/streams/DDLLCR.md) - Method in interface oracle.streams.[DDLLCR](oracle/streams/DDLLCR.md)
Sets the DDL statement text.

[setDDLText(String)](oracle/streams/DefaultDDLLCR.md) - Method in class oracle.streams.[DefaultDDLLCR](oracle/streams/DefaultDDLLCR.md)
Sets the DDL statement text.

[setEditionName(String)](oracle/streams/DDLLCR.md) - Method in interface oracle.streams.[DDLLCR](oracle/streams/DDLLCR.md)
Sets the edition name.

[setEditionName(String)](oracle/streams/DefaultDDLLCR.md) - Method in class oracle.streams.[DefaultDDLLCR](oracle/streams/DefaultDDLLCR.md)
Sets the edition name.

[setEmptyChunk(boolean)](oracle/streams/ChunkColumnValue.md) - Method in interface oracle.streams.[ChunkColumnValue](oracle/streams/ChunkColumnValue.md)
Sets the empty chunk flag.

[setEmptyChunk(boolean)](oracle/streams/DefaultChunkColumnValue.md) - Method in class oracle.streams.[DefaultChunkColumnValue](oracle/streams/DefaultChunkColumnValue.md)
Sets the empty chunk flag.

[setEndOfRow(boolean)](oracle/streams/ChunkColumnValue.md) - Method in interface oracle.streams.[ChunkColumnValue](oracle/streams/ChunkColumnValue.md)
Sets the endOfRow chunk flag.

[setEndOfRow(boolean)](oracle/streams/DefaultChunkColumnValue.md) - Method in class oracle.streams.[DefaultChunkColumnValue](oracle/streams/DefaultChunkColumnValue.md)
Sets the endOfRow chunk flag.

[setIDKeyColumnsOnly(boolean)](oracle/streams/DefaultRowLCR.md) - Method in class oracle.streams.[DefaultRowLCR](oracle/streams/DefaultRowLCR.md)
Sets whether or not this LCR only has identification key columns.

[setLastChunk(boolean)](oracle/streams/ChunkColumnValue.md) - Method in interface oracle.streams.[ChunkColumnValue](oracle/streams/ChunkColumnValue.md)
Sets the last chunk flag.

[setLastChunk(boolean)](oracle/streams/DefaultChunkColumnValue.md) - Method in class oracle.streams.[DefaultChunkColumnValue](oracle/streams/DefaultChunkColumnValue.md)
Sets the last chunk flag.

[setLogonUser(String)](oracle/streams/DDLLCR.md) - Method in interface oracle.streams.[DDLLCR](oracle/streams/DDLLCR.md)
Sets the logon user name.

[setLogonUser(String)](oracle/streams/DefaultDDLLCR.md) - Method in class oracle.streams.[DefaultDDLLCR](oracle/streams/DefaultDDLLCR.md)
Sets the logon user name.

[setMessageTrackingLabel(String)](oracle/streams/AbstractLCR.md) - Method in class oracle.streams.[AbstractLCR](oracle/streams/AbstractLCR.md)
Sets the message tracking label of the LCR.

[setNewValues(ColumnValue\[\])](oracle/streams/DefaultRowLCR.md) - Method in class oracle.streams.[DefaultRowLCR](oracle/streams/DefaultRowLCR.md)
Sets the new column values list for a RowLCR.

[setNewValues(ColumnValue\[\])](oracle/streams/RowLCR.md) - Method in interface oracle.streams.[RowLCR](oracle/streams/RowLCR.md)
Sets the new column values list for a row LCR.

[setObjectName(String)](oracle/streams/AbstractLCR.md) - Method in class oracle.streams.[AbstractLCR](oracle/streams/AbstractLCR.md)
Sets the name of the object that is changed by the LCR.

[setObjectName(String)](oracle/streams/LCR.md) - Method in interface oracle.streams.[LCR](oracle/streams/LCR.md)
Sets the name of the object that is changed by the LCR.

[setObjectOwner(String)](oracle/streams/AbstractLCR.md) - Method in class oracle.streams.[AbstractLCR](oracle/streams/AbstractLCR.md)
Sets the owner of the object that is changed by the LCR .

[setObjectOwner(String)](oracle/streams/LCR.md) - Method in interface oracle.streams.[LCR](oracle/streams/LCR.md)
Sets the owner of the object that is changed by the LCR .

[setObjectType(String)](oracle/streams/DDLLCR.md) - Method in interface oracle.streams.[DDLLCR](oracle/streams/DDLLCR.md)
Sets the object type.

[setObjectType(String)](oracle/streams/DefaultDDLLCR.md) - Method in class oracle.streams.[DefaultDDLLCR](oracle/streams/DefaultDDLLCR.md)
Sets the object type.

[setOldValues(ColumnValue\[\])](oracle/streams/DefaultRowLCR.md) - Method in class oracle.streams.[DefaultRowLCR](oracle/streams/DefaultRowLCR.md)
Sets the old column values list for a row LCR.

[setOldValues(ColumnValue\[\])](oracle/streams/RowLCR.md) - Method in interface oracle.streams.[RowLCR](oracle/streams/RowLCR.md)
Sets the old column values list for a row LCR.

[setPosition(byte\[\])](oracle/streams/AbstractLCR.md) - Method in class oracle.streams.[AbstractLCR](oracle/streams/AbstractLCR.md)
Sets the position in the LCR.

[setPosition(byte\[\])](oracle/streams/LCR.md) - Method in interface oracle.streams.[LCR](oracle/streams/LCR.md)
Sets the position in the LCR.

[setProcessedLowWatermark(byte\[\], int)](oracle/streams/XStreamOut.md) - Method in class oracle.streams.[XStreamOut](oracle/streams/XStreamOut.md)
Sets processed low watermark.

[setProcessedLowWatermark(byte\[\], byte\[\], int)](oracle/streams/XStreamOut.md) - Method in class oracle.streams.[XStreamOut](oracle/streams/XStreamOut.md)
Sets processed low watermark.

[setRootName(String)](oracle/streams/AbstractLCR.md) - Method in class oracle.streams.[AbstractLCR](oracle/streams/AbstractLCR.md)
Sets the root name of the LCR.

[setSequenceLCRFlag(boolean)](oracle/streams/DefaultRowLCR.md) - Method in class oracle.streams.[DefaultRowLCR](oracle/streams/DefaultRowLCR.md)
Sets the sequence LCR flag.

[setSourceDatabaseName(String)](oracle/streams/AbstractLCR.md) - Method in class oracle.streams.[AbstractLCR](oracle/streams/AbstractLCR.md)
Sets the source database name of the object that is changed by the LCR.

[setSourceDatabaseName(String)](oracle/streams/LCR.md) - Method in interface oracle.streams.[LCR](oracle/streams/LCR.md)
Sets the source database name of the object that is changed by the LCR.

[setSourceTime(DATE)](oracle/streams/AbstractLCR.md) - Method in class oracle.streams.[AbstractLCR](oracle/streams/AbstractLCR.md)
Sets the source timestamp when the LCR was created.

[setSourceTime(DATE)](oracle/streams/LCR.md) - Method in interface oracle.streams.[LCR](oracle/streams/LCR.md)
Sets the source timestamp when the LCR was created.

[setTag(byte\[\])](oracle/streams/AbstractLCR.md) - Method in class oracle.streams.[AbstractLCR](oracle/streams/AbstractLCR.md)
Sets the LCR tag information.

[setTag(byte\[\])](oracle/streams/LCR.md) - Method in interface oracle.streams.[LCR](oracle/streams/LCR.md)
Sets the tag for the LCR.

[setTDEFlag(boolean)](oracle/streams/ColumnValue.md) - Method in interface oracle.streams.[ColumnValue](oracle/streams/ColumnValue.md)
Sets the Transparent Data Encryption (TDE) flag.

[setTDEFlag(boolean)](oracle/streams/DefaultColumnValue.md) - Method in class oracle.streams.[DefaultColumnValue](oracle/streams/DefaultColumnValue.md)
Sets the TDE flag.

[setTimeStampFormat(String)](oracle/streams/DefaultRowLCR.md) - Method in class oracle.streams.[DefaultRowLCR](oracle/streams/DefaultRowLCR.md)
Sets the timestamp format that is used to convert a TIMESTAMP value to a String value

[setTransactionId(String)](oracle/streams/AbstractLCR.md) - Method in class oracle.streams.[AbstractLCR](oracle/streams/AbstractLCR.md)
Sets the transaction identifier for the LCR.

[setTransactionId(String)](oracle/streams/LCR.md) - Method in interface oracle.streams.[LCR](oracle/streams/LCR.md)
Sets the transaction identifier for the LCR.

[setXMLDiff(boolean)](oracle/streams/ChunkColumnValue.md) - Method in interface oracle.streams.[ChunkColumnValue](oracle/streams/ChunkColumnValue.md)
Sets the XMLDiff flag.

[setXMLDiff(boolean)](oracle/streams/DefaultChunkColumnValue.md) - Method in class oracle.streams.[DefaultChunkColumnValue](oracle/streams/DefaultChunkColumnValue.md)
Sets the XMLDiff flag.

[StreamsException](oracle/streams/StreamsException.md) - Exception in [oracle.streams](oracle/streams/package-summary.md)
The StreamsException class provides information about Oracle Streams errors.

[StreamsException(String)](oracle/streams/StreamsException.md) - Constructor for exception oracle.streams.[StreamsException](oracle/streams/StreamsException.md)
Constructs a StreamsException object with message only.

[StreamsException(String, int)](oracle/streams/StreamsException.md) - Constructor for exception oracle.streams.[StreamsException](oracle/streams/StreamsException.md)
Constructs a StreamsException object with message and error code.

[StreamsException(String, Throwable)](oracle/streams/StreamsException.md) - Constructor for exception oracle.streams.[StreamsException](oracle/streams/StreamsException.md)
Constructs a StreamsException object with message and cause.

## T

[TIMESTAMP](oracle/streams/ColumnValue.md) - Static variable in interface oracle.streams.[ColumnValue](oracle/streams/ColumnValue.md)
 

[TIMESTAMPLTZ](oracle/streams/ColumnValue.md) - Static variable in interface oracle.streams.[ColumnValue](oracle/streams/ColumnValue.md)
 

[TIMESTAMPTZ](oracle/streams/ColumnValue.md) - Static variable in interface oracle.streams.[ColumnValue](oracle/streams/ColumnValue.md)
 

[toString()](oracle/streams/DefaultChunkColumnValue.md) - Method in class oracle.streams.[DefaultChunkColumnValue](oracle/streams/DefaultChunkColumnValue.md)
 

[toString()](oracle/streams/DefaultColumnValue.md) - Method in class oracle.streams.[DefaultColumnValue](oracle/streams/DefaultColumnValue.md)
 

[toString()](oracle/streams/DefaultRowLCR.md) - Method in class oracle.streams.[DefaultRowLCR](oracle/streams/DefaultRowLCR.md)
 

## U

[UPDATE](oracle/streams/RowLCR.md) - Static variable in interface oracle.streams.[RowLCR](oracle/streams/RowLCR.md)
 

## X

[XMLTYPE](oracle/streams/ChunkColumnValue.md) - Static variable in interface oracle.streams.[ChunkColumnValue](oracle/streams/ChunkColumnValue.md)
 

[XStreamIn](oracle/streams/XStreamIn.md) - Class in [oracle.streams](oracle/streams/package-summary.md)
The XStreamIn class provides APIs for using Oracle XStream In.

[XStreamLCRCallbackHandler](oracle/streams/XStreamLCRCallbackHandler.md) - Interface in [oracle.streams](oracle/streams/package-summary.md)
The XStreamLCRCallbackHandler interface enables clients to receive LCRs and chunk data from an XStream outbound server or send LCRs and chunk data to an XStream inbound server using a callback mechanism.

[XStreamOut](oracle/streams/XStreamOut.md) - Class in [oracle.streams](oracle/streams/package-summary.md)
The XStreamOut class provides APIs for using Oracle XStream Out.

[XStreamUtility](oracle/streams/XStreamUtility.md) - Class in [oracle.streams](oracle/streams/package-summary.md)
The XStreamUtility class provides utility methods for using XStream APIs.

[XStreamUtility()](oracle/streams/XStreamUtility.md) - Constructor for class oracle.streams.[XStreamUtility](oracle/streams/XStreamUtility.md)
 

A B C D E F G H I L M N O P R S T U X 

Skip navigation links

- [Package](oracle/streams/package-summary.md)
- Class
- [Tree](overview-tree.md)
- [Deprecated](deprecated-list.md)
- Index
- [Help](help-doc.md)

**Oracle® Database XStream Java API Reference
19c**
E96285-02

- Prev
- Next

<!-- -->

- [Frames](index.md)
- No Frames

<!-- -->

- [All Classes](allclasses-noframe.md)

Copyright © 2001, 2019, Oracle and/or its affiliates. All Rights Reserved.
