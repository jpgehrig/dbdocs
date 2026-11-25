## 2  SQL Functions

This chapter presents the syntax for SQL functions.

This chapter includes the following section:

- Syntax for SQL Functions

### Syntax for SQL Functions

A function is a command that manipulates data items and returns a single value.

The sections that follow show each SQL function and its related syntax. Refer to [Subclauses](Subclauses.md) for the syntax of the subclauses.

**See Also:**

[Oracle Database SQL Language Reference](../sqlrf/Functions.md) for detailed information about SQL functions

#### [ABS](../sqlrf/ABS.md)

    ABS(n)

#### [ACOS](../sqlrf/ACOS.md)

    ACOS(n)

#### [ADD_MONTHS](../sqlrf/ADD_MONTHS.md)

    ADD_MONTHS(date, integer)

#### [aggregate_function](../sqlrf/Aggregate-Functions.md)

Aggregate functions return a single result row based on groups of rows, rather than on single rows.

#### [analytic_function](../sqlrf/Analytic-Functions.md)

    analytic_function([ arguments ]) OVER (analytic_clause)

#### [ANY_VALUE](../sqlrf/any_value.md)

    ANY_VALUE ( [ DISTINCT | ALL ] expr )

#### [APPROX_COUNT](../sqlrf/APPROX_COUNT.md)

    APPROX_COUNT ( expr [ , expr 'MAX_ERROR' ]... )

#### [APPROX_COUNT_DISTINCT](../sqlrf/APPROX_COUNT_DISTINCT.md)

    APPROX_COUNT_DISTINCT(expr)

#### [APPROX_COUNT_DISTINCT_AGG](../sqlrf/index.md)

    APPROX_COUNT_DISTINCT_AGG(detail)

#### [APPROX_COUNT_DISTINCT_DETAIL](../sqlrf/index.md)

    APPROX_COUNT_DISTINCT_DETAIL(expr)

#### [APPROX_MEDIAN](../sqlrf/index.md)

    APPROX_MEDIAN( expr [ DETERMINISTIC ] [, { 'ERROR_RATE' | 'CONFIDENCE' } ] )

#### [APPROX_PERCENTILE](../sqlrf/index.md)

    APPROX_PERCENTILE( expr [ DETERMINISTIC ] [, { 'ERROR_RATE' | 'CONFIDENCE' } ] )
      WITHIN GROUP ( ORDER BY expr [ DESC | ASC ] )

#### [APPROX_PERCENTILE_AGG](../sqlrf/index.md)

    APPROX_PERCENTILE_AGG(expr)

#### [APPROX_PERCENTILE_DETAIL](../sqlrf/index.md)

    APPROX_PERCENTILE_DETAIL( expr [ DETERMINISTIC ] )

#### [APPROX_RANK](../sqlrf/APPROX_RANK.md)

    APPROX_RANK ( expr [ PARTITION BY partition_by_clause ] [ ORDER BY order_by_clause DESC] )

#### [APPROX_SUM](../sqlrf/APPROX_SUM.md)

    APPROX_SUM ( expr [ , expr 'MAX_ERROR' ] ...)

#### [ASCII](../sqlrf/ASCII.md)

    ASCII(char)

#### [ASCIISTR](../sqlrf/ASCIISTR.md)

    ASCIISTR(char)

#### [ASIN](../sqlrf/ASIN.md)

    ASIN(n)

#### [ATAN](../sqlrf/ATAN.md)

    ATAN(n)

#### [ATAN2](../sqlrf/ATAN2.md)

    ATAN2(n1 , n2)

#### [AVG](../sqlrf/AVG.md)

    AVG([ DISTINCT | ALL ] expr) [ OVER(analytic_clause) ]

#### [BFILENAME](../sqlrf/BFILENAME.md)

    BFILENAME('directory', 'filename')

#### [BIN_TO_NUM](../sqlrf/BIN_TO_NUM.md)

    BIN_TO_NUM(expr [, expr ]... )

#### [BITAND](../sqlrf/BITAND.md)

    BITAND(expr1, expr2)

#### [BITMAP_BIT_POSITION](../sqlrf/BITMAP_BIT_POSITION.md)

    BITMAP_BIT_POSITION  ( expr )

#### [BITMAP_BUCKET_NUMBER](../sqlrf/BITMAP_BUCKET_NUMBER.md)

    BITMAP_BUCKET_NUMBER ( expr )

#### [BITMAP_CONSTRUCT_AGG](../sqlrf/BITMAP_CONSTRUCT_AGG.md)

    BITMAP_CONSTRUCT_AGG (  expr  )

#### [BITMAP_COUNT](../sqlrf/BITMAP_COUNT.md)

    BITMAP_COUNT ( expr )

#### [BITMAP_OR_AGG](../sqlrf/BITMAP_OR_AGG.md)

    BITMAP_OR_AGG ( expr )

#### [CARDINALITY](../sqlrf/CARDINALITY.md)

    CARDINALITY(nested_table)

#### [CAST](../sqlrf/CAST.md)

    CAST({ expr | MULTISET (subquery) } AS type_name
      [ DEFAULT return_value ON CONVERSION ERROR ]
      [, fmt [, 'nlsparam' ] ])

#### [CEIL](../sqlrf/CEIL.md)

    CEIL(n)

#### [CHARTOROWID](../sqlrf/CHARTOROWID.md)

    CHARTOROWID(char)

#### [CHR](../sqlrf/CHR.md)

    CHR(n [ USING NCHAR_CS ])

#### [CLUSTER_DETAILS (aggregate)](../sqlrf/CLUSTER_DETAILS.md)

    CLUSTER_DETAILS ( [ schema . ] model
                      [ , cluster_id [ , topN ] ] [ DESC | ASC | ABS ]
                      mining_attribute_clause )

#### [CLUSTER_DETAILS (analytic)](../sqlrf/CLUSTER_DETAILS.md)

    CLUSTER_DETAILS ( INTO n
                      [ , cluster_id [ , topN ] ] [ DESC | ASC | ABS ]
                      mining_attribute_clause )
                    OVER ( mining_analytic_clause )

#### [CLUSTER_DISTANCE (aggregate)](../sqlrf/CLUSTER_DISTANCE.md)

    CLUSTER_DISTANCE ( [ schema . ] model [ , cluster_id ] mining_attribute_clause )

#### [CLUSTER_DISTANCE (analytic)](../sqlrf/CLUSTER_DISTANCE.md)

    CLUSTER_DISTANCE ( INTO n [, cluster_id] mining_attribute_clause )
                     OVER ( mining_analytic_clause )

#### [CLUSTER_ID (aggregate)](../sqlrf/CLUSTER_ID.md)

    CLUSTER_ID ( [ schema . ] model mining_attribute_clause )

#### [CLUSTER_ID (analytic)](../sqlrf/CLUSTER_ID.md)

    CLUSTER_ID ( INTO n mining_attribute_clause )
               OVER ( mining_analytic_clause )

#### [CLUSTER_PROBABILITY (aggregate)](../sqlrf/CLUSTER_PROBABILITY.md)

    CLUSTER_PROBABILITY ( [ schema . ] model [, cluster_id ] mining_attribute_clause )

