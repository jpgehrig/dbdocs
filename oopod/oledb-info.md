Topics:

- Datatype Mappings

- Objects

- Interfaces

- Properties

- Provider-Specific Properties

### Datatype Mappings

This section lists the datatype mappings between Oracle datatypes and OLE DB datatypes. Oracle OLAP Provider for OLE DB represents Oracle datatypes by using certain OLE DB datatypes. Each Oracle datatype is mapped to a specific OLE DB datatype. This correspondence is used when data is retrieved from Oracle Databases.

Table B-1 Datatype Mappings

| Mapping | Oracle Datatype | OLE DB Datatype      |
|:--------|:----------------|:---------------------|
| 1       | `BINARY_DOUBLE` | `DBTYPE_R8`          |
| 2       | `BINARY_FLOAT`  | `DBTYPE_R4`          |
| 3       | `CHAR`          | `DBTYPE_WSTR`        |
| 4       | `DATE`          | `DBTYPE_DBTIMESTAMP` |
| 5       | `FLOAT`         | `DBTYPE_R8`          |
| 6       | `NCHAR`         | `DBTYPE_WSTR`        |
| 7       | `NUMBER`        | `DBTYPE_VARNUMERIC`  |
| 8       | `NUMBER` (p, s) | `DBTYPE_NUMERIC`     |
| 9       | `NVARCHAR2`     | `DBTYPE_WSTR`        |
| 10      | `VARCHAR`       | `DBTYPE_WSTR`        |

### Objects

The provider exposes OLAP-specific as well as OLE DB core interfaces. This section identifies the objects that the Oracle OLAP Provider for OLE DB exposes:

- Data Source

- Session

- Command

- Rowset

- Dataset

- Errors

- Error Records

### Interfaces

The provider exposes the following OLE DB and OLE DB for OLAP interfaces.

#### Data Source Object Interfaces

     CoType TDataSource {
           interface IDBCreateSession;
           interface IDBInitialize;
           interface IDBProperties;
           interface IPersist;
           interface IDBInfo;
           interface ISupportErrorInfo;
        }

#### Session Object Interfaces

        CoType TSession {
           interface IGetDataSource;
           interface IDBCreateCommand;
           interface ISessionProperties;
           interface IDBSchemaRowset;
           interface ISupportErrorInfo;
        }

#### Command Object Interface

     CoType TCommand {
           interface IAccessor;
           interface IColumnsInfo;
           interface ICommand;
           interface ICommandProperties;
           interface ICommandText;
           interface IConvertType;
           interface ISupportErrorInfo;
        }

#### Rowset Object interfaces

      CoType TRowset {
           interface IAccessor;
           interface IColumnsInfo;
           interface IConvertType;
           interface IRowset;
           interface IRowsetInfo;
           interface IConnectionPointContainer;
           interface IRowsetLocate;
           interface IRowsetScroll;
           interface ISupportErrorInfo;
        }


#### DataSet Object Interface

       CoType TDataset {
           interface IAccessor;
           interface IConvertType;
           interface IColumnsInfo;
           interface IMDDataset;
           interface ISupportErrorInfo;
        }

#### Error Object Interfaces

        CoType TErrorObject {
           interface IErrorRecords;
        }

#### Error Records Interfaces

    CoType TErrorRecord {
           interface IErrorInfo;
        }

### Properties

This section lists the properties supported by the provider. R/W indicates read, or write or both.

For details on the definition (including the type, and equivalent ADO MD property name) of the listed properties in this section, read the Microsoft OLE DB and OLE DB for OLAP documentation .

**See Also:**

    Microsoft Developer Network

- Data Source Properties

- Data Source Info Properties

- Initialization and Authorization Properties

- Rowset Properties

- Session Properties

#### Data Source Properties

Table B-2 lists the data source properties that the provider supports, with their default values.

Table B-2 DBPROPSET_DATASOURCE

| Property                     | R/W | Default Value   |
|:-----------------------------|:----|:----------------|
| `DBPROP_CURRENTCATALOG`      | R   | `""`            |
| `DBPROP_MULTIPLECONNECTIONS` | R   | `VARIANT_FALSE` |

#### Data Source Info Properties

