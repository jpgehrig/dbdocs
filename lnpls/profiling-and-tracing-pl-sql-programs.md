## 12.9 Profiling and Tracing PL/SQL Programs

To help you isolate performance problems in large PL/SQL programs, PL/SQL provides these tools, implemented as PL/SQL packages.

Table 12-1 Profiling and Tracing Tools Summary

| Tool                         | Package                    | Description                                                                                                                                                                                                                                                                                                                                                                                                                  |
|:-----------------------------|:---------------------------|:-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Profiler interface           | `DBMS_PROFILER`            | Computes the time that your PL/SQL program spends at each line and in each subprogram.<br>You must have `CREATE` privileges on the units to be profiled.<br>Saves runtime statistics in database tables, which you can query.                                                                                                                                                                                                |
| Trace interface              | `DBMS_TRACE`               | Traces the order in which subprograms run.<br>You can specify the subprograms to trace and the tracing level.<br>Saves runtime statistics in database tables, which you can query.                                                                                                                                                                                                                                           |
| PL/SQL hierarchical profiler | `DBMS_HPROF`               | Reports the dynamic execution program profile of your PL/SQL program, organized by subprogram invocations. Accounts for SQL and PL/SQL execution times separately.<br>Requires no special source or compile-time preparation.<br>Generates reports in HTML. Provides the option of storing profiler data and results in relational format in database tables for custom report generation (such as third-party tools offer). |
| SQL trace                    | `DBMS_APPLICATION_INFO`    | Uses the `DBMS_APPLICATION_INFO` package with Oracle Trace and the SQL trace facility to record names of executing modules or transactions in the database for later use when tracking the performance of various modules and debugging.                                                                                                                                                                                     |
| PL/SQL Basic Block Coverage  | `DBMS_PLSQL_CODE_COVERAGE` | Collects and analyzes basic block coverage data.                                                                                                                                                                                                                                                                                                                                                                             |
| Call Stack Utilities         | `UTL_CALL_STACK`           | Provides information about currently executing subprograms (such as subprogram names, unit names, owner names, edition names, and error stack information) that you can use to create more revealing error logs and application execution traces.                                                                                                                                                                            |

### Related Topics

- [Oracle Database PL/SQL Packages and Types Reference](../arpls/DBMS_APPLICATION_INFO.md) for more information about the `DBMS_APPLICATION_INFO` package

- [Oracle Database PL/SQL Packages and Types Reference](../arpls/DBMS_HPROF.md) for more information about the `DBMS_HPROF` package

- [Oracle Database PL/SQL Packages and Types Reference](../arpls/DBMS_PLSQL_CODE_COVERAGE.md) for more information about the `DBMS_PLSQL_CODE_COVERAGE` package

- [Oracle Database PL/SQL Packages and Types Reference](../arpls/DBMS_PROFILER.md) for more information about the `DBMS_PROFILER` package

- [Oracle Database PL/SQL Packages and Types Reference](../arpls/DBMS_TRACE.md) for more information about the `DBMS_TRACE` package

  [Oracle Database PL/SQL Packages and Types Reference](../arpls/UTL_CALL_STACK.md) for more information about the `UTL_CALL_STACK` package

- [COVERAGE Pragma](COVERAGE-pragma.md) for the syntax and semantics of `COVERAGE PRAGMA`

- [Oracle Database Development Guide](../adfns/basic-block-coverage.md) for more information about using PL/SQL basic block coverage

- [Oracle Database Development Guide](../adfns/hierarchical-profiler.md) for a detailed description of PL/SQL hierarchical profiler

- [Oracle Database Development Guide](../adfns/coding-subprograms-and-packages.md) for more information about analyzing and debugging stored subprograms
