## 12  CTX_QUERY Package

This chapter describes the `CTX_QUERY` PL/SQL package you can use for generating query feedback, counting hits, and creating stored query expressions.

The `CTX_QUERY` package includes the following procedures and functions:

| Name                  | Description                                                                                                                                                 |
|:----------------------|:------------------------------------------------------------------------------------------------------------------------------------------------------------|
| BROWSE_WORDS          | Returns the words around a seed word in the index.                                                                                                          |
| COUNT_HITS            | Returns the number hits to a query.                                                                                                                         |
| EXPLAIN               | Generates query expression parse and expansion information.                                                                                                 |
| HFEEDBACK             | Generates hierarchical query feedback information (broader term, narrower term, and related term).                                                          |
| REMOVE_SQE            | Removes a specified stored query expression from the SQL tables.                                                                                            |
| RESULT_SET            | Executes a query and generates a result set.                                                                                                                |
| RESULT_SET_CLOB_QUERY | Executes a query and generates a result set based on a `CLOB` query parameter.                                                                              |
| RESULT_SET_DOCUMENT   | Holds the result set document after the CONTAINS query cursor is explicitly closed and if the query template has the \<ctx_result_set_descriptor\> element. |
| STORE_SQE             | Executes a query and stores the results in stored query expression tables.                                                                                  |

**Note:**

You can use this package only when your index type is `CONTEXT`. This package does not support the `CTXCAT` index type.

The APIs in the `CTX_QUERY` package do not support identifiers that are prefixed with the schema or the owner name.

### 12.1 BROWSE_WORDS

This procedure enables you to browse words in an Oracle Text index. Specify a seed word and `BROWSE_WORDS` returns the words around it in the index, and an approximate count of the number of documents that contain each word.

This feature is useful for refining queries. You can identify the following words:

- Unselective words (words that have low document count)

- Misspelled words in the document set

#### Syntax 1: To Store Results in Table

    ctx_query.browse_words(

    index_name  IN   VARCHAR2,
    seed        IN   VARCHAR2,
    restab      IN   VARCHAR2,
    browse_id   IN   NUMBER   DEFAULT 0,
    numwords    IN   NUMBER   DEFAULT 10,
    direction   IN   VARCHAR2 DEFAULT BROWSE_AROUND,
    part_name   IN   VARCHAR2 DEFAULT NULL

    );

#### Syntax 2: To Store Results in Memory

    ctx_query.browse_words(

    index_name  IN      VARCHAR2,
    seed        IN      VARCHAR2,
    resarr      IN OUT  BROWSE_TAB,
    numwords    IN      NUMBER   DEFAULT 10,
    direction   IN      VARCHAR2 DEFAULT BROWSE_AROUND,
    part_name   IN      VARCHAR2 DEFAULT NULL

    );

index
Specify the name of the index. You can specify `schema.name`. Must be a local index.

seed
Specify the seed word. This word is lexed before browse expansion. The word need not exist in the token table. `seed` must be a single word. Using multiple words as the seed will result in an error.

restab
Specify the name of the result table. You can enter `restab` as `schema.name`. The table must exist before you call this procedure, and you must have `INSERT` permissions on the table. This table must have the following schema.

| Column    | Datatype     |
|:----------|:-------------|
| browse_id | number       |
| word      | varchar2(64) |
| doc_count | number       |

Existing rows in `restab` are not deleted before `BROWSE_WORDS` is called.

resarr
Specify the name of the result array. `resarr` is of type `ctx_query.browse_tab`.

    type browse_rec is record (
       word varchar2(64),
       doc_count number
    );
    type browse_tab is table of browse_rec index by binary_integer;

browse_id
Specify a numeric identifier between 0 and 2<sup>32</sup>. The rows produced for this browse have a value of in the `browse_id` column in `restab`. When you do not specify `browse_id`, the default is 0.

numwords
Specify the number of words returned.

direction
Specify the direction for the browse. You can specify one of:

| value    | behavior                                                             |
|:---------|:---------------------------------------------------------------------|
| `BEFORE` | Browse seed word and words alphabetically before the seed.           |
| `AROUND` | Browse seed word and words alphabetically before and after the seed. |
| `AFTER`  | Browse seed word and words alphabetically after the seed.            |

Symbols `CTX_QUERY.BROWSE_BEFORE`, `CTX_QUERY.BROWSE_AROUND`, and `CTX_QUERY.BROWSE_AFTER` are defined for these literal values as well.

part_name
Specify the name of the index partition to browse.

#### Example

Browsing Words with Result Table

    begin
    ctx_query.browse_words('myindex','dog','myres',numwords=>5,direction=>'AROUND');
    end;

    select word, doc_count from myres order by word;

    WORD       DOC_COUNT
    --------   ----------
    CZAR       15
    DARLING    5
    DOC        73
    DUNK       100
    EAR        3

Browsing Words with Result Array

    set serveroutput on;
    declare
      resarr ctx_query.browse_tab;
    begin
    ctx_query.browse_words('myindex','dog',resarr,5,CTX_QUERY.BROWSE_AROUND);
    for i in 1..resarr.count loop
      dbms_output.put_line(resarr(i).word || ':' || resarr(i).doc_count);
    end loop;
    end;

