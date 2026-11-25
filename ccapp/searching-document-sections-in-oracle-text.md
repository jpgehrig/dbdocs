You can use document sections in a text query application.

This chapter contains the following topics:

- About Oracle Text Document Section Searching

- HTML Section Searching with Oracle Text

- XML Section Searching with Oracle Text

### 11.1 About Oracle Text Document Section Searching

Section searching enables you to narrow text queries down to blocks of text within documents. Section searching is useful when your documents have internal structure, such as HTML and XML documents.

You can also search for text at the sentence and paragraph level.

This section contains these topics:

- Enabling Oracle Text Section Searching

- Oracle Text Section Types

- Oracle Text Section Attributes

#### 11.1.1 Enabling Oracle Text Section Searching

The steps for enabling section searching for your document collection are:

1.  Create a Section Group

2.  Define Your Sections

3.  Index Your Documents

4.  Section Searching with the WITHIN Operator

5.  Path Searching with INPATH and HASPATH Operators

6.  Marking an SDATA Section to be Searchable

##### 11.1.1.1 Create a Section Group

You enable section searching by defining section groups. Use one of the system-defined section groups to create an instance of a section group.

You use section groups to specify the type of document set that you have and implicitly indicate the tag structure. Choose a section group that is appropriate for your document collection. For instance, to index HTML tagged documents, use `HTML_SECTION_GROUP`. Likewise, to index XML tagged documents, use `XML_SECTION_GROUP`.

Table 11-1 Types of Section Groups

| Section Group Preference | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    |
|:-------------------------|:-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `NULL_SECTION_GROUP`     | This is the default. Use this group type when you define no sections or when you define only `SENTENCE` or `PARAGRAPH` sections.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                               |
| `BASIC_SECTION_GROUP`    | Use this group type for defining sections where the start and end tags are of the form `<A>` and `</A>`.<br>Note: This group type does not support input such as unbalanced parentheses, comments tags, and attributes. Use `HTML_SECTION_GROUP` for this type of input.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       |
| `HTML_SECTION_GROUP`     | Use this group type to index HTML documents and for defining sections in HTML documents.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       |
| `XML_SECTION_GROUP`      | Use this group type to index XML documents and for defining sections in XML documents.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         |
| `AUTO_SECTION_GROUP`     | Use this group type to automatically create a zone section for each start-tag/end-tag pair in an XML document. As in XML, the section names derived from XML tags are case-sensitive.<br>Attribute sections are created automatically for XML tags that have attributes. Attribute sections are named in the form tag@attribute.<br>Stop sections, empty tags, processing instructions, and comments are not indexed.<br>The following limitations apply to automatic section groups:<br>• You cannot add zone, field, or special sections to an automatic section group.<br>• Automatic sectioning does not index XML document types (root elements.)<br>• The length of the indexed tags, including prefix and namespace, cannot exceed 64 bytes. Tags longer than 64 bytes are not indexed. |
| `PATH_SECTION_GROUP`     | Use this group type to index XML documents. This preference behaves like `AUTO_SECTION_GROUP.`<br>The difference is that you can search paths with the `INPATH` and `HASPATH` operators. Queries are also case-sensitive for tag and attribute names.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          |
| `NEWS_SECTION_GROUP`     | Use this group to define sections in newsgroup-formatted documents according to RFC 1036.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      |

##### Notes

- Documents sent to the `HTML`, `XML`, `AUTO`, and `PATH` sectioners must begin with `\s*<.` The `\s*` represents zero or more whitespace characters. Otherwise, the document is treated as a plain-text document, and no sections are recognized.

- Do not use left-angle-brackets within a section data. If a left-angle-bracket is followed by a non-blank character, then the section parser treats the free text (between the left-angle and right-angle brackets) as a tag name.

  For example:

      <DOCUMENT> <BODYTEXT> ABC
      < R1 NOMISS
      <R2 MISSED1 </BODYTEXT> <FIELDS> DEF
      <R3 MISSED2 </FIELDS> </DOCUMENT> GHI FALSEPOSITIVE JKL

  In the preceding example, the section parser treats `R2 MISSED1 </BODYTEXT` and `R3 MISSED2 </FIELDS` as tag names. This may result in false-positive hits or missed hits, which may cause the following issues:
  - Any word in the `R2 MISSED1 </BODYTEXT` and `R3 MISSED2 </FIELDS` phrases are not searchable within a section.

  - Any text outside a section, such as `GHI`, `FALSEPOSITIVE`, and `JKL` are wrongly included in a section if it is not closed.

- You use the `CTX_DDL` package to create section groups and define sections as part of section groups. For example, to index HTML documents, create a section group with `HTML_SECTION_GROUP`:
      begin
      ctx_ddl.create_section_group('htmgroup', 'HTML_SECTION_GROUP');
      end;

- Starting with Oracle Database 18c, use of `NEWS_SECTION_GROUP` is deprecated in Oracle Text. Use external processing instead.

  If you want to index USENET posts, then preprocess the posts to use `BASIC_SECTION_GROUP` or `HTML_SECTION_GROUP` within Oracle Text. USENET is rarely used commercially.

