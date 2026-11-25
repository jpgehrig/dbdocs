This appendix describes the changes that have occurred in the OLAP DML in previous releases. It contains the following topics:

- OLAP DML Statement Changes for Oracle Database 11g

- OLAP DML Statement Changes for Oracle Database 10g

- OLAP DML Statement Changes for Oracle Database 9i

### D.1 OLAP DML Statement Changes for Oracle Database 11g

This section contains listings of the OLAP DML statements that were added, changed, renamed, or deleted in Oracle Database 11g:

- Statements Added in Oracle Database 11g

- Statements Deleted in Oracle Database 11g

- Statements Changed in Oracle Database 11g

- Statements Changed in Oracle Database 11g

#### D.1.1 Statements Added in Oracle Database 11g

The following statements have been added to the OLAP DML in Oracle Database 11g. The number in parentheses indicates the specific release in which the statement was added.

- [\$GID_DEPTH](olap-dml-properties.md) system property (11.0.0.0)
- [\$GID_LIST](olap-dml-properties.md) system property (11.0.0.0)
- [\$GID_TYPE](olap-dml-properties.md) system property (11.0.0.0)
- [\$LOOP_AGGMAP](olap-dml-properties.md) system property (11.0.0.0)
- [\$LOOP_DENSE](olap-dml-properties.md) system property (11.0.0.0)
- [\$LOOP_VAR](olap-dml-properties.md) system property (11.0.0.0)
- [ADD_CUBE_MODEL](olap-dml-commands-a-g.md) program (11.2)
- [ADD_DIMENSION_MEMBER](olap-dml-commands-a-g.md) program (11.2)
- [ADD_MODEL_DIMENSION](olap-dml-commands-a-g.md) program (11.2)
- [AW FREEZE](olap-dml-commands-a-g.md) command (11.0.0.0)
- [AW PURGE CACHE](olap-dml-commands-a-g.md) command (11.0.0.0)
- [AW THAW](olap-dml-commands-a-g.md) command (11.0.0.0)
- [ASCIISTR](olap-dml-functions-a-k.md) function (11.2)
- [BIN_TO_NUM](olap-dml-functions-a-k.md) function (11.0.0.0)
- [CHANGEDRELATIONS](olap-dml-functions-a-k.md) function (11.0.0.0)
- [CHANGEDVALUES](olap-dml-functions-a-k.md) function (11.0.0.0)
- [CHARTOROWID](olap-dml-functions-a-k.md) function (11.0.0.0)
- [CREATE_LOGICAL_MODEL](olap-dml-commands-a-g.md) program (11.2)
- [CURRENT_DATE](olap-dml-functions-a-k.md) function (11.0.0.0)
- [CURRENT_TIMESTAMP](olap-dml-functions-a-k.md) function (11.0.0.0)
- [DATE_FORMAT](olap-dml-commands-a-g.md) command (11.0.0.0)
- [DBTIMEZONE](olap-dml-functions-a-k.md) function (11.0.0.0)
- [EXTRACT](olap-dml-functions-a-k.md) function (11.0.0.0)
- [FROM_TZ](olap-dml-functions-a-k.md) function (11.0.0.0)
- [GROUPINGID function](olap-dml-functions-a-k.md) (11.0.0.0)
- [HEXTORAW](olap-dml-functions-a-k.md) function (11.2)
- [HIERDEPTH](olap-dml-commands-h-z.md) command (11.0.0.0)
- [HIERSHAPE](olap-dml-functions-a-k.md) function (11.2)
- [INSTR functions](olap-dml-functions-a-k.md) (11.0.0.0)
- [ISEMPTY](olap-dml-functions-a-k.md) function (11.0.0.0)
- [ISINFINITE](olap-dml-functions-a-k.md) function (11.2)
- [ISNAN](olap-dml-functions-a-k.md) function (11.2)
- [LENGTH functions](olap-dml-functions-l-z.md) (11.0.0.0)
- [LNNVL](olap-dml-functions-l-z.md) function (11.0.0.0)
- [LOCALTIMESTAMP](olap-dml-functions-l-z.md) function (11.0.0.0)
- [LOWER](olap-dml-functions-l-z.md) function (11.2)
- [MODULO](olap-dml-functions-l-z.md) function (11.0.0.0)
- [NA2](olap-dml-functions-l-z.md) function (11.0.0.0)
- [NAFLAG](olap-dml-functions-l-z.md) function (11.0.0.0)
- [NLS_CHARSET_ID](olap-dml-functions-l-z.md) function (11.2)
- [NLS_CHARSET_NAME](olap-dml-functions-l-z.md) function (11.2)
- [NLSSORT](olap-dml-functions-l-z.md) function (11.0.0.0)
- [NUMTODSINTERVAL](olap-dml-functions-l-z.md) function (11.1.0.0)
- [NUMTOYMINTERVAL](olap-dml-functions-l-z.md) function (11.1.0.0)
- [OBJORG](olap-dml-functions-l-z.md) function (11.2)
- [ORA_HASH](olap-dml-functions-l-z.md) function (11.2)
- [PARTITION](olap-dml-functions-l-z.md) function (11.0.0.0)
- [PERMITREADERROR](olap-dml-options.md) option (11.2)
- [RAWTOHEX](olap-dml-functions-l-z.md) function (11.2)
- [REGEXP_COUNT](olap-dml-functions-l-z.md)function (11.2)
- [REGEXP_INSTR](olap-dml-functions-l-z.md) function (11.2)
- [REGEXP_REPLACE](olap-dml-functions-l-z.md) function (11.2)
- [REGEXP_SUBSTR](olap-dml-functions-l-z.md) function (11.2)
- [REMAINDER](olap-dml-functions-l-z.md) function (11.0.0.0)
- [REMOVE_CUBE_MODEL](olap-dml-commands-h-z.md) program (11.2)
- [REMOVE_DIMENSION_MEMBER](olap-dml-commands-h-z.md) program (11.2)
- [REMOVE_MODEL_DIMENSION](olap-dml-commands-h-z.md) program (11.2)
- [REPLACE](olap-dml-functions-l-z.md) function (11.0.0.0)
- [ROWIDTOCHAR](olap-dml-functions-l-z.md) function (11.0.0.0)
- [ROWIDTONCHAR](olap-dml-functions-l-z.md) function (11.0.0.0)
- [SESSIONTIMEZONE](olap-dml-functions-l-z.md) function (11.0.0.0)
- [SET_INCLUDED_MODEL](olap-dml-commands-h-z.md) program (11.2)
- [SET_PROPERTY](olap-dml-commands-h-z.md) program (11.2)
- [SOUNDEX](olap-dml-functions-l-z.md) function (11.2)
- [STATCURR](olap-dml-functions-l-z.md) function (11.2)
- [SYS_CONTEXT](olap-dml-functions-l-z.md) function (11.0.0.0)
- [SYSTIMESTAMP](olap-dml-functions-l-z.md) function (11.0.0.0)
- [TO_BINARY_DOUBLE](olap-dml-functions-l-z.md) function (11.2)
- [TO_BINARY_FLOAT](olap-dml-functions-l-z.md) function (11.2)
- [TO_DSINTERVAL](olap-dml-functions-l-z.md) function (11.0.0.0)
- [TO_TIMESTAMP](olap-dml-functions-l-z.md) function (11.0.0.0)
- [TO_TIMESTAMP_TZ](olap-dml-functions-l-z.md) function (11.0.0.0)
- [TO_YMINTERVAL](olap-dml-functions-l-z.md) function (11.0.0.0)
- [TRACE](olap-dml-commands-h-z.md) command (11.2)
- [TZ_OFFSET](olap-dml-functions-l-z.md) function (11.0.0.0)
- [UPDATE_ATTRIBUTE_VALUE](olap-dml-commands-h-z.md) program (11.2)
- [UPDATE_DIMENSION_MEMBER](olap-dml-commands-h-z.md) program (11.2)
- [UPPER](olap-dml-functions-l-z.md) function (11.2)
- [VSIZE](olap-dml-functions-l-z.md) function (11.2)

