## 3  Oracle Text CONTAINS Query Operators

This chapter describes operator precedence and provides descriptions, syntax, and examples for every [CONTAINS](oracle-text-SQL-statements-and-operators.md) operator.

This chapter contains the following topics:

- Operator Precedence

- ABOUT

- ACCUMulate ( \_ )

- AND (&)

- Broader Term (BT\_ BTG\_ BTP\_ BTI)

- CTXFILTERCACHE

- DEFINEMERGE

- DEFINESCORE

- EQUIValence (=)

- Fuzzy

- HASPATH

- INPATH

- MDATA

- MINUS (-)

- MNOT

- Narrower Term (NT\_ NTG\_ NTP\_ NTI)

- NDATA

- NEAR (;)

- NEAR2

- NOT (~)

- OR (\|)

- Preferred Term (PT)

- Related Term (RT)

- SDATA

- soundex (!)

- stem (\$)

- Stored Query Expression (SQE)

- SYNonym (SYN)

- threshold (\>)

- Translation Term (TR)

- Translation Term Synonym (TRSYN)

- Top Term (TT)

- weight (\*)

- wildcards (% \_)

- WITHIN

### 3.1 Operator Precedence

Operator precedence determines the order in which the components of a query expression are evaluated. Text query operators can be divided into two sets of operators that have their own order of evaluation. These two groups are described later as Group 1 and Group 2.

In all cases, query expressions are evaluated in order from left to right according to the precedence of their operators. Operators with higher precedence are applied first. Operators of equal precedence are applied in order of their appearance in the expression from left to right.

- Group 1 Operators

- Group 2 Operators and Characters

- Procedural Operators

- Precedence Examples

- Altering Precedence

#### 3.1.1 Group 1 Operators

Within query expressions, the Group 1 operators have the following order of evaluation from highest precedence to lowest:

1.  EQUIValence (=)

2.  NEAR (;)

3.  weight (\*), threshold (\>)

4.  MINUS (-)

5.  NOT (~)

6.  MNOT

7.  WITHIN

8.  AND (&)

9.  OR (\|)

10. ACCUMulate ( \_ )

#### 3.1.2 Group 2 Operators and Characters

Within query expressions, the Group 2 operators have the following order of evaluation from highest to lowest:

1.  Wildcard Characters

2.  stem (\$)

3.  Fuzzy

4.  soundex (!)

#### 3.1.3 Procedural Operators

Other operators not listed under Group 1 or Group 2 are procedural. These operators have no sense of precedence attached to them. They include the SQE and thesaurus operators.

#### 3.1.4 Precedence Examples

Table 3-1 Query Expression Precedence Examples

| Query Expression          | Order of Evaluation           |
|:--------------------------|:------------------------------|
| w1 \| w2 & w3             | (w1) \| (w2 & w3)             |
| w1 & w2 \| w3             | (w1 & w2) \| w3               |
| ?w1, w2 \| w3 & w4        | (?w1), (w2 \| (w3 & w4))      |
| abc = def ghi & jkl = mno | ((abc = def) ghi) & (jkl=mno) |
| dog and cat WITHIN body   | dog and (cat WITHIN body)     |

In the first example, because `AND` has a higher precedence than `OR`, the query returns all documents that contain w1 and all documents that contain both w2 and w3.

In the second example, the query returns all documents that contain both w1 and w2 and all documents that contain w3.

In the third example, the fuzzy operator is first applied to w1, then the `AND` operator is applied to arguments w3 and w4, then the `OR` operator is applied to term w2 and the results of the `AND` operation, and finally, the score from the fuzzy operation on w1 is added to the score from the `OR` operation.

The fourth example shows that the equivalence operator has higher precedence than the `AND` operator.

The fifth example shows that the `AND` operator has lower precedence than the `WITHIN` operator.

#### 3.1.5 Altering Precedence

Precedence is altered by grouping characters as follows:

- Within parentheses, expansion or execution of operations is resolved before other expansions regardless of operator precedence.

- Within parentheses, precedence of operators is maintained during evaluation of expressions.

- Within parentheses, expansion operators are not applied to expressions unless the operators are also within the parentheses.

  **See Also:**

  "[Grouping Characters](special-characters-in-oracle-text-queries.md)" in [Special Characters in Oracle Text Queries](special-characters-in-oracle-text-queries.md)

### 3.2 ABOUT

Use the `ABOUT` operator to return documents that are related to a query term or phrase.

#### General Behavior

In English and French, `ABOUT` enables you to query on concepts, even if a concept is not actually part of a query. For example, an `ABOUT` query on heat might return documents related to temperature, even though the term temperature is not part of the query.

In other languages, using `ABOUT` will often increase the number of returned documents and may improve the sorting order of results. For all languages, Oracle Text scores results for an `ABOUT` query with the most relevant document receiving the highest score.

#### English and French Behavior

In English and French, use the `ABOUT` operator to query on concepts. The system looks up concept information in the theme component of the index. Create a theme component to your index by setting the `INDEX_THEMES` [BASIC_LEXER](oracle-text-indexing-elements.md) attribute to `YES`.

**Note:**

You need not have a theme component in the index to enter `ABOUT` queries in English and French. However, having a theme component in the index yields the best results for `ABOUT` queries.

Oracle Text retrieves documents that contain concepts that are related to your query word or phrase. For example, if you enter an `ABOUT` query on California, the system might return documents that contain the terms Los Angeles and San Francisco, which are cities in California.The document need not contain the term California to be returned in this `ABOUT` query.

The word or phrase specified in your `ABOUT` query need not exactly match the themes stored in the index. Oracle Text normalizes the word or phrase before performing lookup in the index.

You can use the `ABOUT` operator with the `CONTAINS` and `CATSEARCH` SQL operators. In the case of `CATSEARCH`, you must use query templating with the `CONTEXT` grammar to query on the indexed themes. See ABOUT Query with CATSEARCH in the Examples section.

#### Syntax

| Syntax        | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                |
|:--------------|:-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| about(phrase) | In all languages, increases the number of relevant documents returned for the same query without the `ABOUT` operator. The phrase parameter can be a single word or a phrase, or a string of words in free text format.<br>In English and French, returns documents that contain concepts related to phrase, provided the `BASIC_LEXER` `INDEX_THEMES` attribute is set to YES at index time.<br>The score returned is a relevance score.<br>Oracle Text ignores any query operators that are included in phrase.<br>If your index contains only theme information, an `ABOUT` operator and operand must be included in your query on the text column or else Oracle Text returns an error.<br>The phrase you specify cannot be more than 4000 characters. |

#### Case-Sensitivity

`ABOUT` queries give the best results when your query is formulated with proper case. This is because the normalization of your query is based on the knowledge catalog which is case-sensitive.

However, you need not type your query in exact case to obtain results from an `ABOUT` query. The system does its best to interpret your query. For example, if you enter a query of CISCO and the system does not find this in the knowledge catalog, the system might use Cisco as a related concept for look-up.

#### Improving ABOUT Results

The `ABOUT` operator uses the supplied knowledge base in English and French to interpret the phrase you enter. Your `ABOUT` query therefore is limited to knowing and interpreting the concepts in the knowledge base.

Improve the results of your `ABOUT` queries by adding your application-specific terminology to the knowledge base.

**See Also:**

"[Extending the Knowledge Base](oracle-text-utilities.md)" in [Oracle Text Utilities](oracle-text-utilities.md)

#### Limitations

- The phrase you specify in an `ABOUT` query cannot be more than 4000 characters.

- The `ABOUT` query operator is not supported within sections.

- The `JSON_TEXTCONTAINS` query does not support the `ABOUT` operator.

#### Examples for ABOUT Operator

Single Words

To search for documents that are about soccer, use the following syntax:

    'about(soccer)'

Phrases

Further refine the query to include documents about soccer rules in international competition by entering the phrase as the query term:

    'about(soccer rules in international competition)'

In this English example, Oracle Text returns all documents that have themes of soccer, rules, or international competition.

In terms of scoring, documents which have all three themes will generally score higher than documents that have only one or two of the themes.

Unstructured Phrases

You can also query on unstructured phrases, such as the following:

    'about(japanese banking investments in indonesia)'

Combined Queries

Use other operators, such as `AND` or `NOT`, to combine `ABOUT` queries with word queries. For example, enter the following combined `ABOUT` and word query:

    'about(dogs) and cat'

Combine an `ABOUT` query with another `ABOUT` query as follows:

    'about(dogs) not about(labradors)'

**Note:**

You cannot combine `ABOUT` with the `WITHIN` operator, as for example 'ABOUT (xyz) WITHIN abc'.

ABOUT Query with CATSEARCH

