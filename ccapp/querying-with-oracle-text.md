Become familiar with Oracle Text querying and associated features.

This chapter contains the following topics:

- Overview of Queries

- Oracle Text Query Features

### 6.1 Overview of Queries

The basic Oracle Text query takes a query expression, usually a word with or without operators, as input. Oracle Text returns all documents (previously indexed) that satisfy the expression along with a relevance score for each document. You can use the scores to order the documents in the result set.

To enter an Oracle Text query, use the SQL `SELECT` statement. Depending on the type of index, you use either the `CONTAINS` or `CATSEARCH` operator in the `WHERE` clause. You can use these operators programatically wherever you can use the `SELECT` statement, such as in PL/SQL cursors.

Use the `MATCHES` operator to classify documents with a `CTXRULE` index.

- Querying with CONTAINS

- Querying with CATSEARCH

- Querying with MATCHES

- Word and Phrase Queries

- Querying Stopwords

- ABOUT Queries and Themes

#### 6.1.1 Querying with CONTAINS

When you create an index of type `CONTEXT`, you must use the `CONTAINS` operator to enter your query. This index is suitable for indexing collections of large coherent documents.

With the `CONTAINS` operator, you can use a number of operators to define your search criteria. These operators enable you to enter logical, proximity, fuzzy, stemming, thesaurus, and wildcard searches. With a correctly configured index, you can also enter section searches on documents that have internal structure such as HTML and XML.

With `CONTAINS,` you can also use the `ABOUT` operator to search on document themes.

- CONTAINS SQL Example

- CONTAINS PL/SQL Example

- Structured Query with CONTAINS

##### 6.1.1.1 CONTAINS SQL Example

In the `SELECT` statement, specify the query in the `WHERE` clause with the `CONTAINS` operator. Also specify the `SCORE` operator to return the score of each hit in the hitlist. The following example shows how to enter a query:

    SELECT SCORE(1), title from news WHERE CONTAINS(text, 'oracle', 1) > 0;

You can order the results from the highest scoring documents to the lowest scoring documents by using the `ORDER` `BY` clause as follows:

    SELECT SCORE(1), title from news
               WHERE CONTAINS(text, 'oracle', 1) > 0
               ORDER BY SCORE(1) DESC;

The `CONTAINS` operator must always be followed by the \> 0 syntax, which specifies that the score value returned by the `CONTAINS` operator must be greater than zero for the row to be returned.

When the `SCORE` operator is called in the `SELECT` statement, the `CONTAINS` operator must reference the score label value in the third parameter, as shown in the previous example.

##### 6.1.1.2 CONTAINS PL/SQL Example

In a PL/SQL application, you can use a cursor to fetch the results of the query.

The following example enters a `CONTAINS` query against the `NEWS` table to find all articles that contain the word oracle. The titles and scores of the first ten hits are output.

    declare
      rowno number := 0;
    begin
      for c1 in (SELECT SCORE(1) score, title FROM news
                  WHERE CONTAINS(text, 'oracle', 1) > 0
                  ORDER BY SCORE(1) DESC)
      loop
        rowno := rowno + 1;
        dbms_output.put_line(c1.title||': '||c1.score);
        exit when rowno = 10;
      end loop;
    end;

This example uses a cursor `FOR` loop to retrieve the first ten hits. An alias score is declared for the return value of the `SCORE` operator. The score and title are shown as output by using the cursor dot notation.

##### 6.1.1.3 Structured Query with CONTAINS Example

A structured query, also called a mixed query, is a query that has one `CONTAINS` predicate to query a text column and another predicate to query a structured data column.

To enter a structured query, specify the structured clause in the `WHERE` condition of the `SELECT` statement.

For example, the following `SELECT` statement returns all articles that contain the word oracle written on or after October 1, 1997:

    SELECT SCORE(1), title, issue_date from news
               WHERE CONTAINS(text, 'oracle', 1) > 0
               AND issue_date >= ('01-OCT-97')
               ORDER BY SCORE(1) DESC;

**Note:**

Although you can enter structured queries with `CONTAINS,` consider creating a `CTXCAT` index and issuing the query with `CATSEARCH,` which offers better structured query performance.

#### 6.1.2 Querying with CATSEARCH

When you create an index of type `CTXCAT`, you must use the `CATSEARCH` operator to enter your query. This index is suitable when your application stores short text fragments in the text column and associated information in related columns.

For example, an application serving an online auction site includes a table that stores item descriptions in a text column and date and price information in other columns. With a `CTXCAT` index, you can create b-tree indexes on one or more columns, so that query performance is generally faster for mixed queries.

