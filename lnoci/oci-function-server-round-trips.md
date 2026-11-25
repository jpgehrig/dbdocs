This appendix provides information about server round-trips incurred during various OCI calls.

This information can help programmers to determine the most efficient way to accomplish a particular task in an application. A server round-trip is defined as the trip from the client to the server and back to the client.

When using client-side SQL, OCI provides:

- Enhanced array data manipulation language (DML) capability for arrays

- Ability to associate a commit request with a run to reduce round-trips

- Optimization for queries using transparent prefetch buffers to reduce round-trips

As is often the case, there are tradeoffs. For example, for queries the trade off is often arraysize and prefetch size versus the number of underlying fetches.

**See Also:**

- [Using SQL Statements in OCI](using-sql_statements-in-oci.md) for an overview and more specific information on tips to reduce server round-trips

- [OCI Array Interface](binding-and-defining-in-oci.md) to significantly reduce round-trips to the database when you are updating or inserting a large volume of data

- [About Setting Prefetch Count](using-sql_statements-in-oci.md) to minimize server round-trips

.

This appendix contains these topics:

- Relational Function Round-Trips

- LOB Function Round-Trips

- Object and Cache Function Round-Trips

- Describe Operation Round-Trips

- Data Type Mapping and Manipulation Function Round-Trips

- Any Type and Data Function Round-Trips

- Other Local Functions

### C.1 Relational Function Round-Trips

Describes for each OCI relational function the number of server round-trips.

Table C-1 lists the number of server round-trips required by each OCI relational function.

Table C-1 Server Round-Trips for Relational Operations

| Function                    | Number of Server Round-Trips                                                                                                                                                                         |
|:----------------------------|:-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `OCIBreak()`                | 1                                                                                                                                                                                                    |
| `OCIDBShutdown()`           | 1                                                                                                                                                                                                    |
| `OCIDBStartup()`            | 1                                                                                                                                                                                                    |
| `OCIEnvCreate()`            | 0                                                                                                                                                                                                    |
| `OCIEnvInit()`              | 0                                                                                                                                                                                                    |
| `OCIErrorGet()`             | 0                                                                                                                                                                                                    |
| `OCIInitialize()`           | 0                                                                                                                                                                                                    |
| `OCILdaToSvcCtx()`          | 0                                                                                                                                                                                                    |
| `OCILogoff()`               | 1                                                                                                                                                                                                    |
| `OCILogon()`                | 1                                                                                                                                                                                                    |
| `OCILogon2()`               | Connection pool or session pool: same as OCISessionGet()<br>Normal: 2 (depends on authentication and TAF situation)                                                                                  |
| `OCIPasswordChange()`       | 1                                                                                                                                                                                                    |
| `OCIPing()`                 | 1                                                                                                                                                                                                    |
| `OCIReset()`                | 0                                                                                                                                                                                                    |
| `OCIServerAttach()`         | 1                                                                                                                                                                                                    |
| `OCIServerDetach()`         | 1                                                                                                                                                                                                    |
| `OCIServerVersion()`        | 1                                                                                                                                                                                                    |
| `OCISessionBegin()`         | 1                                                                                                                                                                                                    |
| `OCISessionEnd()`           | 1                                                                                                                                                                                                    |
| `OCISessionGet()`           | Session pool: 0 - increment of logins. Connection pool: 1 to (1+ (increment \* logins)). Depends on cache hit: one for the user session, optional increment for primary sessions.<br>Normal: 1 login |
| `OCISessionPoolCreate()`    | sessMin \* logins                                                                                                                                                                                    |
| `OCISessionPoolDestroy()`   | Sessions in cache \* logoffs                                                                                                                                                                         |
| `OCISessionRelease()`       | Session pooling: 0, except when explicit session destroys flag set<br>Normal: 1 login                                                                                                                |
| `OCIStmtExecute()`          | 1                                                                                                                                                                                                    |
| `OCIStmtFetch()`            | 0 or 1                                                                                                                                                                                               |
| `OCIStmtFetch2()`           | 0 in prefetch, otherwise 1                                                                                                                                                                           |
| `OCIStmtGetPieceInfo()`     | 1                                                                                                                                                                                                    |
| `OCIStmtPrepare()`          | 0                                                                                                                                                                                                    |
| `OCIStmtPrepare2()`         | 0                                                                                                                                                                                                    |
| `OCIStmtSetPieceInfo()`     | 0                                                                                                                                                                                                    |
| `OCISvcCtxToLda()`          | 0                                                                                                                                                                                                    |
| `OCITerminate()`            | 1                                                                                                                                                                                                    |
| `OCITransCommit()`          | 1                                                                                                                                                                                                    |
| `OCITransDetach()`          | 1                                                                                                                                                                                                    |
| `OCITransForget()`          | 1                                                                                                                                                                                                    |
| `OCITransPrepare()`         | 1                                                                                                                                                                                                    |
| `OCItransRollback()`        | 1                                                                                                                                                                                                    |
| `OCITransStart()`           | 1                                                                                                                                                                                                    |
| `OCIUserCallbackGet()`      | 0                                                                                                                                                                                                    |
| `OCIUserCallbackRegister()` | 0                                                                                                                                                                                                    |

