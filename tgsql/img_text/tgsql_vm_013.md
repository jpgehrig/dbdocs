# Description of the illustration tgsql_vm_013.eps

This graphic depicts part of a SQL statement: SELECT /\*+ INDEX (employees emp_dep_ix)\*? .... This statement points down to the Optimizer. The Optimizer points down to a fragment of an explain plan. The arrow is labeled "Generate Plan." The plan has columns ID, Operation, and Name. The rows are: 0, SELECT STATEMENT, null; 1, TABLE ACCESS BY INDEX ROWID, EMPLOYEES; 2, INDEX UNIQUE SCAN, TABLE ACCESS BY INDEX ROWID.
