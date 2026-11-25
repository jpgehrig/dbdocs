The screenshot shows the Actions and SQL Affected by Recommendations sections of the Recommendation Details page. At the top of the Actions section is the Set Schema for All Actions field, which is blank. Next to the field is a search icon and to the left of that is a Go button. Below that field is the Set Tablespace for All Actions field, which is blank. Next to the field is a search icon and to the left of that is another Go button.

Below those fields is a table. The column headings are, from left to right: Implementation Status, Recommendation IDs, Action, Object Name, Object Attributes, Indexed Columns, Base Table, and Schema. The values in the Implementation Status column are icons indicating the status. The values in the Action column are links. Some values in the Object Name, Schema, and Tablespace (not shown) columns appear as fields in which you can modify the value. The rows in the table have the following values:

- Row 1: pending, 3, ALTER_MATERIALIZED_VIEW_LOG, null, null, SH.SALES, SH

- Row 2: pending, 3, ALTER_MATERIALIZED_VIEW_LOG, null, null, SH.PRODUCTS, SH

- Row 3: pending, 1, CREATE_INDEX, SALES_IDX\$\$\_01680000 (field), BITMAP LOCAL, QUANTITY_SOLD, SH_SALES, SH (field with an associated search icon)

- Row 4: pending, 2, CREATE_INDEX, SALES_IDX\$\$\_01680001 (field), BITMAP LOCAL, AMOUNT_SOLD, SH_SALES, SH (field with an associated search icon)

- Row 5: pending, 3, CREATE_MATERIALIZED \_VIEW, MV\$\$\_01680000, General Match, null, null, DBA1 (field with an associated search icon)

- Row 6: pending, 3, GATHER_TABLE_STATISTICS, MV\$\$\_01680000, null, null, null, DBA1

The SQL Affected by Recommendations section contains a table. The column headings are, from left to right: Statement ID, Statement, Recommendation ID, Original Cost, New Cost, Cost Improvement, Cost Improvement (%), Execution Count. The values in the Statement ID column are links. The rows in the table have the following values:

- Row 1: 497, SELECT \* FROM sales WHERE quantity_sold \< 5 UNION SELECT \* FROM sales WHERE quantity_sold \> 500, 1, 307676, 297784, 9892, 3.22, 4

- Row 2: 1479, SELECT \* FROM sales WHERE amount_sold = 4, 2, 9964, 204, 9760, 97.95, 4

- Row 3: SELECT SUM(quantity_sold) FROM sales s, products p WHERE s.prod_id = p.prod_id AND s.amount_sold \> 20000 AND p.prod_name = "Linen Big Shirt', 3, 6144, 12, 6132, 99.80, 4

End of description.
