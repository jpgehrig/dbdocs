These topics describe OLE DB information that is specific to Oracle Provider for OLE DB. For generic OLE DB information that includes a detailed listing of all OLE DB properties and interfaces, see the Microsoft OLE DB Programmer's Reference Guide.

- Data Type Mappings in Rowsets and Parameters

- Properties Supported

- Interfaces Supported

- MetaData Columns Supported

- OraOLEDB Tracing

### Data Type Mappings in Rowsets and Parameters

This section lists the data type mapping between Oracle data types and OLE DB-defined types. Oracle Provider for OLE DB represents Oracle data types by using certain OLE DB-defined data types in the rowset as well as in parameters. OLE DB-defined types are also mapped to an Oracle data type when creating tables.

Each Oracle data type is mapped to a specific OLE DB data type, as shown in the following table. This correspondence is used when data type information is retrieved from an Oracle Database.

Table A-1 Data Type Mappings

| Oracle Data Type                         | OLE DB Data Type - Regular (NonUnicode) Mode | OLE DB Data Type - Unicode Mode |
|:-----------------------------------------|:---------------------------------------------|:--------------------------------|
| `BFILE`                                  | `DBTYPE_BYTES`                               | `DBTYPE_BYTES`                  |
| `BINARY_FLOAT`                           | `DBTYPE_R4`                                  | `DBTYPE_R4`                     |
| `BINARY_DOUBLE`                          | `DBTYPE_R8`                                  | `DBTYPE_R8`                     |
| `BLOB`                                   | ` DBTYPE_BYTES`                              | `DBTYPE_BYTES`                  |
| `CHAR`                                   | `DBTYPE_STR`                                 | `DBTYPE_WSTR`                   |
| `CLOB`                                   | `DBTYPE_STR`                                 | `DBTYPE_WSTR`                   |
| `DATE`                                   | `DBTYPE_DBTIMESTAMP`                         | `DBTYPE_DBTIMESTAMP`            |
| `FLOAT`                                  | `DBTYPE_R8`                                  | `DBTYPE_R8`                     |
| `INTERVAL` `DAY` `TO` `SECOND`           | `DBTYPE_STR`                                 | `DBTYPE_WSTR`                   |
| `INTERVAL` `YEAR` `TO` `MONTH`           | `DBTYPE_STR`                                 | `DBTYPE_WSTR`                   |
| `LONG`                                   | `DBTYPE_STR`                                 | `DBTYPE_WSTR`                   |
| `LONG RAW`                               | `BTYPE_BYTES`                                | `DBTYPE_BYTES`                  |
| `NCHAR`                                  | `DBTYPE_STR`                                 | `DBTYPE_WSTR`                   |
| `NCLOB`                                  | `DBTYPE_STR`                                 | `DBTYPE_WSTR`                   |
| `NUMBER`                                 | `DBTYPE_VARNUMERIC`                          | `DBTYPE_VARNUMERIC`             |
| `NUMBER(p,s)`                            | `DBTYPE_NUMERIC`                             | `DBTYPE_NUMERIC`                |
| `NVARCHAR2`                              | `DBTYPE_STR`                                 | `DBTYPE_WSTR`                   |
| `RAW`                                    | `DBTYPE_BYTES`                               | `DBTYPE_BYTES`                  |
| `ROWID`                                  | `DBTYPE_STR`                                 | `DBTYPE_STR`                    |
| `TIMESTAMP`                              | `DBTYPE_DBTIMESTAMP`                         | `DBTYPE_DBTIMESTAMP`            |
| `TIMESTAMP` `WITH` `TIME` `ZONE`         | `DBTYPE_DBTIMESTAMP`                         | `DBTYPE_DBTIMESTAMP`            |
| `TIMESTAMP` `WITH` `LOCAL` `TIME` `ZONE` | `DBTYPE_DBTIMESTAMP`                         | `DBTYPE_DBTIMESTAMP`            |
| `VARCHAR`                                | `DBTYPE_STR`                                 | `DBTYPE_WSTR`                   |

### Properties Supported

This section lists the properties supported by Oracle Provider for OLE DB. The read/write status and initial values are noted.

- Data Source Properties

- DataSourceInfo Properties

- Initialization and Authorization Properties

- Session Properties

- Rowset Properties

#### Data Source Properties

Table A-2 lists data source properties.

Table A-2 DBPROPSET_DATASOURCE Properties

| Property                | Status    | Initial Value |
|:------------------------|:----------|:--------------|
| `DBPROP_CURRENTCATALOG` | READ-ONLY | `NULL`        |

