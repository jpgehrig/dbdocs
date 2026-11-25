## Single-Row Functions

Single-row functions return a single result row for every row of a queried table or view. These functions can appear in select lists, `WHERE` clauses, `START` `WITH` and `CONNECT` `BY` clauses, and `HAVING` clauses.

### Numeric Functions

Numeric functions accept numeric input and return numeric values. Most numeric functions return `NUMBER` values that are accurate to 38 decimal digits. The transcendental functions `COS`, `COSH`, `EXP`, `LN`, `LOG`, `SIN`, `SINH`, `SQRT`, `TAN`, and `TANH` are accurate to 36 decimal digits. The transcendental functions `ACOS`, `ASIN`, `ATAN`, and `ATAN2` are accurate to 30 decimal digits. The numeric functions are:

- [ABS](ABS.md)
- [ACOS](ACOS.md)
- [ASIN](ASIN.md)
- [ATAN](ATAN.md)
- [ATAN2](ATAN2.md)
- [BITAND](BITAND.md)
- [CEIL](CEIL.md)
- [COS](COS.md)
- [COSH](COSH.md)
- [EXP](EXP.md)
- [FLOOR](FLOOR.md)
- [LN](LN.md)
- [LOG](LOG.md)
- [MOD](MOD.md)
- [NANVL](NANVL.md)
- [POWER](POWER.md)
- [REMAINDER](REMAINDER.md)
- [ROUND (number)](ROUND-number.md)
- [SIGN](SIGN.md)
- [SIN](SIN.md)
- [SINH](SINH.md)
- [SQRT](SQRT.md)
- [TAN](TAN.md)
- [TANH](TANH.md)
- [TRUNC (number)](TRUNC-number.md)
- [WIDTH_BUCKET](WIDTH_BUCKET.md)

### Character Functions Returning Character Values

Character functions that return character values return values of the following data types unless otherwise documented:

- If the input argument is `CHAR` or `VARCHAR2`, then the value returned is `VARCHAR2`.

- If the input argument is `NCHAR` or `NVARCHAR2`, then the value returned is `NVARCHAR2`.

The length of the value returned by the function is limited by the maximum length of the data type returned.

- For functions that return `CHAR` or `VARCHAR2`, if the length of the return value exceeds the limit, then Oracle Database truncates it and returns the result without an error message.

- For functions that return `CLOB` values, if the length of the return values exceeds the limit, then Oracle raises an error and returns no data.

The character functions that return character values are:

- [CHR](CHR.md)
- [CONCAT](CONCAT.md)
- [INITCAP](INITCAP.md)
- [LOWER](LOWER.md)
- [LPAD](LPAD.md)
- [LTRIM](LTRIM.md)
- [NCHR](NCHR.md)
- [NLS_INITCAP](NLS_INITCAP.md)
- [NLS_LOWER](NLS_LOWER.md)
- [NLS_UPPER](NLS_UPPER.md)
- [NLSSORT](NLSSORT.md)
- [REGEXP_REPLACE](REGEXP_REPLACE.md)
- [REGEXP_SUBSTR](REGEXP_SUBSTR.md)
- [REPLACE](REPLACE.md)
- [RPAD](RPAD.md)
- [RTRIM](RTRIM.md)
- [SOUNDEX](SOUNDEX.md)
- [SUBSTR](SUBSTR.md)
- [TRANSLATE](TRANSLATE.md)
- [TRANSLATE ... USING](TRANSLATE-USING.md)
- [TRIM](TRIM.md)
- [UPPER](UPPER.md)

### Character Functions Returning Number Values

Character functions that return number values can take as their argument any character data type. The character functions that return number values are:

- [ASCII](ASCII.md)
- [INSTR](INSTR.md)
- [LENGTH](LENGTH.md)
- [REGEXP_COUNT](REGEXP_COUNT.md)
- [REGEXP_INSTR](REGEXP_INSTR.md)

### Character Set Functions