#### D.1.2 Statements Deleted in Oracle Database 11g

The following statements were deleted from the OLAP DML in Oracle Database 11g. The number in parentheses indicates the specific release in which the statement was deleted.

- POUTFILEUNIT option (11.2)
- SORTCOMPOSITE option

#### D.1.3 Statements Changed in Oracle Database 11g

The following statements have been changed in the OLAP DML in Oracle Database 11g. The number in parentheses indicates the most recent release in which the statement was changed.

- [ACROSS](olap-dml-commands-a-g.md) command (11.2)
- [AGGREGATE command](olap-dml-commands-a-g.md) (11.0.0.0)
- [AW function](olap-dml-functions-a-k.md) (11.0.0.0)
- [AW ATTACH](olap-dml-commands-a-g.md) command (11.0.0.0)
- [AW DETACH](olap-dml-commands-a-g.md) command (11.0.0.0)
- [AW LIST](olap-dml-commands-a-g.md) command (11.0.0.0)
- [AW TRUNCATE](olap-dml-commands-a-g.md) command (11.0.0.0)
- [CHGDFN](olap-dml-commands-a-g.md) command (11.2)
- [CLEAR](olap-dml-commands-a-g.md) command (11.0.0.0)
- [CONVERT](olap-dml-functions-a-k.md) function (11.0.0.0)
- [DEFINE COMPOSITE](olap-dml-commands-a-g.md) (11.0.0.0)
- [DEFINE DIMENSION](olap-dml-commands-a-g.md) command (11.0.0.0)
- [DEFINE PARTITION TEMPLATE](olap-dml-commands-a-g.md) (11.0.0.0)
- [DEFINE VARIABLE](olap-dml-commands-a-g.md) command (11.0.0.0)
- [EXPORT (EIF)](olap-dml-commands-a-g.md) command (11.2)
- [GROUPINGID command](olap-dml-commands-a-g.md) (11.0.0.0)
- [IMPORT (EIF)](olap-dml-commands-h-z.md) command (11.2)
- [LOG function](olap-dml-functions-l-z.md) (11.0.0.0)
- [OBJ](olap-dml-functions-l-z.md) function (11.2)