#### DataSourceInfo Properties

Table A-3 lists `DataSourceInfo` properties.

Table A-3 DBPROPSET_DATASOURCEINFO Properties

| Property                             | Status     | Initial Value                                                                                                                      |
|:-------------------------------------|:-----------|:-----------------------------------------------------------------------------------------------------------------------------------|
| `DBPROP_ACTIVESESSIONS`              | READ-ONLY  | `0`, Unlimited sessions                                                                                                            |
| `DBPROP_ASYNCTXNABORT`               | READ-ONLY  | `VARIANT_FALSE`                                                                                                                    |
| `DBPROP_ASYNCTXNCOMMIT`              | READ-ONLY  | `VARIANT_FALSE`                                                                                                                    |
| `DBPROP_BYREFACCESSORS`              | READ-ONLY  | `VARIANT_TRUE`                                                                                                                     |
| `DBPROP_CATALOGLOCATION`             | READ-ONLY  | `DBPROPVAL_CL_END`                                                                                                                 |
| `DBPROP_CATALOGTERM`                 | READ-ONLY  | "Database link"                                                                                                                    |
| `DBPROP_CATALOGUSAGE`                | READ-ONLY  | `DBPROPVAL_CU_DML_STATEMENTS`                                                                                                      |
| `DBPROP_COLUMNDEFINITION`            | READ-ONLY  | `DBPROPVAL_CD_NOTNULL`                                                                                                             |
| `DBPROP_CONCATNULLBEHAVIOR`          | READ-ONLY  | `DBPROPVAL_CB_NON_NULL`                                                                                                            |
| `DBPROP_CONNECTIONSTATUS`            | READ-ONLY  | `DBPROPVAL_CS_INITIALIZED`                                                                                                         |
| `DBPROP_DATASOURCENAME `             | READ-ONLY  | " ", set at run time                                                                                                               |
| `DBPROP_DATASOURCEREADONLY`          | READ-ONLY  | `VARIANT_FALSE`                                                                                                                    |
| `DBPROP_DBMSNAME`                    | READ-ONLY  | " ", set at run time                                                                                                               |
| `DBPROP_DBMSVER`                     | READ-ONLY  | set at run time                                                                                                                    |
| `DBPROP_DSOTHREADMODEL`              | READ/WRITE | `DBPROPVAL_RT_FREETHREAD`                                                                                                          |
| `DBPROP_GROUPBY`                     | READ-ONLY  | `DBPROPVAL_GB_CONTAINS_SELECT`                                                                                                     |
| `DBPROP_HETEROGENEOUSTABLES`         | READ-ONLY  | `DBPROPVAL_HT_DIFFERENT_CATALOGS`                                                                                                  |
| `DBPROP_IDENTIFIERCASE`              | READ-ONLY  | `DBPROPVAL_IC_UPPER`                                                                                                               |
| `DBPROP_MAXINDEXSIZE`                | READ-ONLY  | `0`, limit unknown - depends on block size                                                                                         |
| `DBPROP_MAXOPENCHAPTERS`             | READ-ONLY  | `0`, not supported                                                                                                                 |
| `DBPROP_MAXORSINFILTER`              | READ-ONLY  | `0`, not supported                                                                                                                 |
| `DBPROP_MAXROWSIZE`                  | READ-ONLY  | `0`, no limit                                                                                                                      |
| `DBPROP_MAXROWSIZEINCLUDESBLOB`      | READ-ONLY  | `VARIANT_FALSE`                                                                                                                    |
| `DBPROP_MAXSORTCOLUMNS`              | READ-ONLY  | `0`, not supported                                                                                                                 |
| `DBPROP_MAXTABLESINSELECT`           | READ-ONLY  | 0, no limit                                                                                                                        |
| `DBPROP_MULTIPLEPARAMSETS`           | READ-ONLY  | `VARIANT_TRUE`                                                                                                                     |
| `DBPROP_MULTIPLERESULTS`             | READ-ONLY  | `DBPROP_MR_SUPPORTED | DBPROPVAL__MR_CONCURRENT`                                                                                   |
| `DBPROP_MULTIPLESTORAGEOBJECTS`      | READ-ONLY  | `VARIANT_FALSE`                                                                                                                    |
| `DBPROP_MULTITABLEUPDATE`            | READ-ONLY  | `VARIANT_FALSE`                                                                                                                    |
| `DBPROP_NULLCOLLATION`               | READ-ONLY  | `DBPROPVAL_NC_HIGH`                                                                                                                |
| `DBPROP_OLEOBJECTS`                  | READ-ONLY  | `DBPROPVAL_OO_BLOB`                                                                                                                |
| `DBPROP_ORDERBYCOLUMNSINSELECT`      | READ-ONLY  | `VARIANT_FALSE`                                                                                                                    |
| `DBPROP_OUTPUTPARAMETERAVAILABILITY` | READ-ONLY  | `DBPROPVAL_OA_ATEXECUTE`                                                                                                           |
| `DBPROP_PERSISTENTIDTYPE`            | READ-ONLY  | `DBPROPVAL_PT_NAME`                                                                                                                |
| `DBPROP_PREPAREABORTBEHAVIOR `       | READ-ONLY  | `DBPROPVAL_CB_PRESERVE`                                                                                                            |
| `DBPROP_PREPARECOMMITBEHAVIOR`       | READ-ONLY  | `DBPROPVAL_CB_PRESERVE`                                                                                                            |
| `DBPROP_PROCEDURETERM`               | READ-ONLY  | "PL/SQL Stored Procedure"                                                                                                          |
| `DBPROP_PROVIDERFRIENDLYNAME`        | READ-ONLY  | "Oracle Provider for OLE DB"                                                                                                       |
| `DBPROP_PROVIDERNAME`                | READ-ONLY  | `OraOLEDB``ver``.dll`                                                                                                              |
| `DBPROP_PROVIDEROLEDBVER`            | READ-ONLY  | "02.01"                                                                                                                            |
| `DBPROP_PROVIDERVER`                 | READ-ONLY  | set to current OraOLEDB version                                                                                                    |
| `DBPROP_QUOTEDIDENTIFIERCASE`        | READ-ONLY  | `DBPROPVAL_IC_SENSITIVE`                                                                                                           |
| `DBPROP_ROWSETCONVERSIONSONCOMMAND`  | READ-ONLY  | `VARIANT_TRUE`                                                                                                                     |
| `DBPROP_SCHEMATERM`                  | READ-ONLY  | "Owner"                                                                                                                            |
| `DBPROP_SCHEMAUSAGE`                 | READ-ONLY  | `DBPROPVAL_SU_DML_STATEMENTS | DBPROPVAL_SU_TABLE_DEFINITION | DBPROPVAL_SU_INDEX_DEFINITION | DBPROPVAL_SU_PRIVILEGE_DEFINITION ` |
| `DBPROP_SERVERNAME`                  | READ-ONLY  | " ", set at run time                                                                                                               |
| `DBPROP_SORTONINDEX`                 | READ-ONLY  | `VARIANT_FALSE`                                                                                                                    |
| `DBPROP_SQLSUPPORT`                  | READ-ONLY  | `DBPROPVAL_SQL_ODBC_MINIMUM | DBPROPVAL_SQL_ANSI92_ENTRY | DBPROPVAL_SQL_ESCAPECLAUSES`                                            |
| `DBPROP_STRUCTUREDSTORAGE`           | READ-ONLY  | `DBPROPVAL_SS_ISEQUENTIAL_STREAM`                                                                                                  |
| `DBPROP_SUBQUERIES`                  | READ-ONLY  | `DBPROPVAL_SQ_CORRELATEDSUBQUERIES`                                                                                                |
| `DBPROP_SUPPORTEDTXNDDL`             | READ-ONLY  | `DBPROPVAL_TC_DDL_COMMIT`                                                                                                          |
| `DBPROP_SUPPORTEDTXNISOLEVELS`       | READ-ONLY  | `DBPROPVAL_TI_CURSORSTABILITY | DBPROPVAL_TI_READCOMMITTED`                                                                        |
| `DBPROP_SUPPORTEDTXNISORETAIN`       | READ-ONLY  | `DBPROPVAL_TR_DONTCARE`                                                                                                            |
| `DBPROP_TABLETERM`                   | READ-ONLY  | "Table"                                                                                                                            |
| `DBPROP_USERNAME`                    | READ-ONLY  | " ", set at run time                                                                                                               |

