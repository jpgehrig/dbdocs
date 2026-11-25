## 11  CTX_OUTPUT Package

This chapter provides reference information for using the `CTX_OUTPUT` PL/SQL package.

`CTX_OUTPUT` contains the following stored procedures:

| Name                | Description                                            |
|:--------------------|:-------------------------------------------------------|
| ADD_EVENT           | Adds an event to the index log.                        |
| ADD_TRACE           | Enables tracing.                                       |
| DISABLE_QUERY_STATS | Turns off the gathering of query stats for the index.  |
| ENABLE_QUERY_STATS  | Enables gathering of query stats for the index.        |
| END_LOG             | Halts logging of index and document services requests. |
| END_QUERY_LOG       | Stops logging queries into a logfile.                  |
| GET_TRACE_VALUE     | Returns the value of a trace.                          |
| LOG_TRACES          | Prints traces to logfile.                              |
| LOGFILENAME         | Returns the name of the current log file.              |
| REMOVE_EVENT        | Removes an event from the index log.                   |
| REMOVE_TRACE        | Disables tracing.                                      |
| RESET_TRACE         | Clears a trace.                                        |
| START_LOG           | Starts logging index and document service requests.    |
| START_QUERY_LOG     | Creates a log file of queries.                         |

**Note:**

The APIs in the `CTX_OUTPUT` package do not support identifiers that are prefixed with the schema or the owner name.

### 11.1 ADD_EVENT

Use this procedure to add an event to the index log for a more detailed log output or to enable error tracing for Oracle Text errors. Index logs are now appended to the database trace files.

#### Syntax

    CTX_OUTPUT.ADD_EVENT(event in NUMBER, errnum in NUMBER := null);

event
Specify the type of index event to log. You can add the following events:

- `CTX_OUTPUT.EVENT_INDEX_PRINT_ROWID`, which logs the rowid of each row as it is indexed. This is useful for debugging a failed index operation.

- `CTX_OUTPUT.EVENT_INDEX_PRINT_TOKEN`, which prints the each token as it is being indexed.

- `CTX_OUTPUT.EVENT_DRG_DUMP_ERRORSTACK`, which prints the stack trace for the specified DRG error in the log. An error will be raised if `errnum` is not specified.

**Note:**

`CTX_OUTPUT.EVENT_OPT_PRINT_TOKEN`, which prints each token as it is being optimized, and `CTX_OUTPUT.EVENT_INDEX_PRINT_TOKEN`, which prints each token as it is being indexed, are disabled when using PDB lockdown profile `CTX_PROTOCOLS`.

errnum
Specify the DRG error number for a `CTX_OUTPUT.EVENT_DRG_DUMP_ERRRORSTACK` event.

#### Example

    begin
    CTX_OUTPUT.ADD_EVENT(CTX_OUTPUT.EVENT_INDEX_PRINT_ROWID);
    end;

#### Related Topics

"REMOVE_EVENT"

### 11.2 ADD_TRACE

Use this procedure to enable a trace. If the trace has not been enabled, this call adds the trace to the list of active traces and resets its value to 0. If the trace has already been enabled, an error is raised.

#### Syntax

    CTX_OUTPUT.ADD_TRACE(trace_id BINARY_INTEGER);

trace_id
Specify the ID of the trace to enable. See Table 11-1 for possible trace values.

#### Notes

Table 11-1 shows the available traces:

Table 11-1 Available Traces