#### [CLUSTER_PROBABILITY (analytic)](../sqlrf/CLUSTER_PROBABILITY.md)

    CLUSTER_PROBABILITY ( INTO n [, cluster_id] mining_attribute_clause )
                        OVER ( mining_analytic_clause )

#### [CLUSTER_SET (aggregate)](../sqlrf/CLUSTER_SET.md)

    CLUSTER_SET ( [ schema . ] model [ , topN [ , cutoff ] ] mining_attribute_clause )

#### [CLUSTER_SET (analytic)](../sqlrf/CLUSTER_SET.md)

    CLUSTER_SET ( INTO n [, topN [, cutoff]] mining_attribute_clause )
                OVER ( mining_analytic_clause )

#### [COALESCE](../sqlrf/COALESCE.md)

    COALESCE(expr [, expr ]...)

#### [COLLATION](../sqlrf/COLLATION.md)

    COLLATION(expr)

#### [COLLECT](../sqlrf/COLLECT.md)

    COLLECT( [ DISTINCT | UNIQUE ] column [ ORDER BY expr ] )

#### [COMPOSE](../sqlrf/COMPOSE.md)

    COMPOSE(char)

#### [CON_DBID_TO_ID](../sqlrf/CON_DBID_TO_ID.md)

    CON_DBID_TO_ID(container_dbid)

#### [CON_GUID_TO_ID](../sqlrf/CON_GUID_TO_ID.md)

    CON_GUID_TO_ID(container_guid)

#### [CON_ID_TO_CON_NAME](../sqlrf/con_id_to_con_name.md)

    CON_ID_TO_CON_NAME(container_guid)

#### [CON_ID_TO_DBID](../sqlrf/con_id_to_dbid.md)

    CON_ID_TO_DBID(container_guid)

#### [CON_NAME_TO_ID](../sqlrf/CON_NAME_TO_ID.md)

    CON_NAME_TO_ID(container_name)

#### [CON_UID_TO_ID](../sqlrf/CON_UID_TO_ID.md)

    CON_UID_TO_ID(container_uid)

#### [CONCAT](../sqlrf/CONCAT.md)

    CONCAT(char1, char2)

#### [CONVERT](../sqlrf/CONVERT.md)

    CONVERT(char, dest_char_set[, source_char_set ])

#### [CORR](../sqlrf/CORR.md)

    CORR(expr1, expr2) [ OVER (analytic_clause) ]

#### [CORR_K](../sqlrf/CORR_A.md), [CORR_S](../sqlrf/CORR_A.md)

    { CORR_K | CORR_S }
       (expr1, expr2
         [, { COEFFICIENT
            | ONE_SIDED_SIG
            | ONE_SIDED_SIG_POS
            | ONE_SIDED_SIG_NEG
            | TWO_SIDED_SIG
            }
         ]
       )

#### [COS](../sqlrf/COS.md)

    COS(n)

#### [COSH](../sqlrf/COSH.md)

    COSH(n)

#### [COUNT](../sqlrf/COUNT.md)

    COUNT({ * | [ DISTINCT | ALL ] expr }) [ OVER (analytic_clause) ]

#### [COVAR_POP](../sqlrf/COVAR_POP.md)

    COVAR_POP(expr1, expr2)
       [ OVER (analytic_clause) ]

#### [COVAR_SAMP](../sqlrf/COVAR_SAMP.md)

    COVAR_SAMP(expr1, expr2) [ OVER (analytic_clause) ]

#### [CUBE_TABLE](../sqlrf/CUBE_TABLE.md)

    CUBE_TABLE
    ( ' { schema.cube [ {HIERARCHY | HRR} dimension hierarchy ]...
        | schema.dimension [ {HIERARCHY | HRR} [dimension] hierarchy ]
        }
      '
    )

#### [CUME_DIST (aggregate)](../sqlrf/CUME_DIST.md)

    CUME_DIST(expr[,expr ]...) WITHIN GROUP
      (ORDER BY expr [ DESC | ASC ]
                     [ NULLS { FIRST | LAST } ]
                [, expr [ DESC | ASC ]
                        [ NULLS { FIRST | LAST } ]
                ]...
      )

#### [CUME_DIST (analytic)](../sqlrf/CUME_DIST.md)

    CUME_DIST() OVER ([ query_partition_clause ] order_by_clause)

#### [CURRENT_DATE](../sqlrf/CURRENT_DATE.md)

    CURRENT_DATE

#### [CURRENT_TIMESTAMP](../sqlrf/CURRENT_TIMESTAMP.md)

    CURRENT_TIMESTAMP [ (precision) ]

#### [CV](../sqlrf/CV.md)

    CV([ dimension_column ])

#### [DATAOBJ_TO_MAT_PARTITION](../sqlrf/DATAOBJ_TO_MAT_PARTITION.md)

    DATAOBJ_TO_MAT_PARTITION( table, partition_id )

#### [DATAOBJ_TO_PARTITION](../sqlrf/DATAOBJ_TO_PARTITION.md)

    DATAOBJ_TO_PARTITION( table, partition_id )

#### [DBTIMEZONE](../sqlrf/DBTIMEZONE.md)

    DBTIMEZONE

#### [DECODE](../sqlrf/DECODE.md)

    DECODE(expr, search, result [, search, result ]... [, default ])

#### [DECOMPOSE](../sqlrf/DECOMPOSE.md)

    DECOMPOSE( string [, { 'CANONICAL' | 'COMPATIBILITY' } ] )

#### [DENSE_RANK (aggregate)](../sqlrf/DENSE_RANK.md)

    DENSE_RANK(expr [, expr ]...) WITHIN GROUP
      (ORDER BY expr [ DESC | ASC ]
                     [ NULLS { FIRST | LAST } ]
                [,expr [ DESC | ASC ]
                       [ NULLS { FIRST | LAST } ]
                ]...
      )

#### [DENSE_RANK (analytic)](../sqlrf/DENSE_RANK.md)

    DENSE_RANK( ) OVER([ query_partition_clause ] order_by_clause)

#### [DEPTH](../sqlrf/DEPTH.md)

    DEPTH(correlation_integer)

#### [DEREF](../sqlrf/DEREF.md)

    DEREF(expr)

#### [DUMP](../sqlrf/DUMP.md)

    DUMP(expr[, return_fmt [, start_position [, length ] ]])

#### [EMPTY_BLOB](../sqlrf/EMPTY_BLOB-EMPTY_CLOB.md), [EMPTY_CLOB](../sqlrf/EMPTY_BLOB-EMPTY_CLOB.md)

    { EMPTY_BLOB | EMPTY_CLOB }( )

#### [EXISTSNODE](../sqlrf/EXISTSNODE.md)

    EXISTSNODE(XMLType_instance, XPath_string [, namespace_string ])

#### [EXP](../sqlrf/EXP.md)

    EXP(n)

#### [EXTRACT (datetime)](../sqlrf/EXTRACT-datetime.md)

    EXTRACT( { YEAR
             | MONTH
             | DAY
             | HOUR
             | MINUTE
             | SECOND
             | TIMEZONE_HOUR
             | TIMEZONE_MINUTE
             | TIMEZONE_REGION
             | TIMEZONE_ABBR
             }
             FROM { expr }
           )