#### Initialization and Authorization Properties

Table A-4 lists initialization and authorization properties.

Table A-4 DBPROPSET_DBINIT Properties

| Property                                 | Status     | Initial Value            |
|:-----------------------------------------|:-----------|:-------------------------|
| `DBPROP_AUTH_PERSIST_SENSITIVE_AUTHINFO` | READ-ONLY  | `VARIANT_FALSE`          |
| `DBPROP_AUTH_USERID`                     | READ/WRITE | User ID                  |
| `DBPROP_INIT_DATASOURCE`                 | READ/WRITE | Connect string           |
| `DBPROP_INIT_HWND`                       | READ/WRITE | Window handle for prompt |
| `DBPROP_INIT_LCID`                       | READ/WRITE | LCID of system           |
| `DBPROP_INIT_OLEDBSERVICES`              | READ/WRITE | `DBPROPVAL_OS_ENABLEALL` |
| `DBPROP_INIT_PROMPT`                     | READ/WRITE | `DBPROMPT_NOPROMPT`      |

#### Session Properties

Table A-5 lists session properties.

Table A-5 DBPROPSET_SESSION Properties

| Property                          | Status    | Initial Value                                               |
|:----------------------------------|:----------|:------------------------------------------------------------|
| `DBPROP_SESS_AUTOCOMMITISOLEVELS` | READ-ONLY | `DBPROPVAL_TI_CURSORSTABILITY | DBPROPVAL_TI_READCOMMITTED` |

