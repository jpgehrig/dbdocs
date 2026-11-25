The screenshot shows a portion of the SQL Statements subpage. There are two sections displayed: SQL Statements By Cost Improvement and Select SQL Statements to be Improved.

The SQL Statements By Cost Improvement section contains a bar chart. The vertical axis measures Cost Improvement with values from 0 to 12,000 incrementing by 2,000. The horizontal axis contains the Statement ID, with values, from left to right: 497, 1479, 803, and 637. According to the legend, blue bars indicate Cost Improvement. There are three blue bars in the graph:

- For statement ID 497, the cost improvement is 9,892.

- For statement ID 1479, the cost improvement is 9,964.

- For statement ID 803, the cost improvement is 6,144.

- For statement ID 637, the cost improvement is 0.

The Select SQL Statements to be Improved section contains a table. Just below the section heading is the Affected SQL Statements option, which is selected. Below this option are the Schedule Implementation and Show SQL buttons. Below the buttons and just above the table are the links Select All and Select None. The table has the following columns, from left to right: Select, Statement ID, Statement, Recommendation ID, Original Cost, New Cost, Cost Improvement, Cost Improvement (%), and Execution Count. The values of the Select column are check boxes. The values of the Statement ID column are links. The rows in the table have the following values:

- Row 1: (not selected), 497, SELECT \* FROM sales WHERE quantity_sold \< 5 UNION SELECT \* FROM sales WHERE quantity_sold \> 500, 1, 307676, 297784, 9892, 3.22, 4

- Row 2: (not selected), 1479, SELECT \* FROM sales WHERE amount_sold = 4, 2, 9964, 204, 9760, 97.95, 4

- Row 3: (selected), 803, SELECT SUM(quantity_sold) FROM sales s, products p WHERE s.prod_id = p.prod_id AND s.amount_sold \> 20000 AND p.prod_name = "Linen Big Shirt', 3, 6144, 12, 6132, 99.80, 4

- Row 4: (not selected), 637, SELECT COUNT(\*) FROM costs WHERE unit_cost \> 1200, 4, 4, 4, 0, 0.00, 4

End of description.