##### 11.1.1.2 Define Your Sections

You define sections as part of the section group. The following example defines a zone section called heading for all text within the HTML `< H1>` tag:

    begin
    ctx_ddl.create_section_group('htmgroup', 'HTML_SECTION_GROUP');
    ctx_ddl.add_zone_section('htmgroup', 'heading', 'H1');
    end;

**Note:**

If you are using `AUTO_SECTION_GROUP` or `PATH_SECTION_GROUP` to index an XML document collection, then you do not have to explicitly define sections. The system defines the sections during indexing.

**See Also:**

- "Oracle Text Section Types" for more information about sections

- "XML Section Searching with Oracle Text" for more information about section searching with XML

##### 11.1.1.3 Index Your Documents

When you index your documents, you specify your section group in the parameter clause of `CREATE` `INDEX.`

    create index myindex on docs(htmlfile) indextype is ctxsys.context
    parameters('filter ctxsys.null_filter section group htmgroup');

##### 11.1.1.4 Search Sections with the WITHIN Operator

When your documents are indexed, you can query within sections by using the `WITHIN` operator. For example, to find all documents that contain the word Oracle within their headings, enter the following query:

    'Oracle WITHIN heading'

**See Also:**

[Oracle Text Reference](../ccref/oracle-text-CONTAINS-query-operators.md) to learn more about using the `WITHIN` operator

##### 11.1.1.5 Search Paths with INPATH and HASPATH Operators

When you use `PATH_SECTION_GROUP,` the system automatically creates XML sections. In addition to using the `WITHIN` operator to enter queries, you can enter path queries with the `INPATH` and `HASPATH` operators.

**See Also:**

- "XML Section Searching with Oracle Text" to learn more about using these operators

- [Oracle Text Reference](../ccref/oracle-text-CONTAINS-query-operators.md) to learn more about using the `INPATH` operator

##### 11.1.1.6 Mark an SDATA Section to Be Searchable

To mark an `SDATA` section to be searchable and have a `$S``datatype` table created, use the `CTX_DDL.SET_SECTION_ATTRIBUTE` API.

The following tables are created:

- `$SN` – `NUMBER`

- `$SD` – `DATE`

- `$SV` – `VARCHAR2`, `CHAR`

- `$SR` – `RAW`

- `$SBD` – `BINARY DOUBLE`

- `$SBF` – `BINARY FLOAT`

- `$ST` – `TIMESTAMP`

- `$STZ` – `TIMESTAMP WITH TIMEZONE`

The following example creates a `$SV` table for this `SDATA` section to allow efficient searching on that section.

    ctx_ddl.add_sdata_section('sec_grp', 'sdata_sec', 'mytag', 'varchar');
    ctx_ddl.set_section_attribute('sec_grp', 'sdata_sec', 'optimized_for', 'search');

The default value of this attribute is `FALSE.`

#### 11.1.2 Oracle Text Section Types

All section types are blocks of text in a document. However, sections can differ in the way that they are delimited and the way that they are recorded in the index. Sections can be one of the following types:

- Zone Section

- Field Section

- Stop Section

- MDATA Section

- NDATA Section

- SDATA Section

- Attribute Section (for XML documents)

- Special Sections (sentence or paragraphs)

Table 11-2 shows which section types may be used with each kind of section group.

Table 11-2 Section Types and Section Groups

| Section Group | ZONE | FIELD | STOP | MDATA | NDATA | SDATA | ATTRIBUTE | SPECIAL |
|:--------------|:-----|:------|:-----|:------|:------|:------|:----------|:--------|
| NULL          | NO   | NO    | NO   | NO    | NO    | NO    | NO        | YES     |
| BASIC         | YES  | YES   | NO   | YES   | YES   | YES   | NO        | YES     |
| HTML          | YES  | YES   | NO   | YES   | YES   | YES   | NO        | YES     |
| XML           | YES  | YES   | NO   | YES   | YES   | YES   | YES       | YES     |
| NEWS          | YES  | YES   | NO   | YES   | YES   | YES   | NO        | YES     |
| AUTO          | NO   | NO    | YES  | NO    | NO    | NO    | NO        | NO      |
| PATH          | NO   | NO    | NO   | NO    | NO    | NO    | NO        | NO      |

##### 11.1.2.1 Zone Section

A zone section is a body of text delimited by start and end tags in a document. The positions of the start and end tags are recorded in the index so that any words in between the tags are considered to be within the section. Any instance of a zone section must have a start and an end tag.

For example, define the text between the `<TITLE>` and `</TITLE>` tags as a zone section as follows:

    <TITLE>Tale of Two Cities</TITLE>
    It was the best of times...

Zone sections can nest, overlap, and repeat within a document.

When querying zone sections, you use the `WITHIN` operator to search for a term across all sections. Oracle Text returns those documents that contain the term within the defined section.

Zone sections are well suited for defining sections in HTML and XML documents. To define a zone section, use `CTX_DDL`.`ADD_ZONE_SECTION.`

