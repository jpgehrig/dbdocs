You can create a database table of JSON data from the content of a JSON dump file.

This topic shows how you can load a full table of JSON documents from the data in a JSON dump file, `$ORACLE_HOME``/demo/schema/order_entry/PurchaseOrders.dmp`. The format of this file is compatible with the export format produced by common NoSQL databases, including Oracle NoSQL Database. Each row of the file contains a single JSON document represented as a JSON object.

You can query such an external table directly or, for better performance if you have multiple queries that target different rows, you can load an ordinary database table from the data in the external table.

Example 13-1 creates a database directory that corresponds to file-system directory `$ORACLE_HOME``/demo/schema/order_entry`. Example 13-2 then uses this database directory to create and fill an external table, `json_dump_file_contents`, with the data from the dump file, `PurchaseOrders.dmp`. It bulk-fills the external table completely, copying all of the JSON documents to column `json_document`.

Example 13-4 then uses an `INSERT` as `SELECT` statement to copy the JSON documents from the external table to JSON column `po_document` of ordinary database table `j_purchaseorder`.

Because we chose `BLOB` storage for JSON column `json_document` of the external table, column `po_document` of the ordinary table must also be of type `BLOB`. Example 13-3 creates table `j_purchaseorder` with `BLOB` column `po_document`.

**Note:**

You need system privilege `CREATE ANY DIRECTORY` to create a database directory.

**See Also:**

- [Oracle Database Concepts](../cncpt/tables-and-table-clusters.md) for overview information about external tables

- [Oracle Database Utilities](../sutil/oracle-external-tables.md) and [Oracle Database Administrator’s Guide](../admin/managing-tables.md) for detailed information about external tables

- [Oracle Database Data Warehousing Guide](../dwhsg/loading-transformation-date-warehouses.md)

- [Oracle Database SQL Language Reference](../sqlrf/CREATE-TABLE.md) for information about `CREATE TABLE`

Example 13-1 Creating a Database Directory Object for Purchase Orders

You must replace `$ORACLE_HOME` here by its value.

    CREATE OR REPLACE DIRECTORY order_entry_dir
      AS '$ORACLE_HOME/demo/schema/order_entry';

Example 13-2 Creating an External Table and Filling It From a JSON Dump File

    CREATE TABLE json_dump_file_contents (json_document BLOB)
      ORGANIZATION EXTERNAL (TYPE ORACLE_LOADER DEFAULT DIRECTORY order_entry_dir
                             ACCESS PARAMETERS
                               (RECORDS DELIMITED BY 0x'0A'
                                DISABLE_DIRECTORY_LINK_CHECK
                                FIELDS (json_document CHAR(5000)))
                             LOCATION (order_entry_dir:'PurchaseOrders.dmp'))
      PARALLEL
      REJECT LIMIT UNLIMITED;

Example 13-3 Creating a Table With a BLOB JSON Column

Table` j_purchaseorder` has primary key `id` and JSON column `po_document`, which is stored using data type `BLOB`. The LOB cache option is turned on for that column.

    DROP TABLE j_purchaseorder;

    CREATE TABLE j_purchaseorder
      (id          VARCHAR2 (32) NOT NULL PRIMARY KEY,
       date_loaded TIMESTAMP (6) WITH TIME ZONE,
       po_document BLOB
       CONSTRAINT ensure_json CHECK (po_document IS JSON))
      LOB (po_document) STORE AS (CACHE);

Example 13-4 Copying JSON Data From an External Table To a Database Table

    INSERT INTO j_purchaseorder (id, date_loaded, po_document)
      SELECT SYS_GUID(), SYSTIMESTAMP, json_document FROM json_dump_file_contents
        WHERE json_document IS JSON;

**Parent topic:** [Insert, Update, and Load JSON Data](insert-load-and-update-json-data.md)
