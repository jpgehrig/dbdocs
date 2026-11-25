## 5.265 DBA_RECOVERABLE_SCRIPT_ERRORS

`DBA_RECOVERABLE_SCRIPT_ERRORS` provides details about errors that occurred during script execution.

| Column                | Datatype         | NULL | Description                                               |
|:----------------------|:-----------------|:-----|:----------------------------------------------------------|
| `SCRIPT_ID`           | `RAW(16)`        |      | Global unique ID of the recoverable script                |
| `BLOCK_NUM`           | `NUMBER`         |      | The `n`th block that failed                               |
| `ERROR_NUMBER`        | `NUMBER`         |      | Number of the error encountered while executing the block |
| `ERROR_MESSAGE`       | `VARCHAR2(4000)` |      | Error message encountered while executing the block       |
| `ERROR_CREATION_TIME` | `DATE`           |      | Time that the error was created                           |