Table B-3 lists the data source info properties that the provider supports, with their default values.

Table B-3 DBPROPSET_DATASOURCEINFO

| Property                              | R/W | Default Value                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          |
|:--------------------------------------|:----|:-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `DBPROP_ACTIVESESSIONS`               | R   | `0` (unlimited)                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                        |
| `DBPROP_BYREFACCESSORS `              | R   | `VARIANT_FALSE`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                        |
| `DBPROP_CATALOGLOCATION`              | R   | `0` (not supported)                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    |
| `DBPROP_CATALOGTERM `                 | R   | `""`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   |
| `DBPROP_CATALOGUSAGE `                | R   | `0` (not supported)                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    |
| `DBPROP_COLUMNDEFINITION`             | R   | `0` (not supported)                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    |
| `DBPROP_CONCATNULLBEHAVIOR`           | R   | `DBPROPVAL_CB_NON_NULL `                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                               |
| `DBPROP_CONNECTIONSTATUS `            | R   | Dynamically set to status of connection                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                |
| `DBPROP_DATASOURCENAME `              | R   | Dynamically set to `tns` `alias` string                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                |
| `DBPROP_DATASOURCEREADONLY`           | R   | `VARIANT_FALSE`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                        |
| `DBPROP_DATASOURCE_TYPE `             | R   | `DBPROPVAL_DST_MDP`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    |
| `DBPROP_DBMSNAME `                    | R   | `"Oracle"`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             |
| `DBPROP_DBMSVER`                      | R   | Dynamically set to version \# string                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   |
| `DBPROP_DSOTHREADMODEL `              | R   | `DBPROPVAL_RT_FREETHREAD`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              |
| `DBPROP_GROUPBY `                     | R   | `DBPROPVAL_GB_CONTAINS_SELECT `                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                        |
| `DBPROP_HETEROGENEOUSTABLES`          | R   | `0` (not supported)                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    |
| `DBPROP_IDENTIFIERCASE`               | R   | `0` (not supported)                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    |
| `DBPROP_MAXINDEXSIZE`                 | R   | 0 (unlimited)                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          |
| `DBPROP_MAXOPENCHAPTERS`              | R   | 0 (not supported)                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      |
| `DBPROP_MAXROWSIZE `                  | R   | 0 (unlimited)                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          |
| `DBPROP_MAXROWSIZEINCLUDESBLOB`       | R   | `VARIANT_FALSE`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                        |
| `DBPROP_MAXTABLESINSELECT`            | R   | 0 (unlimited, unknown, or not applicable)                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              |
| `DBPROP_MULTIPLEPARAMSETS`            | R   | `VARIANT_FALSE`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                        |
| `DBPROP_MULTIPLERESULTS `             | R   | `DBPROPVAL_MR_NOTSUPPORTED`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            |
| `DBPROP_MULTITABLEUPDATE`             | R   | `VARIANT_FALSE`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                        |
| `DBPROP_NULLCOLLATION`                | R   | `DBPROPVAL_NC_HIGH`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    |
| `DBPROP_OLEOBJECTS `                  | R   | `0` (not supported)                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    |
| `DBPROP_ORDERBYCOLUMNSINSELECT`       | R   | `VARIANT_FALSE`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                        |
| `DBPROP_OUTPUTPARAMETERAVAILABILITY ` | R   | `DBPROPVAL_OA_NOTSUPPRTED`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             |
| `DBPROP_PERSISTENTIDTYPE`             | R   | `DBPROPVAL_PT_NAME`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    |
| `DBPROP_PREPAREABORTBEHAVIOR`         | R   | `0` (not supported)                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    |
| `DBPROP_PREPARECOMMITBEHAVIOR `       | R   | `0` (not supported)                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    |
| `DBPROP_PROCEDURETERM `               | R   | `"Calculated member"`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  |
| `DBPROP_PROVIDERFRIENDLYNAME `        | R   | `"Oracle OLAP Provider for OLE DB"`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    |
| `DBPROP_PROVIDERMEMORY `              | R   | `VARIANT_FALSE`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                        |
| `DBPROP_PROVIDERFILENAME `            | R   | `"OraOLEDBOLAP10.dll"`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 |
| `DBPROP_PROVIDEROLEDBVER `            | R   | `"2.7"`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                |
| `DBPROP_PROVIDERVER `                 | R   | "10.1.0.2.0"                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           |
| `DBPROP_QUOTEDIDENTIFIERCASE `        | R   | `0` (not supported)                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    |
| `DBPROP_ROWSETCONVERSIONSONCOMMAND `  | R   | `VARIANT_TRUE`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         |
| `DBPROP_SCHEMATERM `                  | R   | `"Schema"`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             |
| `DBPROP_SCHEMAUSAGE `                 | R   | `0` (not supported)                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    |
| `DBPROP_SERVERNAME `                  | R   | `"Oracle"`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             |
| `DBPROP_SQLSUPPORT `                  | R   | `DBPROPVAL_SQL_NONE`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   |
| `DBPROP_STRUCTUREDSTORAGE `           | R   | `0` (not supported)                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    |
| `DBPROP_SUBQUERIES `                  | R   | `0` (not supported)                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    |
| `DBPROP_SUPPORTEDTXNDDL `             | R   | `0` (not supported)                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    |
| `DBPROP_SUPPORTEDTXNISOLEVELS`        | R   | `0` (not supported)                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    |
| `DBPROP_SUPPORTEDTXNISORETAIN `       | R   | `0` (not supported)                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    |
| `DBPROP_TABLETERM `                   | R   | `"Cube"`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                               |
| `DBPROP_USERNAME`                     | R   | Dynamically set to `user` `id` string                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  |
| `MDPROP_AGGREGATECELL_UPDATE `        | R   | `MDPROPVAL_AU_UNSUPPORTED`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             |
| `MDPROP_AXES `                        | R   | 0 (no limit)                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           |
| `MDPROP_FLATTENING_SUPPORT `          | R   | `MDPROPVAL_FS_NO_SUPPORT`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              |
| `MDPROP_MDX_CASESUPPORT `             | R   | `0` (not supported)                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    |
| `MDPROP_MDX_DESCFLAGS `               | R   | `MDPROPVAL_MD_BEFORE | `<br>`MDPROPVAL_MD_AFTER | `<br>`MDPROPVAL_MD_SELF`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             |
| `MDPROP_MDX_FORMULAS `                | R   | `MDPROPVAL_MF_WITH_NAMEDSETS | `<br>`MDPROPVAL_MF_CREATE_CALCMEMBERS |`<br>`MDPROPVAL_MF_CREATE_NAMEDSETS | `<br>`MDPROPVAL_MF_SCOPE_SESSION`                                                                                                                                                                                                                                                                                                                                                                                                                                                                          |
| `MDPROP_MDX_JOINCUBES `               | R   | `MDPROPVAL_MJC_SINGLECUBE`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             |
| `MDPROP_MDX_MEMBER_FUNCTIONS `        | R   | `MDPROPVAL_MMF_COUSIN | `<br>`MDPROPVAL_MMF_PARALLELPERIOD | `<br>`MDPROPVAL_MMF_OPENINGPERIOD | `<br>`MDPROPVAL_MMF_CLOSINGPERIOD`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    |
| `MDPROP_MDX_NONMEASURE_EXPRESSIONS `  | R   | `MDPROPVAL_NME_ALLDIMENSIONS`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          |
| `MDPROP_MDX_NUMERIC_FUNCTIONS `       | R   | `MDPROPVAL_MNF_MEDIAN | `<br>`MDPROPVAL_MNF_VAR |`<br>`MDPROPVAL_MNF_STDDEV`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           |
| `MDPROP_MDX_OBJQUALIFICATION `        | R   | `MDPROPVAL_MOQ_CUBE_DIM |`<br>`MDPROPVAL_MOQ_DIM_HIER | `<br>`MDPROPVAL_MOQ_DIMHIER_LEVEL | `<br>`MDPROPVAL_MOQ_DIMHIER_MEMBER |`<br>`MDPROPVAL_MOQ_LEVEL_MEMBER`                                                                                                                                                                                                                                                                                                                                                                                                                                                      |
| `MDPROP_MDX_QUERYBYPROPERTY `         | R   | `VARIANT TRUE`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         |
| `MDPROP_MDX_SET_FUNCTIONS `           | R   | `MDPROPVAL_MSF_TOPPERCENT |`<br>`MDPROPVAL_MSF_BOTTOMPERCENT |`<br>`MDPROPVAL_MSF_TOPSUM |`<br>`MDPROPVAL_MSF_BOTTOMSUM |`<br>`MDPROPVAL_MSF_DRILLDOWNMEMBER |`<br>`MDPROPVAL_MSF_DRILLDOWNMEMBERTOP|`<br>`MDPROPVAL_MSF_DRILLDOWNMEMBERBOTTOM | `<br>`MDPROPVAL_MSF_DRILLDOWNLEVELTOP | `<br>`MDPROPVAL_MSF_DRILLDOWNLEVELBOTTOM | `<br>`MDPROPVAL_MSF_DRILLUPMEMBER |`<br>`MDPROPVAL_MSF_DRILLUPLEVEL | `<br>`MDPROPVAL_MSF_DRILLDOWNLEVEL | `<br>`MDPROPVAL_MSF_PERIODSTODATE |`<br>`MDPROPVAL_MSF_LASTPERIODS |`<br>`MDPROPVAL_MSF_YTD |`<br>`MDPROPVAL_MSF_QTD |`<br>`MDPROPVAL_MSF_MTD |`<br>`MDPROPVAL_MSF_WTD` |
| `MDPROP_MDX_SLICER`                   | R   | `MDPROPVAL_MS_SINGLETUPLE`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             |
| `MDPROP_MDX_STRING_COMPOP `           | R   | `MDPROPVAL_MSC_LESSTHAN | `<br>`MDPROPVAL_MSC_GREATERTHAN | `<br>`MDPROPVAL_MSC_LESSTHANEQUAL |`<br>`MDPROPVAL_MSC_GREATERTHANEQUAL`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   |
| `MDPROP_NAMED_LEVELS `                | R   | `MDPROPVAL_NL_NAMEDLEVELS | `<br>`MDPROPVAL_NL_NUMBEREDLEVELS`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         |
| `MDPROP_RANGEROWSET `                 | R   | `MDPROPVAL_RR_NORANGEROWSET`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           |
| `MDPROP_VISUALMODE`                   | R   | `MDPROPVAL_VISUAL_MODE_VISUALOFF`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      |