#### Rowset Properties

Table A-6 lists rowset properties.

Table A-6 DBPROPSET_ROWSET Properties

| Property                                 | Status     | Initial Value                                                                                                                                                |
|:-----------------------------------------|:-----------|:-------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `DBPROP_ABORTPRESERVE`                   | READ/WRITE | `VARIANT_TRUE`                                                                                                                                               |
| `DBPROP_ACCESSORORDER`                   | READ-ONLY  | `DBPROP_AO_RANDOM`                                                                                                                                           |
| `DBPROP_APPENDONLY`                      | READ-ONLY  | `VARIANT_FALSE`                                                                                                                                              |
| `DBPROP_BLOCKINGSTORAGEOBJECTS`          | READ-ONLY  | `VARIANT_FALSE`                                                                                                                                              |
| `DBPROP_BOOKMARKINFO`                    | READ-ONLY  | `0`                                                                                                                                                          |
| `DBPROP_BOOKMARKS`                       | READ/WRITE | `VARIANT_FALSE`                                                                                                                                              |
| `DBPROP_BOOKMARKSKIPPED`                 | READ/WRITE | `VARIANT_TRUE`                                                                                                                                               |
| `DBPROP_BOOKMARKTYPE`                    | READ-ONLY  | `DBPROP_BMK_NUMERIC`                                                                                                                                         |
| `DBPROP_CACHEDEFERRED`                   | READ-ONLY  | `VARIANT_FALSE`                                                                                                                                              |
| `DBPROP_CANFETCHBACKWARDS`               | READ/WRITE | `VARIANT_FALSE`                                                                                                                                              |
| `DBPROP_CANHOLDROWS`                     | READ/WRITE | `VARIANT_FALSE`                                                                                                                                              |
| `DBPROP_CANSCROLLBACKWARDS`              | READ/WRITE | `VARIANT_FALSE`                                                                                                                                              |
| `DBPROP_CHANGEINSERTEDROWS`              | READ-ONLY  | `VARIANT_TRUE`                                                                                                                                               |
| `DBPROP_CLIENTCURSOR`                    | READ/WRITE | `VARIANT_TRUE`                                                                                                                                               |
| `DBPROP_COLUMNRESTRICT`                  | READ-ONLY  | `VARIANT_TRUE`                                                                                                                                               |
| `DBPROP_COMMANDTIMEOUT`                  | READ/WRITE | `0`                                                                                                                                                          |
| `DBPROP_COMMITPRESERVE`                  | READ/WRITE | `VARIANT_TRUE`                                                                                                                                               |
| `DBPROP_DEFERRED`                        | READ-ONLY  | `VARIANT_TRUE`                                                                                                                                               |
| `DBPROP_DELAYSTORAGEOBJECTS`             | READ-ONLY  | `VARIANT_TRUE`, no delayed update                                                                                                                            |
| `DBPROP_FINDCOMPAREOPS`                  | READ-ONLY  | `DBPROPVAL_CO_EQUALITY | DBPROPVAL_CO_STRING | DBPROPVAL_CO_CASESENSITIVE | DBPROPVAL_CO_CASEINSENSITIVE | DBPROPVAL_CO_CONTAINS | DBPROPVAL_CO_BEGINSWITH ` |
| `DBPROP_HIDDENCOLUMNS`                   | READ-ONLY  | `0`                                                                                                                                                          |
| `DBPROP_IACCESSOR`                       | READ-ONLY  | `VARIANT_TRUE`                                                                                                                                               |
| `DBPROP_ICOLUMNSINFO`                    | READ-ONLY  | `VARIANT_TRUE`                                                                                                                                               |
| `DBPROP_ICOLUMNSROWSET`                  | READ/WRITE | `VARIANT_TRUE`                                                                                                                                               |
| `DBPROP_ICONNECTIONPOINTCONTAINER`       | READ-ONLY  | `VARIANT_TRUE`                                                                                                                                               |
| `DBPROP_ICONVERTTYPE`                    | READ-ONLY  | `VARIANT_TRUE`                                                                                                                                               |
| `DBPROP_IMMOBILEROWS`                    | READ-ONLY  | `VARIANT_TRUE`                                                                                                                                               |
| `DBPROP_IMULTIPLERESULTS`                | READ/WRITE | `VARIANT_TRUE`                                                                                                                                               |
| `DBPROP_IROWSET`                         | READ-ONLY  | `VARIANT_TRUE`                                                                                                                                               |
| `DBPROP_IROWSETCHANGE`                   | READ/WRITE | `VARIANT_FALSE`                                                                                                                                              |
| `DBPROP_IROWSETFIND`                     | READ/WRITE | `VARIANT_FALSE`                                                                                                                                              |
| `DBPROP_IROWSETIDENTITY`                 | READ-ONLY  | `VARIANT_TRUE`                                                                                                                                               |
| `DBPROP_IROWSETINFO`                     | READ-ONLY  | `VARIANT_TRUE`                                                                                                                                               |
| `DBPROP_IROWSETLOCATE`                   | READ/WRITE | `VARIANT_FALSE`                                                                                                                                              |
| `DBPROP_IROWSETREFRESH`                  | READ/WRITE | `VARIANT_FALSE`                                                                                                                                              |
| `DBPROP_IROWSETSCROLL`                   | READ/WRITE | `VARIANT_FALSE`                                                                                                                                              |
| `DBPROP_IROWSETUPDATE`                   | READ/WRITE | `VARIANT_FALSE`                                                                                                                                              |
| `DBPROP_ISEQUENTIALSTREAM`               | READ/WRITE | `VARIANT_TRUE`                                                                                                                                               |
| `DBPROP_ISUPPORTERRORINFO`               | READ/WRITE | `VARIANT_TRUE`                                                                                                                                               |
| `DBPROP_LITERALBOOKMARKS `               | READ-ONLY  | `VARIANT_FALSE`                                                                                                                                              |
| `DBPROP_LITERALIDENTITY`                 | READ-ONLY  | `VARIANT_FALSE`                                                                                                                                              |
| `DBPROP_LOCKMODE`                        | READ-ONLY  | `DBPROPVAL_LM_NONE`                                                                                                                                          |
| `DBPROP_MAXOPENROWS`                     | READ/WRITE | `0`, No limit                                                                                                                                                |
| `DBPROP_MAXPENDINGROWS`                  | READ-ONLY  | `0`, No limit                                                                                                                                                |
| `DBPROP_MAXROWS`                         | READ/WRITE | `0`                                                                                                                                                          |
| `DBPROP_MAXROWSIZE`                      | READ-ONLY  | `0`                                                                                                                                                          |
| `DBPROP_MAXROWSIZEINCLUDESBLOB`          | READ-ONLY  | `VARIANT_FALSE`                                                                                                                                              |
| `DBPROP_NOTIFICATIONGRANULARITY`         | READ/WRITE | `DBPROPVAL_NT_MULTIPLEROWS`                                                                                                                                  |
| `DBPROP_NOTIFICATIONPHASES`              | READ/WRITE | `DBPROPVAL_NP_OKTODO | DBPROPVAL_NP_ABOUTTODO | DBPROPVAL_NP_SYNCHAFTER | DBPROPVAL_NP_FAILEDTODO | DBPROPVAL_NP_DIDEVENT`                                   |
| `DBPROP_NOTIFYCOLUMNSET`                 | READ/WRITE | `DBPROPVAL_NP_OKTODO | DBPROPVAL_NP_ABOUTTODO | DBPROPVAL_NP_SYNCHAFTER | DBPROPVAL_NP_FAILEDTODO | DBPROPVAL_NP_DIDEVENT`                                   |
| `DBPROP_NOTIFYROWDELETE`                 | READ/WRITE | `DBPROPVAL_NP_OKTODO | DBPROPVAL_NP_ABOUTTODO | DBPROPVAL_NP_SYNCHAFTER | DBPROPVAL_NP_FAILEDTODO | DBPROPVAL_NP_DIDEVENT`                                   |
| `DBPROP_NOTIFYROWFIRSTCHANGE`            | READ/WRITE | `DBPROPVAL_NP_OKTODO | DBPROPVAL_NP_ABOUTTODO`                                                                                                               |
| `DBPROP_NOTIFYROWINSERT`                 | READ/WRITE | `DBPROPVAL_NP_OKTODO | DBPROPVAL_NP_ABOUTTODO | DBPROPVAL_NP_SYNCHAFTER | DBPROPVAL_NP_FAILEDTODO | DBPROPVAL_NP_DIDEVENT`                                   |
| `DBPROP_NOTIFYROWRESYNCH`                | READ/WRITE | `DBPROPVAL_NP_OKTODO | DBPROPVAL_NP_ABOUTTODO | DBPROPVAL_NP_SYNCHAFTER`                                                                                     |
| `DBPROP_NOTIFYROWSETRELEASE`             | READ/WRITE | `DBPROPVAL_NP_OKTODO | DBPROPVAL_NP_ABOUTTODO | DBPROPVAL_NP_SYNCHAFTER`                                                                                     |
| `DBPROP_NOTIFYROWSETFETCHPOSITIONCHANGE` | READ/WRITE | `DBPROPVAL_NP_OKTODO | DBPROPVAL_NP_ABOUTTODO | DBPROPVAL_NP_SYNCHAFTER`                                                                                     |
| `DBPROP_NOTIFYROWUNDOCHANGE`             | READ/WRITE | `DBPROPVAL_NP_OKTODO | DBPROPVAL_NP_ABOUTTODO | DBPROPVAL_NP_SYNCHAFTER | DBPROPVAL_NP_FAILEDTODO | DBPROPVAL_NP_DIDEVENT`                                   |
| `DBPROP_NOTIFYROWUNDODELETE`             | READ/WRITE | `DBPROPVAL_NP_OKTODO | DBPROPVAL_NP_ABOUTTODO | DBPROPVAL_NP_SYNCHAFTER | DBPROPVAL_NP_FAILEDTODO | DBPROPVAL_NP_DIDEVENT`                                   |
| `DBPROP_NOTIFYROWUNDOINSERT`             | READ/WRITE | `DBPROPVAL_NP_OKTODO | DBPROPVAL_NP_ABOUTTODO | DBPROPVAL_NP_SYNCHAFTER | DBPROPVAL_NP_FAILEDTODO | DBPROPVAL_NP_DIDEVENT`                                   |
| `DBPROP_NOTIFYROWUNDOUPDATE`             | READ/WRITE | `DBPROPVAL_NP_OKTODO | DBPROPVAL_NP_ABOUTTODO | DBPROPVAL_NP_SYNCHAFTER | DBPROPVAL_NP_FAILEDTODO | DBPROPVAL_NP_DIDEVENT`                                   |
| `DBPROP_ORDEREDBOOKMARKS`                | READ-ONLY  | `VARIANT_TRUE`                                                                                                                                               |
| `DBPROP_OTHERINSERT`                     | READ-ONLY  | `VARIANT_FALSE`                                                                                                                                              |
| `DBPROP_OTHERUPDATEDELETE`               | READ-ONLY  | `VARIANT_FALSE`                                                                                                                                              |
| `DBPROP_OWNINSERT`                       | READ-ONLY  | `VARIANT_TRUE`                                                                                                                                               |
| `DBPROP_OWNUPDATEDELETE`                 | READ-ONLY  | `VARIANT_TRUE`                                                                                                                                               |
| `DBPROP_QUICKRESTART`                    | READ/WRITE | `VARIANT_FALSE`                                                                                                                                              |
| `DBPROP_REENTRANTEVENTS`                 | READ-ONLY  | `VARIANT_FALSE`                                                                                                                                              |
| `DBPROP_REMOVEDELETED`                   | READ-ONLY  | `VARIANT_TRUE`                                                                                                                                               |
| `DBPROP_REPORTMULTIPLECHANGES`           | READ-ONLY  | `VARIANT_FALSE`                                                                                                                                              |
| `DBPROP_RETURNPENDINGINSERTS`            | READ/WRITE | `VARIANT_TRUE`                                                                                                                                               |
| `DBPROP_ROWRESTRICT`                     | READ/WRITE | `VARIANT_FALSE`                                                                                                                                              |
| `DBPROP_ROWTHREADMODEL`                  | READ-ONLY  | `DBPROPVAL_RT_FREETHREAD`                                                                                                                                    |
| `DBPROP_SERVERCURSOR`                    | READ/WRITE | `VARIANT_FALSE`                                                                                                                                              |
| `DBPROP_SERVERDATAONINSERT`              | READ/WRITE | `VARIANT_TRUE`                                                                                                                                               |
| `DBPROP_STRONGIDENTITY`                  | READ/WRITE | `VARIANT_TRUE`                                                                                                                                               |
| `DBPROP_TRANSACTEDOBJECT`                | READ-ONLY  | `VARIANT_TRUE`                                                                                                                                               |
| `DBPROP_UNIQUEROWS`                      | READ/WRITE | `VARIANT_FALSE`                                                                                                                                              |
| `DBPROP_UPDATABILITY`                    | READ/WRITE | `DBPROPVAL_UP_CHANGE | DBPROPVAL_UP_DELETE | DBPROPVAL_UP_INSET`                                                                                             |