#### [EXTRACT (XML)](../sqlrf/EXTRACT-XML.md)

    EXTRACT(XMLType_instance, XPath_string [, namespace_string ])

#### [EXTRACTVALUE](../sqlrf/EXTRACTVALUE.md)

    EXTRACTVALUE(XMLType_instance, XPath_string [, namespace_string ])

#### [FEATURE_COMPARE](../sqlrf/FEATURE_COMPARE.md)

    FEATURE_COMPARE ( [ schema . ] model
      mining_attribute_clause AND mining_attribute_clause )

#### [FEATURE_DETAILS (aggregate)](../sqlrf/FEATURE_DETAILS.md)

    FEATURE_DETAILS ( [ schema . ] model
                      [ , feature_id [ , topN ] ] [ DESC | ASC | ABS ]
                      mining_attribute_clause )

#### [FEATURE_DETAILS (analytic)](../sqlrf/FEATURE_DETAILS.md)

    FEATURE_DETAILS ( INTO n
                      [ , feature_id [ , topN ] ] [ DESC | ASC | ABS ]
                      mining_attribute_clause )
                    OVER ( mining_analytic_clause )

#### [FEATURE_ID (aggregate)](../sqlrf/FEATURE_ID.md)

    FEATURE_ID( [ schema . ] model mining_attribute_clause )

#### [FEATURE_ID (analytic)](../sqlrf/FEATURE_ID.md)

    FEATURE_ID ( INTO n mining_attribute_clause )
               OVER ( mining_analytic_clause )

#### [FEATURE_SET (aggregate)](../sqlrf/FEATURE_SET.md)

    FEATURE_SET ( [ schema . ] model [, topN [, cutoff ]] mining_attribute_clause )

#### [FEATURE_SET (analytic)](../sqlrf/FEATURE_SET.md)

    FEATURE_SET ( INTO n [, topN [, cutoff ] ] mining_attribute_clause )
                OVER ( mining_analytic_clause )

#### [FEATURE_VALUE (aggregate)](../sqlrf/FEATURE_VALUE.md)

    FEATURE_VALUE ( [ schema . ] model [, feature_id ] mining_attribute_clause )

#### [FEATURE_VALUE (analytic)](../sqlrf/FEATURE_VALUE.md)

    FEATURE_VALUE ( INTO n [ , feature_id ] mining_attribute_clause )
                  OVER ( mining_analytic_clause )

#### [FIRST](../sqlrf/FIRST.md)

    aggregate_function
       KEEP
       (DENSE_RANK FIRST ORDER BY
        expr [ DESC | ASC ]
             [ NULLS { FIRST | LAST } ]
        [, expr [ DESC | ASC ]
                [ NULLS { FIRST | LAST } ]
        ]...
       )
       [ OVER ( [query_partition_clause] ) ]

#### [FIRST_VALUE](../sqlrf/FIRST_VALUE.md)

    FIRST_VALUE
      { (expr) [ {RESPECT | IGNORE} NULLS ]
      | (expr [ {RESPECT | IGNORE} NULLS ])
      }
      OVER (analytic_clause)

#### [FLOOR](../sqlrf/FLOOR.md)

    FLOOR(n)

#### [FROM_TZ](../sqlrf/FROM_TZ.md)

    FROM_TZ (timestamp_value, time_zone_value)

#### [GREATEST](../sqlrf/GREATEST.md)

    GREATEST(expr [, expr ]...)

#### [GROUP_ID](../sqlrf/GROUP_ID.md)

    GROUP_ID( )

#### [GROUPING](../sqlrf/GROUPING.md)

    GROUPING(expr)

#### [GROUPING_ID](../sqlrf/GROUPING_ID.md)

    GROUPING_ID(expr [, expr ]...)

#### [HEXTORAW](../sqlrf/HEXTORAW.md)

    HEXTORAW(char)

#### [INITCAP](../sqlrf/INITCAP.md)

    INITCAP(char)

#### [INSTR](../sqlrf/INSTR.md)

    { INSTR
    | INSTRB
    | INSTRC
    | INSTR2
    | INSTR4
    }
    (string , substring [, position [, occurrence ] ])

#### [ITERATION_NUMBER](../sqlrf/ITERATION_NUMBER.md)

    ITERATION_NUMBER

#### [JSON_ARRAY](../sqlrf/JSON_ARRAY.md)

    JSON_ARRAY   ( JSON_ARRAY_content ) | JSON [ JSON_ARRAY_content ]

#### [JSON_ARRAYAGG](../sqlrf/JSON_ARRAYAGG.md)

    JSON_ARRAYAGG
      ( expr [ FORMAT JSON ] [ order_by_clause ]
        [ JSON_on_null_clause ] [ JSON_agg_returning_clause ]
        [ STRICT ] )

#### [JSON_DATAGUIDE](../sqlrf/JSON_DATAGUIDE.md)

    JSON_DATAGUIDE (expr [ , format [ , flag ] ] )

#### [JSON_MERGEPATCH](../sqlrf/JSON_MERGEPATCH.md)

    JSON_MERGEPATCH
       ( target_expr , patch_expr [ returning_clause ] [ PRETTY ] [ ASCII ]
         [ TRUNCATE ] [ on_error_clause ] )

#### [JSON_OBJECT](../sqlrf/JSON_OBJECT.md)

    JSON_OBJECT ( JSON_OBJECT_content ) JSON | { JSON_OBJECT_content }

#### [JSON_OBJECTAGG](../sqlrf/JSON_OBJECTAGG.md)

    JSON_OBJECTAGG
      ( [ KEY ] key_expr VALUE val_expr [ FORMAT JSON ]
        [ JSON_on_null_clause ] [ JSON_agg_returning_clause ]
        [ STRICT ] [ WITH UNIQUE KEYS ]  )

#### [JSON_QUERY](../sqlrf/JSON_QUERY.md)

    JSON_QUERY
      ( expr [ FORMAT JSON ], JSON_basic_path_expression
        [ JSON_query_returning_clause ] [ JSON_query_wrapper_clause ]
        [ JSON_query_on_error_clause ] [ JSON_query_on_empty_clause ]
      )

#### [JSON_SERIALIZE](../sqlrf/JSON_SERIALIZE.md)

    JSON_SERIALIZE
    (  expr [ JSON_returning_clause ] [ PRETTY ] [ASCII ] [ TRUNCATE ]
       [ { NULL | ERROR | ( EMPTY {ARRAY | OBJECT} ) } ON ERROR ]
    )

#### [JSON_TABLE](../sqlrf/JSON_TABLE.md)

    JSON_TABLE
      ( expr [ FORMAT JSON ] [ , JSON_basic_path_expression ]
        [ JSON_table_on_error_clause ] [ JSON_table_on_empty_clause ]
        JSON_columns_clause )

#### [JSON_VALUE](../sqlrf/JSON_VALUE.md)

    JSON_VALUE
      ( expr [ FORMAT JSON ] , [ JSON_basic_path_expression ]
        [ JSON_value_returning_clause ] [ JSON_value_on_error_clause ]
        [ JSON_value_on_empty_clause ] [ JSON_value_on_mismatch_clause ]
      )