### C.2 LOB Function Round-Trips

Describes for each OCI LOB function the number of server round-trips.

Table C-2 lists the server round-trips incurred by the `OCILob` calls.

**Note:**

To minimize the number of round-trips, you can use the data interface for LOBs. You can bind or define character data for a `CLOB` column or `RAW` data for a `BLOB` column.

For calls whose number of round-trips is "0 or 1," if LOB buffering is on, and the request can be satisfied in the client, no round-trips are incurred.

Table C-2 Server Round-Trips for OCILob Calls

| Function                   | Number of Server Round-Trips                                                           |
|:---------------------------|:---------------------------------------------------------------------------------------|
| `OCILobAppend()`           | 1                                                                                      |
| `OCILobArrayRead()`        | 1                                                                                      |
| `OCILobArraywrite()`       | 1                                                                                      |
| `OCILobAssign()`           | 0                                                                                      |
| `OCILobCharSetForm()`      | 0                                                                                      |
| `OCILobCharSetId()`        | 0                                                                                      |
| `OCILobClose()`            | 1                                                                                      |
| `OCILobCopy()`             | 1                                                                                      |
| `OCILobCopy2()`            | 1                                                                                      |
| `OCILobCreateTemporary()`  | 1                                                                                      |
| `OCILobDisableBuffering()` | 0                                                                                      |
| `OCILobEnableBuffering()`  | 0                                                                                      |
| `OCILobErase()`            | 1                                                                                      |
| `OCILobErase2()`           | 1                                                                                      |
| `OCILobFileClose()`        | 1                                                                                      |
| `OCILobFileCloseAll()`     | 1                                                                                      |
| `OCILobFileExists()`       | 1                                                                                      |
| `OCILobFileGetName()`      | 0                                                                                      |
| `OCILobFileIsOpen()`       | 1                                                                                      |
| `OCILobFileOpen()`         | 1                                                                                      |
| `OCILobFileSetName()`      | 0                                                                                      |
| `OCILobFlushBuffer()`      | 1 for each modified page in the buffer for this LOB                                    |
| `OCILobFreeTemporary()`    | 1                                                                                      |
| `OCILobGetChunkSize()`     | 1                                                                                      |
| `OCILobGetLength()`        | 1                                                                                      |
| `OCILobGetLength2()`       | 1                                                                                      |
| `OCILobGetStorageLimit()`  | 1                                                                                      |
| `OCILobIsEqual()`          | 0                                                                                      |
| `OCILobIsOpen()`           | 1                                                                                      |
| `OCILobIsTemporary()`      | 0                                                                                      |
| `OCILobLoadFromFile()`     | 1                                                                                      |
| `OCILobLoadFromFile2()`    | 1                                                                                      |
| `OCILobLocatorAssign()`    | 1 round-trip if either the source or the destination locator refers to a temporary LOB |
| `OCILobLocatorIsInit()`    | 0                                                                                      |
| `OCILobOpen()`             | 1                                                                                      |
| `OCILobRead()`             | 0 or 1                                                                                 |
| `OCILobRead2()`            | 0 or 1                                                                                 |
| `OCILobTrim()`             | 1                                                                                      |
| `OCILobTrim2()`            | 1                                                                                      |
| `OCILobWrite()`            | 0 or 1                                                                                 |
| `OCILobWrite2()`           | 0 or 1                                                                                 |
| `OCILobWriteAppend()`      | 0 or 1                                                                                 |
| `OCILobWriteAppend2()`     | 0 or 1                                                                                 |

