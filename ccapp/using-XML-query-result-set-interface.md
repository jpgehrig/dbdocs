The `CTX_QUERY.RESULT_SET` procedure executes an XML query and generates a result set in XML.

**Note:**

The Oracle Text Result Set Interface queries are not supported on shard catalog instances.

- Overview of the XML Query Result Set Interface

- Using the XML Query Result Set Interface

- Creating XML-Only Applications with Oracle Text

- Example of a Result Set Descriptor

- Identifying Collocates

### 15.1 Overview of the XML Query Result Set Interface

The XML Query Result Set Interface (RSI) enables you to perform queries in XML and return results as XML, avoiding the SQL layer and requirement to work within `SELECT` semantics. The RSI uses a simple Oracle Text query and an XML result set descriptor, where the hitlist is returned in XML according to the result set descriptor. The XML Query RSI uses `SDATA` sections for grouping and counting.

In applications, a page of search results can consist of many disparate elements, such as metadata of the first few documents, total hit counts, and per-word hit counts. Each extra call takes time to reparse the query and look up index metadata. Additionally, some search operations, such as iterative query refinement, are difficult for SQL. If it is even possible to construct a SQL statement to produce the desired results, such SQL is usually suboptimal.

The XML Query RSI is able to produce the various kinds of data needed for a page of search results all at once, thus improving performance by sharing overhead. The RSI can also return data views that are difficult to express in SQL.

### 15.2 Using the XML Query Result Set Interface

The `CTX_QUERY.RESULT_SET()` and `CTX_QUERY.RESULT_SET_CLOB_QUERY()` APIs enable you to obtain query results with a single query, rather than running multiple `CONTAINS()` queries to achieve the same result. The two APIs are identical except that one uses a `VARCHAR2` query parameter, and the other uses a `CLOB` query parameter to allow for longer queries.

For example, to display a search result page, you must first get the following information:

- Top 20 hit list sorted by date and relevancy

- Total number of hits for the given Oracle Text query

- Counts group by publication date

- Counts group by author

Assume the following table definition for storing documents to be searched:

    create table docs (
      docid    number,
      author   varchar2(30),
      pubdate  date,
      title    varchar2(60),  doc      clob);

Assume the following Oracle Text Index definition:

    create index docidx on docs(doc) indextype is ctxsys.context
    filter by author, pubdate, title
    order by pubdate;

With these definitions, you can issue four SQL statements to obtain the four pieces of information needed for displaying the search result page:

    -- Get top 20 hits sorted by date and relevancy
    select * from
      (select /*+ first_rows */ rowid, title, author, pubdate
       from docs where contains(doc, 'oracle',1)>0
       order by pubdate desc, score(1) desc)
    where rownum < 21;

    -- Get total number of hits for the given Oracle Text query
    select count(*) from docs where contains(doc, 'oracle',1)>0;

    -- Get counts group by publication date
    select pubdate, count(*) from docs where contains(doc, 'oracle',1)>0
    group by pubdate;

    -- Get counts group by author
    select author, count(*) from docs where contains(doc, 'oracle',1)>0 group by author;

