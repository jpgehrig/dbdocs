This part covers creating JSON columns in a database table, partitioning such tables, replicating them using Oracle GoldenGate, and character-set encoding of JSON data. It covers the use of SQL/JSON condition `is json` as a check constraint to ensure that the data in a column is well-formed JSON data.

- [Overview of Storing and Managing JSON Data](overview-of-storage-and-management-of-JSON-data.md)
  This overview describes: (1) data types for JSON columns, (2) LOB storage considerations for JSON data, and (3) ensuring that JSON columns contain well-formed JSON data.
- [Creating a Table With a JSON Column](creating-a-table-with-a-json-column.md)
  You can create a table that has JSON columns. You use SQL condition `is json` as a check constraint to ensure that data inserted into a column is (well-formed) JSON data. Oracle recommends that you always use an `is_json` check constraint when you create a column intended for JSON data.
- [SQL/JSON Conditions IS JSON and IS NOT JSON](conditions-is-json-and-is-not-json.md)
  SQL/JSON conditions `is json` and `is not json` are complementary. They test whether their argument is syntactically correct, that is, well-formed, JSON data. You can use them in a `CASE` expression or the `WHERE` clause of a `SELECT` statement. You can use `is json` in a check constraint.
- [Character Sets and Character Encoding for JSON Data](json-character-sets-and-encoding.md)
  JSON data always uses the Unicode character set. In this respect, JSON data is simpler to use than XML data. This is an important part of the JSON Data Interchange Format (RFC 4627). For JSON data processed by Oracle Database, any needed character-set conversions are performed automatically.
- [Considerations When Using LOB Storage for JSON Data](considerations-when-using-lob-storage-json-data.md)
  LOB storage considerations for JSON data are described, including considerations when you use a client to retrieve JSON data as a LOB instance.
- [Partitioning JSON Data](partitioning-json-data.md)
  You can partition a table using a JSON virtual column as the partitioning key. The virtual column is extracted from a JSON column using SQL/JSON function `json_value`.
- [Replication of JSON Data](replication-of-json-data.md)
  You can use Oracle GoldenGate to replicate tables that have columns containing JSON data.