#### D.1.4 Statements Renamed in Oracle Database 11g

No statements have been renamed in the OLAP DML in Oracle Database 11g.

### D.2 OLAP DML Statement Changes for Oracle Database 10g

This section contains listings of the OLAP DML statements that were added, changed, renamed, or deleted in Oracle Database 10g:

- Statements Added in Oracle Database 10g

- Statements Deleted in Oracle Database 10g

- Statements Changed in Oracle Database 10g

- Statements Renamed in Oracle Database 10g

#### D.2.1 Statements Added in Oracle Database 10g

The following statements were added to the OLAP DML in Oracle Database 10g. The number in parentheses indicates the specific release in which the statement was added.

- [\$AGGMAP](olap-dml-properties.md) property (10.1.0.0)
- [\$AGGREGATE_FORCECALC](olap-dml-properties.md) property (10.2.0.0)
- [\$AGGREGATE_FORCEORDER](olap-dml-properties.md) property (10.2.0.0)
- [\$AGGREGATE_FROM](olap-dml-properties.md) property (10.1.0.0)
- [\$AGGREGATE_FROMVAR](olap-dml-properties.md) property (10.1.0.0)
- [\$ALLOCMAP](olap-dml-properties.md) property (10.1.0.0)
- [\$COUNTVAR](olap-dml-properties.md) property (10.1.0.0)
- [\$DEFAULT_LANGUAGE](olap-dml-properties.md) property (10.2.0.0)
- [ACQUIRE](olap-dml-commands-a-g.md) command (10.1.0.0)
- [AGGCOUNT](olap-dml-functions-a-k.md) function (10.2.0.0)
- AGGMAP command, [DROP DIMENSION](olap-dml-commands-a-g.md) statement (10.1.0.0)
- AGGMAP command, [PRECOMPUTE](olap-dml-commands-a-g.md) statement (10.2.0.0)
- [AGGROPS](olap-dml-functions-a-k.md) function (10.2.0.0)
- ALLOCMAP command, [VALUESET](olap-dml-commands-a-g.md) statement (10.1.0.0)
- [ALLOCOPS](olap-dml-functions-a-k.md) function (10.2.0.0)
- [ARCTAN](olap-dml-functions-a-k.md) function (10.1.0.0)
- [ASCII](olap-dml-functions-a-k.md) function (10.1.0.0)
- [AW TRUNCATE](olap-dml-commands-a-g.md) command (10.1.0.3)
- [BITAND](olap-dml-functions-a-k.md) function (10.1.0.0)
- [CHR](olap-dml-functions-a-k.md) function (10.1.0.0)
- [COALESCE](olap-dml-functions-a-k.md) function (10.1.0.0)
- [DECODE](olap-dml-functions-a-k.md) function (10.1.0.0)
- [DEFINE PARTITION TEMPLATE](olap-dml-commands-a-g.md) command (10.1.0.0)
- [DROP DIMENSION](olap-dml-commands-a-g.md) statement of the AGGMAP command (10.1.0.0)
- [EXP](olap-dml-functions-a-k.md) function (10.1.0.0)
- [GREATEST](olap-dml-functions-a-k.md) function (10.1.0.0)
- [INF_STOP_ON_ERROR](olap-dml-options.md) option (10.1.0.0)
- [INITCAP](olap-dml-functions-a-k.md) function (10.1.0.0)
- [INSTR functions](olap-dml-functions-a-k.md) (INSTR and INSTRB) (10.1.0.0)
- [LEAST](olap-dml-functions-l-z.md) function (10.1.0.0)
- [LPAD](olap-dml-functions-l-z.md) function (10.1.0.0)
- [LIMIT BASEDIMS](olap-dml-commands-h-z.md) command (10.2.0.0)
- [LOCK_LANGUAGE_DIMS](olap-dml-options.md) option (10.2.0.0)
- [LTRIM](olap-dml-functions-l-z.md) function (10.1.0.0)
- [MAXFETCH](olap-dml-options.md) option (10.1.0.0)
- [NULLIF](olap-dml-functions-l-z.md) function (10.1.0.0)
- [NVL](olap-dml-functions-l-z.md) function (10.1.0.0)
- [NVL2](olap-dml-functions-l-z.md) function (10.1.0.0)
- [ONATTACH](olap-dml-programs.md) program (10.1.0.0)
- [PARTITIONCHECK](olap-dml-functions-l-z.md) function (10.1.0.0)
- [PRECOMPUTE](olap-dml-commands-a-g.md) statement in AGGMAP command (10.2.0.0)
- [RANK_CALLS](olap-dml-functions-l-z.md) option (10.2.0.0)
- [RANK_CELLS](olap-dml-functions-l-z.md) option (10.2.0.0)
- [RANK_SORTS](olap-dml-functions-l-z.md) option (10.2.0.0)
- [RELATION command](olap-dml-commands-h-z.md) (10.2.0.0)
- [RELEASE](olap-dml-commands-h-z.md) command (10.1.0.0)
- [RESYNC](olap-dml-commands-h-z.md) command (10.1.0.0)
- [REVERT](olap-dml-commands-h-z.md) command (10.1.0.0)
- [RPAD](olap-dml-functions-l-z.md) function (10.1.0.0)
- [RTRIM](olap-dml-functions-l-z.md) function (10.1.0.0)
- [SESSION_NLS_LANGUAGE](olap-dml-options.md) option (10.2.0.0)
- [SET1](olap-dml-commands-h-z.md) command (10.1.0.0)
- [SIGN](olap-dml-functions-l-z.md) function (10.1.0.0)
- [SORT function](olap-dml-functions-l-z.md) (10.2.0.0)
- [SQLFETCH](olap-dml-functions-l-z.md) function (10.2.0.0)
- [STATDEPTH](olap-dml-functions-l-z.md) function (10.2.0.0)
- [STATEQUAL](olap-dml-functions-l-z.md) function (10.2.0.2)
- [STATIC_SESSION_LANGUAGE](olap-dml-options.md) option (10.2.0.0)
- [SUBSTR functions](olap-dml-functions-l-z.md), SUBSTR and SUBTRB (10.1.0.0)
- [SUBSTR functions](olap-dml-functions-l-z.md), SUBSTRC, SUBSTR2, and SUBSTR4 (10.2.0.4)
- [TRANSLATE](olap-dml-functions-l-z.md) function (10.2.0.4)
- [TRIGGER command](olap-dml-commands-h-z.md) (10.1.0.0)
- [TRIGGER function](olap-dml-functions-l-z.md) (10.1.0.0)
- [TRIGGER_DEFINE](olap-dml-programs.md) program (10.1.0.0)
- [TRIGGER_AFTER_UPDATE](olap-dml-programs.md) program (10.1.0.0)
- [TRIGGER_BEFORE_UPDATE](olap-dml-programs.md) program (10.1.0.0)
- [TRIGGERASSIGN](olap-dml-commands-h-z.md) command (10.1.0.0)
- [TRIM](olap-dml-functions-l-z.md) function (10.1.0.0)
- [USETRIGGERS](olap-dml-options.md) option(10.1.0.0)
- [VALUESET](olap-dml-commands-a-g.md) statement in ALLOCMAP command (10.1.0.0)
- [WIDTH_BUCKET](olap-dml-functions-l-z.md) function (10.1.0.0)
- [WRAPERRORS](olap-dml-options.md) option (10.2.0.0)
- [WRITABLE](olap-dml-functions-l-z.md) function (10.2.0.0)