For example, assume you define the `booktitle` section as follows:

    begin
    ctx_ddl.create_section_group('htmgroup', 'HTML_SECTION_GROUP');
    ctx_ddl.add_zone_section('htmgroup', 'booktitle', 'TITLE');
    end;

After you index, you can search for all documents that contain the term Cities within the `booktitle` section as follows:

    'Cities WITHIN booktitle'

With multiple query terms such as (dog and cat) WITHIN booktitle, Oracle Text returns those documents that contain cat and dog within the same instance of a `booktitle` section.

##### Repeated Zone Sections

Zone sections can repeat. Each occurrence is treated as a separate section. For example, if `<H1>` denotes a `heading` section, the heading can be repeated in the same documents as follows:

    <H1> The Brown Fox </H1>
    <H1> The Gray Wolf </H1>

Assuming that these zone sections are named `Heading,` a query of Brown WITHIN Heading returns this document. However, a query of (Brown and Gray) WITHIN Heading does not.

##### Overlapping Zone Sections

Zone sections can overlap each other. For example, if `<B>` and `<I>` denote two different zone sections, they can overlap in a document as follows:

    plain <B> bold <I> bold and italic </B> only italic </I>  plain

##### Nested Zone Sections

Zone sections can be nested, as follows:

    <TD> <TABLE><TD>nested cell</TD></TABLE></TD>

Using the `WITHIN` operator, you can write queries to search for text in sections within sections. For example, assume that the `BOOK1, BOOK2,` and `AUTHOR` zone sections occur as follows in the doc1 and doc2 documents:

doc1:

    <book1> <author>Scott Tiger</author> This is a cool book to read.</book1>

doc2:

    <book2> <author>Scott Tiger</author> This is a great book to read.</book2>

Consider the nested query. It returns only doc1.

    '(Scott within author) within book1'

##### 11.1.2.2 Field Section

A field section is similar to a zone section in that it is a region of text delimited by start and end tags. Field sections are more efficient from zone sections and are different than zone sections in that the region is indexed separately from the rest of the document. You can create an unlimited number of field sections.

Because field sections are indexed differently, you can also get better query performance over zone sections when a large number of documents are indexed.

Field sections are more suited to a single occurrence of a section in a document, such as a field in a news header. Field sections can also be made visible to the rest of the document.

Unlike zone sections, field sections have the following restrictions:

- They cannot overlap.

- They cannot repeat.

- They cannot nest.

##### Visible and Invisible Field Sections

By default, field sections are indexed as a sub-document separate from the rest of the document. As such, field sections are invisible to the surrounding text and can only be queried by explicitly naming the section in the `WITHIN` clause.

You can make field sections visible if you want the text within the field section to be indexed as part of the enclosing document. You can query text within a visible field section with or without the `WITHIN` operator.

The following example shows the difference using invisible and visible field sections. The code defines a `basicgroup` section group of the `BASIC_SECTION_GROUP` type. It then creates a field section in `basicgroup` called `Author` for the `<A>` tag. It also sets the visible flag to `FALSE` to create an invisible section.

    begin
    ctx_ddl.create_section_group('basicgroup', 'BASIC_SECTION_GROUP');
    ctx_ddl.add_field_section('basicgroup', 'Author', 'A', FALSE);
    end;

Because the `Author` field section is not visible, to find text within the `Author` section, you must use the `WITHIN` operator.

    '(Martin Luther King) WITHIN Author'

A query of Martin Luther King without the `WITHIN` operator does not return instances of this term in field sections. If you want to query text within field sections without specifying `WITHIN,` you must set the visible flag to `TRUE` when you create the section, as follows:

    begin
    ctx_ddl.add_field_section('basicgroup', 'Author', 'A', TRUE);
    end;

##### Nested Field Sections

You cannot nest field sections. For example, if you define a field section to start with `<TITLE>` and define another field section to start with `<FOO>,` you cannot nest the two sections as follows:

    <TITLE> dog <FOO> cat </FOO> </TITLE>

To work with nested sections, define them as zone sections.

##### Repeated Field Sections

Repeated field sections are allowed, but `WITHIN` queries treat them as a single section. Here is an example of a repeated field section in a document:

    <TITLE> cat </TITLE>
    <TITLE> dog </TITLE>

The query dog and cat within title returns the document, even though these words occur in different sections.

To have `WITHIN` queries distinguish repeated sections, define them as zone sections.

##### 11.1.2.3 Stop Section

When you add a stop section to an automatic section group, the automatic section indexing operation ignores the specified section in XML documents.

**Note:**

Adding a stop section causes no section information to be created in the index. However, the text within a stop section is always searchable.

Adding a stop section is useful when your documents contain many low-information tags. Adding stop sections also improves indexing performance with the automatic section group.

You can add an unlimited number of stop sections.

Stop sections do not have section names and are not recorded in the section views.

##### 11.1.2.4 MDATA Section

You use an `MDATA` section to reference user-defined metadata for a document.

`MDATA` sections can speed up mixed queries, and there is no limit to the number of `MDATA` sections that can be returned in a query.