#### Initialization and Authorization Properties

Table B-4 lists the initialization and authorization properties that the provider supports, with their default values.

Table B-4 DBPROPSET_DBINIT

| Property                                 | R/W | Default Value                                                  |
|:-----------------------------------------|:----|:---------------------------------------------------------------|
| `DBPROP_AUTH_PASSWORD`                   | R/W | Dynamically set to `password` string                           |
| `DBPROP_AUTH_PERSIST_SENSITIVE_AUTHINFO` | R   | `VARIANT_FALSE`                                                |
| `DBPROP_AUTH_USERID`                     | R/W | Dynamically set to `user` `id` string                          |
| `DBPROP_INIT_DATASOURCE `                | R/W | Dynamically set to `tns` `alias` string                        |
| `DBPROP_INIT_HWND `                      | R/W | `0`                                                            |
| `DBPROP_INIT_LCID `                      | R/W | Dynamically set to System LCID                                 |
| `DBPROP_INIT_OLEDBSERVICES `             | R/W | `DBPROPVAL_OS_ENABLEALL`                                       |
| `DBPROP_INIT_PROMPT `                    | R/W | `DBPROMPT_NOPROMPT`                                            |
| `DBPROP_INIT_PROVIDERSTRING `            | R/W | Dynamically set to provider-specific string attribute settings |