**See Also:**

- [About Binding LOB Data](binding-and-defining-in-oci.md) for usage and examples for both `INSERT` and `UPDATE` statements

- [About Defining LOB Data](binding-and-defining-in-oci.md)

  for usage and examples of `SELECT` statements

### C.3 Object and Cache Function Round-Trips

Describes for each OCI object and cache function the number of server round-trips.

Table C-3 lists the number of server round-trips required for the object and cache functions. These values assume the cache is in a warm state, meaning that the type descriptor objects required by the application have been loaded.

Table C-3 Server Round-Trips for Object and Cache Functions

| Function                     | Number of Server Round-Trips                   |
|:-----------------------------|:-----------------------------------------------|
| `OCICacheFlush()`            | 1                                              |
| `OCICacheFree()`             | 0                                              |
| `OCICacheRefresh()`          | 1                                              |
| `OCICacheUnmark()`           | 0                                              |
| `OCICacheUnpin()`            | 0                                              |
| `OCIObjectArrayPin()`        | 1                                              |
| `OCIObjectCopy()`            | 0                                              |
| `OCIObjectExists()`          | 0                                              |
| `OCIObjectFlush()`           | 1                                              |
| `OCIObjectFree()`            | 0                                              |
| `OCIObjectGetInd()`          | 0                                              |
| `OCIObjectGetObjectRef()`    | 0                                              |
| `OCIObjectGetTypeRef()`      | 0                                              |
| `OCIObjectIsDirty()`         | 0                                              |
| `OCIObjectIsLocked()`        | 0                                              |
| `OCIObjectLock()`            | 1                                              |
| `OCIObjectMarkDelete()`      | 0                                              |
| `OCIObjectMarkDeleteByRef()` | 0                                              |
| `OCIObjectMarkUpdate()`      | 0                                              |
| `OCIObjectNew()`             | 0                                              |
| `OCIObjectPin()`             | 1; 0 if the desired object is already in cache |
| `OCIObjectPinCountReset()`   | 0                                              |
| `OCIObjectPinTable()`        | 1                                              |
| `OCIObjectRefresh()`         | 1                                              |
| `OCIObjectUnmark()`          | 0                                              |
| `OCIObjectUnmarkByRef()`     | 0                                              |
| `OCIObjectUnpin()`           | 0                                              |

### C.4 Describe Operation Round-Trips

Describes for each OCI operation function the number of server round-trips.

Table C-4 lists the number of server round-trips required by `OCIDescribeAny()`, `OCIAttrGet()`, and `OCIParamGet()`.

Table C-4 Server Round-Trips for Describe Operations

| Function           | Number of Server Round-Trips                                                                                                                                                                                                                                                                                                                                                                                                                                 |
|:-------------------|:-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `OCIAttrGet()`     | 2 round-trips to describe a type if the type objects are not in the object cache<br>1 round-trip for each collection element, or each type attribute, method, or method argument descriptor. 1 more round-trip if using `OCI_ATTR_TYPE_NAME`, or `OCI_ATTR_SCHEMA_NAME` on the collection element, type attribute, or method argument.<br>0 if all the type objects to be described are already in the object cache following the first `OCIAttrGet()` call. |
| `OCIDescribeAny()` | 1 round-trip to get the `REF` of the type descriptor object                                                                                                                                                                                                                                                                                                                                                                                                  |
| `OCIParamGet()`    | 0                                                                                                                                                                                                                                                                                                                                                                                                                                                            |