#### D.2.2 Statements Deleted in Oracle Database 10g

The following statements were deleted from the OLAP DML in Oracle Database 10g. The number in parentheses indicates the specific release in which the statement was deleted.

- AW ALLOCATE (10.1.0.0)
- ROLLUP (10.2.0.0)

#### D.2.3 Statements Changed in Oracle Database 10g

The following OLAP DML statements were significantly changed in Oracle Database 10g. Examples of significant changes are the addition of a new keyword or a change in a default value. The number in parentheses indicates the last release in which the statement was significantly changed.

- AGGMAPINFO (10.1.0.0)
- AGGREGATE command (10.2.0.0)
- AGGREGATE function (10.2.0.0)
- ARGUMENT (10.1.0.0)
- ANY (10.2.0.0)
- AVERAGE (10.2.0.0)
- AW function (10.2.0.0)
- AW ATTACH (10.1.0.0)
- CACHE (10.2.0.0)
- CHGDFN (10.2.0.0)
- CHGDIMS (10.1.0.3)
- COUNT (10.2.0.0)
- DEFINE COMPOSITE (10.1.0.0)
- DEFINE VARIABLE (10.2.0.0)
- DEPRDECL (10.2.0.0)
- DEPRDECLSW (10.2.0.0)
- DEPRSL (10.2.0.0)
- DEPRSOYD (10.2.0.0)
- EVERY (10.2.0.0)
- FINTSCHED (10.2.0.0)
- FPMTSCHED (10.2.0.0)
- HIERCHECK (10.2.0.2)
- LARGEST (10.2.0.0)
- LIMIT command (10.2.0.0)
- LIMIT function (10.2.0.0)
- MAINTAIN ADD SESSION (10.1.0.0)
- MAINTAIN ADD TO PARTITION (10.1.0.0)
- NONE (10.2.0.0)
- OBJ (10.2.0.3)
- RANK (10.2.0.0)
- RELATION (for aggregation) (10.2.0.0)
- SMALLEST (10.2.0.0)
- SORT command (10.1.0.3)
- SQL (10.1.0.0)
- STDDEV (10.2.0.0)
- TALLY (10.2.0.0)
- TOTAL (10.2.0.0)
- UPDATE (10.1.0.0)
- VARIABLE (10.1.0.0)
- VALSPERPAGE (10.1.0.0)
- VINTSCHED (10.2.0.0)
- VPMTSCHED (10.2.0.0)