#### [JSON_TRANSFORM](../sqlrf/json_transform.md)

    JSON_TRANSFORM
      ( input_expr , operation [ , operation ]... [ JSON_TRANSFORM_returning_clause ]
      [ JSON_passing_clause ] )


#### [LAG](../sqlrf/LAG.md)

    LAG
      { ( value_expr [, offset [, default]]) [ { RESPECT | IGNORE } NULLS ]
      | ( value_expr [ { RESPECT | IGNORE } NULLS ] [, offset [, default]] )
      }
      OVER ([ query_partition_clause ] order_by_clause)

#### [LAST](../sqlrf/LAST.md)

    aggregate_function KEEP
      (DENSE_RANK LAST ORDER BY
        expr [ DESC | ASC ]
             [ NULLS { FIRST | LAST } ]
        [, expr [ DESC | ASC ]
                [ NULLS { FIRST | LAST } ]
        ]...
      )
      [ OVER ( [query_partition_clause] ) ]

#### [LAST_DAY](../sqlrf/LAST_DAY.md)

    LAST_DAY(date)

#### [LAST_VALUE](../sqlrf/LAST_VALUE.md)

    LAST_VALUE
      { (expr) [ { RESPECT | IGNORE } NULLS ]
      | (expr [ { RESPECT | IGNORE } NULLS ])
      OVER (analytic_clause)

#### [LEAD](../sqlrf/LEAD.md)

    LEAD
      { ( value_expr [, offset [, default]] ) [ { RESPECT | IGNORE } NULLS ]
      | ( value_expr [ { RESPECT | IGNORE } NULLS ] [, offset [, default]] )
      }
      OVER ([ query_partition_clause ] order_by_clause)

#### [LEAST](../sqlrf/LEAST.md)

    LEAST(expr [, expr ]...)

#### [LENGTH](../sqlrf/LENGTH.md)

    { LENGTH
    | LENGTHB
    | LENGTHC
    | LENGTH2
    | LENGTH4
    }
    (char)

#### [LISTAGG](../sqlrf/LISTAGG.md)

    LISTAGG( [ ALL | DISTINCT ] measure_expr
               [, 'delimiter'] [listagg_overflow_clause] )
               [ WITHIN GROUP  order_by_clause ]
               [OVER query_partition_clause]

#### [LN](../sqlrf/LN.md)

    LN(n)

#### [LNNVL](../sqlrf/LNNVL.md)

    LNNVL(condition)

#### [LOCALTIMESTAMP](../sqlrf/LOCALTIMESTAMP.md)

    LOCALTIMESTAMP [ (timestamp_precision) ]

#### [LOG](../sqlrf/LOG.md)

    LOG(n2, n1)

#### [LOWER](../sqlrf/LOWER.md)

    LOWER(char)

#### [LPAD](../sqlrf/LPAD.md)

    LPAD(expr1, n [, expr2 ])

#### [LTRIM](../sqlrf/LTRIM.md)

    LTRIM(char [, set ])

#### [MAKE_REF](../sqlrf/MAKE_REF.md)

    MAKE_REF({ table | view } , key [, key ]...)

#### [MAX](../sqlrf/MAX.md)

    MAX([ DISTINCT | ALL ] expr) [ OVER (analytic_clause) ]

#### [MEDIAN](../sqlrf/MEDIAN.md)

    MEDIAN(expr) [ OVER (query_partition_clause) ]

#### [MIN](../sqlrf/MIN.md)

    MIN([ DISTINCT | ALL ] expr) [ OVER (analytic_clause) ]

#### [MOD](../sqlrf/MOD.md)

    MOD(n2, n1)

#### [MONTHS_BETWEEN](../sqlrf/MONTHS_BETWEEN.md)

    MONTHS_BETWEEN(date1, date2)

#### [NANVL](../sqlrf/NANVL.md)

    NANVL(n2, n1)

#### [NCHR](../sqlrf/NCHR.md)

    NCHR(number)

#### [NEW_TIME](../sqlrf/NEW_TIME.md)

    NEW_TIME(date, timezone1, timezone2)

#### [NEXT_DAY](../sqlrf/NEXT_DAY.md)

    NEXT_DAY(date, char)

#### [NLS_CHARSET_DECL_LEN](../sqlrf/NLS_CHARSET_DECL_LEN.md)

    NLS_CHARSET_DECL_LEN(byte_count, char_set_id)

#### [NLS_CHARSET_ID](../sqlrf/NLS_CHARSET_ID.md)

    NLS_CHARSET_ID(string)

#### [NLS_CHARSET_NAME](../sqlrf/NLS_CHARSET_NAME.md)

    NLS_CHARSET_NAME(number)

#### [NLS_COLLATION_ID](../sqlrf/NLS_COLLATION_ID.md)

    NLS_COLLATION_ID(expr)

#### [NLS_COLLATION_NAME](../sqlrf/NLS_COLLATION_NAME.md)

    NLS_COLLATION_NAME(expr [, flag ])

#### [NLS_INITCAP](../sqlrf/NLS_INITCAP.md)

    NLS_INITCAP(char [, 'nlsparam' ])

#### [NLS_LOWER](../sqlrf/NLS_LOWER.md)

    NLS_LOWER(char [, 'nlsparam' ])

#### [NLS_UPPER](../sqlrf/NLS_UPPER.md)

    NLS_UPPER(char [, 'nlsparam' ])

#### [NLSSORT](../sqlrf/NLSSORT.md)

    NLSSORT(char [, 'nlsparam' ])

#### [NTH_VALUE](../sqlrf/NTH_VALUE.md)

    NTH_VALUE(measure_expr, n)
      [ FROM { FIRST | LAST } ][ { RESPECT | IGNORE } NULLS ]
      OVER (analytic_clause)

#### [NTILE](../sqlrf/NTILE.md)

    NTILE(expr) OVER ([ query_partition_clause ] order_by_clause)

#### [NULLIF](../sqlrf/NULLIF.md)

    NULLIF(expr1, expr2)

#### [NUMTODSINTERVAL](../sqlrf/NUMTODSINTERVAL.md)

    NUMTODSINTERVAL(n, 'interval_unit')

#### [NUMTOYMINTERVAL](../sqlrf/NUMTOYMINTERVAL.md)

    NUMTOYMINTERVAL(n, 'interval_unit')

#### [NVL](../sqlrf/NVL.md)

    NVL(expr1, expr2)

#### [NVL2](../sqlrf/NVL2.md)

    NVL2(expr1, expr2, expr3)

#### [ORA_DM_PARTITION_NAME](../sqlrf/ORA_DM_PARTITION_NAME.md)

    ORA_DM_PARTITION_NAME ( [ schema . ] model mining_attribute_clause )

#### [ORA_DST_AFFECTED](../sqlrf/ORA_DST_AFFECTED.md)

    ORA_DST_AFFECTED(datetime_expr)

#### [ORA_DST_CONVERT](../sqlrf/ORA_DST_CONVERT.md)

    ORA_DST_CONVERT(datetime_expr [, integer [, integer ]])

#### [ORA_DST_ERROR](../sqlrf/ORA_DST_ERROR.md)

    ORA_DST_ERROR(datetime_expr)

#### [ORA_HASH](../sqlrf/ORA_HASH.md)

    ORA_HASH(expr [, max_bucket [, seed_value ] ])

#### [ORA_INVOKING_USER](../sqlrf/ORA_INVOKING_USER.md)

    ORA_INVOKING_USER

#### [ORA_INVOKING_USERID](../sqlrf/ORA_INVOKING_USERID.md)

    ORA_INVOKING_USERID

#### [PATH](../sqlrf/PATH.md)

    PATH(correlation_integer)

#### [PERCENT_RANK (aggregate)](../sqlrf/PERCENT_RANK.md)

    PERCENT_RANK(expr [, expr ]...) WITHIN GROUP
      (ORDER BY
       expr [ DESC | ASC ]
            [NULLS { FIRST | LAST } ]
       [, expr [ DESC | ASC ]
               [NULLS { FIRST | LAST } ]
       ]...
      )

#### [PERCENT_RANK (analytic)](../sqlrf/PERCENT_RANK.md)

    PERCENT_RANK( )
       OVER ([ query_partition_clause ] order_by_clause)

#### [PERCENTILE_CONT](../sqlrf/PERCENTILE_CONT.md)

    PERCENTILE_CONT(expr) WITHIN GROUP
      (ORDER BY expr [ DESC | ASC ])
      [ OVER (query_partition_clause) ]

#### [PERCENTILE_DISC](../sqlrf/PERCENTILE_DISC.md)

    PERCENTILE_DISC(expr) WITHIN GROUP
      (ORDER BY expr [ DESC | ASC ])
      [ OVER (query_partition_clause) ]

#### [POWER](../sqlrf/POWER.md)

    POWER(n2, n1)

#### [POWERMULTISET](../sqlrf/POWERMULTISET.md)

    POWERMULTISET(expr)

#### [POWERMULTISET_BY_CARDINALITY](../sqlrf/POWERMULTISET_BY_CARDINALITY.md)

    POWERMULTISET_BY_CARDINALITY(expr, cardinality)

#### [PREDICTION (aggregate)](../sqlrf/index.md)

    PREDICTION ( [ grouping_hint ] [ schema . ] model
      [ cost_matrix_clause ] mining_attribute_clause )

#### [PREDICTION (analytic)](../sqlrf/index.md)

    PREDICTION ( ( OF ANOMALY | FOR expr ) [ cost_matrix_clause ] mining_attribute_clause )
               OVER ( mining_analytic_clause )

#### [PREDICTION_BOUNDS](../sqlrf/PREDICTION_BOUNDS.md)

    PREDICTION_BOUNDS ( [schema.] model [, confidence_level [, class_value]]
                        mining_attribute_clause )

#### [PREDICTION_COST (aggregate)](../sqlrf/PREDICTION_COST.md)

    PREDICTION_COST ( [ schema . ] model [ , class ] cost_matrix_clause mining_attribute_clause )

#### [PREDICTION_COST (analytic)](../sqlrf/PREDICTION_COST.md)

    PREDICTION_COST ( ( OF ANOMALY | FOR expr ) [ , class ]
                      cost_matrix_clause mining_attribute_clause )
                    OVER (mining_analytic_clause)

#### [PREDICTION_DETAILS (aggregate)](../sqlrf/PREDICTION_DETAILS.md)

    PREDICTION_DETAILS ( [ schema . ] model
                         [ , class_value [ , topN ] ] [ DESC | ASC | ABS ]
                         mining_attribute_clause )

#### [PREDICTION_DETAILS (analytic)](../sqlrf/PREDICTION_DETAILS.md)

    PREDICTION_DETAILS ( ( OF ANOMALY | FOR expr ) [ , class_value [ , topN ] ]
                         [ DESC | ASC | ABS ] mining_attribute_clause )
                       OVER ( mining_analytic_clause )

#### [PREDICTION_PROBABILITY (aggregate)](../sqlrf/PREDICTION_PROBABILITY.md)

    PREDICTION_PROBABILITY ( [ schema . ] model [ , class ] mining_attribute_clause )

#### [PREDICTION_PROBABILITY (analytic)](../sqlrf/PREDICTION_PROBABILITY.md)

    PREDICTION_PROBABILITY ( ( OF ANOMALY | FOR expr ) [ , class ]
                             mining_attribute_clause )
                           OVER (mining_analytic_clause )

#### [PREDICTION_SET (aggregate)](../sqlrf/PREDICTION_SET.md)

    PREDICTION_SET ( [ schema . ] model [ , bestN [ , cutoff ] ]
                     [ cost_matrix_clause ] mining_attribute_clause )

#### [PREDICTION_SET (analytic)](../sqlrf/PREDICTION_SET.md)

    PREDICTION_SET ( ( OF ANOMALY | FOR "expr" ) [ , bestN [ , cutoff ] ]
                     [ cost_matrix_clause ] mining_attribute_clause )
                   OVER ( mining_analytic_clause )

#### [PRESENTNNV](../sqlrf/PRESENTNNV.md)

    PRESENTNNV(cell_reference, expr1, expr2)

#### [PRESENTV](../sqlrf/PRESENTV.md)

    PRESENTV(cell_reference, expr1, expr2)

####

    PREVIOUS(cell_reference)

#### [RANK (aggregate)](../sqlrf/RANK.md)

    RANK(expr [, expr ]...) WITHIN GROUP
       (ORDER BY
        expr [ DESC | ASC ]
             [ NULLS { FIRST | LAST } ]
        [, expr [ DESC | ASC ]
                [ NULLS { FIRST | LAST } ]
        ]...
       )

#### [RANK (analytic)](../sqlrf/RANK.md)

    RANK( )
       OVER ([ query_partition_clause ] order_by_clause)

#### [RATIO_TO_REPORT](../sqlrf/RATIO_TO_REPORT.md)

    RATIO_TO_REPORT(expr)
       OVER ([ query_partition_clause ])

#### [RAWTOHEX](../sqlrf/RAWTOHEX.md)

    RAWTOHEX(raw)

#### [RAWTONHEX](../sqlrf/RAWTONHEX.md)

    RAWTONHEX(raw)

#### [REF](../sqlrf/REF.md)

    REF (correlation_variable)

#### [REFTOHEX](../sqlrf/REFTOHEX.md)

    REFTOHEX (expr)

#### [REGEXP_COUNT](../sqlrf/REGEXP_COUNT.md)

    REGEXP_COUNT (source_char, pattern [, position [, match_param]])

#### [REGEXP_INSTR](../sqlrf/REGEXP_INSTR.md)

    REGEXP_INSTR ( source_char, pattern
                   [, position
                      [, occurrence
                         [, return_opt
                            [, match_param
                               [, subexpr ]
                            ]
                         ]
                      ]
                   ]
                 )

#### [REGEXP_REPLACE](../sqlrf/REGEXP_REPLACE.md)

    REGEXP_REPLACE ( source_char, pattern
                     [, replace_string
                        [, position
                           [, occurrence
                              [, match_param ]
                           ]
                        ]
                     ]
                   )

#### [REGEXP_SUBSTR](../sqlrf/REGEXP_SUBSTR.md)

    REGEXP_SUBSTR ( source_char, pattern
                    [, position
                       [, occurrence
                          [, match_param
                             [, subexpr ]
                          ]
                       ]
                    ]
                  )

#### [REGR_AVGX](../sqlrf/REGR_-Linear-Regression-Functions.md), [REGR_AVGY](../sqlrf/REGR_-Linear-Regression-Functions.md), [REGR_COUNT](../sqlrf/REGR_-Linear-Regression-Functions.md), [REGR_INTERCEPT](../sqlrf/REGR_-Linear-Regression-Functions.md), [REGR_R2](../sqlrf/REGR_-Linear-Regression-Functions.md), [REGR_SLOPE](../sqlrf/REGR_-Linear-Regression-Functions.md), [REGR_SXX](../sqlrf/REGR_-Linear-Regression-Functions.md), [REGR_SXY](../sqlrf/REGR_-Linear-Regression-Functions.md), [REGR_SYY](../sqlrf/REGR_-Linear-Regression-Functions.md)

    { REGR_SLOPE
    | REGR_INTERCEPT
    | REGR_COUNT
    | REGR_R2
    | REGR_AVGX
    | REGR_AVGY
    | REGR_SXX
    | REGR_SYY
    | REGR_SXY
    }
    (expr1 , expr2)
    [ OVER (analytic_clause) ]

#### [REMAINDER](../sqlrf/REMAINDER.md)

    REMAINDER(n2, n1)

#### [REPLACE](../sqlrf/REPLACE.md)

    REPLACE(char, search_string
            [, replacement_string ]
           )

#### [ROUND (date)](../sqlrf/ROUND-date.md)

    ROUND(date [, fmt ])

#### [ROUND (number)](../sqlrf/ROUND-number.md)

    ROUND(n [, integer ])

#### [ROUND_TIES_TO_EVEN (number)](../sqlrf/ROUND_TIES_TO_EVEN-number.md)

    ROUND_TIES_TO_EVEN ( n [, integer ] )

#### [ROW_NUMBER](../sqlrf/ROW_NUMBER.md)

    ROW_NUMBER( )
       OVER ([ query_partition_clause ] order_by_clause)

#### [ROWIDTOCHAR](../sqlrf/ROWIDTOCHAR.md)

    ROWIDTOCHAR(rowid)

#### [ROWIDTONCHAR](../sqlrf/ROWIDTONCHAR.md)

    ROWIDTONCHAR(rowid)

#### [RPAD](../sqlrf/RPAD.md)

    RPAD(expr1 , n [, expr2 ])

#### [RTRIM](../sqlrf/RTRIM.md)

    RTRIM(char [, set ])

#### [SCN_TO_TIMESTAMP](../sqlrf/SCN_TO_TIMESTAMP.md)

    SCN_TO_TIMESTAMP(number)

#### [SESSIONTIMEZONE](../sqlrf/SESSIONTIMEZONE.md)

    SESSIONTIMEZONE

#### [SET](../sqlrf/SET.md)

    SET (nested_table)

#### [SIGN](../sqlrf/SIGN.md)

    SIGN(n)

#### [SIN](../sqlrf/SIN.md)

    SIN(n)

#### [SINH](../sqlrf/SINH.md)

    SINH(n)

#### [SOUNDEX](../sqlrf/SOUNDEX.md)

    SOUNDEX(char)

#### [SQRT](../sqlrf/SQRT.md)

    SQRT(n)

#### [STANDARD_HASH](../sqlrf/STANDARD_HASH.md)

    STANDARD_HASH(expr [, 'method' ])

#### [STATS_BINOMIAL_TEST](../sqlrf/STATS_BINOMIAL_TEST.md)

    STATS_BINOMIAL_TEST(expr1, expr2, p
                        [, { TWO_SIDED_PROB
                           | EXACT_PROB
                           | ONE_SIDED_PROB_OR_MORE
                           | ONE_SIDED_PROB_OR_LESS
                           }
                        ]
                       )

#### [STATS_CROSSTAB](../sqlrf/STATS_CROSSTAB.md)

    STATS_CROSSTAB(expr1, expr2
                   [, { CHISQ_OBS
                      | CHISQ_SIG
                      | CHISQ_DF
                      | PHI_COEFFICIENT
                      | CRAMERS_V
                      | CONT_COEFFICIENT
                      | COHENS_K
                      }
                   ]
                  )

#### [STATS_F_TEST](../sqlrf/STATS_F_TEST.md)

    STATS_F_TEST(expr1, expr2
                 [, { { STATISTIC
                      | DF_NUM
                      | DF_DEN
                      | ONE_SIDED_SIG
        } , expr3
                    | TWO_SIDED_SIG
                    }
                 ]
                )

#### [STATS_KS_TEST](../sqlrf/STATS_KS_TEST.md)

    STATS_KS_TEST(expr1, expr2
                  [, { STATISTIC | SIG } ]
                 )

#### [STATS_MODE](../sqlrf/STATS_MODE.md)

    STATS_MODE(expr)

#### [STATS_MW_TEST](../sqlrf/STATS_MW_TEST.md)

    STATS_MW_TEST(expr1, expr2
                  [, { STATISTIC
                     | U_STATISTIC
                     | ONE_SIDED_SIG , expr3
                     | TWO_SIDED_SIG
                     }
                  ]
                 )

#### [STATS_ONE_WAY_ANOVA](../sqlrf/STATS_ONE_WAY_ANOVA.md)

    STATS_ONE_WAY_ANOVA(expr1, expr2
                        [, { SUM_SQUARES_BETWEEN
                           | SUM_SQUARES_WITHIN
                           | DF_BETWEEN
                           | DF_WITHIN
                           | MEAN_SQUARES_BETWEEN
                           | MEAN_SQUARES_WITHIN
                           | F_RATIO
                           | SIG
                           }
                        ]
                       )

#### [STATS_T_TEST_INDEP](../sqlrf/STATS_T_TEST_.md), [STATS_T_TEST_INDEPU](../sqlrf/STATS_T_TEST_.md), [STATS_T_TEST_ONE](../sqlrf/STATS_T_TEST_.md), [STATS_T_TEST_PAIRED](../sqlrf/STATS_T_TEST_.md)

    {
      STATS_T_TEST_ONE ( expr1 [, expr2 ]
    |
      { { STATS_T_TEST_PAIRED
        | STATS_T_TEST_INDEP
        | STATS_T_TEST_INDEPU
        } ( expr1, expr2
      }
    }
    [, { { STATISTIC | ONE_SIDED_SIG } , expr3 | TWO_SIDED_SIG | DF } ] )

#### [STATS_WSR_TEST](../sqlrf/STATS_WSR_TEST.md)

    STATS_WSR_TEST(expr1, expr2
                   [, { STATISTIC
                      | ONE_SIDED_SIG
                      | TWO_SIDED_SIG
                      }
                   ]
                  )

#### [STDDEV](../sqlrf/STDDEV.md)

    STDDEV([ DISTINCT | ALL ] expr)
       [ OVER (analytic_clause) ]

#### [STDDEV_POP](../sqlrf/STDDEV_POP.md)

    STDDEV_POP(expr)
       [ OVER (analytic_clause) ]

#### [STDDEV_SAMP](../sqlrf/STDDEV_SAMP.md)

    STDDEV_SAMP(expr)
       [ OVER (analytic_clause) ]

#### [SUBSTR](../sqlrf/SUBSTR.md)

    { SUBSTR
    | SUBSTRB
    | SUBSTRC
    | SUBSTR2
    | SUBSTR4
    }
    (char, position [, substring_length ])

#### [SUM](../sqlrf/SUM.md)

    SUM([ DISTINCT | ALL ] expr)
       [ OVER (analytic_clause) ]

#### [SYS_CONNECT_BY_PATH](../sqlrf/SYS_CONNECT_BY_PATH.md)

    SYS_CONNECT_BY_PATH(column, char)

#### [SYS_CONTEXT](../sqlrf/SYS_CONTEXT.md)

    SYS_CONTEXT('namespace', 'parameter' [, length ])

#### [SYS_DBURIGEN](../sqlrf/SYS_DBURIGEN.md)

    SYS_DBURIGEN({ column | attribute }
                 [ rowid ]
                   [, { column | attribute }
                      [ rowid ]
                   ]...
                 [, 'text ( )' ]
                )

#### [SYS_EXTRACT_UTC](../sqlrf/SYS_EXTRACT_UTC.md)

    SYS_EXTRACT_UTC(datetime_with_timezone)

#### [SYS_GUID](../sqlrf/SYS_GUID.md)

    SYS_GUID( )

#### [SYS_OP_ZONE_ID](../sqlrf/SYS_OP_ZONE_ID.md)

    SYS_OP_ZONE_ID( [ [ schema. ] table. | t_alias. ] rowid [, scale ] )

#### [SYS_TYPEID](../sqlrf/SYS_TYPEID.md)

    SYS_TYPEID(object_type_value)

#### [SYS_XMLAGG](../sqlrf/SYS_XMLAGG.md)

    SYS_XMLAGG(expr [, fmt ])

#### [SYS_XMLGEN](../sqlrf/SYS_XMLGEN.md)

    SYS_XMLGEN(expr [, fmt ])

#### [SYSDATE](../sqlrf/SYSDATE.md)

    SYSDATE

#### [SYSTIMESTAMP](../sqlrf/SYSTIMESTAMP.md)

    SYSTIMESTAMP

#### [TAN](../sqlrf/TAN.md)

    TAN(n)

#### [TANH](../sqlrf/TANH.md)

    TANH(n)

#### [TIMESTAMP_TO_SCN](../sqlrf/TIMESTAMP_TO_SCN.md)

    TIMESTAMP_TO_SCN(timestamp)

#### [TO_APPROX_COUNT_DISTINCT](../sqlrf/index.md)

    TO_APPROX_COUNT_DISTINCT(detail)

#### [TO_APPROX_PERCENTILE](../sqlrf/index.md)

    TO_APPROX_PERCENTILE(detail, expr, 'datatype'
      [, { 'DESC' | 'ASC' | 'ERROR_RATE' | 'CONFIDENCE' } ])

#### [TO_BINARY_DOUBLE](../sqlrf/TO_BINARY_DOUBLE.md)

    TO_BINARY_DOUBLE(expr [ DEFAULT return_value ON CONVERSION ERROR ]
      [, fmt [, 'nlsparam' ] ])

#### [TO_BINARY_FLOAT](../sqlrf/TO_BINARY_FLOAT.md)

    TO_BINARY_FLOAT(expr [ DEFAULT return_value ON CONVERSION ERROR ]
      [, fmt [, 'nlsparam' ] ])

#### [TO_BLOB (bfile)](../sqlrf/TO_BLOB-bfile.md)

    TO_BLOB( bfile [, mime_type] )

#### [TO_BLOB (raw)](../sqlrf/TO_BLOB-raw.md)

    TO_BLOB( raw_value )

#### [TO_CHAR (bfile\|blob)](../sqlrf/TO_CHAR-bfile-blob.md)

    TO_CHAR( { bfile | blob } [, csid] )

#### [TO_CHAR (character)](../sqlrf/TO_CHAR-character.md)

    TO_CHAR(nchar | clob | nclob)

#### [TO_CHAR (datetime)](../sqlrf/TO_CHAR-datetime.md)

    TO_CHAR({ datetime | interval } [, fmt [, 'nlsparam' ] ])

#### [TO_CHAR (number)](../sqlrf/TO_CHAR-number.md)

    TO_CHAR(n [, fmt [, 'nlsparam' ] ])

#### [TO_CLOB (bfile\|blob)](../sqlrf/TO_CLOB-bfile-blob.md)

    TO_CLOB( { bfile | blob } [, csid] [, mime_type] )

#### [TO_CLOB (character)](../sqlrf/TO_CLOB-character.md)

    TO_CLOB(lob_column | char)

#### [TO_DATE](../sqlrf/TO_DATE.md)

    TO_DATE(char [ DEFAULT return_value ON CONVERSION ERROR ]
      [, fmt [, 'nlsparam' ] ])

#### [TO_DSINTERVAL](../sqlrf/TO_DSINTERVAL.md)

    TO_DSINTERVAL ( ' { sql_format | ds_iso_format } '
      [ DEFAULT return_value ON CONVERSION ERROR ] )

#### [TO_LOB](../sqlrf/TO_LOB.md)

    TO_LOB(long_column)

#### [TO_MULTI_BYTE](../sqlrf/TO_MULTI_BYTE.md)

    TO_MULTI_BYTE(char)

#### [TO_NCHAR (character)](../sqlrf/TO_NCHAR-character.md)

    TO_NCHAR({char | clob | nclob})

#### [TO_NCHAR (datetime)](../sqlrf/TO_NCHAR-datetime.md)

    TO_NCHAR({ datetime | interval }
             [, fmt [, 'nlsparam' ] ]
            )

#### [TO_NCHAR (number)](../sqlrf/TO_NCHAR-number.md)

    TO_NCHAR(n [, fmt [, 'nlsparam' ] ])

#### [TO_NCLOB](../sqlrf/TO_NCLOB.md)

    TO_NCLOB(lob_column | char)

#### [TO_NUMBER](../sqlrf/TO_NUMBER.md)

    TO_NUMBER(expr [ DEFAULT return_value ON CONVERSION ERROR ]
      [, fmt [, 'nlsparam' ] ])

#### [TO_SINGLE_BYTE](../sqlrf/TO_SINGLE_BYTE.md)

    TO_SINGLE_BYTE(char)

#### [TO_TIMESTAMP](../sqlrf/TO_TIMESTAMP.md)

    TO_TIMESTAMP(char [ DEFAULT return_value ON CONVERSION ERROR ]
      [, fmt [, 'nlsparam' ] ])

#### [TO_TIMESTAMP_TZ](../sqlrf/TO_TIMESTAMP_TZ.md)

    TO_TIMESTAMP_TZ(char [ DEFAULT return_value ON CONVERSION ERROR ]
      [, fmt [, 'nlsparam' ] ])

#### [TO_UTC_TIMESTAMP_TZ](../sqlrf/TO_UTC_TIMESTAMP_TZ.md)

    TO_UTC_TIMESTAMP_TZ ( varchar )
     )

#### [TO_YMINTERVAL](../sqlrf/TO_YMINTERVAL.md)

    TO_YMINTERVAL
      ( '  { [+|-] years - months
           | ym_iso_format
           } '
        [ DEFAULT return_value ON CONVERSION ERROR ]
      )

