When preparing SQL\*Loader control files (`.ctl`), you must follow certain syntax and notational conventions.

In the full path descriptions, backslashes do not require escape characters or other special treatment. When embedding a single or a double quotation mark inside a string delimited by double quotation marks, place a backslash escape character before the embedded quotation mark.

When specifying data types in the SQL\*Loader control file, note that the default sizes of native data types shown in Default Sizes of Native Data types are specific to Windows. These data types can be loaded with correct results only between systems where they have the same length in bytes. You cannot override these defaults in the control file. If the byte order is different between the systems, you can indicate the byte order of the data with the `BYTEORDER` parameter, or you can place a byte-order mark (BOM) in the file.

Table 2-5 Default Sizes of Native Data types

| Native Data Types | Default Field Length |
|:------------------|:---------------------|
| DOUBLE            | 8                    |
| FLOAT             | 4                    |
| INTEGER           | 4                    |
| SMALLINT          | 2                    |

**Note:**

The default listed is correct if `INTEGER` is specified without a size. But `INTEGER(n)` is also allowed. In that case, `n` specifies the size of the `INTEGER` field in bytes.

**See Also:**

[Oracle Database Utilities ](../sutil/oracle-sql-loader-concepts.md)for a complete list of options and instructions on using SQL\*Loader

**Parent topic:** [Using SQL\*Loader](using-sql-loader.md)
