These topics provide provider-specific information that is applicable for both OLE DB and ADO MD users.

- Oracle Datatypes Supported

- Schema Rowsets Supported

- Tracing

- MDX Keywords

### Oracle Datatypes Supported

The following Oracle datatypes are supported:

- `BINARY_DOUBLE`

- `BINARY_FLOAT`

- `CHAR`

- `DATE`

- `FLOAT`

- `NCHAR`

- `NUMBER`

- `NVARCHAR2`

- `VARCHAR2`

### Schema Rowsets Supported

This section lists the following:

- Core OLE DB Schema Rowsets

- OLE DB for OLAP Schema Rowsets

#### Core OLE DB Schema Rowsets

This section lists the core OLE DB schema rowsets and their restriction columns that are supported by OraOLEDB OLAP.

For completeness, all the restriction columns defined by the core OLE DB specification are listed for each schema rowset that is supported. The restriction columns that are actually supported by OraOLEDB OLAP are indicated by an asterisk (\*). For all core OLE DB schema rowsets, `CATALOG` related restriction columns are not supported since Oracle does not understand the concept of a catalog. Instead, the `SCHEMA_NAME` restriction column can be used to fetch information pertaining to a specific schema.

Setting a restriction on an unsupported column causes an error to be returned. However, as noted in the OLE DB specifications, the value for the unsupported restriction should be a `VARIANT` whose `vt` element is set to `VT_EMPTY`.

##### COLUMNS Rowset

The restrictions columns for the `COLUMNS` schema rowset are:

- `TABLE_CATALOG`\*

- `TABLE_SCHEMA` \*

- `TABLE_NAME` \*

- `COLUMN_NAME` \*

##### SCHEMATA Rowset

The restrictions columns for the `SCHEMATA` schema rowset are:

- `CATALOG_NAME`\*

- `SCHEMA_NAME` \*

- `SCHEMA_OWNER`

##### TABLES Rowset

The restrictions columns for the `TABLES` schema rowset are:

- `TABLE_CATALOG` \*

- `TABLE_SCHEMA` \*

- `TABLE_NAME` \*

- `TABLE_TYPE` \*

##### PROVIDER_TYPES Rowset

The restrictions columns for the `PROVIDER_TYPES` schema rowset are:

- `DATA_TYPE`

- `BEST_MATCH`

#### OLE DB for OLAP Schema Rowsets

This section lists the OLE DB for OLAP schema rowsets and their restriction columns that are supported by OraOLEDB OLAP.

For completeness, all the restriction columns defined by the OLE DB for OLAP specification are listed for each schema rowset that is supported. The restriction columns that are actually supported by OraOLEDB OLAP are indicated by an asterisk (\*). For all OLE DB for OLAP schema rowsets, `CATALOG` related restriction columns are not supported since Oracle does not understand the concept of a catalog. Instead, the `SCHEMA_NAME` restriction column can be used to fetch information pertaining to a specific schema.

##### CUBES Rowset

The restrictions columns for the `CUBES` schema rowset are:

- `CATALOG_NAME`\*

- `SCHEMA_NAME` \*

- `CUBE_NAME` \*

##### DIMENSIONS Rowset

The restrictions columns for the `DIMENSIONS` schema rowset are:

- `CATALOG_NAME` \*

- `SCHEMA_NAME` \*

- `CUBE_NAME` \*

- `DIMENSION_NAME` \*

- `DIMENSION_UNIQUE_NAME` \*

##### FUNCTIONS Rowset

The restrictions columns for the `FUNCTIONS` schema rowset are:

- `LIBRARY_NAME` \*

- `INTERFACE_NAME` \*

- `FUNCTION_NAME` \*

##### HIERARCHIES Rowset

The restrictions columns for the `HIERARCHIES` schema rowset are:

- `CATALOG_NAME` \*

- `SCHEMA_NAME` \*

- `CUBE_NAME` \*

- `DIMENSION_UNIQUE_NAME` \*

- `HIERARCHY_NAME` \*

- `HIERARCHY_UNIQUE_NAME` \*

##### LEVELS Rowset

The restrictions columns for the `LEVELS` schema rowset are:

- `CATALOG_NAME` \*

- `SCHEMA_NAME` \*

