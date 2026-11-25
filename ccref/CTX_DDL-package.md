## 8  CTX_DDL Package

The `CTX_DDL` PL/SQL package provides procedures to create and manage the preferences, section groups, and stoplists required for Text indexes.

`CTX_DDL` contains the following stored procedures and functions:

| Name                       | Description                                                                                                      |
|:---------------------------|:-----------------------------------------------------------------------------------------------------------------|
| ADD_ATTR_SECTION           | Adds an attribute section to an XML section group.                                                               |
| ADD_AUTO_OPTIMIZE          | Adds an index or partition to the list of indexes subject to auto optimization.                                  |
| ADD_FIELD_SECTION          | Creates a field section and assigns it to the specified section group.                                           |
| ADD_INDEX                  | Adds an index to a catalog index preference.                                                                     |
| ADD_MDATA                  | Changes the `MDATA` value of a document.                                                                         |
| ADD_MDATA_COLUMN           | Maps a `FILTER` `BY` column to the specified `MDATA` section.                                                    |
| ADD_MDATA_SECTION          | Adds an `MDATA` metadata section to a document.                                                                  |
| ADD_NDATA_SECTION          | Adds an `NDATA` section to a document.                                                                           |
| ADD_SDATA_COLUMN           | Maps a `FILTER` `BY` column to the specified `SDATA` section.                                                    |
| ADD_SDATA_SECTION          | Adds an `SDATA` structured data section to a document.                                                           |
| ADD_SEC_GRP_ATTR_VAL       | Adds a section group attribute value to the list of values of an already existing section group attribute.       |
| ADD_SPECIAL_SECTION        | Adds a special section to a section group.                                                                       |
| ADD_STOPCLASS              | Adds a stopclass to a stoplist.                                                                                  |
| ADD_STOP_SECTION           | Adds a stop section to an automatic section group.                                                               |
| ADD_STOPTHEME              | Adds a stoptheme to a stoplist.                                                                                  |
| ADD_STOPWORD               | Adds a stopword to a stoplist.                                                                                   |
| ADD_SUB_LEXER              | Adds a sub-lexer to a multi-lexer preference.                                                                    |
| ADD_ZONE_SECTION           | Creates a zone section and adds it to the specified section group.                                               |
| COPY_POLICY                | Creates a copy of a policy.                                                                                      |
| CREATE_INDEX_SET           | Creates an index set for `CTXCAT` index types.                                                                   |
| CREATE_POLICY              | Creates a policy to use with `ORA:CONTAINS()`.                                                                   |
| CREATE_PREFERENCE          | Creates a preference in the Text data dictionary.                                                                |
| CREATE_SECTION_GROUP       | Creates a section group in the Text data dictionary.                                                             |
| CREATE_SHADOW_INDEX        | Creates a policy for the passed-in index. For nonpartitioned index, also creates an index table.                 |
| CREATE_STOPLIST            | Creates a stoplist.                                                                                              |
| DROP_INDEX_SET             | Drops an index set.                                                                                              |
| DROP_POLICY                | Drops a policy.                                                                                                  |
| DROP_PREFERENCE            | Deletes a preference from the Text data dictionary.                                                              |
| DROP_SECTION_GROUP         | Deletes a section group from the Text data dictionary.                                                           |
| DROP_SHADOW_INDEX          | Drops a shadow index.                                                                                            |
| DROP_STOPLIST              | Drops a stoplist.                                                                                                |
| EXCHANGE_SHADOW_INDEX      | Swaps the shadow index metadata and data.                                                                        |
| OPTIMIZE_INDEX             | Optimizes the index.                                                                                             |
| POPULATE_PENDING           | Populates the pending queue with every rowid in the base table or table partition.                               |
| PREFERENCE_IMPLICIT_COMMIT | Specifies whether procedures related to CTX_DDL preferences issue an implicit commit.                            |
| RECREATE_INDEX_ONLINE      | Recreates the passed-in index.                                                                                   |
| REM_SEC_GRP_ATTR_VAL       | Removes a specific section group attribute value from the list of values of an existing section group attribute. |
| REMOVE_AUTO_OPTIMIZE       | Removes an index or partition from the list of indexes subject to auto optimization                              |
| REMOVE_INDEX               | Removes an index from a `CTXCAT` index preference.                                                               |
| REMOVE_MDATA               | Removes `MDATA` values from a document.                                                                          |
| REMOVE_SECTION             | Deletes a section from a section group.                                                                          |
| REMOVE_STOPCLASS           | Deletes a stopclass from a stoplist.                                                                             |
| REMOVE_STOPTHEME           | Deletes a stoptheme from a stoplist.                                                                             |
| REMOVE_STOPWORD            | Deletes a stopword from a stoplist.                                                                              |
| REMOVE_SUB_LEXER           | Deletes a sub-lexer from a multi-lexer preference.                                                               |
| REPLACE_INDEX_METADATA     | Replaces metadata for local domain indexes.                                                                      |
| SET_ATTRIBUTE              | Sets a preference attribute.                                                                                     |
| SET_SEC_GRP_ATTR           | Adds a section group-specific attribute to a section group identified by name.                                   |
| SET_SECTION_ATTRIBUTE      | Sets a section attribute.                                                                                        |
| SYNC_INDEX                 | Synchronizes the index.                                                                                          |
| UNSET_ATTRIBUTE            | Removes a set attribute from a preference.                                                                       |
| UPDATE_SUB_LEXER           | Updates a sub-lexer.                                                                                             |
| UNSET_SEC_GRP_ATTR         | Removes a section group specific attribute.                                                                      |
| UPDATE_POLICY              | Updates a policy.                                                                                                |
| UPDATE_SDATA               | Updates an SDATA section.                                                                                        |

**Note:**

Except `CREATE_PREFERENCE` and `CREATE_SECTION_GROUP`, the APIs in the `CTX_DDL` package do not support identifiers that are prefixed with the schema or owner name.

### 8.1 ADD_ATTR_SECTION

Adds an attribute section to an XML section group. This procedure is useful for defining attributes in XML documents as sections. This enables you to search XML attribute text with the `WITHIN` operator.

**Note:**

When you use `AUTO_SECTION_GROUP`, attribute sections are created automatically. Attribute sections created automatically are named in the form `tag@attribute`.

#### Syntax

    CTX_DDL.ADD_ATTR_SECTION(
      group_name     IN    VARCHAR2,
      section_name   IN    VARCHAR2,
      tag            IN    VARCHAR2);

group_name
Specify the name of the XML section group. You can add attribute sections only to XML section groups.

section_name
Specify the name of the attribute section. This is the name used for `WITHIN` queries on the attribute text.

The section name you specify cannot contain the colon (:), comma (,), or dot (.) characters. The section name must also be unique within `group_name`. Section names are case-insensitive.

Attribute section names can be no more than 64 bytes long.

tag
Specify the name of the attribute in `tag@attr` form. This parameter is case-sensitive.

#### Examples

Consider an XML file that defines the `BOOK` tag with a `TITLE` attribute as follows:

    <BOOK TITLE="Tale of Two Cities">
      It was the best of times.
    </BOOK>

To define the title attribute as an attribute section, create an `XML_SECTION_GROUP` and define the attribute section as follows:

    begin
    ctx_ddl.create_section_group('myxmlgroup', 'XML_SECTION_GROUP');
    ctx_ddl.add_attr_section('myxmlgroup', 'booktitle', 'BOOK@TITLE');
    end;

When you define the `TITLE` attribute section as such and index the document set, you can query the XML attribute text as follows:

    'Cities within booktitle'

#### Related Topic

"PREFERENCE_IMPLICIT_COMMIT"

### 8.2 ADD_AUTO_OPTIMIZE

Adds an index or partition to the list of indexes subject to auto optimization. For partitioned indexes, the name of the partition must be specified, or else an error occurs. For global indexes, `STAGE_ITAB` must be enabled, or else an error occurs.

The `AUTO_OPTIMIZE` feature improves the manageability of indexes that use the `STAGE_ITAB` feature. The `STAGE_ITAB` feature introduces a staging \$G table to collect postings from newly synced documents.

The `AUTO_OPTIMIZE` feature has the following goals:

- Enables you to register indexes and partitions to a background `AUTO_OPTIMIZE` process.

- Automatically moves rows from the \$G table to \$I at appropriate times.

- Movement of rows from \$G to \$I is done in a way to maximize query performance.

This procedure starts the background process if it has not already been started. The progress of the auto optimization is tracked by CTX logging.

The changes made by this procedure take effect immediately.

**Note:**

The init.ora parameter `JOB_QUEUE_PROCESSES` must be set to one or higher. See [Oracle Database Reference](../refrn/JOB_QUEUE_PROCESSES.md) for more information about `JOB_QUEUE_PROCESSES`.

#### Syntax

    CTX_DDL.ADD_AUTO_OPTIMIZE(

        idx_name       IN VARCHAR2,
        part_name      IN VARCHAR2 default NULL,
        optlevel       IN VARCHAR2 default CTX_DDL.OPTLEVEL_MERGE
    );

idx_name
Specify the name of the index to add.

part_name
Specify the name of the partition to add.

optlevel
Specifies the `optlevel` of the `CTX_DDL.OPTIMIZE_INDEX` procedure. The only valid value for this parameter is `merge`.

#### Notes

The recommended sequence of steps for using auto optimization is:

1.  Create the required indexes.

2.  Add these indexes to the auto optimization list by using the `CTX_DDL.ADD_AUTO_OPTIMIZE` procedure.

The synchronize index operation automatically begins executing an auto optimization job (unless it is already running). This job continues until it runs out of work. Future synchronize index operations will automatically start executing the auto optimization job, if it is not already running.

#### Related Topics

"REMOVE_AUTO_OPTIMIZE"

[Oracle Text Application Developer's Guide](../ccapp/tuning-oracle-text.md) for information about using `STAGE_ITAB` with CONTEXT indexes

SYNC_INDEX

### 8.3 ADD_FIELD_SECTION

Creates a field section and adds the section to an existing section group. This enables field section searching with the [WITHIN](oracle-text-CONTAINS-query-operators.md) operator. You can add an unlimited number of field sections.

Field sections are delimited by start and end tags. By default, the text within field sections are indexed as a sub-document separate from the rest of the document.

Unlike zone sections, field sections cannot nest or overlap. As such, field sections are best suited for non-repeating, non-overlapping sections such as `TITLE` and `AUTHOR` markup in e-mail- or news-type documents.

Because of how field sections are indexed, [WITHIN](oracle-text-CONTAINS-query-operators.md) queries on field sections are usually faster than `WITHIN` queries on zone sections.

#### Syntax

    CTX_DDL.ADD_FIELD_SECTION(
      group_name     IN    VARCHAR2,
      section_name   IN    VARCHAR2,
      tag            IN    VARCHAR2,
      visible        IN    BOOLEAN default FALSE
    );

group_name
Specify the name of the section group to which `section_name` is added. You can add an unlimited number of field sections to a single section group. Within the same group, section zone names and section field names cannot be the same.

section_name
Specify the name of the section to add to the `group_name`. Use this name to identify the section in queries. Avoid using names that contain non-alphanumeric characters such as \_, because these characters must be escaped in queries. Section names are case-insensitive.

**Note:**

The `section_name` may not be prefixed by the schema or the owner name as this syntax is not supported.

Within the same group, zone section names and field section names cannot be the same. The terms Paragraph and Sentence are reserved for special sections.

Section names need not be unique across tags. You can assign the same section name to more than one tag, which makes details transparent to searches.

tag
Specify the tag that marks the start of a section. For example, if the tag is \<H1\>, then specify H1. The start tag you specify must be unique within a section group.

**Note:**

The tag may not be prefixed by the schema or the owner name as this syntax is not supported.

If `group_name` is an `HTML_SECTION_GROUP`, then you can create field sections for the META tag's `NAME/CONTENT` attribute pairs. To do so, specify `tag` as `meta@namevalue` where `namevalue` is the value of the `NAME` attribute whose `CONTENT` attribute is to be indexed as a section. Refer to the example "Creating Sections for \<META\> Tags".

Oracle Text knows what the end tags look like from the `group_type` parameter you specify when you create the section group.

visible
Specify `TRUE` to make the text visible within the rest of the document.

By default the `visible` flag is `FALSE`. This means that Oracle Text indexes the text within field sections as a sub-document separate from the rest of the document. However, you can set the visible flag to `TRUE` if you want text within the field section to be indexed as part of the enclosing document.

#### Examples

Visible and Invisible Field Sections

The following example defines a section group `basicgroup` of the `BASIC_SECTION_GROUP` type. (See "[Section Group Types](oracle-text-indexing-elements.md)" for information about the `BASIC_SECTION_GROUP` type.) The example then creates a field section in `basicgroup` called `Author` for the `<A>` tag.

The example also sets the visible flag to `FALSE`:

    begin

    ctx_ddl.create_section_group('basicgroup', 'BASIC_SECTION_GROUP');
    ctx_ddl.add_field_section('basicgroup', 'Author', 'A', FALSE);

    end;

Because the `Author` field section is not visible, to find text within the `Author` section, you must use the [WITHIN](oracle-text-CONTAINS-query-operators.md) operator as follows:

    '(Martin Luther King) WITHIN Author'

A query of Martin Luther King without the `WITHIN` operator does not return instances of this term in field sections. To query text within field sections without specifying `WITHIN`, you must set the visible flag to `TRUE` when you create the section as follows:

    begin
    ctx_ddl.add_field_section('basicgroup', 'Author', 'A', TRUE);
    end;

Creating Sections for `<META>` Tags

When you use the `HTML_SECTION_GROUP`, you can create sections for `META` tags.

Consider an HTML document that has a `META` tag as follows:

    <META NAME="author" CONTENT="ken">

To create a field section that indexes the `CONTENT` attribute for the `<META NAME="author">` tag:

    begin
    ctx_ddl.create_section_group('myhtmlgroup', 'HTML_SECTION_GROUP');
    ctx_ddl.add_field_section('myhtmlgroup', 'author', 'META@AUTHOR');
    end

After indexing with section group `mygroup`, query the document as follows:

    'ken WITHIN author'

#### Limitations

Nested Sections

Field sections cannot be nested. For example, if you define a field section to start with `<TITLE>` and define another field section to start with `<FOO>`, the two sections cannot be nested as follows:

    <TITLE> dog <FOO> cat </FOO> </TITLE>

To work with nested section define them as zone sections.

Repeated Sections

Repeated field sections are allowed, but `WITHIN` queries treat them as a single section. The following is an example of repeated field section in a document:

    <TITLE> cat </TITLE>
    <TITLE> dog </TITLE>

The query (dog and cat) within title returns the document, even though these words occur in different sections.

To have `WITHIN` queries distinguish repeated sections, define them as zone sections.

#### Related Topics

"[WITHIN](oracle-text-CONTAINS-query-operators.md)"

"[Section Group Types](oracle-text-indexing-elements.md)"

"CREATE_SECTION_GROUP "

"ADD_ZONE_SECTION "

"ADD_SPECIAL_SECTION "

"REMOVE_SECTION "

"DROP_SECTION_GROUP "

### 8.4 ADD_INDEX

Use this procedure to add a subindex to a catalog index preference. Create this preference by naming one or more columns in the base table.

Because you create subindexes to improve the response time of structured queries, the column you add should be used in the `structured_query` clause of the `CATSEARCH` operator at query time.

#### Syntax

    CTX_DDL.ADD_INDEX(
               set_name        IN VARCHAR2,
               column_list     IN VARCHAR2,
               storage_clause  IN VARCHAR2
    );

set_name
Specify the name of the index set.

column_list
Specify a comma-delimited list of columns to index. At index time, any column listed here cannot have a NULL value in any row in the base table. If any row is NULL during indexing, then an error is raised.

Always ensure that your columns have non-NULL values before and after indexing.

**Note:**

A column name in `column_list` must not be prefixed by the owner, schema or table name.

storage_clause
Specify a storage clause.

#### Example

Consider a table called `AUCTION` with the following schema:

    create table auction(

    item_id number,
    title varchar2(100),
    category_id number,
    price number,
    bid_close date);

Assume that queries on the table involve a mandatory text query clause and optional structured conditions on `category_id`. Results must be sorted based on `bid_close`.

You can create a catalog index to support the different types of structured queries a user might enter.

To create the indexes, first create the index set preference then add the required indexes to it:

    begin
      ctx_ddl.create_index_set('auction_iset');
      ctx_ddl.add_index('auction_iset','bid_close');
      ctx_ddl.add_index('auction_iset','category_id, bid_close');
    end;

Create the combined catalog index with `CREATE` `INDEX` as follows:

    create index auction_titlex on AUCTION(title) indextype is CTXCAT parameters
    ('index set auction_iset');

#### Querying

To query the title column for the word pokemon, enter regular and mixed queries as follows:

    select * from AUCTION where CATSEARCH(title, 'pokemon',NULL)> 0;
    select * from AUCTION where CATSEARCH(title, 'pokemon', 'category_id=99 order by
    bid_close desc')> 0;

#### Notes

`VARCHAR2` columns in the column list of a `CTXCAT` index of an index set cannot exceed 30 bytes.

#### Related Topic

"REMOVE_INDEX"

### 8.5 ADD_MDATA

Use this procedure to change the metadata of a document that has been specified as an `MDATA` section.

After this call, `MDATA` queries involving the named `MDATA` value will find documents with the given `MDATA` value.

There are two versions of `CTX_DDL.ADD_MDATA`: one for adding a single metadata value to a single rowid, and one for handing multiple values, multiple rowids, or both.

`CTX_DDL.ADD_MDATA` is transactional; it takes effect immediately in the calling session, can be seen only in the calling session, can be reversed with a `ROLLBACK` command, and must be committed to take permanent effect.

Use CTX_DDL.REMOVE_MDATA to remove metadata values from already-indexed documents. Only the owner of the index is allowed to call `ADD_MDATA` and `REMOVE_MDATA`.

#### Syntax

This is the syntax for adding a single value to a single rowid:

    CTX_DDL.ADD_MDATA(
         idx_name           IN VARCHAR2,
         section_name       IN VARCHAR2,
         mdata_value        IN VARCHAR2,
         mdata_rowid        IN VARCHAR2,
         [part_name]        IN VARCHAR2]
    );

idx_name
Name of the text index that contains the named rowid.

section_name
Name of the `MDATA` section.

mdata_value
The metadata value to add to the document.

mdata_rowid
The rowid to which to add the metadata value.

\[part_name\]
Name of the index partition, if any. Must be provided for local partitioned indexes and must be NULL for global, nonpartitioned indexes.

This is the syntax for handling multiple values, multiple rowids, or both. This version is more efficient for large numbers of new values or rowids.

    CTX_DDL.ADD_MDATA(
         idx_name           IN VARCHAR2,
         section_name       IN VARCHAR2,
         mdata_values       SYS.ODCIVARCHAR2LIST,
         mdata_rowids       SYS.ODCIRIDLIST,
         [part_name]        IN VARCHAR2]
    );

