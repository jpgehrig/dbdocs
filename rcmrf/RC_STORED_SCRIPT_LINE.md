## 5.58 RC_STORED_SCRIPT_LINE

This view lists information about individual lines of stored scripts in the recovery catalog.

The view contains one row for each line of each stored script.

| Column        | Data Type        | Description                                                                                                                   |
|:--------------|:-----------------|:------------------------------------------------------------------------------------------------------------------------------|
| `DB_KEY`      | `NUMBER`         | The primary key for the database that owns this stored script. Use this column to join with almost any other catalog view.    |
| `SCRIPT_NAME` | `VARCHAR2(100)`  | The name of the stored script.                                                                                                |
| `LINE`        | `NUMBER`         | The number of the line in the stored script. Each line of a stored script is uniquely identified by `SCRIPT_NAME` and `LINE`. |
| `TEXT`        | `VARCHAR2(1024)` | The text of the line of the stored script.                                                                                    |
