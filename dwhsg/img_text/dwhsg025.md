This figure illustrates four steps in a multistage data transformation:

- Load into staging table

- Validate customer keys (in this case, by using the customer dimension table)

- Convert source product keys to warehouse keys

- Insert into the warehouse table

Before loading, you start with flat files. After loading, the data is in the table.
