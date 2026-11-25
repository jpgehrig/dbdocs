## 13  CTX_REPORT Package

This chapter describes how to use the `CTX_REPORT` package to create reports on indexing and querying. These reports can help you troubleshoot problems or fine-tune your applications.

This chapter contains the following topics:

- Description of Procedures in CTX_REPORT

- Using the Function Versions

- DESCRIBE_INDEX

- DESCRIBE_POLICY

- CREATE_INDEX_SCRIPT

- CREATE_POLICY_SCRIPT

- INDEX_SIZE

- INDEX_STATS

- QUERY_LOG_SUMMARY

- TOKEN_INFO

- TOKEN_TYPE

- VALIDATE_INDEX

**Note:**

The APIs in the `CTX_REPORT` package do not support identifiers that are prefixed with the schema or the owner name.

**See Also:**

[Oracle Text Application Developer's Guide](../ccapp/administering-oracle-text.md) for an overview of the `CTX_REPORT` package and how you can use the various procedures described in this chapter

### 13.1 Description of Procedures in CTX_REPORT

The `CTX_REPORT` package contains the following procedures:

| Name                 | Description                                                                                  |
|:---------------------|:---------------------------------------------------------------------------------------------|
| DESCRIBE_INDEX       | Creates a report describing the index.                                                       |
| DESCRIBE_POLICY      | Creates a report describing a policy.                                                        |
| CREATE_INDEX_SCRIPT  | Creates a SQL\*Plus script to duplicate the named index.                                     |
| CREATE_POLICY_SCRIPT | Creates a SQL\*Plus script to duplicate the named policy.                                    |
| INDEX_SIZE           | Creates a report to show the internal objects of an index, their tablespaces and used sizes. |
| INDEX_STATS          | Creates a report to show the various statistics of an index.                                 |
| QUERY_LOG_SUMMARY    | Creates a report showing query statistics                                                    |
| TOKEN_INFO           | Creates a report showing the information for a token, decoded.                               |
| TOKEN_TYPE           | Translates a name and returns a numeric token type.                                          |
| VALIDATE_INDEX       | Checks for index corruption and reports on problems found. Mainly used with Oracle Support.  |

### 13.2 Using the Function Versions

Some of the procedures in the `CTX_REPORT` package have function versions. You can call these functions as follows:

    select ctx_report.describe_index('MYINDEX') from dual;

In SQL\*Plus, to generate an output file to send to support, you can do:

    set long 64000
    set pages 0
    set heading off
    set feedback off
    spool outputfile
    select ctx_report.describe_index('MYINDEX') from dual;
    spool off

### 13.3 DESCRIBE_INDEX

Creates a report describing the index. This includes the settings of the index metadata, the indexing objects used, the settings of the attributes of the objects, and index partition descriptions, if any.

You can call this operation as a procedure with an `IN` `OUT` `CLOB` parameter or as a function that returns the report as a `CLOB`.

#### Syntax

    procedure CTX_REPORT.DESCRIBE_INDEX(
      index_name     IN VARCHAR2,
      report         IN OUT NOCOPY CLOB,
      report_format  IN VARCHAR2 DEFAULT FMT_TEXT
    );

    function CTX_REPORT.DESCRIBE_INDEX(
      index_name     IN VARCHAR2,
      report_format  IN VARCHAR2 DEFAULT FMT_TEXT
    ) return CLOB;

index_name
Specify the name of the index to describe.

report
Specify the `CLOB` locator to which to write the report.

If `report` is NULL, a session-duration temporary `CLOB` will be created and returned. It is the caller's responsibility to free this temporary `CLOB` as needed.

The `report` `CLOB` will be truncated before report is generated, so any existing contents will be overwritten by this call.

report_format
Specify whether the report should be generated as 'TEXT' or as 'XML'. TEXT is the default. You can also specify the values `CTX_REPORT.FMT_TEXT` or `CTX_REPORT.FMT_XML`.

#### Notes

`CTX_REPORT.DESCRIBE_INDEX` outputs `FILTER` `BY` and `ORDER` `BY` column information if the index is created with `FILTER` `BY` and/or `ORDER` `BY` clauses.

#### Related Topics

"[CREATE INDEX](oracle-text-SQL-statements-and-operators.md)"

"[ADD_SDATA_COLUMN](CTX_DDL-package.md)"

### 13.4 DESCRIBE_POLICY

Creates a report describing the policy. This includes the settings of the policy metadata, the indexing objects used, and the settings of the attributes of the objects.

You can call this operation as a procedure with an `IN` `OUT` `CLOB` parameter or as a function that returns the report as a `CLOB`.

#### Syntax

    procedure CTX_REPORT.DESCRIBE_POLICY(
      policy_name    IN VARCHAR2,
      report         IN OUT NOCOPY CLOB,
      report_format  IN VARCHAR2 DEFAULT FMT_TEXT
    );

    function CTX_REPORT.DESCRIBE_POLICY(
      policy_name    IN VARCHAR2,
      report_format  IN VARCHAR2 DEFAULT FMT_TEXT
    ) return CLOB;

report
Specify the `CLOB` locator to which to write the report.

If `report` is NULL, a session-duration temporary `CLOB` will be created and returned. It is the caller's responsibility to free this temporary `CLOB` as needed.

The `report` `CLOB` will be truncated before `report` is generated, so any existing contents will be overwritten by this call.

report_format
Specify whether the report should be generated as 'TEXT' or as 'XML'. TEXT is the default. You can also specify the values `CTX_REPORT.FMT_TEXT` or `CTX_REPORT.FMT_XML`.

policy_name
Specify the name of the policy to describe.

### 13.5 CREATE_INDEX_SCRIPT

Creates a SQL\*Plus script which will create a text index that duplicates the named text index.

The created script will include creation of preferences identical to those used in the named text index. However, the names of the preferences will be different.

You can call this operation as a procedure with an `IN` `OUT` `CLOB` parameter or as a function that returns the report as a `CLOB`.

#### Syntax

    procedure CTX_REPORT.CREATE_INDEX_SCRIPT(
      index_name      in varchar2,
      report          in out nocopy clob,
      prefname_prefix in varchar2 default null
    );

    function CTX_REPORT.CREATE_INDEX_SCRIPT(
      index_name      in varchar2,
      prefname_prefix in varchar2 default null
    ) return clob;

index_name
Specify the name of the index.

report
Specify the `CLOB` locator to which to write the script.

If `report` is NULL, a session-duration temporary `CLOB` will be created and returned. It is the caller's responsibility to free this temporary `CLOB` as needed.

The `report` `CLOB` will be truncated before report is generated, so any existing contents will be overwritten by this call.

prefname_prefix
Specify optional prefix to use for preference names.

If `prefname_prefix` is omitted or NULL, index name will be used. The `prefname_prefix` follows index length restrictions.

#### Notes

`CTX_REPORT.CREATE_INDEX_SCRIPT` will also generate necessary `FILTER` `BY` and `ORDER` `BY` clauses for `CREATE` `INDEX` statements.

#### Related Topics

"[CREATE INDEX](oracle-text-SQL-statements-and-operators.md)"

### 13.6 CREATE_POLICY_SCRIPT

Creates a SQL\*Plus script which will create a text policy that duplicates the named text policy.

The created script will include creation of preferences identical to those used in the named text policy.

You can call this operation as a procedure with an `IN` `OUT` `CLOB` parameter or as a function that returns the report as a `CLOB`.

#### Syntax

    procedure CTX_REPORT.CREATE_POLICY_SCRIPT(
      policy_name      in varchar2,
      report           in out nocopy clob,
      prefname_prefix  in varchar2 default null
    );

    function CTX_REPORT.CREATE_POLICY_SCRIPT(
      policy_name      in varchar2,
      prefname_prefix  in varchar2 default null
    ) return clob;

policy_name
Specify the name of the policy.

report
Specify the locator to which to write the script.

If `report` is NULL, a session-duration temporary `CLOB` will be created and returned. It is the caller's responsibility to free this temporary `CLOB` as needed.

The `report` `CLOB` will be truncated before report is generated, so any existing contents will be overwritten by this call.

prefname_prefix
Specify the optional prefix to use for preference names. If `prefname_prefix` is omitted or NULL, policy name will be used. `prefname_prefix` follows policy length restrictions.

### 13.7 INDEX_SIZE

Creates a report showing the internal objects of the text index or text index partition, and their tablespaces, allocated, and used sizes.

You can call this operation as a procedure with an `IN` `OUT` `CLOB` parameter, or as a function that returns the report as a `CLOB`.

#### Syntax

    procedure CTX_REPORT.INDEX_SIZE(
      index_name     IN VARCHAR2,
      report         IN OUT NOCOPY CLOB,
      part_name      IN VARCHAR2 DEFAULT NULL,
      report_format  IN VARCHAR2 DEFAULT FMT_TEXT
    );

    function CTX_REPORT.INDEX_SIZE(
      index_name     IN VARCHAR2,
      part_name      IN VARCHAR2 DEFAULT NULL,
      report_format  IN VARCHAR2 DEFAULT FMT_TEXT
    ) return clob;

index_name
Specify the name of the index to describe.

report
Specify the `CLOB` locator to which to write the report.

If `report` is NULL, a session-duration temporary `CLOB` will be created and returned. It is the caller's responsibility to free this temporary `CLOB` as needed.

The `report` `CLOB` will be truncated before report is generated, so any existing contents will be overwritten by this call

part_name
Specify the name of the index partition (optional). If `part_name` is NULL, and the index is a local partitioned text index, then all objects of all partitions will be displayed. If `part_name` is provided, then only the objects of a particular partition will be displayed.

report_format
Specify whether the report should be generated as 'TEXT' or as 'XML'. TEXT is the default. You can also specify the values `CTX_REPORT`.`FMT_TEXT` or `CTX_REPORT`.`FMT_XML`.

#### Notes

`CTX_REPORT.INDEX_SIZE` will also output information on dr\$indexname\$S table.

#### Related Topics

"[CREATE INDEX](oracle-text-SQL-statements-and-operators.md)"

[Table 2-40](oracle-text-indexing-elements.md)

### 13.8 INDEX_STATS

Creates a report showing various calculated statistics about the text index.

This procedure fully scans the text index tables, so it may take a long time to run for large indexes.

#### Syntax

    procedure ctx_report.index_stats(
      index_name     IN VARCHAR2,
      report         IN OUT NOCOPY CLOB,
      part_name      IN VARCHAR2 DEFAULT NULL,
      frag_stats     IN BOOLEAN DEFAULT TRUE,
      list_size      IN NUMBER DEFAULT 100,
      report_format  IN VARCHAR2 DEFAULT FMT_TEXT,
      stat_type      IN VARCHAR2 DEFAULT NULL
    );

index_name
Specify the name of the index to describe. This must be a `CONTEXT` index.

report
Specify the `CLOB` locator to which to write the report. If report is NULL, a session-duration temporary `CLOB` will be created and returned. It is the caller's responsibility to free this temporary `CLOB` as needed.

The report `CLOB` will be truncated before report is generated, so any existing contents will be overwritten by this call.

part_name
Specify the name of the index partition. If the index is a local partitioned index, then `part_name` must be provided. `INDEX_STATS` will calculate the statistics for that index partition.

frag_stats
Specify TRUE to calculate fragmentation statistics. If `frag_stats` is FALSE, the report will not show any statistics relating to size of index data. However, the operation should take less time and resources to calculate the token statistics.

list_size
Specify the number of elements in each compiled list. `list_size` has a maximum value of 1000.

report_format
Specify whether the report should be generated as 'TEXT' or as 'XML'. TEXT is the default. You can also specify the values `CTX_REPORT`.`FMT_TEXT` or `CTX_REPORT`.`FMT_XML`.

stat_type
Specify the estimated statistics to output. If this parameter is set, then `frag_stats` is ignored. The possible values are:

| Statistics Type          | Description                                                                                                                                                             |
|:-------------------------|:------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `EST_FRAG_STATS`         | Get the estimated fragmentation stats for the index. When this type is given, `list_size` is ignored.                                                                   |
| `EST_FREQUENT_TOKENS`    | Get the estimated frequently queried tokens for the index. You can give a value of up to 100 for `list_size`.                                                           |
| `EST_TOKENS_TO_OPTIMIZE` | Show best tokens to optimize, based on frequency of querying and fragmentation. You can give a value of up to 100 for `list_size`.                                      |
| `EST_SLOWEST_QUERIES`    | Show slowest running queries for the index. You can give a value of up to 100 for `list_size`.<br>Note: `EST_SLOWEST_QUERIES` is not supported for a JSON search index. |

**Note:**

The estimated statistics for `stat_type` is only available if `query_stats` is enabled and the following privileges must be granted to the user running the report:

    grant select, insert, delete, update on ctxsys.dr$slowqrys to <user>;

    grant select, insert, delete, update on ctxsys.dr$freqtoks to <user>;

#### Example for CTX_REPORT.INDEX_STATS

    create table output (result CLOB);

      declare
        x clob := null;
      begin
        ctx_report.index_stats('tdrbprx21',x);
        insert into output values (x);
        commit;
        dbms_lob.freetemporary(x);
      end;
      /

    set long 32000
    set head off
    set pagesize 10000
    select * from output;

The following sample output is for `INDEX_STATS` on a context index. This report has been truncated for clarity. It shows some of the token statistics and all of the fragmentation statistics.

The fragmentation statistics are at the end of the report. It tells you optimal row fragmentation, an estimated amount of garbage data in the index, and a list of the most fragmented tokens. Running `CTX_DDL.OPTIMIZE_INDEX` cleans up the index.

    =================================================================
                  STATISTICS FOR "DR_TEST"."TDRBPRX21"
    =================================================================

    indexed documents:                                          53
    allocated docids:                                           68
    $I rows:                                                16,259

    -----------------------------------------------------------------
                            TOKEN STATISTICS
    -----------------------------------------------------------------

    unique tokens:                                          13,445
    average $I rows for each token:                           1.21
    tokens with most $I rows:
      telecommunications industry (THEME)                        6
      science and technology (THEME)                             6
      EMAIL (FIELD SECTION "SOURCE")                             6
      DEC (FIELD SECTION "TIMESTAMP")                            6
      electronic mail (THEME)                                    6
      computer networking (THEME)                                6
      communications (THEME)                                     6
      95 (FIELD SECTION "TIMESTAMP")                             6
      15 (FIELD SECTION "TIMESTAMP")                             6
      HEADLINE (ZONE SECTION)                                    6

    average size for each token:                                 8
    tokens with largest size:
      T (NORMAL)                                               405
      SAID (NORMAL)                                            313
      HEADLINE (ZONE SECTION)                                  272
      NEW (NORMAL)                                             267
      I (NORMAL)                                               230
      MILLION (PREFIX)                                         222
      D (NORMAL)                                               219
      MILLION (NORMAL)                                         215
      U (NORMAL)                                               192
      DEC (FIELD SECTION "TIMESTAMP")                          186

    average frequency for each token:                         2.00
    most frequent tokens:
      HEADLINE (ZONE SECTION)                                   68
      DEC (FIELD SECTION "TIMESTAMP")                           62
      95 (FIELD SECTION "TIMESTAMP")                            62
      15 (FIELD SECTION "TIMESTAMP")                            62
      T (NORMAL)                                                61
      D (NORMAL)                                                59
      881115 (THEME)                                            58
      881115 (NORMAL)                                           58
      I (NORMAL)                                                55
      geography (THEME)                                         52

    token statistics by type:
      token type:                                           NORMAL
        unique tokens:                                       6,344
        total rows:                                          7,631
        average rows:                                         1.20
        total size:                              67,445 (65.86 KB)
        average size:                                           11
        average frequency:                                    2.33
        most frequent tokens:
          T                                                     61
          D                                                     59
          881115                                                58
          I                                                     55
          SAID                                                  45
          C                                                     43
          NEW                                                   36
          MILLION                                               32
          FIRST                                                 28
          COMPANY                                               27

      token type:                                            THEME
        unique tokens:                                       4,563
        total rows:                                          5,523
        average rows:                                         1.21
        total size:                              21,930 (21.42 KB)
        average size:                                            5
        average frequency:                                    2.40
        most frequent tokens:
          881115                                                58
          political geography                                   52
          geography                                             52
          United States                                         51
          business and economics                                50
          abstract ideas and concepts                           48
          North America                                         48
          science and technology                                46
          NKS                                                   34
          nulls                                                 34

The fragmentation portion of this report is as follows:

    -----------------------------------------------------------------
                        FRAGMENTATION STATISTICS
    -----------------------------------------------------------------

    total size of $I data:                     116,772 (114.04 KB)

    $I rows:                                                16,259
    estimated $I rows if optimal:                           13,445
    estimated row fragmentation:                              17 %

    garbage docids:                                             15
    estimated garbage size:                      21,379 (20.88 KB)

    most fragmented tokens:
      telecommunications industry (THEME)                     83 %
      science and technology (THEME)                          83 %
      EMAIL (FIELD SECTION "SOURCE")                          83 %
      DEC (FIELD SECTION "TIMESTAMP")                         83 %
      electronic mail (THEME)                                 83 %
      computer networking (THEME)                             83 %
      communications (THEME)                                  83 %
      95 (FIELD SECTION "TIMESTAMP")                          83 %
      HEADLINE (ZONE SECTION)                                 83 %
      15 (FIELD SECTION "TIMESTAMP")                          83 %

#### Examples for CTX_REPORT.INDEX_STATS with STAT_TYPE

The following sample output is for `EST_FRAG_STATS` statistics type:

    var report clob;

        begin
            dbms_lob.createtemporary(:report, true);
            ctx_report.index_stats(
            index_name     => 'tdrbps.idx',
            report         => :report,
            report_format  => 'XML',
            stat_type => 'EST_FRAG_STATS'
            );
        end;
        /

    select :report from dual;

    :REPORT
    ------------------------------------------------------------------------------

    <CTXREPORT>
    <INDEX_STATS>
    <STAT_INDEX_NAME>"TDRBPS"."IDX"</STAT_INDEX_NAME>

    <STAT_INDEX_STATS>
    <STAT_STATISTIC NAME="Estimated Fragmentation Stats">50</STAT_STATISTIC>
    </STAT_INDEX_STATS>
    </INDEX_STATS>
    </CTXREPORT>

The following sample output is for `EST_FREQUENT_TOKENS` statistics type:

      begin
            dbms_lob.createtemporary(:report, true);
            ctx_report.index_stats(
            index_name     => 'tdrbps.idx',
            report         => :report,
            report_format  => 'XML',
            stat_type => 'EST_FREQUENT_TOKENS'
            );
        end;
        /

    select :report from dual;

    :REPORT
    ------------------------------------------------------------------------------

    <CTXREPORT>
    <INDEX_STATS>
    <STAT_INDEX_NAME>"TDRBPS"."IDX"</STAT_INDEX_NAME>

    <STAT_INDEX_STATS>
    <STAT_TOKEN_LIST NAME="Most Frequently Queried Tokens">
    <STAT_TOKEN>
    <STAT_TOKEN_TEXT>ORACLE</STAT_TOKEN_TEXT>
    <STAT_TOKEN_TYPE>0:TEXT</STAT_TOKEN_TYPE>
    <STAT_TOKEN_STATISTIC>2</STAT_TOKEN_STATISTIC>
    </STAT_TOKEN>
    <STAT_TOKEN>
    <STAT_TOKEN_TEXT>DATABASE</STAT_TOKEN_TEXT>
    <STAT_TOKEN_TYPE>0:TEXT</STAT_TOKEN_TYPE>
    <STAT_TOKEN_STATISTIC>1</STAT_TOKEN_STATISTIC>
    </STAT_TOKEN>
    </STAT_TOKEN_LIST>
    </STAT_INDEX_STATS>
    </INDEX_STATS>
    </CTXREPORT>

**Note:**

`<STAT_TOKEN_STATISTIC>` shows the number of times a particular token was queried.

The following sample output is for `EST_SLOWEST_QUERIES` statistics type:

      begin
            dbms_lob.createtemporary(:report, true);
            ctx_report.index_stats(
            index_name     => 'tdrbps.idx',
            report         => :report,
            report_format  => 'XML',
            stat_type => 'EST_SLOWEST_QUERIES'
            );
        end;
        /

    select :report from dual;

    :REPORT
    ------------------------------------------------------------------------------

    <CTXREPORT>
    <INDEX_STATS>
    <STAT_INDEX_NAME>"TDRBPS"."IDX"</STAT_INDEX_NAME>

    <STAT_INDEX_STATS>
    <STAT_QUERY_LIST NAME="Slowest Queries">
    <STAT_QUERY>
    <STAT_QUERY_FULL>select count(*) from tbl where
    contains(txt,'Oracle')>0</STAT_QUERY_FULL>
    <STAT_QUERY_TEXT_PART>Oracle</STAT_QUERY_TEXT_PART>
    <STAT_QUERY_TIME>114</STAT_QUERY_TIME>
    <STAT_QUERY_HASH>2992140927</STAT_QUERY_HASH>
    </STAT_QUERY>
    <STAT_QUERY>
    <STAT_QUERY_FULL>select count(*) from tbl where
    contains(txt,'ora%')>0</STAT_QUERY_FULL>
    <STAT_QUERY_TEXT_PART>ora%</STAT_QUERY_TEXT_PART>
    <STAT_QUERY_TIME>4</STAT_QUERY_TIME>
    <STAT_QUERY_HASH>2229259029</STAT_QUERY_HASH>
    </STAT_QUERY>
    <STAT_QUERY>
    <STAT_QUERY_FULL>select count(*) from tbl where
    contains(txt,'Database')>0</STAT_QUERY_FULL>
    <STAT_QUERY_TEXT_PART>Database</STAT_QUERY_TEXT_PART>
    <STAT_QUERY_TIME>2</STAT_QUERY_TIME>
    <STAT_QUERY_HASH>1111113040</STAT_QUERY_HASH>
    </STAT_QUERY>
    </STAT_QUERY_LIST>
    </STAT_INDEX_STATS>
    </INDEX_STATS>
    </CTXREPORT>

**Note:**

- `<STAT_QUERY_FULL>` contains the full query and `<STAT_QUERY_TEXT_PART>` contains the Oracle Text `CONTAINS` clause of the query.

- `<STAT_QUERY_TIME>` contains query response times and `<STAT_QUERY_HASH>` contains the hash values of the queries.

The following sample output is for `EST_TOKENS_TO_OPTIMIZE` statistics type:

      begin
            dbms_lob.createtemporary(:report, true);
            ctx_report.index_stats(
            index_name     => 'tdrbps.idx',
            report         => :report,
            report_format  => 'XML',
            stat_type => 'EST_TOKENS_TO_OPTIMIZE'
            );
        end;
        /

    select :report from dual;

    :REPORT
    ------------------------------------------------------------------------------

    <CTXREPORT>
    <INDEX_STATS>
    <STAT_INDEX_NAME>"TDRBPS"."IDX"</STAT_INDEX_NAME><STAT_INDEX_STATS>

    <STAT_TOKEN_LIST NAME="Best Tokens To Optimize">
    <STAT_TOKEN>
    <STAT_TOKEN_TEXT>ORACLE</STAT_TOKEN_TEXT>
    <STAT_TOKEN_TYPE>0:TEXT</STAT_TOKEN_TYPE>
    <STAT_TOKEN_STATISTIC>100</STAT_TOKEN_STATISTIC>
    </STAT_TOKEN>
    <STAT_TOKEN>
    <STAT_TOKEN_TEXT>DATABASE</STAT_TOKEN_TEXT>
    <STAT_TOKEN_TYPE>0:TEXT</STAT_TOKEN_TYPE>
    <STAT_TOKEN_STATISTIC>50</STAT_TOKEN_STATISTIC>
    </STAT_TOKEN>
    </STAT_TOKEN_LIST>
    </STAT_INDEX_STATS>
    </INDEX_STATS>
    </CTXREPORT>

**Note:**

`<STAT_TOKEN_STATISTIC>` indicates the fragmentation of a particular token.

#### Notes

These metadata are available only when `QUERY_STATS` is turned on for the index: estimated fragmentation stats, estimated frequently queried tokens, estimated most fragmented frequently queried token, and estimated slowest running queries for the specified index.

`CTX_REPORT.INDEX_STATS` will also output information on dr\$indexname\$S table, which is the section data, or `SDATA`, table.

**Related Topics**

- [ENABLE_QUERY_STATS](CTX_OUTPUT-package.md)
- [DISABLE_QUERY_STATS](CTX_OUTPUT-package.md)
- [CREATE INDEX](oracle-text-SQL-statements-and-operators.md)
- [BASIC_STORAGE Attributes](oracle-text-indexing-elements.md)

### 13.9 QUERY_LOG_SUMMARY

Obtain a report of logged queries.

`QUERY_LOG_SUMMARY` enables you to analyze queries you have logged. For example, suppose you have an application that searches a database of large animals, and your analysis of queries against it shows that users are continually searching for the word mouse; this analysis might induce you to rewrite your application so that a search for mouse redirects the user to a database for small animals instead of simply returning an unsuccessful search.

With query analysis, you can find out the following:

- Which queries were made

- Which queries were successful

- Which queries were unsuccessful

- How many times each query was made

You can combine these factors in various ways, such as determining the 50 most frequent unsuccessful queries made by your application.

Query logging is begun with `CTX_OUTPUT.START_QUERY_LOG` and terminated with `CTX_OUTPUT.END_QUERY_LOG`.

**Note:**

You must connect as `CTXSYS` to use `CTX_REPORT.QUERY_LOG_SUMMARY`.

**See Also:**

"[START_QUERY_LOG](CTX_OUTPUT-package.md)" and "[END_QUERY_LOG](CTX_OUTPUT-package.md)"

#### Syntax

    procedure CTX_REPORT.QUERY_LOG_SUMMARY(
       logfile       IN VARCHAR2,
       indexname     IN VARCHAR2 DEFAULT NULL,
       result_table  IN OUT NOCOPY QUERY_TABLE,
       row_num       IN NUMBER,
       most_freq     IN BOOLEAN DEFAULT TRUE,
       has_hit       IN BOOLEAN DEFAULT TRUE
    );

logfile
Specify the name of the logfile that contains the queries. Starting with Oracle Database 12c release 2 (12.2), this parameter is ignored as all the query logs are written to database trace files.

indexname
Specify the name of the context index for which you want the summary report. If you specify `NULL`, the procedure provides a summary report for all context indexes.

result_table
Specify the name of the in-memory table of type `TABLE OF RECORD` where the results of the `QUERY_LOG_SUMMARY` are to go. The default is the location specified by the system parameter `LOG_DIRECTORY`.

row_num
The number of rows of results from `QUERY_LOG_SUMMARY` to be reported into the table named by restab. For example, if this is number is 10, most_freq is TRUE, and has_hit is TRUE, then the procedure returns the 10 most frequent queries that were successful (that is, returned hits).

most_freq
Specify whether `QUERY_LOG_SUMMARY` should return the most frequent or least frequent queries. The default is most frequent queries. If most_freq is set to `FALSE`, the procedure returns the least successful queries.

has_hit
Specify whether `QUERY_LOG_SUMMARY` should return queries that are successful (that is, that generate hits) or unsuccessful queries. The default is to count successful queries; set has_hit to `FALSE` to return unsuccessful queries.

#### Example

The following example shows how a query log can be used.

First connect as `CTXSYS`. Then create and populate two tables, and then create an index for each:

    create table qlogtab1 (tk number primary key, text varchar2(2000));
    insert into qlogtab1 values(1, 'The Roman name for France was Gaul.');
    insert into qlogtab1 values(2, 'The Tour de France is held each summer.');
    insert into qlogtab1 values(3, 'Jacques Anatole Thibault took the pen name Anatole France.');
    create index idx_qlog1 on qlogtab1(text) indextype is ctxsys.context;
    create table qlogtab2 (tk number primary key, text varchar2(2000));
    insert into qlogtab2 values(1, 'The Great Wall of China is about 2400 kilometers long');
    insert into qlogtab2 values(2, 'Soccer dates back at least to 217 C.E.');
    insert into qlogtab2 values(3, 'The Corn Palace is a tourist attraction in South Dakota.');
    create index idx_qlog2 on qlogtab2(text) indextype is ctxsys.context;

Turn on query logging, creating a log called `query_log`:

    exec ctx_output.start_query_log('query.log');

Now make some queries (some of which will be unsuccessful):

    select text from qlogtab1 where contains(text, 'France',1)>0;
    select text from qlogtab1 where contains(text, 'cheese',1)>0;
    select text from qlogtab1 where contains(text, 'Text Wizard',1)>0;
    select text from qlogtab2 where contains(text, 'Corn Palace',1)>0;
    select text from qlogtab2 where contains(text, 'China',1)>0;
    select text from qlogtab1 where contains(text, 'Text Wizards',1)>0;
    select text from qlogtab2 where contains(text, 'South Dakota',1)>0;
    select text from qlogtab1 where contains(text, 'Text Wizard',1)>0;
    select text from qlogtab2 where contains(text, 'China',1)>0;
    select text from qlogtab1 where contains(text, 'Text Wizard',1)>0;
    select text from qlogtab2 where contains(text, 'company',1)>0;
    select text from qlogtab1 where contains(text, 'Text Wizard',1)>0;
    select text from qlogtab1 where contains(text, 'France',1)>0;
    select text from qlogtab1 where contains(text, 'database',1)>0;
    select text from qlogtab2 where contains(text, 'high-tech',1)>0;
    select text from qlogtab1 where contains(text, 'database',1)>0;
    select text from qlogtab1 where contains(text, 'France',1)>0;
    select text from qlogtab1 where contains(text, 'Japan',1)>0;
    select text from qlogtab1 where contains(text, 'Egypt',1)>0;
    select text from qlogtab1 where contains(text, 'Argentina',1)>0;
    select text from qlogtab1 where contains(text, 'Argentina',1)>0;
    select text from qlogtab1 where contains(text, 'Argentina',1)>0;
    select text from qlogtab1 where contains(text, 'Japan',1)>0;
    select text from qlogtab1 where contains(text, 'Egypt',1)>0;
    select text from qlogtab1 where contains(text, 'Air Shuttle',1)>0;
    select text from qlogtab1 where contains(text, 'Argentina',1)>0;

With the querying over, turn query logging off:

    exec ctx_output.end_query_log;

Use `QUERY_LOG_SUMMARY` to get query reports. In the first instance, you ask to see the three most frequent queries that return successfully. First declare the results table (`the_queries`).

    set serveroutput on;
    declare
       the_queries ctx_report.query_table;
    begin
       ctx_report.query_log_summary('query.log', null, the_queries,
                       row_num=>3, most_freq=>TRUE, has_hit=>TRUE);
       dbms_output.put_line('The 3 most frequent queries returning hits');
       dbms_output.put_line('number of times  query string');
       for i in 1..the_queries.count loop
         dbms_output.put_line(the_queries(i).times||'                '||the_queries(i).query);
       end loop;
    end;
    /

This returns the following:

    The 3 most frequent queries returning hits
    number of times  query string
    3                France
    2                China
    1                Corn Palace

Next, look for the three most frequent queries on `idx_qlog1` that were successful.

    declare
       the_queries ctx_report.query_table;
    begin
       ctx_report.query_log_summary('query.log', 'idx_qlog1', the_queries,
                       row_num=>3, most_freq=>TRUE, has_hit=>TRUE);
       dbms_output.put_line('The 3 most frequent queries returning hits for index idx_qlog1');
       dbms_output.put_line('number of times  query string');
       for i in 1..the_queries.count loop
         dbms_output.put_line(the_queries(i).times||'                '||the_queries(i).query);
       end loop;
    end;
    /

Because only the queries for France were successful, `ctx_report.query_log_summary` returns the following:

    The 3 most frequent queries returning hits for index idx_qlog1
    number of times  query string
    3                France

Lastly, ask to see the three least frequent queries that returned no hits (that is, queries that were unsuccessful and called infrequently). In this case, you are interested in queries on both context indexes, so you set the indexname parameter to NULL.

    declare
       the_queries ctx_report.query_table;
    begin
       ctx_report.query_log_summary('query.log', null, the_queries, row_num=>3,
                       most_freq=>FALSE, has_hit=>FALSE);
       dbms_output.put_line('The 3 least frequent queries returning no hit');
       dbms_output.put_line('number of times  query string');
       for i in 1..the_queries.count loop
         dbms_output.put_line(the_queries(i).times||'                '||the_queries(i).query);
       end loop;
    end;
    /

This returns the following results:

    The 3 least frequent queries returning no hit
    number of times  query string
    1                high-tech
    1                company
    1                cheese

Argentina and Japan do not make this list, because they are queried more than once, while Corn Palace does not make this list because it is successfully queried.

### 13.10 TOKEN_INFO

Creates a report showing the information for a token, decoded. This procedure will fully scan the info for a token, so it may take a long time to run for really large tokens.

You can call this operation as a procedure with an `IN` `OUT` `CLOB` parameter or as a function that returns the report as a `CLOB`.

#### Syntax

    procedure CTX_REPORT.TOKEN_INFO(
      index_name      IN VARCHAR2,
      report          IN OUT NOCOPY CLOB,
      token           IN VARCHAR2,
      token_type      IN NUMBER,
      part_name       IN VARCHAR2 DEFAULT NULL,
      raw_info        IN BOOLEAN  DEFAULT FALSE,
      decoded_info    IN BOOLEAN  DEFAULT TRUE,
      report_format   IN VARCHAR2 DEFAULT FMT_TEXT
    );

    function CTX_REPORT.TOKEN_INFO(
      index_name      IN VARCHAR2,
      token           IN VARCHAR2,
      token_type      IN NUMBER,
      part_name       IN VARCHAR2 DEFAULT NULL,
      raw_info        IN VARCHAR2 DEFAULT 'N',
      decoded_info    IN VARCHAR2 DEFAULT 'Y',
      report_format   IN VARCHAR2 DEFAULT FMT_TEXT
    ) return clob;

index_name
Specify the name of the index.

report
Specify the `CLOB` locator to which to write the report.

If report is NULL, a session-duration temporary `CLOB` will be created and returned. It is the caller's responsibility to free this temporary `CLOB` as needed.

The `report` `CLOB` will be truncated before report is generated, so any existing contents will be overwritten by this call token may be case-sensitive, depending on the passed-in token type.

token
Specify the token text.

token_type
Specify the token type. You can use a number returned by the TOKEN_TYPE function. `THEME`, `ZONE`, `ATTR`, `PATH`, and `PATH` `ATTR` tokens are case-sensitive.

Everything else gets passed through the lexer, so if the index's lexer is case-sensitive, the token input is case-sensitive.

part_name
Specify the name of the index partition.

If the index is a local partitioned index, then part_name must be provided. `TOKEN_INFO` will apply to just that index partition.

raw_info
Specify `TRUE` to include a hex dump of the index data. If raw_info is `TRUE`, the report will include a hex dump of the raw data in the `token_info` column.

decoded_info
Specify decode and include docid and offset data. If `decoded_info` is FALSE, `CTX_REPORT` will not attempt to decode the token information. This is useful when you just want a dump of data.

report_format
Specify whether the report should be generated as 'TEXT' or as 'XML'. TEXT is the default. You can also specify the values `CTX_REPORT.FMT_TEXT` or `CTX_REPORT.FMT_XML`.

### 13.11 TOKEN_TYPE

This is a helper function which translates an English name into a numeric token type.

This is suitable for use with `token_info`, or any other `CTX` API which takes in a `token_type`.

    function token_type(
      index_name in varchar2,
      type_name  in varchar2
    ) return number;

    TOKEN_TYPE_TEXT      constant number := 0;
    TOKEN_TYPE_THEME     constant number := 1;
    TOKEN_TYPE_ZONE_SEC  constant number := 2;
    TOKEN_TYPE_ORIG         constant number := 3,
    TOKEN_TYPE_ATTR_TEXT constant number := 4;
    TOKEN_TYPE_ATTR_SEC  constant number := 5;
    TOKEN_TYPE_PREFIX    constant number := 6;
    TOKEN_TYPE_PATH_SEC  constant number := 7;
    TOKEN_TYPE_PATH_ATTR constant number := 8;
    TOKEN_TYPE_STEM      constant number := 9;

index_name
Specify the name of the index.

type_name
Specify an English name for `token_type`. The following strings are legal input. All input is case-insensitive.

| Input                      | Meaning                                | Type Returned |
|:---------------------------|:---------------------------------------|:--------------|
| `TEXT`                     | Normal text token                      | 0             |
| `THEME`                    | Theme token                            | 1             |
| `ZONE SEC`                 | Zone token                             | 2             |
| `ATTR TEXT`                | Text that occurs in attribute          | 4             |
| `ATTR SEC`                 | Attribute section                      | 5             |
| `PREFIX`                   | Prefix token                           | 6             |
| `PATH SEC`                 | Path section                           | 7             |
| `PATH ATTR`                | Path attribute section                 | 8             |
| `STEM`                     | Stem form token                        | 9             |
| `FIELD ``<name>`` TEXT`    | Text token in field section `<name>`   | 16-79         |
| `SORTABLE SDATA`           | Sortable `SDATA` section               | 101           |
| `MDATA`                    | `MDATA` section                        | 400           |
| `FIELD ``<name>`` PREFIX`  | Prefix token in field section `<name>` | 616-916       |
| `FIELD ``<name>`` STEM`    | Stem token in field section `<name>`   | 916-979       |
| `NDATA ``<name>`           | `NDATA`-type token                     | 200-299       |
| `TOKEN_TYPE_ATTR_TXT_PFIX` | Attribute text prefix                  | 604           |
| `TOKEN_TYPE_ATTR_TXT_STEM` | Attribute text stem                    | 904           |

For `FIELD` types, the index metadata needs to be read, so if you are going to be calling this a lot for such things, you might want to consider caching the values in local variables rather than calling token_type over and over again.

The constant types (0 - 9) also have constants in this package defined.

#### Notes

To get token types for `MDATA` tokens, do not use `CTX_REPORT.TOKEN_TYPE`; use the [MDATA](oracle-text-CONTAINS-query-operators.md) operator instead. (See "[MDATA](oracle-text-CONTAINS-query-operators.md)".) The syntax to use is '`MDATA` secname'.

#### Example

    typenum := ctx_report.token_type('myindex', 'field author text');

### 13.12 VALIDATE_INDEX

Provides diagnostics if index corruption is believed to have occurred. `CTX_REPORT.VALIDATE_INDEX` checks an index (or a partition for a locally partitioned index) and reports whether or not any corruption has been detected. `VALIDATE_INDEX` only checks \$I rows that have `token_type` `0` and does not check other rows that contain information about sections, such as the `NDATA` section.

This procedure is primarily intended as a diagnostic tool to be used under the direction of Oracle Support.