Consider the case where you want to query according to text content and document type (magazine, newspaper, or novel). You can create an index with a column for text and a column for the document type, and then perform a mixed query of this form. In this case, search for all novels with the phrase Adam Thorpe (author of the novel Ulverton):

    SELECT id FROM documents
       WHERE doctype = 'novel'
          AND CONTAINS(text, 'Adam Thorpe')>0;

However, it is usually faster to incorporate the attribute (in this case, the document type) in a field section, rather than using a separate column, and then using a single `CONTAINS` query.

    SELECT id FROM documents
      WHERE CONTAINS(text, 'Adam Thorpe AND novel WITHIN doctype')>0;

This approach has two drawbacks:

- Each time the attribute is updated, the entire text document must be reindexed, resulting in increased index fragmentation and slower rates of data manipulation language (DML) processing.

- Field sections tokenize the section value. Tokenization has several effects. Special characters in metadata, such as decimal points or currency characters, are not easily searchable; value searching (searching for John Smith but not John Smith, Jr.) is difficult; multiword values are queried by phrase, which is slower than single-token searching; and multiword values do not show up in browsed words, making author browsing or subject browsing impossible.

For these reasons, using `MDATA` sections instead of field sections may be worthwhile. `MDATA` sections are indexed like field sections, but you can add and remove metadata values from documents without the need to reindex the document text. Unlike field sections, `MDATA` values are not tokenized. Additionally, `MDATA` section indexing generally takes up less disk space than field section indexing.

Starting with Oracle Database 12c Release 2 (12.2), the `MDATA` section can be updatable or nonupdatable depending on the value of its read-only tag, which can be set to either `FALSE` or `TRUE`.

Use `CTX_DDL.ADD_MDATA_SECTION` to add an `MDATA` section to a section group. By default, the value of a read-only `MDATA` section is `FALSE.` It implies that you want to permit calling `CTX_DDL.ADD_MDATA()` and `CTX_DDL.REMOVE_MDATA()` for this `MDATA` section, otherwise you can set it to `TRUE.` When set to `FALSE,` the queries on the `MDATA` section run less efficiently because a cursor must be opened on the index table to track the deleted values for that `MDATA` section. This example adds an `MDATA` section called `AUTHOR` and gives it the value Soseki Natsume (author of the novel Kokoro).

    ctx_ddl.create.section.group('htmgroup', 'HTML_SECTION_GROUP');
    ctx_ddl.add_mdata_section('htmgroup', 'author', 'Soseki Natsume');

You can change `MDATA` values with `CTX_DDL.ADD_MDATA,` and you can remove them with `CTX_DDL.REMOVE_MDATA.` Also, `MDATA` sections can have multiple values. Only the owner of the index may call `CTX_DDL.ADD_MDATA` and `CTX_DDL.REMOVE_MDATA.`

Neither `CTX_DDL.ADD_MDATA` nor `CTX_DDL.REMOVE_MDATA` is supported for `CTXCAT` and `CTXRULE` indexes.

`MDATA` values are not passed through a lexer. Instead, all values undergo the following simplified normalization:

- Leading and trailing whitespace on the value is removed.

- The value is truncated to 255 bytes.

- The value is indexed as a single value; if the value consists of multiple words, it is not broken up.

- Case is preserved. If the document is dynamically generated, you can implement case-insensitivity by uppercasing `MDATA` values and making sure to search only in uppercase.

After you add `MDATA` metadata to a document, you can query for that metadata by using the `CONTAINS` query operator:

    SELECT id FROM documents
       WHERE CONTAINS(text, 'Tokyo and MDATA(author, Soseki Natsume)')>0;

This query is only successful if an `AUTHOR` tag has the exact value Soseki Natsume (after simplified tokenization). Soseki or Natsume Soseki returns no rows.

The following are considerations for `MDATA`:

- `MDATA` values are not highlightable, do not appear in the output of `CTX_DOC.TOKENS,` and do not appear when you enable `FILTER PLAINTEXT.`

- `MDATA` sections must be unique within section groups. For example, do not use `FOO` as the name of an `MDATA` section and a zone or field section in the same section group.

- Like field sections, `MDATA` sections cannot overlap or nest. An `MDATA` section is implicitly closed by the first tag encountered. In this example:

      <AUTHOR>Dickens <B>Shelley</B> Keats</AUTHOR>

  The `<B>` tag closes the `AUTHOR` `MDATA` section; as a result, this document has an `AUTHOR` of 'Dickens', but not of 'Shelley' or 'Keats'.

- To prevent race conditions, each call to `ADD_MDATA` and `REMOVE_MDATA` locks out other calls on that rowid for that index for all values and sections. However, because `ADD_MDATA` and `REMOVE_MDATA` do not commit, it is possible for an application to deadlock when calling them both. It is the application's responsibility to prevent deadlocking.

**See Also:**

- `"ALTER INDEX"` in [Oracle Text Reference](../ccref/index.md)

- `"ADD_MDATA_SECTION"` in [Oracle Text Reference](../ccref/index.md)