As you can see, using separate SQL statements results in a resource-intensive query, because you run the same query four times. However, if you use `CTX_QUERY.RESULT_SET()`, then you can enter all of the information in one single Oracle Text query:

    declare
       rs clob;
    begin
       dbms_lob.createtemporary(rs, true, dbms_lob.session);
       ctx_query.result_set('docidx', 'oracle text performance tuning', '
       <ctx_result_set_descriptor>
        <count/>
        <hitlist start_hit_num="1" end_hit_num="20" order="pubDate desc,
            score desc">
          <score/>
          <rowid/>
             <sdata name="title"/>
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

    -- Put in your code here to process the Output Result Set XML
       dbms_lob.freetemporary(rs);
    exception
       when others then
        dbms_lob.freetemporary(rs);
        raise;
    end;
    /

The result set output is XML that as the information required to construct the search result page:

    <ctx_result_set>
      <hitlist>
        <hit>
          <score>90</score>
          <rowid>AAAPoEAABAAAMWsAAC</rowid>
          <sdata name="TITLE"> Article 8 </sdata>
          <sdata name="AUTHOR">John</sdata>
          <sdata name="PUBDATE">2001-01-03 00:00:00</sdata>
        </hit>
        <hit>
          <score>86</score>
          <rowid>AAAPoEAABAAAMWsAAG</rowid>
          <sdata name="TITLE"> Article 20 </sdata>
          <sdata name="AUTHOR">John</sdata>
          <sdata name="PUBDATE">2001-01-03 00:00:00</sdata>
        </hit>
        <hit>
          <score>78</score>
          <rowid>AAAPoEAABAAAMWsAAK</rowid>
          <sdata name="TITLE"> Article 17 </sdata>
          <sdata name="AUTHOR">John</sdata>
          <sdata name="PUBDATE">2001-01-03 00:00:00</sdata>
        </hit>
        <hit>
          <score>77</score>
          <rowid>AAAPoEAABAAAMWsAAO</rowid>
          <sdata name="TITLE"> Article 37 </sdata>
          <sdata name="AUTHOR">John</sdata>
          <sdata name="PUBDATE">2001-01-03 00:00:00</sdata>
        </hit>
    ...
        <hit>
          <score>72</score>
          <rowid>AAAPoEAABAAAMWsAAS</rowid>
          <sdata name="TITLE"> Article 56 </sdata>
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

**See Also:**

[Oracle Text Reference](../ccref/preface.md) for syntax details and more information on `CTX_QUERY.RESULT_SET`

### 15.3 Creating XML-Only Applications with Oracle Text

Although it is common to create applications by using SQL `SELECT` statements with the `CONTAINS` clause, it is not the most efficient method. An alternative method is to use the XML-based RSI. With this method, you can obtain summary information (such as the total number of hits) without fetching all results of the query.

To use the RSI, you specify a Result Set Descriptor (RSD). The RSD declares the information to be returned, which can consist of:

- Total result count of the query

- Hitlist

- Summary information over `SDATA` fields

In turn, the hitlist consists of repeating elements, each of which may contain:

- Rowid of the hit

- SDATA fields from the hit

**Related Topics**

- Example of a Result Set Descriptor

### 15.4 Example of a Result Set Descriptor

This example shows how to use an RSD. The following example requests a hitlist with the top 10 hits (ordered by score) and the count of the total number of results.

    <ctx_result_set_descriptor>
      <hitlist start_hit_num="1" end_hit_num="10" order="SCORE DESC">
        <rowid />
        <sdata name="title" />
        <sdata name="author" />
        <sdata name="articledate" />
        <snippet radius="20" max_length="160" starttag="&lt;b&gt;" endtag="&lt;/b&gt;" />
      </hitlist>
      <count />
    </ctx_result_set_descriptor>

For each hit, you are requesting the `rowid` (which you could use to fetch further information about the row, if necessary), the contents of the `SDATA` fields or the `title,` `author,` and `articledate` columns, and a snippet (which is a short summary with keywords highlighted, in this case by `<b>`...`</b>`).

### 15.5 Identifying Collocates

Collocates are a group of words that frequently co-occur in a document. They provide a quick summary of other keywords or concepts that are related to a specified keyword. You can then use the other keywords in queries to fetch more relevant results.

You identify collocates based on a search query. For each document that is returned by the query, snippets of text around the search keyword are automatically extracted. Next, the words in these snippets are correlated to the query keyword by using statistical measures and, depending on how frequently the extracted words occur in the overall document set, a score is assigned to each returned co-occurring word.

Use the RSI to identify collocates. You can specify the number of co-occurring words that must be returned by the query. You can also specify whether to identify collocates that are common nouns or collocates that emphasize uniqueness. Synonyms of the specified search keyword can also be returned.

**Note:**

Collocates are supported only for `BASIC_LEXER.`

To identify collocates:

1.  Create the document set table for the query.
2.  Create an Oracle Text index on the document set table.
3.  Use the XML Query RSI to define and input a query that identifies collocates. Include the `collocates` element with the required attributes.

Example 15-1 Identifying Collocates Within a Document Set

In this example, the keyword used to query documents in a data set is ‘Nobel.’ Oracle Text searches for occurrences of this keyword in the document set. In addition to the result set, use collocates to search for five common words that co-occur with ‘Nobel.’ Use the `max_words` attribute to identify the number of collocates to be generated. Set the `use_tscore` attribute to `TRUE` to specify that common words must be identified for the collocates. The number of words to pick on either side of the keyword in order to identify collocates is 10.

The following is the input RSI descriptor that is used to determine collocates:

    declare
    rsd varchar2(32767);
     begin
      ctx_query.result_set('tdrbnbsan01idx', 'nobel',
      <ctx_result_set_descriptor>
      <collocates radius = "10" max_words="5" use_tscore="TRUE"/>
      </ctx_result_set_descriptor>',
      :rs);
      end;
    /

Here is the output result set for the query:

    <ctx_result_set>
    <collocates>
        <collocation>
           <word>PRIZE</word>
           <score>82</score>
        </collocation>
        <collocation>
           <word>LAUREATE</word>
           <score>70</score>
        </collocation>
        <collocation>
           <word>NOBELPRIZE</word>
           <score>44</score>
        </collocation>
        <collocation>
           <word>AWARD</word>
           <score>42</score>
        </collocation>
        <collocation>
           <word>ORG</word>
           <score>41</score>
        </collocation
    </collocates>
    </ctx_result_set>

For ‘Nobel,’ the top five common collocates, in order, are Prize, Laureate, Nobelprize, award, and org. Each word is assigned a score that indicates the frequency of occurrence. Collocates are always returned after any `hitlist` elements are returned.

If you set `use_tscore` to `FALSE` in the same example, then less common (unique) words are identified. Here is the output result set:

    <ctx_result_set>
    <collocates>
        <collocation>
           <word>MOLA</word>
           <score>110</score>
        </collocation>
        <collocation>
           <word>BISMARCK</word>
           <score>89</score>
        </collocation>
        <collocation>
           <word>COLONNA</word>
           <score>67</score>
        </collocation>
        <collocation>
           <word>LYNEN</word>
           <score>55</score>
        </collocation>
        <collocation>
           <word>TIMBERGEN</word>
           <score>25</score>
        </collocation>
        </collocates>
    </ctx_result_set>

**See Also:**

[Oracle Text Reference](../ccref/CTX_QUERY-package.md) for information about attributes used with collocates
