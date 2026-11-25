## 5.267 DBA_RECOVERABLE_SCRIPT_PARAMS

`DBA_RECOVERABLE_SCRIPT_PARAMS` provides details about recoverable operation parameters.

| Column        | Datatype         | NULL | Description                      |
|:--------------|:-----------------|:-----|:---------------------------------|
| `SCRIPT_ID`   | `RAW(16)`        |      | Unique ID of the operation       |
| `PARAMETER`   | `VARCHAR2(128)`  |      | Name of the parameter            |
| `PARAM_INDEX` | `NUMBER`         |      | Index for multi-valued parameter |
| `VALUE`       | `VARCHAR2(4000)` |      | Value of the parameter           |
