# Description of the illustration vldbg013.eps

This is partially described in the accompanying text. In addition:

- It shows a typical breaking of the data into A-G, H-M, N-S, and T-Z

- It adds the concept of the data flowing gradually from the employees table to the user process

- It shows intra-operation parallelism for the full table scan and the ORDER BY operation

- It shows the inter-operation parallelism for going between those two inter-operation parallelisms

- The SQL statement is SELECT \* FROM employees ORDER BY last_name;
