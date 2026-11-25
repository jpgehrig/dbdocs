## 5.57 RC_STORED_SCRIPT

This view lists information about scripts stored in the recovery catalog.

The view contains one row for each stored script. RMAN commands for script management such as `LIST SCRIPT NAMES` and `LIST SCRIPT` provide more convenient ways of viewing this information.

| Column           | Data Type       | Description                                                                                                                |
|:-----------------|:----------------|:---------------------------------------------------------------------------------------------------------------------------|
| `DB_KEY`         | `NUMBER`        | The primary key for the database that owns this stored script. Use this column to join with almost any other catalog view. |
| `DB_NAME`        | `VARCHAR2(8)`   | The `DB_NAME` of the database incarnation to which this record belongs.                                                    |
| `SCRIPT_NAME`    | `VARCHAR2(100)` | The name of the stored script.                                                                                             |
| `SCRIPT_COMMENT` | `VARCHAR2(255)` | The comment that the user entered while creating this script. `NULL` if no comment was entered.                            |