##### Rowset Property Implications

Oracle Provider for OLE DB sets other necessary properties if a particular property is set to `VARIANT_TRUE`.

- If `DBPROP_IROWSETLOCATE` is set to `VARIANT_TRUE`, then the following properties are also set to `VARIANT_TRUE`:

  - `DBPROP_IROWSETIDENTITY`

  - `DBPROP_CANHOLDROWS`

  - `DBPROP_BOOKMARKS`

  - `DBPROP_CANFETCHBACKWARDS`

  - `DBPROP_CANSCROLLBACKWARDS`

- If `DBPROP_IROWSETSCROLL` is set to `VARIANT_TRUE`, then the following properties are also set to `VARIANT_TRUE`:

  - `DBPROP_IROWSETIDENTITY`

  - `DBPROP_IROWSETLOCATE`

  - `DBPROP_CANHOLDROWS`

  - `DBPROP_BOOKMARKS`

  - `DBPROP_CANFETCHBACKWARDS`

  - `DBPROP_CANSCROLLBACKWARDS`

- If `DBPROP_IROWSETUPDATE` is set to `VARIANT_TRUE`, then the DBPROP_IROWSETCHANGE property is also set to `VARIANT_TRUE`.

### Interfaces Supported

This section identifies the OLE DB interfaces that are supported by Oracle Provider for OLE DB.

