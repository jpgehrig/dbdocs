Oracle lets you perform parallel queries with objects and objects synthesized in views, when you follow these rules:

- To make queries involving joins and sorts parallel (using the `ORDER` `BY`, `GROUP` `BY`, and `SET` operations), a `MAP` function is required. In the absence of a `MAP` function, the query automatically becomes serial.

- Parallel queries on nested tables are not supported. Even if there are parallel hints or parallel attributes for the table, the query is serial.

- Parallel Insert Direct Load (PIDL) and Parallel Create Table As Select (PCTAS) are supported on varray and ADT columns. The ADT columns must meet the following characteristics:

  - type is final

  - ADT attributes, at any level within the main type is final

  - lob/varray/xmltype attributes are stored as securefile

  - all other attributes are simple scalars

  Rest of the DML and DDL are always performed in serial.

- Parallel DML is not supported on views with `INSTEAD-OF` trigger. However, the individual statements within the trigger may be parallelized.
