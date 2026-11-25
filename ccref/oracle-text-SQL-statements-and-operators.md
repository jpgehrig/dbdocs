## 1  Oracle Text SQL Statements and Operators

This chapter describes the SQL statements and Oracle Text operators for creating and managing Oracle Text indexes and performing Oracle Text queries.

The following statements are described in this chapter:

- ALTER INDEX

- ALTER TABLE: Supported Partitioning Statements

- CATSEARCH

- CONTAINS

- CREATE INDEX

- CREATE SEARCH INDEX

- DROP INDEX

- MATCHES

- MATCH_SCORE

- SCORE

### 1.1 ALTER INDEX

Use the `ALTER INDEX` statement to change or rebuild an existing Oracle Text index or JSON search index.

**Note:**

This section describes the `ALTER` `INDEX` statement as it pertains to managing an Oracle Text domain index. For a complete description of the `ALTER` `INDEX` statement, see [Oracle Database SQL Language Reference](../sqlrf/ALTER-INDEX.md).

#### ALTER INDEX Purpose

To make changes to or perform maintenance tasks for a `CONTEXT`, `CTXCAT`, or `CTXRULE` index.

**Note:**

- When you run any DML or query workload during `ALTER INDEX`, you might encounter an ORA-00060 or other error that may mark the index `UNUSABLE`. This is because `ALTER INDEX` behaves like a DDL operation and is not performed online by default. To overcome this error, set the `ONLINE` parameter in the `ALTER INDEX` statement.

- The `FAST_DML` and `FAST_QUERY` options are not supported for online operations.

All Index Types

Use `ALTER` `INDEX` to perform the following tasks on all Oracle Text index types:

- Rename the index or index partition. See ALTER INDEX RENAME Syntax.

- Rebuild the index using different preferences. Some restrictions apply for the `CTXCAT` index type. See ALTER INDEX REBUILD Syntax.

- Add stopwords to the index. See ALTER INDEX REBUILD Syntax.

- Add or remove a sub_lexer, and remove a stopword or set of stopwords for a given symbol (language or language-independent). See "ALTER INDEX Sub_Lexer Syntax"

CONTEXT and CTXRULE Index Types

Use `ALTER` `INDEX` to perform the following tasks on `CONTEXT` and `CTXRULE` index types:

- Resume a failed index operation (creation/optimization).

- Add sections and stop sections to the index.

- Replace index metadata.

  **See Also:**

  ALTER INDEX REBUILD Syntax to learn more about performing these tasks

#### Overview of ALTER INDEX Syntax

The syntax for `ALTER` `INDEX` is fairly complex. The major divisions are covered in the following sections:

- ALTER INDEX MODIFY PARTITION Syntax: Use this to modify an index partition's metadata.

- ALTER INDEX PARAMETERS Syntax: Use this to modify the parameters of a nonpartitioned index, or to modify all partitions of a local partitioned index, without rebuilding the index.

- ALTER INDEX RENAME Syntax: Use this to rename an index or index partition.

- ALTER INDEX REBUILD Syntax: Use this to rebuild an index or index partition. With this statement, you can also replace index metadata; add stopwords, sections, and stop sections to an index; and resume a failed operation.

  The parameters for `ALTER INDEX REBUILD` have their own syntax, which is a subset of the syntax for `ALTER` `INDEX`. For example, the `ALTER INDEX REBUILD PARAMETERS` statement can take either `REPLACE` or `RESUME` as an argument, and `ALTER INDEX REBUILD PARAMETERS ('REPLACE')` can take several arguments. Valid examples of `ALTER INDEX REBUILD` include the following statements:

      ALTER INDEX REBUILD PARALLEL n
      ALTER INDEX REBUILD PARAMETERS ('REPLACE DATASTORE datastore_pref')
      ALTER INDEX REBUILD PARAMETERS ('REPLACE WORDLIST wordlist_pref')

- ALTER INDEX Syntax for JSON Search Index: Use this to modify the JSON search index preferences, such as `DATAGUIDE` and `SEARCH_ON`.

#### ALTER INDEX MODIFY PARTITION Syntax

Use the following syntax to modify the metadata of an index partition:

    ALTER INDEX index_name MODIFY PARTITION partition_name PARAMETER (paramstring)

index_name
Specify the name of the index whose partition metadata you want to modify.

partition_name
Specify the name of the index partition whose metadata you want to modify.

paramstring
The only valid argument here is '`REPLACE METADATA`'. This follows the same syntax as `ALTER INDEX REBUILD PARTITION PARAMETERS ('REPLACE METADATA')`; see the `REPLACE METADATA` subsection of the "ALTER INDEX REBUILD Syntax" section for more information. (The two statements are equivalent. `ALTER INDEX MODIFY PARTITION` is offered for ease of use, and is the recommended syntax.)

#### ALTER INDEX PARAMETERS Syntax

The parameter string now supports READ ONLY MDATA. Use the following syntax to modify the parameters either of nonpartitioned or local partitioned indexes, without rebuilding the index. For partitioned indexes, this statement works at the index level, not at the partition level. This statement changes information for the entire index, including all partitions.

    ALTER INDEX index_name PARAMETERS (paramstring)

paramstring
`ALTER INDEX PARAMETERS` accepts the following arguments for paramstring:

- '`REPLACE METADATA`'

  Replaces current metadata. See the `REPLACE METADATA` subsection of the "ALTER INDEX REBUILD Syntax" section for more information.

- ‘`ADD MDATA SECTION secname TAG sectag READ ONLY`’

  Creates non-updatable MDATA sections so that queries on these MDATA sections do not require extra cursors to be opened on `$I` table.

- '`ADD STOPWORD`'

  Dynamically adds a stopword to an index. See the `ADD STOPWORD` subsection of the "ALTER INDEX REBUILD Syntax" section for more information.

- '`ADD FIELD SECTION`'

  Dynamically adds a field section to an index. See the `ADD FIELD` subsection of the "ALTER INDEX REBUILD Syntax" section for more information. You can add an unlimited number of field sections.

- '`ADD ZONE SECTION`'

  Dynamically adds a zone section to an index. See the `ADD ZONE` subsection of the "ALTER INDEX REBUILD Syntax" section for more information.

- '`ADD ATTR SECTION`'

  Dynamically adds an attribute section to an index. See the `ADD ATTR` subsection of the "ALTER INDEX REBUILD Syntax" section for more information.

- '`ADD SDATA SECTION`'

  Dynamically adds an `SDATA` section to an index. An `SDATA` section can only be added to `BASIC`, `HTML`, `XML`, and `NEWS` section groups. It supports both global as well as local indexes. New documents synchronized into the index reflect this new preference. The syntax is:

      ALTER INDEX index_name PARAMETERS (ADD SDATA SECTION sdata_section_name TAG sdata_section_tag DATATYPE sdata_section_datatype);

  The datatype can be `VARCHAR2`, `CHAR`, `NUMBER`, `DATE`, or `RAW`.

  See "Adding an SDATA Section" for more information.

  **Note:**

  Documents that were indexed before adding an `SDATA` section do not reflect this new preference. Rebuild the index in this case.

Each of the above described parameters has an equivalent `ALTER INDEX REBUILD PARAMETERS` version, except `ADD SDATA SECTION`.

For example, `ALTER INDEX PARAMETERS ('REPLACE METADATA')` is equivalent to `ALTER INDEX REBUILD PARAMETERS ('REPLACE METADATA')`. However, the `ALTER INDEX PARAMETERS` versions work on either partitioned or nonpartitioned indexes, whereas the `ALTER INDEX REBUILD PARAMETERS` versions work only on nonpartitioned indexes.

#### ALTER INDEX RENAME Syntax

Use the following syntax to rename an index or index partition:

    ALTER INDEX [schema.]index_name RENAME TO new_index_name;

    ALTER INDEX [schema.]index_name RENAME PARTITION part_name TO new_part_name;

\[schema.\]index_name
Specify the name of the index to rename.

new_index_name
Specify the new name for `schema.index.` The `new_index_name` parameter can be no more than 25 bytes, and 21 bytes for a partitioned index in earlier releases of Oracle Database that have not been upgraded to Oracle Database 12c Release 2 (12.2). If you specify a name longer than 25 bytes (or longer than 21 bytes for a partitioned index), then Oracle Text returns an error and the renamed index is no longer valid.

**Note:**

When `new_index_name` is more than 25 bytes (21 for local partitioned index) and less than 30 bytes, Oracle Text renames the index, even though the system returns an error. To drop the index and associated tables, you must drop `new_index_name` with the `DROP` `INDEX` statement and then re-create and drop `index_name`.

The upgraded databases that do not have the `compatible` parameter set to 12.2 can have the `new_index_name` parameter no more than 30 bytes, and 30 bytes for a partitioned index.

The upgraded databases that have the `compatible` parameter set to 12.2 or new Oracle Database 12c Release 2 (12.2) installations can have the `new_index_name` parameter no more than 128 bytes, and 128 bytes for a partitioned index.

part_name
Specify the name of the index partition to rename.

new_part_name
Specify the new name for partition.

#### ALTER INDEX REBUILD Syntax

Use `ALTER` `INDEX` `REBUILD` to rebuild an index, rebuild an index partition, resume a failed operation, replace index metadata, add stopwords to an index, or add sections and stop sections to an index.

The `ALTER` `INDEX` `REBUILD` syntax has its own subsyntax. That is, its parameters have their own syntax. For example, the `ALTER` `INDEX` `REBUILD` `PARAMETERS` statement can take either `REPLACE` or `RESUME` as an argument, and `ALTER` `INDEX` `REBUILD` `PARAMETERS` `('REPLACE')` has several arguments it can take.

**Note:**

You cannot use the `ALTER INDEX REBUILD` syntax to add or remove the `INMEMORY` option associated Text index tables.

Valid examples of `ALTER` `INDEX` `REBUILD` include the following statements:

    ALTER INDEX REBUILD PARALLEL n
    ALTER INDEX REBUILD PARAMETERS (REPLACE DATASTORE datastore_pref)
    ALTER INDEX REBUILD PARAMETERS (REPLACE WORDLIST wordlist_pref)

This is the syntax for `ALTER` `INDEX` `REBUILD`:

    ALTER INDEX [schema.]index [REBUILD] [PARTITION partname] [ONLINE] [PARAMETERS
    (paramstring)][PARALLEL N];

PARTITION partname
Rebuilds the index partition `partname`. Only one index partition can be built at a time.

When you rebuild a partition you can specify only `RESUME` or `REPLACE` in `paramstring`. These operations work only on the `partname` you specify.

With the `REPLACE` operation, you can specify `MEMORY`, `STORAGE`, and `SYNC` for each index partition.

Adding Partitions To add a partition to the base table, use the `ALTER` `TABLE` SQL statement. When you add a partition to an indexed table, Oracle Text automatically creates the metadata for the new index partition. The new index partition has the same name as the new table partition. If you must change the index partition name, then use `ALTER` `INDEX` `RENAME`.

Splitting or Merging Partitions Splitting or merging a table partition with `ALTER` `TABLE` renders the index partitions invalid. You must rebuild them with `ALTER` `INDEX` `REBUILD`.

ONLINE
Enables you to continue to perform updates, insertions, and deletions on a base table. It does not enable you to query the base table. The `ONLINE` keyword can only be used with the Enterprise Edition of Oracle Database.

**Note:**

You can specify `REPLACE` or `RESUME` when rebuilding an index or an index partition `ONLINE`.

PARAMETERS (paramstring)
Optionally, specify `paramstring`. If you do not specify `paramstring`, then Oracle Text rebuilds the index with existing preference settings.

**Note:**

Oracle Text rebuilds the index using metadata values that have been deep-copied into the index. You can use the `CTX_REPORT.CREATE_INDEX_SCRIPT` procedure to recreate the user preferences. This procedure generates a script with the preferences that are identical to those used in the original Text index. However, the names of the preferences will be system-generated.

