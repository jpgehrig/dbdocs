# Description of the illustration tgsql_vm_045.eps

The top of this diagram is a box with the following query:

SELECT e.last_name, d.department_name

FROM hr.employees e, hr.departments d

WHERE e.department_id = d.department_id;

This box points down to a box labeled "Optimizer." Inside this box is a box labeled "Transformer." This box contains three boxes: Join Method, Join Order, Access Path.The Join Method box contains "Hash, Nested Loop, Sort Merge." The Join Order box contains "departments 0 employees 1" and "employees 0 departments 1." The Access Path box contains "Index" and "Full Table Scan." The Optimizer box points down to a box that contains "Hash Join" and "departments 0 employees 1." The arrow is labeled "Lowest Cost Plan."
