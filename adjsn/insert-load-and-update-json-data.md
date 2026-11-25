The usual ways to insert, update, and load data in Oracle Database work with JSON data. You can also create an external table from the content of a JSON dump file.

- [Overview of Inserting, Updating, and Loading JSON Data](overview-of-inserting-updating-loading-JSON-data.md)
  You can use database APIs to insert or modify JSON data in Oracle Database. You can use Oracle SQL function `json_transform` or `json_mergepatch` to update a JSON document. You can work directly with JSON data contained in file-system files by creating an external table that exposes it to the database.
- [Oracle SQL Function JSON_TRANSFORM](oracle-sql-function-json_transform.md)
  Oracle SQL function `json_transform` modifies JSON documents. You specify modification operations to perform and SQL/JSON path expressions that target the places to modify. The operations are applied to the input data in the order specified: each operation acts on the result of applying all of the preceding operations.
- [Updating a JSON Document with JSON Merge Patch](updating-json-document-json-merge-patch.md)
  You can use Oracle SQL function `json_mergepatch` to update specific portions of a JSON document. You pass it a JSON Merge Patch document, which specifies the changes to make to a specified JSON document. JSON Merge Patch is an IETF standard.
- [Loading External JSON Data](loading-external-json-data.md)
  You can create a database table of JSON data from the content of a JSON dump file.