The syntax for `paramstring` is as follows:

    paramstring =
    'REPLACE
         [DATASTORE datastore_pref]
         [FILTER filter_pref]
         [LEXER lexer_pref]
         [WORDLIST wordlist_pref]
         [STORAGE storage_pref]
         [STOPLIST stoplist]
         [SECTION GROUP section_group]
         [MEMORY memsize
         [[POPULATE | NOPOPULATE]
         [INDEX SET index_set]

            [METADATA preference new_preference]
         [METADATA FORMAT COLUMN format_column_name]
         [[METADATA] SYNC (MANUAL | EVERY "interval-string" | ON COMMIT)]
         [[METADATA] TRANSACTIONAL|NONTRANSACTIONAL
         [[METADATA] [ASYNCHRONOUS_UPDATE | SYNCHRONOUS_UPDATE]]

         [[METADATA] OPTIMIZE (MANUAL | AUTO_DAILY | EVERY "interval-string")]

    |[DATAGUIDE [ON | OFF | ON CHANGE [ADD_VC|Function_name]]
    |[SEARCH_ON TEXT_VALUE]
    | RESUME [memory memsize]
    | ADD STOPWORD word [language language]
    | ADD ZONE SECTION section_name tag tag
    | ADD FIELD SECTION section_name tag tag [(VISIBLE | INVISIBLE)]
    | ADD ATTR SECTION section_name tag tag@attr
    | ADD STOP SECTION tag'

REPLACE \[optional_preference_list\]
Rebuilds an index. You can optionally specify your own preferences, or system-defined preferences.

You can replace only the preferences that are supported for that index type. For instance, you cannot replace index set for a `CONTEXT` or `CTXRULE` index. Similarly, for the `CTXCAT` index type, you can replace lexer, wordlist, storage index set, and memory preferences.

The `POPULATE` parameter is the default and need not be specified. If you want to empty the index of its contents, then specify `NOPOPULATE`. Clear an index of its contents when you must rebuild your index incrementally. The `NOPOPULATE` choice is available for a specific partition of the index, and not just for the entire index.

Note that `ALTER INDEX REBUILD` creates a populated index by default, unless you explicitly specify the `NOPOPULATE` keyword. The outputs of `CTX_REPORT.CREATE_INDEX_SCRIPT` and `CTX_REPORT.DESCRIBE_INDEX` include the `NOPOPULATE` keyword for such indexes.

If you are rebuilding a partitioned index using the `REPLACE` parameter, then you can specify only `STORAGE`, `MEMORY`, and `NOPOPULATE`.

A new wordlist preference `SEPARATE_OFFSETS` specifies that the `token_info` in the index is stored as docids only in one place, and `offsets` is stored only in another place. Refer to [Oracle Text Application Developer's Guide](../ccapp/tuning-oracle-text.md) for information on improved response time using the SEPARATE_OFFSETS option of CONTEXT index.

**Note:**

If this procedure modifies the existing index tables for only the following storage attributes of the `BASIC_STORAGE` type (any one of them), then it will not result in re-indexing of data:

- `BIG_IO`

- `I_INDEX_CLAUSE`

- `I_TABLE_CLAUSE`

- `SEPARATE_OFFSETS`

REPLACE METADATA preference new_preference
Replaces the existing `preference` class settings, including `SYNC` parameters, of the index with the settings from `new_preference`. Only index preferences and attributes are replaced. The index is not rebuilt.

This statement is useful when you want to replace a preference and its attribute settings after the index is built, without re-indexing all data. re-indexing data can require significant time and computing resources.

This statement is also useful for changing the `SYNC` parameter type, which can be automatic, manual, or on-commit.

The `ALTER INDEX REBUILD PARAMETER ('REPLACE METADATA')` statement does not work for a local partitioned index at the global level for the index. You cannot, for example, use this syntax to change a global preference, such as filter or lexer type, without rebuilding the index. Use `ALTER INDEX PARAMETERS` instead to change the metadata of an index at the global level, including all partitions. See ALTER INDEX PARAMETERS Syntax.

**Note:**

The `ALTER INDEX REPLACE METADATA` option is essentially a DDL operation (and not an `ONLINE` operation), so it may fail if there are any concurrent DML operations requesting locks on the underlying table, including queries. You must perform `ALTER INDEX REPLACE METADATA` operations during a quiet time on the system when other user operations are not ongoing on the table or index.

When should I use the METADATA keyword? `REPLACE METADATA` should be used only when the change in index metadata will not lead to an inconsistent index, which can lead to incorrect query results.

For example, use this statement in the following instances:

- To go from a single-language lexer to a multilexer in anticipation of multilingual data. For an example, see Replacing Index Metadata: Changing Single-Lexer to Multilexer.

- To change the `WILDCARD_MAXTERMS` setting in [BASIC_WORDLIST](oracle-text-indexing-elements.md).

- To change the `SYNC` parameter type, which can be automatic, manual, or on-commit.

These changes are safe and will not lead to an inconsistent index that might adversely affect your query results.

**WARNING:**

The `REPLACE` `METADATA` statement can result in inconsistent index data, which can lead to incorrect query results. As such, Oracle does not recommend using this statement, unless you carefully consider the effect it will have on the consistency of your index data and subsequent queries.

There can be many instances when changing metadata can result in inconsistent index data. For example, Oracle recommends against using the `METADATA` keyword after performing the following procedures:

- Changing the [USER_DATASTORE](oracle-text-indexing-elements.md) procedure to a new PL/SQL stored procedure that has different output.

- Changing the [BASIC_WORDLIST](oracle-text-indexing-elements.md) attribute `PREFIX_INDEX` from `NO` to `YES` because no prefixes have been generated for existing documents. Changing it from `YES` to `NO` is safe.

- Adding or changing `BASIC_LEXER` printjoin and skipjoin characters, because new queries with these characters would be lexed differently from how these characters were lexed at index time.

- Do not use `REPLACE` `METADATA` with `FORWARD_INDEX`. Instead use `REPLACE` `STORAGE`.

In these unsafe cases, Oracle recommends rebuilding the index.

REPLACE \[METADATA\] SYNC (MANUAL \| EVERY "interval-string" \| ON COMMIT)
Specifies `SYNC` for synchronization of the `CONTEXT` index when a DML change has occurred to the base table. You can specify one of the `SYNC` methods shown in Table 1-1.

Table 1-1 ALTER INDEX SYNC Methods

| SYNC Type               | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         |
|:------------------------|:----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `MANUAL`                | Means no automatic synchronization. This is the default. You must manually synchronize the index using `CTX_DDL.SYNC_INDEX`.<br>Use `MANUAL` to disable `ON` `COMMIT` and `EVERY` synchronization.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  |
| `EVERY` interval-string | Automatically synchronize the index at a regular interval specified by the value of interval-string, which takes the same syntax as that for scheduler jobs. Automatic synchronization using `EVERY` requires that the index creator have `CREATE` `JOB` privileges.<br>Ensure that interval-string is set to a long enough period so that any previous synchronization jobs will have completed. Otherwise, the synchronization job may stop responding. The interval-string argument must be enclosed in double quotation marks ('' '').<br>See "Enabling Automatic Index Synchronization" for an example of automatic synchronization syntax.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    |
| `ON` `COMMIT`           | Synchronize the index immediately after a commit. The commit does not return until the sync is complete. Before Oracle Database Release 18c, the synchronization was performed as a separate transaction. There was a time period, usually small, when the data was committed but index changes were not. Starting with Oracle Database Release 18c, the synchronization is performed as part of the same transaction.<br>The operation uses the memory specified with the memory parameter.<br>Before Oracle Database Release 18c, the sync operation had its own transaction context. If the operation failed, the data transaction still committed. Starting with Oracle Database Release 18c, if there is an irrecoverable index synchronization error, the entire data transaction is rolled back. Recoverable (individual row) synchronization errors are logged in the `CTX_USER_INDEX_ERRORS` view but the transaction still completes. See "Viewing Index Errors" under `CREATE INDEX`.<br>`ON COMMIT` sync works best when the `STAGE_ITAB` index option is enabled, because otherwise it causes significant fragmentation of the main index, requiring frequent OPTIMIZE calls.<br>See "Enabling Automatic Index Synchronization" for an example of `ON` `COMMIT` syntax.<br>Refer to [Oracle Text Application Developer's Guide](../ccapp/tuning-oracle-text.md) for more information about the STAGE_ITAB option of the CONTEXT index. |

Each partition of a locally partitioned index can have its own type of sync: (`ON COMMIT`, `EVERY`, or `MANUAL`). The type of sync specified in primary parameter strings applies to all index partitions unless a partition specifies its own type.

With automatic (`EVERY`) synchronization, you can specify memory size and parallel synchronization. The syntax is:

    ... EVERY interval_string MEMORY mem_size PARALLEL paradegree ...

`ON` `COMMIT` synchronizations can only be executed serially and at the same memory size as what was specified at index creation.

**Note:**

This command rebuilds the index. When you want to change the `SYNC` setting without rebuilding the index, use the `REBUILD REPLACE METADATA SYNC (MANUAL | ON COMMIT)` operation.

REPLACE \[METADATA\] TRANSACTIONAL \| NONTRANSACTIONAL
This parameter enables you to turn the `TRANSACTIONAL` property on or off. For more information, see ""TRANSACTIONAL"".

Using this parameter only succeeds if there are no rows in the DML pending queue. Therefore, you may need to sync the index before issuing this command.

To turn on the `TRANSACTIONAL` index property:

    ALTER INDEX myidx REBUILD PARAMETERS('replace metadata transactional');

or

    ALTER INDEX myidx REBUILD PARAMETERS('replace  transactional');

To turn off the `TRANSACTIONAL` index property:

    ALTER INDEX myidx REBUILD PARAMETERS('replace metadata nontransactional');

or

    ALTER INDEX myidx REBUILD PARAMETERS('replace  nontransactional');

REPLACE \[METADATA\] \[ASYNCHRONOUS_UPDATE \| SYNCHRONOUS_UPDATE\]
When you update the column in a document on which an Oracle Text index is based, that document is marked as invalid for search operations until index synchronization is performed. Enabling asynchronous update for an index enables a document to be searchable even though its index has not yet been synchronized after the index column was updated. Until the index is synchronized, Oracle Text uses the contents of the old document to answer user queries.

To enable asynchronous update for a Text index:

    ALTER INDEX idx PARAMETERS ('REPLACE METADATA asynchronous_update');

To disable asynchronous update for a Text index:

    ALTER INDEX idx PARAMETERS ('REPLACE METADATA synchronous_update');

**Note:**

Synchronous update is not supported with the `TRANSACTIONAL` option and for updates that cause row movement.

REPLACE \[\[METADATA\] OPTIMIZE (MANUAL \| AUTO_DAILY \| EVERY "interval-string")\]
Specify `OPTIMIZE` to enable automatic background index optimization. You can specify any one of the following `OPTIMIZE` methods:

Table 1-2 ALTER INDEX OPTIMIZE TYPES

| OPTIMIZE Type           | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  |
|:------------------------|:---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| MANUAL                  | Provides no automatic optimization. You must manually optimize the index with `CTX_DDL.OPTIMIZE_INDEX`.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      |
| AUTO_DAILY              | When you specify `OPTIMIZE (AUTO_DAILY)` in the create index parameter list, a repeatedly running optimize token job and a repeatedly running optimize full job are scheduled.<br>• The Optimize token job is scheduled to run every midnight from 12 A.M. to 3 A.M. except on Saturday night, in order to optimize the top 10 most fragmented tokens (determined automatically). Jobs that are not started before 3 A.M. are skipped. These skipped jobs are started before the other jobs that are scheduled to run at 12 A.M. the next day.<br>• The Optimize full job is scheduled to run weekly from 12 A.M. every Saturday night in order to optimize index tables and clean up \$N.<br>Existing indexes do not have `OPTIMIZE (AUTO_DAILY)` by default. You must use `ALTER INDEX` to enable automatic background index optimization. |
| EVERY "interval-string" | Automatically runs optimize token for the top 10 most fragmented tokens at a regular interval specified by the value interval-string, which takes the same syntax as scheduler jobs.<br>Ensure that interval-string is set to a long enough period so that any previous optimize jobs are complete. The interval-string value must be enclosed in double quotes, and any single quote within interval-string must be preceded by an escape character with another single quote.                                                                                                                                                                                                                                                                                                                                                              |

With `AUTO_DAILY | EVERY "``interval-string``"` setting, you can specify parallel optimization. That syntax is:

    ... [AUTO_DAILY | EVERY "interval-string"] PARALLEL paradegree ...

RESUME \[MEMORY memsize\]
Resumes a failed index operation. You can optionally specify the amount of memory to use with `memsize`.

**Note:**

This `ALTER` `INDEX` operation applies only to `CONTEXT` and `CTXRULE` indexes. It does not apply to `CTXCAT` indexes.

ADD STOPWORD word \[language language\]
Dynamically adds a stopword word to the index.

Index entries for `word` that existed before this operation are not deleted. However, subsequent queries on `word` are treated as though it has always been a stopword.

When your stoplist is a multilanguage stoplist, you must specify `language`.

The index is not rebuilt by this statement.

ADD ZONE SECTION section_name tag tag
Dynamically adds the zone section `section_name` identified by `tag` to the existing index.

The added section `section_name` applies only to documents indexed after this operation. For the change to take effect, you must manually re-index any existing documents that contain the tag.

The index is not rebuilt by this statement.

**Note:**

This `ALTER` `INDEX` operation applies only to `CONTEXT` and `CTXRULE` indexes. It does not apply to `CTXCAT` indexes.

**See Also:**

"Notes"

ADD FIELD SECTION section_name tag tag \[(VISIBLE \| INVISIBLE)\]
Dynamically adds the field section `section_name` identified by `tag` to the existing index. There is no limit to the number of field sections that can be added.

Optionally specify `VISIBLE` to make the field sections visible. The default is `INVISIBLE`.

**See Also:**

CTX_DDL.[ADD_FIELD_SECTION](CTX_DDL-package.md) for more information on visible and invisible field sections

The added section `section_name` applies only to documents indexed after this operation. For the change to affect previously indexed documents, you must explicitly re-index the documents that contain the tag.

This statement does not rebuild the index.

**Note:**

This `ALTER` `INDEX` operation applies only to `CONTEXT` `CTXRULE` indexes. It does not apply to `CTXCAT` indexes.

**See Also:**

"Notes"

ADD ATTR SECTION section_name tag tag@attr
Dynamically adds an attribute section `section_name` to the existing index. You must specify the XML tag and attribute in the form `tag@attr`. You can add attribute sections only to XML section groups.

The added attribute section `section_name` applies only to documents indexed after this operation. For the change to take effect, you must manually re-index any existing documents that contain the tag.

The index is not rebuilt by this statement.

**Note:**

This `ALTER` `INDEX` operation applies only to `CONTEXT` `CTXRULE` indexes. It does not apply to `CTXCAT` indexes.

**See Also:**

"Notes"

ADD STOP SECTION tag
Dynamically adds the stop section identified by `tag` to the existing index. As stop sections apply only to automatic sectioning of XML documents, the index must use the `AUTO_SECTION_GROUP` section group. The tag you specify must be case sensitive and unique within the automatic section group or else `ALTER` `INDEX` raises an error.

The added stop section `tag` applies only to documents indexed after this operation. For the change to affect previously indexed documents, you must explicitly re-index the documents that contain the tag.

The text within a stop section can always be searched.

The number of stop sections you can add is unlimited.

The index is not rebuilt by this statement.

**See Also:**

"Notes"

**Note:**

This `ALTER` `INDEX` operation applies only to `CONTEXT` indexes. It does not apply to `CTXCAT` indexes.

PARALLEL n
Using n, you can optionally specify the parallel degree for parallel indexing. This parameter is supported only when you use `SYNC`, `REPLACE`, and `RESUME` `in paramstring`. The actual degree of parallelism might be smaller depending on your resources.

Parallel indexing can speed up indexing when you have large amounts of data to index and when your operating system supports multiple CPUs.

#### ALTER INDEX Syntax for JSON Search Index

    ALTER INDEX [schema.]index REBUILD
    PARAMETERS(
      [DATAGUIDE ON [CHANGE (ADD_VC | function_name)] | OFF]
      [SEARCH_ON (NONE | TEXT | TEXT_VALUE)]
      );

**Note:**

The `REPLACE` keyword is not required with the `ALTER INDEX REBUILD PARAMETERS` statement for changing the JSON search index preferences. Also, you cannot change both the JSON and Oracle Text search index preferences in a single `ALTER INDEX` statement.

If you specify the JSON search index preferences (such as `DATAGUIDE` and `SEARCH_ON`), other preferences in the `PARAMETERS` clause are not updated. Similarly, if you specify the Oracle Text search index preferences (such as `STORAGE` and `LEXER`), the JSON preferences are not updated.

\[schema.\]index
Modifies the JSON search index name.

DATAGUIDE ON \| OFF
Modifies data guide support for an existing JSON search index. If you enable the JSON data guide support, then you can also define change-trigger procedures.

**Note:**

You use the `DATAGUIDE` clause only for JSON search indexes.

Specify one of the following options:

- `ON`: Enables data guide support. Also, allows you to define your own PL/SQL procedure or use the predefined change-trigger procedure `add_vc`.

- `OFF`: Disables both the data guide support and change-trigger procedures. Provides only general search-index functionality.

  **Note:**

  You cannot turn off the `DATAGUIDE` clause if the value of `SEARCH_ON` clause is set to `NONE`.

See "[Change Triggers For Data Guide-Enabled Search Index](../adjsn/json-dataguide.md)" in Oracle Database JSON Developer's Guide.

SEARCH_ON (TEXT \| TEXT_VALUE)
Modifies search preferences specified for JSON search index. Enabling a search option rebuilds the index with updated preferences.

**Note:**

You use the `SEARCH_ON` clause only for JSON search indexes.

Specify one of the following options:

- `TEXT`: Indicates that full-text search queries use the search index.

- `TEXT_VALUE`: Indicates that both the full-text and range-based indexes are created for numeric and date-time values.

Specifying `TEXT_VALUE` has a higher cost in indexing time and index space.

In the `SEARCH_ON` clause, specify a value as described in "Table 1-3".

Table 1-3 SEARCH_ON: Parameter Values

| Current Parameter Value | Supported New Parameter Value |
|:------------------------|:------------------------------|
| `NONE`                  | `TEXT`<br>`TEXT_VALUE`        |
| `TEXT`                  | `TEXT_VALUE`                  |

For example, you can change the `SEARCH_ON` parameter value from `NONE` to `TEXT` or from `TEXT` to `TEXT_VALUE` but not from `TEXT_VALUE` to `TEXT` or from `TEXT` to `NONE`.

**Note:**

You must specify the `SEARCH_ON` preferences as described in "Table 1-3". Otherwise, an error is returned while rebuilding the index.

To change the `SEARCH_ON` parameter value to any of the unsupported values (that is, from `TEXT_VALUE` to `TEXT` or from `TEXT` to `NONE`), you must first drop the index using the `DROP INDEX` statement and then recreate the index using the `CREATE SEARCH INDEX` statement.

#### ALTER INDEX Sub_Lexer Syntax

Use the following syntax.

**See Also:**

"ALTER INDEX Purpose" for list of types of indexes and syntax for ALTER INDEX

    New paramstring =
    'REPLACE
         [DATASTORE datastore_pref]
         [FILTER filter_pref]
         [LEXER lexer_pref]
         [WORDLIST wordlist_pref]
         [STORAGE storage_pref]
         [STOPLIST stoplist]
         [SECTION GROUP section_group]
         [MEMORY memsize
         [[POPULATE | NOPOPULATE]
         [INDEX SET index_set]

         [METADATA preference new_preference]
         [[METADATA] SYNC (MANUAL | EVERY "interval-string" | ON COMMIT)]
         [[METADATA] TRANSACTIONAL|NONTRANSACTIONAL

    | RESUME [memory memsize]
    | OPTIMIZE [token index_token | fast | full [maxtime (time | unlimited)]
    | SYNC [memory memsize]
    | ADD STOPWORD word [language language][LANGUAGE_DEPENDENT(TRUE|FALSE)]
    | ADD ZONE SECTION section_name tag tag
    | ADD FIELD SECTION section_name tag tag [(VISIBLE | INVISIBLE)]
    | ADD ATTR SECTION section_name tag tag@attr
    | ADD STOP SECTION tag
    | ADD SUB_LEXER sub_lexer_name LANGUAGE language [ALT_VALUE alternate_value_for_language] [LANGUAGE_DEPENDENT (TRUE|FALSE)]
    | REMOVE SUB_LEXER LANGUAGE language
    | REMOVE STOPWORD word [LANGUAGE language]
    | REMOVE STOPWORDS FOR LANGUAGE language
    | MIGRATE to MULTI_STOPLIST [LANGUAGE COLUMN lang]
    | MIGRATE FIELD SECTION field_section_name to [READ ONLY] MDATA
    | UPDATE SUB_LEXER LANGUAGE language TO sub_lexer_preference
    | ADD MDATA SECTION secname TAG sectag READ ONLY

Sub_Lexer Example

    ALTER INDEX myidx PARAMETERS('ADD SUB_LEXER mycompany_lexer LANGUAGE mycompany LANGUAGE_DEPENDENT FALSE');

    ALTER INDEX myidx PARAMETERS('REMOVE STOPWORDS FOR LANGUAGE mycompany');

Sub_Lexer Notes

The language can be Oracle predefined language symbols (globalization support name or abbreviation of an Oracle Text-supported language), or user-defined symbols for language independent sub_lexer or stopword.

ADD SUB_LEXER
The following conditions apply:

- If LANGUAGE_DEPENDENT clause is not provided, it will default TRUE.

- Sync will be blocked (or it will be blocked by sync).

- If adding first language independent sub_lexer, then base table will also be locked.

- Adding first language independent sub_lexer or stopword will take longer to complete. Otherwise, it should take fraction of a second to complete unless it's being blocked by ongoing sync process on the same index.

<!-- -->

REMOVE SUB_LEXER
Will succeed only if there are no documents with language column set to the symbol for the sub_lexer being removed.

<!-- -->

REMOVE STOPWORD
The following conditions apply:

- If LANGUAGE clause is not specified, it is assumed that the index is using basic_stoplist. If the index is not using basic_stoplist, an error will be raised.

- If the index is using basic_stoplist (instead of multi_stoplist), then it will succeed only if the base table is empty.

- If the index is using multi_stoplist, and user specifies "ALL" for LANGUAGE clause, then it will succeed only if the base table is empty.

- If the index is using multi_stoplist, and user specifies a symbol for LANGUAGE clause, then it will succeed only if there are no documents with language column set to the symbol for the stopword being removed.

**See Also:**

"ALTER INDEX REBUILD Syntax"

<!-- -->

MIGRATE TO MULTI_STOPLIST \[LANGUAGE COLUMN lang\]
The following conditions apply:

- Migrate the stoplist of an existing Text index to Multi_stoplist. The language of the existing stopwords will have the value of ALL.

- If `LANGUAGE` column has already been defined for the index:

  - `LANGUAGE` `COLUMN` can be skipped (old language column is retained for the index).

  - If `LANGUAGE` `COLUMN` is specified and there is a mismatch between index language column and the one specified, an error will be raised.

- `LANGUAGE` `COLUMN` must be specified for the index; otherwise, an error is raised.

MIGRATE FIELD SECTION TO MDATA SECTION
The following conditions apply:

- Allow user to convert a field section to MDATA section. Specify READ ONLY if the MDATA section is meant to be a READ_ONLY MDATA section (ADD and REMOVE not allowed).

- Limitation: Tokens in migrated MDATA sections will not have typical MDATA characteristics - case information, tokens being stored as it is in the document, etc. To retain these, those documents need to be reindexed.

<!-- -->

UPDATE SUB_LEXER LANGUAGE SUB_LEXER_SYMBOL TO SUB_LEXER_PREFERENCE
The following conditions apply:

- Allows user to update sublexer dynamically.

- Language, alt_value, language dependency should remain same for the old and new sublexer preference.

- For updating the default sublexer, the syntax is:

      UPDATE SUB_LEXER DEFAULT TO SUB_LEXER_PREFERENCE

<!-- -->

ADD MDATA SECTION secname TAG sectag READ ONLY
The following conditions apply:

- Allows users to add MDATA section to the index.

- Cannot be used with NULL/AUTO/PATH section groups.

#### ALTER INDEX Examples

Resuming Failed Index

The following statement resumes the indexing operation on `newsindex`with 2 megabytes of memory:

    ALTER INDEX newsindex REBUILD PARAMETERS('resume memory 2M');

Rebuilding an Index

The following statement rebuilds the index, replacing the stoplist preference with `new_stop`.

    ALTER INDEX newsindex REBUILD PARAMETERS('replace stoplist new_stop');

Rebuilding a Partitioned Index

The following example creates a partitioned text table, populates it, and creates a partitioned index. It then adds a new partition to the table and rebuilds the index with `ALTER` `INDEX` as follows:

    PROMPT create partitioned table and populate it

    create table part_tab (a int, b varchar2(40)) partition by range(a)
    (partition p_tab1 values less than (10),
     partition p_tab2 values less than (20),
     partition p_tab3 values less than (30));

    insert into part_tab values (1,'Actinidia deliciosa');
    insert into part_tab values (8,'Distictis buccinatoria');
    insert into part_tab values (12,'Actinidia quinata');
    insert into part_tab values (18,'Distictis Rivers');
    insert into part_tab values (21,'pandorea jasminoides');
    insert into part_tab values (28,'pandorea rosea');

    commit;

    PROMPT create partitioned index
    create index part_idx on part_tab(b) indextype is ctxsys.context
    local (partition p_idx1, partition p_idx2, partition p_idx3);

    PROMPT add a partition and populate it
    alter table part_tab add partition p_tab4 values less than (40);
    insert into part_tab values (32, 'passiflora citrina');
    insert into part_tab values (33, 'passiflora alatocaerulea');
    commit;

The following statement rebuilds the index in the newly populated partition. In general, the index partition name for a newly added partition is the same as the table partition name, unless the name has already been used. In this case, Oracle Text generates a new name.

    alter index part_idx rebuild partition p_tab4;

The following statement queries the table for the two hits in the newly added partition:

    select * from part_tab where contains(b,'passiflora') >0;

The following statement queries the newly added partition directly:

    select * from part_tab partition (p_tab4) where contains(b,'passiflora') >;

Replacing Index Metadata: Changing Single-Lexer to Multilexer

The following example demonstrates how an application can migrate from single-language documents (English) to multilanguage documents (English and Spanish) by replacing the index metadata for the lexer.

    REM creates a simple table, which stores only English (American) text

    create table simple (text varchar2(80));
    insert into simple values ('the quick brown fox');
    commit;

    REM create a simple lexer to lex this English text

    begin
      ctx_ddl.create_preference('us_lexer','basic_lexer');
    end;
    /

    REM create a text index on the simple table
    create index simple_idx on simple(text)
    indextype is ctxsys.context parameters ('lexer us_lexer');

    REM we can query easily
    select * from simple where contains(text, 'fox')>0;

    REM now suppose we want to start accepting Spanish documents.
    REM first we have to extend the table with a language column
    alter table simple add (lang varchar2(10) default 'us');

    REM now let's create a Spanish lexer,
    begin
      ctx_ddl.create_preference('e_lexer','basic_lexer');
      ctx_ddl.set_attribute('e_lexer','base_letter','yes');
    end;
    /
    REM Then create a multilexer incorporating our English and Spanish lexers.
    REM Note that the DEFAULT lexer is the exact same lexer, with which we have
    REM have already indexed all the documents.
    begin
      ctx_ddl.create_preference('m_lexer','multi_lexer');
      ctx_ddl.add_sub_lexer('m_lexer','default','us_lexer');
      ctx_ddl.add_sub_lexer('m_lexer','spanish','e_lexer');
    end;
    /
    REM next replace our metadata
    alter index simple_idx rebuild
    parameters ('replace metadata language column lang lexer m_lexer');

    REM We are ready for some Spanish data.  Note that we could have inserted
    REM this BEFORE the alter index, as long as we did not SYNC.
    insert into simple values ('el zorro marr&oacute;n r&aacute;pido', 'e');
    commit;
    exec ctx_ddl.sync_index('simple_idx');
    REM now query the Spanish data with base lettering:
    select * from simple where contains(text, 'rapido')>0;

Optimizing the Index

To optimize your index, use CTX_DDL.[OPTIMIZE_INDEX](CTX_DDL-package.md).

Synchronizing the Index

To synchronize your index, use CTX_DDL.[SYNC_INDEX](CTX_DDL-package.md).

Adding a Zone Section

To add to the index the zone section `author` identified by the tag \<`author>`, enter the following statement:

    ALTER INDEX myindex REBUILD PARAMETERS('add zone section author tag author');

Adding a Stop Section

To add a stop section identified by tag \<`fluff>` to the index that uses the `AUTO_SECTION_GROUP`, enter the following statement:

    ALTER INDEX myindex REBUILD PARAMETERS('add stop section fluff');

Adding an Attribute Section

Assume that the following text appears in an XML document:

    <book title="Tale of Two Cities">It was the best of times.</book>

Assume also that you want to create a separate section for the title attribute and you want to name the new attribute section `booktitle`. To do so, enter the following statement:

    ALTER INDEX myindex REBUILD PARAMETERS('add attr section booktitle tag
    title@book');

Adding an SDATA Section

To add an SDATA section `S1` of `NUMBER` data type and identified by tag `T1`, to the index, enter the following statement:

    ALTER INDEX myindex PARAMETERS('add sdata section S1 tag T1 datatype NUMBER);

Disabling Automatic Background Index Optimization

The following example disables optimize token and optimize full jobs which are automatically running in the background:

    ALTER INDEX myindex PARAMETERS ('REPLACE METADATA OPTIMIZE (MANUAL)');

Using Flashback Queries

If a Text query is flashed back to a point before an `ALTER` `INDEX` statement was issued on the Text index for which the query is being run, then:

- The query optimizer will not choose the index access path for that given index because the index is treated according to its creation time with `ALTER` `INDEX`. Therefore, to the query optimizer, the index is perceived not to exist.

- The functional processing of the Text operator will fail with ORA-01466 or ORA-08176 errors if the `ALTER` `INDEX` statement involves re-creation of `DR$` index tables.

To work around this issue, use the `DBMS_FLASHBACK` package. For example:

    EXEC dbms_flashback.enable_at_system_change_number(:scn);
    SELECT id from documents WHERE CONTAINS(text, 'oracle')>0;
    EXEC dbms_flashback.disable;

**See Also:**

"[Using DBMS_FLASHBACK Package](../adfns/flashback.md)" in Oracle Database Development Guide

#### Notes

Add Section Constraints

Before altering the index section information, Oracle Text checks the new section against the existing sections to ensure that all validity constraints are met. These constraints are the same for adding a section to a section group with the `CTX_DDL` PL/SQL package and are as follows:

- You cannot add zone, field, or stop sections to a `NULL_SECTION_GROUP`.

- You cannot add zone, field, or attribute sections to an automatic section group.

- You cannot add attribute sections to anything other than XML section groups.

- You cannot have the same tag for two different sections.

- Section names for zone, field, and attribute sections cannot intersect.

- You cannot exceed 64 fields per section.

- You cannot add stop sections to basic, HTML, XML, or news section groups.

- `SENTENCE` and `PARAGRAPH` are reserved section names.

- You cannot have embedded blanks in section and field names.

**Related Topics**

- [Oracle Text Indexing Elements](oracle-text-indexing-elements.md)
- CREATE INDEX
- ALTER INDEX
- [OPTIMIZE_INDEX](CTX_DDL-package.md)

### 1.2 ALTER TABLE: Supported Partitioning Statements

**Note:**

This section describes the `ALTER` `TABLE` statement as it pertains to adding and modifying a partitioned text table with a context domain index.

For a complete description of the `ALTER` `TABLE` statement, see [Oracle Database SQL Language Reference.](../sqlrf/ALTER-TABLE.md)

#### Purpose

Use the `ALTER` `TABLE` statement to add, modify, split, merge, exchange, or drop a partitioned text table with a context domain index. The following sections describe some of the `ALTER` `TABLE` operations.

#### Modify Partition Syntax

Unusable Local Indexes

    ALTER TABLE  [schema.]table MODIFY PARTITION partition UNUSABLE LOCAL INDEXES

Marks the index partition corresponding to the given table partition `UNUSABLE`. You might mark an index partition unusable before you rebuild the index partition as described in "Rebuild Unusable Local Indexes".

If the index partition is not marked unusable, then the statement returns without actually rebuilding the local index partition.

Rebuild Unusable Local Indexes

    ALTER TABLE  [schema.]table MODIFY PARTITION partition REBUILD UNUSABLE LOCAL
    INDEXES

Rebuilds the index partition corresponding to the specified table partition that has an `UNUSABLE` status.

**Note:**

If the index partition status is already `VALID` before you enter this statement, then this statement does not rebuild the index partition. Do not depend on this statement to rebuild the index partition unless the index partition status is `UNUSABLE`.

#### Add Partition Syntax

    ALTER TABLE [schema.]table ADD PARTITION [partition]
    VALUES LESS THAN (value_list) [partition_description]

Adds a new partition to the high end of a range-partitioned table.

To add a partition to the beginning or to the middle of the table, use the `ALTER TABLE SPLIT PARTITION` statement.

The newly added table partition is always empty, and the context domain index (if any) status for this partition is always `VALID`. After issuing DML, if you want to synchronize or optimize this newly added index partition, then you must look up the index partition name and enter the `ALTER` `INDEX` `REBUILD` `PARTITION` statement. For this newly added partition, the index partition name is usually the same as the table partition name, but if the table partition name is already used by another index partition, the system assigns a name in the form of `SYS_Pn`.

By querying the `USER_IND_PARTITIONS` view and comparing the `HIGH_VALUE` field, you can determine the index partition name for the newly added partition.

#### Merge Partition Syntax

    ALTER TABLE [schema.]table
    MERGE PARTITIONS partition1, partition2
    [INTO PARTITION [new_partition] [partition_description]]
    [UPDATE GLOBAL INDEXES]

Applies only to a range partition. This statement merges the contents of two adjacent partitions into a new partition and then drops the original two partitions. If the resulting partition is non-empty, then the corresponding local domain index partition is marked `UNUSABLE`. You can use `ALTER TABLE MODIFY PARTITION` to rebuild the partition index.

For a global, nonpartitioned index, if you perform the merge operation without an `UPDATE GLOBAL INDEXES` clause, then the resulting index (if not `NULL`) will be invalid and must be rebuilt. If you specify the `UPDATE GLOBAL INDEXES` clause after the operation and the `SYNC` type is `MANUAL`, then the index will be valid, but you still must synchronize the index with CTX_DDL.[SYNC_INDEX](CTX_DDL-package.md) for the update to take place.

The naming convention for the resulting index partition is the same as in the `ALTER TABLE ADD PARTITION` statement.

#### Split Partition Syntax

    ALTER TABLE [schema.]table
    SPLIT PARTITION partition_name_old
    AT (value_list)
    [into (partition_description, partition_description)]
    [parallel_clause]
    [UPDATE GLOBAL INDEXES]

Applies only to range partitions. This statement divides a table partition into two partitions, thus adding a new partition to the table. The local corresponding index partitions will be marked `UNUSABLE` if the corresponding table partitions are non-empty. Use the `ALTER TABLE MODIFY PARTITION` statement to rebuild the partition indexes.

For a global, nonpartitioned index, if you perform the split operation without an `UPDATE GLOBAL INDEXES` clause, then the resulting index (if not `NULL`) will be invalid and must be rebuilt. If you specify the `UPDATE GLOBAL INDEXES` clause after the operation and the `SYNC` type is `MANUAL`, then the index will be valid, but you still must synchronize the index with CTX_DDL.[SYNC_INDEX](CTX_DDL-package.md) for the update to take place.

The naming convention for the two resulting index partition is the same as in the `ALTER TABLE ADD PARTITION` statement.

#### Exchange Partition Syntax

    ALTER TABLE [schema.]table EXCHANGE PARTITION partition WITH TABLE table
    [INCLUDING|EXCLUDING INDEXES}
    [WITH|WITHOUT VALIDATION]
    [EXCEPTIONS INTO [schema.]table]
    [UPDATE GLOBAL INDEXES]

Converts a partition to a nonpartitioned table, and converts a table to a partition of a partitioned table by exchanging their data segments. Rowids are preserved.

If `EXCLUDING INDEXES` is specified, all the context indexes corresponding to the partition and all the indexes on the exchanged table are marked as `UNUSABLE`. To rebuild the new index partition in this case, issue an `ALTER TABLE MODIFY PARTITION` statement.

If `INCLUDING INDEXES` is specified, then for every local domain index on the partitioned table, there must be a nonpartitioned domain index on the nonpartitioned table. The local index partitions are exchanged with the corresponding regular indexes.

For a global, nonpartitioned index, if you perform the exchange operation without an `UPDATE GLOBAL INDEXES` clause, then the resulting index (if not `NULL`) will be invalid and must be rebuilt. If you specify the `UPDATE GLOBAL INDEXES` clause after the operation and the `SYNC` type is `MANUAL`, then the index will be valid, but you still must synchronize the index with CTX_DDL.[SYNC_INDEX](CTX_DDL-package.md) for the update to take place.

Field Sections

Field section queries might not work the same way if the nonpartitioned index and local index use different section IDs for the same field section.

Storage

Storage is not changed. So if the index on the nonpartitioned table `$I` table was in tablespace XYZ, then after the exchange partition, it will still be in tablespace XYZ, but now it is the `$I` table for an index partition.

Storage preferences are not switched, so if you switch and then rebuild the index, then the table may be created in a different location.

Restrictions

Both indexes must be equivalent. They must use the same objects and the same settings for each object. Note that Oracle Text checks only that the indexes are using the same object. But they should use the same exact everything.

No index object can be partitioned, that is, when the user has used the storage object to partition the \$I, \$N tables.

If either index or index partition does not meet all these restrictions an error is raised and both the index and index partition will be `INVALID`. You must manually rebuild both index and index partition using the `ALTER INDEX REBUILD` statement.

#### Truncate Partition Syntax

    ALTER TABLE [schema.]table TRUNCATE PARTITION [DROP|REUSE STORAGE] [UPDATE GLOBAL
    INDEXES]

Removes all rows from a partition in a table. Corresponding `CONTEXT` index partitions are also removed.

For a global, nonpartitioned index, if you perform the truncate operation without an `UPDATE GLOBAL INDEXES` clause, then the resulting index (if not `NULL`) will be invalid and must be rebuilt. If you specify the `UPDATE GLOBAL INDEXES` clause after the operation, the index will be valid.

#### ALTER TABLE Examples

Global Index on Partitioned Table Examples

The following example creates a range-partitioned table with three partitions. Each partition is populated with two rows. A global, nonpartitioned `CONTEXT` index is then created. To demonstrate the `UPDATE GLOBAL INDEXES` clause, the partitions are split and merged with an index synchronization.

    create table tdrexglb_part(a int, b varchar2(40)) partition by range(a)
    (partition p1 values less than (10),
     partition p2 values less than (20),
     partition p3 values less than (30));

    insert into tdrexglb_part values (1,'row1');
    insert into tdrexglb_part values (8,'row2');
    insert into tdrexglb_part values (11,'row11');
    insert into tdrexglb_part values (18,'row18');
    insert into tdrexglb_part values (21,'row21');
    insert into tdrexglb_part values (28,'row28');

    commit;
    create index tdrexglb_parti on tdrexglb_part(b) indextype is ctxsys.context;

    create table tdrexglb(a int, b varchar2(40));

    insert into tdrexglb values(20,'newrow20');
    commit;

    PROMPT make sure query works
    select * from tdrexglb_part where contains(b,'row18') >0;

    PROMPT split partition
    alter table tdrexglb_part split partition p2 at (15) into
    (partition p21, partition p22) update global indexes;

    PROMPT before sync
    select * from tdrexglb_part where contains(b,'row11') >0;
    select * from tdrexglb_part where contains(b,'row18') >0;

    exec ctx_ddl.sync_index('tdrexglb_parti')

    PROMPT after sync
    select * from tdrexglb_part where contains(b,'row11') >0;
    select * from tdrexglb_part where contains(b,'row18') >0;

    PROMPT merge partition
    alter table tdrexglb_part merge partitions p22, p3
    into partition pnew3 update global indexes;

    PROMPT before sync
    select * from tdrexglb_part where contains(b,'row18') >0;
    select * from tdrexglb_part where contains(b,'row28') >0;
    exec ctx_ddl.sync_index('tdrexglb_parti');

    PROMPT after sync
    select * from tdrexglb_part where contains(b,'row18') >0;
    select * from tdrexglb_part where contains(b,'row28') >0;

    PROMPT drop partition
    alter table tdrexglb_part drop partition p1 update global indexes;

    PROMPT before sync
    select * from tdrexglb_part where contains(b,'row1') >0;
    exec ctx_ddl.sync_index('tdrexglb_parti');

    PROMPT after sync
    select * from tdrexglb_part where contains(b,'row1') >0;

    PROMPT exchange partition
    alter table tdrexglb_part exchange partition pnew3 with table
    tdrexglb update global indexes;

    PROMPT before sync
    select * from tdrexglb_part where contains(b,'newrow20') >0;
    select * from tdrexglb_part where contains(b,'row28') >0;

    exec ctx_ddl.sync_index('tdrexglb_parti');
    PROMPT after sync
    select * from tdrexglb_part where contains(b,'newrow20') >0;
    select * from tdrexglb_part where contains(b,'row28') >0;

    PROMPT move table partition
    alter table tdrexglb_part move partition p21 update global indexes;
    PROMPT before sync
    select * from tdrexglb_part where contains(b,'row11') >0;

    exec ctx_ddl.sync_index('tdrexglb_parti');
    PROMPT after sync
    select * from tdrexglb_part where contains(b,'row11') >0;

    PROMPT truncate table partition
    alter table tdrexglb_part truncate partition p21 update global indexes;

    update global indexes;

### 1.3 CATSEARCH

Use the `CATSEARCH` operator to search `CTXCAT` indexes. Use this operator in the `WHERE` clause of a `SELECT` statement.

The `CATSEARCH` operator also supports database links. You can identify a remote table or materialized view by appending `@dblink` to the end of its name. The `dblink` must be a complete or partial name for a database link to the database containing the remote table or materialized view. (Indexing of remote views is not supported.)

The grammar of this operator is called `CTXCAT`. You can also use the `CONTEXT` grammar if your search criteria require special functionality, such as thesaurus, fuzzy matching, proximity searching, or stemming. To utilize the `CONTEXT` grammar, use the "Query Template Specification" in the text_query parameter as described in this section.

#### About Performance

Use the `CATSEARCH` operator with a CTXCAT index mainly to improve mixed-query performance. Specify your text query condition with `text_query` and your structured condition with the `structured_query` argument.

Internally, Oracle Text uses a combined B-tree index on text and structured columns to quickly produce results satisfying the query.

#### Limitations

If the optimizer chooses to use the functional query invocation, then your query will fail. The optimizer might choose functional invocation when your structured clause is highly selective.

You can use the `INDEX` hint to specify the optimizer to use the index and avoid functional evaluation of `CATSEARCH`.

The `structured_query` argument of the `CATSEARCH` operator must reference columns used during `CREATE` `INDEX` sets; otherwise, error DRG-10845 will be raised. For example, the error will be raised if you issue a `CATSEARCH` query on a view created on top of a table with the `CTXCAT` index on it, and the name of the logical column on the view is different from the actual column name on the physical table. The columns referenced by the `structured_query` argument of the `CATSEARCH` operator must be the physical column name used during `CREATE` `INDEX` sets, not the logical column on the view.

#### Syntax

    CATSEARCH(

    [schema.]column,
    text_query       [VARCHAR2|CLOB],
    structured_query VARCHAR2,

    RETURN NUMBER;

\[schema.\]column
Specifies the text column to be searched on. This column must have a `CTXCAT` index associated with it.

text_query
Specify one of the following to define your search in `column`:

- CATSEARCH Query Operations

- Query Template Specification (for using `CONTEXT` grammar)

CATSEARCH Query Operations

The `CATSEARCH` operator supports only the following query operations:

- Logical `AND`

- Logical `OR` (\|)

- Logical `NOT` (-)

- " " (quoted phrases)

- Wildcarding

Table 1-4 provides the syntax for these operators.

Table 1-4 CATSEARCH Query Operators

| Operation                                | Syntax         | Description of Operation                                                                                                                                                                                                                                                                                                                                |
|:-----------------------------------------|:---------------|:--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Logical `AND`                            | a b c          | Returns rows that contain a, b, and c.                                                                                                                                                                                                                                                                                                                  |
| Logical `OR`                             | a \| b \| c    | Returns rows that contain a, b, or c.                                                                                                                                                                                                                                                                                                                   |
| Logical `NOT`                            | a - b          | Returns rows that contain a and not b.                                                                                                                                                                                                                                                                                                                  |
| Hyphen with no space                     | a-b            | Hyphen treated as a regular character.<br>For example, if the hyphen is defined as skipjoin, words such as web-site are treated as the single query term website.<br>Likewise, if the hyphen is defined as a printjoin, words such as web-site are treated as web-site in the `CTXCAT` query language.                                                  |
| " "                                      | "a b c"        | Returns rows that contain the phrase "a b c".<br>For example, entering "Sony CD Player" means return all rows that contain this sequence of words.                                                                                                                                                                                                      |
| ( )                                      | (A B) \| C     | Parentheses group operations. This query is equivalent to the `CONTAINS` query (A &B) \| C.                                                                                                                                                                                                                                                             |
| Wildcard<br>(right and double truncated) | term\*<br>a\*b | The wildcard character matches zero or more characters.<br>For example, do\* matches dog, and gl\*s matches glass.<br>Left truncation not supported.<br>Note: Oracle recommends that you create a prefix index if your application uses wildcard searching. Set prefix indexing with the [BASIC_WORDLIST](oracle-text-indexing-elements.md) preference. |

The following limitations apply to these operators:

- The left-hand side (the column name) must be a column named in at least one of the indexes of the index set.

- The left-hand side must be a plain column name. Functions and expressions are not allowed.

- The right-hand side must be composed of literal values. Functions, expressions, other columns, and subselects are not allowed.

- Multiple criteria can be combined with `AND`. Note that `OR` is not supported.

- When querying a remote table through a database link, the database link must be specified for `CATSEARCH` as well as for the table being queried.

For example, these expressions are supported:

    catsearch(text, 'dog', 'foo > 15')
    catsearch(text, 'dog', 'bar = ''SMITH''')
    catsearch(text, 'dog', 'foo between 1 and 15')
    catsearch(text, 'dog', 'foo = 1 and abc = 123')
    catsearch@remote(text, 'dog', 'foo = 1 and abc = 123')

These expressions are not supported:

    catsearch(text, 'dog', 'upper(bar) = ''A''')
    catsearch(text, 'dog', 'bar LIKE ''A%''')
    catsearch(text, 'dog', 'foo = abc')
    catsearch(text, 'dog', 'foo = 1 or abc = 3')

Query Template Specification

Specifies a marked-up string that specifies a query template. Specify one of the following templates:

- Query rewrite, used to expand a query string into different versions

- Progressive relaxation, used to progressively enter less restrictive versions of a query to increase recall

- Alternate grammar, used to specify `CONTAINS` operators (See "CONTEXT Query Grammar Examples")

- Alternate language, used to specify alternate query language

- Alternate scoring, used to specify alternate scoring algorithms

  **See Also:**

  The "text_query" parameter description for `CONTAINS` for more information about the syntax for these query templates

structured_query
Specifies the structured conditions and the `ORDER` `BY` clause. There must exist an index for any column you specify. For example, if you specify `'category_id=1 order by bid_close'`, you must have an index for `'category_id, bid_close'` as specified with the `CTX_DDL`.`ADD_INDEX` package.

With `structured_query`, you can use standard SQL syntax only with the following operators:

- =

- \<=

- \>=

- \>

- \<

- `IN`

- `BETWEEN`

- `AND` (to combine two or more clauses)

  **Note:**

  You cannot use parentheses () in the `structured_query` parameter.

#### Examples

1.  Create the table.

    The following statement creates the table to be indexed:

        CREATE TABLE auction (category_id number primary key, title varchar2(20),
        bid_close date);

    The following statements insert the values into the table:

        INSERT INTO auction values(1, 'Sony DVD Player', '20-FEB-2012');
        INSERT INTO auction values(2, 'Sony DVD Player', '24-FEB-2012');
        INSERT INTO auction values(3, 'Pioneer DVD Player', '25-FEB-2012');
        INSERT INTO auction values(4, 'Sony DVD Player', '25-FEB-2012');
        INSERT INTO auction values(5, 'Bose Speaker', '22-FEB-2012');
        INSERT INTO auction values(6, 'Tascam CD Burner', '25-FEB-2012');
        INSERT INTO auction values(7, 'Nikon digital camera', '22-FEB-2012');
        INSERT INTO auction values(8, 'Canon digital camera', '26-FEB-2012');

2.  Create the `CTXCAT` index.

    The following statements create the `CTXCAT` index:

        begin

        ctx_ddl.create_index_set('auction_iset');
        ctx_ddl.add_index('auction_iset','bid_close');

        end;
        /
        CREATE INDEX auction_titlex ON auction(title) INDEXTYPE IS CTXSYS.CTXCAT
        PARAMETERS ('index set auction_iset');

3.  Query the table.

    A typical query with `CATSEARCH` might include a structured clause as follows to find all rows that contain the word camera ordered by `bid_close`:

        SELECT * FROM auction WHERE CATSEARCH(title, 'camera', 'order by bid_close desc')>
        0;

        CATEGORY_ID TITLE                BID_CLOSE
        ----------- -------------------- ---------
                  8 Canon digital camera 26-FEB-12
                  7 Nikon digital camera 22-FEB-12

    The following query finds all rows that contain the phrase Sony DVD Player and that have a bid close date of February 20, 2012:

        SELECT * FROM auction WHERE CATSEARCH(title, '"Sony DVD Player"',
        'bid_close=''20-FEB-00''')> 0;

        CATEGORY_ID TITLE                BID_CLOSE
        ----------- -------------------- ---------
                  1 Sony DVD Player       20-FEB-12

    The following query finds all rows with the terms Sony and DVD and Player:

        SELECT * FROM auction WHERE CATSEARCH(title, 'Sony DVD Player',
        'order by bid_close
        desc')> 0;
        CATEGORY_ID TITLE                BID_CLOSE
        ----------- -------------------- ---------
                  4 Sony DVD Player       25-FEB-12
                  2 Sony DVD Player       24-FEB-12
                  1 Sony DVD Player       20-FEB-12

    The following query finds all rows with the term DVD and not Player:

        SELECT * FROM auction WHERE CATSEARCH(title, 'DVD - Player', 'order by bid_close
        desc')> 0;

        CATEGORY_ID TITLE                BID_CLOSE
        ----------- -------------------- ---------
                  6 Tascam CD Burner     25-FEB-12

    The following query finds all rows with the terms CD or DVD or Speaker:

        SELECT * FROM auction WHERE CATSEARCH(title, 'CD | DVD | Speaker', 'order by
        bid_close desc')> 0;

        CATEGORY_ID TITLE                BID_CLOSE
        ----------- -------------------- ---------
                  3 Pioneer DVD Player   25-FEB-12
                  4 Sony DVD Player      25-FEB-12
                  6 Tascam CD Burner     25-FEB-12
                  2 Sony DVD Player      24-FEB-12
                  5 Bose Speaker         22-FEB-12
                  1 Sony DVD Player      20-FEB-12

    The following query finds all rows that are about audio equipment:

        SELECT * FROM auction WHERE CATSEARCH(title, 'ABOUT(audio equipment)',
        NULL)> 0;

CONTEXT Query Grammar Examples

The following examples show how to specify the `CONTEXT` grammar in `CATSEARCH` queries using the template feature:

    PROMPT
    PROMPT fuzzy: query = ?test
    PROMPT should match all fuzzy variations of test (for example, text)
    select pk||' ==> '||text from test
    where catsearch(text,
    '<query>
      <textquery grammar="context">
         ?test
      </textquery>
    </query>','')>0
    order by pk;

    PROMPT
    PROMPT fuzzy: query = !sail
    PROMPT should match all soundex variations of bot (for example, sell)
    select pk||' ==> '||text from test
    where catsearch(text,
    '<query>
      <textquery grammar="context">
         !sail
      </textquery>
    </query>','')>0
    order by pk;

    PROMPT
    PROMPT theme (ABOUT) query
    PROMPT query: about(California)
    select pk||' ==> '||text from test
    where catsearch(text,
    '<query>
      <textquery grammar="context">
         about(California)
      </textquery>
    </query>','')>0
    order by pk;

The following example shows a field section search against a `CTXCAT` index using `CONTEXT` grammar by means of a query template in a `CATSEARCH` query:

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
    exec ctx_ddl.add_index('BOOKSET','PUBDATE');

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
    -- sections with CATSEARCH.

    select  id, info from books
    where catsearch(info,
    '<query>
          <textquery grammar="context">
                  NOAM within author and english within language
          </textquery>
     </query>',
    'order by pubdate')>0;

#### Related Topics

"Syntax for CTXCAT Index Type"

[Oracle Text Application Developer's Guide](../ccapp/querying-with-oracle-text.md)

### 1.4 CONTAINS

Use the `CONTAINS` operator in the `WHERE` clause of a `SELECT` statement to specify the query expression for a Text query.

The `CONTAINS` operator also supports database links. You can identify a remote table or materialized view by appending `@dblink` to the end of its name. The `dblink` must be a complete or partial name for a database link to the database containing the remote table or materialized view (querying of remote views is not supported).

`CONTAINS` returns a relevance score for every row selected. Obtain this score with the SCORE operator.

The grammar for this operator is called the `CONTEXT` grammar. You can also use `CTXCAT` grammar if your application works better with simpler syntax. To do so, use the Query Template Specification in the `text_query` parameter as described in this section.

**See Also:**

- Query Rewrite Template

- Query Result Set Descriptor Template

- Query Relaxation Template

- Alternate Grammar Template

- Language Independent Template

- Alternate Language Template

- Alternative Scoring Template

- The CONTEXT Grammar" topic in [Oracle Text Application Developer's Guide](../ccapp/working-with-CONTEXT-and-CTXCAT-grammars-in-oracle-text.md)

#### Syntax

    CONTAINS(
             [schema.]column,
             text_query    [VARCHAR2|CLOB]
             [,label       NUMBER])
    RETURN NUMBER;

\[schema.\]column
Specify the text column to be searched on. This column must have a Text index associated with it.

text_query
Specify one of the following (limited to 4000 bytes for a `VARCHAR2` or 64000 bytes for a `CLOB`):

- The query expression that defines your search in `column`.

- A marked-up document that specifies a query template.

  Use one of the following query templates:

  - Query Rewrite Template

  - Query Result Set Descriptor Template

  - Query Relaxation Template

  - Alternate Grammar Template

  - Language Independent Template

  - Alternate Language Template

  - Alternative Scoring Template

Query Rewrite Template

Use this template to automatically write different versions of a query before you submit the query to Oracle Text. This is useful when you need to maximize the recall of a user query. For example, you can program your application to expand a single phrase query of 'cat dog' into the following queries:

    {cat} {dog}
    {cat} ; {dog}
    {cat} AND {dog}
    {cat} ACCUM {dog}

These queries are submitted as one query and results are returned with no duplication. In this example, the query returns documents that contain the phrase cat dog as well as documents in which cat is near dog, and documents that have cat and dog.

This is done with the following template:

     <query>
       <textquery lang="ENGLISH" grammar="CONTEXT"> cat dog
         <progression>
           <seq><rewrite>transform((TOKENS, "{", "}", " "))</rewrite></seq>
           <seq><rewrite>transform((TOKENS, "{", "}", " ; "))</rewrite></seq>
           <seq><rewrite>transform((TOKENS, "{", "}", " AND "))</rewrite></seq>
           <seq><rewrite>transform((TOKENS, "{", "}", " ACCUM "))</rewrite></seq>
         </progression>
       </textquery>
      <score datatype="INTEGER" algorithm="COUNT"/>
    </query>

The operator `TRANSFORM` is used to specify the rewrite rules and has the following syntax (note that it uses double parentheses). The parameters are described in the following table.

    TRANSFORM((terms, prefix, suffix, connector))

Table 1-5 TRANSFORM Parameters

| Parameter   | Description                                                                                              |
|:------------|:---------------------------------------------------------------------------------------------------------|
| `term`      | Specifies the type of terms to be produced from the original query. Specify either `TOKENS` or `THEMES`. |
| `prefix`    | Specifies the literal string to be prepended to all terms.                                               |
| `suffix`    | Specifies the literal string to be appended to all terms.                                                |
| `connector` | Specifies the literal string to connect all terms after applying the prefix and suffix.                  |

**Note:**

An error will be raised if the input Text query string specified in the Query Rewrite Template with `TRANSFORM` rules contains any Oracle Text query operators (such as `AND`, `OR`, or `SOUNDEX`). Also, any special characters (such as `%` or `$`) in the input Text query string must be preceded by an escape character, or an error is raised.

Query Result Set Descriptor Template

Use this template to take in a Result Set Descriptor. The element ctx_result_set_descriptor is added to the query template. This enables the CONTAINS query cursor to take in a group count query.

The Result Set Interface document is placed in a public variable in the ctx_query package. (ctx_query.result_set_document.)

The CONTAINS query cursor behavior remains unchanged and the Result Set Document is available right after closing the cursor

For example, the following query of kukui nut returns a result set with the following template.

    <query>
       <textquery lang="ENGLISH" grammar="CONTEXT">
         <progression>
           <seq><rewrite>transform((TOKENS, "{", "}", " "))</rewrite></seq>
           <seq><rewrite>transform((TOKENS, "{", "}", " ; "))</rewrite></seq>
           <seq><rewrite>transform((TOKENS, "{", "}", " AND "))</rewrite></seq>
           <seq><rewrite>transform((TOKENS, "{", "}", " ACCUM "))</rewrite></seq>
         </progression>
       </textquery>
      <score datatype="INTEGER" algorithm="COUNT"/>
    <ctx_result_set_descriptor>
     <group>
        <group_values>
           <value id="2"/>
           <value id="3"/>
           <value id="4"/>
        </group_values>
        <count/>
      </group>
    </ctx_result_set_descriptor>
    </query>

Query Relaxation Template

Use this template to progressively relax your query. Progressive relaxation is when you increase recall by progressively issuing less restrictive versions of a query, so that your application can return an appropriate number of hits to the user.

For example, the query of blue pen can be progressively relaxed to:

    blue pen
    blue NEAR pen
    blue AND pen
    blue ACCUM pen

This is done with the following template

    <query>
       <textquery lang="ENGLISH" grammar="CONTEXT">
         <progression>
           <seq>blue pen</seq>
           <seq>blue NEAR pen</seq>
           <seq>blue AND pen</seq>
           <seq>blue ACCUM pen</seq>
         </progression>
       </textquery>
       <score datatype="INTEGER" algorithm="COUNT"/>
    </query>

Alternate Grammar Template

Use this template to specify an alternate grammar, such as `CONTEXT` or `CATSEARCH`. Specifying an alternate grammar enables you to enter queries using different syntax and operators.

For example, with `CATSEARCH`, enter `ABOUT` queries using the `CONTEXT` grammar. Likewise with `CONTAINS`, enter logical queries using the simplified `CATSEARCH` syntax.

The phrase 'dog cat mouse' is interpreted as a phrase in `CONTAINS`. However, with `CATSEARCH`, this is equivalent to an `AND` query of 'dog AND cat AND mouse'. Specify that `CONTAINS` use the alternate grammar with the following template:

    <query>
      <textquery grammar="CTXCAT">dog cat mouse</textquery>
      <score datatype="integer"/>
    </query>

Language Independent Template

Use this template to specify a lexer that uses user-defined symbols (or abbreviations) and does not depend on any language.

The following example specifies that the query take a list of language-independent sublexers.

    <query>
          <textquery grammar="CONTEXT" lang="ENGLISH">
                Oracle
          </textquery>
          <score datatype="INTEGER" algorithm="COUNT"/>
          <sublexers>
                <sublexer_label>  SESSION_LANG   </sublexer_label>
                <sublexer_label>   MAIL   </sublexer_label>
                <sublexer_label> CALENDER </sublexer_label>
          </sublexers>
    </query>

The following conditions apply:

- The `sublexers` element consists of one or more `sublexer_label` elements.

- Each `sublexer_label` element contains the symbol for the language independent sub_lexer.

- When the `sublexers` element is specified, the query will be processed with the stopwords and sub_lexers for each of the symbols specified in the `sublexers` element, and `query` will return only the documents indexed by the specified sub_lexers.

- A special reserved symbol called `SESSION_LANG` can be used for the system to pick a language-dependent sub_lexer based on the language specified in `lang` attribute of the `textquery` element in the query template. If `lang` attribute is not specified, then the `lang` attribute will be based on session language. `Query` parsed by the chosen sub_lexer will only return documents indexed by that language-dependent sub_lexer. If both `SESSION_LANG` and `lang` attribute are specified, the `lang` attribute will take priority.

- If `sublexers` element is specified without `SESSION_LANG`, then `lang` attribute of `textquery` element will be ignored.

- Default Behavior:

  If `sublexers` element is not present in the query template, then `query` will be parsed with one language-dependent sub-lexer (if any), which is chosen based on the specified `lang` attribute value or the session language AND all language independent sub-lexers.

Alternate Language Template

Use this template to specify an alternate language:

    <query><textquery lang="french">bon soir</textquery></query>

Alternative Scoring Template

Use this template to specify an alternative scoring algorithm.

The following example specifies that the query use the `CONTEXT` grammar and return integer scores using the `COUNT` algorithm. This algorithm returns a score as the number of query occurrences in the document.

    <query>
         <textquery grammar="CONTEXT" lang="english"> mustang
         </textquery>
         <score datatype="INTEGER" algorithm="COUNT"/>
    </query>

The following example uses the `normalization_expr` attribute to add `SDATA`(price) into the score returned by the query, and uses it as the final score:

    <query>
        <textquery grammar="CONTEXT" lang="english">
            DEFINESCORE(dog, RELEVANCE) and  cat
        </textquery>
        <score  algorithm="COUNT"  normalization_expr ="doc_score+ SDATA(price)"/>
    </query>

The `normalization_expr` attribute is used only with the alternate scoring template, and is an arithmetic expression that consists of:

- Arithmetic operators: + - \* /. The operator precedence is the same as that for SQL operator precedence.

- Grouping operators: (). Parentheses can be used to alter the precedence of the arithmetic operators.

- Absolute function: ABS(n) returns the absolute value of n; where n is any expression that returns a number.

- Logarithmic function: LOG(n): returns the base-10 logarithmic value of n; where n is any expression that returns a number.

- Predefined components: The `doc_score` predefined component can be used to return the initial query score of a particular document.

- `SDATA` component: `SDATA`(name) returns the value of the `SDATA` with the specified name as the score.

  - Only `SDATA` with a `NUMBER` or `DATE` data type is allowed. An error is raised otherwise.

  - The sdata string and the `SDATA` name are case-insensitive.

  - Because an `SDATA` section value can be `NULL`, any expression with `NULL` `SDATA` section value is evaluated as 0. For example: the `normalization_expr "doc_score + SDATA(price)"` will be evaluated to 0 if `SDATA(price)` for a given document has a `NULL` value.

- Numeric literals: There are any number literal that conforms to the SQL pattern of `NUMBER` literal and is within the range of the double-precision floating-point (`-3.4e38` to `3.4e38`).

- Date literals: Date literals must be enclosed with `DATE` (). Only the following format is allowed: `YYYY-MM-DD` or `YYYY-MM-DD HH24:MI:SS`. For example: `DATE(2005-11-08)`.

  Consistent with SQL, if no time is specified, then `00:00:00` is assumed.

The `normalization_expr` attribute overrides the algorithm attribute. That is, if algorithm is set to `COUNT`, and the user also specifies `normalization_expr`, then the score will not be count, but the calculated score based on the `normalization_expr`.

If the score (either from `algorithm = COUNT` or `normalization_expr =` ...) is internally calculated to be greater than 100, then it will be set to 100.

If the query relaxation template is used, the score will be further normalized in such a way that documents returned from higher sequences will always have higher scores than documents returned from sequence(s) below.

DATE Literal Restrictions
Only the minus (`-`) operator is allowed between date-type data (`DATE` literals and date-type `SDATA`). Using other operators will result in an error. Subtracting two date-type data will produce a number (float) that represents the difference in number of days between the two dates. For example, the following expression is allowed:

    SDATA(dob) –  DATE(2005-11-08)

The following expression is not allowed:

    SDATA(dob) +  DATE(2005-11-08)

The plus (`+`) and minus (`-`) operators are allowed between numeric data and date type of data. The number operand is interpreted as the number or fraction of days. For example, the following expression is allowed:

    DATE(2005-11-08) + 1        = 9 NOV 2005

The following expression is not allowed:

    DATE(2005-11-08)* 3          = ERROR

Template Attribute Values

Table 1-6 gives the possible values for template attributes.

Table 1-6 Template Attribute Values

| Tag Attribute | Description                                     | Possible Values                                                                                                                              | Meaning                                                                                                                     |
|:--------------|:------------------------------------------------|:---------------------------------------------------------------------------------------------------------------------------------------------|:----------------------------------------------------------------------------------------------------------------------------|
| grammar=      | Specifies the grammar of the query.             | `CONTEXT`<br>`CTXCAT`                                                                                                                        | The grammar of the query.                                                                                                   |
| datatype=     | Specifies the type of number returned as score. | `INTEGER`<br>`FLOAT`                                                                                                                         | Returns score as integer between 0 and 100.<br>Returns score as its high-precision floating-point number between 0 and 100. |
| algorithm=    | Specifies the scoring algorithm to use.         | `DEFAULT`<br>`COUNT`                                                                                                                         | Returns the default.<br>Returns scores as the number of occurrences in the document.                                        |
| lang=         | Specifies the language name.                    | Any language supported by Oracle Database. See [Oracle Database Globalization Support Guide](../nlspg/overview-of-globalization-support.md). | The language name.                                                                                                          |

Template Grammar Definition

The query template interface is an XML document. Its grammar is defined with the following XML DTD:

    <!DOCTYPE query [
    <!ELEMENT query (textquery, score?, order?)>
    <!ELEMENT textquery (#PCDATA|progression)*>
    <!ELEMENT progression (seq)+>
    <!ELEMENT seq (#PCDATA|rewrite)*>
    <!ELEMENT rewrite (#PCDATA)>
    <!ELEMENT score EMPTY>
    <!ELEMENT order (orderkey+)>
    <!ELEMENT orderkey (#PCDATA)>
    <!ATTLIST textquery grammar (CONTEXT | CTXCAT | CTXRULE) #REQUIRED>
    <!ATTLIST textquery lang CDATA #IMPLIED>
    <!ATTLIST score datatype (integer | float) "integer">
    <!ATTLIST score algorithm (default | count) "default">
    <!ATTLIST score normalization_expr CDATA >

Values are case insensitive: integer \| float, default \| count, context \|ctxcat .

**See Also:**

[Oracle Text CONTAINS Query Operators](oracle-text-CONTAINS-query-operators.md) for more information about the operators in query expressions

label
Optionally, specifies the label that identifies the score generated by the `CONTAINS` operator.

#### Returns

For each row selected, the `CONTAINS` operator returns a number between 0 and 100 that indicates how relevant the document row is to the query. The number 0 means that Oracle Text found no matches in the row.

**Note:**

You must use the `SCORE` operator with a label to obtain this number.

#### Example

The following example searches for all documents in the `text` column that contain the word oracle. The score for each row is selected with the `SCORE` operator using a label of `1`:

    SELECT SCORE(1), title from newsindex
        WHERE CONTAINS(text, 'oracle', 1) > 0;

The `CONTAINS` operator must be followed by an expression such as \> 0, which specifies that the score value calculated must be greater than zero for the row to be selected.

When the `SCORE` operator is called (for example, in a `SELECT` clause), the `CONTAINS` clause must reference the score label value as in the following example:

    SELECT SCORE(1), title from newsindex
         WHERE CONTAINS(text, 'oracle', 1) > 0 ORDER BY SCORE(1) DESC;

The following example specifies that the query be parsed using the `CATSEARCH` grammar:

    SELECT id FROM test WHERE CONTAINS (text,
     '<query>
       <textquery lang="ENGLISH" grammar="CATSEARCH">
          cheap pokemon
       </textquery>
       <score datatype="INTEGER"/>
      </query>' ) > 0;

Grammar Template Example

The following example shows how to use the `CTXCAT` grammar in a `CONTAINS` query. The example creates a `CTXCAT` and a `CONTEXT` index on the same table, and compares the query results.

    PROMPT create context and ctxcat indexes, both using theme indexing
    PROMPT
    create index tdrbqcq101x on test(text) indextype is ctxsys.context
    parameters ('lexer theme_lexer');

    create index tdrbqcq101cx on test(text) indextype is ctxsys.ctxcat
    parameters ('lexer theme_lexer');

    PROMPT *****  San Diego             ***********
    PROMPT *****  CONTEXT grammar       ***********
    PROMPT ** should be interpreted as phrase query **
    select pk||' ==> '||text from test
    where contains(text,'San Diego')>0
    order by pk;

    PROMPT *****  San Diego      ***********
    PROMPT *****  CTXCAT grammar ***********
    PROMPT ** should be interpreted as AND query  ***
    select pk||' ==> '||text from test
    where contains(text,
    '<query>
      <textquery grammar="CTXCAT">San Diego</textquery>
      <score datatype="integer"/>
    </query>')>0
    order by pk;

    PROMPT *****  Hitlist from CTXCAT index ***********
    select pk||' ==> '||text from test
    where catsearch(text,'San Diego','')>0
    order by pk;

Alternate Scoring Query Template Example

The following query template adds price `SDATA` section (or `SDATA` filter-by column) value into the score returned by the query and uses it as the final score:

    <query>
          <textquery grammar="CONTEXT" lang="english">
                 DEFINESCORE(dog, RELEVANCE) and cat
          </textquery>
          <score algorithm="COUNT" normalization_expr ="doc_score+SDATA(price)"/>
    </query>

Query Relaxation Template Example

The following query template defines a query relaxation sequence. The query of blue pen is entered in sequence as blue pen, then blue NEAR pen, then blue AND pen, and then blue ACCUM pen. Query hits are returned in this sequence with no duplication as long as the application requires results.

    select id from docs where CONTAINS (text, '
    <query>
       <textquery lang="ENGLISH" grammar="CONTEXT">
         <progression>
           <seq>blue pen</seq>
           <seq>blue NEAR pen</seq>
           <seq>blue AND pen</seq>
           <seq>blue ACCUM pen</seq>
         </progression>
       </textquery>
       <score datatype="INTEGER" algorithm="COUNT"/>
    </query>')>0;

Query relaxation is most effective when your application requires the top n hits to a query, which you can obtain with the `DOMAIN_INDEX_SORT` or `FIRST_ROWS` hint, which is being deprecated, in a PL/SQL cursor.

Query Rewrite Template Example

The following template defines a query rewrite sequence. The query of kukui nut is rewritten as follows:

{kukui} {nut}

{kukui} ; {nut}

{kukui} AND {nut}

{kukui} ACCUM {nut}

    select id from docs where CONTAINS (text, '
     <query>
       <textquery lang="ENGLISH" grammar="CONTEXT"> kukui nut
         <progression>
           <seq><rewrite>transform((TOKENS, "{", "}", " "))</rewrite></seq>
           <seq><rewrite>transform((TOKENS, "{", "}", " ; "))</rewrite>/seq>
           <seq><rewrite>transform((TOKENS, "{", "}", " AND "))</rewrite><seq/>
           <seq><rewrite>transform((TOKENS, "{", "}", " ACCUM "))</rewrite><seq/>
         </progression>
       </textquery>
      <score datatype="INTEGER" algorithm="COUNT"/>
    </query>')>0;

Order By SDATA Sections Template Example

The following query template defines a query sequence for ordering by `SDATA` section values using the` <order>` and `<orderkey>` elements. The first level of ordering is done on the `SDATA` section `price`, which is sorted in the ascending order. The second and third level of ordering is done by the `SDATA` section `pub_date` and score, both of which are sorted in the descending order.

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

The `<orderkey>` element value must have the following format:

    <orderkey> SDATA(sdata_section_name) | score [DESC|ASC] </orderkey>

The sort order is ascending by default, if not specified as either `DESC` or `ASC`.

The `<orderkey>` element will be ignored in the following cases:

- when the Oracle Cost-Based Optimizer (CBO) pushes the SQL query level ordering into the Text index

- when the `CONTAINS()` predicate is processed functionally

- when the ordering is already specified by the ORDER BY clause in the SQL query statement

#### Notes

Querying Multilanguage Tables

With the multilexer preference, you can create indexes from multilanguage tables. At query time, the multilexer examines the session's language setting and uses the sublexer preference for that language to parse the query. If the language setting is not mapped, then the default lexer is used.

When the language setting is mapped, the query is parsed and run as usual. The index contains tokens from multiple languages, so such a query can return documents in several languages.

To limit your query to returning documents of a given language, use a structured clause on the language column.

Query Performance Limitation with a Partitioned Index

Oracle Text supports the `CONTEXT` indexing and querying of a partitioned text table.

However, for optimal performance when querying a partitioned table with an `ORDER` `BY` `SCORE` clause, query the partition. If you query the entire table and use an `ORDER` `BY` `SCORE` clause, the query might not perform optimally unless you include a range predicate that can limit the query to a single partition.

For example, the following statement queries the partition `p_tab4` partition directly:

    select * from part_tab partition (p_tab4) where contains(b,'oracle') > 0 ORDER BY
    SCORE DESC;

Limitation with Remote Execution of CONTAINS Query

Oracle Text supports the remote execution of the `CONTAINS` operator, but with some limitations. You can invoke the `CONTAINS` operator in a remote query only if the query is executed completely in the remote database. You cannot use the `CONTAINS` operator in a subquery of a query, which causes the query to run partly on the remote database and partly on the local database. Doing so will raise the error "ORA-00949: illegal reference to remote database." However, `CONTAINS`, when invoked remotely from an inner query might run successfully sometimes if view merging is enabled and possible on this query, as in this case the query will be transformed into a single query and, hence, no error will occur.

For example, the following query is correct:

    select id from remtab@rdb
    where contains@rdb(text,'hello') > 0;

#### Related Topics

"Syntax for CONTEXT Index Type"

[Oracle Text CONTAINS Query Operators](oracle-text-CONTAINS-query-operators.md)

"The CONTEXT Grammar" topic in [Oracle Text Application Developer's Guide](../ccapp/working-with-CONTEXT-and-CTXCAT-grammars-in-oracle-text.md)

"SCORE"

### 1.5 CREATE INDEX

Use the `CREATE INDEX` statement to create an Oracle Text index.

This section describes the `CREATE` `INDEX` statement as it pertains to creating an Oracle Text domain index and composite domain index. See "[Oracle Database SQL Language Reference](../sqlrf/CREATE-INDEX.md) for a complete description of the `CREATE` `INDEX` statement.

#### Purpose

To create an Oracle Text index. An Oracle Text index is an Oracle Database domain index or composite domain index of type `CONTEXT`, `CTXCAT`, or `CTXRULE`. A domain index is an application-specific index. A composite domain index (CDI) is an Oracle Text index that not only indexes and processes a specified text column, but also indexes and processes `FILTER` `BY` and `ORDER` `BY` structured columns, which are specified during index creation.

Example

    create table mytab
    (item_id number,
     item_info varchar2(4000),
     item_supplier varchar2(250),
     item_distributor varchar2(500));

    create index idx on mytab(item_info) indextype is ctxsys.context
    filter by item_supplier order by item_distributor;

You must create an appropriate Oracle Text index to enter `CONTAINS`, `CATSEARCH`, or `MATCHES` queries.

You cannot create an Oracle Text index on an index-organized table.

You can create the following types of Oracle Text indexes.

CONTEXT

A `CONTEXT` index is the basic type of Oracle Text index. This is an index on a text column. A `CONTEXT` index is useful when your source text consists of many large, coherent documents. Query this index with the `CONTAINS` operator in the `WHERE` clause of a `SELECT` statement. This index requires manual synchronization after DML. See "Syntax for CONTEXT Index Type".

CTXCAT

The `CTXCAT` index is a combined index on a text column and one or more other columns. The `CTXCAT` type is typically used to index small documents or text fragments, such as item names, prices, and descriptions found in catalogs. Query this index with the `CATSEARCH` operator in the `WHERE` clause of a `SELECT` statement. This type of index is optimized for mixed queries. This index is transactional, automatically updating itself with DML to the base table. `CTXCAT` indexes are generally larger and slower to create and update than `CONTEXT` indexes, and have a narrower range of indexing options available. See "Syntax for CTXCAT Index Type".

CTXRULE

A `CTXRULE` index is used to build a document classification application. The `CTXRULE` index is an index created on a table of queries or a column containing a set of queries, where the queries serve as rules to define the classification criteria. Query this index with the `MATCHES` operator in the `WHERE` clause of a `SELECT` statement. See "Syntax for CTXRULE Index Type".

Required Privileges

You do not need the `CTXAPP` role to create an Oracle Text index. If you have Oracle Database privileges to create an index on the text column, you have sufficient privilege to create a text index. The issuing owner, table owner, and index owner can all be different users, which is consistent with Oracle standards for creating regular indexes.

**Note:**

Whenever you create an Oracle Text index, a number of additional internal objects are created which have names prefixed with `DR$`. These internal object names usually contain the index name. In some cases, the index name is shortened to fit in the object name. In such cases, the index ID is present in the object name to avoid naming conflicts with objects of other indexes.

#### Syntax for CONTEXT Index Type

Uses a `CONTEXT` index to create an index on a text column. Query this index with the `CONTAINS` operator in the `WHERE` clause of a `SELECT` statement. This index requires manual synchronization after DML.

    CREATE INDEX [schema.]index ON [schema.]table(txt_column)
      INDEXTYPE IS ctxsys.context [ONLINE]
      [FILTER BY filter_column[, filter_column]...]
      [ORDER BY oby_column[desc|asc][, oby_column[desc|asc]]...]
      [LOCAL [PARTITION [partition] [PARAMETERS('paramstring')]]
      [, PARTITION [partition] [PARAMETERS('paramstring')]])]
      [PARAMETERS(paramstring)] [PARALLEL n] [UNUSABLE]];

\[schema.\]index
Specifies the name of the Text index to create.

\[schema.\]table(txt_column)
Specifies the name of the table and column to index. `txt_column` is the name of the domain index column on which the `CONTAINS()` operator will be invoked.

Your table can optionally contain a primary key if you prefer to identify your rows as such when you use procedures in `CTX_DOC`. When your table has no primary key, document services identifies your documents by `ROWID`.

**Note:**

Primary keys of the following type are supported: `NUMBER`, `VARCHAR2`, `DATE`, `CHAR`, `VARCHAR`, and `RAW`.

The column that you specify must be one of the following types: `CHAR`, `VARCHAR`, `VARCHAR2`, `BLOB`, `CLOB` (limited to 4294967295 bytes), `BFILE`, `XMLType`, or `URIType`.

**Note:**

In Oracle Database 12c Release 2 (12.2), an Oracle Text index cannot be created on a column with a declared collation other than `BINARY`, `USING_NLS_COMP`, `USING_NLS_SORT` or `USING_NLS_SORT_CS`. For all the supported collations, the Oracle Text behavior is the same.

The table that you specify can be a partitioned table. If you do not specify the `LOCAL` clause, then a global, nonpartitioned index is created.

The `DATE`, `NUMBER`, and nested table columns cannot be indexed. Object columns also cannot be indexed, but their attributes can be indexed, provided that they are atomic data types.

Attempting to create an index on a Virtual Private Database (VPD) protected table will fail unless one of the following criteria is true:

- The VPD policy is created such that it does not apply to the `INDEX` statement type.

- The policy function returns a `NULL` predicate for the current user.

- The user (or index owner) is `SYS`.

- The user has the `EXEMPT` `ACCESS` `POLICY` privilege.

**Note:**

If you create VPD policies or use `DBMS_REDACT` after you create a context index on the base table, then the `DR$` index tables like `$I` will still contain the redacted column's indexed information. The `CONTAINS` queries also return results accordingly. To prevent indexing of sensitive data, either create the security redaction and VPD policies before creating a context index or rebuild the context index whenever security policies are added.

Indexes on multiple columns are not supported with the `CONTEXT` index type. You must specify only one column in the column list.

**Note:**

With the `CTXCAT` index type, you can create indexes on text and structured columns. See "Syntax for CTXCAT Index Type"

**Note:**

Because a Transparent Data Encryption-enabled column does not support domain indexes, it cannot be used with Oracle Text. However, you can create an Oracle Text index on a column in a table stored in a Transparent Data Encryption-enabled tablespace.

ONLINE
Creates the index while enabling DML insertions/updates/deletions on the base table.

During indexing, Oracle Text enqueues DML requests in a pending queue. At the end of the index creation, Oracle Text locks the base table. During this time, DML is blocked. You must synchronize the index in order for DML changes to be available.

Limitations

The following limitations apply to using `ONLINE`:

- At the very beginning or very end of the `ONLINE` process, DML might fail.

- `ONLINE` is supported for `CONTEXT` indexes only.

FILTER BY filter_column
This is the structured indexed column on which a range or equality predicate in the `WHERE` clause of a mixed query will operate. You can specify one or more structured columns for `filter_column`, on which the relational predicates are expected to be specified along with the `CONTAINS()` predicate in a query.

The Cost-based Optimizer (CBO) will consider pushing down the structured predicates on these `FILTER` `BY` columns with the following relational operators: `<`, `<=`, `=`, `>=`, `>`, `between`, and `LIKE` (for `VARCHAR2`).

These columns can only be of `CHAR`, `NUMBER`, `DATE`, `VARCHAR2`, or `RAW` type. Additionally, `CHAR`, `VARCHAR2` and `RAW` types are supported only if the maximum length is specified and does not exceed 249 bytes. If the maximum length of a `CHAR` or `VARCHAR2` column is specified in characters, for example, `VARCHAR2` (50 `CHAR`), then it cannot exceed `FLOOR` (249/`max_char_width`), where `max_char_width` is the maximum width of any character in the database character set. For example, the maximum specified column length cannot exceed 62 characters, if the database character set is AL32UTF8. The `ADT` attributes of supported types (`CHAR`, `NUMBER`, `DATE`, `VARCHAR2`, or `RAW`) are also allowed. An error is raised for all other data types. Expressions, for example, `func(cola)`, and virtual columns are not allowed.

`txt_column` is allowed in the `FILTER` `BY` column list.

DML operations on `FILTER` `BY` columns are always transactional.

<!-- -->

ORDER BY oby_column
This is the structured indexed column on which a structured `ORDER` `BY` mixed query will be based. A list of structured oby_columns can be specified in the `ORDER` `BY` clause of a `CONTAINS()` query.

These columns can only be of `CHAR`, `NUMBER`, `DATE`, `VARCHAR2`, or `RAW` type. `VARCHAR2` and `RAW` columns longer than `249` bytes are truncated to the first `249` bytes. Expressions, for example, `func(cola)`, and virtual columns are not allowed.

The order of the specified columns matters. The Cost-based Optimizer (CBO) will consider pushing the sort into the composite domain index only if the `ORDER` `BY` clause in the text query contains:

- Entire ordered ORDER BY columns declared by the ORDER BY clause during the CREATE INDEX statement

- Only the prefix of the ordered ORDER BY columns declared by the ORDER BY clause during the CREATE INDEX statement

- The score followed by the prefix of the ordered ORDER BY columns declared by the ORDER BY clause during the CREATE INDEX statement

- The score following the prefix of the ordered ORDER BY columns declared by the ORDER BY clause during the CREATE INDEX statement

The following example illustrates Cost-based Optimizer (CBO) behavior with regard to `ORDER` `BY` columns:

    CREATE INDEX foox ON foo(D) INDEXTYPE IS CTXSYS.CONTEXT
    FILTER BY B, C
    ORDER BY A, B desc;

Consider the following query:

    SELECT A, SCORE(1) FROM foo WHERE CONTAINS(D, 'oracle',1)>0
    AND C>100 ORDER BY col_list;

**Note:**

If you set `NLS_SORT` or `NLS_COMP` parameters (that is, `alter session set NLS_SORT = <some lang>;` ), then CBO will not push the sort or related structured predicate into the CDI. This behavior is consistent with regular optimized for search SDATA indexes.

The Cost-based Optimizer (CBO) will consider pushing the sort into the composite domain index (CDI) if `col_list` has the following values:

     A
     A,B
     SCORE(1), A
     SCORE(1), A, B
     A, SCORE(1)
     A, B, SCORE(1)

The CBO will not consider to push the sort into the CDI if `col_list` has the following values:

     B
     B,A
     SCORE(1), B
     B, SCORE(1)
     A, B, C
     A, B asc

(or simply `A`, `B`)

Expressions, for example, `func(cola)`, are not allowed.

`txt_column` appearing in the `ORDER` `BY` column list is allowed.

DML operations on `ORDER` `BY` columns are always transactional.

Limitations

The following limitations apply to `FILTER` `BY` and `ORDER` `BY`:

- A structured column is allowed in `FILTER` `BY` and `ORDER` `BY` clauses. However, a column that is mapped to `MDATA` in a `FILTER` `BY` clause cannot also appear in the `ORDER` `BY` clause. An error will be raised in this case.

- The maximum length for `CHAR`, `VARCHAR2`, and `RAW` columns cannot be greater than 249 for `FILTER BY` columns. For `ORDER BY` columns, the data is truncated at 249 characters.

- The total number of CDI (`FILTER BY` and `ORDER BY`) is 32.

**Note:**

In a CDI, if the indexed column is also a `FILTER BY` or `ORDER BY` column, then when you update the main indexed column, the updates to the `FILTER BY` or `ORDER BY` columns are not transactional.

**Note:**

- As with concatenated optimized for search SDATA indexes or bitmap indexes, performance degradation may occur in DML as the number of `FILTER` `BY` and `ORDER` `BY` columns increases.

- Mapping a `FILTER` `BY` column to `MDATA` is not recommended if the `FILTER` `BY` column contains sequential values or has very high cardinality. Doing so can result in a very long and narrow `$I` table and reduced `$X` performance. An example is a column of type `DATE`. For columns of this type, mapping to `SDATA` is recommended.

**Note:**

An index table with the name `DR$`indextable`$S` is created to store `FILTER` `BY` and `ORDER` `BY` columns that are mapped to `SDATA` sections. If nothing is mapped to an `SDATA` section, then the `$S` table will not be created.

`$S` table contains the following columns:

- `SDATA_ID` number is the internal `SDATA` section ID.

- `SDATA_LAST` number, the last document ID, which is analogous to `token_last`.

- `SDATA_DATA` `RAW``(2000)`, the compressed `SDATA` values. Note that if `$S` is created on a tablespace with 4K database block size, then it will be defined as `RAW``(1500)`.

Restriction: For performance reasons, `$S` table must be created on a tablespace with db block size \>= 4K without overflow segment and without `PCTTHRESHOLD` clause. If `$S` is created on a tablespace with db block size \< 4K, or is created with an overflow segment or with a `PCTTHRESHOLD` clause, then appropriate errors will be raised during the `CREATE` `INDEX` statement.

Restrictions on exporting and importing text tables with composite domain index created with `FILTER` `BY` and/or `ORDER` `BY` clauses are as follows:

- Regular `exp` and `imp` will not support exporting and importing of composite domain index. Doing so will lead to the following error: `EXP-00113: Feature Composite Domain Index is unsupported`.

- To export a text table with composite domain index, you must use Data Pump Export and Import utilities (invoked with the `expdp` and `impdp` commands, respectively), or `DBMS_DATAPUMP` PL/SQL package.

**See Also:**

[ADD_SDATA_COLUMN](CTX_DDL-package.md) in [CTX_DDL Package](CTX_DDL-package.md)

Limitations of using `ALTER` `INDEX` and `ALTER` `TABLE` with `FILTER` `BY` and `ORDER` BY columns of the composite domain index, which are imposed by Extensible Indexing Framework in Oracle Database:

(These limitations are imposed by Extensible Indexing Framework in Oracle Database.)

- Using `ALTER` `INDEX` to add or drop `FILTER` `BY` and `ORDER` `BY` columns is currently not supported. You must re-create the index to add or drop `FILTER` `BY` or `ORDER` `BY` columns.

- To use `ALTER` `TABLE` `MODIFY` `COLUMN` to modify the datatype of a column that has the composite domain index built on it, you must first drop the composite domain index before modifying the column.

- To use `ALTER` `TABLE` `DROP` `COLUMN` to drop a column that is part of the composite domain index, you must first drop the composite domain index before dropping the index column.

The following limitations apply to `FILTER` `BY` and `ORDER` `BY` when used with PL/SQL packages:

- Mapping `FILTER` `BY` columns to sections is optional. If section mapping does not exist for a `FILTER` `BY` column, then it is mapped to an `SDATA` section by default. The section name assumes the name of the `FILTER` `BY` column.

- If a section group is not specified during the `CREATE` `INDEX` clause of a composite domain index, then system default section group settings are used. An `SDATA` section is created for each of the `FILTER` `BY` and `ORDER` `BY` columns.

  **Note:**

  Because a section name does not allow certain special characters and is case-insensitive, if the column name is case-sensitive or contains special characters, then an error will be raised. To work around this problem, you must map the column to an `MDATA` or `SDATA` section before creating the index. See CTX_DDL.[ADD_MDATA_COLUMN](CTX_DDL-package.md) or CTX_DDL.[ADD_SDATA_COLUMN](CTX_DDL-package.md).

- An error is raised if a column that is mapped to an `MDATA` section also appears in the `ORDER` `BY` column clause.

- Column section names are unique to their section group. That is, you cannot have an `MDATA` column section named `FOO` if you already have an `MDATA` column section named `FOO`. Nor can you have a field section named `FOO` if you already have an `SDATA` column section named `FOO`. This is true whether it is implicitly created (by `CREATE` `INDEX` for `FILTER` `BY` or `ORDER` `BY` clauses) or explicitly created (by `CTX_DDL.ADD_SDATA_COLUMN`).

- One section name can be mapped to only one `FILTER` `BY` column, and vice versa. Mapping a section to more than one column, or mapping a column to more than one section is not allowed.

- Column sections can be added to any type of section group, including the `NULL` section group.

- If a section group with sections added by the `CTX_DDL.ADD_MDATA_COLUMN` or `CTX_DDL.ADD_SDATA_COLUMN` packages is specified for a `CREATE` `INDEX` statement without a `FILTER` `BY` clause, then the mapped column sections will be ignored. However, the index will still get created without those column sections. The same is true for a `FILTER` `BY` clause that does not contain mapped columns in the specified section group.

**See Also:**

CTX_DDL.[ADD_SDATA_COLUMN](CTX_DDL-package.md)

LOCAL \[PARTITION \[partition\] \[PARAMETERS('paramstring')\]
Specifies a local partitioned context index on a partitioned table. The partitioned table must be partitioned by range. Hash, composite, and list partitions are not supported.

You can specify the list of index partition names with partition_name. If you do not specify a partition name, then the system assigns one. The order of the index partition list must correspond to the table partition order.

The `PARAMETERS` clause associated with each partition specifies the parameters string specific to that partition. You can only specify sync (manual\|every \|on commit), memory and storage for each index partition.

The `PARAMETERS` clause also supports the `POPULATE` and `NOPOPULATE` arguments. See ""POPULATE \| NOPOPULATE"".

Query the views [CTX_INDEX_PARTITIONS](oracle-text-views.md) or [CTX_USER_INDEX_PARTITIONS](oracle-text-views.md) to find out index partition information, such as index partition name, and index partition status.

**See Also:**

"Creating a Local Partitioned Index"

Query Performance Limitation with Partitioned Index

For optimal performance when querying a partitioned index with an `ORDER` `BY` `SCORE` clause, query the partition. If you query the entire table and use an `ORDER` `BY` `SCORE` clause, the query might not perform optimally unless you include a range predicate that can limit the query to the fewest number of partitions, which is optimally a single partition.

**See Also:**

"Query Performance Limitation with a Partitioned Index"

PARALLEL n
Optionally specifies the parallel degree for parallel indexing. The actual degree of parallelism might be smaller depending on your resources. You can use this parameter on nonpartitioned tables. However, creating a nonpartitioned index in parallel does not turn on parallel query processing. Parallel indexing is supported for creating a local partitioned index.

The indexing memory size specified in the parameter clause applies to each parallel worker. For example, if indexing memory size is specified in the parameter clause as 500M and parallel degree is specified as 2, then you must ensure that there is at least 1GB of memory available for indexing.

**See Also:**

- "Parallel Indexing"

- "Creating a Local Partitioned Index in Parallel"

- The "Performance Tuning" chapter in [Oracle Text Application Developer's Guide](../ccapp/tuning-oracle-text.md)

Performance

Parallel indexing can speed up indexing when you have large amounts of data to index and when your operating system supports multiple CPUs.

**Note:**

Using `PARALLEL` to create a local partitioned index that enables parallel queries. (Creating a nonpartitioned index in parallel does not turn on parallel query processing.)

Parallel querying degrades query throughput especially on heavily loaded systems. Because of this, Oracle recommends that you disable parallel querying after creating a local index. To do so, use the `ALTER` `INDEX` `NOPARALLEL` statement.

For more information on parallel querying, see the "Performance Tuning" chapter in [Oracle Text Application Developer's Guide](../ccapp/tuning-oracle-text.md).

Limitations

Parallel indexing is supported only for the `CONTEXT` index type.

UNUSABLE
Creates an unusable index. This creates index metadata only and exits immediately.

You might create an unusable index when you need to create a local partitioned index in parallel.

**See Also:**

"Creating a Local Partitioned Index in Parallel"

PARAMETERS(paramstring)
Optionally specify indexing parameters in `paramstring`. You can specify preferences owned by another user using the `user.preference` notation.

The syntax for `paramstring` is as follows:

    paramstring =
    '[ASYNCHRONOUS_UPDATE | SYNCHRONOUS_UPDATE]
     [DATASTORE datastore_pref]
     [FILTER filter_pref]
     [CHARSET COLUMN charset_column_name]
     [FORMAT COLUMN format_column_name]
     [SAVE_COPY COLUMN save_copy_column_name]

     [LEXER lexer_pref]
     [LANGUAGE COLUMN language_column_name]

     [WORDLIST wordlist_pref]
     [STORAGE storage_pref]
     [STOPLIST stoplist]
     [SECTION GROUP section_group]
     [MEMORY memsize]
     [POPULATE | NOPOPULATE]
     [SYNC (MANUAL | EVERY "interval-string" | ON COMMIT)]
     [TRANSACTIONAL]
     [OPTIMIZE (MANUAL | AUTO_DAILY | EVERY "interval-string")]'

Create datastore, filter, lexer, wordlist, and storage preferences with CTX_DDL.[CREATE_PREFERENCE](CTX_DDL-package.md) and then specify them in the paramstring.

**Note:**

When you specify no paramstring, Oracle Text uses the system defaults.

For more information about these defaults, see "[Default Index Parameters](oracle-text-indexing-elements.md)".

ASYNCHRONOUS_UPDATE \| SYNCHRONOUS_UPDATE
Specifies whether Oracle Text must retain old index entries for documents in which the indexed column was updated. The default is `SYNCHRONOUS_UPDATE` which indicates that index updates are synchronous and that old index entries are unavailable for search operations until the index is synchronized.

`ASYNCHRONOUS_UPDATE` indicates that until the index is synchronized, search queries will use the old index entries to return the old document content. After index synchronization, the rebuilt index is used to return the updated document content.

This option cannot be set at the partition level.

The following example creates a `CONTEXT` index `idx` for which asynchronous update is enabled.

    CREATE INDEX myidx ON mytab1(item_info) INDEXTYPE IS CTXSYS.CONTEXT PARAMETERS('asynchronous_update');

Note: Asynchronous updates are not supported for DML operations that cause row movement.

DATASTORE datastore_pref
Specifies the name of your datastore preference. Use the datastore preference to specify where your text is stored.See "[Datastore Types](oracle-text-indexing-elements.md) ".

FILTER filter_pref
Specifies the name of your filter preference. Use the filter preference to specify how to filter formatted documents to plain text or HTML. See "[Filter Types](oracle-text-indexing-elements.md)".

CHARSET COLUMN charset_column_name
Specifies the name of the character set column. This column must be in the same table as the text column, and it must be of type `CHAR`, `VARCHAR`, or `VARCHAR2`. Use this column to specify the document character set for conversion to the database character set. The value is case-insensitive. You must specify a globalization support character set string, such as JA16EUC.

When the document is plain text or HTML, the `AUTO_FILTER` and `CHARSET` filters use this column to convert the document character set to the database character set for indexing.

Use this column when you have plain text or HTML documents with different character sets or in a character set different from the database character set.

Setting `NLS_LENGTH_SEMANTICS` parameter to `CHAR` is not supported at the database level. This parameter is supported for the following columns:

- The `CHARSET` `COLUMN`, for example:

      VARCHAR2 <size> CHAR
      CHAR <size> CHAR

- An index created on a `VARCHAR2` and `CHAR` column

- `VARCHAR2` and `CHAR` columns for `FILTER` `BY` and `ORDER` `BY` clauses of `CREATE` `INDEX`

- `FORMAT` `COLUMN`

**Note:**

- Documents are not marked for re-indexing when only the character set column changes. The indexed column must be updated to flag the re-index.

- The `NLS_LENGTH_SEMANTICS = CHAR` parameter is supported at the column level only, and is not supported at the database level, as described in this section.

FORMAT COLUMN format_column_name
Specifies the name of the format column. The format column must be in the same table as the text column and it must be `CHAR`, `VARCHAR`, or `VARCHAR2` type.

`FORMAT COLUMN` determines how a document is filtered, or, in the case of the `IGNORE` value, if it is to be indexed.

`AUTO_FILTER` uses the format column when filtering documents. Use this column with heterogeneous document sets to optionally bypass filtering for plain text or HTML documents.

In the format column, you can specify one of the following options:

- `TEXT`

- `BINARY`

- `IGNORE`

The `TEXT` option indicates that the document is either plain text or HTML. When `TEXT` is specified, the document is not filtered, but may have the character set converted.

The `BINARY` option indicates that the document is a format supported by the `AUTO_FILTER` object other than plain text or HTML, for example PDF. `BINARY` is the default, if the format column entry cannot be mapped.

The `IGNORE` option indicates that the row is to be ignored during indexing. Use this value when you need to bypass rows that contain data incompatible with text indexing such as image data, or rows in languages that you do not want to process. The difference between documents with `TEXT` and `IGNORE` format column types is that the former are indexed but ignored by the filter, while the latter are not indexed at all. Thus, `IGNORE` can be used with any filter type.

**Note:**

Documents are not marked for re-indexing when only the format column changes. The indexed column must be updated to flag the re-index.

SAVE_COPY COLUMN save_copy_column_name
Specifies the name of the column that contains the preference of whether to save a copy of a document into the `$D` index table during a search operation.

You can specify one of the following three options in the `SAVE_COPY` column: `PLAINTEXT`, `FILTERED`, or `NONE`.

The `PLAINTEXT` option indicates that the document should be stored as a plain text in the `$D` index table. Specify this value when using the SNIPPET procedure.

The `FILTERED` option indicates that a filter preference should be applied on the text present in the document before storing it into the `$D` index table. Specify this value when using the MARKUP procedure or the HIGHLIGHT procedure.

The `NONE` option indicates that a copy of the document should not be saved in the `$D` index table. Specify this value for any of the following scenarios:

- when SNIPPET, MARKUP, or HIGHLIGHT procedure is not used.

- when the indexed column is either `VARCHAR2` or `CLOB`.

LEXER lexer_pref
Specifies the name of your lexer or multilexer preference. Use the lexer preference to identify the language of your text and how text is tokenized for indexing. See "[Lexer Types](oracle-text-indexing-elements.md)".

LANGUAGE COLUMN language_column_name
Specifies the name of the language column when using a multi-lexer preference. See "[MULTI_LEXER](oracle-text-indexing-elements.md)".

This column must exist in the base table. It cannot be the same column as the indexed column. Only the first 30 bytes of the language column are examined for language identification.

**Note:**

Documents are not marked for re-indexing when only the language column changes. The indexed column must be updated to flag the re-index.

WORDLIST wordlist_pref
Specifies the name of your wordlist preference. Use the wordlist preference to enable features such as fuzzy, stemming, and prefix indexing for better wildcard searching. See "[Wordlist Type](oracle-text-indexing-elements.md)".

STORAGE storage_pref
Specifies the name of your storage preference for the Text index. Use the storage preference to specify how the index tables are stored. See "[Storage Types](oracle-text-indexing-elements.md)".

STOPLIST stoplist
Specifies the name of your stoplist. Use stoplist to identify words that are not to be indexed. See CTX_DDL.[CREATE_STOPLIST](CTX_DDL-package.md) .

SECTION GROUP section_group
Specifies the name of your section group. Use section groups to create searchable sections in structured documents. See CTX_DDL.[CREATE_SECTION_GROUP](CTX_DDL-package.md) .

MEMORY memsize
Specifies the amount of run-time memory to use for indexing. The syntax for `memsize` is as follows:

    memsize = number[K|M|G]

K stands for kilobytes, M stands for megabytes, and G stands for gigabytes.

The value you specify for `memsize` must be between 1M and the value of `MAX_INDEX_MEMORY` in the [CTX_PARAMETERS](oracle-text-views.md) view. To specify a memory size larger than the `MAX_INDEX_MEMORY`, you must reset this parameter with CTX_ADM.[SET_PARAMETER](CTX_ADM-package.md) to be larger than or equal to `memsize`.

The default is the value specified for `DEFAULT_INDEX_MEMORY` in `CTX_PARAMETERS`.

The `memsize` parameter specifies the amount of memory Oracle Text uses for indexing before flushing the index to disk. Specifying a large amount memory improves indexing performance because there are fewer I/O operations and improves query performance and maintenance, because there is less fragmentation.

Specifying smaller amounts of memory increases disk I/O and index fragmentation, but might be useful when run-time memory is scarce.

POPULATE \| NOPOPULATE
Specifies whether an index should be empty or populated. The default is `POPULATE`.

**Note:**

`POPULATE` \| `NOPOPULATE` is the only option whose default value cannot be set with CTX_ADM.[SET_PARAMETER](CTX_ADM-package.md).

Empty indexes are populated by updates or inserts to the base table. You might create an empty index when you need to create your index incrementally or to selectively index documents in the base table. You might also create an empty index when you require only theme and Gist output from a document set.

SYNC (MANUAL \| EVERY "interval-string" \| ON COMMIT)
Specifies `SYNC` for synchronization of the `CONTEXT` index when there are inserts, updates or deletes to the base table. You can specify one of the following `SYNC` methods:

Table 1-7 SYNC Types

| SYNC Type               | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  |
|:------------------------|:---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `MANUAL`                | Provides no automatic synchronization. This is the default. You must manually synchronize the index with `CTX_DDL.SYNC_INDEX`.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                               |
| EVERY "interval-string" | Automatically synchronizes the index at a regular interval specified by the value of interval-string, which takes the same syntax as that for scheduler jobs. Automatic synchronization using `EVERY` requires that the index creator have `CREATE JOB` privileges.<br>Ensure that interval-string is set to a long enough period that any previous sync jobs will have completed; otherwise, the sync job might stop responding. interval-string must be enclosed in double quotes, and any single quote within interval-string must be preceded by the escape character with another single quote.<br>See "Enabling Automatic Index Synchronization" for an example of automatic sync syntax.                                                                                                                                                                                                                                                                                                                                                                                              |
| ON COMMIT               | Synchronizes the index immediately after a commit transaction. The commit transaction does not return until the sync is complete. Before Oracle Database Release 18c, the synchronization was performed as a separate transaction. There was a time period, usually small, when the data was committed but index changes were not. Starting with Oracle Database Release 18c, the synchronization is performed as part of the same transaction.<br>The operation uses the memory specified with the memory parameter.<br>Before Oracle Database Release 18c, the sync operation had its own transaction context. If the operation failed, the data transaction still committed. Starting with Oracle Database Release 18c, if there is an irrecoverable index synchronization error, the entire data transaction is rolled back. Recoverable (individual row) synchronization errors are logged in the `CTX_USER_INDEX_ERRORS` view but the transaction still completes. See "Viewing Index Errors".<br>See "Enabling Automatic Index Synchronization" for an example of `ON COMMIT` syntax. |

Each partition of a locally partitioned index can have its own type of sync (`ON COMMIT`, `EVERY`, or `MANUAL`). The type of sync specified in primary parameter strings applies to all index partitions unless a partition specifies its own type.

With automatic (`EVERY`) synchronization, users can specify memory size and parallel synchronization. That syntax is:

    ... EVERY interval_string MEMORY mem_size PARALLEL paradegree ...

The `ON` `COMMIT` synchronizations can be run only serially and must use the same memory size that was specified at index creation.

**See Also:**

- [Oracle Database Administrator's Guide](../admin/administering-oracle-scheduler.md) for information about job scheduling

- [Oracle Database PL/SQL Packages and Types Reference](../arpls/DBMS_SCHEDULER.md) for information about `DBMS_SCHEDULER`

TRANSACTIONAL
Specifies that documents can be searched immediately after they are inserted or updated. If a text index is created with `TRANSACTIONAL` enabled, then, in addition to processing the synchronized rowids already in the index, the `CONTAINS` operator will process unsynchronized rowids as well. Oracle Text does in-memory indexing of unsynchronized rowids and processes the query against the in-memory index.

`TRANSACTIONAL` is an index-level parameter and does not apply at the partition level.

You must still synchronize your text indexes from time to time (with `CTX_DDL.SYNC_INDEX`) to bring pending rowids into the index. Query performance degrades as the number of unsynchronized rowids increases. For that reason, Oracle recommends setting up your index to use automatic synchronization with the `EVERY` or `ON COMMIT` parameter. (See ""SYNC (MANUAL \| EVERY "interval-string" \| ON COMMIT)"".)

Transactional querying for indexes that have been created with the `TRANSACTIONAL` parameter can be turned on and off (for the duration of a user session) with the PL/SQL variable `CTX_QUERY.disable_transactional_query`. This is useful, for example, if you find that querying is slow due to the presence of too many pending rowids. Here is an example of setting this session variable:

    exec ctx_query.disable_transactional_query := TRUE;

If the index uses `AUTO_FILTER`, queries involving unsynchronized rowids will require filtering of unsynchronized documents.

OPTIMIZE (MANUAL \| AUTO_DAILY \| EVERY "interval-string")
Specify `OPTIMIZE` to enable automatic background index optimization. You can specify any one of the following `OPTIMIZE` methods:

Table 1-8 CREATE INDEX OPTIMIZE Types

| OPTIMIZE Type           | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  |
|:------------------------|:---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| MANUAL                  | Provides no automatic optimization. You must manually optimize the index with `CTX_DDL.OPTIMIZE_INDEX`.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      |
| AUTO_DAILY              | When you specify `OPTIMIZE (AUTO_DAILY)` in the create index parameter list, a repeatedly running optimize token job and a repeatedly running optimize full job are scheduled.<br>• The Optimize token job is scheduled to run every midnight from 12 A.M. to 3 A.M. except on Saturday night, in order to optimize the top 10 most fragmented tokens (determined automatically). Jobs that are not started before 3 A.M. are skipped. These skipped jobs are started before the other jobs that are scheduled to run at 12 A.M. the next day.<br>• The Optimize full job is scheduled to run weekly from 12 A.M. every Saturday night in order to optimize index tables and clean up \$N.<br>Existing indexes do not have `OPTIMIZE (AUTO_DAILY)` by default. You must use `ALTER INDEX` to enable automatic background index optimization. |
| EVERY "interval-string" | Automatically runs optimize token for the top 10 most fragmented tokens at a regular interval specified by the value interval-string, which takes the same syntax as scheduler jobs.<br>Ensure that interval-string is set to a long enough period so that any previous optimize jobs are complete. The interval-string value must be enclosed in double quotes, and any single quote within interval-string must be preceded by an escape character with another single quote.                                                                                                                                                                                                                                                                                                                                                              |

With `AUTO_DAILY | EVERY "``interval-string``"` setting, you can specify parallel optimization. That syntax is:

    ... [AUTO_DAILY | EVERY "interval-string"] PARALLEL paradegree ...

#### CREATE INDEX: CONTEXT Index Examples

The following sections give examples of creating a `CONTEXT` index.

Creating CONTEXT Index Using Default Preferences

The following example creates a `CONTEXT` index called `myindex` on the `docs` column in `mytable`. Default preferences are used.

    CREATE INDEX myindex ON mytable(docs) INDEXTYPE IS ctxsys.context;

**See Also:**

- [Oracle Text Application Developer's Guide](../ccapp/creating-oracle-text-indexes.md)

- For more information about default settings, see "[Default Index Parameters](oracle-text-indexing-elements.md)"

Creating CONTEXT Index with Custom Preferences

The following example creates a `CONTEXT` index called `myindex` on the `docs` column in `mytable`. The index is created with a custom lexer preference called `my_lexer` and a custom stoplist called `my_stop`.

This example also assumes that the preference and stoplist were previously created with CTX_DDL.[CREATE_PREFERENCE](CTX_DDL-package.md) for `my_lexer`, and CTX_DDL.[CREATE_STOPLIST](CTX_DDL-package.md) for `my_stop`. Default preferences are used for the unspecified preferences.

    CREATE INDEX myindex ON mytable(docs) INDEXTYPE IS ctxsys.context
      PARAMETERS('LEXER my_lexer STOPLIST my_stop');

Any user can use any preference. To specify preferences that exist in another user's schema, add the user name to the preference name. The following example assumes that the preferences `my_lexer` and `my_stop` exist in the schema that belongs to user `kenny`:

    CREATE INDEX myindex ON mytable(docs) INDEXTYPE IS ctxsys.context
      PARAMETERS('LEXER kenny.my_lexer STOPLIST kenny.my_stop');

Enabling Automatic Index Synchronization

You can create your index and specify that the index be synchronized at regular intervals for insertions, updates and deletions to the base table. To do so, create the index with the `SYNC` `(``EVERY` `"`interval-string`")` parameter.

To use job scheduling, you must log in as a user who has DBA privileges and then grant `CREATE JOB` privileges.

The following example creates an index and schedules three synchronization jobs for three index partitions. The first partition uses `ON` `COMMIT` synchronization. The other two partitions are synchronized by jobs that are scheduled to be executed every Monday at 3 P.M.

    CONNECT system/password
    GRANT CREATE JOB TO dr_test

    CREATE INDEX tdrmauto02x ON tdrmauto02(text)
       INDEXTYPE IS CTXSYS.CONTEXT local
       (PARTITION tdrm02x_i1 PARAMETERS('
       MEMORY 20m SYNC(ON COMMIT)'),
       PARTITION tdrm02x_i2,
       PARTITION tdrm02x_i3)  PARAMETERS('
       SYNC (EVERY "NEXT_DAY(TRUNC(SYSDATE), ''MONDAY'') + 15/24")
      ');

See [Oracle Database Administrator's Guide](../admin/administering-oracle-scheduler.md) for information about job scheduling syntax.

Enabling Automatic Background Index Optimization

The following example creates an index and schedules a repeatedly running optimize token job at 12 A.M. every midnight and a repeatedly running optimize full job running at 12 A.M. every Saturday night.

    CREATE TABLE mytable (
        text VARCHAR2(30)
    );

    CREATE INDEX myindex ON mytable(text)
        INDEXTYPE IS CTXSYS.CONTEXT
        PARAMETERS('OPTIMIZE (EVERY "FREQ=DAILY; BYHOUR=0")');

Creating CONTEXT Index with Multilexer Preference

The multilexer preference decides which lexer to use for each row based on a language column. This is a character column in the table that stores the language of the document in the text column. For example, create the table `globaldoc` to hold documents of different languages:

    CREATE TABLE globaldoc (
       doc_id NUMBER PRIMARY KEY,
       lang VARCHAR2(10),
       text CLOB
    );

Assume that `global_lexer` is a multilexer preference you created. To index the `global_doc` table, specify the multilexer preference and the name of the language column as follows:

    CREATE INDEX globalx ON globaldoc(text) INDEXTYPE IS ctxsys.context PARAMETERS
    ('LEXER global_lexer LANGUAGE COLUMN lang');

**See Also:**

"[MULTI_LEXER](oracle-text-indexing-elements.md)" for more information about creating multilexer preferences

Creating a Local Partitioned Index

The following example creates a text table that is partitioned into three, populates it, and then creates a partitioned index:

    PROMPT create partitioned table and populate it

    CREATE TABLE part_tab (a int, b varchar2(40)) PARTITION BY RANGE(a)
    (partition p_tab1 values less than (10),
     partition p_tab2 values less than (20),
     partition p_tab3 values less than (30));

    PROMPT create partitioned index
    CREATE INDEX part_idx on part_tab(b) INDEXTYPE IS CTXSYS.CONTEXT
     LOCAL (partition p_idx1, partition p_idx2, partition p_idx3);

**Note:**

The limit for the number of partitions in Oracle Text is the same as the maximum number of partitions per table in Oracle Database.

Using FILTER BY and ORDER BY Clauses

The following example creates an index on table docs and orders the documents by author's publishing date.

First, create the table:

    CREATE TABLE docs (
        docid    NUMBER,
        pub_date DATE,
        author   VARCHAR2(30),
        category VARCHAR2(30),
        document CLOB
    );

Create the index with `FILTER` `BY` and `ORDER` `BY` clauses:

    CREATE INDEX doc_idx on docs(document) indextype is ctxsys.context
      FILTER BY category, author
      ORDER BY pub_date desc, docid
      PARAMETERS ('memory 500M');

Parallel Indexing

Parallel indexing can improve index performance when you have multiple CPUs.

To create an index in parallel, use the `PARALLEL` clause with a parallel degree. This example uses a parallel degree of 3:

    CREATE INDEX myindex ON mytab(pk) INDEXTYPE IS ctxsys.context PARALLEL 3;

Creating a Local Partitioned Index in Parallel

Creating a local partitioned index in parallel can improve performance when you have multiple CPUs. With partitioned tables, you can divide the work. You can create a local partitioned index in parallel in two ways:

- Use the `PARALLEL` clause with the `LOCAL` clause in the `CREATE INDEX` statement. In this case, the maximum parallel degree is limited to the number of partitions you have. See "Parallelism with CREATE INDEX".

- Create an unusable index first, then run the `DBMS_PCLXUTIL.BUILD_PART_INDEX` utility. This method can result in a higher degree of parallelism, especially if you have more CPUs than partitions. See "Parallelism with DBMS_PCLUTIL.BUILD_PART_INDEX".

If you attempt to create a local partitioned index in parallel, and the attempt fails, you may see the following error message:

    ORA-29953: error in the execution of the ODCIIndexCreate routine for one or more
    of the index partitions

To determine the specific reason why the index creation failed, query the [CTX_USER_INDEX_ERRORS](oracle-text-views.md) view.

Parallelism with CREATE INDEX

You can achieve local index parallelism by using the `PARALLEL` and `LOCAL` clauses in the `CREATE INDEX` statement. In this case, the maximum parallel degree is limited to the number of partitions that you have.

The following example creates a table with three partitions, populates them, and then creates the local indexes in parallel with a degree of 2:

    create table part_tab3(id number primary key, text varchar2(100))
    partition by range(id)
    (partition p1 values less than (1000),
     partition p2 values less than (2000),
     partition p3 values less than (3000));

    begin
      for i in 0..2999
      loop
          insert into part_tab3 values (i,'oracle');
      end loop;
    end;
    /

    create index part_tab3x on part_tab3(text)
    indextype is ctxsys.context local (partition part_tabx1,
                                       partition part_tabx2,
                                       partition part_tabx3)
    parallel 2;

Parallelism with DBMS_PCLUTIL.BUILD_PART_INDEX

You can achieve local index parallelism by first creating an unusable `CONTEXT` index, and then running the [`DBMS_PCLUTIL.BUILD_PART_INDEX`](../arpls/DBMS_PCLXUTIL.md) utility. This method can result in a higher degree of parallelism, especially when you have more CPUs than partitions.

In this example, the base table has three partitions. We create a local partitioned unusable index first, then run [`DBMS_PCLUTIL.BUILD_PART_INDEX`](../arpls/DBMS_PCLXUTIL.md), which builds the 3 partitions in parallel (referred to as inter-partition parallelism). Also, inside each partition, index creation proceeds in parallel (called intra-partition parallelism) with a parallel degree of 2. Therefore, the total parallel degree is 6 (3 times 2).

    create table part_tab3(id number primary key, text varchar2(100))
    partition by range(id)
    (partition p1 values less than (1000),
     partition p2 values less than (2000),
     partition p3 values less than (3000));

    begin
      for i in 0..2999
      loop
          insert into part_tab3 values (i,'oracle');
      end loop;
    end;
    /

    create index part_tab3x on part_tab3(text)
    indextype is ctxsys.context local (partition part_tabx1,
                                       partition part_tabx2,
                                       partition part_tabx3)
    unusable;

    exec dbms_pclxutil.build_part_index(jobs_per_batch=>3,
      procs_per_job=>2,
      tab_name=>'PART_TAB3',
      idx_name=>'PART_TAB3X',
      force_opt=>TRUE);

Viewing Index Errors

After a `CREATE` `INDEX` or `ALTER` `INDEX` operation, you can view index errors with Oracle Text views. To view errors on your indexes, query the [CTX_USER_INDEX_ERRORS](oracle-text-views.md) view. To view errors on all indexes as `CTXSYS`, query the [CTX_INDEX_ERRORS](oracle-text-views.md) view.

For example, to view the most recent errors on your indexes, enter the following statement:

    SELECT err_timestamp, err_text FROM ctx_user_index_errors
    ORDER BY err_timestamp DESC;

Deleting Index Errors

To clear the index error view, enter the following statement:

    DELETE FROM ctx_user_index_errors;

#### Syntax for CTXCAT Index Type

Combines an index on a text column and one or more other columns. Query this index with the `CATSEARCH` operator in the `WHERE` clause of a `SELECT` statement. This type of index is optimized for mixed queries. This index is transactional, automatically updating itself with DML to the base table.

    CREATE INDEX [schema.]index on [schema.]table(column) INDEXTYPE IS ctxsys.ctxcat
    [PARAMETERS('[index set index_set]
    [lexer lexer_pref]
    [storage storage_pref]
    [stoplist stoplist]
    [section group sectiongroup_pref]
    [wordlist wordlist_pref]
    [memory memsize]');

\[schema.\]table(column)
Specifies the name of the table and column to index.

The column that you specify when you create a `CTXCAT` index must be of type `CHAR` or `VARCHAR2`. No other types are supported for `CTXCAT`.

Attempting to create an index on a Virtual Private Database (VPD) protected table will fail unless one of the following options is true:

- The VPD policy is created such that it does not apply to `INDEX` statement type, which is the default

- The policy function returns a null predicate for the current user.

- The user (index owner) is `SYS`.

- The user has the `EXEMPT` `ACCESS` `POLICY` privilege.

#### Supported CTXCAT Preferences

index set index_set
Specifies the index set preference to create the `CTXCAT` index. Index set preferences name the columns that make up your subindexes. Any column that is named in an index set column list cannot have a `NULL` value in any row of the base table, or else you get an error.

Always ensure that your columns have non-null values before and after indexing.

See "Creating a CTXCAT Index".

Index Performance and Size Considerations

Although a `CTXCAT` index offers query performance benefits, creating this type of index has its costs. The time that it takes Oracle Text to create a `CTXCAT` index depends on the total size of the index.

The total size of a `CTXCAT` index is directly related to:

- Total text to be indexed

- Number of component indexes in the index set

- Number of columns in the base table that make up the component indexes

Having many component indexes in your index set also degrades DML performance because more indexes must be updated.

Because of these added costs in creating a `CTXCAT` index, you should carefully consider the query performance benefit that each component index gives your application before adding it to your index set.

**See Also:**

[Oracle Text Application Developer's Guide](../ccapp/creating-oracle-text-indexes.md) for more information about creating `CTXCAT` indexes and the benefits

Other CTXCAT Preferences
When you create an index of type `CTXCAT`, you can use the supported index preferences listed in Table 1-9 in the `parameters` string.

Table 1-9 Supported CTXCAT Index Preferences

| Preference Class | Supported Types                                                                                                                                                                                                                                                                                                                                                                      |
|:-----------------|:-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Datastore        | This preference class is not supported for `CTXCAT`.                                                                                                                                                                                                                                                                                                                                 |
| Filter           | This preference class is not supported for `CTXCAT`.                                                                                                                                                                                                                                                                                                                                 |
| Lexer            | [BASIC_LEXER](oracle-text-indexing-elements.md) (`index_themes` attribute not supported)<br>[CHINESE_LEXER](oracle-text-indexing-elements.md)<br>[CHINESE_VGRAM_LEXER](oracle-text-indexing-elements.md)<br>[JAPANESE_LEXER](oracle-text-indexing-elements.md)<br>[JAPANESE_VGRAM_LEXER](oracle-text-indexing-elements.md)<br>[KOREAN_MORPH_LEXER](oracle-text-indexing-elements.md) |
| Wordlist         | [BASIC_WORDLIST](oracle-text-indexing-elements.md)                                                                                                                                                                                                                                                                                                                                   |
| Storage          | [BASIC_STORAGE](oracle-text-indexing-elements.md)                                                                                                                                                                                                                                                                                                                                    |
| Stoplist         | Supports single language stoplists only (`BASIC_STOPLIST` type).                                                                                                                                                                                                                                                                                                                     |
| Section Group    | Only Field Section is supported for `CTXCAT`.                                                                                                                                                                                                                                                                                                                                        |

#### Unsupported Preferences and Parameters

When you create a `CTXCAT` index, you cannot specify datastore and filter preferences. For section group preferences, only the field section preference is supported. You also cannot specify language, format, or charset columns as with a `CONTEXT` index.

#### Creating a CTXCAT Index

This section gives a brief example for creating a `CTXCAT` index. For a more complete example, see [Oracle Text Application Developer's Guide](../ccapp/creating-oracle-text-indexes.md).

Consider a table called `AUCTION` with the following schema:

    create table auction(item_id number,
    title varchar2(100),
    category_id number,
    price number,
    bid_close date);

Assume that queries on the table involve a mandatory text query clause and optional structured conditions on `price`. Results must be sorted based on `bid_close`. This means that an index to support good response time for the structured and sorting criteria is required.

You can create a catalog index to support the different types of structured queries a user might enter. For structured queries, a `CTXCAT` index improves query performance over a context index.

To create the indexes, first, create the index set preference, next, optionally, add the storage preference, and, finally, add the required indexes to it:

    begin
    ctx_ddl.create_index_set('auction_iset');
    ctx_ddl.add_index('auction_iset','bid_close');
    ctx_ddl.add_index('auction_iset','price, bid_close');
    end;

Optionally, create the storage preference:

    begin
     ctx_ddl.create_preference('auction_st_pref', 'BASIC_STORAGE');
     ctx_ddl.set_attribute('auction_st_pref', 'I_TABLE_CLAUSE',
                           'tablespace TEXT storage (initial 5M)');
     ctx_ddl.set_attribute('auction_st_pref', 'I_ROWID_INDEX_CLAUSE',
                            'tablespace TEXT storage (initial 5M)');
     ctx_ddl.set_attribute('auction_st_pref', 'I_INDEX_CLAUSE',
                            'tablespace TEXT storage (initial 5M) compress 2');
    end;
    /

Then, create the `CTXCAT` index with the `CREATE` `INDEX` statement as follows:

    create index auction_titlex on AUCTION(title) indextype is CTXSYS.CTXCAT
    parameters ('index set auction_iset storage auction_st_pref');

Querying a CTXCAT Index

To query the title column for the word pokemon, enter regular and mixed queries as follows:

    select * from AUCTION where CATSEARCH(title, 'pokemon',NULL)> 0;
    select * from AUCTION where CATSEARCH(title, 'pokemon', 'price < 50 order by
    bid_close desc')> 0;

**See Also:**

[Oracle Text Application Developer's Guide](../ccapp/creating-oracle-text-indexes.md) for a complete `CTXCAT` example

#### Syntax for CTXRULE Index Type

The `CTXRULE` type is an index on a column containing a set of queries. Query this index with the `MATCHES` operator in the `WHERE` clause of a `SELECT` statement.

    CREATE INDEX [schema.]index on [schema.]table(rule_col) INDEXTYPE IS
    ctxsys.ctxrule
    [PARAMETERS ('[lexer lexer_pref] [storage storage_pref]
    [section group section_pref] [wordlist wordlist_pref]
    [classifier classifier_pref]');

    [PARALLEL n];

\[schema.\]table(column)
Specifies the name of the table and rule column to index. The rules can be query compatible strings, query template strings, or binary Support Vector Machine rules.

The column you specify when you create a `CTXRULE` index must be `VARCHAR2`, `CLOB or BLOB`. No other types are supported for the `CTXRULE` type.

Attempting to create an index on a Virtual Private Database (VPD) protected table will fail unless one of the following is true:

- The VPD policy does not have the `INDEX` statement type turned on (which is the default).

- The policy function returns a null predicate for the current user.

- The user (index owner) is `SYS`.

- The user has the `EXEMPT` `ACCESS` `POLICY` privilege.

lexer_pref
Specifies the lexer preference to be used for processing queries and later for the documents to be classified with the `MATCHES` function.

With both classifiers `SVN_CLASSFIER` and `RULE_CLASSIFIER`, you can use the `BASIC_LEXER`, `CHINESE_LEXER`, `JAPANESE_LEXER`, or `KOREAN_MORPH_LEXER` lexer. (See "[Classifier Types](oracle-text-indexing-elements.md)" and "[Lexer Types](oracle-text-indexing-elements.md)".)

For processing queries, these lexers support the following operators: `ABOUT`, `STEM`, `AND`, `NEAR`, `NOT`, `OR`, and `WITHIN`.

The thesaural operators (`BT*`, `NT*`, `PT`, `RT`, `SYN`, `TR`, `TRSYS`, `TT,` and so on) are supported. However, these operators are expanded using a snapshot of the thesaurus at index time, not when the `MATCHES` function is entered. This means that if you change your thesaurus after you index, you must re-index your query set.

storage_pref
Specify the storage preference for the index on the queries. Use the storage preference to specify how the index tables are stored. See "[Storage Types](oracle-text-indexing-elements.md)".

section group
Specify the section group. This parameter does not affect the queries. It applies to sections in the documents to be classified. The following section groups are supported for the `CTXRULE` index type:

- `BASIC_SECTION_GROUP`

- `HTML_SECTION_GROUP`

- `XML_SECTION_GROUP`

- `AUTO_SECTION_GROUP`

See "[Section Group Types](oracle-text-indexing-elements.md)".

`CTXRULE` does not support special sections. It also does not support `NDATA` sections.

wordlist_pref
Specifies the wordlist preferences. This is used to enable stemming operations on query terms. See [Wordlist Type](oracle-text-indexing-elements.md).

classifier_pref
Specifies the classifier preference. See "[Classifier Types](oracle-text-indexing-elements.md)". You must use the same preference name you specify with `CTX_CLS.TRAIN`.

#### Example for Creating a CTXRULE Index

See [Oracle Text Application Developer's Guide](../ccapp/creating-oracle-text-indexes.md) for a complete example of using the `CTXRULE` index type in a document routing application.

#### Related Topics

CTX_DDL.[CREATE_PREFERENCE](CTX_DDL-package.md)

CTX_DDL.[CREATE_STOPLIST](CTX_DDL-package.md)

CTX_DDL.[CREATE_SECTION_GROUP](CTX_DDL-package.md)

"ALTER INDEX "

"CATSEARCH "

### 1.6 CREATE SEARCH INDEX

Use the `CREATE SEARCH INDEX` statement to create a JSON search index.

#### Purpose

**Note:**

Search indexes do not support the shadow index.

Search indexes that are partitioned do not support the naming of index partitions because these indexes use system-managed partitioning.

You can create a JSON Search Index on a `VARCHAR2`, `CLOB`, or `BLOB` data type column with an `IS JSON` check constraint. To index JSON data, you must specify the `FOR JSON` clause in the `CREATE SEARCH INDEX` statement.

**Note:**

You can create a JSON Search Index only on a column with an `IS JSON` check constraint.

Example

    create table t1 (txn_date date, po CLOB, constraint c1 check (po is json));
    create search index idx on t1(po) for JSON parameters(‘DATAGUIDE ON sync (on commit)’);

#### Syntax

You can use a simpler alternative syntax to create a search index on JSON.

    CREATE SEARCH INDEX [schema.]index ON [schema.]table(json_column) FOR JSON
    [LOCAL]
    PARAMETERS(
      [DATAGUIDE ON [CHANGE (ADD_VC | function_name)] | OFF]
      [STORAGE storage_pref]
      [SEARCH_ON (NONE | TEXT | TEXT_VALUE)]
      [MEMORY memsize]
      [SYNC (MANUAL | EVERY "interval-string" | ON COMMIT)]
      [OPTIMIZE (MANUAL | EVERY "interval-string" | AUTO_DAILY)]
    )
    [PARALLEL N]
    [UNUSABLE];

If the `PARAMETERS` clause is omitted, then the default values for `DATAGUIDE`, `SEARCH_ON` and `SYNC` are `ON`, `TEXT_VALUE` and `ON COMMIT` respectively.

\[schema.\]index
Specifies the name of the JSON search index to create.

\[schema.\]table(json_col)
Specifies the name of the table and the JSON column to index. `json_col` is the name of the JSON column on which the index is created.

The column must have an `IS JSON` check constraint.

LOCAL
Creates a local partitioned JSON search index on a partitioned table. The index is partitioned using the partitioning scheme of the base table.

You can partition a table using range, list, hash, interval, range-composite (range, list, and hash), list-composite (range, list, and hash), and hash-composite (range, list, and hash) partitioning schemes. You can create a local JSON search index using reference partitioning if the base table of the reference partitioned table is partitioned using any of the supported schemes.

**Note:**

You cannot create a local JSON search index on an interval-composite partitioned table.

The following example shows how to create a table that is partitioned into three, populate it, and then create a partitioned JSON search index:

    PROMPT create partitioned table and populate it

    CREATE TABLE part_tab (a int, b CLOB check (b IS JSON)) PARTITION BY RANGE (a)
    (partition p_tab1 values less than (10),
     partition p_tab2 values less than (20),
     partition p_tab3 values less than (30));

    PROMPT create partitioned JSON search index
    CREATE SEARCH INDEX part_idx ON part_tab (b) FOR JSON LOCAL;

**See Also:**

- "Creating a Local Partitioned Index"
- "[System Managed Domain Index - Supported Schemes](../addci/building-domain-indexes.md)" in Oracle Database Data Cartridge Developer's Guide

DATAGUIDE ON \| OFF
Specifies data guide support for an existing JSON search index. If you enable the JSON data guide support, then you can also define change-trigger procedures.

Specify one of the following options:

- `ON`: Enables data guide support. If you set the value of `DATAGUIDE` to `ON`, then you can also define your own PL/SQL procedure or use the predefined change-trigger procedure `ADD_VC`.

  `ADD_VC` indicates if virtual columns are created based on the data guide.

  `function_name` specifies the function to be executed when the data guide changes.

- `OFF`: Disables both the data guide support and change-trigger procedures. Provides only general search-index functionality.
  **Note:**

  You cannot create an index with the `SEARCH_ON` clause set to `NONE` when the `DATAGUIDE` feature is disabled.

See "[Change Triggers For Data Guide-Enabled Search Index](../adjsn/json-dataguide.md)" in Oracle Database JSON Developer's Guide.

STORAGE storage_pref
Specifies the name of your storage preference for JSON search index. Use the storage preference to specify how index tables are stored. See "[Storage Types](oracle-text-indexing-elements.md)".

SEARCH_ON (NONE \| TEXT \| TEXT_VALUE)
Specifies search preferences for JSON search index. Enabling a search option rebuilds the index with updated preferences.

Specify one of the following options:

- `NONE`: Indicates that the tables used for full-text and range searches are not populated. Only the index data guide is maintained. The index will not be used by any JSON query operators, including `JSON_TEXTCONTAINS`.

- `TEXT`: Indicates that full-text search queries use the search index.

- `TEXT_VALUE`: Indicates that both the full-text and range-based indexes are created for numeric and date-time values.

Specifying `TEXT_VALUE` has a higher cost in indexing time and index space.

MEMORY memsize
Specifies the amount of run-time memory to use for indexing. The syntax for `memsize` is as follows:

    memsize = number[K|M|G]

K stands for kilobytes, M stands for megabytes, and G stands for gigabytes.

The value you specify for `memsize` must be between 1M and the value of `MAX_INDEX_MEMORY` in the [CTX_PARAMETERS](oracle-text-views.md) view. To specify a memory size larger than the `MAX_INDEX_MEMORY`, you must reset this parameter with CTX_ADM.[SET_PARAMETER](CTX_ADM-package.md) to be larger than or equal to `memsize`.

The default is the value specified for `DEFAULT_INDEX_MEMORY` in `CTX_PARAMETERS`.

The `memsize` parameter specifies the amount of memory Oracle Text uses for indexing before flushing the index to disk. Specifying a large amount memory improves indexing performance because there are fewer I/O operations and improves query performance and maintenance, because there is less fragmentation.

Specifying smaller amounts of memory increases disk I/O and index fragmentation, but might be useful when run-time memory is scarce.

SYNC (MANUAL \| EVERY "interval-string" \| ON COMMIT)
Specifies `SYNC` for automatic synchronization of the `CONTEXT` index when there are inserts, updates or deletes to the base table. You can specify one of the `SYNC` methods as described in Table 1-7.

Each partition of a locally partitioned index can have its own type of sync (`ON COMMIT`, `EVERY`, or `MANUAL`). The type of sync specified in primary parameter strings applies to all index partitions. The `ON COMMIT` sync is the default synchronization method for JSON search indexes. The `ON COMMIT` sync can be run only serially and must use the same memory size that was specified at index creation.

With automatic (`EVERY`) synchronization, you can specify memory size and parallel synchronization. You can define repeating schedules in the interval-string argument using calendaring syntax values. These values are described in [Oracle Database PL/SQL Packages and Types Reference](../arpls/DBMS_SCHEDULER.md).

Syntax:

    SYNC [EVERY "interval-string"] MEMORY mem_size PARALLEL paradegree

Example:

    SYNC [EVERY "freq=secondly;interval=20"] MEMORY 500M PARALLEL 2

The following examples create a JSON search index with automatic (`EVERY`) synchronization:

- Starting every night at 1:00 A.M.:
      CREATE SEARCH INDEX nightly_refreshed ON purchase_orders(json_document) FOR JSON PARAMETERS('SYNC (EVERY "freq=daily; byhour=1")');
- Starting every 5 minutes:
      CREATE SEARCH INDEX nightly_refreshed ON purchase_orders(json_document) FOR JSON PARAMETERS('SYNC (EVERY "freq=minutely; interval=5")');

OPTIMIZE
Specify `OPTIMIZE` to enable automatic background index optimization. You can specify the `OPTIMIZE` methods as described in Table 1-8.

With `AUTO_DAILY | EVERY "``interval-string``"` setting, you can specify parallel optimization. That syntax is:

    ... [AUTO_DAILY | EVERY "interval-string"] PARALLEL paradegree ...

**Related Topics**

- [Oracle Database Administrator’s Guide](../admin/administering-oracle-scheduler.md)
- [Oracle Database JSON Developer’s Guide](../adjsn/indexes-for-json-data.md)

### 1.7 DROP INDEX

**Note:**

This section describes the `DROP` `INDEX` statement as it pertains to dropping a Text domain index.

For a complete description of the `DROP` `INDEX` statement, see[ Oracle Database SQL Language Reference.](../sqlrf/DROP-INDEX.md)

#### Purpose

Use `DROP` `INDEX` to drop a specified Text index.

#### Syntax

    DROP INDEX [schema.]index [force];

\[force\]
Optionally forces the index to be dropped. Use the `force` option when Oracle Text cannot determine the state of the index, such as when an indexing operation fails.

Oracle recommends against using this option by default. Use it only when a regular call to `DROP` `INDEX` fails.

#### Example

The following example drops an index named `doc_index`in the current user's database schema:

    DROP INDEX doc_index;

#### Related Topics

"ALTER INDEX "

"CREATE INDEX"

### 1.8 MATCHES

Use the `MATCHES` operator to find all rows in a query table that match a given document. The document must be a plain text, HTML, or XML document.

The `MATCHES` operator also supports database links. You can identify a remote table or materialized view by appending `@dblink` to the end of its name. The `dblink` must be a complete or partial name for a database link to the database containing the remote table or materialized view. (Querying of remote views is not supported.)

This operator requires a `CTXRULE` index on your set of queries.

When the [SVM_CLASSIFIER](oracle-text-indexing-elements.md) classifier type is used, `MATCHES` returns a score in the range 0 to 100; a higher number indicates a greater confidence in the match. Use the `label` parameter and `MATCH_SCORE` to obtain this number. Then use the matching score to apply a category-specific threshold to a particular category.

If the `SVM_CLASSIFIER` type is not used, then this operator returns either 100 (the document matches the criteria) or 0 (the document does not match).

#### Limitation

If the optimizer chooses to use the functional query invocation with a `MATCHES` query, your query will fail.

#### Syntax

    MATCHES(

    [schema.]column,
    document VARCHAR2 or CLOB
    [,label INTEGER])

    RETURN NUMBER;

column
Specifies the column containing the indexed query set.

document
Specifies the document to be classified. The document can be plain text, HTML, or XML. Binary formats are not supported.

label
Optionally specifies the label that identifies the score generated by the `MATCHES` operator. Use this label with MATCH_SCORE.

#### Matches Example

The following example creates a table `querytable`, and populates it with classification names and associated rules. It then creates a `CTXRULE` index.

The example enters the `MATCHES` query with a document string to be classified. The `SELECT` statement returns all rows (queries) that are satisfied by the document:

    create table querytable (classification varchar2(64), text varchar2(4000));
    insert into querytable values ('common names', 'smith OR jones OR brown');
    insert into querytable values ('countries', 'United States OR Great Britain OR
    France');
    insert into querytable values ('Oracle DB', 'oracle NEAR database');

    create index query_rule on querytable(text) indextype is ctxsys.ctxrule;

    SELECT classification FROM querytable WHERE MATCHES(text, 'Smith is a common name
    in the United States') > 0;

    CLASSIFICATION
    ----------------------------------------------------------------
    common names
    countries

#### Related Topics

"MATCH_SCORE"

"Syntax for CTXRULE Index Type"

CTX_CLS.[TRAIN](CTX_CLS-package.md)

[Oracle Text Application Developer's Guide](../ccapp/classifying-documents-in-oracle-text.md) contains extended examples of simple and supervised classification, which make use of the `MATCHES` operator.

### 1.9 MATCH_SCORE

Use the `MATCH_SCORE` operator in a statement to return scores produced by a `MATCHES` query.

The `MATCH_SCORE` operator also supports database links. You can identify a remote table or materialized view by appending `@dblink` to the end of its name. The `dblink` must be a complete or partial name for a database link to the database containing the remote table or materialized view. (Querying of remote views is not supported.)

When the `SVM_CLASSIFIER` classifier type is used, this operator returns a score in the range 0 to 100. Use the matching score to apply a category-specific threshold to a particular category.

If the `SVM_CLASSIFIER` classifier is not used, then this operator returns either 100 (the document matches the criteria) or 0 (the document does not match).

#### Syntax

    MATCH_SCORE(label NUMBER)

label
Specifies a number to identify the score produced by the query. Use this number to identify the `MATCHES` clause that returns this score.

#### Example

To get the matching score, use:

    select cat_id, match_score(1) from training_result where matches(profile,
    text,1)>0;

#### Related Topics

"MATCHES "

### 1.10 SCORE

Use the `SCORE` operator in a `SELECT` statement to return the score values produced by a CONTAINS query. The `SCORE` operator can be used in a `SELECT`, `ORDER` `BY`, or `GROUP` `BY` clause.

The `SCORE` operator also supports database links. You can identify a remote table or materialized view by appending `@dblink` to the end of its name. The `dblink` must be a complete or partial name for a database link to the database containing the remote table or materialized view. (Querying of remote views is not supported.)

#### Syntax

    SCORE(label NUMBER)

label
Specifies a number to identify the score produced by the query. Use this number to identify the `CONTAINS` clause that returns this score.

#### Example

Single CONTAINS

When the `SCORE` operator is called (for example, in a `SELECT` clause), the `CONTAINS` clause must reference the score label value as in the following example:

    SELECT SCORE(1), title from newsindex
               WHERE CONTAINS(text, 'oracle', 1) > 0 ORDER BY SCORE(1) DESC;

Multiple CONTAINS

Assume that a news database stores and indexes the title and body of news articles separately. The following query returns all the documents that include the words Oracle in their title and java in their body. The articles are sorted by the scores for the first `CONTAINS` (Oracle) and then by the scores for the second `CONTAINS` (java).

    SELECT title, body, SCORE(10), SCORE(20)

    FROM news
    WHERE CONTAINS (news.title, 'Oracle', 10) > 0 OR

    CONTAINS (news.body, 'java', 20) > 0
    ORDER BY SCORE(10), SCORE(20);

#### Related Topics

"CONTAINS"

[The Oracle Text Scoring Algorithm](oracle-text-scoring-algorithm.md)