#### [TRANSLATE](../sqlrf/TRANSLATE.md)

    TRANSLATE(expr, from_string, to_string)

#### [TRANSLATE ... USING](../sqlrf/TRANSLATE-USING.md)

    TRANSLATE ( char USING
              { CHAR_CS | NCHAR_CS }
              )

#### [TREAT](../sqlrf/TREAT.md)

    TREAT(expr AS [ REF ] [ schema. ]type)

#### [TRIM](../sqlrf/TRIM.md)

    TRIM([ { { LEADING | TRAILING | BOTH }
             [ trim_character ]
           | trim_character
           }
           FROM
         ]
         trim_source
        )

#### [TRUNC (date)](../sqlrf/TRUNC-date.md)

    TRUNC(date [, fmt ])

#### [TRUNC (number)](../sqlrf/TRUNC-number.md)

    TRUNC(n1 [, n2 ])

#### [TZ_OFFSET](../sqlrf/TZ_OFFSET.md)

    TZ_OFFSET({ 'time_zone_name'
              | '{ + | - } hh : mi'
              | SESSIONTIMEZONE
              | DBTIMEZONE
              }
             )

#### [UID](../sqlrf/UID.md)

    UID

#### [UNISTR](../sqlrf/UNISTR.md)

    UNISTR( string )