#### Rowset Properties

Table B-5 lists the rowset properties that this release supports, with their default values.

Table B-5 DBPROP_ROWSET

| Property                                  | R/W | Default Value                                                                                                                                                                           |
|:------------------------------------------|:----|:----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `DBPROP_ACCESSORDER`                      | R   | `DBPROP_AO_RANDOM`                                                                                                                                                                      |
| `DBPROP_APPENDONLY `                      | R   | `VARIANT_FALSE`                                                                                                                                                                         |
| `DBPROP_BOOKMARKINFO `                    | R   | `0`                                                                                                                                                                                     |
| `DBPROP_BOOKMARKS `                       | R/W | `VARIANT_TRUE`                                                                                                                                                                          |
| `DBPROP_BOOKMARKSKIPPED `                 | R/W | `VARIANT_TRUE`                                                                                                                                                                          |
| `DBPROP_BOOKMARKTYPE `                    | R   | `DBPROP_BMK_NUMERIC`                                                                                                                                                                    |
| `DBPROP_CACHEDEFERRED `                   | R   | `VARIANT_FALSE`                                                                                                                                                                         |
| `DBPROP_CANFETCHBACKWARDS `               | R/W | `VARIANT_TRUE`                                                                                                                                                                          |
| `DBPROP_CANHOLDROWS `                     | R/W | `VARIANT_FALSE`                                                                                                                                                                         |
| `DBPROP_CANSCROLLBACKWARDS `              | R/W | `VARIANT_TRUE`                                                                                                                                                                          |
| `DBPROP_CHANGEINSERTEDROWS`               | R   | `VARIANT_FALSE `                                                                                                                                                                        |
| `DBPROP_CLIENTCURSOR`                     | R/W | `VARIANT_TRUE`                                                                                                                                                                          |
| `DBPROP_COLUMNRESTRICT`                   | R   | `VARIANT_TRUE`                                                                                                                                                                          |
| `DBPROP_COMMANDTIMEOUT`                   | R   | `0` (unlimited)                                                                                                                                                                         |
| `DBPROP_DEFERRED`                         | R   | `VARIANT_FALSE`                                                                                                                                                                         |
| `DBPROP_FINDCOMPAREOPS`                   | R   | `DBPROPVAL_CO_EQUALITY | `<br>`DBPROPVAL_CO_STRING | `<br>`DBPROPVAL_CO_CASESENSITIVE |`<br>`DBPROPVAL_CO_CASEINSENSITIVE | `<br>`DBPROPVAL_CO_CONTAINS |`<br>`DBPROPVAL_CO_BEGINSWITH` |
| `DBPROP_HIDDENCOLUMNS`                    | R   | `0`                                                                                                                                                                                     |
| `DBPROP_IAccessor`                        | R   | `VARIANT_TRUE`                                                                                                                                                                          |
| `DBPROP_IColumnsInfo`                     | R   | `VARIANT_TRUE`                                                                                                                                                                          |
| `DBPROP_IColumnsRowset`                   | R/W | `VARIANT_TRUE`                                                                                                                                                                          |
| `DBPROP_IConnectionPointContainer `       | R   | `VARIANT_TRUE`                                                                                                                                                                          |
| `DBPROP_IConvertType`                     | R   | `VARIANT_TRUE`                                                                                                                                                                          |
| `DBPROP_IMMOBILEROWS`                     | R   | `VARIANT_TRUE`                                                                                                                                                                          |
| `DBPROP_IMultipleResults`                 | R   | `VARIANT_FALSE`                                                                                                                                                                         |
| `DBPROP_IRowset`                          | R   | `VARIANT_TRUE`                                                                                                                                                                          |
| `DBPROP_IRowsetChange`                    | R   | `VARIANT_FALSE`                                                                                                                                                                         |
| `DBPROP_IRowsetFind`                      | R   | `VARIANT_FALSE`                                                                                                                                                                         |
| `DBPROP_IRowsetIdentity`                  | R   | `VARIANT_FALSE`                                                                                                                                                                         |
| `DBPROP_IRowsetInfo`                      | R   | `VARIANT_TRUE`                                                                                                                                                                          |
| `DBPROP_IRowsetLocate`                    | R/W | `VARIANT_TRUE`                                                                                                                                                                          |
| `DBPROP_IRowsetRefresh`                   | R   | `VARIANT_FALSE`                                                                                                                                                                         |
| `DBPROP_IRowsetScroll`                    | R/W | `VARIANT_TRUE`                                                                                                                                                                          |
| `DBPROP_IRowsetUpdate `                   | R   | `VARIANT_FALSE `                                                                                                                                                                        |
| `DBPROP_ISupportErrorInfo `               | R   | `VARIANT_TRUE`                                                                                                                                                                          |
| `DBPROP_LITERALBOOKMARKS `                | R   | `VARIANT_FALSE`                                                                                                                                                                         |
| `DBPROP_LITERALIDENTITY `                 | R   | `VARIANT_FALSE`                                                                                                                                                                         |
| `DBPROP_LOCKMODE `                        | R   | `DBPROPVAL_LM_NONE`                                                                                                                                                                     |
| `DBPROP_MAXOPENROWS `                     | R/W | `0` (unlimited)                                                                                                                                                                         |
| `DBPROP_MAXPENDINGROWS `                  | R   | `0` (unlimited)                                                                                                                                                                         |
| `DBPROP_MAXROWS `                         | R/W | `0` (unlimited)                                                                                                                                                                         |
| `DBPROP_MAXROWSIZE`                       | R   | `0` (unlimited)                                                                                                                                                                         |
| `DBPROP_MAXROWSIZEXINCLUDESBLOB`          | R   | `VARIANT_FALSE`                                                                                                                                                                         |
| `DBPROP_NOTIFICATIONGRANULARITY `         | R   | `DBPROPVAL_NT_MULTIPLEROWS`                                                                                                                                                             |
| `DBPROP_NOTIFICATIONPHASES `              | R   | `DBPROPVAL_NP_OKTODO | `<br>`DBPROPVAL_NP_ABOUTTODO | `<br>`DBPROPVAL_NP_SYNCHAFTER | `<br>`DBPROPVAL_NP_DIDEVENT | `<br>`DBPROPVAL_NP_FAILEDTODO`                                      |
| `DBPROP_NOTIFYCOLUMNSET `                 | R   | `0` (unlimited)                                                                                                                                                                         |
| `DBPROP_NOTIFYROWDELETE `                 | R   | `0` (unlimited)                                                                                                                                                                         |
| `DBPROP_NOTIFYROWFIRSTCHANGE `            | R   | `0` (unlimited)                                                                                                                                                                         |
| `DBPROP_NOTIFYROWINSERT `                 | R   | `0` (unlimited)                                                                                                                                                                         |
| `DBPROP_NOTIFYROWRESYNCH `                | R/W | `DBPROPVAL_NP_OKTODO | `<br>`DBPROPVAL_NP_ABOUTTODO |`<br>`DBPROPVAL_NP_SYNCHAFTER`                                                                                                     |
| `DBPROP_NOTIFYROWSETCHANGED `             | R   | `0` (not supported)                                                                                                                                                                     |
| `DBPROP_NOTIFYROWSETFETCHPOSITIONCHANGE ` | R/W | `DBPROPVAL_NP_OKTODO | `<br>`DBPROPVAL_NP_ABOUTTODO |`<br>`DBPROPVAL_NP_SYNCHAFTER`                                                                                                     |
| `DBPROP_NOTIFYROWSETRELEASE `             | R/W | `DBPROPVAL_NP_OKTODO | `<br>`DBPROPVAL_NP_ABOUTTODO |`<br>`DBPROPVAL_NP_SYNCHAFTER`                                                                                                     |
| `DBPROP_NOTIFYROWUNDOCHANGE `             | R   | `0` (not supported)                                                                                                                                                                     |
| `DBPROP_NOTIFYROWUNDODELETE `             | R   | `0` (not supported)                                                                                                                                                                     |
| `DBPROP_NOTIFYROWUNDOINSERT `             | R   | `0` (not supported)                                                                                                                                                                     |
| `DBPROP_NOTIFYROWUPDATE `                 | R   | `0` (not supported)                                                                                                                                                                     |
| `DBPROP_ORDEREDBOOKMARKS `                | R   | `VARIANT_TRUE`                                                                                                                                                                          |
| `DBPROP_OTHERINSERT `                     | R   | `VARIANT_FALSE`                                                                                                                                                                         |
| `DBPROP_OTHERUPDATEDELETE `               | R   | `VARIANT_FALSE`                                                                                                                                                                         |
| `DBPROP_OWNINSERT `                       | R   | `VARIANT_FALSE`                                                                                                                                                                         |
| `DBPROP_OWNUPDATEDELETE `                 | R   | `VARIANT_FALSE`                                                                                                                                                                         |
| `DBPROP_QUICKRESTART `                    | R/W | `VARIANT_FALSE`                                                                                                                                                                         |
| `DBPROP_REENTRANTEVENTS `                 | R   | `VARIANT_FALSE`                                                                                                                                                                         |
| `DBPROP_REMOVEDELETED `                   | R   | `VARIANT_FALSE`                                                                                                                                                                         |
| `DBPROP_REPORTMULTIPLECHANGES `           | R   | `VARIANT_FALSE`                                                                                                                                                                         |
| `DBPROP_RETURNPENDINGINSERTS `            | R   | `VARIANT_FALSE`                                                                                                                                                                         |
| `DBPROP_ROWRESTRICT `                     | R   | `VARIANT_FALSE`                                                                                                                                                                         |
| `DBPROP_ROWTHREADMODEL `                  | R   | `DBPROPVAL_RT_FREETHREAD`                                                                                                                                                               |
| `DBPROP_SERVERCURSOR `                    | R/W | `VARIANT_FALSE`                                                                                                                                                                         |
| `DBPROP_STRONGIDENTITY `                  | R/W | `VARIANT_TRUE`                                                                                                                                                                          |
| `DBPROP_UNIQUEROWS `                      | R/W | `VARIANT_FALSE`                                                                                                                                                                         |
| `DBPROP_UPDATABILITY`                     | R   | `0` (not supported)                                                                                                                                                                     |