Enter `ABOUT` queries with `CATSEARCH` using the query template method with grammar set to `CONTEXT` as follows:

    select pk||' ==> '||text from test
    where catsearch(text,
    '<query>
      <textquery grammar="context">
         about(California)
      </textquery>
      <score datatype="integer"/>
    </query>','')>0
    order by pk;

### 3.3 ACCUMulate ( , )

Use the `ACCUM` operator to search for documents that contain at least one occurrence of any query terms, with the returned documents ranked by a cumulative score based on how many query terms are found (and how frequently).

#### Syntax

| Syntax                           | Description                                                                                                                                                                              |
|:---------------------------------|:-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| term1,term2<br>term1 ACCUM term2 | Returns documents that contain term1 or term2. Ranks documents according to document term weight, with the highest scores assigned to documents that have the highest total term weight. |

#### ACCUMulate Scoring

ACCUMulate first scores documents on how many query terms a document matches. A document that matches more terms will always score higher than a document that matches fewer terms, even if the terms appear more frequently in the latter. In other words, if you search for dog ACCUM cat, you'll find that

    the dog played with the cat

scores higher than

    the big dog played with the little dog while a third dog ate the dog food

Scores are divided into ranges. In a two-term `ACCUM`, hits that match both terms will always score between 51 and 100, whereas hits matching only one of the terms will score between 1 and 50. Likewise, for a three-term `ACCUM`, a hit matching one term will score between 1 and 33; a hit matching two terms will score between 34 and 66, and a hit matching all three terms will score between 67 and 100. Within these ranges, normal scoring algorithms apply.

**See Also:**

[The Oracle Text Scoring Algorithm](oracle-text-scoring-algorithm.md) for more information on how scores are calculated

You can assign different weights to different terms. For example, in a query of the form

    soccer, Brazil*3

the term Brazil is weighted three times as heavily as soccer. Therefore, the document

    people play soccer because soccer is challenging and fun

will score lower than

    Brazil is the largest nation in South America

but both documents will rank below

    soccer is the national sport of Brazil

Note that a query of soccer ACCUM Brazil\*3 is equivalent to soccer ACCUM Brazil ACCUM Brazil ACCUM Brazil. Because each query term Brazil is considered independent, the entire query is scored as though it has four terms, not two, and thus has four scoring ranges. The first Brazil-and-soccer example document shown above scores in the first range (1-25), the second scores in the third range (51-75), and the third scores in the fourth range (76-100). (No document scores in the second range, because any document with Brazil in it will be considered to match at least three query terms.)

#### Example for ACCUM Operator

    set serveroutput on;
    DROP TABLE accumtbl;
    CREATE TABLE accumtbl (id NUMBER, text VARCHAR2(4000) );

    INSERT INTO accumtbl VALUES ( 1, 'the little dog played with the big dog
          while the other dog ate the dog food');
    INSERT INTO accumtbl values (2, 'the cat played with the dog');

    CREATE INDEX accumtbl_idx ON accumtbl (text) indextype is ctxsys.context;

    PROMPT dog ACCUM cat
    SELECT SCORE(10) FROM accumtbl WHERE CONTAINS (text, 'dog ACCUM cat', 10)
       > 0;

    PROMPT dog*3 ACCUM cat
    SELECT SCORE(10) FROM accumtbl WHERE CONTAINS (text, 'dog*3 ACCUM cat', 10)
       > 0;

This produces the following output. Note that the document with both dog and cat scores highest.

    dog ACCUM cat
       ID  SCORE(10)
    ----- ----------
        1          6
        2         52

    dog*3 ACCUM cat
       ID  SCORE(10)
    ----- ----------
        1         53
        2         76

#### Related Topics

weight (\*)

### 3.4 AND (&)

Use the `AND` operator to search for documents that contain at least one occurrence of each of the query terms.

The `AND` operator returns documents that contain all of the query terms, while `OR` operator returns documents that contain any of the query terms.

#### Syntax

| Syntax                         | Description                                                                                                                               |
|:-------------------------------|:------------------------------------------------------------------------------------------------------------------------------------------|
| term1&term2<br>term1 and term2 | Returns documents that contain term1 and term2. Returns the minimum score of its operands. All query terms must occur; lower score taken. |

#### Example for AND Operator

To obtain all the documents that contain the terms blue and green and red, enter the following query:

    'blue & green & red'

In an `AND` query, the score returned is the score of the lowest query term. In this example, if the three individual scores for the terms blue, green, and red is 10, 20 and 30 within a document, the document scores 10.

#### Related Topics

OR (\|)

### 3.5 Broader Term (BT, BTG, BTP, BTI)

Use the broader term operators (`BT`, `BTG`, `BTP`, `BTI`) to expand a query to include the term that has been defined in a thesaurus as the broader or higher level term for a specified term. They can also expand the query to include the broader term for the broader term and the broader term for that broader term, and so on up through the thesaurus hierarchy.

#### Syntax

| Syntax                                      | Description                                                                                              |
|:--------------------------------------------|:---------------------------------------------------------------------------------------------------------|
| BT(term\[(qualifier)\]\[,level\]\[,thes\])  | Expands a query to include the term defined in the thesaurus as a broader term for `term`.               |
| BTG(term\[(qualifier)\]\[,level\]\[,thes\]) | Expands a query to include all terms defined in the thesaurus as broader generic terms for `term`.       |
| BTP(term\[(qualifier)\]\[,level\]\[,thes\]) | Expands a query to include all the terms defined in the thesaurus as broader partitive terms for `term`. |
| BTI(term\[(qualifier)\]\[,level\]\[,thes\]) | Expands a query to include all the terms defined in the thesaurus as broader instance terms for `term`.  |

term
Specify the operand for the broader term operator. Oracle Text expands `term` to include the broader term entries defined for the term in the thesaurus specified by `thes`. For example, if you specify BTG(dog), the expansion includes only those terms that are defined as broader term generic for dog. You cannot specify expansion operators in the `term` argument.

The number of broader terms included in the expansion is determined by the value for `level`.

qualifier
Specify a qualifier for `term`, if `term` is a homograph (word or phrase with multiple meanings, but the same spelling) that appears in two or more nodes in the same hierarchy branch of `thes`.

If a qualifier is not specified for a homograph in a broader term query, the query expands to include the broader terms of all the homographic terms.

level
Specify the number of levels traversed in the thesaurus hierarchy to return the broader terms for the specified term. For example, a level of 1 in a BT query returns the broader term entry, if one exists, for the specified term. A level of 2 returns the broader term entry for the specified term, as well as the broader term entry, if one exists, for the broader term.

The level argument is optional and has a default value of one (1). Zero or negative values for the level argument return only the original query term.

thes
Specify the name of the thesaurus used to return the expansions for the specified term. The `thes` argument is optional and has a default value of `DEFAULT`. A thesaurus named `DEFAULT` must exist in the thesaurus tables if you use this default value.

**Note:**

If you specify `thes`, then you must also specify `level`.

#### Examples for Broader Term Operators

The following query returns all documents that contain the term tutorial or the `BT` term defined for tutorial in the `DEFAULT` thesaurus:

    'BT(tutorial)'

When you specify a thesaurus name, you must also specify `level` as in:

    'BT(tutorial, 2, mythes)'

Broader Term Operator on Homographs

If machine is a broader term for crane (building equipment) and bird is a broader term for crane (waterfowl) and no qualifier is specified for a broader term query, the query

    BT(crane)

expands to:

    '{crane} or {machine} or {bird}'

If waterfowl is specified as a qualifier for crane in a broader term query, the query

    BT(crane{(waterfowl)})

expands to the query:

    '{crane} or {bird}'

**Note:**

When specifying a qualifier in a broader or narrower term query, the qualifier and its notation (parentheses) must be escaped, as is shown in this example.

#### Related Topics

CTX_THES.[BT](CTX_THES-package.md) in [CTX_THES Package](CTX_THES-package.md) for more information on browsing the broader terms in your thesaurus

### 3.6 CTXFILTERCACHE

Oracle Text provides a cache layer called query filter cache that can be used to cache the query results. Query filter cache is sharable across queries. Thus, the cached query results can be reused by multiple queries, improving the query response time. The `CTXFILTERCACHE` operator is used to specify which query results or part of query results to cache in the query filter cache.

`CTXFILTERCACHE` only supports CONTEXT grammar queries. CONTAINER queries like template queries are not supported. If you execute it with a template query, then errors are raised.

**Caution:**

Before using `CTXFILTERCACHE`, you must run `PURGE` `recyclebin` as follows:

    SQL> PURGE recylebin;

See [Oracle Database Administrator's Guide](../admin/managing-tables.md) for complete information about purging objects in the recycle bin.

#### Syntax

    ctxfiltercache((query_text) [, save_score] [, topN])

query_text
Specify the query whose results need to be stored in the cache.

save_score
Specify `TRUE` if you want to cache all the query results along with their scores in the cache.

The default is `FALSE`. In this case, a score of 100 is returned for each query result, and these scores are not stored in the cache. Only the query results are stored in the cache.

Specify `FALSE` when you want to reuse the query results and not their scores in other queries. This is particularly useful when you use the query text as a filter, such as a security filter, where the relevance of the cached part of the query does not affect the relevance of the query as a whole. Thus, when used with the AND operator (which returns a lower score of its operands), a score of 100 does not affect the score of a query as a whole.

topN
Specify `TRUE` if you want only the highest scoring query results to be stored in the cache. Oracle Text internally determines how many highest scoring query results to store in the cache. This helps in reducing the memory consumption of the cache.

**Note:**

If you specify `TRUE` for `topN`, then `save_score` should also be `TRUE`.

#### Examples for CTXFILTERCACHE

Stored Query Results and TopN Examples

The following example stores the query results of the `common_predicate` query in the cache:

    select * from docs where contains(txt, 'ctxfiltercache((common_predicate), FALSE)')>0;

Here, `save_score` is `FALSE`, and hence the score of 100 is returned for each query result, and the scores are not stored in the cache.

In the following example, the cached results of the `common_predicate` query are reused by the `new_query` query.

    select * from docs where contains(txt, 'new_query & ctxfiltercache((common_predicate), FALSE)')>0;

Set `save_score` to `TRUE` as shown in the following example to store all the query results of the `common_predicate` query, along with the actual scores, in the cache.

    select * from docs where contains(txt, 'ctxfiltercache((common_predicate), TRUE)')>0;

Set `topN` to `TRUE` if you want to store only the highest scoring query results of the `common_predicate` query in the cache as described in the following example.

    select id, score(1) from docs where contains(txt, 'ctxfiltercache((common_predicate), TRUE, TRUE)', 1)>0 order by score(1) desc;

Set `topN` to `TRUE` for the main part of the query and `FALSE` for the filter part, when the score is relevant only for the main part of the query. The following example shows a query with two `ctxfiltercache` clauses. It performs a free-text search for "cat AND dog" and then applies a security filter to the search operation. Results of both the parts of this query are separately cached so that they can be reused, but the score is relevant only for the first part of the query.

    select id, score(1) from docs where contains(txt, 'ctxfiltercache((cat AND dog), TRUE, TRUE) AND ctxfiltercache((john WITHIN allowedUsers), FALSE, FALSE)', 1) > 0;

Cached Score Example

`CTXFILTERCACHE` stores one query result for `score` at a time in the cache. Hence, two similar queries executed serially are considered the same query, and there is only one such query stored in the cache.

The following examples, query A and query B, show two similar queries. The hit score for A is `100`, and the hit score for B is `5`. Assume the cache is empty and you execute query A first. The computed score `100` is stored in the cache for this query. When you execute query B subsequently now, the cache contains the stored score of `100`, and therefore, query B returns the cached score of `100`. Conversely, if you execute query B before query A, then the cached computed score that gets returned is `5`.

Query A:

    select  /*+ DOMAIN_INDEX_SORT */ id, score(1) as ORADD from mydocs where contains (txt ,'ctxfiltercache((DEFINEMERGE
            (       ((definescore(Oracle,relevance)),(definescore(Java,discrete)))
                    ,OR,ADD
            )),T,T)',1)>0 order by score(1) desc;

Query B:

    select /*+ DOMAIN_INDEX_SORT */ id, score(1) as ORAVG from docs where contains (txt ,'ctxfiltercache((DEFINEMERGE
            (       ((definescore(Oracle,relevance)),(definescore(Java,discrete)))
                    ,OR,AVG
            )),T,T)',1)>0 order by score(1) desc;

#### Notes

The query filter cache is an index level storage preference.

The storage preference for the query filter cache can be set at partition level only if this is also set at index level. If a filter cache preference is set at partition level without any filter cache preference being set at index level, then an error is thrown as follows: "Illegal syntax for index, preference, source or section name."

Note that `CTXFILTERCACHE` is not utilized with:

- `INPATH`/`HASPATH` queries

- First query after `syncindex` for `NDATA` and `SDATA`

When `topN` is `FALSE`, the `CTXFILTERCACHE` operator can be either a top-level operator or a child of the following operators:

- `AND`

- `ACCUM`

- `NOT`

- `OR`

- `THRESHOLD` (left side operand only)

- `WEIGHT` (left side operand only)

When `topN` is `TRUE`:

- The `ctxfiltercache` operator can be either a top-level operator or a child of the following operators:

  - `AND`

  - `THRESHOLD` (left side operand only)

  - `WEIGHT` (left side operand only)

- TopN is enabled only when the `ctxfiltercache` operator is used with the order key ORDER BY SCORE(n) DESC and Oracle hint `DOMAIN_INDEX_SORT` for global index. Additionally, for a partitioned index, be sure to have partition pruning in your query. Otherwise, although topN is set to TRUE, normal mode will be used instead of topN mode.

**Note:**

The `ctxfiltercache` operator only supports a CONTEXT grammar query. This means that container queries like template queries are not supported.

If `ctxfiltercache` is used with a query template, then the following type of error will occur:

    ERROR at line 1:
    ORA-29902: error in executing ODCIIndexStart() routine
    ORA-20000: Oracle Text error:
    DRG-50900: text query parser error on line 1, column 8
    DRG-50905: invalid score threshold <textquery

An example of a query that results in this error is as follows:

    select score(1), id, txt from tdrbqfc45 where contains(txt, 'ctxfiltercache((<query><textquery>near2((a,b,c,d))
    </textquery><score datatype="FLOAT"/>
    </query>),true)', 1)>0 order by id;

To use `ctxfiltercache` you must specify a size for the query filter cache using the basic storage attribute `query_filter_cache_size`. The default size is `0`, which means that `ctxfiltercache` is disabled by default.

The view `ctx_filter_cache_statistics` provides various statistics about the query filter cache.

The query filter cache does not differentiate queries that only vary in how the score is computed. Score is never computed on the fly within the query filter cache. See "Cached Score Example" for an illustration of how this works.

#### Related Topics

"[CTX_FILTER_CACHE_STATISTICS](oracle-text-views.md)" for more information about the `ctx_filter_cache_statistics` view

"[BASIC_STORAGE](oracle-text-indexing-elements.md)" for more information about the `query_filter_cache_size` basic storage attribute

### 3.7 DEFINEMERGE

Use the `DEFINEMERGE` operator to define how the score of child nodes of the `AND` and `OR` should be merged.

The `DEFINEMERGE` operator can be used as operand(s) of any operators that allow `AND` or `OR` as operands. The score can be merged in three ways: picking the minimum value, picking the maximum value, or calculating the average score of all child nodes.

Use DEFINESCORE before using `DEFINEMERGE`.

#### Syntax

    DEFINEMERGE ( (  (text_query1), (text_query2), … )  , operator, merge_method )

| Syntax            | Description                                                                                             |
|:------------------|:--------------------------------------------------------------------------------------------------------|
| text_query1,2 ... | Defines the search criteria. These parameters can have any value that is valid for the AND/OR operator. |
| operator          | Defines the relationship between the two `text_query` parameters.                                       |
| merge_method      | Defines how the score of the text_query should be merged. Possible values: `MIN`, `MAX`, `AVG`, `ADD`   |

#### Example for DEFINEMERGE Operator

    'DEFINEMERGE (((dog , cat) , (blue or green)), AND, MIN )'

Queries for the expression "dog `ACCUM` cat" and "blue `OR` green," using the default scoring schemes and then using the minimum score of the two as the merged-score.

    'DEFINEMERGE( ((DEFINESCORE(dog, DISCRETE)) , (cat)), AND, MAX)'

Queries for the term "dog" using the `DISCRETE` scoring, and for the term "cat" using the default relevant scoring, and then using the maximum score of the two as the merged-score.

Example 3-1 DEFINEMERGE and text_query

The following examples show only the `text_query` part of a `CONTAINS` query:

    'DEFINEMERGE ( ((dog), (cat)), OR, AVG)'

Queries for the term "dog" or "cat," using the average relevance score of both terms as the merged score.

#### Related Topic

DEFINESCORE.

### 3.8 DEFINESCORE

Use the `DEFINESCORE` operator to define how a term or phrase, or a set of term equivalences will be scored. The definition of a scoring expression can consist of an arithmetic expression of predefined scoring components and numeric literals.

DEFINEMERGE can be used after `DEFINESCORE`.

#### Syntax

    DEFINESCORE (query_term, scoring_expression)

query_term
The query term or phrase. Expressions containing the following operators are also allowed:

| Operators  | Operators         |
|:-----------|:------------------|
| \-         | \-                |
| `ABOUT`    | `EQUIV(=)`        |
| `Fuzzy`    | `Soundex (!)`     |
| `Stem ($)` | `Wildcards (% _)` |
| `SDATA`    | `MDATA`           |

<!-- -->

scoring_expression
An arithmetic expression that describes how the `query_term` should be scored. This operand is a string that contains the following components:

- Arithmetic operators: `+ - * /`. The precedence is multiplication and division (\*, /) first before addition and subtraction (+, -).

- Grouping operators: `()`. Parentheses can be used to alter the precedence of the arithmetic operators.

- Absolute function: `ABS(n)` returns the absolute value of `n`; where `n` is any expression that returns a number.

- Logarithmic function: `LOG(n)` returns the base-10 logarithmic value of `n` ; where `n` is any expression that returns a number.