idx_name
Name of the text index that contains the named rowids.

section_name
Name of the `MDATA` section.

mdata_values
List of metadata values. If a metadata value contains a comma, the comma must be escaped with a backslash.

mdata_rowids
The rowids to which to add the metadata values.

\[part_name\]
Name of the index partition, if any. Must be provided for local partitioned indexes and must be NULL for global, nonpartitioned indexes.

#### Example

This example updates a single value:

    select rowid from mytab where contains(text, 'MDATA(sec, value')>0;
    No rows returned
    exec ctx_ddl.add_mdata('my_index', 'sec', 'value', 'ABC');
    select rowid from mytab where contains(text, 'MDATA(sec, value')>0;
    ROWID
    -----
    ABC

This example updates multiple values:

    begin
    ctx_ddl.add_mdata('my_index', 'sec',
         sys.odcivarchar2list('value1','value2','value3'),
         sys.odciridlist('ABC','DEF'));
    end;

This is equivalent to:

    begin
    ctx_ddl.add_mdata('my_index', 'sec', 'value1', 'ABC');
    ctx_ddl.add_mdata('my_index', 'sec', 'value1', 'DEF');
    ctx_ddl.add_mdata('my_index', 'sec', 'value2', 'ABC');
    ctx_ddl.add_mdata('my_index', 'sec', 'value2', 'DEF');
    ctx_ddl.add_mdata('my_index', 'sec', 'value3', 'ABC');
    ctx_ddl.add_mdata('my_index', 'sec', 'value3', 'DEF');
    end;

#### Notes

If a rowid is not yet indexed, `CTX_DDL.ADD.MDATA` completes without error, but an error is logged in `CTX_USER_INDEX_ERRORS`.

These updates are updates directly on the index itself, not on the actual contents stored in the base table. Therefore, they will not exist when the Text index is rebuilt.

#### Related Topics

"ADD_MDATA_SECTION"

"REMOVE_MDATA"

"[MDATA](oracle-text-CONTAINS-query-operators.md)"

**See Also:**

