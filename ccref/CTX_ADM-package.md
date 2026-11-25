## 5  CTX_ADM Package

This chapter contains the following topics.

- About CTX_ADM Package Procedures

- MARK_FAILED

- RECOVER

- RESET_AUTO_OPTIMIZE_STATUS

- SET_PARAMETER

### 5.1 About CTX_ADM Package Procedures

The `CTX_ADM` PL/SQL package provides administrative procedures for managing index preferences.

The `CTX_ADM` package contains the following stored procedures.

| Name                       | Description                                                         |
|:---------------------------|:--------------------------------------------------------------------|
| MARK_FAILED                | Changes an index's status from `LOADING` to `FAILED`.               |
| RECOVER                    | Cleans up database objects for deleted Text tables.                 |
| RESET_AUTO_OPTIMIZE_STATUS | Resets the [`CTX_AUTO_OPTIMIZE_STATUS`](oracle-text-views.md) view. |
| SET_PARAMETER              | Sets system-level defaults for index creation.                      |

**Note:**

Only the `CTXSYS` user can use the procedures in the `CTX_ADM` package.

The APIs in the `CTX_ADM` package do not support identifiers that are prefixed with the schema or the owner name.

### 5.2 MARK_FAILED

Use the `MARK_FAILED` procedure to change the status of an index from `LOADING` to `FAILED`.

Under rare circumstances, if `CREATE INDEX` or `ALTER INDEX` fails, an index may be left with the status `LOADING`. When an index is in `LOADING` status, any attempt to recover using `RESUME INDEX` is blocked. For this situation, use `CTX_ADM.MARK_FAILED` to forcibly change the status from `LOADING` to `FAILED` so that you can recover the index with `RESUME INDEX`.

You must log on as `CTXSYS` to run `CTX_ADM.MARK_FAILED`.

**WARNING:**

Use `CTX_ADM.MARK_FAILED` with caution. It should only be used as a last resort and only when no other session is touching the index. Normally, `CTX_ADM.MARK_FAILED` does not succeed if another session is actively building the index with `CREATE` or `ALTER` `INDEX`. However, index creation or alteration may include windows of time during which `CTX_ADM.MARK_FAILED` can succeed, marking the index as failed even as it is being built by another session.

`CTX_ADM.MARK_FAILED` works with local partitioned indexes. However, it changes the status of all partitions to `FAILED`. Therefore, you should rebuild all index partitions with `ALTER INDEX REBUILD PARTITION PARAMETERS ('RESUME')` after using `CTX_ADM.MARK_FAILED`. If you run `ALTER INDEX PARAMETER ('RESUME')` after this operation, then Oracle resets the index partition status to valid. Oracle does not rebuild the index partitions that were successfully built before the `MARK_FAILED` operation.

#### Syntax

    CTX_ADM.MARK_FAILED(
      owner_name     in    VARCHAR2,
      index_name     in    VARCHAR2);

owner_name
The name of the owner of the index whose status is to be changed.

index_name
The name of the index whose status is to be changed.

**Note:**

The `index_name` must not be prefixed by the schema or the owner name.

#### Example

    begin
       CTX_ADM.MARK_FAILED('owner_1', 'index_1');
    end;

### 5.3 RECOVER

The `RECOVER` procedure cleans up the Text data dictionary, deleting objects such as leftover preferences.

#### Syntax

    CTX_ADM.RECOVER;

#### Example

    begin
       ctx_adm.recover;
    end;

### 5.4 RESET_AUTO_OPTIMIZE_STATUS

Use the `RESET_AUTO_OPTIMIZE_STATUS` procedure to reset (or delete the contents of) the [CTX_AUTO_OPTIMIZE_STATUS](oracle-text-views.md) view.

You must log on as `CTXSYS` to run `CTX_ADM.RESET_AUTO_OPTIMIZE_STATUS`.

#### Syntax

    CTX_ADM.RESET_AUTO_OPTIMIZE_STATUS;

#### Example

    begin
       ctx_adm.reset_auto_optimize_status;
    end;

### 5.5 SET_PARAMETER

The `SET_PARAMETER` procedure sets system-level parameters for index creation and for near real-time indexes.

#### Syntax

    CTX_ADM.SET_PARAMETER(param_name IN VARCHAR2,
                          param_value IN VARCHAR2);

param_name
Specify the name of the parameter to set, which can be one of the following parameters:

- `max_index_memory` (maximum memory allowed for indexing)

- `default_index_memory` (default memory allocated for indexing)

- `ctx_doc_key_type` (default input key type for `CTX_DOC` procedures)

- `auto_optimize` (`ENABLE` or `DISABLE` for auto optimization)

- `default_datastore` (default datastore preference)

- `default_filter_file` (default filter preference for data stored in files)

- `default_filter_text` (default text filter preference)

- `default_filter_binary` (default binary filter preference)

- `default_section_html` (default html section group preference)

- `default_section_xml` (default xml section group preference)

- `default_section_text` (default text section group preference)

- `default_lexer` (default lexer preference)

- `default_wordlist` (default wordlist preference)

- `default_stoplist` (default stoplist preference)

- `default_storage` (default storage preference)

- `default_ctxcat_lexer` (default lexer preference for CTXCAT index)

- `default_ctxcat_stoplist` (default stoplist preference for CTXCAT index)

- `default_ctxcat_storage` (default CTXCAT index storage

- `default_ctxcat_wordlist` (default wordlist preference for CTXCAT index)

- `default_ctxrule_lexer` (default lexer for CTXRULE index)

- `default_ctxrule_stoplist` (default stoplist for CTXRULE index)

- `default_ctxrule_storage` (default storage for CTXRULE index)

- `default_ctxrule_wordlist` (default wordlist for CTXRULE index)

  **See Also:**

  To learn more about the default values for these parameters, see "[System Parameters](oracle-text-indexing-elements.md)" in [Oracle Text Indexing Elements](oracle-text-indexing-elements.md)

**Note:**

`log_directory` (directory for `CTX_OUTPUT` files) and `auto_optimize_logfile` (the base file name for the auto optimization log file) can no longer be modified. Any call to the API is ignored for these parameters.

param_value
Specify the value to assign to the parameter. For `max_index_memory` and `default_index_memory`, the value you specify must have the following syntax:

    number[K|M|G]

where K stands for kilobytes, M stands for megabytes, and G stands for gigabytes.

For each of the other parameters, specify the name of a preference to use as the default for indexing.

For `auto_optimize`, the value you specify must be either `ENABLE` or `DISABLE`. When you set this parameter to `ENABLE`, auto optimization jobs can be started. When you set this parameter to `DISABLE`, no auto optimization jobs can be started and all the currently-running optimization jobs are terminated.

#### Example

To modify the `MAX_INDEX_MEMORY` value:

`exec ctx_adm.set_parameter(‘MAX_INDEX_MEMORY’, 100G);`

The memory parameter in the indexing statements can be as high as 256 GB (if the `MAX_INDEX_MEMORY` parameter is not explicitly specified to a lower value).

    create index myindex1 on mytab(textcol) indextype is ctxsys.context parameters ('memory 256G');
    exec ctx_ddl.sync_index(' myindex2', memory=> '256G');

#### Example

    begin
      ctx_adm.set_parameter('default_lexer', 'my_lexer');
    end;
