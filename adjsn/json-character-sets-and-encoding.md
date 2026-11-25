JSON data always uses the Unicode character set. In this respect, JSON data is simpler to use than XML data. This is an important part of the JSON Data Interchange Format (RFC 4627). For JSON data processed by Oracle Database, any needed character-set conversions are performed automatically.

Oracle Database uses UTF-8 internally when it processes JSON data (parsing, querying). If the data that is input to such processing, or the data that is output from it, must be in a different character set from UTF-8, then character-set conversion is carried out accordingly.

Character-set conversion can affect performance. And in some cases it can be lossy. Conversion of input data to UTF-8 is a lossless operation, but conversion to output can result in information loss in the case of characters that cannot be represented in the output character set.

If your JSON data is stored in the database as Unicode then no character-set conversion is needed for storage or retrieval. This is the case if the database character set is AL32UTF8 (Unicode UTF-8) or if your JSON data is stored in CLOB instances that have character set AL16UTF16. Oracle recommends that you use AL32UTF8 as the database character set if at all possible.

Regardless of the database character set, JSON data that is stored using data type `BLOB` never undergoes character-set conversion for storage or retrieval. JSON data can be stored using data type `BLOB` as AL32UTF8, AL16UTF16, or AL16UTF16LE.

If you transform JSON data using SQL/JSON functions or PL/SQL methods and you return the result of the transformation using data type `BLOB` then the result is encoded as AL32UTF8. This is true even if the input `BLOB` data uses another Unicode encoding.

For example, if you use function `json_query` to extract some JSON data from `BLOB` input and return the result as `BLOB`, it is returned using AL32UTF8.

Lossy character-set conversion can occur if application of a SQL/JSON function or a PL/SQL method specifies a return data type of `VARCHAR2` or `CLOB` and the database character set is not Unicode. If input JSON data was stored in a `BLOB` instance then even if it is ultimately written again as `BLOB`, if some of it was temporarily changed to `VARCHAR2` or `CLOB` then the resulting `BLOB` data can suffer from lossy conversion.

**Related Topics**

- [Overview of Storing and Managing JSON Data](overview-of-storage-and-management-of-JSON-data.md)

**See Also:**

- [Unicode.org](https://docs.oracle.com/pls/topic/lookup?ctx=en/database/oracle/oracle-database/19/adjsn&id=unicode_org) for information about Unicode

- [IETF RFC4627](https://docs.oracle.com/pls/topic/lookup?ctx=en/database/oracle/oracle-database/19/adjsn&id=tools_ietf_rfc4627) and [ECMA 404](https://ecma-international.org/publications-and-standards/standards/ecma-404/) for the JSON Data Interchange Format

- [Oracle Database Migration Assistant for Unicode Guide](https://docs.oracle.com/pls/topic/lookup?ctx=en/database/oracle/oracle-database/19/adjsn&id=DUMAG101) for information about using different character sets with the database

- [Oracle Database Globalization Support Guide](../nlspg/character-set-migration.md) for information about character-set conversion in the database

**Parent topic:** [Store and Manage JSON Data](store-and-manage-json-data.md)