### 12.2 COUNT_HITS

Returns the number of hits for the specified query. You can call `COUNT_HITS` in exact or estimate mode. Exact mode returns the exact number of hits for the query. Estimate mode returns an upper-bound estimate but runs faster than exact mode.

#### Syntax

Syntax 1

    exec CTX_QUERY.COUNT_HITS(
        index_name  IN VARCHAR2,
        text_query  IN VARCHAR2,
        exact       IN BOOLEAN  DEFAULT TRUE,
        part_name   IN VARCHAR2 DEFAULT NULL
    ) RETURN NUMBER;

Syntax 2

    exec CTX_QUERY.COUNT_HITS_CLOB_QUERY(
        index_name  IN VARCHAR2,
        text_query  IN CLOB,
        exact       IN BOOLEAN DEFAULT TRUE,
        part_name   IN VARCHAR2 DEFAULT NULL
    ) RETURN NUMBER;

index_name
Specify the index name.

text_query
Specify the query.

exact
Specify `TRUE` for an exact count. Specify `FALSE` for an upper-bound estimate.

Specifying `FALSE` returns a less accurate number but runs faster. Specifying `FALSE` might return a number which is too high if rows have been updated or deleted since the last `FULL` index optimize. Optimizing in full mode removes these false hits, and then `EXACT` set to `FALSE` will return the same number as `EXACT` set to `TRUE`.

part_name
Specify the name of the index partition to query.

#### Notes

If the query contains structured criteria, then you should use `SELECT COUNT(*)`.

If the index was created with the `TRANSACTIONAL` parameter, then `COUNT_HITS` will include pending rowids as well as those that have been synchronized.

### 12.3 EXPLAIN

Use `CTX_QUERY.EXPLAIN` to generate explain plan information for a query expression. The `EXPLAIN` plan provides a graphical representation of the parse tree for a Text query expression. This information is stored in a result table.

This procedure does not execute the query. Instead, this procedure can tell you how a query is expanded and parsed before you enter the query. This is especially useful for stem, wildcard, thesaurus, fuzzy, soundex, or about queries. Parse trees also show the following information:

- Order of execution (precedence of operators)

- `ABOUT` query normalization

- Query expression optimization

- Stop-word transformations

- Breakdown of composite-word tokens

Knowing how Oracle Text evaluates a query is useful for refining and debugging queries. You can also design your application so that it uses the explain plan information to help users write better queries.

#### Syntax

Syntax 1

    exec CTX_QUERY.EXPLAIN(

        index_name     IN VARCHAR2,
        text_query     IN VARCHAR2,
        explain_table  IN VARCHAR2,
        sharelevel     IN NUMBER DEFAULT 0,
        explain_id     IN VARCHAR2 DEFAULT NULL,
        part_name      IN VARCHAR2 DEFAULT NULL

    );

Syntax 2

    exec CTX_QUERY.EXPLAIN_CLOB_QUERY(
        index_name     IN VARCHAR2,
        text_query     IN CLOB,
        explain_table  IN VARCHAR2,
        sharelevel     IN NUMBER DEFAULT 0,
        explain_id     IN VARCHAR2 DEFAULT NULL,
        part_name      IN VARCHAR2 DEFAULT NULL
    );

index_name
Specify the name of the index to be queried.

text_query
Specify the query expression to be used as criteria for selecting rows.

When you include a wildcard, fuzzy, or soundex operator in `text_query`, this procedure looks at the index tables to determine the expansion.

Wildcard, fuzzy (?), and soundex (!) expression feedback does not account for lazy deletes as in regular queries.

explain_table
Specify the name of the table used to store representation of the parse tree for text_query. You must have at least `INSERT` and `DELETE` privileges on the table used to store the results from `EXPLAIN`.

**See Also:**

"[EXPLAIN Table](oracle-text-result-tables.md)" in [Oracle Text Result Tables](oracle-text-result-tables.md) for more information about the structure of the explain table.

sharelevel
Specify whether `explain_table` is shared by multiple `EXPLAIN` calls. Specify 0 for exclusive use and 1 for shared use. Default is 0 (single-use).

When you specify 0, the system automatically truncates the result table before the next call to `EXPLAIN`.

When you specify 1 for shared use, this procedure does not truncate the result table. Only results with the same `explain_id` are updated. When no results with the same `explain_id` exist, new results are added to the `EXPLAIN` table.

explain_id
Specify a name that identifies the explain results returned by an `EXPLAIN` procedure when more than one `EXPLAIN` call uses the same shared `EXPLAIN` table. Default is `NULL`.

part_name
Specify the name of the index partition to query.

#### Example

Creating the Explain Table

To create an explain table called `test_explain` for example, use the following SQL statement:

    create table test_explain(
             explain_id varchar2(30),
             id number,
             parent_id number,
             operation varchar2(30),
             options varchar2(30),
             object_name varchar2(255),
             position number,
             cardinality number);

Running CTX_QUERY.EXPLAIN

To obtain the expansion of a query expression such as comp% OR ?smith, use `CTX_QUERY.EXPLAIN` as follows:

    ctx_query.explain(
             index_name => 'newindex',
             text_query => 'comp% OR ?smith',
             explain_table => 'test_explain',
             sharelevel => 0,
             explain_id => 'Test');