#### [UPPER](../sqlrf/UPPER.md)

    UPPER(char)

#### [USER](../sqlrf/USER.md)

    USER

#### [user-defined function](../sqlrf/About-User-Defined-Functions.md)

    [ schema. ]
    { [ package. ]function | user_defined_operator }
    [ @ dblink. ]
    [ ( [ [ DISTINCT | ALL ] expr [, expr ]... ] ) ]

#### [USERENV](../sqlrf/USERENV.md)

    USERENV('parameter')

#### [VALIDATE_CONVERSION](../sqlrf/index.md)

    VALIDATE_CONVERSION(expr AS type_name
      [, fmt [, 'nlsparam' ] ])

#### [VALUE](../sqlrf/VALUE.md)

    VALUE(correlation_variable)

#### [VAR_POP](../sqlrf/VAR_POP.md)

    VAR_POP(expr) [ OVER (analytic_clause) ]

#### [VAR_SAMP](../sqlrf/VAR_SAMP.md)

    VAR_SAMP(expr) [ OVER (analytic_clause) ]

#### [VARIANCE](../sqlrf/VARIANCE.md)

    VARIANCE([ DISTINCT | ALL ] expr)
            [ OVER (analytic_clause) ]

#### [VSIZE](../sqlrf/VSIZE.md)

    VSIZE(expr)