#### D.2.4 Statements Renamed in Oracle Database 10g

No OLAP DML statements have been renamed in Oracle Database 10g.

### D.3 OLAP DML Statement Changes for Oracle Database 9i

This section contains listings of the OLAP DML statement changes in Oracle Database 9i.

- Statements Added in Oracle Database 9i

- Statements Deleted in Oracle Database 9i

- Statements Changed in Oracle Database 9i

- Statements Renamed in Oracle Database 9i

#### D.3.1 Statements Added in Oracle Database 9i

The following statements were added to the OLAP DML in Oracle Database 9i. The number in parentheses indicates the specific release in which the statement was added.

- ADD_MONTHS (9.0.0.0)
- ALLOCATE (9.2.0.0)
- ALLOCERRLOGFORMAT (9.2.0.0)
- ALLOCERRLOCHEADER (9.2.0.0)
- ALLOCMAP (9.2.0.0)
- BASEDIM (9.2.0.0)
- BASEVAL (9.2.0.0)
- CDA (9.2.0.0)
- CEIL (9.0.0.0)
- CHANGEBYTES (9.0.0.0)
- CHGDIMS (9.2.0.0)
- CHILDLOCK (9.2.0.0)
- COMMIT (9.2.0.0)
- DEADLOCK (9.2.0.0)
- ERRORLOG (9.2.0.0)
- ERRORMASK (9.2.0.0)
- EXTBYTES (9.0.0.0)
- FETCH (9.2.0.0)
- FINDBYTES (9.0.0.0)
- FLOOR (9.0.0.0)
- GROUPINGID (9.2.0.0)
- HIERHEIGHT command (9.2.0.0)
- HIERHEIGHT function (9.2.0.0)
- INSBYTES (9.0.0.0)
- JOINBYTES (9.0.0.0)
- LAST_DAY (9.0.0.0)
- LIMITMAPINFO (9.2.0.2)
- LIMITSTRICT (9.2.0.2)
- MAXBYTES (9.0.0.0)
- MAXFETCH (9.0.0.0)
- MONTHS_BETWEEN (9.0.0.0)
- MULTIPATHHIER (9.0.0.0)
- NEW_TIME (9.0.0.0)
- NEXT_DAY (9.0.0.0)
- NLS Options, specifically:

<!-- -->

- NLS_CALENDAR (9.0.0.0)
- NLS_CURRENCY (9.0.0.0)
- NLS_DATE_FORMAT (9.0.0.0)
- NLS_DATE_LANGUAGE (9.0.0.0)
- NLS_DUAL_CURRENCY (9.0.0.0)
- NLS_ISO_CURRENCY (9.0.0.0)
- NLS_LANG (9.0.0.0)
- NLS_LANGUAGE (9.0.0.0)
- NLS_NUMERIC_CHARACTERS (9.0.0.0)
- NLS_SORT (9.0.0.0)
- NLS_TERRITORY (9.0.0.0)

<!-- -->

- NULLIF (9.0.0.0)
- POUTFILEUNIT (9.2.0.0)
- REMBYTES (9.0.0.0)
- REPLBYTES (9.0.0.0)
- ROLE (9.0.0.0)
- SOURCEVAL (9.2.0.0)
- SYSDATE (9.0.0.0)
- TO_CHAR (9.0.0.0)
- TO_DATE (9.0.0.0)
- TO_NCHAR (9.2.0.0)
- TO_NUMBER (9.0.0.0)
- TRACEFILEUNIT (9.2.0.0)
- TRIM (9.0.0.0)
- USERID (9.0.0.0)

#### D.3.2 Statements Deleted in Oracle Database 9i

The following statements were deleted from the OLAP DML in Oracle Database 9i. The number in parentheses indicates the specific release in which the statement was deleted.

