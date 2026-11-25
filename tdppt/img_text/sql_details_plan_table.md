The Plan subpage is shown.

The page shows the following label-value pairs: Data Source is Cursor Cache, Capture Time is Dec 30, 2012 3:56:03 PM, Parsing Schema is HR, Optimizer Mode is ALL_ROWS.

In the View section, Table is selected. The table has the following columns: Operation, Object, Order, Rows, Bytes, Cost, CPU (%), Time, Query Block Name/Object Alias, Predicate, Filter, and Projection. The Operation column values are expandable or collapsible tree nodes. The values in the Object column are links. The table has six rows. The values in the rows are the following:

Row 1: (expanded node) SELECT STATEMENT, null, 7, null, null, 7, 100, null, null, null, null, null.

Row 2: (expanded node) HASH JOIN, null, 6, 3, 189, 7, 14, 0:0:1, SEL\$1, "E"."DEPARTMENT_ID"="D"."DEPAR...", null, (#keys=1) "E"."LAST_NAME"\[VARC...

Row 3: (expanded node) HASH JOIN, null, 4, 3, 141, 5, 20, 0:0:1, null, "E"."JOB_ID"="D"."JOB_ID", null, (#keys=1) "E"."LAST_NAME"\[VARC...

Row 4: (collapsed node) TABLE ACCESS BY INDEX ROWID, EMPLOYEES, 2, 3, 60, 2, 0, 0:0:1, SEL\$1/E@SEL\$1, null, null, "E"."LAST_NAME"\[VARCHAR2,25\],...

Row 5: TABLE ACCESS FULL, JOBS, 3, 19, 513, 2, 0, 0:0:1, SEL\$1/J@SEL\$1, null, null, "J"."JOB_ID"\[VARCHAR2,10\], "J"...

Row 5: TABLE ACCESS FULL, DEPARTMENTS, 5, 27, 2, 2, 0, 0:0:1, SEL\$1/D@SEL\$1, null, null, "D"."DEPARTMENT_ID"\[NUMBER,22\].

End of description.
