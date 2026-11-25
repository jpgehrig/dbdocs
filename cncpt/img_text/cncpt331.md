# Description of the illustration cncpt331.eps

At the top left of the figure is the following statement: SELECT \* FROM employees WHERE department_id = 20. The 20 points down to Hash(20), which in turn points to Hash Value 77, which in turn points to a Data Block labeled 100. This block exists in row of boxes labeled "Data Blocks in Cluster Segment." At the top right is the following statement: SELECT \* FROM employees WHERE department_id = 43. The 43 points to Hash(43). The Hash (43) points to Hash Value 77. The 77 points down to Block 100. Block 100 points to Block 200.
