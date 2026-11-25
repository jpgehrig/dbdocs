This overview describes: (1) data types for JSON columns, (2) LOB storage considerations for JSON data, and (3) ensuring that JSON columns contain well-formed JSON data.

### Data Types for JSON Columns

You can store JSON data in Oracle Database using columns whose data types are `VARCHAR2`, `CLOB`, or `BLOB`. Whichever type you use, you can manipulate JSON data as you would manipulate any other data of those types. Storing JSON data using standard data types allows all features of Oracle Database, such as advanced replication, to work with tables containing JSON documents. The choice of which to use is typically motivated by the size of the JSON documents you need to manage:

- Use `VARCHAR2(4000)` if you are sure that your largest JSON documents do not exceed 4000 bytes (or characters)<sup>Foot 1Foot 1</sup>.

  If you use Oracle Exadata then choosing `VARCHAR2(4000)` can improve performance by allowing the execution of some JSON operations to be pushed down to Exadata storage cells, for improved performance.

- Use `VARCHAR2(32767)` if you know that some of your JSON documents are larger than 4000 bytes (or characters) and you are sure than none of the documents exceeds 32767 bytes (or characters)<sup>Foot 1</sup>.

  With `VARCHAR2(32767)`, the first roughly 3.5K bytes (or characters) of a document is stored in line, as part of the table row. This means that the added cost of using `VARCHAR2(32767)` instead of `VARCHAR2(4000)` applies only to those documents that are larger than about 3.5K. If most of your documents are smaller than this then you will likely notice little performance difference from using `VARCHAR2(4000)`.

  If you use Oracle Exadata then push-down is enabled for any documents that are stored in line.

- Use `BLOB` (binary large object) or `CLOB` (character large object) textual JSON storage if you know that you have some JSON documents that are larger than 32767 bytes (or characters)<sup>Foot 1</sup>.

- Use `BLOB` storage with optimized binary format OSON if you want the fastest query and update performance. To do this, use a check constraint with condition `is json FORMAT OSON`.

  For Release 19c, `BLOB` with format OSON is supported only for Oracle Autonomous Databases.

### Ensure That JSON Columns Contain Well-Formed JSON Data

You can use SQL/JSON condition `is json` to check whether or not some JSON data is well formed. Oracle strongly recommends that you apply an `is json` check constraint to any JSON column, unless you expect some rows to contain something other than well-formed JSON data.

The overhead of parsing JSON is such that evaluating the condition should not have a significant impact on insert and update performance, and omitting the constraint means you cannot use the simple dot-notation syntax to query the JSON data.

What constitutes well-formed JSON data is a gray area. In practice, it is common for JSON data to have some characteristics that do not strictly follow the standard definition. You can control which syntax you require a given column of JSON data to conform to: the standard definition (strict syntax) or a JavaScript-like syntax found in common practice (lax syntax). The default SQL/JSON syntax for Oracle Database is lax. Which kind of syntax is used is controlled by condition `is json`. Applying an `is json` check constraint to a JSON column thus enables the use of lax JSON syntax, by default.

**Related Topics**

- [Character Sets and Character Encoding for JSON Data](json-character-sets-and-encoding.md)
- [Overview of Inserting, Updating, and Loading JSON Data](overview-of-inserting-updating-loading-JSON-data.md)
- [Simple Dot-Notation Access to JSON Data](simple-dot-notation-access-to-json-data.md)

**Parent topic:** [Store and Manage JSON Data](store-and-manage-json-data.md)

------------------------------------------------------------------------



Footnote Legend

Footnote 1: Whether the limit is expressed in bytes or characters is determined by session parameter `NLS_LENGTH_SEMANTICS`.