- Data Source

- Session

- Command

- Rowset

- Multiple Results

- Transaction Options

- Custom Error Object

#### Data Source

       CoType TDataSource {
          interface IDBCreateSession;
          interface IDBInitialize;
          interface IDBProperties;
          interface IPersist;
          interface IDBInfo;
          interface ISupportErrorInfo;
       }

#### Session

       CoType TSession {
          interface IGetDataSource;
          interface IOpenRowset;
          interface ISessionProperties;
          interface IDBCreateCommand;
          interface IDBSchemaRowset;
          interface ISupportErrorInfo;
          interface ITransactionJoin;
          interface ITransactionLocal;
          interface ITransaction;
       }

#### Command

       CoType TCommand {
          interface IAccessor;
          interface IColumnsInfo;
          interface ICommand;
          interface ICommandProperties;
          interface ICommandText;
          interface IConvertType;
          interface IColumnsRowset;
          interface ICommandPrepare;
          interface ICommandWithParameters;
          interface ISupportErrorInfo;
       }

#### Rowset

       CoType TRowset {
          interface IAccessor;
          interface IColumnsInfo;
          interface IConvertType;
          interface IRowset;
          interface IRowsetInfo;
          interface IColumnsRowset;
          interface IConnectionPointContainer;
          interface IRowsetChange;
          interface IRowsetFind;
          interface IRowsetIdentity;
          interface IRowsetLocate;
          interface IRowsetRefresh;
          interface IRowsetFastLoad;
          interface IRowsetScroll;
          interface IRowsetUpdate;
          interface ISupportErrorInfo;
       }

