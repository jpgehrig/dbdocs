# Description of the illustration schema_plan.gif

The figure illustrates the schema plan for the purchase order application. The StockNo column of the LineItems table is a foreign key and references the primary key column, StockNo, of the StockItems table. Similarly, Orders.CustNo is a foreign key and references the primary key Customers.CustNo. Also, LineItems.PONo is a foreign key and references the primary key Orders.PONo.