- \_UPDATEOLDVERS (9.2.0.0)
- \_XCALONGTIME (9.0.0.0)
- \_XCARETRIES (9.0.0.0)
- \_XCASHORTIME (9.0.0.0)
- ALLOWQONS (9.2.0.0)
- AW ALLOCATE (10.1.0.0)
- CACHEHITS (9.2.0.0)
- CACHEMISSES (9.2.0.0)
- CACHETRIES (9.2.0.0)
- CHARSET (9.0.0.0)
- CHDIR (9.2.0.0)
- CHDRIVE (9.2.0.0)
- COMQUERY (9.0.0.0)
- COMSET (9.0.0.0)
- COMUNIT (9.0.0.0)
- CONNECT (9.0.0.0)
- DBEXTENDPATH (9.2.0.0)
- DBGSESSION (9.2.0.0)
- DBREPORT (9.2.0.0)
- DBSEARCHPATH (9.2.0.0)
- DBTEMPPATH (9.2.0.0)
- DEFINE EXTCALL (9.0.0.0)
- DGCART (9.2.0.0)
- DIR (9.2.0.0)
- DISCONNECT (9.0.0.0)
- EPRODUCT (9.2.0.0)
- ERELEASE (9.2.0.0)
- EXECBREAK (9.0.0.0)
- EXECSTART (9.0.0.0)
- EXECSTATUS (9.0.0.0)
- EXECUTE (9.0.0.0)
- EXECWAIT (9.0.0.0)
- EXTARGS (9.0.0.0)
- FETCH (9.0.0.0) -- SNAPI
- FILEMODEMASK (9.2.0.0)
- IFCOPY (9.2.0.0)
- LONGOBJNAMES (9.0.0.0)
- MAXFETCH (9.0.0.0)
- MKDIR (9.0.0.0)
- NAPAGEFREE (9.2.0.0)
- ODBC.CONNECTION (9.0.0.0)
- ODBC.CONNLIST (9.0.0.0)
- ODBC.DISCONN (9.0.0.0)
- ODBC.SOURCE (9.0.0.0)
- ODBC.SOURCELIST (9.0.0.0)
- PGCACHEHITS (9.2.0.0)
- PGCACHEMISSES (9.2.0.0)
- PAGEPAUSE (9.2.0.0)
- PAGEPROMPT (9.2.0.0)
- PAUSE (9.2.0.0)
- RETRIEVE (9.0.0.0)
- RMDIR (9.0.0.0)
- SESSIONQUERY (9.0.0.0)
- SHARESESSION (9.0.0.0)
- SHELL (9.0.0.0)
- SQL CONNECT (9.0.0.0)
- SQL DISCONNECT (9.0.0.0)
- SQL.DMBS (9.0.0.0)
- SQL.DMBSLIST (9.0.0.0)
- STRIP (9.2.0.0)
- THREADEXTCALL (9.0.0.0)
- TRACE (9.2.0.0)
- TRANSLATE (9.0.0.0)
- TRANSPORT (9.0.0.0)
- WATCH (9.2.0.0)
- XABORT (9.0.0.0)
- XCAPORTNUMBER (9.0.0.0)
- XCLOSE (9.0.0.0)
- XOPEN (9.0.0.0)

#### D.3.3 Statements Changed in Oracle Database 9i

The following OLAP DML statements were significantly changed in Oracle Database 9i and have not changed since then. Examples of significant changes are the addition of a new keyword or a change in a default value. The number in parentheses indicates the last release in which the statement was significantly changed. See also "Statements Renamed in Oracle Database 9i" for a list of renamed statements.

- CONVERT (9.2.0.0)
- DECIMALCHAR (9.2.0.0)
- EXPORT (9.2.0.0)
- FCQUERY (9.2.0.0)
- FCSET (9.2.0.0)
- FILEOPEN (9.0.0.0)
- FILEQUERY (9.0.0.0)
- FILEREAD (9.2.0.0)
- HIERHEIGHT command (9.2.0.0)
- IMPORT (9.0.0.0)
- INFILE (9.0.0.0)
- LAG (9.2.0.2)
- LAGABSPCT (9.2.0.2)
- LAGDIF (9.2.0.2)
- LAGPCT (9.2.0.2)
- LEAD (9.2.0.2)
- MODEL (9.2.0.2)
- MOVINGAVERAGE (9.2.0.2)
- MOVINGMAX (9.2.0.2)
- MOVINGMIN (9.2.0.2)
- MOVINGTOTAL (9.2.0.2)
- NOSPELL (9.2.0.0)
- OUTFILE (9.0.0.0)
- PROGRAM (9.2.0.0)
- PROPERTY (9.0.0.0)
- RECURSIVE (9.0.0.0)
- RELATION (for aggregation) (9.2.0.2)
- RELATION (for allocation) (9.2.0.2)
- ROUND (9.0.0.0)
- SYSDATE (9.2.0.0)
- SYSINFO (9.2.0.2)
- SYSTEM (9.2.0.0)
- TALLY (10.2.0.0)
- THOUSANDSCHAR (9.2.0.0)
- YESSPELL (9.2.0.0)

#### D.3.4 Statements Renamed in Oracle Database 9i

The following OLAP DML statements were renamed in Oracle Database 9i. The number in parentheses indicates the specific release in which the statement was renamed.

- DATABASE command to AW command (9.2.0.0)
- DATABASE function to AW function (9.2.0.0)
- DBDESCRIBE to AWDESCRIBE (9.2.0.0)
- DBWAITTIME to AWWAITTIME (9.2.0.0)
- DEFAULTDBFSIZE t o DEFAULTAWSEGSIZE (9.2.0.0)
- OESEIFVERSION to EIFVERSION (9.2.0.0)

HCE
