## 9  CTX_DOC Package

The `CTX_DOC` PL/SQL package provides procedures and functions for requesting document services, such as highlighting extracted text or generating a list of themes for a document.

- About CTX_DOC Package Procedures

The `CTX_DOC` package includes the following procedures and functions:

| Name                  | Description                                                                                                                     |
|:----------------------|:--------------------------------------------------------------------------------------------------------------------------------|
| FILTER                | Generates a plain text or HTML version of a document.                                                                           |
| GIST                  | Generates a Gist or theme summaries for a document.                                                                             |
| HIGHLIGHT             | Generates plain text or HTML highlighting offset information for a document.                                                    |
| IFILTER               | Generates a plain text version of binary data. Can be called from a `USER_DATASTORE` procedure.                                 |
| MARKUP                | Generates a plain text or HTML version of a document with query terms highlighted.                                              |
| PKENCODE              | Encodes a composite textkey string (value) for use in other `CTX_DOC` procedures.                                               |
| POLICY_FILTER         | Generates a plain text or HTML version of a document, without requiring an index.                                               |
| POLICY_GIST           | Generates a Gist or theme summaries for a document, without requiring an index.                                                 |
| POLICY_HIGHLIGHT      | Generates plain text or HTML highlighting offset information for a document, without requiring an index.                        |
| POLICY_LANGUAGES      | Provides the ability to fetch the language for a section of text.                                                               |
| POLICY_MARKUP         | Generates a plain text or HTML version of a document with query terms highlighted, without requiring an index.                  |
| POLICY_NOUN_PHRASES   | Extracts noun phrases for a document.                                                                                           |
| POLICY_PART_OF_SPEECH | Extracts the part of speech for each word in a document.                                                                        |
| POLICY_SNIPPET        | Generates a concordance for a document, based on query terms, without requiring an index.                                       |
| POLICY_STEMS          | Extracts stems for each word in a body of text.                                                                                 |
| POLICY_THEMES         | Generates a list of themes for a document, without requiring an index.                                                          |
| POLICY_TOKENS         | Generates all index tokens for a document, without requiring an index.                                                          |
| SENTIMENT             | Performs sentiment analysis for a single document and provides a separate sentiment score for each segment within the document. |
| SENTIMENT_AGGREGATE   | Performs sentiment analysis for a single document and provides an aggregate sentiment score for the entire document.            |
| SET_KEY_TYPE          | Sets `CTX_DOC` procedures to accept rowid or primary key document identifiers.                                                  |
| SNIPPET               | Generates a concordance for a document, based on query terms.                                                                   |
| THEMES                | Generates a list of themes for a document.                                                                                      |
| TOKENS                | Generates all index tokens for a document.                                                                                      |

The performance of the procedures SNIPPET, HIGHLIGHT, and MARKUP can be improved by using the forward index feature, and the performance of the procedures FILTER, GIST, THEMES. TOKENS can be improved by using the save copy feature of Oracle Text.

**See Also:**