- The `"CONTAINS"` query operators chapter of the [Oracle Text Reference](../ccref/oracle-text-CONTAINS-query-operators.md) for information on the `MDATA` operator

- The `"CTX_DDL"` package chapter of [Oracle Text Reference](../ccref/CTX_DDL-package.md) for information on adding and removing `MDATA` sections

##### 11.1.2.5 NDATA Section

For fields containing data to be indexed for name searching, you can specify them exclusively by adding `NDATA` sections to section groups of type `BASIC_SECTION_GROUP,` `HTML_SECTION_GROUP,` or `XML_SECTION_GROUP.`

Users can synthesize textual documents, which contain name data, by using two possible datastores: `MULTI_COLUMN_DATASTORE` or `USER_DATASTORE.` The following example uses `MULTI_COLUMN_DATASTORE` to pick up relevant columns containing the name data for indexing:

    create table people(firstname varchar2(80), surname varchar2(80));
     insert into people values('John', 'Smith');
     commit;
     begin
       ctx_ddl.create_preference('nameds', 'MULTI_COLUMN_DATASTORE');
       ctx_ddl.set_attribute('nameds', 'columns', 'firstname,surname');
     end;
     /

This example produces the following virtual text for indexing:

    <FIRSTNAME>
    John
    </FIRSTNAME>
    <SURNAME>
    Smith
    </SURNAME>

You can then create `NDATA` sections for `FIRSTNAME` and `SURNAME` sections:

    begin
      ctx_ddl.create_section_group('namegroup', 'BASIC_SECTION_GROUP');
      ctx_ddl.add_ndata_section('namegroup', 'FIRSTNAME', 'FIRSTNAME');
      ctx_ddl.add_ndata_section('namegroup', 'SURNAME', 'SURNAME');
    end;
    /

Next, create the index by using the datastore preference and section group preference that you created earlier:

    create index peopleidx on people(firstname) indextype is ctxsys.context
    parameters('section group namegroup datastore nameds');

`NDATA` sections support both single- and multibyte data with character- and term-based limitations. `NDATA` section data that is indexed is constrained as follows:

- The number of characters in a single, whitespace-delimited term: 511

- The number of whitespace-delimited terms: 255

- The total number of characters, including whitespaces: 511

##### 11.1.2.6 SDATA Section

The value of an `SDATA` section is extracted from the document text like other sections, but it is indexed as structured data, also referred to as `SDATA.` `SDATA` sections support operations such as projection, range searches, and ordering. `SDATA` sections also enable `SDATA` indexing of section data (such as embedded tags) and detail table or function invocations. You can perform various combinations of text and structured searches in one single SQL statement.

Use `SDATA` operators only as descendants of `AND` operators that also have non-`SDATA` children. `SDATA` operators are meant to be used as secondary (checking or non-driving) criteria. For example, "find documents with DOG that also have price \> 5", rather than "find documents with rating \> 4".

Use `CTX_DDL.ADD_SDATA_SECTION` to add an `SDATA` section to a section group. Use `CTX_DDL.UPDATE_SDATA` to update the values of an existing `SDATA` section. When querying within an `SDATA` section, you must use the `CONTAINS` operator. The following example creates a table called `items,` adds an `SDATA` section called `my_sec_group,` and then queries `SDATA` in the section.

After you create an `SDATA` section, you can further modify the attributes of the `SDATA` section by using `CTX_DDL.SET_SECTION_ATTRIBUTE`.