Retrieving Data from Explain Table

To read the explain table, you can select the columns as follows:

    select explain_id, id, parent_id, operation, options, object_name, position
    from test_explain order by id;

The output is ordered by ID to simulate a hierarchical query:

    EXPLAIN_ID    ID PARENT_ID OPERATION    OPTIONS OBJECT_NAME POSITION
    ----------- ---- --------- ------------ ------- ----------- --------
    Test           1         0 OR           NULL    NULL          1
    Test           2         1 EQUIVALENCE  NULL    COMP%         1
    Test           3         2 WORD         NULL    COMPTROLLER   1
    Test           4         2 WORD         NULL    COMPUTER      2
    Test           5         1 EQUIVALENCE  (?)     SMITH         2
    Test           6         5 WORD         NULL    SMITH         1
    Test           7         5 WORD         NULL    SMYTHE        2

#### Restrictions

`CTX_QUERY.EXPLAIN` does not support the use of query templates.

You cannot use `CTX_QUERY.EXPLAIN` with remote queries.

#### Related Topics

[Oracle Text CONTAINS Query Operators](oracle-text-CONTAINS-query-operators.md)

[Stopword Transformations in Oracle Text](stopword-transformations-in-oracle-text.md)

### 12.4 HFEEDBACK

In English or French, this procedure generates hierarchical query feedback information (broader term, narrower term, and related term) for the specified query.

Broader term, narrower term, and related term information is obtained from the knowledge base. However, only knowledge base terms that are also in the index are returned as query feedback information. This increases the chances that terms returned from `HFEEDBACK` produce hits over the currently indexed document set.

Hierarchical query feedback information is useful for suggesting other query terms to the user.

#### Syntax

Syntax 1

    exec CTX_QUERY.HFEEDBACK(
               index_name     IN VARCHAR2,
               text_query     IN VARCHAR2,
               feedback_table IN VARCHAR2,
               sharelevel     IN NUMBER DEFAULT 0,
               feedback_id    IN VARCHAR2 DEFAULT NULL,
               part_name      IN VARCHAR2 DEFAULT NULL
    );

Syntax 2

    exec CTX_QUERY.HFEEDBACK_CLOB_QUERY(
               index_name     IN VARCHAR2,
               text_query     IN CLOB,
               feedback_table IN VARCHAR2,
               sharelevel     IN NUMBER DEFAULT 0,
               feedback_id    IN VARCHAR2 DEFAULT NULL,
               part_name      IN VARCHAR2 DEFAULT NULL
    );

index_name
Specify the name of the index for the text column to be queried.

text_query
Specify the query expression to be used as criteria for selecting rows.

feedback_table
Specify the name of the table used to store thefeedback terms.

**See Also:**

"[HFEEDBACK Table](oracle-text-result-tables.md)" in [Oracle Text Result Tables](oracle-text-result-tables.md) for more information about the structure of the explain table.

sharelevel
Specify whether `feedback_table` is shared by multiple `HFEEDBACK` calls. Specify 0 for exclusive use and 1 for shared use. Default is 0 (single-use).

When you specify 0, the system automatically truncates the feedback table before the next call to `HFEEDBACK`.

When you specify 1 for shared use, this procedure does not truncate the feedback table. Only results with the same `feedback_id` are updated. When no results with the same `feedback_id` exist, new results are added to the feedback table.

feedback_id
Specify a value that identifies the feedback results returned by a call to `HFEEDBACK` when more than one `HFEEDBACK` call uses the same shared feedback table. Default is `NULL`.

part_name
Specify the name of the index partition to query.

#### Example

Create HFEEDBACK Result Table