[Oracle Text Application Developer's Guide](../ccapp/indexing-with-oracle-text.md) for more information about forward index and save copy features

### 9.1 About CTX_DOC Package Procedures

Many of the `CTX_DOC` PL/SQL package procedures exist in two versions: those that make use of indexes, and those that do not. Those that do not make use of indexes are called "policy-based" procedures. They are offered because there are times when you may want to use document services on a single document without creating a CONTEXT index in advance. Policy-based procedures enable you to do this.

The policy\_\* procedures mirror the conventional in-memory document services and are used with `policy_name` replacing `index_ name`, and document of type `VARCHAR2`, `CLOB`, `BLOB`, or `BFILE` replacing `textkey`. Thus, you need not create an index to obtain document services output with these procedures.

For the procedures that generate character offsets and lengths, such as `HIGHLIGHT` and `TOKENS`, Oracle Text follows USC-2 codepoint semantics.

**Note:**

The APIs in the `CTX_DOC` package do not support identifiers that are prefixed with the schema or the owner name.

### 9.2 FILTER

Use the `CTX_DOC.FILTER` procedure to generate either a plain text or HTML version of a document.

You can store the rendered document in either a result table or in memory. This procedure is generally called after a query, from which you identify the document to be filtered.

**Note:**

The resultant HTML document does not include graphics.

#### Syntax 1: In-memory Result Storage

    exec CTX_DOC.FILTER(
              index_name  IN VARCHAR2,
              textkey     IN VARCHAR2,
              restab      IN OUT NOCOPY CLOB,
              plaintext   IN BOOLEAN DEFAULT FALSE,
              use_saved_copy IN NUMBER DEFAULT CTX_DOC.SAVE_COPY_FALLBACK);

#### Syntax 2: Result Table Storage

    exec CTX_DOC.FILTER(
              index_name  IN VARCHAR2,
              textkey     IN VARCHAR2,
              restab      IN VARCHAR2,
              query_id    IN NUMBER DEFAULT 0,
              plaintext   IN BOOLEAN DEFAULT FALSE,
              use_saved_copy IN NUMBER DEFAULT CTX_DOC.SAVE_COPY_FALLBACK);

index_name
Specify the name of the index associated with the text column containing the document identified by `textkey`.

textkey
Specify the unique identifier (usually the primary key) for the document.

The `textkey` parameter can be as follows:

- a single column primary key value

- encoded specification for a composite (multiple column) primary key. Use CTX_DOC.PKENCODE

- the rowid of the row containing the document

Toggle between primary key and rowid identification using CTX_DOC.SET_KEY_TYPE.

restab
You can specify that this procedure store the marked-up text to either a table or to an in-memory `CLOB`.

To store results to a table, specify the name of the table. The table to which you want to store results must exist before you make this call.

**See Also:**

"[Filter Table](oracle-text-result-tables.md)" in [Oracle Text Result Tables](oracle-text-result-tables.md) for more information about the structure of the filter result table

To store results in memory, specify the name of the `CLOB` locator. If `restab` is `NULL`, then a temporary `CLOB` is allocated and returned. You must de-allocate the locator after using it with `DBMS_LOB.FREETEMPORARY()`.

If `restab` is not `NULL`, then the `CLOB` is truncated before the operation.

query_id
Specify an identifier to use to identify the row inserted into `restab`.

When `query_id` is not specified or set to `NULL`, it defaults to 0. You must manually truncate the table specified in `restab`.

plaintext
Specify `TRUE` to generate a plaintext version of the document. Specify `FALSE` to generate an HTML version of the document if you are using the `AUTO_FILTER` filter or indexing HTML documents.

use_saved_copy
Specify whether to refer to the \$D table to fetch the copy of the document, and what action to take when the copy of the document is not available in the \$D table.

You can specify one of the following values for the `use_saved_copy` parameter:

- `CTX_DOC.SAVE_COPY_FALLBACK`: Fetch the copy of the document from the \$D table. If the copy of the document is not present in the \$D table, then fetch the document from the datastore.

- `CTX_DOC.SAVE_COPY_ERROR`: Fetch the copy of the document from the \$D table. If the `SAVE_COPY` option of the index is set to `none` and the document is not present in the \$D table, then show the `CTX_DOC.SAVE_COPY_ERROR` error. If the `SAVE_COPY` option of the index is set to `plaintext` or `filtered` and the document is not present in the \$D table, then show the `nodoc_err` error. If the document is present in the \$D table, then retrieve the document from the datastore.

- `CTX_DOC.SAVE_COPY_IGNORE`: Always fetch the document from the datastore.

The default value is `CTX_DOC.SAVE_COPY_FALLBACK`.

#### Example

In-Memory Filter

The following code shows how to filter a document to HTML in memory.

    declare
    mklob clob;
    amt number := 40;
    line varchar2(80);

    begin
     ctx_doc.filter('myindex','1', mklob, FALSE);
     -- mklob is NULL when passed-in, so ctx-doc.filter will allocate a temporary
     -- CLOB for us and place the results there.
     dbms_lob.read(mklob, amt, 1, line);
     dbms_output.put_line('FIRST 40 CHARS ARE:'||line);
     -- have to de-allocate the temp lob
     dbms_lob.freetemporary(mklob);
     end;

Create the filter result table to store the filtered document as follows:

    create table filtertab (query_id  number,
                            document  clob);

To obtain a plaintext version of document with textkey 20, enter the following statement:

    begin
    ctx_doc.filter('newsindex', '20', 'filtertab', '0', TRUE);
    end;

### 9.3 GIST

Use the `CTX_DOC.GIST` procedure to generate gist and theme summaries for a document. You can generate paragraph-level or sentence-level gists or theme summaries.

#### Syntax 1: In-Memory Storage

    CTX_DOC.GIST(

    index_name    IN VARCHAR2,
    textkey       IN VARCHAR2,
    restab        IN OUT CLOB,
    glevel        IN VARCHAR2 DEFAULT 'P',
    pov           IN VARCHAR2 DEFAULT 'GENERIC',
    numParagraphs IN NUMBER DEFAULT 16,
    maxPercent    IN NUMBER DEFAULT 10,
    num_themes    IN NUMBER DEFAULT 50,
    use_saved_copy IN NUMBER DEFAULT CTX_DOC.SAVE_COPY_FALLBACK);

#### Syntax 2: Result Table Storage

    CTX_DOC.GIST(

    index_name    IN VARCHAR2,
    textkey       IN VARCHAR2,
    restab        IN VARCHAR2,
    query_id      IN NUMBER DEFAULT 0,
    glevel        IN VARCHAR2 DEFAULT 'P',
    pov           IN VARCHAR2 DEFAULT NULL,
    numParagraphs IN NUMBER DEFAULT 16,
    maxPercent    IN NUMBER DEFAULT 10,
    num_themes    IN NUMBER DEFAULT 50,
    use_saved_copy IN NUMBER DEFAULT CTX_DOC.SAVE_COPY_FALLBACK);

index_name
Specify the name of the index associated with the text column containing the document identified by `textkey`.

textkey
Specify the unique identifier (usually the primary key) for the document.

The `textkey` parameter can be as follows:

- a single column primary key value

- an encoded specification for a composite (multiple column) primary key. To encode a composite textkey, use the `CTX_DOC.PKENCODE` procedure

- the rowid of the row containing the document

Toggle between primary key and rowid identification using `CTX_DOC.SET_KEY_TYPE`.

restab
Specify that this procedure store the gist and theme summaries to either a table or to an in-memory `CLOB`.

To store results to a table specify the name of an existing table.

**See Also:**

"[Gist Table](oracle-text-result-tables.md)" in [Oracle Text Result Tables](oracle-text-result-tables.md)

To store results in memory, specify the name of the `CLOB` locator. If `restab` is `NULL`, then a temporary `CLOB` is allocated and returned. You must de-allocate the locator after using it.

If `restab` is not `NULL`, then the `CLOB` is truncated before the operation.

query_id
Specify an identifier to use to identify the row(s) inserted into `restab`.

glevel
Specify the type of gist or theme summary to produce. The possible values are:

- P for paragraph

- S for sentence

The default is P.

pov
Specify whether a gist or a single theme summary is generated. The type of gist or theme summary generated (sentence-level or paragraph-level) depends on the value specified for `glevel`.

To generate a gist for the entire document, specify a value of '`GENERIC`' for `pov`. To generate a theme summary for a single theme in a document, specify the theme as the value for `pov`.

When using result table storage, if you do not specify a value for `pov`, then this procedure returns the generic gist plus up to 50 theme summaries for the document.

When using in-memory result storage to a `CLOB`, you must specify a `pov`. However, if you do not specify a `pov`, then this procedure generates only a generic gist for the document.

**Note:**

The `pov` parameter is case sensitive. To return a gist for a document, specify '`GENERIC`' in all uppercase. To return a theme summary, specify the theme exactly as it is generated for the document.

Only the themes generated by THEMES for a document can be used as input for `pov`.

numParagraphs
Specify the maximum number of document paragraphs (or sentences) selected for the document gist or theme summaries. The default is 16.

**Note:**

The `numParagraphs` parameter is used only when this parameter yields a smaller gist or theme summary size than the gist or theme summary size yielded by the `maxPercent` parameter.

This means that the system always returns the smallest size gist or theme summary.

maxPercent
Specify the maximum number of document paragraphs (or sentences) selected for the document gist or theme summaries as a percentage of the total paragraphs (or sentences) in the document. The default is 10.

**Note:**

The `maxPercent` parameter is used only when this parameter yields a smaller gist or theme summary size than the gist or theme summary size yielded by the `numParagraphs` parameter.

This means that the system always returns the smallest size gist or theme summary.

num_themes
Specify the number of theme summaries to produce when you do not specify a value for `pov`. For example, if you specify 10, this procedure returns the top 10 theme summaries. The default is 50.

If you specify 0 or NULL, then this procedure returns all themes in a document. If the document contains more than 50 themes, only the top 50 themes show conceptual hierarchy.

use_saved_copy
Specify whether to refer to the \$D table to fetch the copy of the document, and what action to take when the copy of the document is not available in the \$D table.

You can specify one of the following values for the `use_saved_copy` parameter:

- `CTX_DOC.SAVE_COPY_FALLBACK`: Fetch the copy of the document from the \$D table. If the copy of the document is not present in the \$D table, then fetch the document from the data store.

- `CTX_DOC.SAVE_COPY_ERROR`: Fetch the copy of the document from the \$D table. If the copy of the document is not present in the \$D table, then show an error message. Specify this value when you want to implement a specific fallback logic when the copy of the document is not available in the \$D table.

- `CTX_DOC.SAVE_COPY_IGNORE`: Always fetch the document from the data store.

The default value is `CTX_DOC.SAVE_COPY_FALLBACK`.

#### Examples

In-Memory Gist

The following example generates a non-default size generic gist of at most 10 paragraphs. The result is stored in memory in a `CLOB` locator. The code then de-allocates the returned `CLOB` locator after using it.

    set serveroutput on;
    declare
      gklob clob;
      amt number := 40;
      line varchar2(80);

    begin
     ctx_doc.gist('newsindex','34',gklob, pov => 'GENERIC',numParagraphs => 10);
      -- gklob is NULL when passed-in, so ctx-doc.gist will allocate a temporary
      -- CLOB for us and place the results there.

      dbms_lob.read(gklob, amt, 1, line);
      dbms_output.put_line('FIRST 40 CHARS ARE:'||line);
      -- have to de-allocate the temp lob
      dbms_lob.freetemporary(gklob);
     end;

Result Table Gists

The following example creates a gist table called `CTX_GIST`:

    create table CTX_GIST (query_id  number,
                           pov       varchar2(80),
                           gist      CLOB);

Gists and Theme Summaries

The following example returns a default sized paragraph-level gist for document 34 as well as the top 10 theme summaries in the document:

    begin
     ctx_doc.gist('newsindex','34','CTX_GIST', 1, num_themes=>10);
    end;

The following example generates a non-default size gist of at most 10 paragraphs:

    begin
      ctx_doc.gist('newsindex','34','CTX_GIST',1,pov =>'GENERIC',numParagraphs=>10);
    end;

The following example generates a gist whose number of paragraphs is at most 10 percent of the total paragraphs in document:

    begin
      ctx_doc.gist('newsindex','34','CTX_GIST',1,pov => 'GENERIC',  maxPercent => 10);
    end;

Theme Summary

The following example returns a paragraph-level theme summary for insects for document 34. The default theme summary size is returned.

    begin
       ctx_doc.gist('newsindex','34','CTX_GIST',1, pov => 'insects');
    end;

### 9.4 HIGHLIGHT

Use the `CTX_DOC.HIGHLIGHT` procedure to generate highlight offsets for a document. The offset information is generated for the terms in the document that satisfy the query you specify. These highlighted terms are either the words that satisfy a word query or the themes that satisfy an `ABOUT` query.

You can generate highlight offsets for either plaintext or HTML versions of the document. The table returned by `CTX_DOC.HIGHLIGHT` does not include any graphics found in the original document. Apply the offset information to the same documents filtered with CTX_DOC.FILTER .

You usually call this procedure after a query, from which you identify the document to be processed. You can store the highlight offsets to either an in-memory PL/SQL table or a result table.

Note that for queries that have predicates used mainly for filtering documents at query time, the predicates are ignored during highlighting. This applies to `SNIPPET`, `MARKUP` and `HIGHLIGHT` procedures. The following predicates are treated as filter predicates for this purpose: `SDATA`, `HASPATH`, and `WITHIN`/`INPATH` searching inside XML attributes.

See CTX_DOC.POLICY_HIGHLIGHT for a version of this procedure that does not require an index.

The performance of the procedures SNIPPET, `HIGHLIGHT`, and MARKUP can be improved by using the forward index feature of Oracle Text.

**See Also:**

[Oracle Text Application Developer's Guide](../ccapp/indexing-with-oracle-text.md) for more information about forward index

#### Syntax 1: In-Memory Result Storage

    exec CTX_DOC.HIGHLIGHT(
            index_name  IN VARCHAR2,
            textkey     IN VARCHAR2,
            text_query  IN VARCHAR2,
            restab      IN OUT NOCOPY HIGHLIGHT_TAB,
            plaintext   IN BOOLEAN  DEFAULT FALSE,
            use_saved_copy IN NUMBER DEFAULT CTX_DOC.SAVE_COPY_FALLBACK);

    exec CTX_DOC.HIGHLIGHT_CLOB_QUERY(
            index_name  IN VARCHAR2,
            textkey     IN VARCHAR2,
            text_query  IN CLOB,
            restab      IN OUT NOCOPY HIGHLIGHT_TAB,
            plaintext   IN BOOLEAN DEFAULT FALSE,
            use_saved_copy IN NUMBER DEFAULT CTX_DOC.SAVE_COPY_FALLBACK);

#### Syntax 2: Result Table Storage

    exec CTX_DOC.HIGHLIGHT(
              index_name  IN VARCHAR2,
              textkey     IN VARCHAR2,
              text_query  IN VARCHAR2,
              restab      IN VARCHAR2,
              query_id    IN NUMBER   DEFAULT 0,
              plaintext   IN BOOLEAN  DEFAULT FALSE,
              use_saved_copy IN NUMBER DEFAULT CTX_DOC.SAVE_COPY_FALLBACK);

    exec CTX_DOC.HIGHLIGHT_CLOB_QUERY(
              index_name  IN VARCHAR2,
              textkey     IN VARCHAR2,
              text_query  IN CLOB,
              restab      IN VARCHAR2,
              query_id    IN NUMBER DEFAULT 0,
              plaintext   IN BOOLEAN DEFAULT FALSE,
              use_saved_copy IN NUMBER DEFAULT CTX_DOC.SAVE_COPY_FALLBACK);

index_name
Specify the name of the index associated with the text column containing the document identified by `textkey`.

textkey
Specify the unique identifier (usually the primary key) for the document.

The `textkey` parameter can be as follows:

- a single column primary key value

- encoded specification for a composite (multiple column) primary key. Use the CTX_DOC.PKENCODE procedure.

- the rowid of the row containing the document

Toggle between primary key and rowid identification using CTX_DOC.SET_KEY_TYPE.

text_query
Specify the original query expression used to retrieve the document. If NULL, no highlights are generated.

If `text_query` includes wildcards, stemming, fuzzy matching which result in stopwords being returned, `HIGHLIGHT` does not highlight the stopwords.

If `text_query` contains the threshold operator, the operator is ignored. The `HIGHLIGHT` procedure always returns highlight information for the entire result set.

restab
You can specify that this procedure store highlight offsets to either a table or to an in-memory PL/SQL table.

To store results to a table specify the name of the table. The table must exist before you call this procedure.

**See Also:**

"[Highlight Table](oracle-text-result-tables.md)" in [Oracle Text Result Tables](oracle-text-result-tables.md) for more information about the structure of the highlight result table.

To store results to an in-memory table, specify the name of the in-memory table of type `CTX_DOC.HIGHLIGHT_TAB`. The `HIGHLIGHT_TAB` datatype is defined as follows:

    type highlight_rec is record (
      offset number,
      length number
    );
    type highlight_tab is table of highlight_rec index by binary_integer;

`CTX_DOC.HIGHLIGHT` clears `HIGHLIGHT_TAB` before the operation.

query_id
Specify the identifier used to identify the row inserted into `restab`. When `query_id` is not specified or set to `NULL`, it defaults to 0. You must manually truncate the table specified in `restab`.

plaintext
Specify `TRUE` to generate a plaintext offsets of the document. Specify `FALSE` to generate HTML offsets of the document if you are using the `AUTO_FILTER` filter or indexing HTML documents.

use_saved_copy
Specify whether to refer to the \$D table to fetch the copy of the document, and what action to take when the copy of the document is not available in the \$D table. The default value is `CTX_DOC.SAVE_COPY_FALLBACK`.

You can specify one of the following values for the `use_saved_copy` parameter:

- `CTX_DOC.SAVE_COPY_FALLBACK`: Fetch the copy of the document from the \$D table. If the copy of the document is not present in the \$D table, then fetch the document from the data store.

- `CTX_DOC.SAVE_COPY_ERROR`: Fetch the copy of the document from the \$D table. If the copy of the document is not present in the \$D table, then show an error message. Specify this value when you want to implement a specific fallback logic when the copy of the document is not available in the \$D table.

- `CTX_DOC.SAVE_COPY_IGNORE`: Always fetch the document from the data store.

#### Examples

Create Highlight Table

Create the highlight table to store the highlight offset information:

    create table hightab(query_id number,
                         offset number,
                         length number);

Word Highlighting in the Presence of Filters

When performing highlight on queries such as the following, only the keyword ("dog" in these examples) will be highlighted. The filtering predicates after the `AND` operator will be ignored.

    begin
    ctx_doc.highlight('newsindex', '20', 'dog AND cat WITHIN titlesection@name', 'hightab', 0, FALSE);
    end;
    begin
    ctx_doc.highlight('newsindex', '20', 'dog AND SDATA(price > 100)', 'hightab', 0, FALSE);
    end;

Word Highlight Offsets

To obtain HTML highlight offset information for document 20 for the word dog:

    begin
    ctx_doc.highlight('newsindex', '20', 'dog', 'hightab', 0, FALSE);
    end;

    begin
    ctx_doc.highlight('newsindex', '20', 'dog AND cat WITHIN titlesection', 'hightab', 0, FALSE);
    end;

Theme Highlight Offsets

Assuming the index newsindex has a theme component, obtain HTML highlight offset information for the theme query of politics by issuing the following query:

    begin
    ctx_doc.highlight('newsindex', '20', 'about(politics)', 'hightab', 0, FALSE);
    end;

The output for this statement are the offsets to highlighted words and phrases that represent the theme of politics in the document.

#### Restrictions

`CTX_DOC.HIGHLIGHT` does not support the use of query templates or highlighting XML attribute values.

#### Related Topics

"POLICY_HIGHLIGHT"

"MARKUP "

"SNIPPET"

### 9.5 IFILTER

Use this procedure to filter binary data to text.

This procedure takes binary data (`BLOB IN`), filters the data with the `AUTO_FILTER` filter, and writes the text version to a `CLOB`. (Any graphics in the original document are ignored.) `CTX_DOC.IFILTER` employs the safe callout, and it does not require an index, as `CTX_DOC.FILTER` does.

**Note:**

This procedure will not be supported in future releases. Applications should use CTX_DOC.POLICY_FILTER instead.

#### Requirements

Because `CTX_DOC.IFILTER` employs the safe callout mechanism, the SQL\*Net listener must be running and configured for `extproc` agent startup.

#### Syntax

    CTX_DOC.IFILTER(data IN BLOB, text IN OUT NOCOPY CLOB);

data
Specify the binary data to be filtered.

text
Specify the destination `CLOB`. The filtered data is placed in here. This parameter must be a valid `CLOB` locator that is writable. Passing `NULL` or a non-writable `CLOB` will result in an error. Filtered text will be appended to the end of existing content, if any.

#### Example

The document text used in a `MATCHES` query can be `VARCHAR2` or `CLOB`. It does not accept `BLOB` input, so you cannot match filtered documents directly. Instead, you must filter the binary content to `CLOB` using the `AUTO_FILTER` filter. Assuming the document data is in bind variable `:doc_blob`:

      declare
        doc_text clob;
      begin
        -- create a temporary CLOB to hold the document text
        dbms_lob.createtemporary(doc_text, TRUE, DBMS_LOB.SESSION);

        -- call ctx_doc.ifilter to filter the BLOB to CLOB data
        ctx_doc.ifilter(:doc_blob, doc_text);

        -- now do the matches query using the CLOB version
        for c1 in (select * from queries where matches(query_string, doc_text)>0)
        loop
          -- do what you need to do here
        end loop;

        dbms_lob.freetemporary(doc_text);
      end;

### 9.6 MARKUP

The `CTX_DOC.MARKUP` procedure takes a query specification and a document textkey and returns a version of the document in which the query terms are marked up. These marked-up terms are either the words that satisfy a word query or the themes that satisfy an `ABOUT` query.

You can set the marked-up output to be either plaintext or HTML. The marked-up document returned by `CTX_DOC.MARKUP` does not include any graphics found in the original document.

You can use one of the predefined tag sets for marking highlighted terms, including a tag sequence that enables HTML navigation.

You usually call `CTX_DOC.MARKUP` after a query, from which you identify the document to be processed.

You can store the marked-up document either in memory or in a result table.

Note that for queries that have predicates used mainly for filtering documents at query time, the predicates are ignored during `MARKUP`. The following predicates are treated as filter predicates for this purpose: `SDATA`, `HASPATH`, and `WITHIN`/`INPATH` searching inside XML attributes.

See CTX_DOC.POLICY_MARKUP for a version of this procedure that does not require an index.

The performance of the procedures SNIPPET, HIGHLIGHT, and `MARKUP` can be improved by using the forward index feature of Oracle Text.

**See Also:**

[Oracle Text Application Developer's Guide](../ccapp/indexing-with-oracle-text.md) for more information about forward index

**Note:**

Oracle Text does not guarantee well-formed output from `CTX.DOC.MARKUP`, especially for terms that are already marked up with HTML or XML. In particular, unexpected nesting of markup tags may occasionally result.

#### Syntax 1: In-Memory Result Storage

    exec CTX_DOC.MARKUP(

    index_name     IN VARCHAR2,
    textkey        IN VARCHAR2,
    text_query     IN VARCHAR2,
    restab         IN OUT NOCOPY CLOB,
    plaintext      IN BOOLEAN   DEFAULT FALSE,
    tagset         IN VARCHAR2  DEFAULT 'TEXT_DEFAULT',
    starttag       IN VARCHAR2  DEFAULT NULL,
    endtag         IN VARCHAR2  DEFAULT NULL,
    prevtag        IN VARCHAR2  DEFAULT NULL,
    nexttag        IN VARCHAR2  DEFAULT NULL,
    use_saved_copy IN NUMBER DEFAULT CTX_DOC.SAVE_COPY_FALLBACK);

    exec CTX_DOC.MARKUP_CLOB_QUERY(
    index_name     IN VARCHAR2,
    textkey        IN VARCHAR2,
    text_query     IN CLOB,
    restab         IN OUT NOCOPY CLOB,
    plaintext      IN BOOLEAN DEFAULT FALSE,
    tagset         IN VARCHAR2 DEFAULT 'TEXT_DEFAULT',
    starttag       IN VARCHAR2 DEFAULT NULL,
    endtag         IN VARCHAR2 DEFAULT NULL,
    prevtag        IN VARCHAR2 DEFAULT NULL,
    nexttag        IN VARCHAR2 DEFAULT NULL,
    use_saved_copy IN NUMBER DEFAULT CTX_DOC.SAVE_COPY_FALLBACK);

#### Syntax 2: Result Table Storage

    exec CTX_DOC.MARKUP(

    index_name     IN VARCHAR2,
    textkey        IN VARCHAR2,
    text_query     IN VARCHAR2,
    restab         IN VARCHAR2,
    query_id       IN NUMBER    DEFAULT 0,
    plaintext      IN BOOLEAN   DEFAULT FALSE,
    tagset         IN VARCHAR2  DEFAULT 'TEXT_DEFAULT',
    starttag       IN VARCHAR2  DEFAULT NULL,
    endtag         IN VARCHAR2  DEFAULT NULL,
    prevtag        IN VARCHAR2  DEFAULT NULL,
    nexttag        IN VARCHAR2  DEFAULT NULL,
    use_saved_copy IN NUMBER DEFAULT CTX_DOC.SAVE_COPY_FALLBACK);

    exec CTX_DOC.MARKUP_CLOB_QUERY(
    index_name     IN VARCHAR2,
    textkey        IN CLOB,
    text_query     IN VARCHAR2,
    restab         IN VARCHAR2,
    query_id       IN NUMBER DEFAULT 0,
    plaintext      IN BOOLEAN DEFAULT FALSE,
    tagset         IN VARCHAR2 DEFAULT 'TEXT_DEFAULT',
    starttag       IN VARCHAR2 DEFAULT NULL,
    endtag         IN VARCHAR2 DEFAULT NULL,
    prevtag        IN VARCHAR2 DEFAULT NULL,
    nexttag        IN VARCHAR2 DEFAULT NULL,
    use_saved_copy IN NUMBER DEFAULT CTX_DOC.SAVE_COPY_FALLBACK);

index_name
Specify the name of the index associated with the text column containing the document identified by `textkey`.

textkey
Specify the unique identifier (usually the primary key) for the document.

The `textkey` parameter can be as follows:

- A single column primary key value

- Encoded specification for a composite (multiple column) primary key. Use the CTX_DOC.PKENCODE procedure.

- The rowid of the row containing the document

Toggle between primary key and rowid identification using CTX_DOC.SET_KEY_TYPE.

text_query
Specify the original query expression used to retrieve the document.

If `text_query` includes wildcards, stemming, fuzzy matching which result in stopwords being returned, `MARKUP` does not highlight the stopwords.

If `text_query` contains the threshold operator, the operator is ignored. The `MARKUP` procedure always returns highlight information for the entire result set.

restab
You can specify that this procedure store the marked-up text to either a table or to an in-memory `CLOB`.

To store results to a table specify the name of the table. The result table must exist before you call this procedure.

**See Also:**

For more information about the structure of the markup result table, see "[Markup Table](oracle-text-result-tables.md)" in [Oracle Text Result Tables](oracle-text-result-tables.md).

To store results in memory, specify the name of the CLOB locator. If `restab` is `NULL`, a temporary CLOB is allocated and returned. You must de-allocate the locator after using it.

If `restab` is not `NULL`, the CLOB is truncated before the operation.

query_id
Specify the identifier used to identify the row inserted into `restab`.

When `query_id` is not specified or set to `NULL`, it defaults to 0. You must manually truncate the table specified in `restab`.

plaintext
Specify `TRUE` to generate plaintext marked-up document. Specify `FALSE` to generate a marked-up HTML version of document if you are using the `AUTO_FILTER` filter or indexing HTML documents.

tagset
Specify one of the following predefined tag sets. The second and third columns show how the different tags are defined for each `tagset`:

| Tagset          | Tag      | Tag Value                       |
|:----------------|:---------|:--------------------------------|
| `TEXT_DEFAULT`  | starttag | `<<<`                           |
| `TEXT_DEFAULT`  | endtag   | `>>>`                           |
| `HTML_DEFAULT`  | starttag | `<B>`                           |
| `HTML_DEFAULT`  | endtag   | `</B>`                          |
| `HTML_NAVIGATE` | starttag | `<A NAME=ctx%CURNUM><B>`        |
| `HTML_NAVIGATE` | endtag   | `</B></A>`                      |
| `HTML_NAVIGATE` | prevtag  | `<A HREF=#ctx%PREVNUM>&lt;</A>` |
| `HTML_NAVIGATE` | nexttag  | `<A HREF=#ctx%NEXTNUM>&gt;</A>` |

starttag
Specify the character(s) inserted by `MARKUP` to indicate the start of a highlighted term.

The sequence of `starttag, endtag, prevtag` and `nexttag` with respect to the highlighted word is as follows:

    ... prevtag starttag word endtag nexttag...

endtag
Specify the character(s) inserted by `MARKUP` to indicate the end of a highlighted term.

prevtag
Specify the markup sequence that defines the tag that navigates the user to the previous highlight.

In the markup sequences `prevtag` and `nexttag`, you can specify the following offset variables which are set dynamically:

| Offset Variable | Value                      |
|:----------------|:---------------------------|
| `%CURNUM`       | the current offset number  |
| `%PREVNUM`      | the previous offset number |
| `%NEXTNUM`      | the next offset number     |

See the description of the `HTML_NAVIGATE `""tagset"" for an example.

nexttag
Specify the markup sequence that defines the tag that navigates the user to the next highlight tag.

Within the markup sequence, you can use the same offset variables you use for `prevtag`. See the explanation for ""prevtag"" and the `HTML_NAVIGATE` ""tagset"" for an example.

use_saved_copy
Specify whether to refer to the \$D table to fetch the copy of the document, and what action to take when the copy of the document is not available in the \$D table.

You can specify one of the following values for the `use_saved_copy` parameter:

- `CTX_DOC.SAVE_COPY_FALLBACK`: Fetch the copy of the document from the \$D table. If the copy of the document is not present in the \$D table, then fetch the document from the data store.

- `CTX_DOC.SAVE_COPY_ERROR`: Fetch the copy of the document from the \$D table. If the copy of the document is not present in the \$D table, then show an error message. Specify this value when you want to implement a specific fallback logic when the copy of the document is not available in the \$D table.

- `CTX_DOC.SAVE_COPY_IGNORE`: Always fetch the document from the data store.

The default value is `CTX_DOC.SAVE_COPY_FALLBACK`.

#### Examples

In-Memory Markup

The following code takes document (the dog chases the cat), performs the assigned markup on it, and stores the result in memory.

    set serveroutput on

    drop table mark_tab;
    create table mark_tab (id number primary key, text varchar2(80) );
    insert into mark_tab values ('1', 'The dog chases the cat.');

    create index mark_tab_idx on mark_tab(text)
            indextype is ctxsys.context parameters
            ('filter ctxsys.null_filter');

    declare
    mklob clob;
    amt number := 40;
    line varchar2(80);

    begin
     ctx_doc.markup('mark_tab_idx','1','dog AND cat', mklob);
     -- mklob is NULL when passed-in, so ctx_doc.markup will
     -- allocate a temporary CLOB for us and place the results there.
     dbms_lob.read(mklob, amt, 1, line);
     dbms_output.put_line('FIRST 40 CHARS ARE:'||line);
     -- have to de-allocate the temp lob
     dbms_lob.freetemporary(mklob);
     end;
    /

The output from this example shows what the marked-up document looks like:

    FIRST 40 CHARS ARE:  The <<<dog>>> chases the <<<cat>>>.

Markup Table

Create the highlight markup table to store the marked-up document as follows:

    create table markuptab (query_id  number,
                            document  clob);

Word Highlighting in HTML

You can also store your `MARKUP` results in a table. To create HTML highlight markup for the words dog or cat for document 23, enter the following examples:

    begin
      ctx_doc.markup(index_name => 'my_index',
                          textkey => '23',
                          text_query => 'dog|cat',
                          restab => 'markuptab',
                          query_id => '1',
                          tagset => 'HTML_DEFAULT');
    end;

    begin
      ctx_doc.markup(index_name => 'my_index',
                          textkey => '23',
                          text_query => 'dog AND cat WITHIN titlesection@name',
                          restab => 'markuptab',
                          query_id => '1',
                          tagset => 'HTML_DEFAULT');
    end;

Word Highlighting in the Presence of Filters

When performing markup on queries such as the following, only the keyword ("dog" in these examples) will be marked up. The filtering predicates after the `AND` operator will be ignored.

    begin
      ctx_doc.markup(index_name => 'my_index',
                          textkey => '23',
                          text_query => 'dog AND cat WITHIN titlesection@name',
                          restab => 'markuptab',
                          query_id => '1',
                          tagset => 'HTML_DEFAULT');
    end;

    begin
      ctx_doc.markup(index_name => 'my_index',
                          textkey => '23',
                          text_query => 'dog AND SDATA(price > 100)',
                          restab => 'markuptab',
                          query_id => '1',
                          tagset => 'HTML_DEFAULT');
    end;

Theme Highlighting in HTML

To create HTML highlight markup for the theme of politics for document 23, enter the following statement:

    begin
      ctx_doc.markup(index_name => 'my_index',
                          textkey => '23',
                          text_query => 'about(politics)',
                          restab => 'markuptab',
                          query_id => '1',
                          tagset => 'HTML_DEFAULT');
    end;

#### Restrictions

`CTX_DOC.MARKUP` does not support the use of query templates.

#### Related Topics

"POLICY_MARKUP"

"SNIPPET"

### 9.7 PKENCODE

The `CTX_DOC.PKENCODE` function converts a composite textkey list into a single string and returns the string.

The string created by `PKENCODE` can be used as the primary key parameter `textkey`in other `CTX_DOC` procedures, such as CTX_DOC.THEMES and CTX_DOC.GIST.

#### Syntax

    CTX_DOC.PKENCODE(
             pk1    IN VARCHAR2,
             pk2    IN VARCHAR2 DEFAULT NULL,
             pk4    IN VARCHAR2 DEFAULT NULL,
             pk5    IN VARCHAR2 DEFAULT NULL,
             pk6    IN VARCHAR2 DEFAULT NULL,
             pk7    IN VARCHAR2 DEFAULT NULL,
             pk8    IN VARCHAR2 DEFAULT NULL,
             pk9    IN VARCHAR2 DEFAULT NULL,
             pk10   IN VARCHAR2 DEFAULT NULL,
             pk11   IN VARCHAR2 DEFAULT NULL,
             pk12   IN VARCHAR2 DEFAULT NULL,
             pk13   IN VARCHAR2 DEFAULT NULL,
             pk14   IN VARCHAR2 DEFAULT NULL,
             pk15   IN VARCHAR2 DEFAULT NULL,
             pk16   IN VARCHAR2 DEFAULT NULL)
    RETURN VARCHAR2;

pk1-pk16
Each PK argument specifies a column element in the composite textkey list. You can encode at most 16 column elements.

#### Returns

String that represents the encoded value of the composite textkey.

#### Example

    begin
    ctx_doc.gist('newsindex',CTX_DOC.PKENCODE('smith', 14), 'CTX_GIST');
    end;

In this example, smith and 14 constitute the composite textkey value for the document.

### 9.8 POLICY_FILTER

Generates a plain text or an HTML version of a document. With this procedure, no `CONTEXT` index is required.

This procedure uses a trusted callout.

#### Syntax

    ctx_doc.policy_filter(policy_name    in  VARCHAR2,
                          document       in [VARCHAR2|CLOB|BLOB|BFILE],
                          restab         in out nocopy CLOB,
                          plaintext      in BOOLEAN default FALSE,
                          language       in VARCHAR2 default NULL,
                          format         in VARCHAR2 default NULL,
                          charset        in VARCHAR2 default NULL);

policy_name
Specify the policy name created with CTX_DDL.[CREATE_POLICY](CTX_DDL-package.md).

document
Specify the document to filter.

restab
Specify the name of the `CLOB` locator.

plaintext
Specify `TRUE` to generate a plaintext version of the document. Specify `FALSE` to generate an HTML version of the document if you are using the `AUTO_FILTER` filter or indexing HTML documents.

language
Specify the language of the document. Use an Oracle Text supported language value as you would in the language column of the base table. See [BASIC_LEXER](oracle-text-indexing-elements.md) in [Oracle Text Indexing Elements](oracle-text-indexing-elements.md).

format
Specify the format of the document. Use an Oracle Text supported format value, either TEXT, BINARY or IGNORE as you would specify in the format column of the base table. For more information, see the format column description in [CREATE INDEX](oracle-text-SQL-statements-and-operators.md) in [Oracle Text SQL Statements and Operators](oracle-text-SQL-statements-and-operators.md) .

charset
Specify the character set of the document. Use an Oracle Text supported value as you would specify in the charset column of the base table. See "[Filter Types](oracle-text-indexing-elements.md)".

### 9.9 POLICY_GIST

Generates a gist or theme summary for document. You can generate paragraph-level or sentence-level gists or theme summaries. With this procedure, no `CONTEXT` index is required.

#### Syntax

    ctx_doc.policy_gist(policy_name      in VARCHAR2,
                        document         in [VARCHAR2|CLOB|BLOB|BFILE],
                        restab           in out nocopy CLOB,
                        glevel           in VARCHAR2 default 'P',
                        pov              in VARCHAR2 default 'GENERIC',
                        numParagraphs    in NUMBER default NULL,
                        maxPercent       in NUMBER default NULL,
                        num_themes       in NUMBER default 50
                        language         in VARCHAR2 default NULL,
                        format           in VARCHAR2 default NULL,
                        charset          in VARCHAR2 default NULL
    );

policy_name
Specify the policy name created with CTX_DDL.[CREATE_POLICY](CTX_DDL-package.md).

document
Specify the document for which to generate the Gist or theme summary.

restab
Specify the name of the `CLOB` locator.

glevel
Specify the type of gist or theme summary to produce. The possible values are:

- P for paragraph

- S for sentence

The default is P.

pov
Specify whether a gist or a single theme summary is generated. The type of gist or theme summary generated (sentence-level or paragraph-level) depends on the value specified for `glevel`.

To generate a gist for the entire document, specify a value of '`GENERIC`' for `pov`. To generate a theme summary for a single theme in a document, specify the theme as the value for `pov`.

When using result table storage and you do not specify a value for `pov`, this procedure returns the generic gist plus up to 50 theme summaries for the document.

**Note:**

The `pov` parameter is case sensitive. To return a gist for a document, specify '`GENERIC`' in all uppercase. To return a theme summary, specify the theme exactly as it is generated for the document.

Only the themes generated by THEMES for a document can be used as input for `pov`.

numParagraphs
Specify the maximum number of document paragraphs (or sentences) selected for the document gist or theme summaries. The default is 16.

**Note:**

The `numParagraphs` parameter is used only when this parameter yields a smaller gist or theme summary size than the gist or theme summary size yielded by the `maxPercent` parameter.

This means that the system always returns the smallest size gist or theme summary.

maxPercent
Specify the maximum number of document paragraphs (or sentences) selected for the document gist or theme summaries as a percentage of the total paragraphs (or sentences) in the document. The default is 10.

**Note:**

The `maxPercent` parameter is used only when this parameter yields a smaller gist or theme summary size than the gist or theme summary size yielded by the `numParagraphs` parameter.

This means that the system always returns the smallest size gist or theme summary.

num_themes
Specify the number of theme summaries to produce when you do not specify a value for `pov`. For example, if you specify 10, this procedure returns the top 10 theme summaries. The default is 50.

If you specify 0 or NULL, this procedure returns all themes in a document. If the document contains more than 50 themes, only the top 50 themes show conceptual hierarchy.

language
Specify the language of the document. Use an Oracle Text supported language value as you would in the language column of the base table. See "[MULTI_LEXER](oracle-text-indexing-elements.md)".

format
Specify the format of the document. Use an Oracle Text supported format value, either TEXT, BINARY or IGNORE as you would specify in the format column of the base table. For more information, see the format column description in "[CREATE INDEX](oracle-text-SQL-statements-and-operators.md)".

charset
Specify the character set of the document. Use an Oracle Text supported value as you would specify in the charset column of the base table.

### 9.10 POLICY_HIGHLIGHT

Generates plain text or HTML highlighting offset information for a document. With this procedure, no `CONTEXT` index is required.

The offset information is generated for the terms in the document that satisfy the query you specify. These highlighted terms are either the words that satisfy a word query or the themes that satisfy an `ABOUT` query.

You can generate highlight offsets for either plaintext or HTML versions of the document. You can apply the offset information to the same documents filtered with CTX_DOC.FILTER .

#### Syntax

    exec ctx_doc.policy_highlight(
                             policy_name  in  VARCHAR2,
                             document     in  [VARCHAR2|CLOB|BLOB|BFILE],
                             text_query   in VARCHAR2,
                             restab       in out nocopy highlight_tab,
                             plaintext    in boolean FALSE
                             language     in VARCHAR2 default NULL,
                             format       in VARCHAR2 default NULL,
                             charset      in VARCHAR2 default NULL
    );

    exec ctx_doc.policy_highlight_clob_query(
                             policy_name  in VARCHAR2,
                             document     in [VARCHAR2|CLOB|BLOB|BFILE],
                             text_query   in CLOB,
                             restab       in out nocopy highlight_tab,
                             plaintext    in boolean FALSE
                             language     in VARCHAR2 default NULL,
                             format       in VARCHAR2 default NULL,
                             charset      in VARCHAR2 default NULL
    );

policy_name
Specify the policy name created with CTX_DDL.[CREATE_POLICY](CTX_DDL-package.md).

document
Specify the document to generate highlighting offset information.

text_query
Specify the original query expression used to retrieve the document. If NULL, no highlights are generated.

If `text_query` includes wildcards, stemming, or fuzzy matching which result in stopwords being returned, this procedure does not highlight the stopwords.

If `text_query` contains the threshold operator, the operator is ignored. This procedure always returns highlight information for the entire result set.

restab
Specify the name of the `highlight_tab` PL/SQL index-by-table type.

**See Also:**

"HIGHLIGHT " for more information about the structure of the `highlight_tab` table type

plaintext
Specify `TRUE` to generate a plaintext offsets of the document.

Specify `FALSE` to generate HTML offsets of the document if you are using the `AUTO_FILTER` filter or indexing HTML documents.

language
Specify the language of the document. Use an Oracle Text supported language value as you would in the language column of the base table. See "[MULTI_LEXER](oracle-text-indexing-elements.md)" in [Oracle Text Indexing Elements](oracle-text-indexing-elements.md).

format
Specify the format of the document. Use an Oracle Text supported format value, either TEXT, BINARY or IGNORE as you would specify in the format column of the base table. For more information, see the format column description under "[CREATE INDEX](oracle-text-SQL-statements-and-operators.md)".

charset
Specify the character set of the document. Use an Oracle Text supported value as you would specify in the charset column of the base table.

#### Restrictions

`CTX_DOC.POLICY_HIGHLIGHT` does not support the use of query templates.

### 9.11 POLICY_LANGUAGES

Provides the ability to fetch the language for a section of text.

Returns a table of language descriptors and scores, where the score is the confidence level with which the system can assert that the supplied text is in the specific language.

#### Syntax

    CTX_DOC.POLICY_LANGUAGES (
       policy_name    IN VARCHAR2 | CLOB,
       document       IN VARCHAR2,
       restab         IN OUT NOCOPY CTX_DOC.LANGUAGE_TAB
    );

policy_name
A policy that was previously created using the CTX_DDL.[CREATE_POLICY](CTX_DDL-package.md) method. If the specified policy includes a sectioning preference, the API will honor the sectioning preference. For instance, if HTML sectioning is specified, then HTML tags will be removed before processing the input document.

document
A body of text for which the languages are to be extracted. The text is assumed to be plain text with UTF-8 character encoding.

restab
The result of the language extraction process. The result is a table of records. Each record has two attributes: the language string, and the score for each language string. The score can range from 0 to 100 and represents the confidence with which the system can assert that the supplied text is in the specified language. The resulting languages are returned in sorted order with the language with the most confidence appearing first.

The table layout for `restab` is similar to that for HIGHLIGHT.

**See Also:**

"HIGHLIGHT " for information on `restab` layout

#### Supported Languages for CTX_DOC.POLICY_LANGUAGES and POLICY_STEMS

Language extraction is supported for text in the languages supported by [AUTO_LEXER](oracle-text-indexing-elements.md). The supported languages for CTX_DOC.POLICY_LANGUAGES and CTX_DOC.POLICY_STEMS for this release are:

Arabic

Bokmal

Catalan

Croatian

Czech

Danish

Dutch

English

Finnish

French

German

Greek

Hebrew

Hungarian

Italian

Japanese

Korean

Polish

Nynorsk

Persian

Portuguese

Romanian

Russian

Serbian

Slovak

Slovenian

Simplified Chinese

Spanish

Swedish

Thai

Traditional Chinese

Turkish

#### Related Topics

"POLICY_STEMS"

"[AUTO_LEXER](oracle-text-indexing-elements.md)"

### 9.12 POLICY_MARKUP

Generates plain text or HTML version of a document with query terms highlighted. With this procedure, no `CONTEXT` index is required.

The `CTX_DOC.POLICY_MARKUP` procedure takes a query specification and a document and returns a version of the document in which the query terms are marked up. These marked-up terms are either the words that satisfy a word query or the themes that satisfy an `ABOUT` query.

You can set the marked-up output to be either plaintext or HTML.

You can use one of the predefined tag sets for marking highlighted terms, including a tag sequence that enables HTML navigation.

#### Syntax

    ctx_doc.policy_markup(policy_name     in VARCHAR2,
                          document        in [VARCHAR2|CLOB|BLOB|BFILE],
                          text_query      in VARCHAR2,
                          restab          in out nocopy CLOB,
                          plaintext       in BOOLEAN default FALSE,
                          tagset          in VARCHAR2 default 'TEXT_DEFAULT',
                          starttag        in VARCHAR2 default NULL,
                          endtag          in VARCHAR2 default NULL,
                          prevtag         in VARCHAR2 default NULL,
                          nexttag         in VARCHAR2 default NULL
                          language        in VARCHAR2 default NULL,
                          format          in VARCHAR2 default NULL,
                          charset         in VARCHAR2 default NULL
    );

    ctx_doc.policy_markup_clob_query(
                          policy_name     in VARCHAR2,
                          document        in [VARCHAR2|CLOB|BLOB|BFILE],
                          text_query      in CLOB,
                          restab          in out nocopy CLOB,
                          plaintext       in BOOLEAN default FALSE,
                          tagset          in VARCHAR2 default 'TEXT_DEFAULT',
                          starttag        in VARCHAR2 default NULL,
                          endtag          in VARCHAR2 default NULL,
                          prevtag         in VARCHAR2 default NULL,
                          nexttag         in VARCHAR2 default NULL
                          language        in VARCHAR2 default NULL,
                          format          in VARCHAR2 default NULL,
                          charset         in VARCHAR2 default NULL
    );

policy_name
Specify the policy name created with CTX_DDL.[CREATE_POLICY](CTX_DDL-package.md).

document
Specify the document to generate highlighting offset information.

text_query
Specify the original query expression used to retrieve the document.

If `text_query` includes a NULL, then this procedure will fail and generate errors.

If `text_query` includes wildcards, stemming, or fuzzy matching which result in stopwords being returned, then this procedure does not highlight the stopwords.

If `text_query` contains the threshold operator, the operator is ignored. This procedure always returns highlight information for the entire result set.

restab
Specify the name of the `CLOB` locator.

plaintext
Specify `TRUE` to generate a plaintext marked-up document. Specify `FALSE` to generate a marked-up HTML version of the document if you are using the `AUTO_FILTER` filter or indexing HTML documents.

tagset
Specify one of the following predefined tag sets. The second and third columns show how the different tags are defined for each tagset:

| Tagset          | Tag      | Tag Value                       |
|:----------------|:---------|:--------------------------------|
| `TEXT_DEFAULT`  | starttag | `<<<`                           |
| `TEXT_DEFAULT`  | endtag   | `>>>`                           |
| `HTML_DEFAULT`  | starttag | `<B>`                           |
| `HTML_DEFAULT`  | endtag   | `</B>`                          |
| `HTML_NAVIGATE` | starttag | `<A NAME=ctx%CURNUM><B>`        |
| `HTML_NAVIGATE` | endtag   | `</B></A>`                      |
| `HTML_NAVIGATE` | prevtag  | `<A HREF=#ctx%PREVNUM>&lt;</A>` |
| `HTML_NAVIGATE` | nexttag  | `<A HREF=#ctx%NEXTNUM>&gt;</A>` |

starttag
Specify the character(s) inserted by `MARKUP` to indicate the start of a highlighted term.

The sequence of `starttag, endtag, prevtag` and `nexttag` with regard to the highlighted word is as follows:

    ... prevtag starttag word endtag nexttag...

endtag
Specify the character(s) inserted by `MARKUP` to indicate the end of a highlighted term.

prevtag
Specify the markup sequence that defines the tag that navigates the user to the previous highlight.

In the markup sequences `prevtag` and `nexttag`, you can specify the following offset variables which are set dynamically:

| Offset Variable | Value                      |
|:----------------|:---------------------------|
| `%CURNUM`       | the current offset number  |
| `%PREVNUM`      | the previous offset number |
| `%NEXTNUM`      | the next offset number     |

See the description of the `HTML_NAVIGATE` tagset for an example ""tagset"".

nexttag
Specify the markup sequence that defines the tag that navigates the user to the next highlight tag.

Within the markup sequence, you can use the same offset variables you use for `prevtag`. See the explanation for `prevtag` and the `HTML_NAVIGATE` ""tagset"" for an example.

language
Specify the language of the document. Use an Oracle Text supported language value as you would in the language column of the base table. See "[MULTI_LEXER](oracle-text-indexing-elements.md)" in [Oracle Text Indexing Elements](oracle-text-indexing-elements.md).

format
Specify the format of the document. Use an Oracle Text supported format value, either TEXT, BINARY or IGNORE as you would specify in the format column of the base table. For more information, see the format column description in "[CREATE INDEX](oracle-text-SQL-statements-and-operators.md)".

charset
Specify the character set of the document. Use an Oracle Text supported value as you would specify in the charset column of the base table. See "[Filter Types](oracle-text-indexing-elements.md)".

#### Restrictions

`CTX_DOC.POLICY_MARKUP` does not support the use of query templates.

### 9.13 POLICY_NOUN_PHRASES

Provides the ability to extract the noun phrases along with part-of-speech information for each word in each noun phrase from a given document.

For example, consider the following sentence:

"The mayor of Chicago is giving a brief press conference."

The noun phrases for this input are "mayor of Chicago" and "brief press conference." The subgroups in the input text are not returned. For instance, in the above example, subgroups such as "mayor,Chicago, brief press, press conference, press, conference" are not returned.

POLICY_NOUN_PHRASES (and POLICY_PART_OF_SPEECH) supports the following languages:

- Dutch

- English

- German

- French

- Italian

- Japanese

- Korean

- Simplified Chinese

- Spanish

- Traditional Chinese

#### Syntax

    ctx_doc.policy_noun_phrases (
       policy_name    in varchar2,
       document       in varchar2 | CLOB,
       restab         in out nocopy noun_phrase_tab,
       language       in varchar2  default NULL,
       format         in varchar2  default NULL,
       charset        in varchar2  default NULL
    );

policy_name
Specify the policy name created with CTX_DDL.[CREATE_POLICY](CTX_DDL-package.md).

document
A body of text for which the languages are to be extracted. The text is assumed to be plain text with UTF-8 character encoding.

restab
Specify the name of the `CLOB` locator.

<!-- -->

language
Specify the language. See the list of supported languages in this section. If this parameter is null, the language will be automatically detected. There is a cost associated with language detection.

format
The format of the input text.

charset
The character set of the input text.

#### Abbreviations for Use with POLICY_NOUN_PHRASES and POLICY_PART_OF_SPEECH

Table 9-1 provides a list of abbreviations to use in queries for `POLICY_NOUN_PHRASES` and `POLICY_PART_OF_SPEECH`. The examples use these abbreviations.

Table 9-1 Part of Speech Abbreviations

| Abbreviation | Part of Speech |
|:-------------|:---------------|
| N            | noun           |
| propN        | nounProper     |
| V            | verb           |
| Adj          | adjective      |
| Adv          | adverb         |
| Prep         | preposition    |
| Part         | particle       |
| Punct        | punct          |
| Pro          | pronoun        |
| Wh           | interrog       |
| Det          | determiner     |
| Conj         | conjunction    |
| Card         | numCardinal    |
| Ord          | numOrdinal     |
| Suf          | suffix         |
| Pre          | prefix         |
| Acr          | nounAcronym    |
| Poss         | poss           |
| Unk          | unknown        |

#### Example for POLICY\_\_NOUN_PHRASES

The example in this section uses the abbreviations shown in Table 9-1.

    set serverout on
    create or replace function toString(b boolean) return varchar2 is
        begin
          if (b) then
            return 'TRUE';
          end if;
          return 'FALSE';
     end;
     /

    declare
     the_nps ctx_doc.noun_phrase_tab;
    begin
      ctx_ddl.create_preference('rvlex', 'AUTO_LEXER');
      ctx_ddl.set_attribute('rvlex','mixed_case','YES');
      ctx_ddl.set_attribute('rvlex','timeout',0);

      ctx_ddl.create_policy(policy_name => 'rv_policy_21',lexer => 'rvlex');

     ctx_doc.policy_noun_phrases('rv_policy_21','The mayor of Chicago is giving a
     brief press conference',the_nps);
     dbms_output.put_line(the_nps.count);

     for i in 1..the_nps.count loop
          if (the_nps(i).is_phrase_start) then
            if (i>1) then
              dbms_output.put(']');
              dbms_output.new_line;
            end if;
            dbms_output.put('Phrase{term,POS,is_in_lex,offset,len,is_phrase_
            start}:[');
          else
            dbms_output.put(',');
          end if;
          dbms_output.put('{' || the_nps(i).term || ',' || the_nps(i).pos_tag || ','
          || toString(the_nps(i).is_in_lexicon) || ',' || the_nps(i).offset
          || ',' || the_nps(i).length || ',' || toString(the_nps(i).is_phrase_start)
          || '}');
          end loop;
          dbms_output.put(']');
          dbms_output.new_line;
    end;
    /

Output for this example:

    Phrase{term,POS,is_in_lex,offset,len,is_phrase_start}:
    [{The,Det,TRUE,1,3,TRUE},{mayor,N,TRUE,5,5,FALSE},
    {of,Prep,TRUE,11,2,FALSE},{Chicago,propN,TRUE,14,7,FALSE}

    Phrase{term,POS,is_in_lex,offset,len,is_phrase_start}:
    [{a,Det,TRUE,32,1,TRUE},{brief,N,TRUE,34,5,FALSE},
    {press,N,TRUE,40,5,FALSE},{conference,N,TRUE,46,10,FALSE}]

#### Related Topics

"POLICY_PART_OF_SPEECH"

### 9.14 POLICY_PART_OF_SPEECH

Extracts part of speech information for each word in a body of text.

POLICY_NOUN_PHRASES has the list of supported languages.

#### Syntax

    ctx_doc.policy_part_of_speech (
       policy_name       in varchar2,
       document          in varchar2 | CLOB,
       restab            in out nocopy noun_phrase_tab,
       language          in varchar2  default NULL,
       format            in varchar2  default NULL,
       charset           in varchar2  default NULL
       disambiguate_tags in boolean default TRUE
    );

policy_name
Specify the policy name created with CTX_DDL.[CREATE_POLICY](CTX_DDL-package.md). If the specified policy includes a sectioning preference, the API will honor the sectioning preference. For instance, if HTML sectioning is specified, HTML tags will be removed before processing the input document.

document
A body of text for which the languages are to be extracted. The text is assumed to be plain text with UTF-8 character encoding.

restab
Specify the name of the `CLOB` locator. The query returns a table with the result of the noun phrase extraction. For each word, the following attributes are also returned:

- `pos_tags`: the part of speech tags for this word. There can be multiple part of speech tags with the most likely tag listed first.

- `offset`: offset of the word in the input string

- `length`: length of the word in the input string.

- `is_in_lexicon`: Indicates whether the word is in the lexicon.

<!-- -->

language
Specify the language. See the list of supported languages in this section. If this parameter is null, the language will be automatically detected. There is a cost associated with language detection.

format
The format of the input text.

charset
The character set of the input text.

#### Example for POLICY_PART_OF_SPEECH

The example in this section uses the abbreviations shown in Table 9-1.

    set serveroutput on;
    declare
      the_nps ctx_doc.part_of_speech_tab;
    begin
       ctx_doc.policy_part_of_speech(policy_name => 'rv_policy_21',
                                    document => 'The mayor of Chicago is giving
                                                 a brief press conference',
                                     restab => the_nps,
                                     disambiguate_tags => false,
                                     language => 'english');
     for i in 1..the_nps.count loop
      dbms_output.put('word:' || the_nps(i).word || ',pos:[');
      for j in 1..the_nps(i).pos_tags.count loop
        dbms_output.put(the_nps(i).pos_tags(j) || ',');
      end loop;
      dbms_output.put_line(']');
     end loop;
    end;
    /

Output for this example:

    word:The,pos:[Det,]
    word:mayor,pos:[N,]
    word:of,pos:[Prep,]
    word:Chicago,pos:[propN,]
    word:is,pos:[V,]
    word:giving,pos:[N,V,Adj,]
    word:a,pos:[Det,]
    word:brief,pos:[N,V,Adj,]
    word:press,pos:[N,V,]
    word:conference,pos:[N,V,]

#### Related Topics

"POLICY_NOUN_PHRASES"

"[Table 6-1](CTX_ANL-package.md)"

### 9.15 POLICY_SNIPPET

Displays marked-up keywords in context. The returned text contains either the words that satisfy a word query or the themes that satisfy an `ABOUT` query. This version of the CTX_DOC.SNIPPET procedure does not require an index.

#### Syntax

Syntax 1

    exec CTX_DOC.POLICY_SNIPPET(

    policy_name              IN VARCHAR2,
    document                 IN [VARCHAR2|CLOB|BLOB|BFILE],
    text_query               IN VARCHAR2,
    language                 IN VARCHAR2 default NULL,
    format                   IN VARCHAR2 default NULL,
    charset                  IN VARCHAR2 default NULL,
    starttag                 IN VARCHAR2 DEFAULT '<b>',
    endtag                   IN VARCHAR2 DEFAULT '</b>',
    entity_translation       IN BOOLEAN  DEFAULT TRUE,
    separator                IN VARCHAR2 DEFAULT '<b>...</b>'
    radius                     IN INTEGER DEFAULT 25,
    max_length               IN INTEGER DEFAULT 250
    )
    return varchar2;

Syntax 2

    exec CTX_DOC.POLICY_SNIPPET_CLOB_QUERY(
    policy_name              IN VARCHAR2,
    document                 IN [VARCHAR2|CLOB|BLOB|BFILE],
    text_query               IN CLOB,
    language                 IN VARCHAR2 default NULL,
    format                   IN VARCHAR2 default NULL,
    charset                  IN VARCHAR2 default NULL,
    starttag                 IN VARCHAR2 DEFAULT '<b>',
    endtag                   IN VARCHAR2 DEFAULT '</b>',
    entity_translation       IN BOOLEAN DEFAULT TRUE,
    separator                IN VARCHAR2 DEFAULT '<b>...</b>'
    radius                     IN INTEGER DEFAULT 25,
    max_length               IN INTEGER DEFAULT 250
    )
    return varchar2;

policy_name
Specify the name of a policy created with CTX_DDL.[CREATE_POLICY](CTX_DDL-package.md).

document
Specify the document in which to search for keywords.

<!-- -->

text_query
Specify the original query expression used to retrieve the document. If NULL, no highlights are generated.

If `text_query` includes wildcards, stemming, fuzzy matching which result in stopwords being returned, `POLICY_SNIPPET` does not highlight the stopwords.

If `text_query` contains the threshold operator, the operator is ignored.

language
Specify the language of the document. Use an Oracle Text supported language value as you would in the language column of the base table. See [MULTI_LEXER](oracle-text-indexing-elements.md) in [Oracle Text Indexing Elements](oracle-text-indexing-elements.md).

format
Specify the format of the document. Use an Oracle Text supported format value, either TEXT, BINARY or IGNORE as you would specify in the format column of the base table. For more information, see the format column description in "[CREATE INDEX](oracle-text-SQL-statements-and-operators.md)".

charset
Specify the character set of the document. Use an Oracle Text supported value as you would specify in the charset column of the base table. See "[Filter Types](oracle-text-indexing-elements.md)".

starttag
Specify the start tag for marking up the query keywords. Default is '\<b\>'.

endtag
Specify the end tag for marking up the query keywords. Default is '\</b\>'.

entity_translation
Specify if you want HTML entities to be translated. The default is TRUE, which means the special entities (\<, \>, and &) are translated into their alternate forms ('&lt;', '&gt;', and '&amp;') when output by the procedure. However, special characters in the markup tags generated by `CTX_DOC.POLICY_SNIPPET` will not be translated.

separator
Specify the string separating different returned fragments. Default is '\<b\>...\</b\>'.

radius
Specify the number of characters to be shown on either side of the hit query in a segment. The character count before the hit query begins on the first character of the first hit query displayed in a segment. Accordingly, the character count after the hit query begins on the last character of the last hit query displayed on a specific segment. Two segments are merged into one if their radii overlap. The displayed number of characters on each side may be modified by +/-10 chars to best match the beginning or ending of a sentence or word.

Special attention is required for the value `0`. When specified, the radius is set to automatic and varies between sentences. A best guess of the results is displayed, which attempts to match a full sentence. Note that the length of the radius on each side of the hit query will most likely significantly differ.

The default value is 25.

max_length
Specify the maximum length of the snippet output in characters. This value is currently upper-bounded by the current return type of CTX_DOC.SNIPPET and CTX_DOC.POLICY_SNIPPET (VARCHAR2). Should the output be longer than the return type VARCHAR2, the result will be truncated.

The default value for max_length is 250.

**Note:**

If you set `max_length` value to a very low value, no snippet may be generated. For example, if `max_length` is set to `0` or if `max_length` is lower than the length of query tokens themselves, no snippet may be generated at all.

#### Limitations

`CTX_DOC.POLICY_SNIPPET` does not support the use of query templates.

`CTX_DOC.POLICY_SNIPPET` displays marked-up keywords in context when used with `NULL_SECTION_GROUP`. However, there are limitations when using this procedure with XML documents. When used with `XML_SECTION_GROUP` or `AUTO_SECTION_GROUP`, the XML structure is ignored and user-specified tags are stripped out, which results in parts of surrounding text to be included in the returned snippet.

#### Related Topics

"SNIPPET"

"MARKUP "

### 9.16 POLICY_STEMS

Extracts stems for each word in a body of text. This procedure is for use with [AUTO_LEXER](oracle-text-indexing-elements.md). This procedure can only use the languages supported by AUTO_LEXER, which are listed under "POLICY_LANGUAGES".

#### Syntax

    exec CTX_DOC.POLICY_STEMS (
       policy_name   in varchar2,
       document      in varchar2 | CLOB,
       restab        in out nocopy ctx_doc.stem_group_tab,
       language      in varchar2  default NULL,
       format        in varchar2  default NULL,
       charset       in varchar2  default NULL
    );

policy_name
A policy that was previously created using the CTX_DDL.[CREATE_POLICY](CTX_DDL-package.md) method. If the specified policy includes a `HTML_SECTION_GROUP` sectioning preference, the API will honor the sectioning preference. For instance, if HTML sectioning is specified, HTML tags will be removed before processing the input document.

Note that the policy must use AUTO_LEXER only.

document
A body of text for which the languages are to be extracted. The text is assumed to be plain text with UTF-8 character encoding.

restab
The result of the stem extraction process. The returned values in the PL/SQL table will have one cell for each word in the input string document. Each word can be a multi-word as determined by the lexer. For each word, all the stems (including all alternate stems) are returned. For each stem, the offset and the length (in the input string) of the word for which this is a stem is returned. Additionally, for each stem, a Boolean value is returned that indicates if the stem was found in the lexicon.

`stem_group_tab` is a table of `stem_group_records`.

language
The language of the input text. The language string can be one of the values specified in the previous section on language extraction. If this parameter is null, the language will be automatically detected. There is a cost associated with language detection. So, if the language is known, it is best to supply the language value. See "POLICY_LANGUAGES" for the list of languages.

format
The format of the input text.

charset
The character set of the input text.

#### Restrictions and Notes

The stem extraction process supports certain nonstandard word forms—e.g. capitalization errors—as well as standard forms, and thus can be used to process informal or imperfect text (such as email, online documents, or queries). It also handles some variations in the text including case variation, hyphenation and unaccented characters among others.

The stem extraction process does not break compound words, but instead separates compound words with a \# character. Such compound words are common in German. For instance, the German compound word Bildungsroman (from Bildung "education" and Roman "novel") yields a single stem Bildungs#roman instead of two stems Bildungs and roman.

#### Related Topics

"POLICY_LANGUAGES"

"[AUTO_LEXER](oracle-text-indexing-elements.md)"

"[CREATE_POLICY](CTX_DDL-package.md)"

### 9.17 POLICY_THEMES

Generates a list of themes for a document. With this procedure, no `CONTEXT` index is required.

#### Syntax

    ctx_doc.policy_themes(policy_name    in VARCHAR2,
                              document       in [VARCHAR2|CLOB|BLOB|BFILE],
                          restab         in out nocopy theme_tab,
                          full_themes    in BOOLEAN default FALSE,
                          num_themes     in number    default 50
                          language       in VARCHAR2 default NULL,
                          format         in VARCHAR2 default NULL,
                          charset        in VARCHAR2 default NULL
    );

policy_name
Specify the policy you create with CTX_DDL.[CREATE_POLICY](CTX_DDL-package.md).

document
Specify the document for which to generate a list of themes.

restab
Specify the name of the `theme_tab` PL/SQL index-by-table type.

**See Also:**

"THEMES" for more information about the structure of the `theme_tab` type.

full_themes
Specify whether this procedure generates a single theme or a hierarchical list of parent themes (full themes) for each document theme.

Specify `TRUE` for this procedure to write full themes to the `THEME` column of the result table.

Specify `FALSE` for this procedure to write single theme information to the `THEME` column of the result table. This is the default.

num_themes
Specify the maximum number of themes to retrieve. For example, if you specify 10, up to first 10 themes are returned for the document. The default is 50.

If you specify 0 or `NULL`, this procedure returns all themes in a document. If the document contains more than 50 themes, only the first 50 themes show conceptual hierarchy.

language
Specify the language of the document. Use an Oracle Text supported language value as you would in the language column of the base table. See "[MULTI_LEXER](oracle-text-indexing-elements.md)" in [Oracle Text Indexing Elements](oracle-text-indexing-elements.md).

format
Specify the format of the document. Use an Oracle Text supported format value, either `TEXT`, `BINARY` or `IGNORE` as you would specify in the format column of the base table. For more information, see the format column description in "[CREATE INDEX](oracle-text-SQL-statements-and-operators.md)" in [Oracle Text SQL Statements and Operators](oracle-text-SQL-statements-and-operators.md) .

charset
Specify the character set of the document. Use an Oracle Text supported value as you would specify in the charset column of the base table. See "[Filter Types](oracle-text-indexing-elements.md)".

#### Example

Create a policy:

    exec ctx_ddl.create_policy('mypolicy');

Run themes:

    declare
      la      varchar2(200);
      rtab    ctx_doc.theme_tab;
    begin
       ctx_doc.policy_themes('mypolicy',
               'To define true madness, What is''t but to be nothing but mad?', rtab);
       for i in 1..rtab.count loop
         dbms_output.put_line(rtab(i).theme||':'||rtab(i).weight);
       end loop;
    end;

### 9.18 POLICY_TOKENS

Generate all index tokens for document. With this procedure, no `CONTEXT` index is required.

#### Syntax

    ctx_doc.policy_tokens(policy_name    in  VARCHAR2,
                          document       in  [VARCHAR2|CLOB|BLOB|BFILE],
                          restab         in  out nocopy token_tab,
                          language       in  VARCHAR2 default NULL,
                          format         in  VARCHAR2 default NULL,
                          charset        in  VARCHAR2 default NULL,
                          thes_name      in  VARCHAR2 default NULL,
                          thes_toktype   in  VARCHAR2 default 'SYN');

policy_name
Specify the policy name created with CTX_DDL.[CREATE_POLICY](CTX_DDL-package.md).

document
Specify the document for which to generate tokens.

restab
Specify the name of the `token_tab` PL/SQL index-by-table type.

The tokens returned are those tokens which are inserted into the index for the document. Stop words are not returned. Section tags are not returned because they are not text tokens.

**See Also:**

"TOKENS" of this chapter for more information about the structure of the `token_tab` type

language
Specify the language of the document. Use an Oracle Text supported language value as you would in the language column of the base table. See "[MULTI_LEXER](oracle-text-indexing-elements.md)" in [Oracle Text Indexing Elements](oracle-text-indexing-elements.md).

format
Specify the format of the document. Use an Oracle Text supported format value, either TEXT, BINARY or IGNORE as you would specify in the format column of the base table. For more information, see the format column description in "[CREATE INDEX](oracle-text-SQL-statements-and-operators.md)".

charset
Specify the character set of the document. Use an Oracle Text supported value as you would specify in the charset column of the base table. See "[Filter Types](oracle-text-indexing-elements.md)".

thes_name
Specify the thesaurus name. If you do not specify a name, no synonyms or broader terms for index tokens will be generated.

To use the system default thesaurus, specify `DEFAULT`.

thes_toktype
Specify `SYN` to generate synonyms. Alternatively, specify `BT` to generate broader terms of index tokens. By default, only synonyms are generated. To use this parameter, you must first specify the thesaurus name using the `thes_name` parameter.

#### Example 1

Get tokens:

    declare
      la     varchar2(200);
      rtab   ctx_doc.token_tab;
    begin
       ctx_doc.policy_tokens('mypolicy',
            'To define true madness, What is''t but to be nothing but mad?',rtab);
       for i in 1..rtab.count loop
         dbms_output.put_line(rtab(i).offset||':'||rtab(i).token);
       end loop;
    end;

#### Example 2

This example uses thesaurus support to generate synonyms for tokens:

    declare
      rtab   ctx_doc.token_tab;
    begin
       ctx_doc.policy_tokens('mypolicy','the lazy dog',rtab,thes_name =>'animals');
       for i in 1..rtab.count loop
         dbms_output.put_line(rtab(i).token||'a'||rtab(i).thes_tokens);
       end loop;
    end;

### 9.19 SENTIMENT

Use this procedure to perform sentiment analysis for a document, determine a sentiment score for each topic within the document, and populate the results into a result table.

The mandatory inputs to this procedure include the name of a text index associated with the document set and the text key, which is a unique identifier that identifies each document. After sentiment classification is performed, the text segments from the document and their associated sentiment scores are populated into the result table. The sentiment score is a value between -100 and 100.

The result table must exist before you run this procedure. An error is returned if the result table does not exist or if the specified topic is null.

If the specified topic is not present in the document, then a default snippet and sentiment score of zero are written into the result table. If no sentiment classifier is specified, then the default sentiment classifier is used. The default classifier is only available when using `AUTO_LEXER`.

#### Syntax

    SENTIMENT(
        index_name IN VARCHAR2,
        textkey IN VARCHAR2,
        topic IN VARCHAR2,
        restab IN VARCHAR2,
        clsfier_name IN VARCHAR2 default NULL,
        ttype IN VARCHAR2 default 'EXACT',
        radius IN NUMBER default 50,
        max_inst IN NUMBER default 5,
        starttag IN VARCHAR2 default '',
        endtag IN VARCHAR2 default '',
        use_saved_copy IN NUMBER default 0
    );

Most parameters in `SENTIMENT` are also used in `SENTIMENT_AGGREGATE`. For a description of parameters common to `SENTIMENT` and `SENTIMENT_AGGREGATE`, refer to SENTIMENT_AGGREGATE.

restab
Specify the name of the result table that will be populated with generated results. The table must exist and you must have `INSERT` permissions on the table. The table must have two columns, `snippet` of data type `CLOB` and `score` of data type `NUMBER`.

starttag
Specify the character(s) to be inserted to indicate the start of a highlighted term.

endtag
Specify the character(s) to be inserted to indicate the end of a highlighted term.

**See Also:**

[Oracle Text Application Developer's Guide](../ccapp/performing-sentiment-analysis-using-oracle-text.md) for an example of using the `SENTIMENT` procedure

### 9.20 SENTIMENT_AGGREGATE

Use this procedure to perform sentiment analysis and return a single aggregate sentiment score per document. The aggregate sentiment score is a value between -100 and 100.

You specify search keywords as part of a text query and then identify a sentiment associated with the topics in the document.

The mandatory inputs for this procedure include the name of a text index associated with the document set and the text key, which is a unique identifier that identifies each document. If no sentiment classifier is specified, then the default sentiment classifier is used. The default classifier is only available when using `AUTO_LEXER`.

If the specified topic keyword is not found within the document, then a sentiment score of zero is returned. If no topic is specified, then the aggregate sentiment score for the entire document is returned.

**Note:**

Avoid using `AUTO_LEXER` with user-defined classifiers as this may provide inconsistent sentiment scores.

#### Syntax

    SENTIMENT_AGGREGATE(
        index_name IN VARCHAR2,
        textkey IN VARCHAR2,
        topic IN VARCHAR2 default NULL,
        clsfier_name IN VARCHAR2 default NULL,
        ttype IN VARCHAR2 default 'EXACT',
        radius IN NUMBER default 50,
        max_inst IN NUMBER default 5,
        use_saved_copy IN NUMBER default 0
    ) return NUMBER;

index_name
Specify the name of the `CONTEXT` index for the text column. This parameter is mandatory.

textkey
Specify the unique identifier (usually the primary key) for the document. The `textkey` is mandatory and is a single column primary key value.

clsfier_name
Specify the name of the sentiment classifier used to perform sentiment analysis. The maximum length supported for a classifier name is 24 bytes. If you do not specify a classifier name, then the default classifier is used.

topic
Specify the topic for which a sentiment score must be generated for this document. If the topic is not specified, then the sentiment score for the entire document is generated.

ttype
Specify the type of search to be performed for this document:

- `EXACT:` Indicates that the specified search keyword must be searched in the document. This is the default setting.

- `ABOUT:` Indicates that the thesaurus must be used to find words that are related to the search keywords.

radius
Specifies the radius of the surrounding text to be analyzed during sentiment classification. The default value is 50.

The exact amount of text used for analysis varies from case to case because Oracle Text attempts to find the best match text segment with respect to nearby topic keywords, word boundaries, and sentence boundaries.

max_inst
Specify the maximum number of instances/occurrences of the `topic` that must be analyzed. The default value for this parameter is 5.

use_saved_copy
Specify whether to refer to the `$D` table to fetch the copy of the document and what action to take when the copy of the document is not available in the `$D` table. The default value of this parameter is zero.

**See Also:**

[Oracle Text Application Developer's Guide](../ccapp/performing-sentiment-analysis-using-oracle-text.md) for an example of using the `SENTIMENT_AGGREGATE` procedure

### 9.21 SET_KEY_TYPE

Use this procedure to set the `CTX_DOC` procedures to accept either the `ROWID` or the `PRIMARY_KEY` document identifiers. This setting affects the invoking session only.

#### Syntax

    ctx_doc.set_key_type(key_type in varchar2);

key_type
Specify either `ROWID` or `PRIMARY_KEY` as the input key type (document identifier) for `CTX_DOC` procedures.

This parameter defaults to the value of the `CTX_DOC_KEY_TYPE` system parameter.

**Note:**

- When your base table has no primary key, setting key_type to `PRIMARY_KEY` is ignored. The textkey parameter that you specify for any `CTX_DOC` procedure is interpreted as a `ROWID`.

- `CTX_DOC.SET_KEY_TYPE` fails to set `PRIMARY_KEY` as the input key type for `CTX_DOC` procedures, if it’s `PRIMARY_KEY` is added to the table post index creation. `ORA-20000` error is displayed. The workaround is to drop the index and recreate the index.

#### Example

The following example sets `CTX_DOC` procedures to accept primary key document identifiers.

    begin
    ctx_doc.set_key_type('PRIMARY_KEY');
    end

### 9.22 SNIPPET

Use the `CTX_DOC.SNIPPET` procedure to produce a concordance for a document. The output of a snippet is a collection of segments. A concordance is a text fragment that contains a query term with some of its surrounding text. This is also sometimes known as Key Word in Context or KWIC, because it returns query keywords marked up in their surrounding text, which enables the user to evaluate them in context. The returned text can also contain themes that satisfy an `ABOUT` query.

For example, a search on brillig and slithey might return one relevant fragment of a document as follows:

    'Twas <b>brillig</b>, and the <b>slithey</b> toves did gyre and

`CTX_DOC.SNIPPET` returns one or more most relevant fragments for a document that contains the query term. Because `CTX_DOC.SNIPPET` returns surrounding text, you can immediately evaluate how useful the returned term is. `CTX_DOC.SNIPPET` returns the entire document if no words in the returned text are marked up.

Note that for queries that have predicates used mainly for filtering documents at query time, the predicates are ignored during `SNIPPET` generation. The following predicates are treated as filter predicates for this purpose: `SDATA`, `HASPATH`, and `WITHIN`/`INPATH` searching inside xml attributes.

**See Also:**

CTX_DOC.POLICY_SNIPPET for a policy-based version of this procedure

#### Syntax

Syntax 1

    exec CTX_DOC.SNIPPET(

    index_name               IN VARCHAR2,
    textkey                  IN VARCHAR2,
    text_query               IN VARCHAR2,
    starttag                 IN VARCHAR2 DEFAULT '<b>',
    endtag                   IN VARCHAR2 DEFAULT '</b>',
    entity_translation       IN BOOLEAN  DEFAULT TRUE,
    separator                IN VARCHAR2 DEFAULT '<b>...</b>',
    radius                     IN INTEGER DEFAULT 25,
    max_length               IN INTEGER DEFAULT 250
    use_saved_copy           IN NUMBER DEFAULT CTX_DOC.SAVE_COPY_FALLBACK
    return varchar2
    );

Syntax 2

    exec CTX_DOC.SNIPPET_CLOB_QUERY(
    index_name               IN VARCHAR2,
    textkey                  IN VARCHAR2,
    text_query               IN CLOB,
    starttag                 IN VARCHAR2 DEFAULT '<b>',
    endtag                   IN VARCHAR2 DEFAULT '</b>',
    entity_translation       IN BOOLEAN DEFAULT TRUE,
    separator                IN VARCHAR2 DEFAULT '<b>...</b>',
    radius                     IN INTEGER DEFAULT 25,
    max_length               IN INTEGER DEFAULT 250
    use_saved_copy           IN NUMBER DEFAULT CTX_DOC.SAVE_COPY_FALLBACK
    return varchar2
    );

index_name
Specify the name of the index for the text column.

textkey
Specify the unique identifier (usually the primary key) for the document.

The `textkey` parameter can be as follows:

- A single column primary key value

- An encoded specification for a composite (multiple column) primary key. When textkey is a composite key, you must encode the composite textkey string using the `CTX_DOC.PKENCODE` procedure.

- The rowid of the row containing the document

Use `CTX_DOC.SET_KEY_TYPE` to toggle between primary key and rowid identification.

text_query
Specify the original query expression used to retrieve the document. If NULL, no highlights are generated.

If `text_query` includes wildcards, stemming, fuzzy matching which result in stopwords being returned, `SNIPPET` does not highlight the stopwords.

If `text_query` contains the threshold operator, the operator is ignored.

starttag
Specify the start tag for marking up the query keywords. Default is '\<b\>'.

endtag
Specify the end tag for marking up the query keywords. Default is '\</b\>'.

entity_translation
Specify if you want HTML entities to be translated. The default is TRUE, which means that the special entities (\<, \>, and &) are translated into their alternative forms ('&lt;', '&gt;', and '&amp;') when output by the procedure. However, special characters in the markup tags that are generated by `CTX_DOC.SNIPPET` will not be translated.

separator
Specify the string separating different returned fragments. Default is '\<b\>...\</b\>'.

radius
Specify the number of characters to be shown on either side of the hit query in a segment. The character count before the hit query begins on the first character of the first hit query displayed in a segment. Accordingly, the character count after the hit query begins on the last character of the last hit query displayed on a specific segment. Two segments are merged into one if their radii overlap. The displayed number of characters on each side may be modified by +/-10 chars to best match the beginning or ending of a sentence or word.

Special attention is required for the value `0`. When specified, the radius is set to automatic and varies between sentences. A best guess of the results is displayed, which attempts to match a full sentence. Note that the length of the radius on each side of the hit query will most likely significantly differ.

The default value is 25.

max_length
Specify the maximum length of the snippet output in characters. This value is currently upper-bounded by the current return type of CTX_DOC.SNIPPET and CTX_DOC.POLICY_SNIPPET (VARCHAR2). Should the output be longer than the return type VARCHAR2, the result will be truncated. The default value for max_length is 250.

If you set `max_length` value to a very low value, no snippet may be generated. For example, if `max_length` is set to `0` or if `max_length` is lower than the length of query tokens themselves, no snippet may be generated at all.

use_saved_copy
Specify whether to refer to the \$D table to fetch the copy of the document, and what action to take when the copy of the document is not available in the \$D table. The default value is `CTX_DOC.SAVE_COPY_FALLBACK`.

You can specify one of the following values for the `use_saved_copy` parameter:

- `CTX_DOC.SAVE_COPY_FALLBACK`: Fetch the copy of the document from the \$D table. If the copy of the document is not present in the \$D table, then fetch the document from the data store.

- `CTX_DOC.SAVE_COPY_ERROR`: Fetch the copy of the document from the \$D table. If the copy of the document is not present in the \$D table, then show an error message. Specify this value when you want to implement a specific fallback logic when the copy of the document is not available in the \$D table.

- `CTX_DOC.SAVE_COPY_IGNORE`: Always fetch the document from the data store.

#### Example

    create table tdrbhk01 (id number primary key, text varchar2(4000));

    insert into tdrbhk01 values (1, 'Oracle Text adds powerful search
     and intelligent text management to the Oracle
    database.  Complete.  You can search and manage documents, web pages,
    catalog entries in more than 150 formats in any language.  Provides a
    complete text query language and complete character support.  Simple.  You
    can index and search text using SQL. Oracle Text Management can be done
    using Oracle Enterprise Manager - a GUI tool.  Fast.  You can search
    millions of documents, document,web pages, catalog entries using the
    power and scalability of the database.  Intelligent.  Oracle Text''s
    unique knowledge-base enables you to search, classify, manage
    documents, clusters and summarize text based on its meaning as well as
    its content. ');

    create index tdrbhk01x on tdrbhk01(text) indextype is ctxsys.context;

    create or replace function my_snippet_wrapper(
     key in varchar2,
     query in varchar2,
     radius in number,
     max_length in number) return varchar2 is
      buff varchar2(4000);
     begin
      buff := ctx_doc.snippet('tdrbhk01x', key, query, '<b>', '<b>', true, '<b>..<b>', radius, max_length);
      return buff;
     end;
    /
    show errors;

    select my_snippet_wrapper('1','Oracle', 10, 100) from dual;

The result looks something like this:

    CTX_DOC.SNIPPET('TDRBHK01X','1','SEARCH|CLASSIFY')
    ------------------------------------------------------------------------

    Text's unique knowledge-base enables you to <b>search</b>,
    <b>classify</b>, manage documents, clusters and summarize

#### Limitations

`CTX_DOC.SNIPPET` does not support the use of query templates.

`CTX_DOC.SNIPPET` displays marked-up keywords in context when used with `NULL_SECTION_GROUP`. However, there are limitations when using this procedure with XML documents. When used with `XML_SECTION_GROUP` or `AUTO_SECTION_GROUP`, the XML structure is ignored and user-specified tags are stripped out, which results in parts of surrounding text to be included in the returned snippet.

#### Related Topics

"POLICY_SNIPPET"

"HIGHLIGHT "

"MARKUP "

### 9.23 THEMES

Use the `CTX_DOC.THEMES` procedure to generate a list of themes for a document. You can store each theme as a row in either a result table or an in-memory PL/SQL table that you specify.

#### Syntax 1: In-Memory Table Storage

    CTX_DOC.THEMES(

    index_name      IN VARCHAR2,
    textkey         IN VARCHAR2,
    restab          IN OUT NOCOPY THEME_TAB,
    full_themes     IN BOOLEAN DEFAULT FALSE,
    num_themes      IN NUMBER DEFAULT 50,
    use_saved_copy  IN NUMBER DEFAULT CTX_DOC.SAVE_COPY_FALLBACK);

#### Syntax 2: Result Table Storage

    CTX_DOC.THEMES(

    index_name      IN VARCHAR2,
    textkey         IN VARCHAR2,
    restab          IN VARCHAR2,
    query_id        IN NUMBER DEFAULT 0,
    full_themes     IN BOOLEAN DEFAULT FALSE,
    num_themes      IN NUMBER DEFAULT 50,
    use_saved_copy  IN NUMBER DEFAULT CTX_DOC.SAVE_COPY_FALLBACK);

index_name
Specify the name of the index for the text column.

textkey
Specify the unique identifier (usually the primary key) for the document.

The `textkey` parameter can be as follows:

- A single column primary key value

- An encoded specification for a composite (multiple column) primary key. When textkey is a composite key, you must encode the composite `textkey` string using the `CTX_DOC.PKENCODE` procedure.

- The rowid of the row containing the document

Toggle between primary key and rowid identification using `CTX_DOC.SET_KEY_TYPE`.

restab
You can specify this procedure to store results to either a table or to an in-memory PL/SQL table.

To store results in a table, specify the name of the table.

**See Also:**

"[Theme Table](oracle-text-result-tables.md)" in [Oracle Text Result Tables](oracle-text-result-tables.md)

To store results in an in-memory table, specify the name of the in-memory table of type `THEME_TAB`. The `THEME_TAB` datatype is defined as follows:

    type theme_rec is record (
       theme varchar2(2000),
       weight number
    );

    type theme_tab is table of theme_rec index by binary_integer;

`CTX_DOC.THEMES` clears the `THEME_TAB` you specify before the operation.

query_id
Specify the identifier used to identify the row(s) inserted into `restab`.

full_themes
Specify whether this procedure generates a single theme or a hierarchical list of parent themes (full themes) for each document theme.

Specify `TRUE` for this procedure to write full themes to the `THEME` column of the result table.

Specify `FALSE` for this procedure to write single theme information to the `THEME` column of the result table. This is the default.

num_themes
Specify the maximum number of themes to retrieve. For example, if you specify 10, then up to the first 10 themes are returned for the document. The default is 50.

If you specify 0 or `NULL`, then this procedure returns all themes in a document. If the document contains more than 50 themes, then only the first 50 themes show conceptual hierarchy.

use_saved_copy
Specify whether to refer to the \$D table to fetch the copy of the document, and what action to take when the copy of the document is not available in the \$D table.

You can specify one of the following values for the `use_saved_copy` parameter:

- `CTX_DOC.SAVE_COPY_FALLBACK`: Fetch the copy of the document from the \$D table. If the copy of the document is not present in the \$D table, then fetch the document from the data store.

- `CTX_DOC.SAVE_COPY_ERROR`: Fetch the copy of the document from the \$D table. If the copy of the document is not present in the \$D table, then show an error message. Specify this value when you want to implement a specific fallback logic when the copy of the document is not available in the \$D table.

- `CTX_DOC.SAVE_COPY_IGNORE`: Always fetch the document from the data store.

The default value is `CTX_DOC.SAVE_COPY_FALLBACK`.

#### Examples

In-Memory Themes

The following example generates the first 10 themes for document 1 and stores them in an in-memory table called `the_themes`. The example then loops through the table to display the document themes.

    declare
     the_themes ctx_doc.theme_tab;

    begin
     ctx_doc.themes('myindex','1',the_themes, num_themes=>10);
     for i in 1..the_themes.count loop
      dbms_output.put_line(the_themes(i).theme||':'||the_themes(i).weight);
      end loop;
    end;

Theme Table

The following example creates a theme table called `CTX_THEMES`:

    create table CTX_THEMES (query_id number,
                             theme varchar2(2000),
                             weight number);

Single Themes

To obtain a list of up to the first 20 themes, where each element in the list is a single theme, enter a statement like the following example:

    begin

     ctx_doc.themes('newsindex','34','CTX_THEMES',1,full_themes => FALSE,
     num_themes=> 20);

    end;

Full Themes

To obtain a list of the top 20 themes, where each element in the list is a hierarchical list of parent themes, enter a statement like the following example:

    begin

    ctx_doc.themes('newsindex','34','CTX_THEMES',1,full_themes => TRUE, num_
    themes=>20);

    end;

### 9.24 TOKENS

Use this procedure to identify all text tokens in a document. The tokens returned are those tokens that are inserted into the index.

Thesaurus support also enables you to generate synonyms or broader terms of the queried index tokens. This feature is useful for implementing document classification, routing, or clustering.

Stopwords are not returned. Section tags are not returned because they are not text tokens.

#### Syntax 1: In-Memory Table Storage

    CTX_DOC.TOKENS(index_name      IN VARCHAR2,
                   textkey         IN VARCHAR2,
                   restab          IN OUT NOCOPY TOKEN_TAB,
                   thes_name       IN VARCHAR2 DEFAULT NULL,
                   thes_toktype    IN VARCHAR2 DEFAULT 'SYN',
                   use_saved_copy  IN NUMBER DEFAULT CTX_DOC.SAVE_COPY_FALLBACK);

#### Syntax 2: Result Table Storage

    CTX_DOC.TOKENS(index_name      IN VARCHAR2,
                   textkey         IN VARCHAR2,
                   restab          IN VARCHAR2,
                   thes_name       IN VARCHAR2 DEFAULT NULL,
                   thes_toktype    IN VARCHAR2 DEFAULT 'SYN',
                   query_id        IN NUMBER DEFAULT 0,
                   use_saved_copy  IN NUMBER DEFAULT CTX_DOC.SAVE_COPY_FALLBACK);

index_name
Specify the name of the index for the text column.

textkey
Specify the unique identifier (usually the primary key) for the document.

The `textkey` parameter can be as follows:

- A single column primary key value

- Encoded specification for a composite (multiple column) primary key. To encode a composite `textkey`, use the CTX_DOC.PKENCODE procedure.

- The rowid of the row containing the document

Toggle between primary key and rowid identification using CTX_DOC.SET_KEY_TYPE.

restab
You can specify that this procedure store results to either a table or to an in-memory PL/SQL table.

The tokens returned are those tokens that are inserted into the index for the document (or row) named with `textkey`. Stop words are not returned. Section tags are not returned because they are not text tokens.

<!-- -->

thes_name
Specify the thesaurus name. If you do not specify a thesaurus name, then no synonyms or broader terms will be generated. To use the system default thesaurus, specify `DEFAULT`.

If you specify `thes_name`, then the token table must include the `THES_TOKENS` column, otherwise the `CTX_DOC.TOKENS` procedure fails with an "`ORA-00904: THES_TOKENS: Invalid identifier when thes_name parameter is used`" error.

thes_toktype
Specify `SYN` to generate synonyms of index tokens. Alternatively, specify `BT` to generate broader terms of index tokens. By default, synonyms are generated. To use this parameter, you must first specify a thesaurus name using the `thes_name` parameter.

Specifying a Token Table

To store results to a table, specify the name of the table. Token tables can be named anything, but must include the columns shown in the following table, with names and datatypes as specified.

Table 9-2 Required Columns for Token Tables

| Column Name   | Type             | Description                                                                                                                                                                                                                                                       |
|:--------------|:-----------------|:------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `QUERY_ID`    | `NUMBER`         | The identifier for the results generated by a particular call to `CTX_DOC.TOKENS` (only populated when table is used to store results from multiple `TOKEN` calls)                                                                                                |
| `TOKEN`       | `VARCHAR2(255)`  | The token string in the text.                                                                                                                                                                                                                                     |
| `THES_TOKENS` | `VARCHAR2(4000)` | Synonyms or broader terms generated using a thesaurus for the token in the `TOKEN` column. These values must be colon-separated.<br>**Note:**<br>The `THES_TOKENS` column is required only if you specify the `thes_name` argument with the `CTX_DOC.TOKENS` API. |
| `OFFSET`      | `NUMBER`         | The position of the token in the document, relative to the start of document which has a position of 1.                                                                                                                                                           |
| `LENGTH`      | `NUMBER`         | The character length of the token.                                                                                                                                                                                                                                |

#### Specifying an In-Memory Table

To store results to an in-memory table, specify the name of the in-memory table of type `TOKEN_TAB`. The `TOKEN_TAB` datatype is defined as follows:

    type token_rec is record (

    token varchar2(255),
    offset number,
    length number

    );

    type token_tab is table of token_rec index by binary_integer;

`CTX_DOC.TOKENS` clears the `TOKEN_TAB` you specify before the operation.

query_id
Specify the identifier used to identify the row(s) inserted into `restab`.

use_saved_copy
Specify whether to refer to the \$D table to fetch the copy of the document, and what action to take when the copy of the document is not available in the \$D table.

You can specify one of the following values for the `use_saved_copy` parameter:

- `CTX_DOC.SAVE_COPY_FALLBACK`: Fetch the copy of the document from the \$D table. If the copy of the document is not present in the \$D table, then fetch the document from the data store.

- `CTX_DOC.SAVE_COPY_ERROR`: Fetch the copy of the document from the \$D table. If the copy of the document is not present in the \$D table, then show an error message. Specify this value when you want to implement a specific fallback logic when the copy of the document is not available in the \$D table.

- `CTX_DOC.SAVE_COPY_IGNORE`: Always fetch the document from the data store.

The default value is `CTX_DOC.SAVE_COPY_FALLBACK`.

#### Example

In-Memory Tokens

The following example generates the tokens for document 1 and stores them in an in-memory table, declared as `the_tokens`. The example then loops through the table to display the document tokens.

    declare
     the_tokens ctx_doc.token_tab;

    begin
     ctx_doc.tokens('myindex','1',the_tokens);
     for i in 1..the_tokens.count loop
      dbms_output.put_line(the_tokens(i).token);
      end loop;
    end;
