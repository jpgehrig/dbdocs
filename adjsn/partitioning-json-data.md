You can partition a table using a JSON virtual column as the partitioning key. The virtual column is extracted from a JSON column using SQL/JSON function `json_value`.

### Partition on a Non-JSON Column When Possible

You can partition a table using a JSON virtual column, but it is generally preferable to use a non-JSON column. A partitioning key specifies which partition a new row is inserted into. A partitioning key defined as a JSON virtual column uses SQL/JSON function `json_value`, and the partition-defining `json_value` expression is executed each time a row is inserted. This can be costly, especially for insertion of large JSON documents.

### Rules for Partitioning a Table Using a JSON Virtual Column

- The virtual column that serves as the partitioning key must be defined using SQL/JSON function `json_value`.

- The data type of the virtual column is defined by the `RETURNING` clause used for the `json_value` expression.

- The `json_value` path used to extract the data for the virtual column must not contain any predicates. (The path must be streamable.)

- The JSON column referenced by the expression that defines the virtual column can have an `is json` check constraint, but it need not have such a constraint.

**See Also:**

[Oracle Database SQL Language Reference](../sqlrf/CREATE-TABLE.md) for information about` CREATE TABLE`

Example 8-1 Creating a Partitioned Table Using a JSON Virtual Column

This example creates table `j_purchaseorder_partitioned`, which is partitioned using virtual column `po_num_vc`. That virtual column references JSON column `po_document` (which uses `CLOB` storage). The `json_value` expression that defines the virtual column extracts JSON field `PONumber` from `po_document` as a number. Column `po_document` does not have an `is json` check constraint.

    CREATE TABLE j_purchaseorder_partitioned
      (id VARCHAR2 (32) NOT NULL PRIMARY KEY,
       date_loaded TIMESTAMP (6) WITH TIME ZONE,
       po_document CLOB,
       po_num_vc NUMBER GENERATED ALWAYS AS
         (json_value (po_document, '$.PONumber' RETURNING NUMBER)))
      LOB (po_document) STORE AS (CACHE)
      PARTITION BY RANGE (po_num_vc)
       (PARTITION p1 VALUES LESS THAN (1000),
        PARTITION p2 VALUES LESS THAN (2000));

**Parent topic:** [Store and Manage JSON Data](store-and-manage-json-data.md)
