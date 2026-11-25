Become familiar with CONTEXT and CTXCAT grammars.

This chapter contains the following topics:

- The CONTEXT Grammar

- The CTXCAT Grammar

### 7.1 The CONTEXT Grammar

The `CONTEXT` grammar is the default grammar for `CONTAINS`. With this grammar, you can add complexity to your searches with operators. You use the query operators in your query expression. For example, the `AND` logical operator enables you to search for all documents that contain two different words. The `ABOUT` operator enables you to search on concepts.

You can also use the `WITHIN` operator for section searches; the `NEAR` operator for proximity searches; and the stem, fuzzy, and thesaurus operators for expanding a query expression.

With `CONTAINS,` you can also use the `CTXCAT` grammar with the query template feature.

The following sections describe some of the Oracle Text operators:

- ABOUT Query

- Logical Operators

- Section Searching and HTML and XML

- Proximity Queries with NEAR, NEAR_ACCUM, and NEAR2 Operators

- Fuzzy, Stem, Soundex, Wildcard and Thesaurus Expansion Operators

- Using CTXCAT Grammar

- Stored Query Expressions

- Calling PL/SQL Functions in CONTAINS

- Optimizing for Response Time

- Counting Hits

- Using DEFINESCORE and DEFINEMERGE for User-defined Scoring

**See Also:**

[Oracle Text Reference](../ccref/oracle-text-CONTAINS-query-operators.md) for complete information about using query operators

#### 7.1.1 ABOUT Query

Use the `ABOUT` operator in English or French to query on a concept. The query string is usually a concept or theme that represents the idea to be searched on. Oracle Text returns the documents that contain the theme.

Word information and theme information are combined into a single index. To enter a theme query in your index, you must include that is created by default in English and French.

Enter a theme query by using the `ABOUT` operator inside the query expression. For example, to retrieve all documents that are about politics, write your query as follows:

    SELECT SCORE(1), title FROM news
               WHERE CONTAINS(text, 'about(politics)', 1) > 0
               ORDER BY SCORE(1) DESC;

**See Also:**

[Oracle Text Reference](../ccref/oracle-text-CONTAINS-query-operators.md) for more information about using the `ABOUT` operator

#### 7.1.2 Logical Operators

Use logical operators to limit your search criteria in a number of ways. Table 7-1 describes some of these operators.

Table 7-1 Logical Operators

| Operator | Symbol | Description                                                                                                                                                                           | Example Expression                                                                                                                                                                            |
|:---------|:-------|:--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|:----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `AND`    | &      | Use to search for documents that contain at least one occurrence of each of the query terms.<br>The returned score is the minimum of the operands.                                    | `'cats AND dogs'`<br>`'cats & dogs'`                                                                                                                                                          |
| `OR`     | \|     | Use to search for documents that contain at least one occurrence of any of the query terms.<br>The returned score is the maximum of the operands.                                     | `'cats | dogs'`<br>`'cats OR dogs'`                                                                                                                                                           |
| `NOT`    | ~      | Use to search for documents that contain one query term and not another.                                                                                                              | To obtain the documents that contain the term animals but not dogs, use the following expression:<br>`'animals ~ dogs'`                                                                       |
| `ACCUM`  | ,      | Use to search for documents that contain at least one occurrence of any of the query terms. The accumulate operator ranks documents according to the total term weight of a document. | The following query returns all documents that contain the terms dogs, cats, and puppies, giving the highest scores to the documents that contain all three terms:<br>`'dogs, cats, puppies'` |
| `EQUIV`  | =      | Use to specify an acceptable substitution for a word in a query.                                                                                                                      | The following example returns all documents that contain either the phrase alsatians are big dogs or German shepherds are big dogs:<br>`'German shepherds=alsatians are big dogs'`            |

#### 7.1.3 Section Searching and HTML and XML

Section searching is useful when your document set is HTML or XML. For HTML, you can define sections by using embedded tags and then use the `WITHIN` operator to search these sections.

For XML, you can have the system automatically create sections. You can query with the `WITHIN` operator or with the `INPATH` operator for path searching.

**See Also:**

[Searching Document Sections in Oracle Text](searching-document-sections-in-oracle-text.md)

#### 7.1.4 Proximity Queries with NEAR, NEAR_ACCUM, and NEAR2 Operators

Use the `NEAR` operator to search for terms that are near to one another in a document.

For example, to find all the documents where dog is within 6 words of cat, enter the following query:

    'near((dog, cat), 6)'

The `NEAR` operator is now modified to change how the distance is measured between phrases in `NESTED NEAR.`

