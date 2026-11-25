## EXISTS Condition

An `EXISTS` condition tests for existence of rows in a subquery.

![Description of exists_condition.eps follows](img/exists_condition.gif)
[Description of the illustration exists_condition.eps](img_text/exists_condition.md)

Table 6-11 shows the `EXISTS` condition.

Table 6-11 EXISTS Condition

| Type of Condition | Operation                                      | Example                                                                                                                                                                                            |
|:------------------|:-----------------------------------------------|:---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `EXISTS `         | `TRUE` if a subquery returns at least one row. | `SELECT department_id`<br>`  FROM departments d`<br>`  WHERE EXISTS`<br>`  (SELECT * FROM employees e`<br>`    WHERE d.department_id `<br>`    = e.department_id)`<br>`   ORDER BY department_id;` |