The character set functions return information about the character set. The character set functions are:

- [NLS_CHARSET_DECL_LEN](NLS_CHARSET_DECL_LEN.md)
- [NLS_CHARSET_ID](NLS_CHARSET_ID.md)
- [NLS_CHARSET_NAME](NLS_CHARSET_NAME.md)

### Collation Functions

The collation functions return information about collation settings. The collation functions are:

- [COLLATION](COLLATION.md)
- [NLS_COLLATION_ID](NLS_COLLATION_ID.md)
- [NLS_COLLATION_NAME](NLS_COLLATION_NAME.md)

### Datetime Functions

Datetime functions operate on date (`DATE`), timestamp (`TIMESTAMP`, `TIMESTAMP` `WITH` `TIME` `ZONE`, and `TIMESTAMP` `WITH` `LOCAL` `TIME` `ZONE`), and interval (`INTERVAL` `DAY` `TO` `SECOND`, `INTERVAL` `YEAR` `TO` `MONTH`) values.

Some of the datetime functions were designed for the Oracle `DATE` data type (`ADD_MONTHS`, `CURRENT_DATE`, `LAST_DAY`, `NEW_TIME`, and `NEXT_DAY`). If you provide a timestamp value as their argument, then Oracle Database internally converts the input type to a `DATE` value and returns a `DATE` value. The exceptions are the `MONTHS_BETWEEN` function, which returns a number, and the `ROUND` and `TRUNC` functions, which do not accept timestamp or interval values at all.

The remaining datetime functions were designed to accept any of the three types of data (date, timestamp, and interval) and to return a value of one of these types.

All of the datetime functions that return current system datetime information, such as `SYSDATE`, `SYSTIMESTAMP`, `CURRENT_TIMESTAMP`, and so forth, are evaluated once for each SQL statement, regardless how many times they are referenced in that statement.

The datetime functions are:

- [ADD_MONTHS](ADD_MONTHS.md)
- [CURRENT_DATE](CURRENT_DATE.md)
- [CURRENT_TIMESTAMP](CURRENT_TIMESTAMP.md)
- [DBTIMEZONE](DBTIMEZONE.md)
- [EXTRACT (datetime)](EXTRACT-datetime.md)
- [FROM_TZ](FROM_TZ.md)
- [LAST_DAY](LAST_DAY.md)
- [LOCALTIMESTAMP](LOCALTIMESTAMP.md)
- [MONTHS_BETWEEN](MONTHS_BETWEEN.md)
- [NEW_TIME](NEW_TIME.md)
- [NEXT_DAY](NEXT_DAY.md)
- [NUMTODSINTERVAL](NUMTODSINTERVAL.md)
- [NUMTOYMINTERVAL](NUMTOYMINTERVAL.md)
- [ORA_DST_AFFECTED](ORA_DST_AFFECTED.md)
- [ORA_DST_CONVERT](ORA_DST_CONVERT.md)
- [ORA_DST_ERROR](ORA_DST_ERROR.md)
- [ROUND (date)](ROUND-date.md)
- [SESSIONTIMEZONE](SESSIONTIMEZONE.md)
- [SYS_EXTRACT_UTC](SYS_EXTRACT_UTC.md)
- [SYSDATE](SYSDATE.md)
- [SYSTIMESTAMP](SYSTIMESTAMP.md)
- [TO_CHAR (datetime)](TO_CHAR-datetime.md)
- [TO_DSINTERVAL](TO_DSINTERVAL.md)
- [TO_TIMESTAMP](TO_TIMESTAMP.md)
- [TO_TIMESTAMP_TZ](TO_TIMESTAMP_TZ.md)
- [TO_YMINTERVAL](TO_YMINTERVAL.md)
- [TRUNC (date)](TRUNC-date.md)
- [TZ_OFFSET](TZ_OFFSET.md)

### General Comparison Functions

The general comparison functions determine the greatest and or least value from a set of values. The general comparison functions are:

- [GREATEST](GREATEST.md)
- [LEAST](LEAST.md)

### Conversion Functions

Conversion functions convert a value from one data type to another. Generally, the form of the function names follows the convention `datatype` `TO` `datatype`. The first data type is the input data type. The second data type is the output data type. The SQL conversion functions are:

- [ASCIISTR](ASCIISTR.md)
- [BIN_TO_NUM](BIN_TO_NUM.md)
- [CAST](CAST.md)
- [CHARTOROWID](CHARTOROWID.md)
- [COMPOSE](COMPOSE.md)
- [CONVERT](CONVERT.md)
- [DECOMPOSE](DECOMPOSE.md)
- [HEXTORAW](HEXTORAW.md)
- [NUMTODSINTERVAL](NUMTODSINTERVAL.md)
- [NUMTOYMINTERVAL](NUMTOYMINTERVAL.md)
- [RAWTOHEX](RAWTOHEX.md)
- [RAWTONHEX](RAWTONHEX.md)
- [ROWIDTOCHAR](ROWIDTOCHAR.md)
- [ROWIDTONCHAR](ROWIDTONCHAR.md)
- [SCN_TO_TIMESTAMP](SCN_TO_TIMESTAMP.md)
- [TIMESTAMP_TO_SCN](TIMESTAMP_TO_SCN.md)
- [TO_BINARY_DOUBLE](TO_BINARY_DOUBLE.md)
- [TO_BINARY_FLOAT](TO_BINARY_FLOAT.md)
- [TO_BLOB (bfile)](TO_BLOB-bfile.md)
- [TO_BLOB (raw)](TO_BLOB-raw.md)
- [TO_CHAR (bfile\|blob)](TO_CHAR-bfile-blob.md)
- [TO_CHAR (character)](TO_CHAR-character.md)
- [TO_CHAR (datetime)](TO_CHAR-datetime.md)
- [TO_CHAR (number)](TO_CHAR-number.md)
- [TO_CLOB (bfile\|blob)](TO_CLOB-bfile-blob.md)
- [TO_CLOB (character)](TO_CLOB-character.md)
- [TO_DATE](TO_DATE.md)
- [TO_DSINTERVAL](TO_DSINTERVAL.md)
- [TO_LOB](TO_LOB.md)
- [TO_MULTI_BYTE](TO_MULTI_BYTE.md)
- [TO_NCHAR (character)](TO_NCHAR-character.md)
- [TO_NCHAR (datetime)](TO_NCHAR-datetime.md)
- [TO_NCHAR (number)](TO_NCHAR-number.md)
- [TO_NCLOB](TO_NCLOB.md)
- [TO_NUMBER](TO_NUMBER.md)
- [TO_SINGLE_BYTE](TO_SINGLE_BYTE.md)
- [TO_TIMESTAMP](TO_TIMESTAMP.md)
- [TO_TIMESTAMP_TZ](TO_TIMESTAMP_TZ.md)
- [TO_YMINTERVAL](TO_YMINTERVAL.md)
- [TREAT](TREAT.md)
- [UNISTR](UNISTR.md)
- [VALIDATE_CONVERSION](VALIDATE_CONVERSION.md)

### Large Object Functions

The large object functions operate on LOBs. The large object functions are:

- [BFILENAME](BFILENAME.md)
- [EMPTY_BLOB, EMPTY_CLOB](EMPTY_BLOB-EMPTY_CLOB.md)

### Collection Functions

The collection functions operate on nested tables and varrays. The SQL collection functions are:

- [CARDINALITY](CARDINALITY.md)
- [COLLECT](COLLECT.md)
- [POWERMULTISET](POWERMULTISET.md)
- [POWERMULTISET_BY_CARDINALITY](POWERMULTISET_BY_CARDINALITY.md)
- [SET](SET.md)

### Hierarchical Functions

Hierarchical functions applies hierarchical path information to a result set. The hierarchical function is:

- [SYS_CONNECT_BY_PATH](SYS_CONNECT_BY_PATH.md)

### Data Mining Functions

The data mining functions use Oracle Advanced Analytics to score data. The functions can apply a mining model schema object to the data, or they can dynamically mine the data by executing an analytic clause. The data mining functions can be applied to models built using the native algorithms of Oracle, as well as those built using R through the extensibility mechanism of Oracle Advanced Analytics.

The data mining functions are:

- [CLUSTER_DETAILS](CLUSTER_DETAILS.md)
- [CLUSTER_DISTANCE](CLUSTER_DISTANCE.md)
- [CLUSTER_ID](CLUSTER_ID.md)
- [CLUSTER_PROBABILITY](CLUSTER_PROBABILITY.md)
- [CLUSTER_SET](CLUSTER_SET.md)
- [FEATURE_COMPARE](FEATURE_COMPARE.md)
- [FEATURE_DETAILS](FEATURE_DETAILS.md)
- [FEATURE_ID](FEATURE_ID.md)
- [FEATURE_SET](FEATURE_SET.md)
- [FEATURE_VALUE](FEATURE_VALUE.md)
- [ORA_DM_PARTITION_NAME](ORA_DM_PARTITION_NAME.md)
- [PREDICTION](PREDICTION.md)
- [PREDICTION_BOUNDS](PREDICTION_BOUNDS.md)
- [PREDICTION_COST](PREDICTION_COST.md)
- [PREDICTION_DETAILS](PREDICTION_DETAILS.md)
- [PREDICTION_PROBABILITY](PREDICTION_PROBABILITY.md)
- [PREDICTION_SET](PREDICTION_SET.md)

**See Also:**

- [Oracle Data Mining Concepts](../dmcon/index.md) to learn about Oracle Data Mining

- [Oracle Data Mining User’s Guide](../dmapi/scoring-deployment.md) for information about scoring

### XML Functions

The XML functions operate on or return XML documents or fragments. These functions use arguments that are not defined as part of the ANSI/ISO/IEC SQL Standard but are defined as part of the World Wide Web Consortium (W3C) standards. The processing and operations that the functions perform are defined by the relevant W3C standards. The table below provides a link to the appropriate section of the W3C standard for the rules and guidelines that apply to each of these XML-related arguments. A SQL statement that uses one of these XML functions, where any of the arguments does not conform to the relevant W3C syntax, will result in an error. Of special note is the fact that not every character that is allowed in the value of a database column is considered legal in XML.