Create the `items` table:

    CREATE TABLE items
    (id  NUMBER PRIMARY KEY,
     doc VARCHAR2(4000));

    INSERT INTO items VALUES (1, '<description> Honda Pilot </description>
                                  <category> Cars & Trucks </category>
                                  <price> 27000 </price>');
    INSERT INTO items VALUES (2, '<description> Toyota Sequoia </description>
                                  <category> Cars & Trucks </category>
                                  <price> 35000 </price>');
    INSERT INTO items VALUES (3, '<description> Toyota Land Cruiser </description>
                                  <category> Cars & Trucks </category>
                                  <price> 45000 </price>');
    INSERT INTO items VALUES (4, '<description> Palm Pilot </description>
                                  <category> Electronics </category>
                                  <price> 5 </price>');
    INSERT INTO items VALUES (5, '<description> Toyota Land Cruiser Grill </description>
                                  <category> Parts & Accessories </category>
                                  <price> 100 </price>');
    COMMIT;

Add the `my_sec_group` `SDATA` section:

    BEGIN
      CTX_DDL.CREATE_SECTION_GROUP('my_sec_group', 'BASIC_SECTION_GROUP');
      CTX_DDL.ADD_SDATA_SECTION('my_sec_group', 'category', 'category', 'VARCHAR2');
      CTX_DDL.ADD_SDATA_SECTION('my_sec_group', 'price', 'price', 'NUMBER');
    END;


Create the `CONTEXT` index:

    CREATE INDEX items$doc
      ON items(doc)
      INDEXTYPE IS CTXSYS.CONTEXT
      PARAMETERS('SECTION GROUP my_sec_group');


Run a query:

    SELECT id, doc
      FROM items
      WHERE contains(doc, 'Toyota
                           AND SDATA(category = ''Cars & Trucks'')
                           AND SDATA(price <= 40000 )') > 0;

Return the results:

      ID DOC
    ---- ----------------------------------------------------------------------
       2 <description> Toyota Sequoia </description>
                                       <category> Cars & Trucks </category>
                                       <price> 35000 </price>

Consider a document whose rowid is 1. This example updates the value of the `price` `SDATA` section to a new value of 30000:

    BEGIN
        SELECT ROWID INTO rowid_to_update FROM items WHERE id=1;

        CTX_DDL.UPDATE_SDATA('items$doc',
                             'price',
                             SYS.ANYDATA.CONVERTVARCHAR2('30000'),
                             rowid_to_update);
    END;

After executing the query, the price of `Honda Pilot` is changed from 27000 to 30000.

**Note:**

- You can also add an `SDATA` section to an existing index. Use the `ADD SDATA SECTION` parameter of the `ALTER INDEX PARAMETERS` statement. See the "ALTER INDEX" section of the [Oracle Text Reference](../ccref/oracle-text-SQL-statements-and-operators.md) for more information.

- Documents that were indexed before adding an `SDATA` section do not reflect this new preference. Rebuild the index in this case.

**See Also:**

- The "`CONTAINS`" query section of the [Oracle Text Reference](../ccref/oracle-text-CONTAINS-query-operators.md) for information on the `SDATA` operator

- The "`CTX_DDL`" package section of the [Oracle Text Reference](../ccref/CTX_DDL-package.md) for information on adding and updating the `SDATA` sections and changing their attributes by using the `ADD_SDATA_SECTION`, `SET_SECTION_ATTRIBUTE`, and the `UPDATE_SDATA` procedures

Storage

For `optimized_for` search `SDATA` sections, use `CTX_DDL.SET_ATTRIBUTE` to specify the storage preferences for the `$S``datatype` tables and the indexes on these tables.

By default, large object (LOB) caching is turned on for `$S*` tables and off for `$S*` indexes. These attributes are valid only on `SDATA` sections.

Query Operators

`optimized_for search SDATA` supports the following query operators:

- =

- \<\>

- between

- not between

- \<=

- \<

- \>=

- \>

- is null

- is not null

- like

- not like

##### 11.1.2.7 Attribute Section

You can define attribute sections to query on XML attribute text. You can also have the system automatically define and index XML attributes for you.

**See Also:**

"XML Section Searching with Oracle Text"

##### 11.1.2.8 Special Sections

Special sections are not recognized by tags. Currently, sentence and paragraph are the only supported special sections, and they enable you to search for a combination of words within sentences or paragraphs.

The sentence and paragraph boundaries are determined by the lexer. For example, `BASIC_LEXER` recognizes sentence and paragraph section boundaries as follows:

Table 11-3 Sentence and Paragraph Section Boundaries for BASIC_LEXER

| Special Section | Boundary                                                        |
|:----------------|:----------------------------------------------------------------|
| SENTENCE        | • WORD/PUNCT/WHITESPACE<br>• WORD/PUNCT/NEWLINE                 |
| PARAGRAPH       | • WORD/PUNCT/NEWLINE/WHITESPACE<br>• WORD/PUNCT/NEWLINE/NEWLINE |

If the lexer cannot recognize the boundaries, then no sentence or paragraph sections are indexed.

To add a special section, use the `CTX_DDL`.`ADD_SPECIAL_SECTION` procedure. For example, the following code enables searches within sentences in HTML documents:

    begin
    ctx_ddl.create_section_group('htmgroup', 'HTML_SECTION_GROUP');
    ctx_ddl.add_special_section('htmgroup', 'SENTENCE');
    end;

To enable zone and sentence searches, add zone sections to the group. The following example adds the `Headline` zone section to the `htmgroup` section group:

    begin
    ctx_ddl.create_section_group('htmgroup', 'HTML_SECTION_GROUP');
    ctx_ddl.add_special_section('htmgroup', 'SENTENCE');
    ctx_ddl.add_zone_section('htmgroup', 'Headline', 'H1');
    end;

#### 11.1.3 Oracle Text Section Attributes

Section attributes are the attributes that can be specified at the section level rather than at the index level. Currently, the `visible` section attribute is supported for sections of field type.

You can set the `visible` section attribute for field sections using the `CTX_DDL.ADD_FIELD_SECTION` API directly. You can set this attribute to one of the following values:

- `FALSE`: This is the default value. The text in the field section is indexed separately from the rest of the document.

- `TRUE`: You can set this value if you want to make the text visible within a document. The text in the field section is indexed as part of the enclosing document.

The syntax is as follows:

    CTX_DDL.ADD_FIELD_SECTION(
      group_name     IN    VARCHAR2,
      section_name   IN    VARCHAR2,
      tag            IN    VARCHAR2,
      visible        IN    BOOLEAN default FALSE
    );

The following example enables the `visible` attribute for a field section:

    begin
    ctx_ddl.create_section_group(‘fieldgroup', ‘BASIC_SECTION_GROUP');
    ctx_ddl.add_field_section(‘fieldgroup', ‘author', ‘AUTHOR', TRUE);
    end;

Alternatively, you can use the `ALTER INDEX REBUILD` syntax to add a new field section and enable the `visible` section attribute, as follows:

    ALTER INDEX index_name REBUILD parameters(‘ADD FIELD SECTION section_name tag tag [(VISIBLE | INVISIBLE)]’);

**Related Topics**

- [Oracle Text Reference](../ccref/CTX_DDL-package.md)

### 11.2 HTML Section Searching with Oracle Text

HTML has internal structure in the form of tagged text that you can use for section searching. For example, define a section called `headings` for the `<H1>` tag, and then search for terms only within these tags across your document set.

To query, you use the `WITHIN` operator. Oracle Text returns all documents that contain your query term within the `headings` section. For example, if you want to find all documents that contain the word `oracle` within `headings,` enter the following query:

    'oracle within headings'

This section contains these topics:

- Creating HTML Sections

- Searching HTML Meta Tags

#### 11.2.1 Creating HTML Sections

The following code defines a section group called `htmgroup` of type `HTML_SECTION_GROUP.` It then creates a zone section in `htmgroup` called `heading` identified by the `<H1>` tag:

    begin
    ctx_ddl.create_section_group('htmgroup', 'HTML_SECTION_GROUP');
    ctx_ddl.add_zone_section('htmgroup', 'heading', 'H1');
    end;

You can then index your documents as follows:

    create index myindex on docs(htmlfile) indextype is ctxsys.context
    parameters('filter ctxsys.null_filter section group htmgroup');

After indexing with the `htmgroup` section group, you can query within the `heading` section by issuing this query:

    'Oracle WITHIN heading'

#### 11.2.2 Searching HTML Meta Tags

With HTML documents, you can also create sections for `NAME/CONTENT` pairs in `<META>` tags. When you do so, you can limit your searches to text within `CONTENT.`

Consider an HTML document that has the following `META` tag:

    <META NAME="author" CONTENT="ken">

Create a zone section that indexes all `CONTENT` attributes for the `META` tag whose `NAME` value is author:

    begin
    ctx_ddl.create_section_group('htmgroup', 'HTML_SECTION_GROUP');
    ctx_ddl.add_zone_section('htmgroup', 'author', 'meta@author');
    end

After indexing with the `htmgroup` section group, you can query the document:

    'ken WITHIN author'

### 11.3 XML Section Searching with Oracle Text

Like HTML documents, XML documents have tagged text that you can use to define blocks of text for section searching. You can search the contents of a section with the `WITHIN` or `INPATH` operators.

The following sections describe the different types of XML searching:

- Automatic Sectioning

- Attribute Searching

- Document Type Sensitive Sections

- Path Section Searching

#### 11.3.1 Automatic Sectioning

To set up your indexing operation to automatically create sections from XML documents, use the `AUTO_SECTION_GROUP` section group. The system creates zone sections for XML tags. Attribute sections are created for the tags that have attributes and for the sections named in the form `tag@attribute.`

For example, the following statement uses the `AUTO_SECTION_GROUP` to create the myindex index on a column containing the XML files:

    CREATE INDEX myindex
    ON xmldocs(xmlfile)
     INDEXTYPE IS ctxsys.context
    PARAMETERS ('datastore ctxsys.default_datastore
                 filter ctxsys.null_filter
                 section group ctxsys.auto_section_group'
               );

#### 11.3.2 Attribute Searching

You can search XML attribute text in one of two ways:

- Creating Attribute Sections

  Create attribute sections with `CTX_DDL`.`ADD_ATTR_SECTION` and then index with `XML_SECTION_GROUP.` If you use `AUTO_SECTION_GROUP` when you index, attribute sections are created automatically. You can query attribute sections with the `WITHIN` operator.

  Consider an XML file that defines the `BOOK` tag with a `TITLE` attribute:

      <BOOK TITLE="Tale of Two Cities">
        It was the best of times.
      </BOOK>

  To define the title attribute as an attribute section, create an `XML_SECTION_GROUP` and define the attribute section:

      begin
      ctx_ddl.create_section_group('myxmlgroup', 'XML_SECTION_GROUP');
      ctx_ddl.add_attr_section('myxmlgroup', 'booktitle', 'book@title');
      end;

  To index:

      CREATE INDEX myindex
      ON xmldocs(xmlfile)
      INDEXTYPE IS ctxsys.context
      PARAMETERS ('datastore ctxsys.default_datastore
                   filter ctxsys.null_filter
                   section group myxmlgroup'
                 );

  To query the booktitle XML attribute section:

      'Cities within booktitle'

- Searching Attributes with the INPATH Operator

  Index with the `PATH_SECTION_GROUP` and query attribute text with the `INPATH` operator.

**See Also:**

"Path Section Searching"

#### 11.3.3 Document Type Sensitive Sections

For an XML document set that contains the `<book>` tag declared for different document types, you may want to create a distinct book section for each document type to improve search capability. The following scenario shows you how to create book sections for each document type.

Assume that `mydocname1` is declared as an XML document type (root element):

    <!DOCTYPE mydocname1 ... [...

Within `mydocname1,`, the `<book>` element is declared. For this tag, you can create a section named `mybooksec1` that is sensitive to the tag's document type:

    begin

    ctx_ddl.create_section_group('myxmlgroup', 'XML_SECTION_GROUP');
    ctx_ddl.add_zone_section('myxmlgroup', 'mybooksec1', 'mydocname1(book)');

    end;

Assume that `mydocname2` is declared as another XML document type (root element):

    <!DOCTYPE mydocname2 ... [...

Within `mydocname2,`, the `<book>` element is declared. For this tag, you can create a section named `mybooksec2` that is sensitive to the tag's document type:

    begin

    ctx_ddl.create_section_group('myxmlgroup', 'XML_SECTION_GROUP');
    ctx_ddl.add_zone_section('myxmlgroup', 'mybooksec2', 'mydocname2(book)');

    end;

To query within the `mybooksec1` section, use `WITHIN`:

    'oracle within mybooksec1'

#### 11.3.4 Path Section Searching

XML documents can have parent-child tag structures such as:

    <A> <B> <C> dog </C> </B> </A>

In this scenario, tag C is a child of tag B, which is a child of tag A.

With Oracle Text, you can search paths with `PATH_SECTION_GROUP.` This section group enables you to specify direct parentage in queries, such as to find all documents that contain the term dog in element C, which is a child of element B, and so on.

With `PATH_SECTION_GROUP,` you can also perform attribute value searching and attribute equality testing.

The new operators associated with this feature are

- `INPATH`

- `HASPATH`

This section contains the following topics.

- Creating an Index with PATH_SECTION_GROUP

- Top-Level Tag Searching

- Any-Level Tag Searching

- Direct Parentage Searching

- Tag Value Testing

- Attribute Searching

- Attribute Value Testing

- Path Testing

- Section Equality Testing with HASPATH

##### 11.3.4.1 Creating an Index with PATH_SECTION_GROUP

To enable path section searching, index your XML document set with `PATH_SECTION_GROUP.` For example:

Create the preference.

    begin
    ctx_ddl.create_section_group('xmlpathgroup', 'PATH_SECTION_GROUP');
    end;

Create the index.

    CREATE INDEX myindex
    ON xmldocs(xmlfile)
    INDEXTYPE IS ctxsys.context
    PARAMETERS ('datastore ctxsys.default_datastore
                 filter ctxsys.null_filter
                 section group xmlpathgroup'
               );

When you create the index, you can use the `INPATH` and `HASPATH` operators.

##### 11.3.4.2 Top-Level Tag Searching

To find all documents that contain the term dog in the top-level tag `<A>:`

    dog INPATH (/A)

or

    dog INPATH(A)

##### 11.3.4.3 Any-Level Tag Searching

To find all documents that contain the term dog in the `<A>` tag at any level:

    dog INPATH(//A)

This query finds the following documents:

    <A>dog</A>

and

    <C><B><A>dog</A></B></C>

##### 11.3.4.4 Direct Parentage Searching

To find all documents that contain the term dog in a B element that is a direct child of a top-level A element:

    dog INPATH(A/B)

This query finds the following XML document:

    <A><B>My dog is friendly.</B></A>

but it does not find:

    <C><B>My dog is friendly.</B></C>

##### 11.3.4.5 Tag Value Testing

You can test the value of tags. For example, the query:

    dog INPATH(A[B="dog"])

Finds the following document:

    <A><B>dog</B></A>

But does not find:

    <A><B>My dog is friendly.</B></A>

##### 11.3.4.6 Attribute Searching

You can search the content of attributes. For example, the query:

    dog INPATH(//A/@B)

Finds the document:

    <C><A  B="snoop dog"> </A> </C>

##### 11.3.4.7 Attribute Value Testing

You can test the value of attributes. For example, the query:

    California INPATH (//A[@B = "home address"])

Finds the document:

    <A B="home address">San Francisco, California, USA</A>

But it does not find:

    <A B="work address">San Francisco, California, USA</A>

##### 11.3.4.8 Path Testing

You can test if a path exists with the `HASPATH` operator. For example, the query:

    HASPATH(A/B/C)

finds and returns a score of 100 for the document

    <A><B><C>dog</C></B></A>

without the query having to reference dog at all.

##### 11.3.4.9 Section Equality Testing with HASPATH

You can use the `HASPATH` operator for section quality tests. For example, consider the following query:

    dog INPATH A

It finds:

    <A>dog</A>

but it also finds:

    <A>dog park</A>

To limit the query to the term dog and nothing else, you can use a section equality test with the `HASPATH` operator. For example,

    HASPATH(A="dog")

finds and returns a score of 100 only for the first document, not for the second document.

**See Also:**

[Oracle Text Reference](../ccref/oracle-text-CONTAINS-query-operators.md) to learn more about using the `INPATH` and `HASPATH` operators