#### Multiple Results

       CoType TMultipleResults {
          interface IMultipleResults;
          interface ISupportErrorInfo;
       }

#### Transaction Options

       CoType TTransactionOptions {
          interface ITransactionOptions;
          interface ISupportErrorInfo;
       }

#### Custom Error Object

       CoType TCustomErrorObject {
          interface IErrorLookup;
       }

### MetaData Columns Supported

`DBTYPE_BASECOLUMNNAME`, `DBTYPE_BASETABLENAME`, and `DBTYPE_BASESCHEMANAME` metadata columns are not populated for read-only recordsets. OraOLEDB creates a read-only recordset for server cursor for SQL queries with `DISTINCT` or `UNIQUE` keywords. OraOLEDB also creates a read-only recordset for server cursor for `JOIN` queries.

The following metadata columns are supported by the column rowset of OraOLEDB:

- `DBCOLUMN_IDNAME`

- `DBCOLUMN_PROPID`

- `DBCOLUMN_NAME`

- `DBCOLUMN_NUMBER`

- `DBCOLUMN_TYPE`

- `DBCOLUMN_TYPEINFO`

- `DBCOLUMN_COLUMNSIZE`

- `DBCOLUMN_PRECISION`

- `DBCOLUMN_SCALE`

- `DBCOLUMN_FLAGS`

