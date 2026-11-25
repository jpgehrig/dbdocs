When a SQL statement accesses data from non-Oracle systems, it is said to be a heterogeneous distributed SQL statement.

To optimize heterogeneous distributed SQL statements, follow the same guidelines as for optimizing distributed SQL statements that access Oracle databases only. However, you must consider that the non-Oracle system usually does not support all the functions and operators that Oracle supports.

The Oracle Database gateways tell Oracle (at connect time) which functions and operators they support. If the non-Oracle data source does not support a function or operator, then Oracle performs that function or operator. In this case, Oracle obtains the data from the other data source and applies the function or operator locally. This affects the way in which the SQL statements are decomposed and can affect performance, especially if Oracle is not on the same computer as the other data source. However, performance can be improved if you use the bulk fetch and bulk load features.

**Parent topic:** [Performance Recommendations](performance-recommendations.md)