#### [WIDTH_BUCKET](../sqlrf/WIDTH_BUCKET.md)

    WIDTH_BUCKET
       (expr, min_value, max_value, num_buckets)

#### [XMLAGG](../sqlrf/XMLAGG.md)

    XMLAGG(XMLType_instance [ order_by_clause ])

#### [XMLCAST](../sqlrf/XMLCAST.md)

    XMLCAST ( value_expression AS datatype )

#### [XMLCDATA](../sqlrf/XMLCDATA.md)

    XMLCDATA ( value_expr )

#### [XMLCOLATTVAL](../sqlrf/XMLCOLATTVAL.md)

    XMLCOLATTVAL
      (value_expr [ AS { c_alias  | EVALNAME value_expr } ]
        [, value_expr [ AS { c_alias  | EVALNAME value_expr } ]
          ]...
      )

#### [XMLCOMMENT](../sqlrf/XMLCOMMENT.md)

    XMLCOMMENT ( value_expr )

#### [XMLCONCAT](../sqlrf/XMLCONCAT.md)

    XMLCONCAT(XMLType_instance [, XMLType_instance ]...)

#### [XMLDIFF](../sqlrf/XMLDIFF.md)

    XMLDIFF ( XMLType_document, XMLType_document [ , integer, string ] )

