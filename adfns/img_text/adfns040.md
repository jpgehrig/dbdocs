# Description of the illustration adfns040.eps

Referenced or parent table (DEPTNO is its primary key):

    Table DEPARTMENTS

    DEPTNO   DNAME       LOC
    ------   -----       --------
    20       RESEARCH    DALLAS
    30       SALES       NEW YORK
    40       MARKETING   BOSTON

Dependent or child table (DEPTNO is a foreign key; values in dependent table must match a value in unique key or primary key of referenced table):

    Table EMPLOYEES

    EMPNO  ENAME  JOB       MGR   HIREDATE   SAL       COMM    DEPTNO  COMMENT
    -----  -----  --------  ----  ---------  --------  ------  ------  -------
    7329   SMITH  CEO       N/A   17-DEC-85  9,000.00  N/A     20
    7499   ALLEN  VP-SALES  7329  20-FEB-90  7,500.00  100.00  30
    7521   WARD   MANAGER   7499  22-FEB-90  5,000.00  200.00  30
    7586   JONES  SALESMAN  7521  02-APR-90  2,975.00  400.00  20
    7571   FORD   MANAGER   7499  23-FEB-90  5,000.00  200.00  50      1
    7571   FORD   MANAGER   7499  23-FEB-90  5,000.00  200.00  N/A     2

1.  This row violates the referential constraint because "50" is not present in the referenced table's primary key; therefore, the row is now allowed in the table.

2.  This row is allowed in the table because a null value is entered in the DEPTNO column; however, if a not null constraint is also defined for this column, this row is not allowed.