### C.5 Data Type Mapping and Manipulation Function Round-Trips

Describes for each OCI data type mapping and manipulation function the number of server round-trips.

Table C-5 lists the number of round-trips for the data type mapping and manipulation functions. The asterisks in the table indicate that all functions with a particular prefix incur the same number of server round-trips. For example, `OCINumberAdd()`, `OCINumberPower()`, and `OCINumberFromText()` all incur zero server round-trips.

Table C-5 Server Round-Trips for Data Type Manipulation Functions

| Function       | Number of Server Round-Trips                        |
|:---------------|:----------------------------------------------------|
| `OCIColl*()`   | 0; 1 if the collection is not loaded in the cache   |
| `OCIDate*()`   | 0                                                   |
| `OCIIter*()`   | 0; 1 if the collection is not loaded in the cache   |
| `OCINumber*()` | 0                                                   |
| `OCIRaw*()`    | 0                                                   |
| `OCIRef*()`    | 0                                                   |
| `OCIString*()` | 0                                                   |
| `OCITable*()`  | 0; 1 if the nested table is not loaded in the cache |

### C.6 Any Type and Data Function Round-Trips

Describes for each OCI Any Type and Data function the number of server round-trips.

Table C-6 lists the number of server round-trips required by Any Type and Data functions. The functions not listed do not generate any round-trips.

Table C-6 Server Round-Trips for Any Type and Data Functions

| Function                  | Number of Server Round-Trips                            |
|:--------------------------|:--------------------------------------------------------|
| `OCIAnyDataAttrGet()`     | 0; 1 if the type information is not loaded in the cache |
| `OCIAnyDataAttrSet()`     | 0; 1 if the type information is not loaded in the cache |
| `OCIAnyDataCollGetElem()` | 0; 1 if the type information is not loaded in the cache |

### C.7 Other Local Functions

Describes for each OCI other local function the number of server round-trips.

Table C-7 lists the functions that are local and do not require a server round-trip.

Table C-7 Locally Processed Functions

| Local Function Name        | Notes                                                                                               |
|:---------------------------|:----------------------------------------------------------------------------------------------------|
| `OCIAttrGet()`             | When describing an object type, this call makes one round-trip to fetch the type descriptor object. |
| `OCIAttrSet()`             |                                                                                                     |
| `OCIBindArrayOfStruct()`   |                                                                                                     |
| `OCIDefineArrayOfStruct()` |                                                                                                     |
| `OCIBindByName()`          |                                                                                                     |
| `OCIBindByPos()`           |                                                                                                     |
| `OCIBindDynamic()`         |                                                                                                     |
| `OCIBindObject()`          |                                                                                                     |
| `OCIDefineByPos()`         |                                                                                                     |
| `OCIDefineDynamic()`       |                                                                                                     |
| `OCIDefineObject()`        |                                                                                                     |
| `OCIDescriptorAlloc()`     |                                                                                                     |
| `OCIDescriptorFree()`      |                                                                                                     |
| `OCIEnvCreate()`           |                                                                                                     |
| `OCIEnvInit()`             |                                                                                                     |
| `OCIErrorGet()`            |                                                                                                     |
| `OCIHandleAlloc()`         |                                                                                                     |
| `OCIHandleFree()`          |                                                                                                     |
| `OCILdaToSvcCtx()`         |                                                                                                     |
| `OCIStmtGetBindInfo()`     |                                                                                                     |
| `OCIStmtPrepare()`         |                                                                                                     |
| `OCIStmtRelease()`         |                                                                                                     |
| `OCIStmtPrepare2()`        |                                                                                                     |
| `OCISvcCtxToLda()`         |                                                                                                     |