#### [XMLELEMENT](../sqlrf/XMLELEMENT.md)

    XMLELEMENT ( [ ENTITYESCAPING | NOENTITYESCAPING ]
       { ( [ NAME ] identifier ) | ( EVALNAME value_expr ) }
       [ , XML_attributes_clause ]
       [ , value_expr [ [ AS ] c_alias ]]...

#### [XMLEXISTS](../sqlrf/XMLEXISTS.md)

    XMLEXISTS ( XQuery_string [ XML_passing_clause ] )

#### [XMLFOREST](../sqlrf/XMLFOREST.md)

    XMLFOREST
      ( value_expr [ AS { c_alias | EVALNAME value_expr } ]
        [, value_expr [ AS { c_alias | EVALNAME value_expr } ]
          ]...
      )

#### [XMLISVALID](../sqlrf/XMLISVALID.md)

    XMLISVALID ( XMLType_instance [, XMLSchema_URL [, element ]] )

#### [XMLPARSE](../sqlrf/XMLPARSE.md)

    XMLPARSE
      ({ DOCUMENT | CONTENT } value_expr [ WELLFORMED ]
      )

#### [XMLPATCH](../sqlrf/XMLPATCH.md)

    XMLPATCH ( XMLType_document, XMLType_document )

#### [XMLPI](../sqlrf/XMLPI.md)

    XMLPI
     ( { ( [ NAME ] identifier ) | ( EVALNAME value_expr ) }
         [ , value_expr ]
     )

#### [XMLQUERY](../sqlrf/XMLQUERY.md)

    XMLQUERY
     ( XQuery_string
       [ XML_passing_clause ]
       RETURNING CONTENT [NULL ON EMPTY]
     )

#### [XMLROOT](../sqlrf/XMLROOT.md)

    XMLROOT
      ( value_expr, VERSION
      { value_expr | NO VALUE }
      [, STANDALONE { YES | NO | NO VALUE } ]
      )

#### [XMLSEQUENCE](../sqlrf/XMLSEQUENCE.md)

    XMLSEQUENCE( XMLType_instance
               | sys_refcursor_instance [, fmt ]
               )

#### [XMLSERIALIZE](../sqlrf/XMLSERIALIZE.md)

    XMLSERIALIZE
      ( { DOCUMENT | CONTENT } value_expr [ AS datatype ]
        [ ENCODING xml_encoding_spec ]
        [ VERSION string_literal ]
        [ NO INDENT | { INDENT [SIZE = number] } ]
        [ { HIDE | SHOW } DEFAULTS ]
      )

#### [XMLTABLE](../sqlrf/XMLTABLE.md)

    XMLTABLE
     (
      [ XMLnamespaces_clause , ] XQuery_string XMLTABLE_options
     )

#### [XMLTRANSFORM](../sqlrf/XMLTRANSFORM.md)

    XMLTRANSFORM(XMLType_instance, { XMLType_instance
                                   | string
                                   }
                )