Create a result table to use with `CTX_QUERY.HFEEDBACK `as follows:

      CREATE TABLE restab (
        feedback_id VARCHAR2(30),
        id          NUMBER,
        parent_id   NUMBER,
        operation   VARCHAR2(30),
        options     VARCHAR2(30),
        object_name VARCHAR2(80),
        position    NUMBER,
        bt_feedback ctxsys.ctx_feedback_type,
        rt_feedback ctxsys.ctx_feedback_type,
        nt_feedback ctxsys.ctx_feedback_type,
        NESTED TABLE bt_feedback STORE AS res_bt,
        NESTED TABLE rt_feedback STORE AS res_rt,
        NESTED TABLE nt_feedback STORE AS res_nt
     ;


[CTX_FEEDBACK_TYPE](oracle-text-result-tables.md) is a system-defined type in the `CTXSYS` schema.

**See Also:**

"[HFEEDBACK Table](oracle-text-result-tables.md)" in [Oracle Text Result Tables](oracle-text-result-tables.md) for more information about the structure of the `HFEEDBACK` table.

Call CTX_QUERY.HFEEDBACK

The following code calls the `HFEEDBACK` procedure with the query computer industry.

    BEGIN
    ctx_query.hfeedback (index_name     => 'my_index',
                         text_query     => 'computer industry',
                         feedback_table => 'restab',
                         sharelevel     => 0,
                         feedback_id    => 'query10'
                        );
    END;

Select From the Result Table

The following code extracts the feedback data from the result table. It extracts broader term, narrower term, and related term feedback separately from the nested tables.

    DECLARE
      i NUMBER;
    BEGIN
      FOR frec IN (
        SELECT object_name, bt_feedback, rt_feedback, nt_feedback
        FROM restab
        WHERE feedback_id = 'query10' AND object_name IS NOT NULL
      ) LOOP

        dbms_output.put_line('Broader term feedback for ' || frec.object_name ||
    ':');
        i := frec.bt_feedback.FIRST;
        WHILE i IS NOT NULL LOOP
          dbms_output.put_line(frec.bt_feedback(i).text);
          i := frec.bt_feedback.NEXT(i);
        END LOOP;

        dbms_output.put_line('Related term feedback for ' || frec.object_name ||
    ':');
        i := frec.rt_feedback.FIRST;
        WHILE i IS NOT NULL LOOP
          dbms_output.put_line(frec.rt_feedback(i).text);
          i := frec.rt_feedback.NEXT(i);
        END LOOP;

        dbms_output.put_line('Narrower term feedback for ' || frec.object_name ||
    ':');
        i := frec.nt_feedback.FIRST;
        WHILE i IS NOT NULL LOOP
          dbms_output.put_line(frec.nt_feedback(i).text);
          i := frec.nt_feedback.NEXT(i);
        END LOOP;

      END LOOP;
    END;

#### Sample Output

The following output is for the preceding example, which queries on computer industry:

    Broader term feedback for computer industry:
    hard sciences
    Related term feedback for computer industry:
    computer networking
    electronics
    knowledge
    library science
    mathematics
    optical technology
    robotics
    satellite technology
    semiconductors and superconductors
    symbolic logic
    telecommunications industry
    Narrower term feedback for computer industry:
    AT&T Starlans
    ATI Technologies, Incorporated
    ActivCard
    Actrade International Ltd.
    Alta Technology
    Amiga Format
    Amiga Library Services
    Amiga Shopper
    Amstrat Action
    Apple Computer, Incorporated
    ..

**Note:**

The `HFEEDBACK` information you obtain depends on the contents of your index and knowledge base and as such might differ from the sample shown.

#### Restrictions

`CTX_QUERY.HFEEDBACK` does not support the use of query templates and rolling upgrades.

### 12.5 REMOVE_SQE

The `CTX_QUERY.REMOVE_SQE` procedure removes the specified stored query expression.

`CTX_QUERY.REMOVE_SQE` can be used to remove both session-duration and persistent SQEs. See "STORE_SQE".

Since the `query_name` namespace is shared between the persistent and session-duration SQEs, it is unnecessary to specify the duration of the SQE to be removed.

#### Syntax

    CTX_QUERY.REMOVE_SQE(
              query_name IN VARCHAR2
    );

query_name
Specify the name of the stored or session-duration query expression to be removed.

#### Example

    begin
      ctx_query.remove_sqe('dis1');
      ctx_query.remove_sqe('dis2');
    end;
    /

### 12.6 RESULT_SET

This procedure executes an XML query and generates a result set in XML.

The Result Set Interface can return data views that are difficult to express in SQL.

**See Also:**

[Oracle Text Application Developer's Guide](../ccapp/using-XML-query-result-set-interface.md) for details on how to use the Result Set Interface

#### Syntax

    CTX_QUERY.RESULT_SET (
       index_name            IN VARCHAR2,
       query                 IN VARCHAR2,
       result_set_descriptor IN CLOB,
       result_set            IN OUT NOCOPY CLOB,
       part_name             IN VARCHAR2 DEFAULT NULL
    );

index_name
Specify the index against which to execute the query.

query
Specify the query string.

result_set_descriptor
Specify the result set descriptor in XML. It describes what the result set should contain.

result_set
Specify the output result set. If this variable is `NULL` on input, a session-duration temporary lob will be allocated and returned to the user. The user is responsible for deallocating this temporary lob.

part_name
Specify the index partition name. If the index is global, `part_name` must be `NULL`. If the index is partitioned and `part_name` is not `NULL`, then the query will only be evaluated for the given partition. If the index is partitioned and `part_name` is `NULL`, then the query will be evaluated for all partitions.

#### The Input Result Set Descriptor

The result set descriptor is an XML message which describes what to calculate for the result set. The elements present in the result set descriptor and the order in which they occur serve as a simple template, specifying what to include in the output result set. That is, there should be the list of hit rowids, then a count, then a token count, and so on. The attributes of the elements specify the parameters and options to the specific operations, such as number of hits in the list of rowids, estimate versus exact count, and so on.

The result set descriptor itself is XML conforming to the following DTD:

    <!DOCTYPE ctx_result_set_descriptor [
    <!ELEMENT ctx_result_set_descriptor (hitlist?, group*, count?, collocates?)>
    <!ELEMENT hitlist (rowid?, score?, sdata*, snippet*, sentiment?)>
    <!ELEMENT group (count?, group_values?)>
    <!ELEMENT count EMPTY>
    <!ELEMENT rowid EMPTY>
    <!ELEMENT score EMPTY>
    <!ELEMENT sdata EMPTY>
    <!ELEMENT group_values (value*)>
    <!ELEMENT value EMPTY>
    <!ELEMENT sentiment (item*)>
    <!ELEMENT item EMPTY>
    <!ELEMENT collocates EMPTY>
    <!ATTLIST sentiment classifier CDATA "DEFAULT_CLASSIFIER">
    <!ATTLIST item topic CDATA #REQUIRED>
    <!ATTLIST item type (about|exact) "exact">
    <!ATTLIST item agg (TRUE|FALSE) "FALSE">
    <!ATTLIST item radius CDATA "50">
    <!ATTLIST item max_inst CDATA "5">
    <!ATTLIST item starttag CDATA #IMPLIED>
    <!ATTLIST item endtag CDATA #IMPLIED>
    <!ATTLIST collocates radius CDATA "20">
    <!ATTLIST collocates max_words CDATA "10">
    <!ATTLIST collocates use_tscore (TRUE|FALSE) "TRUE">
    <!ATTLIST collocates use_hits CDATA "10">
    <!ATTLIST group sdata CDATA #REQUIRED>

    <!ATTLIST group topn CDATA #IMPLIED>
    <!ATTLIST group bucketby CDATA #IMPLIED>
    <!ATTLIST group sortby CDATA #IMPLIED>
    <!ATTLIST group order CDATA #IMPLIED>
    <!ATTLIST value id CDATA #IMPLIED>
    <!ATTLIST hitlist start_hit_num CDATA #REQUIRED>
    <!ATTLIST hitlist end_hit_num CDATA #REQUIRED>
    <!ATTLIST hitlist order CDATA #IMPLIED>
    <!ATTLIST count exact (TRUE|FALSE) "FALSE">

    <!ATTLIST sdata name CDATA #REQUIRED>
    <!ATTLIST snippet radius CDATA #IMPLIED>
    <!ATTLIST snippet max_length CDATA #IMPLIED>
    <!ATTLIST snippet starttag CDATA #IMPLIED>
    <!ATTLIST snippet endtag CDATA #IMPLIED>
    ]>

The following is a description of the possible XML elements for the result set descriptor:

- `ctx_result_set_descriptor`

  This is the root element for the result set descriptor. The parent element is none, as are the available attributes.

  The possible child elements are:

  - Zero or more `hitlist` elements.

  - Zero or more `group` elements.

  - At most one `count` element.

- `group`

  The `group` element causes the generated result set to include a group breakdown. In other words, a breakdown of the results by `SDATA` section values. The group element is also used to obtain facet counts for faceted navigation support. The parent element is `ctx_result_set_descriptor`, and the available attributes are:

  - `sdata`

    Specifies the name of the `SDATA` section to use for grouping. It is required.

  - `bucketby`

    Determines how group values are bucketed for counting. At the time of this release, the supported valid attribute value is single. It displays each unique facet value along with its count.

  - `topn`

    Restricts the maximum number of facet values that are returned. It sorts by descending group count by default. Valid attribute values are positive integers larger than zero.

  - `sortby`

    Valid attribute values are value and count. Value sorts using the value themselves, as appropriate for each data type. Count (default) sorts using the counts for each group.

  - `order`

    Order can be ascending or descending.

  Possible child elements of `group` are:

  - At most one `count` element.

- `hitlist`

  The `hitlist` element controls inclusion of a list of hit documents. The parent element is `ctx_result_set_descriptor`, and the available attributes are:

  The possible attribute elements for `hitlist` are:

  - `start_hit_num`

    This specifies the starting document hit to be included in the generated result set. This can be set to any positive integer less than or equal to 16000. For example, if `start_hit_num` is 21, then the result set will include document hits starting from the 21st document hit. This element is required.

  - `end_hit_num`

    This specifies the last document hit to be included in the generated result set. This can be set to any positive integer less than or equal to 48000. For example, if `end_hit_num` is 40, then the result set will include document hits up to the 40th document hit. This element is required.

  - `order`

    This is an optional attribute that specifies the order for the documents in the generated result set. The value is a list similar to a SQL `ORDER` `BY` statement, except that, instead of column names, they can either be `SCORE` or `SDATA` section names. In the following example, `MYDATE` and `MYPRICE` are the `SDATA` section names:

        (order = "SCORE DESC, MYDATE, MYPRICE DESC")

    The possible child elements for `hitlist` are:

  - At most one `rowid` element.

  - At most one `score` element.

  - One or more `sdata` element.

  - At most one `snippet` element.

- `count`

  This element causes the generated result set to include a count of the number of hit documents. The parent elements are:

  - `ctx_result_set_descriptor`

  - `group`

  The available attributes for `count` are:

  - `exact`

    This is to estimate mode. Set to `true` or `false`. It is required, and the default is `false`.

  The possible child elements for `count` are none.

- `rowid`

  This child element causes the generated result set to include rowid information for each hit. The parent element is `hitlist`. There are no attributes and no possible child elements.

- `score`

  This child element causes the generated result set to include score information for each hit.

  - The parent element is `hitlist`.

  - There are no available attributes, and no possible child elements.

- `sdata`

  This child element causes the generated result set to include `sdata` values for each hit.

  - The parent element is `hitlist`.

  - The available attribute is `name`. This specifies the name of the `sdata` section. It is required.

  - There are no child elements.

- `sentiment`

  This element controls the inclusion of sentiment classification results for each document returned as a part of the `hitlist`. There can be only one sentiment element in the `hitlist` element.

  The parent element is `hitlist`.

  The attribute available for this element is `classifier`, which specifies the sentiment classifier that is used to perform sentiment analysis. If no classifier is specified, then the `CTXSYS.DEFAULT_SENTIMENT_CLASSIFIER` is used. If a specified classifier is not available, then an error is displayed.

- `item`

  This element specifies keywords or concepts for which sentiment information must be fetched for the returned set of documents. Each `sentiment` element must contain at least one child `item` element. The maximum is 10 child `item` elements. If you specify an empty `item` element (without any attributes), it indicates that sentiment score for entire document must be returned.

  The parent element is `sentiment`.

  The available attributes for `item` are:

  - `topic`

    This specifies the topic for which sentiment analysis must be performed.

  - `type`

    If this attribute value is set to `ABOUT`, then the classifier treats the specified topic as a concept rather than a keyword. The default is `EXACT`.

  - `agg`

    Determines whether the sentiment score must be aggregated and presented as a single score for the entire document. The possible values are TRUE or FALSE. TRUE indicates that the per text segment scores will be aggregated and text segments will not be returned in the output resultset, only the aggregated score will be returned. The default value is FALSE.

  - `radius`

    This specifies the radius of the surrounding text to be identified during sentiment classification for that keyword. The default value is 50.

  - `max_inst`

    This specifies how many instances of text excerpts related to the specified topic must be analyzed for sentiment classification. The default value is 5.

  - `starttag`

    This specifies the starting tag for topic highlighting.

  - `endtag`

    This specifies the ending tag for topic highlighting.

- `collocates`

  This element controls the generation of related keywords or concepts associated with the collection of documents retrieved by the query.

  The parent element is `ctx_result_set_descriptor`.

  The available attributes for `collocates` are:

  - `radius`

    This specifies the radius of the surrounding text to be identified for collocates. The default value is 20.

  - `max_words`

    This specifies the maximum number of collocates to return for the given query. The default value is 10.

  - `use_tscore`

    This specifies whether to use T-score for scoring the collocates. The possible values are TRUE or FALSE, with the default being TRUE.

    Set this attribute to TRUE to identify collocates that are common tokens. Set this attribute to FALSE to identify collocates that emphasize unique words.

#### The Output Result Set XML

The output result set XML is XML conforming to the following DTD:

    <!DOCTYPE ctx_result_set [
    <!ELEMENT ctx_result_set (hitlist?, groups*, count? , collocates?)>
    <!ELEMENT hitlist (hit*)>
    <!ELEMENT hit (rowid?, score?, snippet*, sdata*, sentiment?)>
    <!ELEMENT groups (group*)>
    <!ELEMENT group (count?)>
    <!ELEMENT count (#PCDATA)>
    <!ELEMENT rowid (#PCDATA)>
    <!ELEMENT score (#PCDATA)>
    <!ELEMENT snippet (segment*)>
    <!ELEMENT sdata (#PCDATA)>
    <!ELEMENT sentiment (item*)>
    <!ELEMENT item (segment*, score*, doc?)>
    <!ELEMENT segment (segment_text?, segment_score?)>
    <!ELEMENT segment_text (#PCDATA)>
    <!ELEMENT segment_score (#PCDATA)>
    <!ELEMENT doc (score?)>
    <!ELEMENT collocates (collocation*)>
    <!ELEMENT collocation (word?, score?)>
    <!ELEMENT word (#PCDATA)>
    <!ATTLIST item topic CDATA #REQUIRED>
    <!ATTLIST groups sdata CDATA #REQUIRED>
    <!ATTLIST group value CDATA #REQUIRED>

    <!ATTLIST group range CDATA #IMPLIED>
    <!ATTLIST group single CDATA #IMPLIED>
    <!ATTLIST sdata name CDATA #REQUIRED>

The following is a description of the list of possible XML elements for the output result set:

- `ctx_result_set`

  This is the root element for the generated result set. There are no attributes. The parent is none. The possible child elements are:

  - At most one `hitlist` element.

  - Zero or more `groups` elements.

- `groups`

  This delimits the start of a group breakdown section. The parent element is `ctx_result_set`. The available attributes are:

  - `sdata`

    This is the name of the `sdata` section used for grouping.

  The possible child elements are:

  - Zero or more `group` elements.

- `group`

  This delimits the start of a `GROUP` `BY` value. The parent element is the `groups` element. The available attributes are:

  - `value`

    This is the value of the `sdata` section.

  The possible child elements are at most one `count` element.

- `hitlist`

  This delimits the start of `hitlist` information. The parent element is `ctx_result_set`, while the children are zero or more `hit` elements. There are no attributes.

- `hit`

  This delimits the start of the information for a particular document within a `hitlist`. The parent element is `hitlist`, and there are no available attributes. The possible child elements are:

  - Zero or one `rowid` elements.

  - Zero or one `score` element.

  - Zero or one `sdata` element.

  - Zero or one `snippet` element.

- `rowid`

  This is the rowid of the document, so the content is the rowid of the document. The parent element is the `hit` element. There are no child elements, and no available attributes.

- `score`

  This is the score of the document. The parent element is the hit element. The content is the numeric score. There are no available attributes, and no possible child elements.

- `sdata`

  This is the `SDATA` value or values for the document. The parent element is the `hit` element, and the available attribute is `name`, which is the name of the `sdata` section. There are no possible child elements available. The content is the `SDATA` section value, which, for `DATE` values, is in the format "YYYY-MM-DD HH24:MI:SS", depending upon the actual values being stored.

- `count`

  This is the document hit count. The parent element is the `ctx_result_set` element or the `group` element. It contains the numeric hit count, has no attributes, and no possible child elements.

- `sentiment`

  This delimits the sentiment element for the `hitlist` document. Its child element is `item` and parent is `hitlist`. It contains no attributes in the output result set.

- `item`

  This delimits the `item` element for the `hitlist` document. Parent element is `sentiment` and child elements are `segment`, `score`, and `doc`. It has one attribute called `topic`.

- `segment`

  This delimits an instance of segment element in a hit. Parent element is `item`. Child elements are `segment_text` and `segment_score`. It contains no attributes.

- `segment_text`

  This specifies the text segment for the given item topic. Parent element is `segment`. It has no child elements or attributes.

- `segment_score`

  This specifies the sentiment score for the segment. Parent element is segment. It has no child elements or attributes.

- `score`

  This specifies the sentiment score for the document or for the parent item topic. When present within collocation it specifies the collocation score for the particular collocation keyword. Parent element is doc or collocation. It has no child elements or attributes

- `doc`

  This denotes the sentiment score is for the entire document. Its parent element is `item` and child element is `score`. It has no attributes.

- `collocates`

  This delimits the collocates element for the result set output. Parent element is `ctx_result_set` and child element is `collocation`. It has no attributes.

- `collocation`

  This denotes a single collocation. Parent element is `collocates` and child elements are `word` and `score`. It has no attributes.

- `word`

  This specifies the collocates token. Its parent element is `collocation`. It has no child elements or attributes.

#### Example

This call to `CTX_QUERY.RESULT_SET` with the specified XML `result_set_descriptor` will generate the following information in the form of XML:

- top 5 hits displaying, score, rowid, author `SDATA` section value, and pubDate `SDATA` section value, order by pubDate `SDATA` section value `DESC` and score `DESC`

- total doc hit count for the text query

- counts group by pubDate `SDATA` section values

- counts group by author `SDATA` section values

<!-- -->

    declare
      rs clob;
    begin
      dbms_lob.createtemporary(rs, true, dbms_lob.session);
      ctx_query.result_set('docidx', 'oracle', '
      <ctx_result_set_descriptor>
       <count/>
       <hitlist start_hit_num="1" end_hit_num="5" order="pubDate desc, score desc">
         <score/>
         <rowid/>
         <sdata name="author"/>
         <sdata name="pubDate"/>
       </hitlist>
       <group sdata="pubDate">
         <count/>
       </group>
       <group sdata="author">
         <count/>
       </group>
      </ctx_result_set_descriptor>
    ', rs);
      dbms_lob.freetemporary(rs);
    exception
      when others then
       dbms_lob.freetemporary(rs);
       raise;
    end;
    /

The XML output store in the result set output clob will resemble the following:

    <ctx_result_set>
      <hitlist>
        <hit>
          <score>3</score><rowid>AAAPoEAABAAAMWsAAC</rowid>
          <sdata name="AUTHOR">John</sdata>
          <sdata name="PUBDATE">2001-01-03 00:00:00</sdata>
        </hit>
        <hit>
          <score>3</score><rowid>AAAPoEAABAAAMWsAAG</rowid>
          <sdata name="AUTHOR">John</sdata>
          <sdata name="PUBDATE">2001-01-03 00:00:00</sdata>
        </hit>
        <hit>
          <score>3</score><rowid>AAAPoEAABAAAMWsAAK</rowid>
          <sdata name="AUTHOR">John</sdata>
          <sdata name="PUBDATE">2001-01-03 00:00:00</sdata>
        </hit>
        <hit>
          <score>3</score><rowid>AAAPoEAABAAAMWsAAO</rowid>
          <sdata name="AUTHOR">John</sdata>
          <sdata name="PUBDATE">2001-01-03 00:00:00</sdata>
        </hit>
        <hit>
          <score>3</score><rowid>AAAPoEAABAAAMWsAAS</rowid>
          <sdata name="AUTHOR">John</sdata>
          <sdata name="PUBDATE">2001-01-03 00:00:00</sdata>
        </hit>
      </hitlist>

      <count>100</count>

      <groups sdata="PUBDATE">
        <group value="2001-01-01 00:00:00"><count>25</count></group>
        <group value="2001-01-02 00:00:00"><count>50</count></group>
        <group value="2001-01-03 00:00:00"><count>25</count></group>
      </groups>

      <groups sdata="AUTHOR">
        <group value="John"><count>50</count></group>
        <group value="Mike"><count>25</count></group>
        <group value="Steve"><count>25</count></group>
      </groups>

    </ctx_result_set>

#### Limitations and Restrictions

The following limitations and restrictions apply for `RESULT_SET`.

- The Result Set Interface (RSI) is not supported with Virtual Private Database. (VPD is supported with the regular `CONTAINS` query, but not with RSI.)

- In order to execute the function, you must be able to query the base table.

- If a VPD policy is active on the base table, the documents portion of the result set will not show any documents to which you are not entitled.

- When a VPD policy is being used, aggregate measures such as count may not be accurate.

#### Related Topics

[Oracle Text Application Developer's Guide](../ccapp/using-XML-query-result-set-interface.md) for information on the XML Result Set Interface

[Oracle Text Application Developer's Guide](../ccapp/using-faceted-navigation.md) for more information on faceted navigation.

### 12.7 RESULT_SET_CLOB_QUERY

This procedure executes an XML query and generates a result set based on a `CLOB` query parameter in XML

#### Syntax

The `RESULT_SET_CLOB_QUERY` procedure is identical to the `RESULT_SET` procedure except that the datatype of its query parameter is `CLOB` instead of `VARCHAR2` to handle longer queries.

    CTX_QUERY.RESULT_SET_CLOB_QUERY (
       index_name            IN VARCHAR2,
       query                 IN CLOB,
       result_set_descriptor IN CLOB,
       result_set            IN OUT CLOB,
       part_name             IN VARCHAR2 DEFAULT
    );

**See Also:**

RESULT_SET for the description of these parameters

### 12.8 RESULT_SET_DOCUMENT

`RESULT_SET_DOCUMENT` holds the result set document after the `CONTAINS` query cursor is explicitly closed and if the query template has the \<ctx_result_set_descriptor\> element.

#### Syntax

    CTX_QUERY.RESULT_SET_DOCUMENT(
       index_name            IN VARCHAR2,
       query                 IN VARCHAR2,
       result_set_descriptor IN CLOB,
       result_set            IN OUT NOCOPY CLOB,
       part_name             IN VARCHAR2 DEFAULT NULL
    );

index_name
Specify the index against which to execute the query.

query
Specify the query string.

result_set_descriptor
Specify the result set descriptor in XML. It describes what the result set should contain. See "The Input Result Set Descriptor" for more details.

result_set
Specify the output result set. If this variable is `NULL` on input, a session-duration temporary lob will be allocated and returned to the user. The user is responsible for deallocating this temporary lob. See "The Output Result Set XML" for more details.

part_name
Specify the index partition name. If the index is global, `part_name` must be `NULL`. If the index is partitioned and `part_name` is not `NULL`, then the query will only be evaluated for the given partition. If the index is partitioned and `part_name` is `NULL`, then the query will be evaluated for all partitions.

### 12.9 STORE_SQE

This procedure creates either a stored or session-duration query expression (SQE). Only the query definition is stored.

SQEs are used to store the definition of a query without storing any results. Referencing the query with the `CONTAINS` SQL operator references the definition of the query. In this way, SQEs make it easy for defining long or frequently used query expressions. Creating a session-duration SQE is useful for when you do not want the maintenance overhead of deleting unused or no longer needed SQEs.

#### Supported Operators

Stored query expressions support all of the `CONTAINS` query operators. Stored query expressions also support all of the special characters and other components that can be used in a query expression, including other stored query expressions.

#### Privileges

Users are permitted to create and remove stored query expressions owned by them. Users are permitted to use stored query expressions owned by anyone. The `CTXSYS` user can create or remove stored query expressions for any user.

#### Syntax

Syntax 1

    CTX_QUERY.STORE_SQE(
               query_name      IN VARCHAR2,
               text_query      IN VARCHAR2,
               duration        IN NUMBER default CTX_QUERY.DURATION_PERSISTENT
    );

Syntax 2

    CTX_QUERY.STORE_SQE_CLOB_SYNTAX(
               query_name      IN VARCHAR2,
               text_query      IN CLOB,
               duration        IN NUMBER default CTX_QUERY.DURATION_PERSISTENT
    );

query_name
Specify the name of the stored query expression to be created.

text_query
Specify the query expression to be associated with `query_name`.

duration
The possible values are `DURATION_SESSION` and `DURATION_PERSISTENT`.

- When `duration` is to set to `DURATION_SESSION`, the stored query expression is stored in a PL/SQL package variable and is available for the session.

- When `duration` is to set to `DURATION_PERSISTENT`, the stored query expression is stored in a database table, and can be referenced by other database sessions.

- SQEs with the `DURATION_SESSION` option are not supported when issued from the catalog of a sharded database. Use the `DURATION_PERSISTENT` option instead.

- The `query_name` namespace is shared between the persistent and session-duration SQEs. If you try to add a persistent or session-duration SQE with a name that is already used by another persistent or session-duration SQE, then an error will be raised.

duration_persistent
When there is a CLOB query, specify that the duration is stored in a database table. This SQE must be deleted when it is no longer needed.

- The `query_name` namespace is shared between the persistent and session-duration SQEs. If you try to add a persistent or session-duration SQE with a name that is already used by another persistent or session-duration SQE, then an error will be raised.

#### Example

    begin
      ctx_query.store_sqe('dis1', 'flood', CTX_QUERY.DURATION_SESSION);
      ctx_query.store_sqe('dis2', 'tornado', CTX_QUERY.DURATION_PERSISTENT);
      ctx_query.store_sqe('dis3', 'fire')
    end;
    /