| Symbol                     | ID  | Metric                                                                                                |
|:---------------------------|:----|:------------------------------------------------------------------------------------------------------|
| `TRACE_IDX_USER_DATASTORE` | 1   | Time spent executing user datastore                                                                   |
| `TRACE_IDX_AUTO_FILTER`    | 2   | Time spent invoking the `AUTO_FILTER` filter. (Replaces the deprecated `TRACE_IDX_INSO_FILTER` trace) |
| `TRACE_QRY_XX_TIME`        | 3   | Time spent executing the `$X` cursor                                                                  |
| `TRACE_QRY_XF_TIME`        | 4   | Time spent fetching from `$X`                                                                         |
| `TRACE_QRY_X_ROWS`         | 5   | Total number of rows whose token metadata was fetched from `$X`                                       |
| `TRACE_QRY_IF_TIME`        | 6   | Time spent fetching the `LOB` locator from `$I`                                                       |
| `TRACE_QRY_IR_TIME`        | 7   | Time spent reading `$I` `LOB` information                                                             |
| `TRACE_QRY_I_ROWS`         | 8   | Number of rows whose `$I` `token_info` was actually read                                              |
| `TRACE_QRY_I_SIZE`         | 9   | Number of bytes read from `$I` `LOB`s                                                                 |
| `TRACE_QRY_R_TIME`         | 10  | Time spent fetching and reading` $R` information                                                      |
| `TRACE_QRY_CON_TIME`       | 11  | Time spent in `CONTAINS` processing (`drexrcontains/drexrstart/drexrfetch)`                           |
| `TRACE_QRY_S_TIME`         | 15  | Time spent fetching and reading `$S` information                                                      |
| `TRACE_QRY_O_TIME`         | 19  | Time spent reading `$O` information                                                                   |
| `TRACE_QRY_D_TIME`         | 23  | Time spent reading `$D` information                                                                   |
| `TRACE_QRY_SNIPPET_TIME`   | 25  | Time spent extracting a snippet from a document                                                       |
| `TRACE_HIL_DOCSERV_TIME`   | 26  | Time spent by document service procedures (snippet, highlight, and markup)                            |

Tracing is independent of logging. Logging does not have to be on to start tracing, and vice-versa.

Traces are associated with a session—they can measure operations that take place within a single session, and conversely, cannot make measurements across sessions.

During parallel sync or optimize, the trace profile will be copied to the worker sessions only if tracing is currently enabled. Each worker will accumulate its own traces and implicitly write all trace values to the worker logfile before termination.

#### Related Topics

REMOVE_TRACE

GET_TRACE_VALUE

LOG_TRACES

RESET_TRACE

[Oracle Text Application Developer's Guide](../ccapp/tuning-oracle-text.md)

### 11.3 DISABLE_QUERY_STATS

Disables gathering of query stats for the index.

#### Syntax

    ctx_output.disable_query_stats(
    index_name IN VARCHAR2
    );

index_name
The name of the index on which query stats collection is to be disabled.

#### Example

Turn off gathering of query stats for the index `myindex`.

    CTX_OUTPUT.DISABLE_QUERY_STATS(myindex);

#### Notes

Once the query stats is disabled for an index, gathering and storing query-related metadata is stopped for that index. All the entries corresponding to that index are cleared from the dictionary tables. An error is returned if you call this procedure on an index where query stats is not enabled.

#### Related Topics

CTX_OUTPUT."ENABLE_QUERY_STATS"

CTX_REPORT."[INDEX_STATS](CTX_REPORT-package.md)"

### 11.4 ENABLE_QUERY_STATS

Enables gathering of query stats for the index. To have query-related metadata stored for the index, use this procedure to enable collection of statistics on that index. You can only access the gathered metadata when `ctx_output.enable_query_stats` is turned on for the index.

**Note:**

Accessing the query stats metadata only works when `ctx_output.enable_query_stats` is turned on for the index. Please see CTX_REPORT."[INDEX_STATS](CTX_REPORT-package.md)" for the list of gathered query stats metadata.

#### Syntax

    ctx_output.enable_query_stats(
    index_name IN VARCHAR2
    );

index_name
The name of the index on which query stats collection is to be enabled.

#### Example

Turn on gathering of query stats for the index `myindex`.

    CTX_OUTPUT.ENABLE_QUERY_STATS(myindex);

#### Notes

The information that shows whether query stats is enabled on an index is available in the views: `CTX_INDEXES` and `CTX_USER_INDEXES` under the column `idx_query_stats_enabled`, which is in both of these views. If `query_stats` is enabled for an index, then the column displays YES; if not, then the column displays NO.

The data corresponding to the query statistics will be stored in persistent dictionary tables. Once `statistics` has been enabled for a particular index, query statistics will be collected for that index from all sessions.

If you call this procedure for an index where query stats is already enabled, then an error is thrown.

Statistics collection has a minimal effect on query performance.

#### Related Topics

CTX_OUTPUT."DISABLE_QUERY_STATS"

CTX_REPORT."[INDEX_STATS](CTX_REPORT-package.md)".

### 11.5 END_LOG

This procedure halts logging index and document service requests.

#### Syntax

    ctx_output.end_log;

#### Example

    begin
    CTX_OUTPUT.END_LOG;
    end;

### 11.6 END_QUERY_LOG

Use this procedure to stop logging queries into the database trace files.

#### Syntax

    ctx_output.end_query_log;

#### Example

    begin

    CTX_OUTPUT.START_QUERY_LOG('mylog1');
         < get queries >
    CTX_OUTPUT.END_QUERY_LOG;

    end;

### 11.7 GET_TRACE_VALUE

Use this procedure to programmatically retrieve the current value of a trace.

#### Syntax

    CTX_OUTPUT.GET_TRACE_VALUE(trace_id BINARY_INTEGER);

trace_id
Specify the trace ID whose value you want. See Table 11-1 for possible values.

#### Example

This sets the value of the variable value:

    value := ctx_output.get_trace_value(trace_id);

#### Notes

You can also retrieve trace values through SQL:

    select * from ctx_trace_values;

See "[CTX_TRACE_VALUES](oracle-text-views.md)" for the entries in the `CTX_TRACE_VALUES` view.

If the trace has not been enabled, an error is raised.

Traces are not reset to 0 by this call.

Traces are associated with a session—they can measure operations that take place within a single session, and conversely, cannot make measurements across sessions.

#### Related Topics

"REMOVE_TRACE"

"ADD_TRACE"

"LOG_TRACES"

"RESET_TRACE"

[Oracle Text Application Developer's Guide](../ccapp/tuning-oracle-text.md)

### 11.8 LOG_TRACES

Use this procedure to print all active traces to the RDBMS trace files.

#### Syntax

    CTX_OUTPUT.LOG_TRACES;

#### Notes

Traces are not reset to 0 by this call.

The traces now go to the database trace files.

#### Related Topics

"REMOVE_TRACE"

"GET_TRACE_VALUE"

"ADD_TRACE"

"RESET_TRACE"

[Oracle Text Application Developer's Guide](../ccapp/tuning-oracle-text.md)

### 11.9 LOGFILENAME

Returns the current session's trace file name. An error occurs if logging is not started.

#### Syntax

    CTX_OUTPUT.LOGFILENAME RETURN VARCHAR2;

#### Returns

Log file name

#### Example

    declare
       logname varchar2(100);
    begin
       logname := CTX_OUTPUT.LOGFILENAME;
       dbms_output.put_line('The current log file is: '||logname);
    end;

### 11.10 REMOVE_EVENT

Use this procedure to remove an event added through `ctx_output.add_event`.

#### Syntax

    CTX_OUTPUT.REMOVE_EVENT(event in NUMBER);

event
Specify the type of index event to remove from the log. You can remove the following events:

- `CTX_OUTPUT.EVENT_INDEX_PRINT_ROWID`, which logs the rowid of each row after it is indexed. This is useful for debugging a failed index operation.

- `CTX_OUTPUT.EVENT_OPT_PRINT_TOKEN`, which prints each token as it is being optimized.

- `CTX_OUTPUT.EVENT_INDEX_PRINT_TOKEN`, which prints the each token as it is being indexed.

#### Example

    begin

    CTX_OUTPUT.REMOVE_EVENT(CTX_OUTPUT.EVENT_INDEX_PRINT_ROWID);

    end;

#### Related Topics

"ADD_EVENT "

### 11.11 REMOVE_TRACE

Use this procedure to disable a trace.

#### Syntax

    CTX_OUTPUT.REMOVE_TRACE(trace_id BINARY_INTEGER);

trace_id
Specify the ID of the trace to disable. See Table 11-1 for possible values.

#### Notes

If the trace has not been enabled, an error is raised.

#### Related Topics

"GET_TRACE_VALUE"

"ADD_TRACE"

"LOG_TRACES"

"RESET_TRACE"

[Oracle Text Application Developer's Guide](../ccapp/tuning-oracle-text.md)

### 11.12 RESET_TRACE

Use this procedure to clear a trace (that is, reset it to 0).

#### Syntax

    CTX_OUTPUT.RESET_TRACE(trace_id BINARY_INTEGER);

trace_id
Specify the ID of the trace to reset. See Table 11-1 for possible values.

#### Notes

If the trace has not been enabled, an error is raised.

#### Related Topics

"REMOVE_TRACE"

"GET_TRACE_VALUE"

"ADD_TRACE"

"LOG_TRACES"

[Oracle Text Application Developer's Guide](../ccapp/tuning-oracle-text.md)

### 11.13 START_LOG

Begin logging index and document service requests. The index logs are written to the database trace files.

#### Syntax

    CTX_OUTPUT.START_LOG(logfile in varchar2, overwrite in default true);

logfile
Specify the name of the log file. Starting with Oracle Database 12c Release 2 (12.2), the logfile parameter is ignored. The logs are now appended to the database trace files. Use the dictionary views such as `V$DIAG_INFO` and `V$PROCESS` to find the path to your current session's trace file or to the trace file for each Oracle Database process.

The Automatic Diagnostic Repository Command Interpreter (ADRCI) utility can also be used to access the trace files.

overwrite
Specify whether you want to overwrite or append to the original query log file specified by logfile, if it already exists. Starting with Oracle Database 12c Release 2 (12.2), this parameter is ignored. By default, all logs are appended to the database trace file.

#### Examples

    begin
    CTX_OUTPUT.START_LOG('mylog1');
    end;

To view the indexing logs, search for `COMPONENT_NAME=’CONTEXT_INDEX’` in view `V$DIAG_TRACE_FILE_CONTENTS`:

    select PAYLOAD from V$DIAG_TRACE_FILE_CONTENTS where COMPONENT_NAME='CONTEXT_INDEX' and TRACE_FILENAME = trc_name;

To view the query logs, search for `COMPONENT_NAME=’CONTEXT_QUERY’` in view `V$DIAG_TRACE_FILE_CONTENTS`:

    select PAYLOAD from V$DIAG_TRACE_FILE_CONTENTS where COMPONENT_NAME='CONTEXT_QUERY' and TRACE_FILENAME = trc_name;

Parallel Query (PQ) workers have trace filenames of the type: `SID_``pxxx``_PID.trc`. To see the traces in the parallel workers:

    select TRACE_FILENAME, PAYLOAD from V$DIAG_TRACE_FILE_CONTENTS where COMPONENT_NAME='CONTEXT_INDEX' and TRACE_FILENAME LIKE '%p00%';

#### Notes

No logs are written if the PDB lockdown profile `CTX_LOGGING` is enabled.

Logging does not have to be `on` to start tracing, and vice-versa.

Logging is associated with a session-it can log operations that take place within a single session, and, conversely, cannot make measurements across sessions.

Filenames used in `CTX_OUTPUT.START_LOG` are restricted to the following characters: alphanumeric, minus, period, space, hash, underscore, single and double quotes. Any other character in the filename will raise an error.

### 11.14 START_QUERY_LOG

Begin logging query requests. Starting with Oracle Database 12c Release 2 (12.2), the query logs are written to the database trace files.

Use `CTX_OUTPUT.END_QUERY_LOG` to stop logging queries. Use `CTX_REPORT.QUERY_LOG_SUMMARY` to obtain reports on logged queries, such as which queries returned successfully the most times.

The query log includes the query string, the index name, and the timestamp of the query, as well as whether or not the query successfully returned a hit. A successful query for the phrase Blues Guitarists made at 6:46 (local time) on November 11th, 2003, would be entered into the query log in this form:

    <QuerySet><TimeStamp>18:46:51 02/04/03</TimeStamp><IndexName>
    IDX_SEARCH_TABLE</IndexName><Query>Blues
    Guitarists</Query><ReturnHit>Yes</ReturnHit></QuerySet>

#### Syntax

    CTX_OUTPUT.START_QUERY_LOG(logfile in varchar2, overwrite in default true);

logfile
Specify the name of the query log file. Starting with Oracle Database 12c Release 2 (12.2), the `logfile` parameter is ignored. The logs are appended to the database trace files instead. Use the dictionary views such as `V$DIAG_INFO` and `V$PROCESS` to find the path to your current session's trace file or to the trace file for each Oracle Database process.

The Automatic Diagnostic Repository Command Interpreter (ADRCI) utility can also be used to access the trace files.

overwrite
Specify whether you want to overwrite or append to the original query log file specified by `logfile`, if it already exists. Starting with Oracle Database 12c Release 2 (12.2), this parameter is ignored. By default, all logs are appended to the database trace file.

#### Example

    begin

    CTX_OUTPUT.START_QUERY_LOG('mylog1');
         < get queries >
    CTX_OUTPUT.END_QUERY_LOG;

    end;

#### Notes

No logs are written if the PDB lockdown profile `CTX_LOGGING` is enabled.

Filenames used in `CTX_OUTPUT.START_QUERY_LOG` are restricted to the following characters: alphanumeric, minus, period, space, hash, underscore, single and double quotes. Any other character in the filename will raise an error.

Logging is associated with a session-it can log operations that take place within a single session, and, conversely, cannot make measurements across sessions.