The `NEAR_ACCUM` operator combines the functionality of the `NEAR` operator with that of the `ACCUM` operator. Like `NEAR,` it returns terms that are within a given proximity of each other; however, if one term is not found, it ranks documents according to the frequency of the occurrence of the term that is found.

The `NEAR2` operator combines the functionality of `PHRASE,` `NEAR,` and `AND` operators. In addition, the `NEAR2` operator can use position information to boost the scores of its hits. That is, if one phrase hit occurs at the beginning of a document and another at the end of the document, then a higher weight is given to the first hit as compared to the second hit.

**See Also:**

[Oracle Text Reference](../ccref/oracle-text-CONTAINS-query-operators.md) for more information about using the `NEAR`, `NEAR_ACCUM`, and `NEAR2` operators

#### 7.1.5 Fuzzy, Stem, Soundex, Wildcard and Thesaurus Expansion Operators

Expand your queries into longer word lists with operators such as wildcard, fuzzy, stem, soundex, and thesaurus.

**See Also:**

- [Oracle Text Reference](../ccref/oracle-text-CONTAINS-query-operators.md) for more information about using these operators

- "[Is it OK to have many expansions in a query?](tuning-oracle-text.md)"

#### 7.1.6 Using CTXCAT Grammar

Use the `CTXCAT` grammar in `CONTAINS` queries. To do so, use a query template specification in the `text_query` parameter of `CONTAINS.`

Take advantage of the `CTXCAT` grammar when you need an alternative and simpler query grammar.

**See Also:**

[Oracle Text Reference](../ccref/oracle-text-SQL-statements-and-operators.md) for more information about using these operators

#### 7.1.7 Defined Stored Query Expressions

Use the `CTX_QUERY.STORE_SQE` procedure to store the definition of a query without storing any results.

Referencing the query with the `CONTAINS` SQL operator references the definition of the query. In this way, you can use the stored query expressions to define long or frequently used query expressions.

Stored query expressions are not attached to an index. When you call `CTX_QUERY.STORE_SQE,` you specify only the name of the stored query expression and the query expression.

The query definitions are stored in the Text data dictionary. Any user can reference a stored query expression.

**Related Topics**

- Defining a Stored Query Expression
- SQE Example
- [Oracle Text Reference](../ccref/CTX_QUERY-package.md)

##### 7.1.7.1 Defining a Stored Query Expression

To define and use a stored query expression:

1.  Call `CTX_QUERY.STORE_SQE` to store the queries for the text column. With `STORE_SQE,` you specify a name for the stored query expression and a query expression.
2.  Use the `SQE` operator to call the stored query expression in a query expression. Oracle Text returns the results of the stored query expression in the same way that it returns the results of a regular query. The query is evaluated when the stored query expression is called.
    You can delete a stored query expression by using `REMOVE_SQE.`

##### 7.1.7.2 SQE Example

The following example creates a stored query expression called disaster that searches for documents containing the words tornado, hurricane, or earthquake:

    begin
    ctx_query.store_sqe('disaster', 'tornado | hurricane | earthquake');
    end;

To execute this query in an expression, write your query as follows:

    SELECT SCORE(1), title from news
       WHERE CONTAINS(text, 'SQE(disaster)', 1) > 0
       ORDER BY SCORE(1);

**See Also:**

[Oracle Text Reference](../ccref/CTX_QUERY-package.md) to learn more about the syntax of `CTX_QUERY.STORE_SQE`

#### 7.1.8 Calling PL/SQL Functions in CONTAINS

You can call user-defined functions directly in the `CONTAINS` clause as long as the function satisfies the requirements for being named in a SQL statement. The caller must also have `EXECUTE` privilege on the function.

For example, if the `french` function returns the French equivalent of an English word, you can search on the French word for cat by writing:

    SELECT SCORE(1), title from news
       WHERE CONTAINS(text, french('cat'), 1) > 0
       ORDER BY SCORE(1);

**See Also:**

[Oracle Database SQL Language Reference](../sqlrf/About-User-Defined-Functions.md) for more information about creating user functions and calling user functions from SQL

#### 7.1.9 Optimizing for Response Time

A `CONTAINS` query optimized for response time provides a fast solution when you need the highest scoring documents from a hitlist.

The following example returns the first twenty hits as output. This example uses the `FIRST_ROWS`(n) hint and a cursor.

    declare
    cursor c is
      select /*+ FIRST_ROWS(20) */ title, score(1) score
        from news where contains(txt_col, 'dog', 1) > 0 order by score(1) desc;
    begin
      for c1 in c
      loop
        dbms_output.put_line(c1.score||':'||substr(c1.title,1,50));
        exit when c%rowcount = 21;
      end loop;
    end;
    /