The operators available for `CATSEARCH` queries are limited to logical operations such as `AND` or `OR.` To define your structured criteria, use the following operators : greater than, less than, equality, `BETWEEN,` and `IN.`

- CATSEARCH SQL Query

- CATSEARCH Example

##### 6.1.2.1 CATSEARCH SQL Query Example

A typical query with `CATSEARCH` includes the following structured clause to find all rows that contain the word camera ordered by the `bid_close` date:

    SELECT FROM auction WHERE CATSEARCH(title, 'camera', 'order by bid_close desc')> 0;

The type of structured query tht you can enter depends on how you create your sub-indexes.

**See Also:**

"[Creating a CTXCAT Index](creating-oracle-text-indexes.md)"

As shown in the previous example, you specify the structured part of a `CATSEARCH` query with the third `structured_query` parameter. The columns in the structured expression must have a corresponding subindex.

For example, assuming that `category_id` and `bid_close` have a subindex in the `ctxcat` index for the `AUCTION` table, enter the following structured query:

    SELECT FROM auction WHERE CATSEARCH(title, 'camera', 'category_id=99 order by bid_close desc')> 0;

##### 6.1.2.2 CATSEARCH Example

The following example shows a field section search against a `CTXCAT` index. It uses `CONTEXT` grammar by means of a query template in a `CATSEARCH` query.

    -- Create and populate table
    create table BOOKS (ID number, INFO varchar2(200), PUBDATE DATE);

    insert into BOOKS values(1, '<author>NOAM CHOMSKY</author><subject>CIVIL
       RIGHTS</subject><language>ENGLISH</language><publisher>MIT
       PRESS</publisher>', '01-NOV-2003');

    insert into BOOKS values(2, '<author>NICANOR PARRA</author><subject>POEMS
      AND ANTIPOEMS</subject><language>SPANISH</language>
      <publisher>VASQUEZ</publisher>', '01-JAN-2001');

    insert into BOOKS values(1, '<author>LUC SANTE</author><subject>XML
      DATABASE</subject><language>FRENCH</language><publisher>FREE
      PRESS</publisher>', '15-MAY-2002');

    commit;


    -- Create index set and section group
    exec ctx_ddl.create_index_set('BOOK_INDEX_SET');
    exec ctx_ddl.add_index('BOOK_INDEX_SET','PUBDATE');

    exec ctx_ddl.create_section_group('BOOK_SECTION_GROUP',
          'BASIC_SECTION_GROUP');
    exec ctx_ddl.add_field_section('BOOK_SECTION_GROUP','AUTHOR','AUTHOR');
    exec ctx_ddl.add_field_section('BOOK_SECTION_GROUP','SUBJECT','SUBJECT');
    exec ctx_ddl.add_field_section('BOOK_SECTION_GROUP','LANGUAGE','LANGUAGE');
    exec ctx_ddl.add_field_section('BOOK_SECTION_GROUP','PUBLISHER','PUBLISHER');

    -- Create index
    create index books_index on books(info) indextype is ctxsys.ctxcat
      parameters('index set book_index_set section group book_section_group');

    -- Use the index
    -- Note that: even though CTXCAT index can be created with field sections, it
    -- cannot be accessed using CTXCAT grammar (default for CATSEARCH).
    -- We need to use query template with CONTEXT grammar to access field
    -- sections with CATSEARCH

    select  id, info from books
    where catsearch(info,
    '<query>
          <textquery grammar="context">
                  NOAM within author and english within language
          </textquery>
     </query>',
    'order by pubdate')>0;

#### 6.1.3 Querying with MATCHES

When you create an index of type `CTXRULE,` you must use the `MATCHES` operator to classify your documents. The `CTXRULE` index is essentially an index on the set of queries that define your classifications.

For example, if you have an incoming stream of documents that need to be routed according to content, you can create a set of queries that define your categories. You create the queries as rows in a text column. You can create this type of table with the `CTX_CLS.TRAIN` procedure.

You then index the table to create a `CTXRULE` index. When documents arrive, you use the `MATCHES` operator to classify each document

- MATCHES SQL Query

- MATCHES PL/SQL Example

**See Also:**

[Classifying Documents in Oracle Text](classifying-documents-in-oracle-text.md)

##### 6.1.3.1 MATCHES SQL Query

A `MATCHES` query finds all rows in a query table that match a given document. Assuming that a `querytable` table is associated with a `CTXRULE` index, enter the following query:

    SELECT classification FROM querytable WHERE MATCHES(query_string,:doc_text) > 0;

The `:doc_text` bind variable contains the `CLOB` document to be classified.

Here is a simple example:

       create table queries (
          query_id      number,
          query_string  varchar2(80)
        );

        insert into queries values (1, 'oracle');
        insert into queries values (2, 'larry or ellison');
        insert into queries values (3, 'oracle and text');
        insert into queries values (4, 'market share');

        create index queryx on queries(query_string)
          indextype is ctxsys.ctxrule;

        select query_id from queries
         where matches(query_string,
                       'Oracle announced that its market share in databases
                        increased over the last year.')>0

This query returns queries 1 (the word oracle appears in the document) and 4 (the phrase market share appears in the document), but not 2 (neither the word larry nor the word ellison appears, and not 3 (there is no text in the document, so it does not match the query).

In this example, the document was passed in as a string for simplicity. Your document is typically passed in a bind variable.

The document text used in a `MATCHES` query can be `VARCHAR2` or `CLOB.` It does not accept `BLOB` input, so you cannot match filtered documents directly. Instead, you must filter the binary content to `CLOB` by using `AUTO_FILTER.` The following example makes two assumptions:

- The document data is in the `:doc_blob` bind variable.

- You have already defined `my_policy` that `CTX_DOC.POLICY_FILTER` can use.

For example:

      declare
        doc_text clob;
      begin
        -- create a temporary CLOB to hold the document text
        doc_text := dbms_lob.createtemporary(doc_text, TRUE, DBMS_LOB.SESSION);

        -- create a simple policy for this example
        ctx_ddl.create_preference(preference_name => 'fast_filter',
                            object_name       => 'AUTO_FILTER');
        ctx_ddl.set_attribute(preference_name => 'fast_filter',
                            attribute_name    => 'OUTPUT_FORMATTING',
                            attribute_value   => 'FALSE');
        ctx_ddl.create_policy(policy_name     => 'my_policy',
                            filter            => 'fast_filter);

        -- call ctx_doc.policy_filter to filter the BLOB to CLOB data
        ctx_doc.policy_filter('my_policy', :doc_blob, doc_text, FALSE);

        -- now do the matches query using the CLOB version
        for c1 in (select * from queries where matches(query_string, doc_text)>0)
        loop
          -- do what you need to do here
        end loop;

        dbms_lob.freetemporary(doc_text);
      end;

The `CTX_DOC.POLICY_FILTER` procedure filters the `BLOB` into the `CLOB` data, because you must get the text into a `CLOB` to enter a `MATCHES` query. It takes, as one argument, the name of a policy that you already created with `CTX_DDL.CREATE_POLICY`.

**See Also:**

[Oracle Text Reference](../ccref/CTX_DOC-package.md) for information on `CTX_DOC.POLICY_FILTER`

If your file is text in the database character set, then you can create a `BFILE` and load it to a `CLOB` by using the `DBMS_LOB.LOADFROMFILE` function, or you can use `UTL_FILE` to read the file into a temp `CLOB` locator.

If your file needs `AUTO_FILTER` filtering, then you can load the file into a `BLOB` instead and call `CTX_DOC.POLICY_FILTER`, as previously shown.

**See Also:**

[Classifying Documents in Oracle Text](classifying-documents-in-oracle-text.md) for more extended classification examples

##### 6.1.3.2 MATCHES PL/SQL Examples

The following example assumes that the `profiles` table of queries is associated with a `CTXRULE` index. It also assumes that the `newsfeed` table contains a set of news articles to be categorized.

This example loops through the `newsfeed` table, categorizing each article by using the `MATCHES` operator. The results are stored in the `results` table.

    PROMPT  Populate the category table based on newsfeed articles
    PROMPT
    set serveroutput on;
    declare
      mypk   number;
      mytitle varchar2(1000);
      myarticles clob;
      mycategory varchar2(100);
      cursor doccur is select pk,title,articles from newsfeed;
      cursor mycur is  select category from profiles where matches(rule, myarticles)>0;
      cursor rescur is select category, pk, title from results order by category,pk;

    begin
      dbms_output.enable(1000000);
      open doccur;
      loop
        fetch doccur into mypk, mytitle, myarticles;
        exit when doccur%notfound;
        open mycur;
        loop
          fetch mycur into mycategory;
          exit when mycur%notfound;
          insert into results values(mycategory, mypk, mytitle);
        end loop;
        close mycur;
        commit;
      end loop;
      close doccur;
      commit;

    end;

The following example displays the categorized articles by category.

    PROMPT  display the list of articles for every category
    PROMPT
    set serveroutput on;

    declare
      mypk   number;
      mytitle varchar2(1000);
      mycategory varchar2(100);
      cursor catcur is select category from profiles order by category;
      cursor rescur is select pk, title from results where category=mycategory order by pk;

    begin
      dbms_output.enable(1000000);
      open catcur;
      loop
        fetch catcur into mycategory;
        exit when catcur%notfound;
        dbms_output.put_line('********** CATEGORY: '||mycategory||' *************');
    open rescur;
        loop
          fetch rescur into mypk, mytitle;
          exit when rescur%notfound;
    dbms_output.put_line('**  ('||mypk||'). '||mytitle);
        end loop;
        close rescur;
        dbms_output.put_line('**');
    dbms_output.put_line('*******************************************************');
      end loop;
      close catcur;
    end;

**See Also:**

[Classifying Documents in Oracle Text](classifying-documents-in-oracle-text.md) for more extended classification examples

#### 6.1.4 Word and Phrase Queries

A word query is a query on a word or phrase. For example, to find all the rows in your text table that contain the word dog, enter a query specifying dog as your query term.

You can enter word queries with both `CONTAINS` and `CATSEARCH` SQL operators. However, phrase queries are interpreted differently.

- CONTAINS Phrase Queries: If multiple words are contained in a query expression, separated only by blank spaces (no operators), the string of words is considered a phrase. Oracle Text searches for the entire string during a query. For example, to find all documents that contain the phrase international law, enter your query with the phrase international law.

- CATSEARCH Phrase Queries: With the `CATSEARCH` operator, you insert the `AND` operator between words in phrases. For example, a query such as international law is interpreted as international AND law.

#### 6.1.5 Querying Stopwords

Stopwords are words for which Oracle Text does not create an index entry. They are usually common words in your language that are unlikely to be searched.

Oracle Text includes a default list of stopwords for your language. This list is called a stoplist. For example, in English, the words this and that are defined as stopwords in the default stoplist. You can modify the default stoplist or create new stoplists with the `CTX_DDL` package. You can also add stopwords after indexing with the `ALTER INDEX` statement.

You cannot query on a stopword itself or on a phrase composed of only stopwords. For example, a query on the word this returns no hits when this is defined as a stopword.

Because the Oracle Text index records the position of stopwords even though it does not create an index entry for them, you can query phrases that contain stopwords as well as indexable words, such as this boy talks to that girl.

When you include a stopword within your query phrase, the stopword matches any word. For example, the following query assumes that was is a stopword. It matches phrases such as Jack is big and Jack grew big. It also matches grew, even though it is not a stopword.

    'Jack was big'

Starting with Oracle Database 12c Release 2 (12.2), stopwords and unary operators on stopwords are ignored at the initial stages of a query result in different query results than earlier releases. For example, the following query does not return documents because `the` is a stopword and the `$` operator and the stopword are ignored during query processing:

    SQL> select count(1) from tabx where contains(text,'$the')>0;
     .
      COUNT(1)
     ----------
            0

The next query returns documents containing `first` because the `the` stopword and the `$` operator are ignored.

    SQL> select count(1) from tabx where contains(text,'first and $the')>0;
     .
      COUNT(1)
     ----------
            2

#### 6.1.6 ABOUT Queries and Themes

An `ABOUT` query is a query on a document theme. A document theme is a concept that is sufficiently developed in the text. For example, an `ABOUT` query on US politics might return documents containing information about US presidential elections and US foreign policy. Documents need not contain the exact phrase US politics to be returned.

During indexing, document themes are derived from the knowledge base, which is a hierarchical list of categories and concepts that represents a view of the world. Some examples of themes in the knowledge catalog are concrete concepts such as jazz music, football, or Nelson Mandela. Themes can also be abstract concepts such as happiness or honesty.

During indexing, the system can also identify and index document themes that are sufficiently developed in the document but that do not exist in the knowledge base.

You can augment the knowledge base to define concepts and terms specific to your industry or query application. When you do so, `ABOUT` queries are more precise for the added concepts.

`ABOUT` queries perform best when you create a theme component in your index. Theme components are created by default for English and French.

**See Also:**

[Oracle Text Reference](../ccref/oracle-text-CONTAINS-query-operators.md)

##### Querying Stopthemes

Oracle Text enables you to query on themes with the `ABOUT` operator. A stoptheme is a theme that is not to be indexed. You can add and remove stopthemes with the `CTX_DDL` package. You can add stopthemes after indexing with the `ALTER INDEX` statement.

### 6.2 Oracle Text Query Features

Oracle Text has various query features. You can use these query features in your query application.

- Query Expressions

- Case-Sensitive Searching

- Query Feedback

- Query Explain Plan

- Using a Thesaurus in Queries

- About Document Section Searching

- Using Query Templates

- Query Analysis

- Other Query Features

#### 6.2.1 Query Expressions

A query expression is everything in between the single quotes in the `text_query` argument of the `CONTAINS` or `CATSEARCH` operator. The contents of a query expression in a `CONTAINS` query differs from the contents of a `CATSEARCH` operator.

- CONTAINS Operators

- CATSEARCH Operator

- MATCHES Operator

##### 6.2.1.1 CONTAINS Operators

A `CONTAINS` query expression can contain query operators that enable logical, proximity, thesaural, fuzzy, and wildcard searching. Querying with stored expressions is also possible. Within the query expression, you can use grouping characters to alter operator precedence. This book refers to these operators as the `CONTEXT` grammar.

With `CONTAINS`, you can also use the `ABOUT` query to query document themes.

**See Also:**

"[The CONTEXT Grammar](working-with-CONTEXT-and-CTXCAT-grammars-in-oracle-text.md)"

##### 6.2.1.2 CATSEARCH Operator

With the `CATSEARCH` operator, you specify your query expression with the `text_query` argument and your optional structured criteria with the `structured_query` argument. The `text_query` argument enables you to query words and phrases. You can use logical operations, such as logical and, or, and not. This book refers to these operators as the `CTXCAT` grammar.

If you want to use the much richer set of operators supported by the `CONTEXT` grammar, you can use the query template feature with `CATSEARCH.`

With `structured_query` argument, you specify your structured criteria. You can use the following SQL operations:

- `=`

- `<=`

- `>=`

- `>`

- `<`

- `IN`

- `BETWEEN`

You can also use the `ORDER BY` clause to order your output.

**See Also:**

"[The CTXCAT Grammar](working-with-CONTEXT-and-CTXCAT-grammars-in-oracle-text.md)"

##### 6.2.1.3 MATCHES Operator

Unlike `CONTAINS` and `CATSEARCH,` `MATCHES` does not take a query expression as input.

Instead, the `MATCHES` operator takes a document as input and finds all rows in a query (rule) table that match it. As such, you can use `MATCHES` to classify documents according to the rules they match.

**See Also:**

"Querying with MATCHES"

#### 6.2.2 Case-Sensitive Searching

Oracle Text supports case-sensitivity for word and `ABOUT` queries.

Word queries are not case-insensitive by default. This means that a query on the term dog returns the rows in your text table that contain the word dog, but not Dog or DOG.

You can enable or disable case-sensitive searching with the `MIXED_CASE` attribute in your `BASIC_LEXER` index preference. With a case-sensitive index, your queries must be entered in exact case. For example, a query on Dog matches only documents with Dog. Documents with dog or DOG are not returned as hits.

To enable case-insensitive searching, set the `MIXED_CASE` attribute in your `BASIC_LEXER` index preference to `NO.`

**Note:**

If you enable case-sensitivity for word queries and you query a phrase containing stopwords and indexable words, then you must specify the correct case for the stopwords. For example, a query on the dog does not return text that contains The Dog, assuming that the is a stopword.

`ABOUT` queries give the best results when your query is formulated with proper case because the normalization of your query is based on the knowledge catalog. The knowledge catalog is case-sensitive. Attention to case is required, especially for words that have different meanings depending on case, such as turkey the bird and Turkey the country.

However, you do not have to enter your query in exact case to obtain relevant results from an `ABOUT` query. The system does its best to interpret your query. For example, if you enter a query of `ORACLE` and the system does not find this concept in the knowledge catalog, the system might use Oracle as a related concept for lookup.

#### 6.2.3 Query Feedback

Feedback provides broader-term, narrower term, and related term information for a specified query with a `CONTEXT` index. You obtain this information programatically with the `CTX_QUERY.HFEEDBACK` procedure.

Broader term, narrower term, and related term information is useful for suggesting other query terms to the user in your query application.

The returned feedback information is obtained from the knowledge base and contains only those terms that are also in the index. This process increases the chances that terms returned from `HFEEDBACK` produce hits over the currently indexed document set.

**See Also:**

[Oracle Text Reference](../ccref/CTX_QUERY-package.md) for more information about using `CTX_QUERY.HFEEDBACK`

#### 6.2.4 Query Explain Plan

Explain plan information provides a graphical representation of the parse tree for a `CONTAINS` query expression. You can obtain this information programatically with the `CTX_QUERY.EXPLAIN` procedure.

Explain plan information tells you how a query is expanded and parsed without having the system execute the query. Obtaining explain information is useful for knowing the expansion for a particular stem, wildcard, thesaurus, fuzzy, soundex, or `ABOUT` query. Parse trees also show the following information:

- Order of execution

- `ABOUT` query normalization

- Query expression optimization

- Stopword transformations

- Breakdown of composite-word tokens for supported languages

  **See Also:**

  [Oracle Text Reference](../ccref/CTX_QUERY-package.md) for more information about using `CTX_QUERY.EXPLAIN`

#### 6.2.5 Using a Thesaurus in Queries

Oracle Text enables you to define a thesaurus for your query application and process queries more intelligently.

Because users might not know which words represent a topic, you can define synonyms or narrower terms for likely query terms. You can use the thesaurus operators to expand your query to include thesaurus terms.

**See Also:**

[Working With a Thesaurus in Oracle Text](working-with-thesaurus-in-oracle-text.md)

#### 6.2.6 Document Section Searching

Section searching enables you to narrow text queries down to sections within documents.

You can implement section searching when your documents have internal structure, such as HTML and XML documents. For example, you can define a section for the \<H1\> tag that enables you to query within this section by using the `WITHIN` operator.

You can set the system to automatically create sections from XML documents.

You can also define attribute sections to search attribute text in XML documents.

**Note:**

Section searching is supported for only word queries with a `CONTEXT` index.

**See Also:**

[Searching Document Sections in Oracle Text](searching-document-sections-in-oracle-text.md)

#### 6.2.7 Using Query Templates

Query templates are an alternative to the existing query languages. Rather than passing a query string to `CONTAINS` or `CATSEARCH`, you pass a structured document that contains the query string in a tagged element. Within this structured document, or query template, you can enable additional query features.

- Query Rewrite

- Query Relaxation

- Query Language

- Ordering By SDATA Sections

- Alternative and User-defined Scoring

- Alternative Grammar

##### 6.2.7.1 Query Rewrite

Query applications sometimes parse end-user queries, interpreting a query string in one or more ways by using different operator combinations. For example, if a user enters a query of kukui nut, your application enters the {kukui nut} and {kukui or nut} queries to increase recall.

The query rewrite feature enables you to submit a single query that expands the original query into the rewritten versions. The results are returned with no duplication.

You specify your rewrite sequences with the query template feature. The rewritten versions of the query are executed efficiently with a single call to `CONTAINS` or `CATSEARCH.`

The following template defines a query rewrite sequence. The query of {kukui nut} is rewritten as follows:

{kukui} {nut}

{kukui} ; {nut}

{kukui} AND {nut}

{kukui} ACCUM {nut}

The following is the query rewrite template for these transformations:

    select id from docs where CONTAINS (text,
     '<query>
       <textquery lang="ENGLISH" grammar="CONTEXT"> kukui nut
         <progression>
           <seq><rewrite>transform((TOKENS, "{", "}", " "))</rewrite></seq>
           <seq><rewrite>transform((TOKENS, "{", "}", " ; "))</rewrite></seq>
           <seq><rewrite>transform((TOKENS, "{", "}", "AND"))</rewrite></seq>
           <seq><rewrite>transform((TOKENS, "{", "}", "ACCUM"))</rewrite></seq>
         </progression>
       </textquery>
      <score datatype="INTEGER" algorithm="COUNT"/>
    </query>')>0;

##### 6.2.7.2 Query Relaxation

The query relaxation feature enables your application to execute the most restrictive version of a query first and progressively relax the query until the required number of hits are obtained.

For example, your application searches first on green pen and then the query is relaxed to green NEAR pen to obtain more hits.

The following query template defines a query relaxation sequence. The query of green pen is entered in sequence.

{green} {pen}

{green} NEAR {pen}

{green} AND {pen}

{green} ACCUM {pen}

The following is the query relaxation template for these transformations:

    select id from docs where CONTAINS (text,
     '<query>
       <textquery lang="ENGLISH" grammar="CONTEXT">
         <progression>
           <seq>{green} {pen}</seq>
           <seq>{green} NEAR {pen}</seq>
           <seq>{green} AND {pen}</seq>
           <seq>{green} ACCUM {pen}</seq>
         </progression>
       </textquery>
       <score datatype="INTEGER" algorithm="COUNT"/>
    </query>')>0;

Query hits are returned in this sequence with no duplication as long as the application needs results.

Query relaxation is most effective when your application needs the top-N hits to a query, which you can obtain with the `DOMAIN_INDEX_SORT` hint or in a PL/SQL cursor.

Using query templating to relax a query is more efficient than reexecuting a query.

##### 6.2.7.3 Query Language

When you use `MULTI_LEXER` to index a column containing documents in different languages, you can specify which language lexer to use during querying. You do so by using the `lang` parameter in the query template, which specifies the document-level lexer.

    select id from docs where CONTAINS (text,
    '<query><textquery lang="french">bon soir</textquery></query>')>0;

**See Also:**

[Oracle Text Reference](../ccref/oracle-text-SQL-statements-and-operators.md) for information on `LANGUAGE` and `lang` with ALTER INDEX and document sublexer

##### 6.2.7.4 Ordering by SDATA Sections

You can order the query results according to the content of `SDATA` sections by using the `<order>` and `<orderkey>` elements of the query template.

In the following example, the first level of ordering is performed on the `SDATA` `price` section, which is sorted in ascending order. The second and third level of ordering are performed by the `SDATA` `pub_date` section and score, both of which are sorted in descending order.

    select id from docs where CONTAINS (text, '
    <query>
       <textquery lang="ENGLISH" grammar="CONTEXT"> Oracle </textquery>
       <score datatype="INTEGER" algorithm="COUNT"/>
       <order>
           <orderkey> SDATA(price) ASC </orderkey>
           <orderkey> SDATA(pub_date) DESC </orderKey>
           <orderkey> Score DESC </orderkey>
       </order>
    </query>', 1)>0;

**Note:**

- You can add additional `SDATA` sections to an index. Refer to the `ADD SDATA SECTION` parameter string under `ALTER INDEX` in [Oracle Text Reference.](../ccref/oracle-text-SQL-statements-and-operators.md)

- Documents that were indexed before adding an `SDATA` section do not reflect this new preference. Rebuild the index in this case.

**See Also:**

[Oracle Text Reference](../ccref/oracle-text-SQL-statements-and-operators.md) for syntax of `<order>` and `<orderkey>` elements of the query template

##### 6.2.7.5 Alternative and User-Defined Scoring

You can use query templating to specify alternative scoring algorithms. Those algorithms help you customize how `CONTAINS` is scored. They also enable `SDATA` to be used as part of the scoring expressions. In this way, you can mathematically define the scoring expression by using not only predefined scoring components, but also `SDATA` components.

With alternative user-defined scoring, you can specify:

- Scoring expressions of terms by defining arithmetic expressions that define how the query should be scored, using

  - predefined scoring algorithms: `DISCRETE`, `OCCURRENCE`, `RELEVANCE`, and `COMPLETION`

  - arithmetic operations: plus, minus, multiply, divide

  - arithmetic functions: `ABS(n)`, finding the absolute value of n ; `LOG(n)`, finding the base-10 logarithmic value of n

  - Numeric literals

- Scoring expressions at the term level

- Terms that should not be taken into account when calculating the score

- How the score from child elements of `OR` and `AND` operators should be merged

- Use

You can also use the `SDATA` that stores numeric or `DATETIME` values to affect the final score of the document.

The following example specifies an alternative scoring algorithm:

    select id from docs where CONTAINS (text,
    '<query>
     <textquery grammar="CONTEXT" lang="english"> mustang  </textquery>
     <score datatype="float" algorithm="DEFAULT"/>
    </query>')>0

The following query templating example includes `SDATA` values as part of the final score:

    select id from docs where CONTAINS (text,
    '<query>
    <textquery grammar="CONTEXT" lang="english"> mustang </textquery>
    <score datatype="float" algorithm="DEFAULT" normalization_expr ="doc_score+SDATA(price)"/>
    </query>')>0"

**See Also:**

"[Using DEFINESCORE and DEFINEMERGE for User-defined Scoring](working-with-CONTEXT-and-CTXCAT-grammars-in-oracle-text.md)"

##### 6.2.7.6 Alternative Grammar

Query templating enables you to use the `CONTEXT` grammar with `CATSEARCH` queries and vice versa.

    select id from docs where CONTAINS (text,
    '<query>
      <textquery grammar="CTXCAT">San Diego</textquery>
      <score datatype="integer"/>
    </query>')>0;

#### 6.2.8 Query Analysis

Oracle Text enables you to create a log of queries and to analyze the queries. For example, suppose you have an application that searches a database of large animals, and your analysis of its queries shows that users search for the word mouse. This analysis shows you that you should rewrite your application to avoid returning an unsuccessful search. Instead, a search for mouse redirects users to a database of small animals.

With query analysis, you can find out:

- Which queries were made

- Which queries were successful

- Which queries were unsuccessful

- How many times each query was made

You can combine these factors in various ways, such as determining the 50 most frequent unsuccessful queries made by your application.

You start query logging with `CTX_OUTPUT.START_QUERY_LOG.` The query log contains all queries made to all `CONTEXT` indexes that the program is using until a `CTX_OUTPUT.END_QUERY_LOG` procedure is entered. Use `CTX_REPORT.QUERY_LOG_SUMMARY` to get a report of queries.

**See Also:**

[Oracle Text Reference](../ccref/oracle-text-CONTAINS-query-operators.md) for syntax and examples for these procedures

#### 6.2.9 Other Query Features

In your query application, you can use other query features such as proximity searching. Table 6-1 lists some of these features.

Table 6-1 Other Oracle Text Query Features

| Feature                                                                                 | Description                                                                                                                                                                                                                                                                                       | Implement With                                                                                                                    |
|:----------------------------------------------------------------------------------------|:--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|:----------------------------------------------------------------------------------------------------------------------------------|
| Case-Sensitive Searching                                                                | Enables you to search on words or phrases exactly as they are entered in the query. For example, a search on Roman returns documents that contain Roman and not roman.                                                                                                                            | `BASIC_LEXER` when you create the index                                                                                           |
| Base-Letter Conversion                                                                  | Queries words with or without diacritical marks such as tildes, accents, and umlauts. For example, with a Spanish base-letter index, a query of energía matches documents containing both energía and energia.                                                                                    | `BASIC_LEXER` when you create the index                                                                                           |
| Word Decompounding<br>(German and Dutch)                                                | Enables searching on words that contain the specified term as subcomposite.                                                                                                                                                                                                                       | `BASIC_LEXER` when you create the index                                                                                           |
| Alternate Spelling<br>(German, Dutch, and Swedish)                                      | Searches on alternate spellings of words.                                                                                                                                                                                                                                                         | `BASIC_LEXER` when you create the index                                                                                           |
| Proximity Searching                                                                     | Searches for words near one another.                                                                                                                                                                                                                                                              | `NEAR` operator when you enter the query                                                                                          |
| Expanded operator containing the functionality of `PHRASE`, `NEAR` and `AND` operators. | Breaks a document into clumps based on the given query. Each clump is classified based on a primary feature, and is scored based on secondary features. The final document score adds clump scores such that the ordering of primary features determines the initial ordering of document scores. | `NEAR2` operator when you enter the query                                                                                         |
| Stemming                                                                                | Searches for words with the same root as the specified term.                                                                                                                                                                                                                                      | \$ operator at when you enter the query                                                                                           |
| Fuzzy Searching                                                                         | Searches for words that have a similar spelling as the specified term.                                                                                                                                                                                                                            | `FUZZY` operator when you enter the query                                                                                         |
| Query Explain Plan                                                                      | Generates query parse information.                                                                                                                                                                                                                                                                | `CTX_QUERY.EXPLAIN` PL/SQL procedure after you index                                                                              |
| Hierarchical Query Feedback                                                             | Generates broader term, narrower term and related term information for a query.                                                                                                                                                                                                                   | `CTX_QUERY.HFEEDBACK` PL/SQL procedure after you index                                                                            |
| Browse index                                                                            | Browses the words around a seed word in the index.                                                                                                                                                                                                                                                | `CTX_QUERY.BROWSE_WORDS` PL/SQL after you index                                                                                   |
| Count hits                                                                              | Counts the number of hits in a query.                                                                                                                                                                                                                                                             | `CTX_QUERY.COUNT_HITS` PL/SQL procedure after you index                                                                           |
| Stored Query Expression                                                                 | Stores the text of a query expression for later reuse in another query.                                                                                                                                                                                                                           | `CTX_QUERY.STORE_SQE` PL/SQL procedure after you index                                                                            |
| Thesaural Queries                                                                       | Uses a thesaurus to expand queries.                                                                                                                                                                                                                                                               | Thesaurus operators such as `SYN` and `BT` as well as the `ABOUT` operator<br>(Use `CTX_THES` package to maintain the thesaurus.) |