##### Rowset Property Implications

OraOLEDB OLAP sets other necessary properties if a particular property is set to `VARIANT_TRUE`.

If `DBPROP_IROWSETLOCATE` is set to `VARIANT_TRUE`, the following properties are also set to `VARIANT_TRUE`:

- `DBPROP_CANHOLDROWS`

- `DBPROP_BOOKMARKS`

- `DBPROP_CANFETCHBACKWARDS`

- `DBPROP_CANSCROLLBACKWARDS`

If `DBPROP_IROWSETSCROLL` is set to `VARIANT_TRUE`, the following properties are also set to `VARIANT_TRUE`:

- `DBPROP_IROWSETLOCATE`

- `DBPROP_CANHOLDROWS`

- `DBPROP_BOOKMARKS`

- `DBPROP_CANFETCHBACKWARDS`

- `DBPROP_CANSCROLLBACKWARDS`

#### Session Properties

Table B-6 lists the data source info properties that this release supports, with their default values.

Table B-6 DBPROPSET_SESSION

| Property                          | R/W | Default Value       |
|:----------------------------------|:----|:--------------------|
| `DBPROP_SESS_AUTOCOMMITISOLEVELS` | R   | `0` (not supported) |

### Provider-Specific Properties

Oracle OLAP Provider for OLE DB provides the following provider-specific properties:

