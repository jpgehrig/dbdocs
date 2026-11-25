This figure illustrates the steps in a pipelined data transformation:

- Load external table with flat files

- Validate customer keys (lookup in customer dimension table)

- Convert source product keys to warehouse product keys

- Insert source product keys to warehouse product keys

Before loading, you start with flat files. After loading, the data is in the table. The difference between pipelined data transformation and multistage data transformation is that pipelined transformation occurs in database tables.