- Predefined scoring components: Each of the following scoring components returns a value of 0 - 100, depending on different criteria:

  | Name         | Description                                                                                                                                                                                                                                                                                         |
  |:-------------|:----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
  | `DISCRETE`   | If the term exists in the document, score = 100. Otherwise, score = 0.                                                                                                                                                                                                                              |
  | `OCCURRENCE` | Score based on the number of occurrences.                                                                                                                                                                                                                                                           |
  | `RELEVANCE`  | Score based on the document's relevance.                                                                                                                                                                                                                                                            |
  | `COMPLETION` | Score based on coverage. Documents will score higher if the ratio between the number of the matching terms and the number of all terms in the section (counting stop words) is higher. The `COMPLETION` scoring is only applicable when used with the `WITHIN` operator to search in zone sections. |
  | `IGNORE`     | Ignore the scoring of this term. This component should be used alone. Otherwise, the query will return a syntax error. If the scoring of the only term in the query is set to `IGNORE`, then all the matching documents should be returned with the same score of 100.                              |

**Note:**

For numeric literals, any number literal can be used that conforms to the SQL pattern of number literal, and is within the range of the double precision floating point (`-3.4e38` to `3.4e38`).

#### scoring_expression Syntax

    <Exp>   :=         <Exp> + <Term> | <Exp> - <Term> |  <Term>

    <Term>   :=         <Term> * <Factor> | <Term> / <Factor> | <Factor>

    <Factor> :=         <<NumericLiterals >>| DISCRETE | OCCURRENCE | RELEVANCE |
             COMPLETION | IGNORE |  ( <Exp> ) | -<Factor> | Abs(<Exp>) | Log(<Exp>)

#### Examples for DEFINESCORE Operator

    'DEFINESCORE (dog, OCCURRENCE)'

Queries for the word dog, and scores each document using the occurrence score. Returns the score as integer.

    'DEFINESCORE (Labradors are big dog, RELEVANCE)'

Queries for the phrase Labradors are big dogs, and scores each document using the relevance score.

    'cat and DEFINESCORE (dog, IGNORE)'

Queries for the words dog and cat, using only the default relevance score of cat as the overall score of the document. Returns the score as integer.

    'DEFINESCORE (dog, IGNORE)'

Queries for the word dog, and returns all documents with the word dog. The result is the same as if all documents get a score of 100. Returns the score as integer.

    'DEFINESCORE (dog, ABS (100-RELEVANCE))'

Queries for the word dog, and scores each document using the absolute value of 100 minus the relevance score. Returns the score as integer.

    'cat and DEFINESCORE (dog, RELEVANCE*5 - OCCURRENCE)'

Returns a syntax error: Two predefined components are used.

When `DEFINESCORE` is used with query templates, the `scoring_expression` overrides the values specified by the template. The following example queries for "dog" and "cat," scores "cat" using `OCCURRENCE``(COUNT)` and scores "dog" based on `RELEVANCE`.

    <query>
          <textquery grammar="CONTEXT" lang="english">
                     DEFINESCORE(dog, RELEVANCE) and  cat
          </textquery>
          <score datatype="INTEGER" algorithm="COUNT"/>
    </query>

#### Limitations

- If the `ABOUT` operator is used in `query_term`, the `OCCURRENCE` and `COMPLETION` scoring will not be applicable. If used, the query will return a syntax error.

- The `IGNORE` score cannot be used as right hand of the minus operator. If used, then a syntax error will occur.

- The `COMPLETION` score is only applicable if the `DEFINESCORE` is used with a `WITHIN` operator to search in zone sections, for example:

      'DEFINESCORE (dog, COMPLETION) within zonesection'

  otherwise, the query will return a syntax error.

- For the left hand operand of `WITHIN`:

  - All nodes must use the same predefined-scoring component. (If not specified, then the predefined scoring is `RELEVANCE`.)

  - If the nodes use `DISCRETE` or `COMPLETION`, then only the `AND` and `OR` operator is allowed as the left hand children of `WITHIN`.

  - If the nodes use `DISCRETE` or `COMPLETION`, then `WITHIN` will use the max score of all section instances as the score.

  - If the nodes use `RELEVANCE` or `OCCURRENCE`, then `WITHIN` will use the summation of the score of all section instances as the score.

- Only one predefined scoring component can be used in the `scoring_expression` at one time. If more than one predefined scoring component is used, then a syntax error will occur.

**See Also:**

[Oracle Database SQL Language Reference](../sqlrf/index.md)

#### Notes

- The `DEFINESCORE` operator, the absolute function, the logarithmic function, and the predefined scoring components are case-insensitive.

- The `query_term` and the `scoring_expression` parameters are mandatory.

- The final score of the `DEFINESCORE` operator will be truncated to be in the 0 – 100 range. If the data type is `INTEGER`, then the score is rounded up.

- The intermediate data type of the scoring value is a double precision float. As a result, the value is limited to be in the `-3.4e38` to `3.4e38` range. If the intermediate scoring of any document exceeds the value, then the score will be truncated. If an integer scoring is required, then the score will always be rounded up after the score is calculated.

- The `DEFINESCORE` operator can be used as an operand of the following operators:

  - AND

  - NOT

  - INPATH

  - THRESHOLD

  - WITHIN

  - SQE

  - OR

  - DEFINEMERGE

  - MINUS

  - WEIGHT

  - ACCUM

  For example, the following statement is valid:

      DEFINESCORE('dog', OCCURRENCE) AND DEFINESCORE('cat', RELEVANCE)

  Queries for the term "dog" using occurrence scoring, and the term "cat" using relevance scoring.

- If `DEFINESCORE` is used as a parameter of other operators, then an error will be returned. For example, the following example returns an error:

      SYN(DEFINESCORE('cat', OCCURRENCE))

- When used with query templates, the `scoring_expression` overrides the values specified by the template. For example,

      <query>
          <textquery grammar="CONTEXT" lang="english">
              DEFINESCORE(dog, RELEVANCE) and  cat
          </textquery>
          <score datatype="INTEGER" algorithm="COUNT"/>
      </query>

  Queries for "dog" and "cat", scores "cat" using `OCCURRENCE(COUNT)`, and scores "dog" based on `RELEVANCE`.

#### Related Topic

DEFINEMERGE.

### 3.9 EQUIValence (=)

Use the `EQUIV` operator to specify an acceptable substitution for a word in a query.

#### Syntax

| Syntax                           | Description                                                                                                                     |
|:---------------------------------|:--------------------------------------------------------------------------------------------------------------------------------|
| term1=term2<br>term1 equiv term2 | Specifies that `term2` is an acceptable substitution for `term1`. Score calculated as the sum of all occurrences of both terms. |

#### Example for EQUIV Operator

The following example returns all documents that contain either the phrase alsatians are big dogs or labradors are big dogs:

    'labradors=alsatians are big dogs'

#### Operator Precedence

The `EQUIV` operator has higher precedence than all other operators except the expansion operators (fuzzy, soundex, stem).

### 3.10 Fuzzy

Use the `fuzzy` operator to expand queries to include words that are spelled similarly to the specified term. This type of expansion is helpful for finding more accurate results when there are frequent misspellings in your document set.

The `fuzzy` syntax enables you to rank the result set so that documents that contain words with high similarity to the query word are scored higher than documents with lower similarity. You can also limit the number of expanded terms.

Unlike stem expansion, the number of words generated by a `fuzzy` expansion depends on what is in the index. Results can vary significantly according to the contents of the index.

#### Supported Languages

Oracle Text supports `fuzzy` definitions for English, French, German, Italian, Dutch, Spanish, Portuguese, Japanese, OCR, and auto-language detection.

#### Stopwords

If the `fuzzy` expansion returns a stopword, the stopword is not included in the query or highlighted by `CTX_DOC.HIGHLIGHT` or `CTX_DOC.MARKUP`.

#### Base-Letter Conversion

If base-letter conversion is enabled for a text column and the query expression contains a `fuzzy` operator, Oracle Text operates on the base-letter form of the query.

#### Syntax

    fuzzy(term, score, numresults, weight)

| Parameter  | Description                                                                                                                                                                                                   |
|:-----------|:--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| term       | Specify the word on which to perform the `fuzzy` expansion. Oracle Text expands `term` to include words only in the index. The word needs to be at least 3 characters for the `fuzzy` operator to process it. |
| score      | Specify a similarity score. Terms in the expansion that score below this number are discarded. Use a number between 1 and 80. The default is 60.                                                              |
| numresults | Specify the maximum number of terms to use in the expansion of `term`. Use a number between 1 and 5000. The default is 100.                                                                                   |
| weight     | Specify `WEIGHT` or `W` for the results to be weighted according to their similarity scores.<br>Specify `NOWEIGHT` or `N` for no weighting of results.                                                        |

#### Examples for Fuzzy Operator

Consider the `CONTAINS` query:

    ...CONTAINS(TEXT, 'fuzzy(government, 70, 6, weight)', 1) > 0;

This query expands to the first six `fuzzy` variations of government in the index that have a similarity score over 70.

In addition, documents in the result set are weighted according to their similarity to government. Documents containing words most similar to government receive the highest score.

Skip unnecessary parameters using the appropriate number of commas. For example:

    'fuzzy(government,,,weight)'

#### Backward Compatibility Syntax

The old `fuzzy` syntax from previous releases is still supported. This syntax is as follows:

| Parameter | Description                                                                                                                                                        |
|:----------|:-------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| ?term     | Expands `term` to include all terms with similar spellings as the specified term. `Term` needs to be at least 3 characters for the `fuzzy` operator to process it. |

### 3.11 HASPATH

Use the `HASPATH` operator to find all `XML` documents that contain a specified section path. You can also use this operator to do section equality testing.

Your index must be created with the `PATH_SECTION_GROUP` for this operator to work.

#### Syntax

| Syntax             | Description                                                                                                                                                                                            |
|:-------------------|:-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| HASPATH(path)      | Searches an XML document set and returns a score of 100 for all documents where path exists. Separate parent and child paths with the / character. For example, you can specify A/B/C.<br>See example. |
| HASPATH(A="value") | Searches an XML document set and returns a score of 100 for all documents that have the element A with content value and only value.<br>See example.                                                   |

#### Using Special Characters with HASPATH and INPATH

The following rules govern the use of special characters with regard to both the `HASPATH` and `INPATH` operators:

- Left-brace ({) and right-brace (}) characters are not allowed inside `HASPATH` or `INPATH` expressions unless they are inside the equality operand enclosed by double quotes. So both '`HASPATH({/A/B})`' and '`HASPATH(/A/{B})`' will return errors. However, '`HASPATH(/A[B="{author}"])`' will be parsed correctly.