The following factors can also influence query response time:

- Collection of table statistics

- Memory allocation

- Sorting

- Presence of large object columns in your base table

- Partitioning

- Parallelism

- Number of term expansions in your query

  **See Also:**

  "[Frequently Asked Questions About Query Performance](tuning-oracle-text.md)"

#### 7.1.10 Counting Hits

Use `CTX_QUERY.COUNT_HITS` in PL/SQL or `COUNT(*)` in a SQL `SELECT` statement to count the number of hits returned from a query with only a `CONTAINS` predicate.

If you want a rough hit count, use `CTX_QUERY.COUNT_HITS` in estimate mode (`EXACT` parameter set to `FALSE`). With respect to response time, this is the fastest count you can get.

Use the `COUNT(*)` function in a `SELECT` statement to count the number of hits returned from a query that contains a structured predicate.

To find the number of documents that contain the word oracle, enter the query with the `SQL COUNT` function.

    SELECT count(*) FROM news WHERE CONTAINS(text, 'oracle', 1) > 0;

To find the number of documents returned by a query with a structured predicate, use `COUNT(*).`

    SELECT COUNT(*) FROM news WHERE CONTAINS(text, 'oracle', 1) > 0 and author = 'jones';

To find the number of documents that contain the word oracle, use `COUNT_HITS.`

    declare count number;
    begin
      count := ctx_query.count_hits(index_name => my_index, text_query => 'oracle', exact => TRUE);
     dbms_output.put_line('Number of docs with oracle:');
     dbms_output.put_line(count);
    end;

**See Also:**

[Oracle Text Reference](../ccref/CTX_QUERY-package.md) to learn more about the syntax of `CTX_QUERY.COUNT_HITS`

#### 7.1.11 Using DEFINESCORE and DEFINEMERGE for User-Defined Scoring

Use the `DEFINESCORE` operator to define how the score for a term or phrase is to be calculated. The `DEFINEMERGE` operator defines how to merge scores of child elements of `AND` and `OR` operators. You can also use the alternative scoring template with `SDATA` to affect the final scoring of the document.

**See Also:**

- "[Alternative and User-defined Scoring](querying-with-oracle-text.md)" for information about the alternative scoring template

- [Oracle Text Reference](../ccref/oracle-text-CONTAINS-query-operators.md) to learn more about the syntax of `DEFINESCORE` and `DEFINEMERGE`

### 7.2 The CTXCAT Grammar

The `CTXCAT` grammar is the default grammar for `CATSEARCH.` This grammar supports logical operations, such as `AND` and `OR,` as well as phrase queries.

The `CATSEARCH` query operators have the following syntax:

Table 7-2 CATSEARCH Query Operator Syntax

| Operation            | Syntax      | Description of Operation                                                                                                                                                                                                                                                                                                                                  |
|:---------------------|:------------|:----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Logical `AND`        | a b c       | Returns rows that contain a, b and c.                                                                                                                                                                                                                                                                                                                     |
| Logical `OR`         | a \| b \| c | Returns rows that contain a, b, or c.                                                                                                                                                                                                                                                                                                                     |
| Logical `NOT`        | a - b       | Returns rows that contain a and not b.                                                                                                                                                                                                                                                                                                                    |
| hyphen with no space | a-b         | Hyphen treated as a regular character.<br>For example, if you define the hyphen as a skipjoin, then words such as vice-president are treated as the single query term vicepresident.<br>Likewise, if you define the hyphen as a printjoin, then words such as vice-president are treated as vice president with the space in the `CTXCAT` query language. |
| " "                  | "a b c"     | Returns rows that contain the phrase "a b c."<br>For example, entering "Sony CD Player" means return all rows that contain this sequence of words.                                                                                                                                                                                                        |
| ( )                  | (A B) \| C  | Parentheses group operations. This query is equivalent to the `CONTAINS` query (A &B) \| C.                                                                                                                                                                                                                                                               |

To use the `CONTEXT` grammar in `CATSEARCH` queries, use a query template specification in the `text_query` parameter.

You might use the `CONTAINS` grammar as such when you need to enter proximity, thesaurus, or `ABOUT` queries with a `CTXCAT` index.

**See Also:**

[Oracle Text Reference](../ccref/oracle-text-SQL-statements-and-operators.md) for more information about using these operators
