## 5.140 DBA_JSON_COLUMNS

`DBA_JSON_COLUMNS` provides information on all JavaScript Object Notation (JSON) columns in the database. Its columns are the same as those in `ALL_JSON_COLUMNS`.

Each column that has an IS JSON check constraint in an AND condition appears in this view. This view enables a DBA to find all the JSON columns in the database

For example, if a check constraint combines the IS JSON condition with another condition using logical condition OR, then the column is not listed in this view. In this case, it is not certain that the data in the column is JSON data. For example, the following constraint does not ensure that the data in column jcol is JSON data:

    jcol is json OR length(jcol) < 1000

**See Also:**

- "[ALL_JSON_COLUMNS](ALL_JSON_COLUMNS.md)"

- [Oracle Database JSON Developer’s Guide](../adjsn/json-in-oracle-database.md) for more information about using JSON with Oracle Database