- With exception of the backslash (\\, special characters, such as dollar sign (\$), percent sign (%), underscore (\_), left brace ({), and right brace (}), when inside the equality operand enclosed by double or single quotes, have no special meaning. (That is, no stemming, wildcard expansion, or similar processing will be performed on them.) However, they are still subject to regular text lexing and will be translated to whitespace, with the exception of characters declared as printjoins. A backslash will still escape any character that immediately follows it.

  For example, if the hyphen (-) and the double quote character (") are defined as printjoins in a lexer preference, then:

  - The string B_TEXT inside `HASPATH(/A[B="B_TEXT")` will be lexed as the phrase B TEXT.

  - The string B-TEXT inside `HASPATH(/A[B="B-TEXT")` will be lexed as the word B-TEXT.

  - The string B'TEXT inside `HASPATH(/A[B="B'TEXT")` will be lexed as the word B"TEXT. You must use a backslash to escape the double quote between B and TEXT, or you will get a parsing error.

  - The string {B_TEXT} inside `HASPATH(/A[B="{B_TEXT}")` will be lexed as a phrase B TEXT.

#### Examples for HASPATH Operator

Path Testing

The query

    HASPATH(A/B/C)

finds and returns a score of 100 for the document

    <A><B><C>dog</C></B></A>

without the query having to reference dog at all.

Section Equality Testing

The query

    dog INPATH A

finds

    <A>dog</A>

but it also finds

    <A>dog park</A>

To limit the query to the term dog and nothing else, you can use a section equality test with the `HASPATH` operator. For example,

    HASPATH(A="dog")

finds and returns a score of 100 only for the first document, and not the second.

#### Limitations

Because of how XML section data is recorded, false matches might occur with XML sections that are completely empty as follows:

\<A\>\<B\>\<C\>\</C\>\</B\>\<D\>\<E\>\</E\>\</D\>\</A\>

A query of `HASPATH(A/B/E)` or `HASPATH(A/D/C)` falsely matches this document. This type of false matching can be avoided by inserting text between empty tags.

False matches might also occur when the document has empty elements but has values in attributes, as in the following example document:

    <Test>
    <Client id="1">
     <Info infoid="1"/>
    </Client>
    <Client id="2">
     <Info infoid="2"/>
    </Client>
    </Test>

When searching with the following query, the query returns the document shown in the example, which is a false match.

The following query was used to return the example document, which is a false match:

    SELECT main_detail_logging_id, t.xml_data.getstringval() xml_data FROM
    TEST_XMLTYPE t
    WHERE CONTAINS(t.xml_data,
    'HASPATH(/Test/Client[@id="1"]/Info[@infoid="2"])') > 0;

### 3.12 INPATH

Use the `INPATH` operator to do path searching in XML documents. This operator is like the `WITHIN` operator except that the right-hand side is a parentheses enclosed path, rather than a single section name.

Your index must be created with the `PATH_SECTION_GROUP` for the `INPATH` operator to work.

#### Syntax

The `INPATH` operator has the following syntax:

Top-Level Tag Searching

| Syntax                              | Description                                                        |
|:------------------------------------|:-------------------------------------------------------------------|
| term INPATH (/A)<br>term INPATH (A) | Returns documents that have term within the \<A\> and \</A\> tags. |

Any-Level Tag Searching

| Syntax            | Description                                                                                               |
|:------------------|:----------------------------------------------------------------------------------------------------------|
| term INPATH (//A) | Returns documents that have term in the \<A\> tag at any level. This query is the same as 'term WITHIN A' |

Direct Parentage Path Searching

| Syntax            | Description                                                                                                                                                                         |
|:------------------|:------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| term INPATH (A/B) | Returns documents where term appears in a B element which is a direct child of a top-level A element.<br>For example, a document containing<br>`<A><B>term</B></A>`<br>is returned. |

Single-Level Wildcard Searching

| Syntax               | Description                                                                                                                                                                                               |
|:---------------------|:----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| term INPATH (A/\*/B) | Returns documents where term appears in a B element which is a grandchild (two levels down) of a top-level A element.<br>For example a document containing<br>`<A><D><B>term</B></D></A>`<br>is returned. |

Multi-level Wildcard Searching

| Syntax                       | Description                                                                                                                                                 |
|:-----------------------------|:------------------------------------------------------------------------------------------------------------------------------------------------------------|
| term INPATH (A/\*/B/\*/\*/C) | Returns documents where term appears in a C element which is 3 levels down from a B element which is two levels down (grandchild) of a top-level A element. |

Any-Level Descendant Searching

| Syntax            | Description                                                                                                        |
|:------------------|:-------------------------------------------------------------------------------------------------------------------|
| term INPATH(A//B) | Returns documents where term appears in a B element which is some descendant (any level) of a top-level A element. |

Attribute Searching

| Syntax               | Description                                                                                                                        |
|:---------------------|:-----------------------------------------------------------------------------------------------------------------------------------|
| term INPATH (//A/@B) | Returns documents where term appears in the B attribute of an A element at any level. Attributes must be bound to a direct parent. |

Descendant/Attribute Existence Testing

| Syntax                  | Description                                                                                                                          |
|:------------------------|:-------------------------------------------------------------------------------------------------------------------------------------|
| term INPATH (A\[B\])    | Returns documents where term appears in a top-level A element which has a B element as a direct child.                               |
| term INPATH (A\[.//B\]) | Returns documents where term appears in a top-level A element which has a B element as a descendant at any level.                    |
| term INPATH (//A\[@B\]) | Finds documents where term appears in an A element at any level which has a B attribute. Attributes must be tied to a direct parent. |

Attribute Value Testing

| Syntax                           | Description                                                                                                       |
|:---------------------------------|:------------------------------------------------------------------------------------------------------------------|
| term INPATH (A\[@B = "value"\])  | Finds all documents where term appears in a top-level A element which has a B attribute whose value is value.     |
| term INPATH (A\[@B != "value"\]) | Finds all documents where term appears in a top-level A element which has a B attribute whose value is not value. |

Tag Value Testing

| Syntax                          | Description                                                                              |
|:--------------------------------|:-----------------------------------------------------------------------------------------|
| term INPATH (A\[B = "value"\])) | Returns documents where term appears in an A tag which has a B tag whose value is value. |

NOT Testing

| Syntax                    | Description                                                                                                        |
|:--------------------------|:-------------------------------------------------------------------------------------------------------------------|
| term INPATH (A\[NOT(B)\]) | Finds documents where term appears in a top-level A element which does not have a B element as an immediate child. |

AND and OR Testing

| Syntax                                | Description                                                                                                               |
|:--------------------------------------|:--------------------------------------------------------------------------------------------------------------------------|
| term INPATH (A\[B and C\])            | Finds documents where term appears in a top-level A element which has a B and a C element as an immediate child.          |
| term INPATH (A\[B and @C="value"\]\]) | Finds documents where term appears in a top-level A element which has a B element and a C attribute whose value is value. |
| term INPATH (A \[B OR C\])            | Finds documents where term appears in a top-level A element which has a B element or a C element.                         |

Combining Path and Node Tests

| Syntax                              | Description                                                                                                                                                                |
|:------------------------------------|:---------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| term INPATH (A\[@B = "value"\]/C/D) | Returns documents where term appears in aD element which is the child of a C element, which is the child of a top-level A element with a B attribute whose value is value. |

#### Nested INPATH

Nest the entire `INPATH` expression in another `INPATH` expression as follows:

    (dog INPATH (//A/B/C)) INPATH (D)

When you do so, the two `INPATH` paths are completely independent. The outer `INPATH` path does not change the context node of the inner `INPATH` path. For example:

    (dog INPATH (A)) INPATH (D)

never finds any documents, because the inner `INPATH` is looking for dog within the top-level tag A, and the outer `INPATH` constrains that to document with top-level tag D. A document can have only one top-level tag, so this expression never finds any documents.

#### Case-Sensitivity

Tags and attribute names in path searching are case-sensitive. That is,

    dog INPATH (A)

finds `<A>dog</A>` but does not find `dog`. Instead use

    dog INPATH (a)

#### Using Special Characters with INPATH

See "Using Special Characters with HASPATH and INPATH" for information on using special characters, such as the percent sign (%) or the backslash (\\, with `INPATH`.

#### Examples for INPATH Operator

Top-Level Tag Searching

To find all documents that contain the term dog in the top-level tag \<A\>:

    dog INPATH (/A)

or

    dog INPATH(A)

Any-Level Tag Searching

To find all documents that contain the term dog in the \<A\> tag at any level:

    dog INPATH(//A)

This query finds the following documents:

    <A>dog</A>

and

    <C><B><A>dog</A></B></C>

Direct Parentage Searching

To find all documents that contain the term dog in a B element that is a direct child of a top-level A element:

    dog INPATH(A/B)

This query finds the following XML document:

    <A><B>My dog is friendly.</B><A>

but does not find:

    <C><B>My dog is friendly.</B></C>

Tag Value Testing

You can test the value of tags. For example, the query:

    dog INPATH(A[B="dog"])

Finds the following document:

    <A><B>dog</B></A>

But does not find:

    <A><B>My dog is friendly.</B></A>

Attribute Searching

You can search the content of attributes. For example, the query:

    dog INPATH(//A/@B)

Finds the document

    <C><A  B="snoop dog"> </A> </C>

Attribute Value Testing

You can test the value of attributes. For example, the query

    California INPATH (//A[@B = "home address"])

Finds the document:

    <A B="home address">San Francisco, California, USA</A>

But does not find:

    <A B="work address">San Francisco, California, USA</A>

Path Testing

You can test if a path exists with the `HASPATH` operator. For example, the query:

    HASPATH(A/B/C)

finds and returns a score of 100 for the document

    <A><B><C>dog</C></B></A>

without the query having to reference dog at all.

#### Limitations

Testing for Equality

The following is an example of an `INPATH` equality test.

    dog INPATH (A[@B = "foo"])

The following limitations apply for these expressions:

- Only equality and inequality are supported. Range operators and functions are not supported.

- The left hand side of the equality must be an attribute. Tags and literals here are not enabled.

- The right hand side of the equality must be a literal. Tags and attributes here are not allowed.

- The test for equality depends on your lexer settings. With the default settings, the query

      dog INPATH (A[@B= "pot of gold"])

  matches the following sections:

      <A B="POT OF GOLD">dog</A>

  and

      <A B="pot of gold">dog</A>

  because lexer is case-insensitive by default.

      <A B="POT IS GOLD">dog</A>

  because of and is are default stopwords in English, and a stopword matches any stopword word.

      <A B="POT_OF_GOLD">dog</A>

  because the underscore character is not a join character by default.

### 3.13 MDATA

Use the `MDATA` operator to query documents that contain `MDATA` sections. `MDATA` sections are metadata that have been added to documents to speed up mixed querying.

`MDATA` queries are treated exactly as literals. For example, with the query:

    MDATA(price, $1.24)

the \$ is not interpreted as a stem operator, nor is the . (period) transformed into whitespace. A right (close) parenthesis terminates the `MDATA` operator, so that `MDATA` values that have close parentheses cannot be searched.

#### Syntax

    MDATA(sectionname, value)

sectionname
The name of the `MDATA` section(s) to search. `MDATA` will also search `DATE` or numerical equality if the `sectionname` parameter is mapped to a `FILTER` `BY` column of `DATE` or some numerical type.

value
The value of the `MDATA` section. For example, if an `MDATA` section called `Booktype` has been created, it might have a value of paperback.

For `MDATA` operator on `MDATA` sections that are mapped to a `DATE` `FILTER` `BY` column, the `MDATA` value must follow the Date format: `YYYY-MM-DD HH24:MI:SS`. Otherwise, the expected rows will not be returned. If the time component is omitted, it will default to `00:00:00`, according to SQL semantics.

#### Example for MDATA Operator

Suppose you want to query for books written by the writer Nigella Lawson that contain the word summer. Assuming that an `MDATA` section called `AUTHOR` has been declared, you can query as follows:

    SELECT id FROM idx_docs
      WHERE CONTAINS(text, 'summer AND MDATA(author, Nigella Lawson)')>0

This query will only be successful if an `AUTHOR` tag has the exact value Nigella Lawson (after simplified tokenization). Nigella or Ms. Nigella Lawson will not work.

#### Notes

`MDATA` query values ignore stopwords.

The `MDATA` operator returns an unlimited number of results or 0, depending on whether the document is a match. You can set the maximum.

The `MDATA` operator is not supported for `CTXCAT` and `CTXRULE` indexes.

Table 3-2 shows how `MDATA` interacts with some other query operators:

Table 3-2 MDATA and Other Query Operators

| Operator                | Example                                                       | Allowed?                                                                      |
|:------------------------|:--------------------------------------------------------------|:------------------------------------------------------------------------------|
| AND                     | dog & MDATA(a, b)                                             | yes                                                                           |
| OR                      | dog \| MDATA(a, b)                                            | yes                                                                           |
| NOT                     | dog ~ MDATA(a, b)                                             | yes                                                                           |
| MINUS                   | dog - MDATA(a, b)                                             | yes                                                                           |
| ACCUM                   | dog , MDATA(a, b)                                             | yes                                                                           |
| PHRASE                  | MDATA(a, b) dog                                               | no                                                                            |
| NEAR                    | MDATA(a, b) ; dog                                             | no                                                                            |
| WITHIN, HASPATH, INPATH | MDATA(a, b) WITHIN c                                          | no                                                                            |
| Thesaurus               | MDATA(a, SYN(b))                                              | no                                                                            |
| expansion               | MDATA(a, \$b)<br>MDATA(a, b%)<br>MDATA(a, !b)<br>MDATA(a, ?b) | no (syntactically allowed, but the inner operator is treated as literal text) |
| ABOUT                   | ABOUT(MDATA(a,b))<br>MDATA(ABOUT(a))                          | no (syntactically allowed, but the inner operator is treated as literal text) |

When `MDATA` sections repeat, each instance is a separate and independent value. For instance, the document

    <AUTHOR>Terry Pratchett</AUTHOR><AUTHOR>Douglas Adams</AUTHOR>

can be found with any of the following queries:

    MDATA(author, Terry Pratchett)
    MDATA(author, Douglas Adams)
    MDATA(author, Terry Pratchett) and MDATA(author, Douglas Adams)

but not any of the following:

    MDATA(author, Terry Pratchett Douglas Adams)
    MDATA(author, Terry Pratchett & Douglas Adams)
    MDATA(author, Pratchett Douglas)

#### Related Topics

"[ADD_MDATA](CTX_DDL-package.md)"

"[ADD_MDATA_SECTION](CTX_DDL-package.md)"

**See Also:**

[Oracle Text Application Developer's Guide](../ccapp/searching-document-sections-in-oracle-text.md) for information about section searching

### 3.14 MINUS (-)

Use the `MINUS` operator to lower the score of documents that contain unwanted noise terms. `MINUS` is useful when you want to search for documents that contain one query term but want the presence of a second term to cause a document to be ranked lower.

#### Syntax

| Syntax                           | Description                                                                                                                                                        |
|:---------------------------------|:-------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| term1-term2<br>term1 minus term2 | Returns documents that contain term1. Calculates score by subtracting the score of term2 from the score of term1. Only documents with positive score are returned. |

#### Example for MINUS Operator

Suppose a query on the term cars always returned high scoring documents about Ford cars. You can lower the scoring of the Ford documents by using the expression:

    'cars - Ford'

In essence, this expression returns documents that contain the term cars and possibly Ford. However, the score for a returned document is the score of cars minus the score of Ford.

#### Related Topics

"NOT (~)"

### 3.15 MNOT

The Mild Not (`MNOT`) operator is similar to the `NOT` and `MINUS` operators. The Mild Not operator returns hits where the the left child is not contained by the right child. Both children can only be `TERM` or `PHRASE` nodes.

The semantics can be illustrated with a query of "term1 mnot term1 term2", where the hits for "term1 term2" will be filtered out. For example:

- A document with only term1 will be returned, with score unchanged.

- A document with only term1 term2 will not be returned.

- A document with term1 term1 term2 will be returned, but the score will be calculated using just the first term1 hit.

The behavior described in the third bullet is different from the behavior of `NOT`, which does not return this type of document.

The `MNOT` operator is more specific than the `MINUS` operator, in that the left child must be contained by the right child. If it is not, the Mild Not operator ignores the right child. Also, for Mild Not, the right child is a true filter, that is, it does not simply subtract the scores of left child and right child.

The `MNOT` operator has precedence lower than `NOT` and higher than `WITHIN`.

#### Syntax

| Syntax                 | Description                                                                        |
|:-----------------------|:-----------------------------------------------------------------------------------|
| term1 mnot term1 term2 | Returns docs that contain term1 unless it is part of the phrase term1 term2.       |
| term1 mnot term2       | Returns all documents that contain term1. It will be the same query as just term1. |

#### Example for MNOT Operator

The children of the `MNOT` operator must be a `TERM` or `PHRASE`.

    SELECT * FROM docs
    WHERE CONTAINS(txt, 'term1 mnot term1 term2') >0

#### Related Topic

"NOT (~)"

### 3.16 Narrower Term (NT, NTG, NTP, NTI)

Use the narrower term operators (`NT`, `NTG`, `NTP`, `NTI`) to expand a query to include all the terms that have been defined in a thesaurus as the narrower or lower level terms for a specified term.

They can also expand the query to include all of the narrower terms for each narrower term, and so on down through the thesaurus hierarchy.

#### Syntax

| Syntax                                      | Description                                                                                                           |
|:--------------------------------------------|:----------------------------------------------------------------------------------------------------------------------|
| NT(term\[(qualifier)\]\[,level\]\[,thes\])  | Expands a query to include all the lower level terms defined in the thesaurus as narrower terms for `term`.           |
| NTG(term\[(qualifier)\]\[,level\]\[,thes\]) | Expands a query to include all the lower level terms defined in the thesaurus as narrower generic terms for `term`.   |
| NTP(term\[(qualifier)\]\[,level\]\[,thes\]) | Expands a query to include all the lower level terms defined in the thesaurus as narrower partitive terms for `term`. |
| NTI(term\[(qualifier)\]\[,level\]\[,thes\]) | Expands a query to include all the lower level terms defined in the thesaurus as narrower instance terms for `term`.  |

term
Specify the operand for the narrower term operator. `term` is expanded to include the narrower term entries defined for the term in the thesaurus specified by `thes`. The number of narrower terms included in the expansion is determined by the value for `level`. You cannot specify expansion operators in the `term` argument.

qualifier
Specify a qualifier for `term`, if `term` is a homograph (word or phrase with multiple meanings, but the same spelling) that appears in two or more nodes in the same hierarchy branch of `thes`.

If a qualifier is not specified for a homograph in a narrower term query, the query expands to include all of the narrower terms of all homographic terms.

level
Specify the number of levels traversed in the thesaurus hierarchy to return the narrower terms for the specified term. For example, a level of 1 in an `NT` query returns all the narrower term entries, if any exist, for the specified term. A level of 2 returns all the narrower term entries for the specified term, as well as all the narrower term entries, if any exist, for each narrower term.

The level argument is optional and has a default value of one (1). Zero or negative values for the level argument return only the original query term.

thes
Specify the name of the thesaurus used to return the expansions for the specified term. The `thes` argument is optional and has a default value of `DEFAULT`. A thesaurus named `DEFAULT` must exist in the thesaurus tables if you use this default value.

**Note:**

If you specify `thes`, then you must also specify `level`.

#### Examples for Narrower Term Operators

The following query returns all documents that contain either the term cat or any of the `NT` terms defined for cat in the `DEFAULT` thesaurus:

    'NT(cat)'

If you specify a thesaurus name, then you must also specify `level` as in:

    'NT(cat, 2, mythes)'

The following query returns all documents that contain either fairy tale or any of the narrower instance terms for fairy tale as defined in the `DEFAULT` thesaurus:

    'NTI(fairy tale)'

That is, if the terms cinderella and little mermaid are defined as narrower term instances for fairy tale, Oracle Text returns documents that contain fairy tale, cinderella, or little mermaid.

#### Notes

Each hierarchy in a thesaurus represents a distinct, separate branch, corresponding to the four narrower term operators. In a narrower term query, Oracle Text only expands the query using the branch corresponding to the specified narrower term operator.

#### Related Topic

CTX_THES.[NT](CTX_THES-package.md) in [CTX_THES Package](CTX_THES-package.md) for more information on browsing the narrower terms in your thesaurus

### 3.17 NDATA

Use the `NDATA` operator to find matches that are spelled in a similar way or where rearranging the terms of the specified phrase is useful.

It is helpful for finding more accurate results when there are frequent misspellings (or inaccurate orderings) of name data in the document set. This operator can be used only on defined `NDATA` sections. The `NDATA` syntax enables you to rank the result set so that documents that contain words with high orthographic similarity are scored higher than documents with lower similarity.

#### Normalization

A lexer does not process `NDATA` query phrases. Users can, however, set base letter and alternate spelling attributes for a particular section group containing `NDATA` sections. Query case is normalized and non-character data (except for white space) is removed (for example, numerical or punctuation).

#### Syntax

    ndata(sectionname, phrase [,order][,proximity][,threshold])

| Parameter Name | Default Value | Parameter Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    |
|:---------------|:--------------|:-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `sectionname`  |               | Specify the name of a defined `NDATA` sections to query (that is, `section_name`)                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                        |
| `phrase`       |               | Specify the phrase for the name data query.<br>The phrase parameter can be a single word or a phrase, or a string of words in free text format.<br>The score returned is a relevant score.<br>Oracle Text ignores any query operators that are included in `phrase`.<br>The phrase should be a minimum of two characters in length and should not exceed 4000 characters in length.                                                                                                                                                                                                      |
| `order`        | `NOORDER`     | Specify whether individual tokens (terms) in a query should be matched in-order or in any order. The order parameter provides a primary filter for matching candidate documents.<br>`ORDER` or `O` - The query terms are matched in-order.<br>`NOORDER` o `N` \[DEFAULT\] - The query terms are matched in any order.                                                                                                                                                                                                                                                                    |
| `proximity`    | `NOPROXIMITY` | Specify whether the proximity of terms should influence the similarity score of candidate matches. That is, if the proximity parameter is enabled, non-matching additional terms between matching terms reduces the similarity score of candidate matches.<br>`PROXIMITY` or `P` - The similarity score influenced by the proximity of query terms in candidate matches.<br>`NOPROXIMITY` or `N` \[DEFAULT\] - The similarity score is not influenced by the proximity of query terms in candidate matches.                                                                              |
| `threshold`    | `20`          | Starting with Oracle Database 12c Release 2 (12.2), you can provide a threshold value as part of the NDATA operator. Specify a threshold value for percentage of matching grams. The section values containing low percentage of matching grams are ignored. If the threshold value is 20, sections with less than 20% of matching grams are ignored. If this value is lowered, fewer sections are ignored and this leads to a better recall. This threshold value promotes recall over precision as the value is lowered. For example:<br>`NDATA(author, LAST First, x, proximity, 10)` |

#### Examples for NDATA Operator

An `NDATA` query on an indexed surname section name that matches terms in the query phrase in any order without influencing the similarity score by the proximity of the jones and smith terms has the form:

    SELECT entryid, SCORE(1) FROM people WHERE
    CONTAINS(idx_column, 'NDATA(surname, jones smith)',1)>0;

An `NDATA` query on an indexed surname section name that matches terms in the query phrase in any order and in which similarity scores are influenced by the proximity of the jones and smith terms has the form:

    SELECT entryid, SCORE(1) FROM people WHERE
    CONTAINS(idx_column, 'NDATA(surname, jones smith,,proximity)',1)>0;

An `NDATA` query on an indexed surname section name that matches terms in the query phrase in-order without influencing the similarity score by the proximity of the jones and smith terms has the form:

    SELECT entryid, SCORE(1) FROM people WHERE
    CONTAINS(idx_column, 'NDATA(surname, jones smith, order)',1)>0;

An `NDATA` query on an indexed surname section name that matches terms in the query phrase in-order and in which similarity scores are influenced by the proximity of the jones and smith terms has the form:

    SELECT entryid, SCORE(1) FROM people WHERE
    CONTAINS(idx_column, 'NDATA(surname, jones smith, order, proximity)',1)>0;

#### Notes

The `NDATA` query operator does not provide offset information. As such, it cannot be used as a child of `WITHIN`, `NEAR(;)`, or `EQUIV(=)`, and `NDATA` sections are ignored by `CTX_DOC.HIGHLIGHT`, `CTX_DOC.SNIPPET`, and `CTX_DOC.MARKUP`.

The `NDATA` operator is not supported in the `CTXCAT` grammar. You can use it with other operators, including `OR` and query templates. You cannot use other query operators inside the `NDATA` operator.

A use case of the `NDATA` operator may involve finding a particular entry based on an approximate spelling of a person's full-name and an estimated date-of-birth. Supposing the entries' date-of-births are stored as an `SDATA` section, user-defined scoring's alternate scoring template can be used to combine the scores of the full-name's `NDATA` section data and the date-of-birth's `SDATA` section data.

The name john smith is queried for the section specified by the fullname `section_name`. Altering the `NDATA` operator's score based on the closeness of the `SDATA` section's date-of-birth to the date 08-NOV-2012 modifies the ranking of matching documents as follows:

    <query>
       <textquery grammar="CONTEXT" lang="english">
           NDATA(fullname, john smith)
       </textquery>
       <score algorithm="COUNT" normalization_expr =
           "doc_score-(DATE(8-NOV-2012)-sdata:dob)"/>
    </query>

#### Restrictions

The `NDATA` query operator does not work with [CTX_DOC Package](CTX_DOC-package.md) procedures. Attempting to use NDATA with CTX_DOC procedures will return an error stating that this is not supported.

### 3.18 NEAR (;)

Use the `NEAR` operator to return a score based on the proximity of two or more query terms.

Oracle Text returns higher scores for terms closer together and lower scores for terms farther apart in a document. If a word or term appears more than once in a `NEAR` query, then the word must appear more than once in the document in order to match.

**Note:**

The `NEAR` operator works with only word queries. You cannot use `NEAR` in `ABOUT` queries.

#### Syntax

    NEAR((word1,word2,...,wordn) [, max_span [, order [, maxreqd]]])

Backward compatibility syntax:

    word1;word2

word1-n
Specify the terms in the query separated by commas. The query terms can be single words or phrases and may make use of other query operators (see "NEAR with Other Operators").

max_span
Optionally specify the number of words separating the start and end words of a clump. The default is 100. Oracle Text returns an error if you specify a number greater than 100.

A clump is the smallest group of words in which all query terms occur. All clumps begin and end with a query term.

For near queries with two terms, `max_span` is the maximum distance allowed between the two terms. For example, if the document contains “The cat sat on the dog” then you can find cat within 3 words of dog by using the following query:

    'near((dog, cat, 3)'

If the document contains “The cat and the rabbit sat on the dog” then you can find cat, dog, and rabbit within 6 words by using the following query:

    'near((cat, dog, rabbit), 6)'

**Note:**

The search term rabbit is still included in the `max_span` calculation. If you specify a `max_span` of 5 then you cannot find rabbit. Stopwords are also included in the span calculation.

order
Specify `TRUE` for Oracle Text to search for terms in the order you specify. The default is `FALSE`.

For example, to search for the words monday, tuesday, and wednesday in that order with a maximum clump size of 20, enter the following query:

    'near((monday, tuesday, wednesday), 20, TRUE)'

**Note:**

To specify `order`, then you must always specify a number for `max_span`.

Oracle Text might return different scores for the same document when you use identical query expressions that have the `order` flag set differently. For example, Oracle Text might return different scores for the same document when you enter the following queries:

    'near((dog, cat), 50, FALSE)'
    'near((dog, cat), 50, TRUE)'

maxreqd
Specify the number of terms that must be near each other resulting in a match. You must specify a number greater than `1`. If the number of terms that must be near each other for a match is not specified, all terms must match. For example, the following query matches documents that contain clusters of words pertaining to fish:

`'near((fish, shark, ocean, scales, fishing), 10, FALSE, 3)'`

Here, only three of the query terms must be within a distance of 10 from each other for a match.

#### NEAR Scoring

The scoring for the `NEAR` operator combines frequency of the terms with proximity of terms. For each document that satisfies the query, Oracle Text returns a score between 1 and 100 that is proportional to the number of clumps in the document and inversely proportional to the average size of the clumps. This means many small clumps in a document result in higher scores, because small clumps imply closeness of terms.

The number of terms in a query also affects score. Queries with many terms, such as seven, generally need fewer clumps in a document to score 100 than do queries with few terms, such as two.

A clump is the smallest group of words in which all query terms occur. All clumps begin and end with a query term. Define clump size with the `max_span`parameter, as described in this section.

The size of a clump does not include the query terms themselves. So for the query `NEAR((DOG, CAT), 1)`, dog cat will be a match, and dog ate cat will be a match, but dog sat on cat will not be a match.

#### NEAR with Other Operators

You can use the `NEAR` operator with other operators such as `AND` and `OR`. Scores are calculated in the regular way.

For example, to find all documents that contain the terms tiger, lion, and cheetah where the terms lion and tiger are within 10 words of each other, enter the following query:

    'near((lion, tiger), 10) AND cheetah'

The score returned for each document is the lower score of the near operator and the term cheetah.

You can also use the equivalence operator to substitute a single term in a near query:

    'near((stock crash, Japan=Korea), 20)'

This query asks for all documents that contain the phrase stock crash within twenty words of Japan or Korea.

The following `NEAR` syntax is now valid:

    SELECT * FROM docs WHERE CONTAINS(txt, 'near((aterm1 aterm2 ... atermI
    OR bterm1 bterm2 ... btermJ
    OR cterm1 cterm2 ... ctermK, dterm))') >0

There can be any number of `OR`s in a given `NEAR` child, and the `OR` can appear in any of the `NEAR` children.

The `NEAR` within `NEAR` feature allows users to use nested proximity queries. Starting with Oracle Database 12c Release 2 (12.2), the distance between phrases is measured from the closest words in the phrases. For example, if the document contains the phrases \` Lorem ipsum dolor sit amet’ and \` Sed ut perspiciatis unde omnis’, rather than measuring the distance of these two phrases as the distance between \`Lorem’ and \`Sed’, the first two words in the phrases, the distance is measured from \`amet’ and ‘Sed’. The distance between phrases is the so-called Hausdorff measure.

    SELECT * FROM docs
    WHERE CONTAINS(txt, 'near((near((term1, term2),5), term3), 100)')>0

This query returns documents where `term1` and `term2` are near within a 5 token window, and the phrase containing `term1` and `term2` is within a 100 token window from `term3`. The distance between `term3` and the phrase containing `term1` and `term2` is computed based on the Hausdorff measure.

Mixing the semicolon and `NEAR` syntax is not supported and throws an error. That is, the queries `"near((a;b,c),3)" or "near((a,b));c"` will be disallowed.

The following operators also work with `NEAR` and `;` :

- `EQUIV`

- All expansion operators that produce words, phrases, or `EQUIV`. These include:

  - soundex

  - fuzzy

  - wildcards

  - stem

#### Backward Compatibility NEAR Syntax

You can write near queries using the syntax of previous Oracle Text releases. However, in a nested NEAR query, the semicolon operator cannot be used as the inner NEAR. That is, the query `'near(((a;d),f),3)'` produces a syntax error. The semicolon operator can be used as the outermost NEAR in a nested NEAR query.

For example, to find all documents where lion occurs near tiger, write:

    'lion near tiger'

or with the semi-colon as follows:

    'lion;tiger'

This query is equivalent to the following query:

    'near((lion, tiger), 100, FALSE)'

**Note:**

Only the syntax of the `NEAR` operator is backward compatible. In the example, the score returned is calculated using the clump method as described in this section.

#### Highlighting with the NEAR Operator

When you use highlighting and your query contains the `near` operator, all occurrences of all terms in the query that satisfy the proximity requirements are highlighted. Highlighted terms can be single words or phrases.

For example, assume a document contains the following text:

    Chocolate and vanilla are my favorite ice cream flavors.  I like chocolate served
    in a waffle cone, and vanilla served in a cup with caramel syrup.

If the query is near((chocolate, vanilla)), 100, FALSE), the following is highlighted:

    <<Chocolate>> and <<vanilla>> are my favorite ice cream flavors.  I like
    <<chocolate>> served in a waffle cone, and <<vanilla>> served in a cup with
    caramel syrup.

However, if the query is near((chocolate, vanilla)), 4, FALSE), only the following is highlighted:

    <<Chocolate>> and <<vanilla>> are my favorite ice cream flavors.  I like
    chocolate served in a waffle cone, and vanilla served in a cup with caramel syrup.

**See Also:**

[CTX_DOC Package](CTX_DOC-package.md) for more information about the procedures for highlighting

#### Section Searching and NEAR

Use the `NEAR` operator with the `WITHIN` operator for section searching as follows:

    'near((dog, cat), 10) WITHIN Headings'

When evaluating expressions such as these, Oracle Text looks for clumps that lie entirely within the given section.

In this example, only those clumps that contain dog and cat that lie entirely within the section Headings are counted. That is, if the term dog lies within Headings and the term cat lies five words from dog, but outside of Headings, this pair of words does not satisfy the expression and is not counted.

### 3.19 NEAR2

Use the `NEAR2` operator to perform position–based scoring and length normalization to help improve relevancy.

The `NEAR2` operator divides a document into segments based on the given query. Then, it classifies each segment based on the primary features and scores them based on the secondary features. The primary features that are used are as follows:

- Phrase Hits

- Partial Phrase Hits

- Ordered Near Hits

- Unordered Near Hits

- AND Hits

The secondary features are as follows:

- Excess Span

- Start Position

- Longest Partial Phrase

#### Syntax

    NEAR2((word1, word2,...,wordn),max_span, phrase_weight, partial_phrase_weight, ordered_near_weight, unordered_near_weight, and_weight)

All or none of the weights must be provided. When the weights are provided, the `NEAR2` operator works in the weighted-average mode. The weights are integers between 0 and 10.

word1-n
Specify the terms in the query separated by commas. The query terms can be single words or phrases and can use other query operators (see "NEAR with Other Operators"). Only the word list is mandatory.

max_span
Optionally, specify the size of the biggest clump. The default is 50. Oracle Text returns an error if you specify a number greater than 50.

A clump is the smallest group of words in which all query terms occur. All clumps begin and end with a query term.

For near queries with two terms, `max_span` is the maximum distance allowed between the two terms. For example, to query on dog and cat where dog is within 6 words of cat, enter the following query:

    'near((dog, cat), 6)'

phrase_weight
Determine the weight of the phrase primary feature when in weighted-average mode. This is a qualitative weight, which is mapped to an internal weight.

partial_phrase_weight
Determine the weight of the partial phrase primary feature when in weighted-average mode. This is a qualitative weight.

ordered_near_weight
Determine the weight of the ordered near primary feature when in weighted-average mode. This is a qualitative weight.

unordered_near_weight
Determine the weight of the unordered near primary feature when in weighted-average mode. This is a qualitative weight.

and_weight
Determine the weight of the AND primary feature when in weighted average mode. This is a qualitative weight.

**Related Topics**

- [Oracle Text Application Developer's Guide](../ccapp/working-with-CONTEXT-and-CTXCAT-grammars-in-oracle-text.md)

### 3.20 NOT (~)

Use the `NOT` operator to search for documents that contain one query term and not another.

#### Syntax

| Syntax                         | Description                                         |
|:-------------------------------|:----------------------------------------------------|
| term1~term2<br>term1 not term2 | Returns documents that contain term1 and not term2. |

#### Examples for NOT Operator

To obtain the documents that contain the term animals but not dogs, use the following expression:

    'animals ~ dogs'

Similarly, to obtain the documents that contain the term transportation but not automobiles or trains, use the following expression:

    'transportation not (automobiles or trains)'

**Note:**

The `NOT` operator does not affect the scoring produced by the other logical operators.

#### Related Topics

"MINUS (-)"

### 3.21 OR (\|)

Use the `OR` operator to search for documents that contain at least one occurrence of any of the query terms. The `OR` operator returns documents that contain any of the query terms, while the `AND` operator returns documents that contain all query terms.

#### Syntax

| Syntax                         | Description                                                                                                                                 |
|:-------------------------------|:--------------------------------------------------------------------------------------------------------------------------------------------|
| term1\|term2<br>term1 or term2 | Returns documents that contain term1 or term2. Returns the maximum score of its operands. At least one term must exist; higher score taken. |

#### Examples for OR Operator

To obtain the documents that contain the term cats or the term dogs, use either of the following expressions:

    'cats | dogs'
    'cats OR dogs'

#### Scoring

In an `OR` query, the score returned is the score for the highest query term. In the example, if the scores for cats and dogs is 30 and 40 within a document, the document scores 40.

#### Related Topics

"AND (&)"

### 3.22 Preferred Term (PT)

Use the preferred term operator (`PT`) to replace a term in a query with the preferred term that has been defined in a thesaurus for the term.

#### Syntax

| Syntax            | Description                                                              |
|:------------------|:-------------------------------------------------------------------------|
| PT(term\[,thes\]) | Replaces the specified word in a query with the preferred term for term. |

term
Specify the operand for the preferred term operator. `term` is replaced by the preferred term defined for the term in the specified thesaurus. However, if no `PT` entries are defined for the term, `term` is not replaced in the query expression and `term` is the result of the expansion.

You cannot specify expansion operators in the `term` argument.

thes
Specify the name of the thesaurus used to return the expansions for the specified term. The `thes` argument is optional and has a default value of `DEFAULT`. As a result, a thesaurus named `DEFAULT` must exist in the thesaurus tables before using any of the thesaurus operators.

#### Example for PT Operator

The term automobile has a preferred term of car in a thesaurus. A `PT` query for automobile returns all documents that contain the word car. Documents that contain the word automobile are not returned.

#### Related Topics

CTX_THES.[PT](CTX_THES-package.md) in [CTX_THES Package](CTX_THES-package.md) form more information on browsing the preferred terms in your thesaurus

### 3.23 Related Term (RT)

Use the related term operator (`RT`) to expand a query to include all related terms that have been defined in a thesaurus for the term.

#### Syntax

| Syntax            | Description                                                                                     |
|:------------------|:------------------------------------------------------------------------------------------------|
| RT(term\[,thes\]) | Expands a query to include all the terms defined in the thesaurus as a related term for `term`. |

term
Specify the operand for the related term operator. `term` is expanded to include `term` and all the related entries defined for `term` in `thes`.

You cannot specify expansion operators in the `term` argument.

thes
Specify the name of the thesaurus used to return the expansions for the specified term. The `thes` argument is optional and has a default value of `DEFAULT`. As a result, a thesaurus named `DEFAULT` must exist in the thesaurus tables before using any of the thesaurus operators.

#### Example for RT Operator

The term dog has a related term of wolf. An RT query for dog returns all documents that contain the word dog and wolf.

#### Related Topics

CTX_THES.[RT](CTX_THES-package.md) in [CTX_THES Package](CTX_THES-package.md) for more information on browsing the related terms in your thesaurus

### 3.24 SDATA

Use the `SDATA` operator to perform tests on `SDATA` sections and columns, which contain structured data values.

`SDATA` sections speed up mixed querying and ordering. This operator provides structured predicate support for `CONTAINS`, which extends non-SQL interfaces such as `count_hits` or the result set interface.

`SDATA` operators should only be used as descendants of `AND` operators that also have non-`SDATA` children.

`SDATA` queries perform on string or numeric literals, and on date strings. The string literal and date string are enclosed within single or double quote characters. The numeric value is not enclosed in quote characters, and must conform to the SQL format of `NUMBER`. For example:

    CONTAINS(text, "dog and SDATA(category = ''news'')")>0 ...

    SDATA(rating between 1.2 and 3.4) ...

    SDATA(author LIKE 'FFORDE%') ...

    SDATA(date >='2005-09-18') ...

Closed parentheses are permitted, as long as they are enclosed in single or double quotes.

The `SDATA` operator can be used in query templates.

#### Syntax

| Syntax         | Operators                                                                           |
|:---------------|:------------------------------------------------------------------------------------|
| SData          | := "SDATA" "(" SDataPredicate ")"                                                   |
| SDataPredicate | := section_name SDataTest                                                           |
| SDataTest      | := \<SDataSingleOp SDataLiteral\> \| SDataBetweenOp \| \<"is" ("not")? "null"\>     |
| SDataSingleOp  | := ("\<" \| "\<=" \| "=" \| "\>=" \| "\>" \| "!=" \| "\<\>" \| "like") SDataLiteral |
| SDataBetweenOp | := "between" SDataLiteral "and" SDataLiteral                                        |
| SDataLiteral   | := numeric_literal \| "'" string_literal "'" \| "'" date_string "'"                 |

section_name
The name of the `SDATA` section(s) on which to search and perform the test, or check.

SDataLiteral
The value of the `SDATA` section. This must be either a string literal, numeric literal, or a date string.

The `SDATA` operator returns a score of 100 if the enclosed predicate returns `TRUE`, and returns `0` otherwise. In the case of a `NULL` value, the `SDATA` operator returns a score of `0` (since in SQL it would not return `TRUE`).

Multi-valued semantics are not defined, as multi-valued `SDATA` sections are not supported.

Comparison of strings is case sensitive. The `BINARY` collation is always used.

**Note:**

For the `SDATA` operator on `SDATA` sections that are mapped to a `DATE` `FILTER` `BY` column, the `SDATA` value must follow the Date format: `YYYY-MM-DD` or `YYYY-MM-DD HH24:MI:SS`. Otherwise, the expected rows will not be returned. If the time component is omitted, it will default to `00:00:00`, according to SQL semantics. This Date format is always used, regardless of the setting of the `NLS_DATE_FORMAT` environment variable.

#### Example for SDATA Operator

Suppose that you want to query for books in the fiction category that contain the word summer. Assuming that an `SDATA` section called `CATEGORY` has been declared, you can query as follows:

    SELECT id FROM idx_docs
      WHERE CONTAINS(text, 'summer AND SDATA(category = "fiction")')>0

#### Restrictions

- An error is raised if the section name is not a defined `SDATA` section. The source of the section (for example, tag versus column) is not important.

- The syntax precludes `RHS` `SDATA` and expressions.

- `SDATA` operators cannot be children of `WITHIN`, `INPATH`, `HASPATH`, or `NEAR`.

- The data type of the named `SDATA` section must be compatible with the literal provided (and the operator, for example, `LIKE`) or an error is raised.

- `SDATA` operators are not supported in `CTXRULE` query documents.

- `SDATA` operators have no effect on highlighting.

#### Notes

Stoplists do not affect string-value `SDATA` sections, that is, if a stopword is present within an `SDATA` section, then the token will still be indexed and can be queried using the `SDATA` operator.

Oracle recommends using `SDATA` operators only as descendants of `AND` operators that also have non-`SDATA` children. Essentially, use `SDATA` operators as secondary (that is, checking or non-driving) criteria. For instance, "find documents with DOG that also have price \> 5", rather than "find documents with rating \> 4". Other usage may operate properly, but may not have optimal performance.

The following examples are consistent with recommended use:

    dog & SDATA(foo = 5)

The `SDATA` is a child of an `AND` operator that also has non-`SDATA` children.

    dog & (SDATA(foo = 5) | SDATA(x = 1))

Although the `SDATA` operators here are children of `OR`, they are still descendants of an `AND` operator with non-`SDATA` children.

The following examples show use that is not recommended:

    SDATA(foo = 5)

Here, `SDATA` is the only criteria and, therefore, the driving criteria.

    dog | SDATA(bar = 9)

The `SDATA` in this example is a child of an `OR` operator rather than an `AND`.

    SDATA(foo = 5) & SDATA(bar = 7)

While both `SDATA` operators in this example are descendants of `AND`, this `AND` operator does not have non-`SDATA` children.

**Related Topics**

- [ADD_SDATA_COLUMN](CTX_DDL-package.md)
- [ADD_SDATA_SECTION](CTX_DDL-package.md)
- [UPDATE_SDATA](CTX_DDL-package.md)
- [CTX_SECTIONS](oracle-text-views.md)
- [Oracle Text Views](oracle-text-views.md)
- [Oracle Text Application Developer's Guide](../ccapp/searching-document-sections-in-oracle-text.md)

### 3.25 soundex (!)

Use the soundex (!) operator to expand queries to include words that have similar sounds; that is, words that sound like other words.

This function enables comparison of words that are spelled differently, but sound alike in English. The `SOUNDEX` operator algorithm uses heuristic methods, so results may vary based on your query words.

#### Syntax

| Syntax | Description                                                                                                  |
|:-------|:-------------------------------------------------------------------------------------------------------------|
| !term  | Expands a query to include all terms that sound the same as the specified term (English-language text only). |

#### Example for Soundex (!) Operator

    SELECT ID, COMMENT FROM EMP_RESUME
    WHERE CONTAINS (COMMENT, '!SMYTHE') > 0 ;

    ID COMMENT
    -- ------------
    23 Smith is a hard worker who..

#### Language

Soundex works best for languages that use a 7-bit character set, such as English. It can be used, with lesser effectiveness, for languages that use an 8-bit character set, such as many Western European languages.

If you have base-letter conversion specified for a text column and the query expression contains a soundex operator, then Oracle Text operates on the base-letter form of the query.

### 3.26 stem (\$)

Use the stem (\$) operator to search for terms that have the same linguistic root as the query term.

If you use the `BASIC_LEXER` to index your language, stemming performance can be improved by using the index_stems attribute.

The Oracle Text stemmer, licensed from XSoft Division of Xerox Corporation, supports the following languages with the [BASIC_LEXER](oracle-text-indexing-elements.md): English, French, Spanish, Italian, German, and Dutch.

Japanese stemming is supported with the [JAPANESE_LEXER](oracle-text-indexing-elements.md).

Specify your stemming language with the [BASIC_WORDLIST](oracle-text-indexing-elements.md) wordlist preference.

#### Syntax

| Syntax | Description                                                                                   |
|:-------|:----------------------------------------------------------------------------------------------|
| \$term | Expands a query to include all terms having the same stem or root word as the specified term. |

#### Examples for Stem (\$) Operator

| Input         | Expands To                              |
|:--------------|:----------------------------------------|
| \$scream      | scream screaming screamed               |
| \$distinguish | distinguish distinguished distinguishes |
| \$guitars     | guitars guitar                          |
| \$commit      | commit committed                        |
| \$cat         | cat cats                                |
| \$sing        | sang sung sing                          |

#### Behavior with Stopwords

If stem returns a word designated as a stopword, the stopword is not included in the query or highlighted by `CTX_QUERY.HIGHLIGHT` or `CTX_QUERY.MARKUP`.

#### Related Topics

For more information about enabling the stem operator with BASIC_LEXER, see "[BASIC_LEXER](oracle-text-indexing-elements.md)" in [Oracle Text Indexing Elements](oracle-text-indexing-elements.md)

### 3.27 Stored Query Expression (SQE)

Use the SQE operator to call a stored query expression created with the `CTX_QUERY.`[`STORE_SQE`](CTX_QUERY-package.md) procedure.

Stored query expressions can be used for creating predefined bins for organizing and categorizing documents or to perform iterative queries, in which an initial query is refined using one or more additional queries.

#### Syntax

| Syntax        | Description                                                   |
|:--------------|:--------------------------------------------------------------|
| SQE(SQE_name) | Returns the results for the stored query expression SQE_name. |

#### Examples for SQE Operator

To create an SQE named disasters, use `CTX_QUERY.`[`STORE_SQE`](CTX_QUERY-package.md) as follows:

    begin
    ctx_query.store_sqe('disasters', 'hurricane or earthquake or blizzard');
    end;

This stored query expression returns all documents that contain either hurricane, earthquake or blizzard.

This SQE can then be called within a query expression as follows:

    SELECT SCORE(1), docid FROM news
    WHERE CONTAINS(resume, 'sqe(disasters)', 1)> 0
    ORDER BY SCORE(1);

#### Limitations

Up to 100 stored query expressions (SQEs) can be stored in a single Text query. If a Text query has more than 100 SQEs, including nested SQEs, then the query fails and error DRG-50949 is raised.

#### Related Topic

"[STORE_SQE](CTX_QUERY-package.md)"

### 3.28 SYNonym (SYN)

Use the synonym operator (`SYN`) to expand a query to include all the terms that have been defined in a thesaurus as synonyms for the specified term.

#### Syntax

| Syntax             | Description                                                                               |
|:-------------------|:------------------------------------------------------------------------------------------|
| SYN(term\[,thes\]) | Expands a query to include all the terms defined in the thesaurus as synonyms for `term`. |

term
Specify the operand for the synonym operator. `term` is expanded to include `term` and all the synonyms defined for `term` in `thes`.

You cannot specify expansion operators in the `term` argument.

thes
Specify the name of the thesaurus used to return the expansions for the specified term. The `thes` argument is optional and has a default value of `DEFAULT`. A thesaurus named `DEFAULT` must exist in the thesaurus tables if you use this default value.

#### Examples for SYN Operator

The following query expression returns all documents that contain the term dog or any of the synonyms defined for dog in the `DEFAULT` thesaurus:

    'SYN(dog)'

Compound Phrases in Synonym Operator

Expansion of compound phrases for a term in a synonym query are returned as `AND` conjunctives.

For example, the compound phrase temperature + measurement + instruments is defined in a thesaurus as a synonym for the term thermometer. In a synonym query for thermometer, the query is expanded to:

    {thermometer} OR ({temperature}&{measurement}&{instruments})

#### Related Topics

CTX_THES.[SYN](CTX_THES-package.md) in [CTX_THES Package](CTX_THES-package.md) for more information on browsing the synonym terms in your thesaurus

### 3.29 threshold (\>)

Use the threshold operator (\>) in two ways:

- at the expression level

- at the query term level

The threshold operator at the expression level eliminates documents in the result set that score below a threshold number.

The threshold operator at the query term level selects a document based on how a term scores in the document.

#### Syntax

| Syntax                   | Description                                                                                                                                                                       |
|:-------------------------|:----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| expression\>n<br>term\>n | Returns only those documents in the result set that score above the threshold n.<br>Within an expression, returns documents that contain the query term with score of at least n. |

#### Examples for Threshold (\>) Operator

At the expression level, to search for documents that contain relational databases and to return only documents that score greater than 75, use the following expression:

    'relational databases > 75'

At the query term level, to select documents that have at least a score of 30 for lion and contain tiger, use the following expression:

    '(lion > 30) and tiger'

### 3.30 Translation Term (TR)

Use the translation term operator (`TR`) to expand a query to include all defined foreign language equivalent terms.

#### Syntax

| Syntax                       | Description                                                                    |
|:-----------------------------|:-------------------------------------------------------------------------------|
| TR(term\[, lang, \[thes\]\]) | Expands term to include all the foreign equivalents that are defined for term. |

term
Specify the operand for the translation term operator. `term` is expanded to include all the foreign language entries defined for `term` in `thes`. You cannot specify expansion operators in the `term` argument.

lang
Optionally, specify which foreign language equivalents to return in the expansion. The language you specify must match the language as defined in `thes`. (You may specify only one language at a time.) If you omit this parameter or specify it as `ALL`, the system expands to use all defined foreign language terms.

thes
Optionally, specify the name of the thesaurus used to return the expansions for the specified term. The `thes` argument has a default value of `DEFAULT`. As a result, a thesaurus named `DEFAULT` must exist in the thesaurus tables before you can use any of the thesaurus operators.

**Note:**

If you specify `thes`, then you must also specify `lang`.

#### Examples for TR Operator

Consider a thesaurus `MY_THES` with the following entries for cat:

    cat
      SPANISH: gato
      FRENCH:  chat

To search for all documents that contain cat and the spanish translation of cat, enter the following query:

    'tr(cat, spanish, my_thes)'

This query expands to:

    '{cat}|{gato}'

#### Related Topics

CTX_THES.[TR](CTX_THES-package.md) in [CTX_THES Package](CTX_THES-package.md) for more information on browsing the related terms in your thesaurus

### 3.31 Translation Term Synonym (TRSYN)

Use the translation term synonym operator (`TRSYN`) to expand a query to include all the defined foreign equivalents of the query term, the synonyms of query term, and the foreign equivalents of the synonyms.

#### Syntax

| Syntax                          | Description                                                                                                                   |
|:--------------------------------|:------------------------------------------------------------------------------------------------------------------------------|
| TRSYN(term\[, lang, \[thes\]\]) | Expands `term` to include foreign equivalents of `term`, the synonyms of `term`, and the foreign equivalents of the synonyms. |

term
Specify the operand for this operator. `term` is expanded to include all the foreign language entries and synonyms defined for `term` in `thes`. You cannot specify expansion operators in the `term` argument.

lang
Optionally, specify which foreign language equivalents to return in the expansion. The language you specify must match the language as defined in `thes`. If you omit this parameter, the system expands to use all defined foreign language terms.

thes
Optionally, specify the name of the thesaurus used to return the expansions for the specified term. The `thes` argument has a default value of `DEFAULT`. As a result, a thesaurus named `DEFAULT` must exist in the thesaurus tables before you can use any of the thesaurus operators.

**Note:**

If you specify `thes`, then you must also specify `lang`.

#### Examples for TRSYN Operator

Consider a thesaurus `MY_THES` with the following entries for cat:

    cat
      SPANISH: gato
      FRENCH:  chat
      SYN lion
        SPANISH: leon

To search for all documents that contain cat, the spanish equivalent of cat, the synonym of cat, and the spanish equivalent of lion, enter the following query:

    'trsyn(cat, spanish, my_thes)'

This query expands to:

    '{cat}|{gato}|{lion}|{leon}'

#### Related Topics

CTX_THES.[TRSYN](CTX_THES-package.md) in [CTX_THES Package](CTX_THES-package.md) for more information on browsing the translation and synonym terms in your thesaurus

### 3.32 Top Term (TT)

Use the top term operator (`TT`) to replace a term in a query with the top term that has been defined for the term in the standard hierarchy (Broader Term \[`BT`\], Narrower Term \[`NT]`) in a thesaurus. A top term is the broadest conceptual term related to a given query term. For example, a thesaurus might define the following hierarchy:

    DOG
       BT1 CANINE
         BT2 MAMMAL
           BT3 VERTEBRATE
             BT4 ANIMAL

The top term for dog in this thesaurus is animal.

Top terms in the generic (`BTG`, `NTG`), partitive (`BTP`, `NTP`), and instance (`BTI`, `NTI`) hierarchies are not returned.

#### Syntax

| Syntax            | Description                                                                                                 |
|:------------------|:------------------------------------------------------------------------------------------------------------|
| TT(term\[,thes\]) | Replaces the specified word in a query with the top term in the standard hierarchy (`BT`, `NT`) for `term`. |

term
Specify the operand for the top term operator. `term` is replaced by the top `term` defined for the term in the specified thesaurus. However, if no `TT` entries are defined for `term`, `term` is not replaced in the query expression and `term` is the result of the expansion.

You cannot specify expansion operators in the `term` argument.

thes
Specify the name of the thesaurus used to return the expansions for the specified term. The `thes` argument is optional and has a default value of `DEFAULT`. A thesaurus named `DEFAULT` must exist in the thesaurus tables if you use this default value.

#### Example for TT Operator

The term dog has a top term of animal in the standard hierarchy of a thesaurus. A `TT` query for dog returns all documents that contain the phrase animal. Documents that contain the word dog are not returned.

#### Related Topics

CTX_THES.[TT](CTX_THES-package.md) for more information on browsing the top terms in your thesaurus

### 3.33 weight (\*)

The weight operator multiplies the score by the given factor, topping out at 100 when the score exceeds 100. For example, the query cat, dog\*2 sums the score of cat with twice the score of dog, topping out at 100 when the score is greater than 100.

In expressions that contain more than one query term, use the weight operator to adjust the relative scoring of the query terms. Reduce the score of a query term by using the weight operator with a number less than 1; increase the score of a query term by using the weight operator with a number greater than 1 and less than 10.

The weight operator is useful in ACCUMulate ( \_ ), AND (&), or OR (\|) queries when the expression has more than one query term. With no weighting on individual terms, the score cannot tell which of the query terms occurs the most. With term weighting, you can alter the scores of individual terms and hence make the overall document ranking reflect the terms you are interested in.

#### Syntax

| Syntax  | Description                                                                                                                                  |
|:--------|:---------------------------------------------------------------------------------------------------------------------------------------------|
| term\*n | Returns documents that contain `term`. Calculates score by multiplying the raw score of `term` by `n`, where `n` is a number from 0.1 to 10. |

#### Examples for Weight (\*) Operator

Suppose you have a collection of sports articles. You are interested in the articles about Brazilian soccer. It turns out that a regular query on soccer or Brazil returns many high ranking articles on US soccer. To raise the ranking of the articles on Brazilian soccer, enter the following query:

    'soccer or Brazil*3'

Table 3-3 illustrates how the weight operator can change the ranking of three hypothetical documents A, B, and C, which all contain information about soccer. The columns in the table show the total score of four different query expressions on the three documents.

Table 3-3 Score Samples

| Document | soccer | Brazil | soccer or Brazil | soccer or Brazil\*3 |
|:---------|:-------|:-------|:-----------------|:--------------------|
| A        | 20     | 10     | 20               | 30                  |
| B        | 10     | 30     | 30               | 90                  |
| C        | 50     | 20     | 50               | 60                  |

The score in the third column containing the query soccer or Brazil is the score of the highest scoring term. The score in the fourth column containing the query soccer or Brazil\*3 is the larger of the score of the first column soccer and of the score Brazil multiplied by three, Brazil\*3.

With the initial query of soccer or Brazil, the documents are ranked in the order C B A. With the query of soccer or Brazil\*3, the documents are ranked B C A, which is the preferred ranking.

Weights can be added to multiple terms. The query Brazil OR (soccer AND Brazil)\*3 will increase the relative scores for documents that contain both soccer and Brazil.

### 3.34 wildcards (% \_)

Wildcard characters can be used in query expressions to expand word searches into pattern searches. When a wildcard is used on its own, for example, "DOG %" or ".%" or "%" by itself, it is treated as a stopword.

The wildcard characters are as follows:

| Wildcard Character | Description                                                                                                                                                                                                                                                                                         |
|:-------------------|:----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| %                  | The percent wildcard can appear any number of times at any part of the search term. The search term will be expanded into an equivalence list of terms. The list consists of all terms in the index that match the wildcarded term, with zero or more characters in place of the percent character. |
| \_                 | The underscore wildcard specifies a single position in which any character can occur.                                                                                                                                                                                                               |

The total number of wildcard expansions from all words in a query containing unescaped wildcard characters cannot exceed the maximum number of expansions specified by the `BASIC_WORDLIST` attribute `WILDCARD_MAXTERMS`. For more information, see "[BASIC_WORDLIST](oracle-text-indexing-elements.md)".

**Note:**

- When a wildcard is used on its own, it is treated as a stopword.

- When a wildcard expression translates to a stopword, the stopword is not included in the query and not highlighted by CTX_DOC.[HIGHLIGHT](CTX_DOC-package.md) or CTX_DOC.[MARKUP](CTX_DOC-package.md) .

#### Right-Truncated Queries

Right truncation involves placing the wildcard on the right-hand-side of the search string.

For example, the following query expression finds all terms beginning with the pattern scal:

    'scal%'

#### Left- and Double-Truncated Queries

Left truncation involves placing the wildcard on the left-hand-side of the search string.

To find words such as king, wing or sing, write the query as follows:

    '_ing'

For all words that end with ing, enter:

    '%ing'

Combine left-truncated and right-truncated searches to create double-truncated searches. The following query finds all documents that contain words that contain the substring %benz%

    '%benz%'

#### Improving Wildcard Query Performance

Improve wildcard query performance by adding a substring or prefix index.

When your wildcard queries are left- and double-truncated, you can improve query performance by creating a substring index. Substring indexes improve query performance for all types of left-truncated wildcard searches such as %ed, \_ing, or %benz%.

When your wildcard queries are right-truncated, you can improve performance by creating a prefix index. A prefix index improves query performance for wildcard searches such as to%.

**See Also:**

"[BASIC_WORDLIST](oracle-text-indexing-elements.md)" in [Oracle Text Indexing Elements](oracle-text-indexing-elements.md) for more information about creating substring and prefix indexes

### 3.35 WITHIN

Use the `WITHIN` operator to narrow a query down into document sections. Document sections can be one of the following:

- Zone sections

- Field sections

- Attribute sections

- Special sections (sentence or paragraph)

#### Syntax

| Syntax                      | Description                                                                                                                                                                                                                                                                                                                             |
|:----------------------------|:----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| expression WITHIN section   | Searches for `expression` within the predefined zone, field, or attribute `section`.<br>If section is a zone, `expression` can contain one or more `WITHIN` operators (nested `WITHIN`) whose section is a zone or special section.<br>If section is a field or attribute section, expression cannot contain another `WITHIN` operator. |
| expression WITHIN SENTENCE  | Searches for documents that contain `expression` within a sentence. Specify an `AND` or `NOT` query for `expression`.<br>The `expression` can contain one or more `WITHIN` operators (nested `WITHIN`) whose section is a zone or special section.                                                                                      |
| expression WITHIN PARAGRAPH | Searches for documents that contain `expression` within a paragraph. Specify an `AND` or `NOT` query for `expression`.<br>`The expression` can contain one or more `WITHIN` operators (nested `WITHIN`) whose section is a zone or special section.                                                                                     |

#### WITHIN Limitations

The `WITHIN` operator has the following limitations:

- You cannot embed the `WITHIN` clause in a phrase. For example, you cannot write: term1 WITHIN section term2

- Because `WITHIN` is a reserved word, you must escape the word with braces to search on it.

#### WITHIN Operator Examples

Querying Within Zone Sections

To find all the documents that contain the term San Francisco within the section Headings, write the query as follows:

    'San Francisco WITHIN Headings'

To find all the documents that contain the term sailing and contain the term San Francisco within the section Headings, write the query in one of two ways:

    '(San Francisco WITHIN Headings) and sailing'

    'sailing and San Francisco WITHIN Headings'

#### Compound Expressions with WITHIN

To find all documents that contain the terms dog and cat within the same section Headings, write the query as follows:

    '(dog and cat) WITHIN Headings'

This query is logically different from:

    'dog WITHIN Headings and cat WITHIN Headings'

This query finds all documents that contain dog and cat where the terms dog and cat are in Headings sections, regardless of whether they occur in the same Headings section or different sections.

#### Near with WITHIN

To find all documents in which dog is near cat within the section Headings, write the query as follows:

    'dog near cat WITHIN Headings'

**Note:**

The near operator has higher precedence than the `WITHIN` operator so braces are not necessary in this example. This query is equivalent to (dog near cat) WITHIN Headings.

#### Nested WITHIN Queries

You can nest the within operator to search zone sections within zone sections.

For example, assume that a document set had the zone section `AUTHOR` nested within the zone `BOOK` section. Write a nested `WITHIN` query to find all occurrences of scott within the `AUTHOR` section of the `BOOK` section as follows:

    '(scott WITHIN AUTHOR) WITHIN BOOK'

#### Querying Within Field Sections

The syntax for querying within a field section is the same as querying within a zone section. The syntax for most of the examples given in the previous section, "Querying Within Zone Sections", apply to field sections.

However, field sections behave differently from zone sections in terms of

- Visibility: Make text within a field section invisible.

- Repeatability: `WITHIN` queries cannot distinguish repeated field sections.

- Nestability: You cannot enter a nested `WITHIN` query with a field section.

The following sections describe these differences.

#### Visible Flag in Field Sections

When a field section is created with the visible flag set to `FALSE` in `CTX_DDL.ADD_FIELD_SECTION`, the text within a field section can only be queried using the `WITHIN` operator.

For example, assume that `TITLE` is a field section defined with visible flag set to `FALSE`. Then the query dog withoutthe `WITHIN` operator will not find a document containing:

    <TITLE>The dog</TITLE> I like my pet.

To find such a document, use the `WITHIN` operator as follows:

    'dog WITHIN TITLE'

Alternatively, set the visible flag to `TRUE` when you define `TITLE` as a field section with `CTX_DDL.ADD_FIELD_SECTION`.

**See Also:**

"[ADD_FIELD_SECTION](CTX_DDL-package.md)" in [CTX_DDL Package](CTX_DDL-package.md) for more information about creating field sections

#### Repeated Field Sections

`WITHIN` queries cannot distinguish repeated field sections in a document. For example, consider the document with the repeated section `<author>`:

    <author> Charles Dickens </author>
    <author> Martin Luther King </author>

Assuming that `<author>` is defined as a field section, a query such as (charles and martin) within author returns the document, even though these words occur in separate tags.

To have `WITHIN` queries distinguish repeated sections, define the sections as zone sections.

#### Nested Field Sections

You cannot enter a nested `WITHIN` query with field sections. Doing so raises an error.

#### Querying Within Sentence or Paragraphs

Querying within sentence or paragraph boundaries is useful to find combinations of words that occur in the same sentence or paragraph. To query sentence or paragraphs, you must first add the special section to your section group before you index. Do so with `CTX_DDL.ADD_SPECIAL_SECTION`.

To find documents that contain dog and cat within the same sentence:

    '(dog and cat) WITHIN SENTENCE'

To find documents that contain dog and cat within the same paragraph:

    '(dog and cat) WITHIN PARAGRAPH'

To find documents that contain sentences with the word dog but not cat:

    '(dog not cat) WITHIN SENTENCE'

#### Querying Within Attribute Sections

Query within attribute sections when you index with either `XML_SECTION_GROUP` or `AUTO_SECTION_GROUP` as your section group type.

Assume you have an XML document as follows:

    <book title="Tale of Two Cities">It was the best of times.</book>

Define the section `title@book` to be the attribute section `title`. Do so with the `CTX_DLL.ADD_ATTR_SECTION` procedure or dynamically after indexing with `ALTER` `INDEX`.

**Note:**

When you use the `AUTO_SECTION_GROUP` to index XML documents, the system automatically creates attribute sections and names them in the form `attribute@tag`.

If you use the `XML_SECTION_GROUP`, you can name attribute sections anything with `CTX_DDL.ADD_ATTR_SECTION`.

To search on Tale within the attribute section `title`, enter the following query:

    'Tale WITHIN title'

#### Constraints for Querying Attribute Sections

The following constraints apply to querying within attribute sections:

- Regular queries on attribute text do not hit the document unless qualified in a within clause. Assume you have an XML document as follows:

<!-- -->

    <book title="Tale of Two Cities">It was the best of times.</book>

A query on Tale by itself does not produce a hit on the document unless qualified with `WITHIN title@book`. (This behavior is like field sections when you set the visible flag set to false.)

- You cannot use attribute sections in a nested `WITHIN` query.

- Phrases ignore attribute text. For example, if the original document looked like:

<!-- -->

    Now is the time for all good <word type="noun"> men </word> to come to the aid.

Then this document would hit on the regular query good men, ignoring the intervening attribute text.

- `WITHIN` queries can distinguish repeated attribute sections. This behavior is like zone sections but unlike field sections. For example, you have a document as follows:

<!-- -->

    <book title="Tale of Two Cities">It was the best of times.</book>
    <book title="Of Human Bondage">The sky broke dull and gray.</book>

Assume that `book` is a zone section and `book@author` is an attribute section. Consider the query:

    '(Tale and Bondage) WITHIN book@author'

This query does not hit the document, because tale and bondage are in different occurrences of the attribute section `book@author`.

#### Notes

Section Names

The `WITHIN` operator requires you to know the name of the section you search. A list of defined sections can be obtained using the [CTX_SECTIONS](oracle-text-views.md) or [CTX_USER_SECTIONS](oracle-text-views.md) views.

Section Boundaries

For special and zone sections, the terms of the query must be fully enclosed in a particular occurrence of the section for the document to satisfy the query. This is not a requirement for field sections.

For example, consider the query where bold is a zone section:

    '(dog and cat) WITHIN bold'

This query finds:

    <B>dog cat</B>

but it does not find:

    <B>dog</B><B>cat</B>

This is because dog and cat must be in the same bold section.

This behavior is especially useful for special sections, where

    '(dog and cat) WITHIN sentence'

means find dog and cat within the same sentence.

Field sections on the other hand are meant for non-repeating, embedded metadata such as a title section. Queries within field sections cannot distinguish between occurrences. All occurrences of a field section are considered to be parts of a single section. For example, the query:

    (dog and cat) WITHIN title

can find a document like this:

\<TITLE\>dog\</TITLE\>\<TITLE\>cat\</TITLE\>

In return for this field section limitation and for the overlap and nesting limitations, field section queries are generally faster than zone section queries, especially if the section occurs in every document, or if the search term is common.