- Rowset-Related Property

- Provider-Specific Command Properties

#### Rowset-Related Property

Table B-7 lists the rowset-related provider-specific OLE DB property.

Table B-7 Rowset Fetch Size

| Property Name                         | Type     | R/W | Default Value |
|:--------------------------------------|:---------|:----|:--------------|
| `DBPROP_ORAOLEDBOLAP_ROWSETFETCHSIZE` | `VT_I4 ` | R/W | `262144`      |

#### Provider-Specific Command Properties

Table B-8 lists the provider-specific OLE DB Properties, which are related to cube caching and enabling maximum precision of `NUMBER` and `FLOAT` column values.

Table B-8 Caching-Related Properties

| Property Name                              | Type                     | R/W | Default Value    |
|:-------------------------------------------|:-------------------------|:----|:-----------------|
| `MDPROP_ORAOLEDBOLAP_CELLDATACACHE`        | `VT_BOOL`                | R/W | `VARIANT_TRUE`   |
| `MDPROP_ORAOLEDBOLAP_CACHEBLOCKSIZE`       | `VT_ARRAY |`<br>`VT_I4 ` | R/W | `NULL`           |
| `MDPROP_ORAOLEDBOLAP_PRESERVEMAXPRECISION` | `VT_BOOL`                | R/W | `VARIANT_FALSE ` |