- `DBCOLUMN_BASECATALOGNAME`

- `DBCOLUMN_BASECOLUMNNAME`

- `DBCOLUMN_BASESCHEMANAME`

- `DBCOLUMN_BASETABLENAME`

- `DBCOLUMN_COMPUTEMODE`

- `DBCOLUMN_ISAUTOINCREMENT`

- `DBCOLUMN_ISCASESENSITIVE`

- `DBCOLUMN_ISSEARCHABLE`

- `DBCOLUMN_OCTETLENGTH`

- `DBCOLUMN_KEYCOLUMN`

### OraOLEDB Tracing

OraOLEDB provides the ability to trace the interface calls for debugging purposes. This feature has been provided to assist Oracle Support Services in debugging customer issues.

The provider can be configured to record the following information:

- For OLE DB Interface method entry and exit:

  - Parameter values supplied (entry)

  - Return value; `HRESULT` (exit)

  - Thread ID (entry and exit)

- For Distributed transaction enlistment and delistment:

  - Session object information

  - Transaction ID

    **Note:**

    To record global transaction enlistment and delistment information, the `TraceLevel` value must be set to session object. See `TraceOption` in Registry Setting for Tracing Calls.

#### Registry Setting for Tracing Calls

In ODAC 12c Release 4, OraOLEDB now uses a new directory to write trace files to by default: `<Windows user temporary folder>`\\`oledb\trace`.

The Windows user temporary folder is determined by your local Windows settings, such as your Windows TMP or TEMP environment variable. Typically, it can be `C:\temp` or `C:\Users\``<user name>``\AppData\Local\Temp`.

To change the trace file location, use the `TraceFileLocation` attribute to set a new location. `TraceFileLocation` will not be created by default in the Windows Registry. OraOLEDB will create an entry in the Windows event log where the trace was created anytime it creates a trace file.

To trace the interface calls, you must configure the following registry values for `HKEY_LOCAL_MACHINE\SOFTWARE\ORACLE\KEY_``HOMENAME``\OLEDB\`:

- `TraceFileLocation`

  Valid Value: Any valid directory path

  `TraceFileLocation` specifies trace file destination directory. The default trace location is `<Windows user temporary folder>`\\`oledb\trace`.

- `TraceCategory`

  Valid Values:

  - `0` = None

  - `1` = OLEDB Interface method entry

  - `2` = OLEDB Interface method exit

  - `4` = Distributed Transaction Enlistment and Delistment

  `TraceCategory` specifies the information that is to be traced. Combinations of different tracing categories can be made by adding the valid values. For example, set `TraceCategory` to `3` to trace all OLE DB interface method entries and exits.

- `TraceLevel`

  Valid Values:

  - `0` = None

  - `1` = Data Source object

  - `2` = Session object

  - `4` = Command object

  - `8` = Rowset object

  - `16` = Error object

  - `64` = Multiple Results Object

  `TraceLevel` specifies the OLE DB objects to be traced. Because tracing all the entry and exit calls for all the OLE DB objects can be excessive, `TraceLevel` is provided to limit tracing to a single or multiple OLE DB objects. To obtain tracing on multiple objects, add the valid values. For example, if `TraceLevel` is set to `12` and `TraceCategory` is set to `3`, the trace file will only contain method entry and exit for Command and Rowset objects.

  The `TraceLevel` value must be set to session object (2) to trace global transaction enlistment and delistment information.

- `TraceOption`

  Valid Values:

  - `0` = Single trace file

  - `1` = Multiple trace files

  `TraceOption` specifies whether to log trace information in single or multiple files for each Thread ID. If multiple trace file is requested, a Thread ID is appended to the file name provided to create a trace file for each thread.