| Syntax Element     | W3C Standard URL                                                                                                                                                                                             |
|:-------------------|:-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `value_expr`       | [`http://www.w3.org/TR/2006/REC-xml-20060816`](http://www.w3.org/TR/2006/REC-xml-20060816)                                                                                                                   |
| `Xpath_string`     | [`http://www.w3.org/TR/1999/REC-xpath-19991116`](http://www.w3.org/TR/1999/REC-xpath-19991116)                                                                                                               |
| `XQuery_string`    | [`http://www.w3.org/TR/2007/REC-xquery-semantics-20070123/`](http://www.w3.org/TR/2007/REC-xquery-semantics-20070123/)<br>[`http://www.w3.org/TR/xquery-update-10/`](http://www.w3.org/TR/xquery-update-10/) |
| `namespace_string` | [`http://www.w3.org/TR/2006/REC-xml-names-20060816/`](http://www.w3.org/TR/2006/REC-xml-names-20060816/)                                                                                                     |
| `identifier`       | [`http://www.w3.org/TR/2006/REC-xml-20060816/#NT-Nmtoken`](http://www.w3.org/TR/2006/REC-xml-20060816/#NT-Nmtoken)                                                                                           |

For more information about selecting and querying XML data using these functions, including information on formatting output, refer to [Oracle XML DB Developer’s Guide](../adxdb/query-and-update-XML.md)

The SQL XML functions are:

- [DEPTH](DEPTH.md)
- [EXISTSNODE](EXISTSNODE.md)
- [EXTRACT (XML)](EXTRACT-XML.md)
- [EXTRACTVALUE](EXTRACTVALUE.md)
- [PATH](PATH.md)
- [SYS_DBURIGEN](SYS_DBURIGEN.md)
- [SYS_XMLAGG](SYS_XMLAGG.md)
- [SYS_XMLGEN](SYS_XMLGEN.md)
- [XMLAGG](XMLAGG.md)
- [XMLCAST](XMLCAST.md)
- [XMLCDATA](XMLCDATA.md)
- [XMLCOLATTVAL](XMLCOLATTVAL.md)
- [XMLCOMMENT](XMLCOMMENT.md)
- [XMLCONCAT](XMLCONCAT.md)
- [XMLDIFF](XMLDIFF.md)
- [XMLELEMENT](XMLELEMENT.md)
- [XMLEXISTS](XMLEXISTS.md)
- [XMLFOREST](XMLFOREST.md)
- [XMLISVALID](XMLISVALID.md)
- [XMLPARSE](XMLPARSE.md)
- [XMLPATCH](XMLPATCH.md)
- [XMLPI](XMLPI.md)
- [XMLQUERY](XMLQUERY.md)
- [XMLROOT](XMLROOT.md)
- [XMLSEQUENCE](XMLSEQUENCE.md)
- [XMLSERIALIZE](XMLSERIALIZE.md)
- [XMLTABLE](XMLTABLE.md)
- [XMLTRANSFORM](XMLTRANSFORM.md)

### JSON Functions

JavaScript Object Notation (JSON) functions allow you to query and generate JSON data.

The following SQL/JSON functions allow you to query JSON data:

- [JSON_QUERY](JSON_QUERY.md)
- [JSON_TABLE](JSON_TABLE.md)
- [JSON_VALUE](JSON_VALUE.md)

The following SQL/JSON functions allow you to generate JSON data:

- [JSON_ARRAY](JSON_ARRAY.md)
- [JSON_ARRAYAGG](JSON_ARRAYAGG.md)
- [JSON_OBJECT](JSON_OBJECT.md)
- [JSON_OBJECTAGG](JSON_OBJECTAGG.md)

The following Oracle SQL function creates a JSON data guide:

- [JSON_DATAGUIDE](JSON_DATAGUIDE.md)

### Encoding and Decoding Functions

The encoding and decoding functions let you inspect and decode data in the database. The encoding and decoding functions are:

- [DECODE](DECODE.md)
- [DUMP](DUMP.md)
- [ORA_HASH](ORA_HASH.md)
- [STANDARD_HASH](STANDARD_HASH.md)
- [VSIZE](VSIZE.md)

### NULL-Related Functions

The `NULL`-related functions facilitate null handling. The `NULL`-related functions are:

- [COALESCE](COALESCE.md)
- [LNNVL](LNNVL.md)
- [NANVL](NANVL.md)
- [NULLIF](NULLIF.md)
- [NVL](NVL.md)
- [NVL2](NVL2.md)

### Environment and Identifier Functions

The environment and identifier functions provide information about the instance and session. The environment and identifier functions are:

- [CON_DBID_TO_ID](CON_DBID_TO_ID.md)
- [CON_GUID_TO_ID](CON_GUID_TO_ID.md)
- [CON_NAME_TO_ID](CON_NAME_TO_ID.md)
- [CON_UID_TO_ID](CON_UID_TO_ID.md)
- [ORA_INVOKING_USER](ORA_INVOKING_USER.md)
- [ORA_INVOKING_USERID](ORA_INVOKING_USERID.md)
- [SYS_CONTEXT](SYS_CONTEXT.md)
- [SYS_GUID](SYS_GUID.md)
- [SYS_TYPEID](SYS_TYPEID.md)
- [UID](UID.md)
- [USER](USER.md)
- [USERENV](USERENV.md)