- `CUBE_NAME` \*

- `DIMENSION_UNIQUE_NAME` \*

- `HIERARCHY_UNIQUE_NAME` \*

- `LEVEL_NAME` \*

- `LEVEL_UNIQUE_NAME` \*

##### MEASURES Rowset

The restrictions columns for the `MEASURES` schema rowset are:

- `CATALOG_NAME` \*

- `SCHEMA_NAME` \*

- `CUBE_NAME` \*

- `MEASURE_NAME` \*

- `MEASURE_UNIQUE_NAME` \* (for a given measure, this name is the same as Members Rowset's `MEMBER_UNIQUE_NAME`)

##### MEMBERS Rowset

The restrictions columns for the `MEMBERS` schema rowset are:

- `CATALOG_NAME`\*

- `SCHEMA_NAME` \*

- `CUBE_NAME` \*

- `DIMENSION_UNIQUE_NAME` \*

- `HIERARCHY_UNIQUE_NAME` \*

- `LEVEL_UNIQUE_NAME` \*

- `LEVEL_NUMBER` \*

- `MEMBER_NAME` \*

- `MEMBER_UNIQUE_NAME` \* (for a given measure, this name is the same as `Measures` Rowset's `MEASURE_UNIQUE_NAME`)

- `MEMBER_TYPE` \*

- `MEMBER_CAPTION` \*

##### PROPERTIES Rowset

The restrictions columns for the `PROPERTIES` schema rowset are:

- `CATALOG_NAME`\*

- `SCHEMA_NAME` \*

- `CUBE_NAME` \*

- `DIMENSION_UNIQUE_NAME` \*

- `HIERARCHY_UNIQUE_NAME` \*

- `LEVEL_UNIQUE_NAME` \*

- `MEMBER_UNIQUE_NAME` \*

- `PROPERTY_NAME` \*

- `PROPERTY_TYPE` \*

##### SETS Rowsets

The `SETS` Schema Rowset is supported as required for a multidimensional data provider (MDP). However, a request for the `SETS` schema rowset always returns an empty rowset.

### Tracing

In order to trace the interface calls, you must configure the following registry values for `HKEY_LOCAL_MACHINE\SOFTWARE\ORACLE\OLEDBOLAP\`:

- `TraceFileName`

  Valid Value: Any valid path and filename

  `TraceFileName` specifies the filename that is to be used for logging trace information. If `TraceOption` is set to `0`, the name is used as is. However, if `TraceOption` is `1`, the thread ID is appended to the filename provided. See `TraceOption` for more information.

- `TraceCategory`

  Valid Values:

  - `0` = None

  - `1` = OLE DB and OLE DB for OLAP Interface method entry

  - `2` = OLE DB and OLE DB for OLAP Interface method exit

  `TraceCategory` specifies the information that is to be traced. Combinations of different tracing categories can be made by simply adding the valid values. For example, set `TraceCategory` to `3` to trace all OLE DB and OLE DB for OLAP interface method entries and exits.

- `TraceLevel`

  Valid Values:

  - `0` = None

  - `1` = Data Source object

  - `2` = Session object

  - `4` = Command object

  - `8` = Rowset object

  - `16` = Dataset object

  - `32` = Error object

  `TraceLevel` specifies the OLE DB and OLE DB for OLAP objects to be traced. Because tracing all the entry and exit calls for all the OLE DB and OLE DB for OLAP objects can be excessive, `TraceLevel` is provided to limit tracing to a single or multiple OLE DB and OLE DB for OLAP objects. To obtain tracing on multiple objects, simply add the valid values. For example, if `TraceLevel` is set to `12` and `TraceCategory` is set to `3`, the trace file will only contain method entry and exit for Command and Rowset objects.

  The `TraceLevel` value must be set to session object (`2`) to trace global transaction enlistment and delistment information.

- `TraceOption`

  Valid Values:

  - `0` = Single trace file

  - `1` = Multiple trace files

  `TraceOption` specifies whether to log trace information in single or multiple files for each Thread ID. If a single trace file is specified, the filename specified in `TraceFileName` is used. If multiple trace file is requested, a Thread ID is appended to the filename provided to create a trace file for each thread.

### MDX Keywords

Oracle OLAP Provider for OLE DB supports the following MDX keywords only. There are no provider-specific keywords.

- `ADDCALCULATEDMEMBERS`

- `AFTER`

- `AGGREGATE`

- `ALL`

- `ANCESTOR`

- `AND`

- `AS`

- `ASC`

- `AVG`

- `AXIS`

- `BACK_COLOR`

- `BASC`

- `BDESC`

- `BEFORE`

- `BEFORE_AND_AFTER`

- `BOTTOMCOUNT`

- `BOTTOMPERCENT`

- `BOTTOMSUM`

- `CATALOG_NAME`

- `CELL`

- `CELL_ORDINAL`

- `CHAPTERS`

- `CHILDREN`

- `CHILDREN_CARDINALITY`

- `COLUMNS`

- `COUNT`

- `CUBE_NAME`

- `CURRENT`

- `CURRENTMEMBER`

- `DEFAULTMEMBER`

- `DESC`

- `DESCENDANTS`

- `DESCRIPTION`

- `DIMENSION`

- `DIMENSION_UNIQUE_NAME`

- `DIMENSIONS`

- `DISTINCT`

- `DRILLDOWNLEVEL`

- `DRILLDOWNLEVELBOTTOM`

- `DRILLDOWNLEVELTOP`

- `DRILLDOWNMEMBER`

- `DRILLDOWNMEMBERBOTTOM`

- `DRILLDOWNMEMBERTOP`

- `DRILLUPLEVEL`

- `DRILLUPMEMBER`

- `EMPTY`

- `EXCEPT`

- `FILTER`

- `FIRSTCHILD`

- `FIRSTSIBLING`

- `FONT_FLAGS`

- `FONT_NAME`

- `FONT_SIZE`

- `FORE_COLOR`

- `FORMAT_STRING`

- `FORMATTED_VALUE`

- `FROM`

- `GENERATE` (set version)

- `HEAD`

- `HIERARCHIZE`

- `HIERARCHY`

- `HIERARCHY_UNIQUE_NAME`

- `INCLUDEEMPTY`

- `IIF`

- `INTERSECT`

- `IS`

- `ISANCESTOR`

- `ISEMPTY`

- `ISLEAF`

- `ISSIBLING`

- `ITEM`

- `LAG`

- `LASTCHILD`

- `LASTPERIODS`

- `LASTSIBLING`

- `LEAD`

- `LEVEL`

- `LEVEL_NUMBER`

- `LEVEL_UNIQUE_NAME`

- `LEVELS`

- `MAX`

- `MEDIAN`

- `MEMBER`

- `MEMBER_CAPTION`

- `MEMBER_GUID`

- `MEMBER_NAME`

- `MEMBER_ORDINAL`

- `MEMBER_TYPE`

- `MEMBER_UNIQUE_NAME`

- `MEMBERS`

- `MTD`

- `NAME`

- `NAMETOSET`

- `NEXTMEMBER`

- `NON`

- `NONEMPTYCROSSJOIN`

- `NOT`

- `NULL`

- `ON`

- `OR`

- `ORDER`

- `ORDINAL`

- `PAGES`

- `PARENT`

- `PARENT_COUNT`

- `PARENT_LEVEL`

- `PARENT_UNIQUE_NAME`

- `PERIODSTODATE`

- `PREVMEMBER`

- `PROPERTIES`

- `QTD`

- `RANK`

- `RECURSIVE`

- `ROWS`

- `SCHEMA_NAME`

- `SECTIONS`

- `SELECT`

- `SELF`

- `SELF_AND_AFTER`

- `SELF_AND_BEFORE`

- `SELF_BEFORE_AFTER`

- `SET`

- `SIBLINGS`

- `SOLVE_ORDER`

- `STDDEV`

- `STDDEVP`

- `STDEV`

- `STDEVP`

- `SUBSET`

- `SUM`

- `TAIL`

- `TOPCOUNT`

- `TOPPERCENT`

- `TOPSUM`

- `UNION`

- `UNIQUENAME`

- `USERNAME`

- `VALUE`

- `VAR`

- `VARIANCE`

- `VARIANCEP`

- `VARP`

- `WHERE`

- `WITH`

- `WTD`

- `YTD`