Chapter 8, "Searching Document Sections in Oracle Text" in [Oracle Text Application Developer's Guide](../ccapp/searching-document-sections-in-oracle-text.md)

### 8.6 ADD_MDATA_COLUMN

Use this procedure to map the `FILTER` `BY` column named in column_name to the `MDATA` section named in section_name.

#### Syntax

The syntax is as follows:

    CTX_DDL.ADD_MDATA_COLUMN(
         group_name         IN VARCHAR2,
         section_name       IN VARCHAR2,
         column_name        IN VARCHAR2,
    );

group_name
Name of the group that contains the section.

section_name
Name of the `MDATA` section.

column_name
Name of the `FILTER` `BY` column to add to the `MDATA` section.

**Note:**

The `column_name` must not be prefixed by the owner, schema or table name.

#### Restrictions

`MDATA` sections that are created with `CTX_DDL.ADD_MDATA_COLUMN` cannot have their values changed using `CTX_DDL.ADD_MDATA` or `CTX_DDL.REMOVE_MDATA`. Doing so will result in errors being returned. The section values must be updated using SQL.

#### Notes

- The stored datatype for `MDATA` sections is `text`. Therefore, the value of the `FILTER` `BY` column is converted to `text` during indexing. For non-text datatypes, the `FILTER` `BY` columns are normalized to an internal format during indexing. If the section is queried with an `MDATA` operator, then the `MDATA` query string will also be normalized to the internal format before processing.

- When a `FILTER` `BY` column is mapped as `MDATA`, the cost-based optimizer in Oracle Text tries to avoid using the Oracle Text composite domain index to process range predicate(s) on that `FILTER` `BY` column. This is because range predicates on `MDATA` `FILTER` `BY` columns are processed less efficiently than if they were declared as `SDATA`. For this reason, you should not add a `FILTER` `BY` column as `MDATA` if you plan to do range searches on the column.

#### Related Topics

"[MDATA](oracle-text-CONTAINS-query-operators.md)"

"ADD_MDATA_SECTION"

"REMOVE_MDATA"

"ADD_SDATA_COLUMN"

**See Also:**

Chapter 8, "Searching Document Sections in Oracle Text" in [Oracle Text Application Developer's Guide](../ccapp/searching-document-sections-in-oracle-text.md)

### 8.7 ADD_MDATA_SECTION

Use this procedure to add an `MDATA` section, with an accompanying value, to an existing section group. `MDATA` sections cannot be added to Null Section groups, Path Section groups, or Auto Section groups.

Section values undergo a simplified normalization:

- Leading and trailing whitespace on the value is removed.

- The value is truncated to 255 bytes.

- The value is indexed as a single value; if the value consists of multiple words, it is not broken up.

- Case is preserved. If the document is dynamically generated, then implement case-insensitivity by uppercasing `MDATA` values and making sure to search only in uppercase.

Use CTX_DDL.REMOVE_SECTION to remove sections.

#### Syntax

    CTX_DDL.ADD_MDATA_SECTION(
         group_name    IN VARCHAR2,
         section_name  IN VARCHAR2,
         tag           IN VARCHAR2,
         read_only     IN BOOLEAN default FALSE);

group_name
Name of the section group that will contain the `MDATA` section.

section_name
Name of the `MDATA` section.

tag
The value of the `MDATA` section. For example, if the section is `<AUTHOR>`, the value could be Cynthia Kadohata (author of the novel The Floating World). More than one tag can be assigned to a given `MDATA` section.

read_only
`FALSE` (default) if you want to allow calling `CTX_DDL.ADD_MDATA()` and `CTX_DDL.REMOVE_MDATA()` for this MDATA section, and `TRUE` otherwise. When set to `FALSE`, the queries on the `MDATA` section run less efficiently because a cursor needs to be opened on the index table to track the deleted values for that `MDATA` section.

#### Example

This example creates an `MDATA` section called `auth`.

    ctx_ddl.create_section_group('htmgroup', 'HTML_SECTION_GROUP');
    ctx_ddl.add_mdata_section('htmgroup', 'auth', 'author', READ_ONLY);

#### Related Topics

"ADD_MDATA"

"REMOVE_MDATA"

"[MDATA](oracle-text-CONTAINS-query-operators.md)"

"CREATE_SECTION_GROUP "

**See Also:**

Chapter 8, "Searching Document Sections in Oracle Text" in [Oracle Text Application Developer's Guide](../ccapp/searching-document-sections-in-oracle-text.md)

### 8.8 ADD_NDATA_SECTION

Use this procedure to find matches that are spelled in a similar way. The value of an `NDATA` section is extracted from the document text like other sections, but is indexed as name data. `NDATA` sections are stored in the `CTX_USER_SECTIONS` view.

#### Syntax

    CTX_DDL.ADD_NDATA_SECTION(
       group_name    IN VARCHAR2,
       section_name  IN VARCHAR2,
       tag           IN VARCHAR2
    );

group_name
Name of the group that contains the section.

section_name
Name of the `NDATA` section.

tag
Name of the tag that marks the start of a section. For example, if the tag is \<H1\>, specify H1. The start tag you specify must be unique within a section group.

#### Notes

`NDATA` sections support both single and multi-byte data, however, there are character- and term-based limitations. `NDATA` section data that is indexed is constrained as follows:

- number of characters in a single, white space delimited term

  511

- number of white space delimited terms

  255

- total number of characters, including white spaces

  511

`NDATA` section data that exceeds these constraints are truncated.

#### Example

The following example defines a section group `namegroup` of the `BASIC_SECTION_GROUP` type. It then creates an `NDATA` section in `namegroup` called `firstname`.

    begin
      ctx_ddl.create_section_group('namegroup', 'BASIC_SECTION_GROUP');
      ctx_ddl.add_ndata_section('namegroup', 'firstname', 'fname1');
    end;

### 8.9 ADD_SDATA_COLUMN

Use this procedure to map the `FILTER BY` or `ORDER BY` column (named in column_name) to the `SDATA` section (named in section_name). By default, all `FILTER BY` columns are mapped as `SDATA`.

#### Syntax

The syntax is as follows:

    CTX_DDL.ADD_SDATA_COLUMN(
         group_name         IN VARCHAR2,
         section_name       IN VARCHAR2,
         column_name        IN VARCHAR2,
    );

group_name
Name of the group that contains the section.

section_name
Name of the `SDATA` section.

column_name
Name of the `FILTER` `BY` column to add to the `SDATA` section.

#### Notes

- Mapping `FILTER` `BY` columns to sections is optional. If no section mapping exists for a `FILTER` `BY` column, then it is mapped to an `SDATA` section, and the section name will be the name of the `FILTER` `BY` column.

- If a section group is not specified during `CREATE` `INDEX` of a composite domain index, then system default section group settings is used, and a `SDATA` section is created for each of the `FILTER` `BY` and `ORDER` `BY` columns.

  **Note:**

  Because section name does not allow certain special characters and is case insensitive, if the column name is case sensitive or contains special characters, then an error is raised. To work around this problem, you need to map the column to an `MDATA` or `SDATA` section before creating the index.

- An error will be raised if a column mapped to `MDATA` also appears in the `ORDER` `BY` column clause.

- Column section names are unique to their section group. That is, you cannot have an `MDATA` column section named `FOO` if you already have an `MDATA` column section named `FOO`. Furthermore, you cannot have a field section named `FOO` if you already have an `SDATA` column section named `FOO`. This is true whether it is implicitly created (by `CREATE` `INDEX` for `FILTER` `BY` or `ORDER` `BY` clauses) or explicitly created (by` CTX_DDL.ADD_SDATA_COLUMN`).

- One section name can only be mapped to one `FILTER` `BY` column, and vice versa. For example, mapping a section to more than one column or mapping a column to more than one section is not allowed.

- Column sections can be added to any type of section group, including the `NULL` section group.

- 99 is the maximum number for `SDATA` sections and columns.

- If the datatype of a `FILTER BY` or `ORDER BY` column is `DATE`, then the `DATE` datatype values must conform to the `YYYY-MM-DD` or `YYYY-MM-DD HH24:MI:SS` format. For example, to store a `DATE` value of "Nov. 24, 2006 10:32 PM 36 sec", the document appears as `<TAG>2006-11-24 22:32:36</TAG>`.

**Related Topics**

- [SDATA](oracle-text-CONTAINS-query-operators.md)
- ADD_SDATA_SECTION
- UPDATE_SDATA
- ADD_MDATA_COLUMN
- [Oracle Text Application Developer's Guide](../ccapp/searching-document-sections-in-oracle-text.md)

### 8.10 ADD_SDATA_SECTION

This procedure adds an `SDATA` section to a section group. By default, all `FILTER` `BY` columns are mapped as `SDATA`.

Starting with Oracle Database 12c Release 2 (12.2), searchable multi-valued `SDATA` sections are supported. There is no restriction on the number of SDATA sections that can be created for an index. That is, the sum total of `SDATA` sections for an index, created implicitly with `FILTER` `BY` and `ORDER` `BY`, and explicitly with the `CTX_DDL.ADD_SDATA_SECTION()` procedure is not restricted anymore. The total number of CDI, including `FILTER BY` and `ORDER BY` is 32, but the number of `SDATA` sections supported is unlimited. There are two types of `SDATA` sections:

- Searchable: Creates optimized for search SDATA sections which support multiple values per document for the section and efficient range search capability.

- Sortable: Creates optimized for sort SDATA sections which support a single value per document for the section. If the `optimized_for` attribute is not set, then the default type of section is Sortable. The Composite Domain Index uses Sortable SDATA internally for efficient `FILTER BY` or `ORDER BY` evaluation.

Starting with Oracle Database Release 18c, group counts or facets are supported for SDATA sections that are created with the `optimized_for` attribute set to `sort`, `search`, or `sort_and_search`. The `optimized_for` attribute can be set by using the `CTX_DDL.SET_SECTION_ATTRIBUTE` procedure.

**See Also:**

- "SET_SECTION_ATTRIBUTE"

- [Oracle Text Application Developer's Guide](../ccapp/using-faceted-navigation.md) for more information about defining sections as facets

#### Syntax

The syntax is as follows:

    CTX_DDL.ADD_SDATA_SECTION(
         group_name         IN VARCHAR2,
         section_name       IN VARCHAR2,
         tag                IN VARCHAR2,
         datatype           IN VARCHAR2 default NULL,
    );

group_name
Name of the group that contains the section.

section_name
Name of the `SDATA` section.

tag
Name of the tag to add to the `SDATA` section.

datatype
Specifies the stored format for the data, as well as the semantics of comparison in later use in `SDATA` operators. The Sortable `SDATA` sections support the following data types:

- `VARCHAR2`

- `CHAR`

- `RAW`

- `NUMBER`

- `DATE`

The `VARCHAR2` datatype stores up to 249 bytes of character data in the database character set. Values larger than this result in a per-document indexing error. Note that leading and trailing whitespace are always trimmed from `SDATA` section values when extracted by the sectioner. This is different than `SDATA` columns. Column values are never trimmed. No lexing is performed on the value from either kind of `SDATA`.

The `CHAR` datatype stores up to 249 bytes of character data in the database character set. Values larger than this result in a per-document indexing error. Note that leading and trailing whitespace are always trimmed from `SDATA` section values when extracted by the sectioner. This is different than `SDATA` columns. Column values are never trimmed. No lexing is performed on the value from either kind of `SDATA`. To be consistent with SQL, the comparisons of `CHAR` datatype `SDATA` values are blank-padded comparisons.

The `RAW` datatype stores up to 249 bytes of binary data. Values larger than this result in a per-document indexing error. The value is converted from hexadecimal string representation. That is, to store a value of `65`, the document appears as `<TAG>40</TAG>`, and not `<TAG>65</TAG>` or `<TAG>A</TAG>`.

The `DATE` datatype values must conform to the following format: `YYYY-MM-DD` or `YYYY-MM-DD HH24:MI:SS`. That is, to store a `DATE` value of "Nov. 24, 2006 10:32 pm 36 sec", the document appears as `<TAG>2006-11-24 22:32:36</TAG>`.

The Searchable `SDATA` sections support the following data types:

- `VARCHAR2`

- `RAW`

- `NUMBER`

- `DATE`

- `BINARY_FLOAT`

- `BINARY_DOUBLE`

- `TIMESTAMP`

- `TIMESTAMP_WITH_TIMEZONE`

**Note:**

The Searchable `SDATA` sections do not support `CHAR` datatype.

The `BINARY_FLOAT` datatype stores 32-bit floating point number.

The `BINARY_DOUBLE` datatype stores 64-bit floating point number.

The `TIMESTAMP` datatype is an extension of the `DATE` datatype. It stores year, month, and day values of date, as well as hour, minute, and second values of time. It also stores fractional seconds, which are not stored by the `DATE` datatype. The fractional seconds precision cannot be more than 9. The `TIMESTAMP` values must follow the ISO format. You can specify the `TIMESTAMP` literal in the `YYYY-MM-DD``T``HH:MI:SS` format. An example of the `TIMESTAMP` value is:

`<TAG>1997-11-05T19:20:00</TAG>`

The `TIMESTAMP_WITH_TIMEZONE` datatype is a variant of `TIMESTAMP` datatype that includes a time zone offset or a time zone region name in its value. The fractional seconds precision cannot be more than 9. The `TIMESTAMP_WITH_TIMEZONE` values must follow the ISO format. An example of the `TIMESTAMP_WITH_TIMEZONE` value is:

`<TAG>1997-12-31T19:20:00-05:00</TAG>`

#### Example

The following example demonstrates how to create a SDATA section:

    create table tab(id number, info varchar2(100));

    insert into tab values(1,'Hello World<fruit>apple</fruit><price>3</price>');
    insert into tab values(2,'Hello World<fruit>orange</fruit><price>5</price>');

The preceding statements create a table named tab with two rows of data.

The following statements create a basic section group named `sg`, add SDATA sections to it and mark the SDATA to be searchable:

    exec ctx_ddl.create_section_group('sg', 'basic_section_group');
    exec ctx_ddl.add_sdata_section('sg','fruit','fruit','varchar2');
    exec ctx_ddl.set_section_attribute('sg','fruit','optimized_for','search');
    exec ctx_ddl.add_sdata_section('sg','price','price','number');
    exec ctx_ddl.set_section_attribute('sg','price','optimized_for','search');

The following statement creates an index on `sg`:

    create index idx on tab(info) indextype is ctxsys.context parameters ('section group sg');

The following statements query `tab` to demonstrate searchable SDATA:

Query 1

    select id from tab where CONTAINS(info, 'SDATA(fruit = "apple")'); return id 1

Query 2

    select id from tab where CONTAINS(info, 'Hello and SDATA(price > 4)'); return id 2

#### Limitations

- If no `SDATA` tag occurs in a given document, then this is treated as an `SDATA` value of `NULL`.

- Empty `SDATA` tags are treated as `NULL` values.

- `SDATA` sections cannot be nested. Sections that are nested inside are ignored.

- `SDATA` sections do not support `skipjoins` and `printjoins` characters.

#### Related Topics

"[SDATA](oracle-text-CONTAINS-query-operators.md)"

"ADD_SDATA_COLUMN"

"UPDATE_SDATA"

**See Also:**

- [Oracle Database SQL Language Reference](../sqlrf/index.md)

<!-- -->

- [Oracle Text Application Developer's Guide](../ccapp/searching-document-sections-in-oracle-text.md)

### 8.11 ADD_SEC_GRP_ATTR_VAL

Adds a section group attribute value to the list of values of an already existing section group attribute.

#### Syntax

    CTX_DDL.ADD_SEC_GRP_ATTR_VAL(
                          group_name      IN VARCHAR2,
                          attribute_name  IN VARCHAR2,
                          attribute_value IN VARCHAR2
    );

group_name
Specify the section group name.

attribute_name
Specify the name of the section group attribute.

attribute_value
Specify the section group attribute value.

### 8.12 ADD_SPECIAL_SECTION

Adds a special section, either `SENTENCE` or `PARAGRAPH`, to a section group. This enables searching within sentences or paragraphs in documents with the [WITHIN](oracle-text-CONTAINS-query-operators.md) operator.

A special section in a document is a section which is not explicitly tagged like zone and field sections. The start and end of special sections are detected when the index is created. Oracle Text supports two such sections: paragraph and sentence.

The sentence and paragraph boundaries are determined by the lexer. For example, the lexer recognizes sentence and paragraph section boundaries as follows:

Table 8-1 Paragraph and Sentence Section Boundaries

| Special Section | Boundary                                           |
|:----------------|:---------------------------------------------------|
| SENTENCE        | WORD/PUNCT/WHITESPACE                              |
| SENTENCE        | WORD/PUNCT/NEWLINE                                 |
| PARAGRAPH       | WORD/PUNCT/NEWLINE/WHITESPACE (indented paragraph) |
| PARAGRAPH       | WORD/PUNCT/NEWLINE/NEWLINE (block paragraph)       |

The punctuation, whitespace, and newline characters are determined by your lexer settings and can be changed.

If the lexer cannot recognize the boundaries, no sentence or paragraph sections are indexed.

#### Syntax

    CTX_DDL.ADD_SPECIAL_SECTION(
                     group_name    IN VARCHAR2,
                     section_name  IN VARCHAR2
    );

group_name
Specify the name of the section group.

section_name
Specify `SENTENCE` or `PARAGRAPH`.

#### Example

The following example enables searching within sentences within HTML documents:

    begin
    ctx_ddl.create_section_group('htmgroup', 'HTML_SECTION_GROUP');
    ctx_ddl.add_special_section('htmgroup', 'SENTENCE');
    end;

Add zone sections to the group to enable zone searching in addition to sentence searching. The following example adds the zone section `Headline` to the section group `htmgroup`:

    begin
    ctx_ddl.create_section_group('htmgroup', 'HTML_SECTION_GROUP');
    ctx_ddl.add_special_section('htmgroup', 'SENTENCE');
    ctx_ddl.add_zone_section('htmgroup', 'Headline', 'H1');
    end;

If you are only interested in sentence or paragraph searching within documents and not interested in defining zone or field sections, then use the `NULL_SECTION_GROUP` as follows:

    begin
    ctx_ddl.create_section_group('nullgroup', 'NULL_SECTION_GROUP');
    ctx_ddl.add_special_section('nullgroup', 'SENTENCE');
    end;

#### Related Topics

"[WITHIN](oracle-text-CONTAINS-query-operators.md)"

"[Section Group Types](oracle-text-indexing-elements.md)"

"CREATE_SECTION_GROUP "

"ADD_ZONE_SECTION "

"ADD_FIELD_SECTION"

"REMOVE_SECTION "

"DROP_SECTION_GROUP "

### 8.13 ADD_STOPCLASS

Adds a stopclass to a stoplist. A stopclass is a class of tokens that is not to be indexed. A stoplist cannot have more than 250 stopclasses with stoppatterns. This does not include the `NUMBERS` stopclass. When indexing with Stop Patterns, the recommended memory setting is at least 500 MB to 1 GB to optimize the performance of indexing.

English is the only language supported for stopclasses.

#### Syntax

    CTX_DDL.ADD_STOPCLASS(
      stoplist_name         IN   VARCHAR2,
      stopclass             IN   VARCHAR2,
      stoppattern           IN   VARCHAR2 default NULL
    );

stoplist_name
Specify the name of the stoplist.

stopclass
Specify the stopclass to be added to `stoplist_name`. It can be either the `NUMBERS` stopclass or else it is considered as the pattern stopclass.

`NUMBERS` includes tokens that follow the number pattern: digits, `numgroup`, and `numjoin` only. Therefore, 123ABC is not a number, nor is A123. These are labeled as `MIXED`. \$123 is not a number (this token is not common in a text index because non-alphanumerics become whitespace by default). In the United States, 123.45 is a number, but 123.456.789 is not; in Europe, where numgroup may be '.', the reverse is true.

If NUMBERS is not specified for the stopclass `parameter`, then it is treated as a pattern stopclass, and you can provide any name to the stopclass `parameter`. If you specify stopclass as a pattern class, then you need to specify the pattern in the `stoppattern` parameter. The pattern includes any string pattern that may contain numbers and dates as well.

The maximum number of stopwords, stopthemes, and stopclasses you can add to a stoplist is 4095.

stoppattern
Specify the stop pattern to add to the stoplist. If the stopclass is specified as a pattern class, then the stop pattern must be specified. You can use the Oracle Regular Expression to specify the stop pattern.

Call the `ADD_STOPCLASS` procedure multiple times to add multiple stop patterns to a stoplist. You must specify different stopclass names for adding multiple stop patterns to a stoplist.

A stop pattern is not case-sensitive by default, but acts as case-sensitive when the `MIXED_CASE` lexer preference is enabled. The stop pattern can have the maximum length of 512 characters. When indexing with Stop Patterns, the recommended memory setting is at least 500 MB to 1 GB to optimize the performance of indexing.

**See Also:**

[Oracle Database Development Guide](../adfns/regexp.md) for more information about the syntax of the Oracle Regular Expression.

#### Example

The following example adds a stopclass of `NUMBERS` to the stoplist `mystoplist`:

    begin
    ctx_ddl.add_stopclass('mystoplist', 'NUMBERS');
    end;

The following example adds the pattern stopclass of `SSN` to the stoplist `mystoplist`:

    begin
    ctx_ddl.add_stopclass('mystoplist', 'SSN', '\d{3}-\d{2}-\d{4}');
    end;

In this example, the stopclass `SSN` matches all the tokens of the form \<3 digit number\>-\<2 digit number\>-\<4 digit number\>, example, `234-11-8902`.

#### Related Topics

"CREATE_STOPLIST "

"REMOVE_STOPCLASS "

"DROP_STOPLIST "

### 8.14 ADD_STOP_SECTION

Adds a stop section to an automatic section group. Adding a stop section causes the automatic section indexing operation to ignore the specified section in XML documents.

**Note:**

Adding a stop section causes no section information to be created in the index. However, the text within a stop section is always searchable.

Adding a stop section is useful when your documents contain many low information tags. Adding stop sections also improves indexing performance with the automatic section group.

The number of stop sections you can add is unlimited.

Stop sections do not have section names and hence are not recorded in the section views.

#### Syntax

    CTX_DDL.ADD_STOP_SECTION(
                     section_group IN VARCHAR2,
                     tag           IN VARCHAR2
    );

section_group
Specify the name of the automatic section group. If you do not specify an automatic section group, then this procedure returns an error.

tag
Specify the tag to ignore during indexing. This parameter is case-sensitive. Defining a stop tag as such also stops the tag's attribute sections, if any.

Qualify the tag with document type in the form `(doctype)tag`. For example, if you wanted to make the `<fluff>` tag a stop section only within the `mydoc` document type, specify `(mydoc)fluff` for tag.

#### Example

Defining Stop Sections

The following example adds a stop section identified by the tag \<`fluff>` to the automatic section group `myauto`:

    begin
    ctx_ddl.add_stop_section('myauto', 'fluff');
    end;

This example also stops any attribute sections contained within `<fluff>`. For example, if a document contained:

    <fluff type="computer">

Then the preceding example also stops the attribute section` ``fluff@type.`

Doctype Sensitive Stop Sections

The following example creates a stop section for the tag \<`fluff>` only in documents that have a root element of `mydoc`:

    begin
    ctx_ddl.add_stop_section('myauto', '(mydoc)fluff');
    end;

#### Related Topics

"[ALTER INDEX](oracle-text-SQL-statements-and-operators.md) "

"CREATE_SECTION_GROUP "

### 8.15 ADD_STOPTHEME

Adds a single stoptheme to a stoplist. A stoptheme is a theme that is not to be indexed.

In English, query on indexed themes using the [ABOUT](oracle-text-CONTAINS-query-operators.md) operator.

#### Syntax

    CTX_DDL.ADD_STOPTHEME(
      stoplist_name     IN   VARCHAR2,
      stoptheme         IN   VARCHAR2
    );

stoplist_name
Specify the name of the stoplist.

stoptheme
Specify the stoptheme to be added to `stoplist_name`. The system normalizes the `stoptheme` you enter using the knowledge base. If the normalized theme is more than one theme, then the system does not process your stoptheme. For this reason, Oracle recommends that you submit single stopthemes.

The maximum number of stopwords, stopthemes, and stopclasses you can add to a stoplist is 4095.

#### Example

The following example adds the stoptheme `banking`to the stoplist `mystop`:

    begin
    ctx_ddl.add_stoptheme('mystop', 'banking');
    end;

#### Related Topics

"CREATE_STOPLIST "

"REMOVE_STOPTHEME "

"DROP_STOPLIST "

"[ABOUT](oracle-text-CONTAINS-query-operators.md)"

### 8.16 ADD_STOPWORD

Use this procedure to add a single stopword to a stoplist.

To create a list of stopwords, you must call this procedure once for each word.

#### Syntax

    CTX_DDL.ADD_STOPWORD(

            stoplist_name       IN VARCHAR2,
            stopword            IN VARCHAR2,
            language            IN VARCHAR2 default NULL,
            language_dependent  IN BOOLEAN default TRUE

    );

stoplist_name
Specify the name of the stoplist.

stopword
Specify the stopword to be added.

Language-specific stopwords must be unique across the other stopwords specific to the language. For example, it is valid to have a German die and an English die in the same stoplist.

The maximum number of stopwords, stopthemes, and stopclasses you can add to a stoplist is 4095.

language
Specify the language of `stopword` when the stoplist you specify with `stoplist_name` is of type `MULTI_STOPLIST`. You must specify the globalization support name or abbreviation of an Oracle Text-supported language.

To make a stopword active in multiple languages, specify `ALL` for this parameter. For example, defining `ALL` stopwords is useful when you have international documents that contain English fragments that need to be stopped in any language.

An `ALL` stopword is active in all languages. If you use the multi-lexer, the language-specific lexing of the stopword occurs, just as if it had been added multiple times in multiple specific languages.

Otherwise, specify `NULL`.

language_dependent
Set this parameter to `FALSE` to indicate that any user-defined string can be specified for the `language` parameter.

#### Example

Single Language Stoplist

The following example adds the stopwords because, notwithstanding, nonetheless, and therefore to the stoplist `mystop`:

    begin

    ctx_ddl.add_stopword('mystop', 'because');
    ctx_ddl.add_stopword('mystop', 'notwithstanding');
    ctx_ddl.add_stopword('mystop', 'nonetheless');
    ctx_ddl.add_stopword('mystop', 'therefore');

    end;

Multi-Language Stoplist

The following example adds the German word die to a multi-language stoplist:

    begin

    ctx_ddl.add_stopword('mystop', 'Die','german');

    end;

Adding An ALL Stopword

The following adds the word the as an `ALL` stopword to the multi-language stoplist globallist:

    begin

    ctx_ddl.add_stopword('globallist','the','ALL');

    end;

#### Notes

- Add stopwords after you create the index with `ALTER INDEX`.

- Stoplists do not affect string-value `SDATA` sections, that is, if a stopword is present within an `SDATA` section, then the token will still be indexed and can be queried using the `SDATA` operator.

**Related Topics**

- CREATE_STOPLIST
- REMOVE_STOPWORD
- DROP_STOPLIST
- [ALTER INDEX](oracle-text-SQL-statements-and-operators.md)
- [Oracle Text Supplied Stoplists](oracle-text-supplied-stoplists.md)

### 8.17 ADD_SUB_LEXER

Adds a sub-lexer to a multi-lexer preference. A sub-lexer identifies a language in a multi-lexer (multi-language) preference. Use a multi-lexer preference when you want to index more than one language.

#### Syntax

    CTX_DDL.ADD_SUB_LEXER(
                 lexer_name          IN VARCHAR2,
                 language            IN VARCHAR2,
                 sub_lexer           IN VARCHAR2,
                 alt_value           IN VARCHAR2 default NULL,
                 language_dependent  IN BOOLEAN default TRUE
    );

lexer_name
Specify the name of the multi-lexer preference.

language
Specify the globalization support language name or abbreviation of the sub-lexer. For example, specify `JAPANESE` or `JA` for Japanese.

The sub-lexer you specify with `sub_lexer` is used when the language column has a value case-insensitive equal to the globalization support name of abbreviation of `language`.

Specify `DEFAULT` to assign a default sub-lexer to use when the value of the language column in the base table is null, invalid, or unmapped to a sub-lexer. The `DEFAULT` lexer is also used to parse stopwords.

If a sub-lexer definition for `language` already exists, then it is replaced by this call.

sub_lexer
Specify the name of the sub-lexer to use for this language.

alt_value
Optionally specify an alternate value for `language`.

If you specify `DEFAULT` for `language`, then you cannot specify an `alt_value`.

The `alt_value` is limited to 30 bytes and cannot be a globalization support language name, abbreviation, or `DEFAULT`.

language_dependent
Set this parameter to `FALSE` to indicate that any user-defined string can be specified for the `language` parameter. If set to `FALSE`, then the lexing applied to the search expression will not be dependent on the query language. The `FALSE` option can only be used when a `BASIC_SECTION_GROUP` is in use for the index.

#### Example

This example shows how to create a multi-language text table and how to set up the multi-lexer to index the table.

Create the multi-language table with a primary key, a text column, and a language column as follows:

    create table globaldoc (
       doc_id number primary key,
       lang varchar2(3),
       text clob
    );

Assume that the table holds mostly English documents, with an occasional German or Japanese document. To handle the three languages, you must create three sub-lexers: one for English, one for German, and one for Japanese as follows:

    ctx_ddl.create_preference('english_lexer','basic_lexer');
    ctx_ddl.set_attribute('english_lexer','index_themes','yes');
    ctx_ddl.set_attribtue('english_lexer','theme_language','english');

    ctx_ddl.create_preference('german_lexer','basic_lexer');
    ctx_ddl.set_attribute('german_lexer','composite','german');
    ctx_ddl.set_attribute('german_lexer','mixed_case','yes');
    ctx_ddl.set_attribute('german_lexer','alternate_spelling','german');

    ctx_ddl.create_preference('japanese_lexer','japanese_vgram_lexer');

Create the multi-lexer preference:

    ctx_ddl.create_preference('global_lexer', 'multi_lexer');

Because the stored documents are mostly English, make the English lexer the default:

    ctx_ddl.add_sub_lexer('global_lexer','default','english_lexer');

Add the German and Japanese lexers in their respective languages. Also assume that the language column is expressed in ISO 639-2, so add those as alternative values.

    ctx_ddl.add_sub_lexer('global_lexer','german','german_lexer','ger');
    ctx_ddl.add_sub_lexer('global_lexer','japanese','japanese_lexer','jpn');

Create the index `globalx`, specifying the multi-lexer preference and the language column in the parameters string as follows:

    create index globalx on globaldoc(text) indextype is ctxsys.context
    parameters ('lexer global_lexer language column lang');

You can specify a user-defined string for the `language` paramater as follows:

    ctx_ddl.add_sub_lexer('global_lexer','mysymbol','german_lexer','my_alt_symbol', language_dependent => FALSE);

#### Restrictions

The following restrictions apply to using `CTX_DDL.ADD_SUB_LEXER`:

- The invoking user must be the owner of the multi-lexer or `CTXSYS`.

- The `lexer_name` parameter must name a preference which is a multi-lexer lexer.

- A lexer for default must be defined before the multi-lexer can be used in an index.

- The sub-lexer preference owner must be the same as multi-lexer preference owner.

- The sub-lexer preference must not be a multi-lexer lexer.

- A sub-lexer preference cannot be dropped while it is being used in a multi-lexer preference.

- `CTX_DDL.ADD_SUB_LEXER` records only a reference. The sub-lexer values are copied at create index time to index value storage.

### 8.18 ADD_ZONE_SECTION

Creates a zone section and adds the section to an existing section group. This enables zone section searching with the [WITHIN](oracle-text-CONTAINS-query-operators.md) operator.

Zone sections are sections delimited by start and end tags. The `<B>` and `</B>` tags in HTML, for instance, marks a range of words which are to be rendered in boldface.

Zone sections can be nested within one another, can overlap, and can occur more than once in a document.

#### Syntax

    CTX_DDL.ADD_ZONE_SECTION(
      group_name     IN    VARCHAR2,
      section_name   IN    VARCHAR2,
      tag            IN    VARCHAR2
    );

group_name
Specify the name of the section group to which `section_name` is added.

section_name
Specify the name of the section to add to the group_name. Use this name to identify the section in `WITHIN` queries. Avoid using names that contain non-alphanumeric characters such as \_, because most of these characters are special must be escaped in queries. Section names are case-insensitive.

Within the same group, zone section names and field section names cannot be the same. The terms Paragraph and Sentence are reserved for special sections.

Section names need not be unique across tags. You can assign the same section name to more than one tag, making details transparent to searches.

tag
Specify the pattern which marks the start of a section. For example, if `<H1>` is the HTML tag, specify `H1` for `tag`. The start tag you specify must be unique within a section group.

Oracle Text knows what the end tags look like from the `group_type` parameter you specify when you create the section group.

If `group_name` is an `HTML_SECTION_GROUP`, you can create zone sections for the META tag's `NAME/CONTENT` attribute pairs. To do so, specify `tag` as `meta@namevalue`` `where `namevalue` is the value of the `NAME` attribute whose `CONTENT` attributes are to be indexed as a section. Refer to the example.

If `group_name` is an `XML_SECTION_GROUP`, you can optionally qualify `tag` with a document type (root element) in the form `(doctype)tag`. Doing so makes `section_name` sensitive to the XML document type declaration. Refer to the example.

#### Examples

Creating HTML Sections

The following example defines a section group called `htmgroup`of type `HTML_SECTION_GROUP`. It then creates a zone section in `htmgroup` called `headline `identified by the \<H1\> tag:

    begin
    ctx_ddl.create_section_group('htmgroup', 'HTML_SECTION_GROUP');
    ctx_ddl.add_zone_section('htmgroup', 'heading', 'H1');
    end;

After indexing with section group `htmgroup`, query within the heading section by issuing a query as follows:

    'Oracle WITHIN heading'

Creating Sections for `<META NAME>` Tags

You can create zone sections for HTML META tags when you use the `HTML_SECTION_GROUP`.

Consider an HTML document that has a `META` tag as follows:

    <META NAME="author" CONTENT="ken">

To create a zone section that indexes all `CONTENT` attributes for the `META` tag whose `NAME` value is author:

    begin
    ctx_ddl.create_section_group('htmgroup', 'HTML_SECTION_GROUP');
    ctx_ddl.add_zone_section('htmgroup', 'author', 'meta@author');
    end

After indexing with section group `htmgroup`, query the document as follows:

    'ken WITHIN author'

Creating Document Type Sensitive Sections (XML Documents Only)

You have an XML document set that contains the `<book>` tag declared for different document types (DTDs). You want to create a distinct book section for each document type.

Assume that `myDTDname` is declared as an XML document type as follows:

    <!DOCTYPE myDTDname>
    <myDTDname>
     ...

(Note: the `DOCTYPE` must match the top-level tag.)

Within `myDTDname`, the element `<book>` is declared. For this tag, create a section named `mybooksec` that is sensitive to the tag's document type as follows:

    begin
    ctx_ddl.create_section_group('myxmlgroup', 'XML_SECTION_GROUP');
    ctx_ddl.add_zone_section('myxmlgroup', 'mybooksec', '(myDTDname)book');
    end;

#### Notes

Repeated Sections

Zone sections can repeat. Each occurrence is treated as a separate section. For example, if \<H1\> denotes a `heading` section, they can repeat in the same documents as follows:

\<H1\> The Brown Fox \</H1\>

\<H1\> The Gray Wolf \</H1\>

Assuming that these zone sections are named `Heading`, the query Brown WITHIN Heading returns this document. However, a query of (Brown and Gray) WITHIN Heading does not.

Overlapping Sections

Zone sections can overlap each other. For example, if `<B>` and `<I>` denote two different zone sections, they can overlap in document as follows:

    plain <B> bold <I> bold and italic </B> only italic </I>  plain

Nested Sections

Zone sections can nest, including themselves as follows:

    <TD> <TABLE><TD>nested cell</TD></TABLE></TD>

Using the `WITHIN` operator, you can write queries to search for text in sections within sections. For example, assume the `BOOK1`, `BOOK2`, and `AUTHOR` zone sections occur as follows in documents doc1 and doc2:

doc1:

    <book1> <author>Scott Tiger</author> This is a cool book to read.</book1>

doc2:

    <book2> <author>Scott Tiger</author> This is a great book to read.</book2>

Consider the nested query:

    '(Scott within author) within book1'

This query returns only doc1.

#### Related Topics

"[WITHIN](oracle-text-CONTAINS-query-operators.md)"

"[Section Group Types](oracle-text-indexing-elements.md)"

"CREATE_SECTION_GROUP "

"ADD_FIELD_SECTION"

"ADD_SPECIAL_SECTION "

"REMOVE_SECTION "

"DROP_SECTION_GROUP "

### 8.19 COPY_POLICY

Creates a new policy from an existing policy or index.

#### Syntax

    ctx_ddl.copy_policy(
        source_policy       VARCHAR2,
        policy_name         VARCHAR2    );

source_policy
The name of the policy or index being copied.

policy_name
The name of the new policy copy.

The preference values are copied from the `source_policy`. Both the source policy or index and the new policy must be owned by the same database user.

### 8.20 CREATE_INDEX_SET

Creates an index set for `CTXCAT` index types. Name this index set in the parameter clause of `CREATE` `INDEX` when you create a `CTXCAT` index.

#### Syntax

    CTX_DDL.CREATE_INDEX_SET(set_name in varchar2);

set_name
Specify the name of the index set. Name this index set in the parameter clause of `CREATE` `INDEX` when you create a `CTXCAT` index.

### 8.21 CREATE_POLICY

Creates a policy to use with the `CTX_DOC.POLICY_*` procedures and the `ORA:CONTAINS` function. `ORA:CONTAINS` is a function you use within an `XPATH` query expression with `existsNode()`.

**See Also:**

[Oracle XML DB Developer's Guide](../adxdb/index.md)

#### Syntax

    CTX_DDL.CREATE_POLICY(
             policy_name     IN VARCHAR2,
             filter          IN VARCHAR2 DEFAULT NULL,
             section_group   IN VARCHAR2 DEFAULT NULL,
             lexer           IN VARCHAR2 DEFAULT NULL,
             stoplist        IN VARCHAR2 DEFAULT NULL,
             wordlist        IN VARCHAR2 DEFAULT NULL);

policy_name
Specify the name for the new policy. Policy names and Text indexes share the same namespace.

filter
Specify the filter preference to use.

section_group
Specify the section group to use. You can specify any section group that is supported by `CONTEXT` index.

lexer
Specify the lexer preference to use. Your `INDEX_THEMES` attribute must be disabled.

stoplist
Specify the stoplist to use.

wordlist
Specify the wordlist to use.

#### Example

Create mylex lexer preference named mylex.

    begin
       ctx_ddl.create_preference('mylex', 'BASIC_LEXER');
       ctx_ddl.set_attribute('mylex', 'printjoins', '_-');
       ctx_ddl.set_attribute ( 'mylex', 'index_themes', 'NO');
       ctx_ddl.set_attribute ( 'mylex', 'index_text', 'YES');
    end;

Create a stoplist preference named mystop.

    begin
      ctx_ddl.create_stoplist('mystop', 'BASIC_STOPLIST');
      ctx_ddl.add_stopword('mystop', 'because');
      ctx_ddl.add_stopword('mystop', 'nonetheless');
      ctx_ddl.add_stopword('mystop', 'therefore');
    end;

Create a wordlist preference named 'mywordlist'.

    begin
     ctx_ddl.create_preference('mywordlist', 'BASIC_WORDLIST');
     ctx_ddl.set_attribute('mywordlist','FUZZY_MATCH','ENGLISH');
     ctx_ddl.set_attribute('mywordlist','FUZZY_SCORE','1');
     ctx_ddl.set_attribute('mywordlist','FUZZY_NUMRESULTS','5000');
     ctx_ddl.set_attribute('mywordlist','SUBSTRING_INDEX','TRUE');
     ctx_ddl.set_attribute('mywordlist','STEMMER','ENGLISH');
    end;

    exec ctx_ddl.create_policy('my_policy', NULL, NULL, 'mylex', 'mystop',
    'mywordlist');

or

    exec ctx_ddl.create_policy(policy_name => 'my_policy',
                               lexer => 'mylex',
                               stoplist => 'mystop',
                               wordlist => 'mywordlist');

Then enter the following `existsNode()` query with your own defined policy:

    select id from xmltab
      where existsNode(doc, '/book/chapter[ ora:contains(summary,"dog or cat",
      "my_policy") >0 ]', 'xmlns:ora="http://xmlns.example.com/xdb" ')=1;

Update the policy with the following:

    exec ctx_ddl.update_policy(policy_name => 'my_policy', lexer => 'my_new_lex');

Drop the policy with the following:

    exec ctx_ddl.drop_policy(policy_name => 'my_policy');

### 8.22 CREATE_PREFERENCE

Creates a preference in the Text data dictionary.

Specify preferences in the parameter string of [CREATE INDEX](oracle-text-SQL-statements-and-operators.md) or [ALTER INDEX](oracle-text-SQL-statements-and-operators.md) .

**Caution:**

`CTX_DDL.CREATE_PREFERENCE` does not respect the current schema as set by `ALTER` `SESSION` `SET` `current_schema`. Therefore, if you need to create or delete a preference owned by another user, then you must explicitly state this, and you must have the `CREATE` `ANY` `TABLE` system privilege.

#### Syntax

    CTX_DDL.CREATE_PREFERENCE(preference_name  in varchar2,
                              object_name      in varchar2);

preference_name
Specify the name of the preference to be created.

object_name
Specify the name of the preference type.

**See Also:**

For a complete list of preference types and their associated attributes, see [Oracle Text Indexing Elements](oracle-text-indexing-elements.md)

#### Examples

Creating Text-only Index

The following example creates a lexer preference that specifies a text-only index. It does so by creating a `BASIC_LEXER` preference called `my_lexer` with `CTX_DDL.CREATE_PREFERENCE`. It then calls CTX_DDL.SET_ATTRIBUTE twice, first specifying YES for the `INDEX_TEXT` attribute, then specifying NO for the `INDEX_THEMES` attribute.

    begin
    ctx_ddl.create_preference('my_lexer', 'BASIC_LEXER');
    ctx_ddl.set_attribute('my_lexer', 'INDEX_TEXT', 'YES');
    ctx_ddl.set_attribute('my_lexer', 'INDEX_THEMES', 'NO');
    end;

Specifying File Data Storage

The following example creates a data storage preference called `mypref` that tells the system that the files to be indexed are stored in an Oracle directory object. The example then uses CTX_DDL.SET_ATTRIBUTE to set the `DIRECTORY` attribute to the directory `/docs`.

    begin
    ctx_ddl.create_preference('mypref', 'DIRECTORY_DATASTORE');
    ctx_ddl.set_attribute('mypref', 'DIRECTORY', '/docs');
    end;

**See Also:**

For more information about data storage, see "[Datastore Types](oracle-text-indexing-elements.md) "

Creating Primary/Detail Relationship

Use CTX_DDL.CREATE_PREFERENCE to create a preference with `DETAIL_DATASTORE`. Use CTX_DDL.SET_ATTRIBUTE to set the attributes for this preference. The following example shows how this is done:

    begin
    ctx_ddl.create_preference('my_detail_pref', 'DETAIL_DATASTORE');
    ctx_ddl.set_attribute('my_detail_pref', 'binary', 'true');
    ctx_ddl.set_attribute('my_detail_pref', 'detail_table', 'my_detail');
    ctx_ddl.set_attribute('my_detail_pref', 'detail_key', 'article_id');
    ctx_ddl.set_attribute('my_detail_pref', 'detail_lineno', 'seq');
    ctx_ddl.set_attribute('my_detail_pref', 'detail_text', 'text');
    end;

**See Also:**

For more information about primary/detail, see "[DETAIL_DATASTORE](oracle-text-indexing-elements.md) "

Specifying Storage Attributes

The following examples specify that the index tables are to be created in the `foo` tablespace with an initial extent of 1K:

    begin
    ctx_ddl.create_preference('mystore', 'BASIC_STORAGE');
    ctx_ddl.set_attribute('mystore', 'I_TABLE_CLAUSE',
                            'tablespace foo storage (initial 1K)');
    ctx_ddl.set_attribute('mystore', 'K_TABLE_CLAUSE',
                            'tablespace foo storage (initial 1K)');
    ctx_ddl.set_attribute('mystore', 'R_TABLE_CLAUSE',
                            'tablespace foo storage (initial 1K)');
    ctx_ddl.set_attribute('mystore', 'S_TABLE_CLAUSE',
                            'tablespace foo storage (initial 1K)');
    ctx_ddl.set_attribute('mystore', 'N_TABLE_CLAUSE',
                            'tablespace foo storage (initial 1K)');
    ctx_ddl.set_attribute('mystore', 'I_INDEX_CLAUSE',
                            'tablespace foo storage (initial 1K)');
    end;

**Note:**

If `S_TABLE_CLAUSE` is specified for a storage preference in an index without `SDATA`, then it has no effect on the index, and the index creation will still succeed.

**See Also:**

[Storage Types](oracle-text-indexing-elements.md)

Creating Preferences with No Attributes

When you create preferences with types that have no attributes, you need only create the preference, as in the following example which sets the filter to the `NULL_FILTER`:

    begin
    ctx_ddl.create_preference('my_null_filter', 'NULL_FILTER');
    end;

Specifying BIGRAM Mode for Japanese VGRAM Lexer

The following example creates a Japanese VGRAM lexer preference that specifies the BIGRAM mode of operation for the Japanese queries:

    begin
    ctx_ddl.create_preference('jp_lexer','JAPANESE_VGRAM_LEXER');
    ctx_ddl.set_attribute('jp_lexer','BIGRAM','TRUE');
    end;

    /* create the index */
    create index jp_idx on jp_doc(text) indextype is ctxsys.context
      parameters('lexer jp_lexer');

#### Related Topics

SET_ATTRIBUTE

DROP_PREFERENCE

[CREATE INDEX](oracle-text-SQL-statements-and-operators.md)

[ALTER INDEX](oracle-text-SQL-statements-and-operators.md)

[Oracle Text Indexing Elements](oracle-text-indexing-elements.md)

### 8.23 CREATE_SECTION_GROUP

Creates a section group for defining sections in a text column.

When you create a section group, you can add to it zone, field, or special sections with ADD_ZONE_SECTION , ADD_FIELD_SECTION, ADD_MDATA_SECTION, or ADD_SPECIAL_SECTION .

You also use `CREATE_SECTION_GROUP` with CTX_DDL.SET_SEC_GRP_ATTR to set `xml_enable` to create an Oracle XML Search Index.

When you index, name the section group in the parameter string of [CREATE INDEX](oracle-text-SQL-statements-and-operators.md) or [ALTER INDEX](oracle-text-SQL-statements-and-operators.md) .

After indexing, query within your defined sections with the [WITHIN](oracle-text-CONTAINS-query-operators.md) operator.

#### Syntax

    CTX_DDL.CREATE_SECTION_GROUP(
      group_name     in    varchar2,
      group_type     in    varchar2
    );

group_name
Specify the section group name to create as `section_group_name`. This parameter must be unique within an owner.

group_type
Specify section group type. The `group_type` parameter can be one of the following:

| Section Group Preference | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         |
|:-------------------------|:----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `NULL_SECTION_GROUP`     | Use this group type when you define no sections or when you define only SENTENCE or PARAGRAPH sections. This is the default.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                        |
| `BASIC_SECTION_GROUP`    | Use this group type for defining sections where the start and end tags are of the form `<A>` and `</A>`.<br>Note: This group type does not support input such as unbalanced parentheses, comments tags, and attributes. Use `HTML_SECTION_GROUP` for this type of input.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            |
| `HTML_SECTION_GROUP`     | Use this group type for indexing HTML documents and for defining sections in HTML documents.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                        |
| `JSON_SECTION_GROUP`     | Use this group to create a JSON enabled context index. The `JSON ENABLE` attribute cannot be used with `XML ENABLE`. A section group can only be marked as `JSON ENABLE`. If it is already marked with `XML ENABLE`, then the path section group cannot be used for `JSON ENABLE` and vice versa.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   |
| `XML_SECTION_GROUP`      | Use this group type for indexing XML documents and for defining sections in XML documents.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          |
| `AUTO_SECTION_GROUP`     | Use this group type to automatically create a zone section for each start-tag/end-tag pair in an XML document. The section names derived from XML tags are case sensitive as in XML.<br>Attribute sections are created automatically for XML tags that have attributes. Attribute sections are named in the form attribute@tag.<br>Stop sections, empty tags, processing instructions, and comments are not indexed.<br>The following limitations apply to automatic section groups:<br>• You cannot add zone, field, or special sections to an automatic section group.<br>• Automatic sectioning does not index XML document types (root elements.) However, you can define stop sections with document type.<br>• The length of the indexed tags, including prefix and namespace, cannot exceed 64 bytes. Tags longer than this are not indexed. |
| `PATH_SECTION_GROUP`     | Use this group type to index XML documents. Behaves like the `AUTO_SECTION_GROUP`.<br>The difference is that with this section group you can do path searching with the `INPATH` and `HASPATH` operators. Queries are also case-sensitive for tag and attribute names.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              |
| `NEWS_SECTION_GROUP`     | Use this group for defining sections in newsgroup formatted documents according to RFC 1036.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                        |

**Note:**

Starting with Oracle Database 18c, use of `NEWS_SECTION_GROUP` is deprecated in Oracle Text. Use external processing instead.

If you want to index USENET posts, then preprocess the posts to use `BASIC_SECTION_GROUP` or `HTML_SECTION_GROUP` within Oracle Text. USENET is rarely used commercially.

#### Examples

The following command creates a section group called `htmgroup` with the HTML group type.

    begin

    ctx_ddl.create_section_group('htmgroup', 'HTML_SECTION_GROUP');

    end;

The following command creates a section group called `auto` with the `AUTO_SECTION_GROUP` group type to be used to automatically index tags in XML documents.

    begin

    ctx_ddl.create_section_group('auto', 'AUTO_SECTION_GROUP');

    end;

The following example creates an Oracle XML Search index:

    exec CTX_DDL.CREATE_SECTION_GROUP('secgroup','PATH_SECTION_GROUP');
    exec CTX_DDL.SET_SEC_GRP_ATTR('secgroup','xml_enable','t');
    CREATE INDEX po_ctx_idx on T(X) indextype is ctxsys.context
    parameters ('section group SECGROUP');

#### Related Topics

"[WITHIN](oracle-text-CONTAINS-query-operators.md)"

"[Section Group Types](oracle-text-indexing-elements.md)"

"ADD_ZONE_SECTION "

"ADD_FIELD_SECTION"

"ADD_MDATA_SECTION"

"ADD_SPECIAL_SECTION "

"REMOVE_SECTION "

"DROP_SECTION_GROUP "

### 8.24 CREATE_SHADOW_INDEX

Creates index metadata (or policy) for the specified index. If the index is not partitioned, then it also creates the index tables. This procedure is only supported in Enterprise Edition of Oracle Database.

The following changes are not supported:

- Transition from non-composite domain index to composite, or changing the composite domain index columns.

- Rebuild indexes that have partitioned index tables, for example, \$I, \$P, \$K.

**Note:**

- For a partitioned index, you must first call this procedure to create the shadow index metadata. This procedure will not create index tables. It has no effect on query, DML, sync, or optimize operations.

- The `CREATE_SHADOW_INDEX` and `RECREATE_INDEX_ONLINE` procedures do not support section group with the `XML_ENABLE` attribute on `CONTEXT` indexes. Doing so results in the "`DRG-10521: Operation not supported with XML_ENABLE on a CONTEXT Index`" error.

#### Syntax

    CTX_DDL.CREATE_SHADOW_INDEX(
      idx_name          IN VARCHAR2,
      parameter_string  IN VARCHAR2 DEFAULT NULL,
      parallel_degree   IN NUMBER DEFAULT 1
    );

idx_name
The name of a valid `CONTEXT` indextype.

parameter_string
For nonpartitioned index, the same string as in `ALTER` `INDEX`. For partitioned index, the same string as in `ALTER` `INDEX` `PARAMETER`.

parallel_degree
Reserved for future use. Specify the degree of parallelism. Parallel operation is not currently supported.

#### Example

Example 8-1 Scheduled Global Index RECREATE (Incremental Rebuild)

In this example, you have the finest control over each stage of RECREATE_INDEX_ONLINE. Since `SYNC_INDEX` can take a time limit, you can limit `SYNC_INDEX` during non-business hours and incrementally recreate the index.

    /* create lexer and original index */
    exec ctx_ddl.create_preference('us_lexer','basic_lexer');
    create index idx on tbl(text) indextype is ctxsys.context
      parameters('lexer us_lexer');

    /* create a new lexer */
    begin
      ctx_ddl.create_preference('e_lexer','basic_lexer');
      ctx_ddl.set_attribute('e_lexer','base_letter','yes');
      ctx_ddl.create_preference('m_lexer','multi_lexer');
      ctx_ddl.add_sub_lexer('m_lexer','default','us_lexer');
      ctx_ddl.add_sub_lexer('m_lexer','e','e_lexer');
    end;
    /

    /* add new language column to the table for multi-lexer */
    alter table tbl add(lang varchar2(10) default 'us');

    /* create shadow index */
    exec ctx_ddl.create_shadow_index('idx',
      'replace lexer m_lexer language column lang NOPOPULATE');

    declare
      idxid integer;
    begin
      /* figure out shadow index name */
      select idx_id into idxid from ctx_user_indexes
         where idx_name ='IDX';
      /* populate pending */
      ctx_ddl.populate_pending('RIO$'||idxid);
      /* time limited sync */
      ctx_ddl.sync_index(idx_name =>'RIO$'||idxid,
                         maxtime =>480);
      /* more sync until no pending rows for the shadow index */
    end;
    /* swap in the shadow index */
    exec ctx_ddl.exchange_shadow_index('idx');

#### Notes

- The index name for the shadow index is `RIO$index_id`. By default, it also populates index tables for nonpartitioned indexes, unless `NOPOPULATE` is specified in `CREATE` `INDEX` or in `ALTER` `INDEX`. For a local partitioned index, it only creates index metadata without creating the index tables for each partition. Each index can have only one shadow index.

- When building a nonpartitioned index online, you can first call this procedure to create index metadata and index tables. If you specify `POPULATE`, then this procedure populates the index, but does not do swapping. You can schedule the swapping at a later, preferred time.

  If you specify `NOPOPULATE`, it only creates metadata for the index tables, but does not populate them. You must perform `POPULATE_PENDING` (CTX_DDL.POPULATE_PENDING) to populate the pending queues after running this procedure, and then sync the indexes. This is referred to as incremental re-create.

  Queries are all processed normally when this procedure is running.

- If `POPULATE` is specified, then DML is blocked for a very short time at the beginning of populate, after which all further DML is logged into an online pending queue and processed later.

- In case of `NOPOPULATE` shadow indexes, ensure that you execute the `POPULATE_PENDING` procedure before calling a DML operation. If you call a DML operation before executing the `POPULATE_PENDING` procedure, then the same tokens appear twice in the `$I` index table.

- Sync with CTX_DDL.SYNC_INDEX runs normally on the index. OPTIMIZE_INDEX runs without doing anything, but does not return an error.

**Related Topics**

- [ALTER INDEX](oracle-text-SQL-statements-and-operators.md)
- [CREATE INDEX](oracle-text-SQL-statements-and-operators.md)
- [Oracle Text SQL Statements and Operators](oracle-text-SQL-statements-and-operators.md)
- DROP_SHADOW_INDEX
- EXCHANGE_SHADOW_INDEX
- SYNC_INDEX
- POPULATE_PENDING

### 8.25 CREATE_STOPLIST

Use this procedure to create a new, empty stoplist. Stoplists can contain words or themes that are not to be indexed.

You can also create multi-language stoplists to hold language-specific stopwords. A multi-language stoplist is useful when you index a table that contains documents in different languages, such as English, German, and Japanese. When you do so, the text table must contain a language column.

Add either stopwords, stopclasses, or stopthemes to a stoplist using ADD_STOPWORD, ADD_STOPCLASS, or ADD_STOPTHEME. Specify a stoplist in the parameter string of [CREATE INDEX](oracle-text-SQL-statements-and-operators.md) or [ALTER INDEX](oracle-text-SQL-statements-and-operators.md) to override the default stoplist `CTXSYS.DEFAULT_STOPLIST`.

#### Syntax

    CTX_DDL.CREATE_STOPLIST(

    stoplist_name IN VARCHAR2,
    stoplist_type IN VARCHAR2 DEFAULT 'BASIC_STOPLIST');

stoplist_name
Specify the name of the stoplist to be created.

stoplist_type
Specify `BASIC_STOPLIST` to create a stoplist for a single language. This is the default.

Specify `MULTI_STOPLIST` to create a stoplist with language-specific stopwords.

At indexing time, the language column of each document is examined, and only the stopwords for that language are eliminated. At query time, the session language setting determines the active stopwords, like it determines the active lexer when using the multi-lexer.

**Note:**

When indexing a multi-language table with a multi-language stoplist, the table must have a language column.

#### Examples

Example 8-2 Single Language Stoplist

The following example creates a stoplist called `mystop`:

    begin
    ctx_ddl.create_stoplist('mystop', 'BASIC_STOPLIST');
    end;

Example 8-3 Multi-Language Stoplist

The following example creates a multi-language stoplist called `multistop` and then adds tow language-specific stopwords:

    begin
    ctx_ddl.create_stoplist('multistop', 'MULTI_STOPLIST');
    ctx_ddl.add_stopword('mystop', 'Die','german');
    ctx_ddl.add_stopword('mystop', 'Or','english');
    end;

#### Related Topics

"ADD_STOPWORD "

"ADD_STOPCLASS "

"ADD_STOPTHEME "

"DROP_STOPLIST "

"[CREATE INDEX](oracle-text-SQL-statements-and-operators.md)"

"[ALTER INDEX](oracle-text-SQL-statements-and-operators.md) "

[Oracle Text Supplied Stoplists](oracle-text-supplied-stoplists.md)

### 8.26 DROP_INDEX_SET

Drops a `CTXCAT` index set created with CTX_DDL.CREATE_INDEX_SET.

#### Syntax

    CTX_DDL.DROP_INDEX_SET(
         set_name    IN VARCHAR2
    );

set_name
Specify the name of the index set to drop.

Dropping an index set drops all of the sub-indexes it contains.

### 8.27 DROP_POLICY

Drops a policy created with CTX_DDL.CREATE_POLICY.

#### Syntax

    CTX_DDL.DROP_POLICY(
         policy_name    IN VARCHAR2
    );

policy_name
Specify the name of the policy to drop.

### 8.28 DROP_PREFERENCE

The `DROP_PREFERENCE` procedure deletes the specified preference from the Text data dictionary. Dropping a preference does not affect indexes that have already been created using that preference.

#### Syntax

    CTX_DDL.DROP_PREFERENCE(
         preference_name    IN VARCHAR2
    );

preference_name
Specify the name of the preference to be dropped.

#### Example

The following example drops the preference `my_lexer`.

    begin
    ctx_ddl.drop_preference('my_lexer');
    end;

#### Related Topics

CTX_DDL.CREATE_PREFERENCE

### 8.29 DROP_SECTION_GROUP

The `DROP_SECTION_GROUP` procedure deletes the specified section group, as well as all the sections in the group, from the Text data dictionary.

#### Syntax

    CTX_DDL.DROP_SECTION_GROUP(
         group_name     IN VARCHAR2
    );

group_name
Specify the name of the section group to delete.

#### Example

The following example drops the section group `htmgroup` and all its sections:

    begin
    ctx_ddl.drop_section_group('htmgroup');
    end;

#### Related Topics

"CREATE_SECTION_GROUP "

"PREFERENCE_IMPLICIT_COMMIT"

### 8.30 DROP_SHADOW_INDEX

Drops a shadow index for the specified index. When you drop a shadow index, if it is partitioned, then its metadata and the metadata of all this shadow index's partitions are dropped. This procedure also drops all the shadow index tables and cleans up any online pending queue.

#### Syntax

    CTX_DDL.DROP_SHADOW_INDEX(
         idx_name       in VARCHAR2
    );

idx_name
The name of a valid `CONTEXT` indextype.

#### Example

The following example drops the shadow index `myshadowidx`:

    begin
    ctx_ddl.drop_shadow_index('myshadowidx');
    end;

#### Related Topics

CTX_DDL.CREATE_SHADOW_INDEX

### 8.31 DROP_STOPLIST

Drops a stoplist from the Text data dictionary. When you drop a stoplist, you must re-create or rebuild the index for the change to take effect.

#### Syntax

    CTX_DDL.DROP_STOPLIST(stoplist_name in varchar2);

stoplist_name
Specify the name of the stoplist.

#### Example

The following example drops the stoplist `mystop`:

    begin
    ctx_ddl.drop_stoplist('mystop');
    end;

#### Related Topics

CTX_DDL.CREATE_STOPLIST

### 8.32 EXCHANGE_SHADOW_INDEX

This procedure swaps the index (or index partition) metadata and index (or index partition) data.

For nonpartitioned indexes, this procedure swaps both the metadata and the index data, and processes the online pending queue.

#### Syntax

    CTX_DDL.EXCHANGE_SHADOW_INDEX(
         idx_name        IN VARCHAR2
         partition_name  IN VARCHAR2 default NULL
    );

idx_name
Specify the name of the `CONTEXT` indextype.

<!-- -->

partition_name
Specify the name of the shadow index partition. May also be NULL.

#### Example

Example 8-4 Global Index RECREATE with Scheduled Swap

This example demonstrates running `CTX_DDL.EXCHANGE_SHADOW_INDEX` during non-business hours when query failures and DML blocking can be tolerated.

    /* create lexer and original index */
    exec ctx_ddl.create_preference('us_lexer','basic_lexer');
    create index idx on tbl(text) indextype is ctxsys.context
      parameters('lexer us_lexer');

    /* create a new lexer */
    begin
      ctx_ddl.create_preference('e_lexer','basic_lexer');
      ctx_ddl.set_attribute('e_lexer','base_letter','yes');
      ctx_ddl.create_preference('m_lexer','multi_lexer');
      ctx_ddl.add_sub_lexer('m_lexer','default','us_lexer');
      ctx_ddl.add_sub_lexer('m_lexer','e','e_lexer');
    end;
    /

    /* add new language column to the table for multi-lexer */
    alter table tbl add(lang varchar2(10) default 'us');

    /* recreate index online with the new multip-lexer */
    exec ctx_ddl.create_shadow_index('idx',
      'replace lexer m_lexer language column lang');
    exec ctx_ddl.exchange_shadow_index('idx');

#### Notes

- Using EXCHANGE_SHADOW_INDEX with Nonpartitioned Indexes:

  For nonpartitioned indexes, this procedure will swap both metadata and index data, and will process the online pending queue.

  Queries will return column not indexed errors when swapping metadata and index data, but queries are processed normally when processing online pending queue. The period of errors being raised should be short.

  If you specify `POPULATE` when you create the shadow index, and if many DML operations have been issued since the creation of the shadow index, then there could be a large pending queue. However, if you use incremental recreate, that is, specify `NOPOPULATE` when you create the shadow index, and you then populate the pending queue and sync, then the online pending queue is always empty no matter how many DML operations have occurred since `CREATE_SHADOW_INDEX` was issued.

  When this procedure is running, DML will first fail with an error about index being in in-progress status. After that DML could be blocked if there are rows in online pending queue that need to be reapplied.

  **Note:**

  When this procedure is running, DML statements will fail with an error that the index is in "in-progress status." If, when this error occurs, there are rows in the online pending queue that need to be reapplied, then the DML could be blocked and stop responding.

- Using EXCHANGE_SHADOW_INDEX with Partitioned Indexes:

  For partitions that are recreated with `NOSWAP`: when the index is partitioned, and if partition_name is a valid index partition, then this procedure will swap the index partition data and the index partition metadata, and will process the online pending queue for this partition.

  This procedure swaps only one partition at a time. When you run this procedure on partitions that are recreated with `NOSWAP`:

  - Queries that span multiple partitions will not return consistent results across all partitions.

  - Queries on the partition that is being swapped will return errors.

  - Queries on partitions that are already swapped will be based on the new index.

  - Queries on the partitions that haven't been swapped will be based on the old index.

  If the partition_name is NULL, then this procedure will swap the index metadata. Run this procedure as the last step when recreating a local partitioned index online.

- Sync Behavior:

  After running `EXCHANGE_SHADOW_INDEX`, you must call the `SYNC_INDEX` operation to synchronize any DML that occurs during the build of the shadow index. If you have specified `SYNC(ON COMMIT)` or `SYNC(EVERY)`, then the sync occurs automatically. However, if you have specified `SYNC(MANUAL)`, then you must manually invoke `SYNC_INDEX`.

#### Related Topics

CTX_DDL."RECREATE_INDEX_ONLINE"

CTX_DDL."CREATE_SHADOW_INDEX"

CTX_DDL."DROP_SHADOW_INDEX"

### 8.33 OPTIMIZE_INDEX

Use this procedure to optimize the index. Optimizing an index removes old data and minimizes index fragmentation, which can improve query response time.

Optimize your index after you synchronize it. Querying and DML may proceed while optimization takes place.

You can optimize in fast, full, rebuild, token, token-type, or merge mode.

- Fast mode compacts data but does not remove rows.

- Full mode compacts data and removes rows.

- Optimize in rebuild mode rebuilds the `$I` table (the inverted list table) in its entirety. Rebuilding an index is often significantly faster than performing a full optimization, and is more likely to result in smaller indexes, especially if the index is heavily fragmented.

  Rebuild optimization creates a more compact copy of the `$I` table, and then switches the original `$I` table and the copy. The rebuild operation will therefore require enough space to store the copy as well as the original. (If redo logging is enabled, then additional space is required in the redo log as well.) At the end of the rebuild operation, the original `$I` table is dropped, and the space can be reused. A temporary "change capture trigger" is used to ensure that updates to the `$I` table during the optimization are not lost. For this reason, the user calling `OPTIMIZE_INDEX` in `REBUILD` mode must have the `CREATE` `TRIGGER` privilege.

  Optimize in rebuild mode supports partitioning on the `$I` table via the `i_table_clause` attribute of the `basic_storage` preference with the following limitations:

  - The `i_index_clause` must specify using a local btree index if the `$I` table is partitioned.

  - Partitioning schemes on the `token_first`, `token_last`, or `token_count` columns are not allowed.

  **Note:**

  `OPTIMIZE_INDEX` in rebuild mode is not supported in Oracle Autonomous Data Warehouse Cloud with Oracle Database release 18c, version 18.3 artifacts unless you grant the privilege to create a trigger to the user. You must also disable parallel DML either at the session or system level. Run the following SQL statements to grant the privilege to create a trigger and disable parallel DML:

      grant create trigger to user;
      alter session disable parallel dml;

- In token mode, specify a specific token to be optimized (for example, all rows with documents containing the word elections). Use this mode to optimize index tokens that are frequently searched, without spending time on optimizing tokens that are rarely referenced. An optimized token can improve query response time (but only for queries on that token).

- Token-type optimization is similar to token mode, except that the optimization is performed on field, `MDATA`, or `SDATA` sections (for example, sections with an `<A>` tag). This is useful in keeping critical field or `MDATA` sections optimal.

- Use the merge mode to optimize the \$I table for the `CONTEXT` indexes that are frequently used for DML operations. The merge operation compacts the existing data in the \$G table, and then copies that data to the \$I table. The compacted rows are then deleted from the \$G table.

A common strategy for optimizing indexes is to perform regular token optimizations on frequently referenced terms, and to perform rebuild optimizations less frequently. (Use CTX_REPORT.[QUERY_LOG_SUMMARY](CTX_REPORT-package.md) to find out which queries are made most frequently.) You can perform full, fast, or token-type optimizations instead of token optimizations.

Some users choose to perform frequent time-limited full optimizations along with occasional rebuild optimizations.

**Note:**

- Optimizing an index can result in better response time only if you insert, delete, or update documents in the base table after your initial indexing operation.

- When you run index optimization, any work in the session is committed effectively and that work cannot be rolled back.

Using this procedure to optimize the index is recommended over using the `ALTER` `INDEX` statement.

Optimization of a large index may take a long time. To monitor the progress of a lengthy optimization, log the optimization with CTX_OUTPUT.[START_LOG](CTX_OUTPUT-package.md) and check the resultant logfile from time to time.

Note that, unlike serial optimize full, `CTX_DDL.OPTIMIZE_INDEX()` run with `optlevel` of `FULL` and `parallel_degree` \> 1 is not resumable. That is, it will not resume from where it left after a time-out or failure.

**Note:**

There is a very small window of time when a query might fail in `CTX_DDL.OPTIMIZE_INDEX` `REBUILD` mode when the `$I` table is being swapped with the optimized shadow `$I` table.

#### Syntax

    CTX_DDL.OPTIMIZE_INDEX(

    idx_name        IN  VARCHAR2,
    optlevel        IN  VARCHAR2,
    maxtime         IN  NUMBER DEFAULT NULL,
    token           IN VARCHAR2 DEFAULT NULL,
    part_name       IN VARCHAR2 DEFAULT NULL,
    token_type      IN NUMBER DEFAULT NULL,
    parallel_degree IN NUMBER DEFAULT 1,
    maxtokens       IN NUMBER DEFAULT NULL,
    section_type    IN NUMBER DEFAULT NULL

    );

idx_name
Specify the name of the index. If you do not specify an index name, then Oracle Text chooses a single index to optimize.

optlevel
Specify optimization level as a string. You can specify one of the following methods for optimization:

| optlevel value                                | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  |
|:----------------------------------------------|:-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `FAST` or `CTX_DDL.OPTLEVEL_FAST`             | This method compacts fragmented rows. However, old data is not removed.<br>`FAST` optimization is not supported for `CTXCAT` indexes. `FAST` optimization will not optimize `$S` index table.<br>Fast optimization is not supported for local Oracle Text search indexes.                                                                                                                                                                                                                                                                                    |
| `FULL` or `CTX_DDL.OPTLEVEL_FULL`             | In this mode you can optimize the entire index or a portion of the index. This method compacts rows and removes old data (deleted rows). Optimizing in full mode runs even when there are no deleted rows.<br>Full optimization is not supported for `CTXCAT` indexes.                                                                                                                                                                                                                                                                                       |
| `REBUILD` or `CTX_DDL.OPTLEVEL_REBUILD`       | This `optlevel` rebuilds the `$I` table (the inverted list table) to produce more compact token info rows. Similar to `FULL` optimize, this mode also deletes information pertaining to deleted rows of the base table.<br>`REBUILD` is not supported for `CTCAT` and `CTXRULE` indexes.                                                                                                                                                                                                                                                                     |
| `TOKEN` or `CTX_DDL.OPTLEVEL_TOKEN`           | This method lets you specify a specific token to be optimized. Oracle Text does a full optimization on the token you specify with `token`. If no token type is provided, 0 (zero) will be used as the default.<br>Use this method to optimize those tokens that are searched frequently.<br>Token optimization is not supported for `CTCAT` and `CTXRULE` indexes.                                                                                                                                                                                           |
| `TOKEN_TYPE` or `CTX_DDL.OPTLEVEL_TOKEN_TYPE` | This optlevel optimizes on demand all tokens in the index matching either the input token type or the input section type.<br>When `optlevel` is `TOKEN_TYPE`, either token_type or section_type must be provided. `TOKEN_TYPE` performs `FULL` optimize on any token of the input token_type or section_type, whichever is provided. Similar to `TOKEN` optimize, `TOKEN_TYPE` optimize does not change the `FULL` optimize state, and runs to completion on each invocation.<br>Token_type optimization is not supported for `CTCAT` and `CTXRULE` indexes. |
| `MERGE` or `CTX_DDL.OPTLEVEL_MERGE`           | This optlevel compacts the rows in the staging `$G` table and merges them into the `$I` table.<br>This option is not supported at the token level. Specifying the `TOKEN` attribute with this option results in an error.<br>Merge optimization should be used for `CONTEXT` indexes with the `STAGE_ITAB` index option enabled.                                                                                                                                                                                                                             |

The behavior of `CTX_DDL.OPTIMIZE_INDEX` with respect to the \$S index table is as follows:

| optlevel value                                | Will Optimize \$S Index Table Yes/No | Notes                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           |
|:----------------------------------------------|:-------------------------------------|:----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `FAST` or `CTX_DDL.OPTLEVEL_FAST`             | No                                   |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 |
| `FULL` or `CTX_DDL.OPTLEVEL_FULL`             | Yes                                  | • The optimize process will optimize \$I table first. Once \$I table optimize is finished, `CTX_DDL.OPTIMIZE_INDEX` will continue on to optimize \$S index table.<br>• `MAXTIME` will also be honored. Once `CTX_DDL.OPTIMIZE_INDEX` completes optimizing \$S rows for a given `SDATA_ID`, it will check `MAXTIME` and exit if total elapsed time (including time taken to optimize \$I) exceeds specified `MAXTIME`. The next `CTX_DDL.OPTIMIZE_INDEX` with `optlevel=>'FULL'` will pick up where it left off.<br>• \$S table optimize will be done in serial. |
| `REBUILD` or `CTX_DDL.OPTLEVEL_REBUILD`       | Yes                                  | • \$S optimize will start after \$I rebuild finishes.<br>• \$S optimize in this case will be processed the same way as \$S optimize in `FULL` mode. \$S table is optimized in place, not rebuilt.<br>• Note: If for some reason \$S optimize exits unusually, then it is recommended that you use `optlevel=>TOKEN_TYPE` to optimize \$S to avoid rebuilding the \$I table again.<br>• \$S table optimize will be done in serial.                                                                                                                               |
| `TOKEN` or `CTX_DDL.OPTLEVEL_TOKEN`           | No                                   |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 |
| `TOKEN_TYPE` or `CTX_DDL.OPTLEVEL_TOKEN_TYPE` | Yes                                  | You can optimize \$S rows for a given `SDATA_ID` by setting `optlevel => TOKEN_TYPE` and the `TOKEN_TYPE` parameter to the target `SDATA_ID`.                                                                                                                                                                                                                                                                                                                                                                                                                   |

maxtime
Specify maximum optimization time, in minutes, for `FULL` optimize.

When you specify the symbol `CTX_DDL`.`MAXTIME_UNLIMITED` (or pass in NULL), the entire index is optimized. This is the default.

token
Specify the `token` to be optimized.

part_name
If your index is a local index, then you must specify the name of the index partition to synchronize otherwise an error is returned.

If your index is a global, nonpartitioned index, then specify `NULL,` which is the default.

token_type
Specify the `token_type` to be optimized.

You can find the `token_type` by using the `CTX_REPORT.TOKEN_TYPE` method or the `CTX_USER_SECTIONS` view.

parallel_degree
Specify the parallel degree as a number for parallel optimization. The actual parallel degree depends on your resources.

Because the `optlevel` values are executed serially, this setting throws the error DRG-10598 for the following values:

- `TOKEN` or `CTX_DDL.OPTLEVEL_TOKEN`

- `FAST` or `CTX_DDL.OPTLEVEL_FAST`

maxtokens
Specify the `maxtokens` to be optimized.

`maxtokens` attribute can be specified only when `optlevel` value is set to `TOKEN` or `CTX_DDL.OPTLEVEL_TOKEN` and when the `token` parameter is `NULL.`

**Note:**

- If the number of fragmented tokens exceeds 50% of total number of tokens in \$I and `maxtokens` is not specified, then “index too fragmented” error is returned.

- If `maxtokens` specified is negative or greater than 50% of total number of tokens in \$I, then “invalid value for maxtokens” error is returned.

section_type
Specify the `section_type` to optimize all sections of a certain type. This parameter can have one of the following values:

| section_type value               | Description                                                                         |
|:---------------------------------|:------------------------------------------------------------------------------------|
| `CTX_DDL.SECTION_FIELD`          | The optimization is run for all field sections in the index.                        |
| `CTX_DDL.SECTION_SORT_SDATA`     | The optimization is run for all `optimized_for` sort SDATA sections in the index.   |
| `CTX_DDL.SECTION_MDATA`          | The optimization is run for all MDATA sections in the index.                        |
| `CTX_DDL.SECTION_SEARCH_SDATA`   | The optimization is run for all `optimized_for` search SDATA sections in the index. |
| `CTX_DDL.SECTION_WILDCARD_INDEX` | The optimization is run for the \$KG table (that is, the wildcard search index).    |

**Note:**

- You can specify `section_type` only when the `optlevel` value is set to `TOKEN_TYPE` or `CTX_DDL.OPTLEVEL_TOKEN_TYPE`.

- In the absence of sections of the specified type, index optimization for `section_type` is a no-op (no operations). Similarly, in the absence of the \$KG table, index optimization for the `CTX_DDL.SECTION_WILDCARD_INDEX` `section_type` value is a no-op.

#### Examples

The following two examples are equivalent ways of optimizing an index using fast optimization:

    begin
      ctx_ddl.optimize_index('myidx','FAST');
    end;

    begin
      ctx_ddl.optimize_index('myidx',CTX_DDL.OPTLEVEL_FAST);
    end;

The following example optimizes the index token Oracle:

    begin
      ctx_ddl.optimize_index('myidx','token', TOKEN=>'Oracle');
    end;

To optimize all tokens of field section `MYSEC` in index `MYINDEX`:

    begin
      ctx_ddl.optimize_index('myindex', ctx_ddl.optlevel_token_type,
         token_type=> ctx_report.token_type('myindex','field mysec text'));end;

The following two examples are equivalent ways of optimizing an index using merge optimization:

    begin
      ctx_ddl.optimize_index('idx','MERGE');
    end;

    begin
      ctx_ddl.optimize_index('idx',CTX_DDL.OPTLEVEL_MERGE);
    end;

The following example optimizes the top 10 fragmented tokens in \$I:

    begin
     ctx_ddl.optimize_index('idx','TOKEN',maxtokens=>10);
    end;

#### Notes

You can run `CTX_DDL.SYNC_INDEX` and `CTX_DDL.OPTIMIZE_INDEX` at the same time. You can also run `CTX_DDL.SYNC_INDEX` and `CTX_DDL.OPTIMIZE_INDEX` with parallelism at the same time. However, you should not:

- Run `CTX_DDL.SYNC_INDEX` with parallelism at the same time as `CTX_DDL.OPTIMIZE_INDEX`

- Run `CTX_DDL.SYNC_INDEX` with parallelism at the same time as `CTX_DDL.OPTIMIZE_INDEX` with parallelism.

If you should run one of these combinations, no error is generated; however, one operation will wait until the other is done.

**Related Topics**

- SYNC_INDEX
- [ALTER INDEX](oracle-text-SQL-statements-and-operators.md)

### 8.34 POPULATE_PENDING

This procedure populates the pending queue with every rowid in the base table or table partition. This procedure is only supported for `CONTEXT` indexes.

This procedure is valuable for large installations that cannot afford to have the indexing process run continuously, and, therefore, need finer control over creating text indexes. The preferred method is to create an empty index, place all the rowids into the pending queue, and build the index through CTX_DDL.SYNC_INDEX.

#### Syntax

    ctx_ddl.populate_pending(
      idx_name  IN VARCHAR2,
      part_name IN VARCHAR2 DEFAULT NULL
    );

idx_name
Name of the `CONTEXT` indextype.

part_name
Name of the index partition, if any. Must be provided for local partitioned indexes and must be NULL for global, nonpartitioned indexes.

#### Notes

The `SYNC_INDEX` is blocked for the duration of the processing. The index unit must be totally empty (`idx_docid_count` = 0, `idx_nextid` = 1). The rowids of rows waiting to be indexed are inserted into table `ctxsys.dr$pending`. You should ensure that there is sufficient space in this table to hold the rowids of the base table.

#### Related Topics

"SYNC_INDEX"

"CREATE_SHADOW_INDEX"

"DROP_SHADOW_INDEX"

"EXCHANGE_SHADOW_INDEX"

"RECREATE_INDEX_ONLINE"

### 8.35 PREFERENCE_IMPLICIT_COMMIT

This variable, set at the package level for CTX_DDL, determines whether procedures related to `CTX_DDL` preferences issue an implicit commit and is session duration.

You can set the `PREFERENCE_IMPLICIT_COMMIT` variable for the procedures listed in the following table.

| Procedure Name      | Procedure Name       |
|:--------------------|:---------------------|
| ADD_ATTR_SECTION    | CREATE_INDEX_SET     |
| ADD_FIELD_SECTION   | CREATE_PREFERENCE    |
| ADD_INDEX           | CREATE_SECTION_GROUP |
| ADD_MDATA_COLUMN    | CREATE_STOPLIST      |
| ADD_MDATA_SECTION   | DROP_PREFERENCE      |
| ADD_SDATA_COLUMN    | DROP_SECTION_GROUP   |
| ADD_SDATA_SECTION   | DROP_STOPLIST        |
| ADD_SPECIAL_SECTION | REMOVE_INDEX         |
| ADD_STOPCLASS       | REMOVE_SECTION       |
| ADD_STOP_SECTION    | REMOVE_SUB_LEXER     |
| ADD_STOPTHEME       | SET_ATTRIBUTE        |
| ADD_STOPWORD        | UNSET_ATTRIBUTE      |
| ADD_SUB_LEXER       | UPDATE_SUB_LEXER     |
| ADD_ZONE_SECTION    |                      |

**Note:**

The `REMOVE_STOPCLASS`, `REMOVE_STOPTHEME`, and `REMOVE_STOPWORD` procedures do not issue an implicit commit, and, therefore, do not use the `PREFERENCE_IMPLICIT_COMMIT` flag.

#### Syntax

    exec CTX_DDL.PREFERENCE_IMPLICIT_COMMIT := TRUE|FALSE ;

The default value of the `PREFERENCE_IMPLICIT_COMMIT` variable is `TRUE`. When this variable is set to `FALSE`, procedures related to `CTX_DDL` preferences will not issue an implicit commit. This enables you to easily rollback multiple preference changes. This variable is session duration.

#### Example

The following example turns off implicit commit.

    exec CTX_DDL.PREFERENCE_IMPLICIT_COMMIT : update_sub_lexer = FALSE;

### 8.36 RECREATE_INDEX_ONLINE

Recreates the specified index, or recreates the passed-in index partition if the index is local partitioned.

For global nonpartitioned indexes, this is a one-step procedure. For local partitioned indexes, this procedure must be run separately on every partition after first using CREATE_SHADOW_INDEX to create a shadow policy (or metadata). This procedure is only supported in Enterprise Edition of Oracle Database.

The following changes are not supported:

- Transitioning from non-composite domain index to composite, or changing the composite domain index columns.

- Rebuilding indexes that have partitioned index tables, for example, `$I`, `$P`, `$K`.

#### Syntax

    CTX_DDL.RECREATE_INDEX_ONLINE(
       idx_name          IN VARCHAR2,
       parameter_string  IN VARCHAR2 default NULL,
       parallel_degree   IN NUMBER default 1,
       partition_name    IN VARCHAR2 default NULL
    );

idx_name
The name of a valid `CONTEXT` indextype.

parameter_string
If the index is a global nonpartitioned index, specify the same index-level parameter string as in `ALTER` `INDEX`. Must start with `REPLACE`, if it is not `NULL`. Optionally specify `SWAP` or `NOSWAP`. The default is `SWAP`.

parallel_degree
Reserved for future use. Specify the degree of parallelism. Parallel operation is not supported in the current release.

partition_name
Specify the name of a valid index partition for a local partitioned index. Otherwise, the default is `NULL`. If the index is partitioned, then first pass a partition name, and then specify the partition-level parameter string for `ALTER` `INDEX` `REBUILD` `PARTITION`.

#### Examples

Example 8-5 Recreate Simple Global Index

The following example creates an index `idx` with a `BASIC_LEXER`-based preference `us_lexer`. It then recreates the index with a new `MULTI_LEXER` based preference `m_lexer` in one step. You can use this one step approach when you do not mind that a query might fail for a small window of time at the end of the operation, and DML might get blocked at the beginning for a short time and again at the end.

    /* create lexer and original index */
    exec ctx_ddl.create_preference('us_lexer','basic_lexer');
    create index idx on tbl(text) indextype is ctxsys.context
      parameters('lexer us_lexer');

    /* create a new lexer */
    begin
      ctx_ddl.create_preference('e_lexer','basic_lexer');
      ctx_ddl.set_attribute('e_lexer','base_letter','yes');
      ctx_ddl.create_preference('m_lexer','multi_lexer');
      ctx_ddl.add_sub_lexer('m_lexer','default','us_lexer');
      ctx_ddl.add_sub_lexer('m_lexer','e','e_lexer');
    end;
    /

    /* add new language column to the table for multi-lexer */
    alter table tbl add(lang varchar2(10) default 'us');

    /* recreate index online with the new multip-lexer */
    exec ctx_ddl.recreate_index_online('idx',
      'replace lexer m_lexer language column lang');

Example 8-6 Local Index Recreate with All-At-Once Swap

The following example creates a local partitioned index `idxp` with a basic lexer `us_lexer`. It has two index partitions `idx_p1` and `idx_p2`. It then recreates a local partitioned index `idxp` online with partition `idx_p1`, which will have a new storage preference `new_store`. The swapping of the partition metadata and index partition data occur at the end. In this example, queries spanning multiple partitions return consistent results across partitions when recreate is in process, except at the end when EXCHANGE_SHADOW_INDEX is running. The extra space required is the combined index size of partition `idx_p1` and `idx_p2`.

    /* create a basic lexer and a local partition index with the lexer*/
    exec ctx_ddl.create_preference('us_lexer','basic_lexer');
    create index idxp on tblp(text) indextype is ctxsys.context local
      (partition idx_p1,
       partition idx_p2)
     parameters('lexer us_lexer');

    /* create new preferences  */
    begin
      ctx_ddl.create_preference('my_store','basic_storage');
      ctx_ddl.set_attribute('my_store','i_table_clause','tablespace tbs');
    end;
    /
    begin
      ctx_ddl.create_preference('e_lexer','basic_lexer');
      ctx_ddl.set_attribute('e_lexer','base_letter','yes');
      ctx_ddl.create_preference('m_lexer','multi_lexer');
      ctx_ddl.add_sub_lexer('m_lexer','default','us_lexer');
      ctx_ddl.add_sub_lexer('m_lexer','e','e_lexer');
    end;
    /

    /* add new language column */
    alter table tblp add column (lang varchar2(10) default 'us');

    /* create a shadow policy with a new lexer */
    exec ctx_ddl.create_shadow_index('idxp', null,
      'replace lexer m_lexer language column lang');

    /* recreate every index partition online without swapping */
    exec ctx_ddl.recreate_index_online('idxp',
       'replace storage my_store NOSWAP', 1, 'idx_p1');
    exec ctx_ddl.recreate_index_online('idxp','replace NOSWAP',1,'idx_p2');

    /* exchange in shadow index partition all at once */
    exec ctx_ddl.exchange_shadow_index('idxp',
          'idx_p1') /* exchange index partition data*/
    exec ctx_ddl.exchange_shadow_index('idxp',
          'idx_p2') /* exchange index partition data*/

    /* exchange in shadow index metadata */
    exec ctx_ddl.exchange_shadow_index('idxp')

Example 8-7 Local Index Recreate with Per-Partition Swap

This example performs the same tasks as Example 8-6, except that each index partition is swapped in as it is completed. Queries across all partitions may return inconsistent results in this example.

    /* create a basic lexer and a local partition index with the lexer*/
    exec ctx_ddl.create_preference('us_lexer','basic_lexer');
    create index idxp on tblp(text) indextype is ctxsys.context local
      (partition idx_p1,
       partition idx_p2)
     parameters('lexer us_lexer');

    /* create new preferences  */
    begin
      ctx_ddl.create_preference('my_store','basic_storage');
      ctx_ddl.set_attribute('my_store','i_table_clause','tablespace tbs');
    end;
    /
    begin
      ctx_ddl.create_preference('e_lexer','basic_lexer');
      ctx_ddl.set_attribute('e_lexer','base_letter','yes');
      ctx_ddl.create_preference('m_lexer','multi_lexer');
      ctx_ddl.add_sub_lexer('m_lexer','default','us_lexer');
      ctx_ddl.add_sub_lexer('m_lexer','e','e_lexer');
    end;
    /

    /* add new language column */
    alter table tblp add column (lang varchar2(10) default 'us');

    /* create a shadow policy with a new lexer *
    exec ctx_ddl.create_shadow_index('idxp',
      'replace lexer m_lexer language column lang');

    /* recreate every index partition online and swap (default) */
    exec ctx_ddl.recreate_index_online('idxp',
           'replace storage my_store', 1, 'idx_p1');
    exec ctx_ddl.recreate_index_online('idxp', 'replace SWAP', 1, 'idx_p2',

        /* exchange in shadow index metadata */
    exec ctx_ddl.exchange_shadow_index('idxp')

Example 8-8 Scheduled Local Index Recreate with All-At-Once Swap

This example shows the incremental recreation of a local partitioned index, where partitions are all swapped at the end.

    /* create a basic lexer and a local partition index with the lexer*/
    exec ctx_ddl.create_preference('us_lexer','basic_lexer');
    create index idxp on tblp(text) indextype is ctxsys.context local
      (partition idx_p1,
       partition idx_p2)
     parameters('lexer us_lexer');

    /* create new preferences  */
    begin
      ctx_ddl.create_preference('my_store','basic_storage');
      ctx_ddl.set_attribute('my_store','i_table_clause','tablespace tbs');
    end;
    /
    begin
      ctx_ddl.create_preference('e_lexer','basic_lexer');
      ctx_ddl.set_attribute('e_lexer','base_letter','yes');
      ctx_ddl.create_preference('m_lexer','multi_lexer');
      ctx_ddl.add_sub_lexer('m_lexer','default','us_lexer');
      ctx_ddl.add_sub_lexer('m_lexer','e','e_lexer');
    end;
    /

    /* add new language column */
    alter table tblp add column (lang varchar2(10) default 'us');

    /* create a shadow policy with a new lexer *
    exec ctx_ddl.create_shadow_index('idxp',
      'replace lexer m_lexer language column lang');
    /* create shadow partition with new storage preference */
    exec ctx_ddl.recreate_index_online('idxp', 'replace storage ctxsys.default_storage nopopulate',1,'idx_p1');
    exec ctx_ddl.recreate_index_online('idxp', 'replace storage ctxsys.default_storage nopopulate',1,'idx_p2');

    declare
      idxid integer;
      ixpid integer;
    begin
      select idx_id into idxid from ctx_user_indexes
        where idx_name = 'IDXP';
      select ixp_id into ixpid from ctx_user_index_partitions
        where ixp_index_name = 'IDXP'
              and ixp_index_partition_name = 'IDX_P1';
      /* populate pending */
      ctx_ddl.populate_pending('RIO$'||idxid, 'RIO$'||idxid||'#'||ixpid);
      /* incremental sync
      ctx_ddl.sync_index('RIO$'||idxid, null, 'RIO$'||idxid||'#'||ixpid,
                          maxtime=>400);
      /* more incremental sync until no more pending rows */

      select ixp_id into ixpid from ctx_user_index_partitions
        where ixp_index_name = 'IDXP'
              and ixp_index_partition_name = 'IDX_P2';
      /* populate pending */
      ctx_ddl.populate_pending('RIO$'||idxid, 'RIO$'||idxid||'#'||ixpid);
      /* incremental sync
      ctx_ddl.sync_index('RIO$'||idxid, null, 'RIO$'||idxid||'#'||ixpid,
                          maxtime=>400);
      /* more incremental sync until no more pending rows */
    end;
    /

    exec ctx_ddl.exchange_shadow_index('idxp','idx_p1');
    exec ctx_ddl.exchange_shadow_index('idxp','idx_p2');
    exec ctx_ddl.exchange_shadow_index('idxp');

Example 8-9 Schedule Local Index Recreate with Per-Partition Swap

For incremental recreate where partitions are swapped as they becomes available, follow the steps in example Example 8-8, except instead of waiting until all syncs are finished before starting exchange shadow index, EXCHANGE_SHADOW_INDEX is done for each partition right after sync is finished.

#### Notes

- Using RECREATE_INDEX_ONLINE with Global Nonpartitioned Indexes:

  For global indexes, this procedure provides a one-step process to recreate an index online. It recreates an index, with new preference values, while preserving base table DML and query capability during the recreate process.

  Because the new index is created alongside the existing index, this operation requires additional storage roughly equal to the size of the existing index.

- DML Behavior:

  Because this procedure is performed online, DML on the base table are permitted during this operation, and are processed as normal. All DML statements that occur during `RECREATE_INDEX_ONLINE` are logged into an online pending queue.

  Towards the end of the recreate operation, there will be a short duration when DML will fail with an error being raised stating that the index is in an in-progress status. DML may stop responding again during the process, and the duration will depend on how many DML are logged in the online pending queue since the start of the recreate process.

  Note that after the recreate index operation is complete, new information, from all the DML that becomes pending since `RECREATE_INDEX_ONLINE` started, may not be immediately reflected. As with creating an index with `INDEXTYPE` `IS` `ctxsys.context` `ONLINE`, the index should be synchronized after the recreate index operation is complete, to bring it fully up-to-date.

- Sync and Optimize Behavior:

  Syncs issued against the index during the recreate operation are processed against the old, existing data. Syncs are also blocked during the same window when queries return errors.

  After running `RECREATE_INDEX_ONLINE`, you must call the `SYNC_INDEX` operation to synchronize any DML that occurs during the build of the shadow index. If you have specified `SYNC(ON COMMIT)` or `SYNC(EVERY)`, then the sync occurs automatically. However, if you have specified `SYNC(MANUAL)`, then you must manually invoke `SYNC_INDEX`.

  Optimize commands issued against the index during the recreate operation return immediately without error and without processing.

- Query Behavior:

  During the recreate operation, the index can be queried normally most of the time. Queries return results based on the existing index and policy (or metadata) until after the final swap.

  There is a short interval towards the end of `RECREATE_INDEX_ONLINE` when queries will return an error indicating that the column is not indexed. This duration should be short for regular queries. It is mainly the time taken for swapping data segments of the shadow index tables and the index tables, plus the time to delete all the rows in the pending queue. This is the same window of time when DML will fail.

  During `RECREATE_INDEX_ONLINE`, if you issue DML statements and synchronize them, then you will be able to see the new rows when you query on the existing index. However, after `RECREATE_INDEX_ONLINE` finishes (swapping completes and query is on the new index) and before sync is performed, it is possible that you will not be able to query on the new rows, which once could be queried on the old index.

  Transactional queries are not supported.

- Using RECREATE_INDEX_ONLINE with Local Partitioned Indexes:

  If the index is local partitioned, you cannot recreate index in one step. You must first create a shadow policy, and then run this procedure for every partition. You can specify `SWAP` or `NOSWAP` to indicate whether `RECREATE_INDEX_ONLINE` partition will swap the index partition data and index partition metadata or not. If the partition was built with `NOSWAP`, then another call to `EXCHANGE_SHADOW_INDEX` must be invoked later against this partition.

  This procedure can also be used to update the metadata (for example, storage preference) of each partition when you specify `NOPOPULATE` in the parameter string. This is useful for incremental building of a shadow index through time-limited sync.

  If `NOPOPULATE` is specified, then `NOSWAP` is silently enforced.

- NOSWAP Behavior:

  During the recreate of the index partition, since no swapping is performed, queries on the partition are processed regularly. Until the swapping stage is reached, queries spanning multiple partitions return consistent results across partitions.

  DML and sync are processed normally. Running optimize on partitions that are being recreated, or that have been built (but not swapped), simply returns without doing anything. Running optimize on a partition that has not been rebuilt processes normally.

  As with a global index, when all of the partitions use `NOSWAP`, the additional storage requirement is roughly equal to the size of the existing index.

- SWAP Behavior:

  Because index partition data and metadata are swapped after index recreate, queries that span multiple partitions will not return consistent results from partition to partition, but will always be correct with respect to each index partition. There is also a short interval towards the end of partition recreate, when the index partition is swapped, during which a query will return a "column not indexed" error.

  When partitions are recreated with `SWAP`, the additional storage requirement for the operation is equal to the size of the existing index partition.

  DML on the partition is blocked. Sync is also blocked during swapping.

- Restrictions:

  The `RECREATE_INDEX_ONLINE` and `CREATE_SHADOW_INDEX` procedures do not support section group with the `XML_ENABLE` attribute on `CONTEXT` indexes. Doing so results in the "`DRG-10521: Operation not supported with XML_ENABLE on a CONTEXT Index`" error.

  The `RECREATE_INDEX_ONLINE` and `CREATE_SHADOW_INDEX` procedures are not supported for search indexes.

**Related Topics**

- [CREATE INDEX](oracle-text-SQL-statements-and-operators.md)
- CREATE_SHADOW_INDEX
- EXCHANGE_SHADOW_INDEX
- DROP_SHADOW_INDEX
- [Oracle Text Application Developer's Guide](../ccapp/searching-document-sections-in-oracle-text.md)

### 8.37 REM_SEC_GRP_ATTR_VAL

Removes a specific section group attribute value from the list of values of an existing section group attribute.

#### Syntax

    CTX_DDL.REM_SEC_GRP_ATTR_VAL(group_name IN VARCHAR2,
                          attribute_name  IN VARCHAR2,
                          attribute_value IN VARCHAR2);

group_name
Specify the section group name.

attribute_name
Specify the name of the section group attribute.

attribute_value
Specify the section group attribute value.

### 8.38 REMOVE_AUTO_OPTIMIZE

Removes an index or partition from the list of indexes subject to auto optimization. No new auto optimization calls are made to this index. The removal takes effect immediately.

If the specified index is not in the existing list of indexes, then an error occurs. For partitioned indexes, an error occurs when the partition name is not specified.

#### Syntax

    CTX_DDL.REMOVE_AUTO_OPTIMIZE(

        idx_name       IN VARCHAR2,
        part_name      IN VARCHAR2 default NULL
    );

idx_name
Specify the name of the index to remove.

part_name
Specify the name of the partition to remove.

#### Related Topic

"ADD_AUTO_OPTIMIZE"

### 8.39 REMOVE_INDEX

Removes the index with the specified column list from a `CTXCAT` index set preference.

**Note:**

This procedure does not remove a `CTXCAT` sub-index from the existing index. To do so, you must drop your index and re-index with the modified index set preference.

#### Syntax

    CTX_DDL.REMOVE_INDEX(

        set_name       IN VARCHAR2,
        column_list    IN VARCHAR2
        language       IN VARCHAR2 default NULL
    );

set_name
Specify the name of the index set.

column_list
Specify the name of the column list to remove.

### 8.40 REMOVE_MDATA

Use this procedure to remove metadata values, which are associated with an `MDATA` section, from a document.

Only the owner of the index is allowed to call ADD_MDATA and `REMOVE_MDATA`.

`CTX_DDL.REMOVE_MDATA` is transactional and takes effect immediately in the calling session. This procedure can be seen only in the calling session and must be committed to take permanent effect. You can reverse this procedure with a `ROLLBACK` command.

#### Syntax

    CTX_DDL.REMOVE_MDATA(
         idx_name           IN VARCHAR2,
         section_name       IN VARCHAR2,
         values             SYS.ODCIVARCHAR2LIST,
         rowids             SYS.ODCIRIDLIST,
         [part_name]        IN VARCHAR2
    );

idx_name
Name of the text index that contains the named rowids.

section_name
Name of the `MDATA` section.

values
List of metadata values. If a metadata value contains a comma, the comma must be escaped with a backslash.

rowids
`Rowids` from which to remove the metadata values.

\[part_name\]
Name of the index partition, if any. Must be provided for local partitioned indexes and must be NULL for global, nonpartitioned indexes.

#### Example

This example removes the `MDATA` value blue from the `MDATA` section `BGCOLOR`.

    ctx_ddl.remove_mdata('idx_docs', 'bgcolor', 'blue', 'rows');

#### Notes

These updates are updates directly on the index itself, not on the actual contents stored in the base table. Therefore, they will not exist when the Text index is rebuilt.

#### Related Topics

"ADD_MDATA"

"ADD_MDATA_SECTION"

"[MDATA](oracle-text-CONTAINS-query-operators.md)"

The Section Searching chapter of [Oracle Text Application Developer's Guide](../ccapp/searching-document-sections-in-oracle-text.md)

### 8.41 REMOVE_SECTION

The `REMOVE_SECTION` procedure removes the specified section from the specified section group. You can specify the section by name or ID. View section ID with the `CTX_USER_SECTIONS` view.

#### Syntax 1

Use the following syntax to remove a section by section name:

    CTX_DDL.REMOVE_SECTION(
      group_name       IN    VARCHAR2,
      section_name     IN    VARCHAR2
    );

group_name
Specify the name of the section group from which to delete `section_name`.

section_name
Specify the name of the section to delete from `group_name`.

#### Syntax 2

Use the following syntax to remove a section by section ID:

    CTX_DDL.REMOVE_SECTION(
      group_name     IN    VARCHAR2,
      section_id     IN    NUMBER
    );

group_name
Specify the name of the section group from which to delete `section_id`.

section_id
Specify the section ID of the section to delete from `group_name`.

#### Example

The following example drops a section called `Title` from the `htmgroup`:

    begin
    ctx_ddl.remove_section('htmgroup', 'Title');
    end;

#### Related Topics

"ADD_FIELD_SECTION"

"ADD_SPECIAL_SECTION "

"ADD_ZONE_SECTION "

### 8.42 REMOVE_STOPCLASS

Removes a stopclass from a stoplist.

#### Syntax

    CTX_DDL.REMOVE_STOPCLASS(
      stoplist_name  IN   VARCHAR2,
      stopclass      IN   VARCHAR2
    );

stoplist_name
Specify the name of the stoplist.

stopclass
Specify the name of the stopclass to be removed.

#### Example

The following example removes the stopclass `NUMBERS` from the stoplist `mystop`.

    begin
    ctx_ddl.remove_stopclass('mystop', 'NUMBERS');
    end;

#### Related Topic

"ADD_STOPCLASS "

### 8.43 REMOVE_STOPTHEME

Removes a stoptheme from a stoplist.

#### Syntax

    CTX_DDL.REMOVE_STOPTHEME(
      stoplist_name   IN   VARCHAR2,
      stoptheme       IN   VARCHAR2
    );

stoplist_name
Specify the name of the stoplist.

stoptheme
Specify the stoptheme to be removed from `stoplist_name`.

#### Example

The following example removes the stoptheme banking from the stoplist `mystop`:

    begin
    ctx_ddl.remove_stoptheme('mystop', 'banking');
    end;

#### Related Topic

"ADD_STOPTHEME "

### 8.44 REMOVE_STOPWORD

Removes a stopword from a stoplist. To have the removal of a stopword be reflected in the index, you must rebuild your index. You can also remove a language-independent stopword.

#### Syntax

    CTX_DDL.REMOVE_STOPWORD(

    stoplist_name  IN   VARCHAR2,
    stopword       IN   VARCHAR2,
    language       IN   VARCHAR2 default NULL

    );

stoplist_name
Specify the name of the stoplist.

stopword
Specify the stopword to be removed from `stoplist_name`.

language
Specify the language of `stopword` to remove when the stoplist you specify with `stoplist_name` is of type `MULTI_STOPLIST`. You must specify the globalization support name or abbreviation of an Oracle Text-supported language. You can also remove `ALL` stopwords.

#### Example

The following example removes a stopword because from the stoplist `mystop`:

    begin

    ctx_ddl.remove_stopword('mystop','because');

    end;

#### Related Topic

"ADD_STOPWORD "

### 8.45 REMOVE_SUB_LEXER

Removes a sub-lexer from a multi-lexer preference. You cannot remove the lexer for `DEFAULT`. You can also remove a language-independent sub-lexer.

#### Syntax

    CTX_DDL.REMOVE_SUB_LEXER(

    lexer_name  IN   VARCHAR2,
    language    IN   VARCHAR2 default NULL

    );

lexer_name
Specify the name of the multi-lexer preference or language-independent sub-lexer.

language
Specify the language of the sub-lexer to remove. You must specify the globalization support name or abbreviation of an Oracle Text-supported language.

#### Example

The following example removes a sub-lexer german_lexer of language `german`:

    begin

    ctx_ddl.remove_sub_lexer('german_lexer','german');

    end;

#### Related Topic

"ADD_SUB_LEXER "

### 8.46 REPLACE_INDEX_METADATA

Use this procedure to replace metadata in local domain indexes at the global (index) level.

**Note:**

The `ALTER INDEX PARAMETERS` command performs the same function as this procedure and can replace more than just metadata. For that reason, using `ALTER INDEX PARAMETERS` is the preferred method of replacing metadata at the global (index) level and should be used in place of this procedure when possible. For more information, see "[ALTER INDEX PARAMETERS Syntax](oracle-text-SQL-statements-and-operators.md)".

`CTX_REPLACE_INDEX_METADATA` may be deprecated in a future release of Oracle Text.

#### Syntax

    CTX_DDL.REPLACE_INDEX_METADATA(
                          idx_name         IN VARCHAR2,
                          parameter_string IN VARCHAR2
    );

idx_name
Specify the name of the index whose metadata you want to replace.

parameter_string
Specify the parameter string to be passed to `ALTER INDEX`. This must begin with '`REPLACE METADATA`'.

#### Notes

`ALTER INDEX REBUILD PARAMETERS ('REPLACE METADATA')` does not work for a local partitioned index at the index (global) level. You cannot, for example, use that `ALTER INDEX` syntax to change a global preference, such as filter or lexer type, without rebuilding the index. Therefore, `CTX_DDL.REPLACE_INDEX_METADATA` is provided as a method of overcoming this limitation of `ALTER INDEX`. Also, `ALTER INDEX REBUILD PARAMETERS ('REPLACE METADATA')` does not work with forward_index; instead use `'REPLACE STORAGE'`.

Though it is meant as a way to replace metadata for a local partitioned index, `CTX_DDL.REPLACE_INDEX_METADATA` can be used on a global, nonpartitioned index, as well.

`REPLACE_INDEX_METADATA` cannot be used to change the sync type at the partition level; that is, parameter_string cannot be `'REPLACE METADATA SYNC'`. For that purpose, use `ALTER INDEX REBUILD PARTITION` to change the sync type at the partition level.

#### Related Topics

"[ALTER INDEX PARAMETERS Syntax](oracle-text-SQL-statements-and-operators.md)"

"[ALTER INDEX REBUILD Syntax](oracle-text-SQL-statements-and-operators.md)"

### 8.47 SET_ATTRIBUTE

Sets a preference attribute. Use this procedure after you have created a preference with `CTX_DDL.CREATE_PREFERENCE`.

#### Syntax

    CTX_DDL.SET_ATTRIBUTE(
                          preference_name IN VARCHAR2,
                          attribute_name  IN VARCHAR2,
                          attribute_value IN VARCHAR2
    );

preference_name
Specify the name of the preference.

**Note:**

Procedure names should not include the semicolon character.

attribute_name
Specify the name of the attribute.

attribute_value
Specify the attribute value. Specify boolean values as `TRUE` or `FALSE`, `T` or `F`, `YES` or `NO`, `Y` or `N`, `ON` or `OFF`, or `1` or `0`.

#### Examples

Example 8-10 Specifying File Data Storage

The following example creates a data storage preference called `filepref` that tells the system that the files to be indexed are stored in an Oracle directory object. The example then uses CTX_DDL.SET_ATTRIBUTE to set the `DIRECTORY` attribute to the directory `/docs`.

    begin
    ctx_ddl.create_preference('filepref', 'DIRECTORY_DATASTORE');
    ctx_ddl.set_attribute('filepref', 'DIRECTORY', '/docs');
    end;

Example 8-11 Storing Text Index Tables in the In-Memory Column Store

This example creates a storage preference called `mysto` of type `BASIC_STORAGE` that specifies that the `$I` index table must be stored in the In-Memory Column Store (IM column store).

    exec ctx_ddl.create_preference('mysto', 'basic_storage');
    exec ctx_ddl.set_attribute('mysto', 'I_TABLE_CLAUSE', 'inmemory’);

**Related Topics**

- CREATE_PREFERENCE
- [Datastore Types](oracle-text-indexing-elements.md)
- [BASIC_STORAGE](oracle-text-indexing-elements.md)

### 8.48 SET_SEC_GRP_ATTR

Adds a section group-specific attribute to a section group identified by name.

Also used to set `xml_enable` to support XML awareness.

#### Syntax

    CTX_DDL.SET_SEC_GRP_ATTR(
                          group_name      IN VARCHAR2,
                          attribute_name  IN VARCHAR2,
                          attribute_value IN VARCHAR2
    );

group_name
Specify the name of the section group.

attribute_name
Specify the name of the section group attribute.

attribute_value
Specify the section group attribute value. The following are the attributes with their supported values:

- `xml_enable`: Specify boolean values as `TRUE` or `FALSE`, `T` or `F`, `YES` or `NO`, `Y` or `N`, `ON` or `OFF`, or `1` or `0`.

#### Related Topics

"CREATE_SECTION_GROUP"

### 8.49 SET_SECTION_ATTRIBUTE

Use `SET_SECTION_ATTRIBUTE` to specify attributes or properties for a given section.

The attribute names listed under "Syntax" are supported. Note that some attributes only apply to sections that are tokenized. The following section types are tokenized:

- Field sections

- Zone sections

- SDATA sections

#### Syntax

    CTX_DDL.SET_SECTION_ATTRIBUTE(
                       group_name   IN VARCHAR2,
                       section_name IN VARCHAR2,
                       attribute    IN VARCHAR2,
                       value        IN VARCHAR2
     );

group_name
Specify the name of the section group.

section_name
Specify the name of the section.

attribute
Specify this attribute for SDATA sections:

- `Visible` section attribute

  This attribute works with FIELD sections only. For FIELD sections:

  Specify TRUE to make the text visible within the rest of the document. By default, the visible flag is FALSE. This means that Oracle Text indexes the text within field sections as a sub-document separate from the rest of the document. However, you can set the visible flag to TRUE if you want text within the field section to be indexed as part of the enclosing document.

  For field sections, attribute will override the value specified in CTX_DDL.ADD_FIELD_SECTION.

  An error is thrown if you try to set the `visible` attribute for a zone section.

  An error is thrown if the `visible` attribute is set on a non-tokenized section.

- `save_copy`. Set to True or False. The `save_copy` option is valid for all types of sections, but only SDATA attributes are fetched from \$D table. The rest of the sections are stored for display purposes only (depending on value of `save_copy`). SDATA sections are never stored for display purposes, but are stored independently (in a separate column of \$D table) for efficient fetching (depending on value of `save_copy`). For all sections (except for SDATA sections): A section is either displayed or discarded during document service procedures (snippet, markup, highlight) depending on the value of `save_copy`.

- `optimized_for` section attribute

  This attribute makes an SDATA section optimal for search, optimal for sort, or optimal for both search and sort. These are achieved by setting the attribute value to `search`, `sort`, or `sort_and_search`.

  - `search` provides efficient searching on SDATA sections.

  - `sort` provides efficient sorting on SDATA sections. This is the default value.

  - `sort_and_search` provides efficient searching and sorting on SDATA sections.

value
Specify the attribute value. Specify boolean values as `TRUE` or `FALSE`, `T` or `F`, `YES` or `NO`, `Y` or `N`, `ON` or `OFF`, or `1` or `0`.

#### Example

The following example creates a basic section group called `sg`, adds a SDATA section to it and marks that SDATA section to be searchable by using the `ctx_ddl.set_section_attribute`:

    begin
       exec ctx_ddl.create_section_group('sg', 'basic_section_group');
       exec ctx_ddl.add_sdata_section('sg', 'sec1', 'sec1', 'varchar2');
       exec ctx_ddl.set_section_attribute('sg', 'sec1', 'optimized_for', 'search');
    end;

#### Notes

Like CTX_DDL.SET_ATTRIBUTE, this procedure issues a commit.

#### Related Topic

See also the "Searching Document Sections in Oracle Text" chapter of [Oracle Text Application Developer's Guide](../ccapp/searching-document-sections-in-oracle-text.md).

### 8.50 SYNC_INDEX

Synchronizes the index to process inserts, updates, and deletes to the base table.

**Note:**

Because `CTX_DDL.SYNC_INDEX` issues implicit commits, calling `CTX_DDL.SYNC_INDEX` in a trigger is strongly discouraged. Doing so can result in errors being raised, as both `SYNC_INDEX` and post-commit `$R` `LOB` maintenance try to update the same `$R` `LOB`.

#### Syntax

    CTX_DDL.SYNC_INDEX(

    idx_name       IN  VARCHAR2 DEFAULT NULL
    memory          IN VARCHAR2 DEFAULT NULL,
    part_name       IN VARCHAR2 DEFAULT NULL,
    parallel_degree IN NUMBER DEFAULT 1
    maxtime         IN NUMBER DEFAULT NULL,
    locking         IN NUMBER DEFAULT LOCK_WAIT
    );

idx_name
Specify the name of the index to synchronize.

**Note:**

When `idx_name` is null, all `CONTEXT` and `CTXRULE` indexes that have pending changes are synchronized. You must be connected as `ctxsys` to perform this operation. Each index or index partition is synchronized in sequence, one after the other. Because of this, the individual syncs are performed with locking set to `NOWAIT` and maxtime set to `0`. Any values that you specify for locking or maxtime on the `SYNC_INDEX` call are ignored. However, the `memory` and `parallel_degree` parameters are passed on to the individual synchronizations.

memory
Specify the runtime memory to use for synchronization. This value overrides the `DEFAULT_INDEX_MEMORY` system parameter.

The memory parameter specifies the amount of memory Oracle Text uses for the synchronization operation before flushing the index to disk. Specifying a large amount of memory:

- Improves indexing performance because there is less I/O

- Improves query performance and maintenance because there is less fragmentation

- The indexing memory size specified in the second argument applies to each parallel slave. For example, if the `memory` argument is set to 500M and `parallel_degree` is set to 2, then ensure that there is at least 1GB of memory available on the system used for the parallel `SYNC_INDEX`.

Specifying smaller amounts of memory increases disk I/O and index fragmentation, but might be useful when runtime memory is scarce.

part_name
If your index is a local index, then you must specify the name of the index partition to synchronize otherwise an error is returned.

If your index is a global, nonpartitioned index, then specify NULL, which is the default.

parallel_degree
Specify the degree to run parallel synchronize. A number greater than 1 turns on parallel synchronize. The actual degree of parallelism might be smaller depending on your resources.

maxtime
Indicate a suggested time limit on the operation, in minutes. `SYNC_INDEX` will process as many documents in the queue as possible within the time limit. The `maxtime` value of NULL is equivalent to `CTX_DDL.MAXTIME_UNLIMITED`. This parameter is ignored when `SYNC_INDEX` is invoked without an index name, in which case `maxtime` value of 0 is used instead. The `locking` parameter is ignored for automatic syncs (that is, `SYNC` `ON` `COMMIT` or `SYNC` `EVERY`).

The time limit specified is treated as approximate. The actual time taken may be somewhat less than or greater than what you specify. The "time clock" for `maxtime` does not start until the SYNC lock is acquired.

locking
Configure how `SYNC_INDEX` deals with the situation where another sync is already running on the same index or index partition. When locking is ignored because `SYNC_INDEX` is invoked without an index name, then locking value of `LOCK_NOWAIT` is used instead. The `locking` parameter is ignored for automatic syncs (that is, `SYNC` `ON` `COMMIT` or `SYNC` `EVERY`).

The options for `locking` are:

| Locking Parameter           | Description                                                                                                                                                                                  |
|:----------------------------|:---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `CTX_DDL.LOCK_WAIT`         | If another sync is running, wait until the running sync is complete, then begin sync. (In the event of not being able to get a lock, it will wait forever and ignore the `maxtime` setting.) |
| `CTX_DDL.LOCK_NOWAIT`       | If another sync is running, immediately returns without error.                                                                                                                               |
| `CTX_DDL.LOCK_NOWAIT_ERROR` | If another sync is running, error "DRG-51313: timeout while waiting for DML or optimize lock" is raised.                                                                                     |

#### Example

The following example synchronizes the index `myindex` with 2 megabytes of memory:

    begin

    ctx_ddl.sync_index('myindex', '2M');

    end;

The following example synchronizes the `part1` index partition with 2 megabytes of memory:

    begin

    ctx_ddl.sync_index('myindex', '2M', 'part1');

    end;

#### Notes

- You can run `CTX_DDL.SYNC_INDEX` and `CTX_DDL.OPTIMIZE_INDEX` at the same time. You can also run `CTX_DDL.SYNC_INDEX` and `CTX_DDL.OPTIMIZE_INDEX` with parallelism at the same time. However, you should not run `CTX_DDL.SYNC_INDEX` with parallelism at the same time as `CTX_DDL.OPTIMIZE_INDEX`, nor `CTX_DDL.SYNC_INDEX` with parallelism at the same time as `CTX_DDL.OPTIMIZE_INDEX` with parallelism. If you should run one of these combinations, no error is generated; however, one operation will wait until the other is done.

- For indexes with a staging table (`$G`), `SYNC_INDEX` automatically merges data back from the staging table to the permanent index table (`$I`) when the threshold of rows inserted into the staging table exceeds the value of the `STAGE_ITAB_MAX_ROWS` setting and the `STAGE_ITAB_MAX_ROWS` is set to a value different than zero. The merge process uses a degree of parallelism of 4. Therefore, there is no need to explicitly run `CTX_DDL.OPTIMIZE_INDEX` in `MERGE` mode or to manually schedule a background job doing the same.

  If you want to submit a user-owned `DBMS_SCHEDULER` background job to run `CTX_DDL.OPTIMIZE_INDEX` in `MERGE` mode, then you must explicitly set the `STAGE_ITAB_MAX_ROWS` attribute to `0`. This turns off the automatic merge process that occurs during `SYNC_INDEX`. The user-submitted background job then periodically merges rows from `$G` to `$I`.

- You can set `STAGE_ITAB_AUTO_OPT` to enable automatic optimize merge. This setting automatically merges rows from `$G` to `$I` in the background.

  When `STAGE_ITAB_MAX_ROWS` is set to a value greater than `0` and the automatic optimize merge is not enabled using `STAGE_ITAB_AUTO_OPT`, some `SYNC` operations may take an unexpectedly long time to complete due to the merging of rows from `$G` to `$I`.

**Related Topics**

- [ALTER INDEX](oracle-text-SQL-statements-and-operators.md)

### 8.51 UNSET_ATTRIBUTE

Removes a set attribute from a preference.

#### Syntax

    CTX_DDL.UNSET_ATTRIBUTE(preference_name varchar2,
                            attribute_name  varchar2);

preference_name
Specify the name of the preference.

attribute_name
Specify the name of the attribute.

#### Example

Enabling/Disabling Alternate Spelling

The following example shows how you can enable alternate spelling for German and disable alternate spelling with `CTX_DDL.UNSET_ATTRIBUTE`:

    begin
    ctx_ddl.create_preference('GERMAN_LEX', 'BASIC_LEXER');
    ctx_ddl.set_attribute('GERMAN_LEX', 'ALTERNATE_SPELLING', 'GERMAN');
    end;

To disable alternate spelling, use the `CTX_DDL.UNSET_ATTRIBUTE` procedure as follows:

    begin
    ctx_ddl.unset_attribute('GERMAN_LEX', 'ALTERNATE_SPELLING');
    end;

#### Related Topics

"SET_ATTRIBUTE "

### 8.52 UNSET_SEC_GRP_ATTR

Removes a section group-specific attribute.

#### Syntax

    CTX_DDL.UNSET_SEC_GRP_ATTR(group_name varchar2,
                            attribute_name  varchar2);

group_name
Specify the name of the section group.

attribute_name
Specify the name of the attribute.

#### Related Topics

"UNSET_ATTRIBUTE "

### 8.53 UPDATE_SUB_LEXER

Updates a sub-lexer and modifies its multi-lexer preference, language, or sub-lexer. You can also update default sub-lexers using this procedure. This procedure can be used in conjunction with the `CTX_DDL.PREFERENCE_IMPLICIT_COMMIT` variable.

**See Also:**

"PREFERENCE_IMPLICIT_COMMIT" for information about setting this variable

#### Syntax

    UPDATE_SUB_LEXER (
          lexer_name     IN   VARCHAR2,
          language       IN   VARCHAR2,
          sub_lexer      IN   VARCHAR2
    );

lexer_name
Specify the name of the multi-lexer preference that needs to be updated.

language
Specify the language name of the sub-lexer. Use `DEFAULT` for the default sub-lexers.

See ""language"" for information on how to specify the globalization support language name or abbreviation of the sub-lexer.

sub_lexer
Specify the name of the sub-lexer to use for this language.

#### Related Topics

"ADD_SUB_LEXER "

"REMOVE_SUB_LEXER"

### 8.54 UPDATE_POLICY

Updates a policy created with `CREATE_POLICY`. Replaces the preferences of the policy. Null arguments are not replaced.

#### Syntax

    CTX_DDL.UPDATE_POLICY(
             policy_name     IN VARCHAR2,
             filter          IN VARCHAR2 DEFAULT NULL,
             section_group   IN VARCHAR2 DEFAULT NULL,
             lexer           IN VARCHAR2 DEFAULT NULL,
             stoplist        IN VARCHAR2 DEFAULT NULL,
             wordlist        IN VARCHAR2 DEFAULT NULL);

policy_name
Specify the name of the policy to update.

filter
Specify the filter preference to use.

section_group
Specify the section group to use.

lexer
Specify the lexer preference to use.

stoplist
Specify the stoplist to use.

wordlist
Specify the wordlist to use.

### 8.55 UPDATE_SDATA

`UPDATE_SDATA` is an index API that modifies the specified `SDATA` values in the index. It does not store or modify column values in a base table, where the base table column may have been used as an `SDATA` section.

Export/import operations rebuild the index from the base table using the specified preferences. Since modifications made using the `UPDATE_SDATA` API are not present in the base table, the export/import operation does not preserve these changes.

`UPDATE_SDATA` modifies temporary metadata it adds in the index table, not the base table. It cannot be used to directly add metadata. For export/import of metadata that is persistent, create a base table column that contains the metadata values. You can then update the metadata through the column in the base table.

`UPDATE_SDATA` truncates data which is larger than 249 bytes.

#### Syntax

    CTX_DDL.UPDATE_SDATA(
             idx_name     IN VARCHAR2 DEFAULT NULL,
             section_name IN VARCHAR2 DEFAULT NULL,
             sdata_value  IN sys.anydata,
             sdata_rowid  IN rowid,
             part_name    IN VARCHAR2 DEFAULT NULL);

idx_name
Specify the name of the index.

section_name
Specify the name of the `SDATA` section.

sdata_value
Specify the new `SDATA` value.

sdata_rowid
Specify the rowid for which the `SDATA` value needs to be updated.

part_name
Specify the name of the locally partitioned index, if applicable. Specify `NULL` for the global index.

#### Related Topics

"[SDATA](oracle-text-CONTAINS-query-operators.md)"

"ADD_SDATA_COLUMN"

"ADD_SDATA_SECTION"

**See Also:**

Chapter 8, "Searching Document Sections in Oracle Text" in [Oracle Text Application Developer's Guide](../ccapp/searching-document-sections-in-oracle-text.md)
