# Description of the illustration

This image illustrates a table (EMP) that is range partitioned on EMPNO. A global prefixed partitioned index is on EMPNO. In this case:

- EMPNO is broken into EMPNO 0-39, EMPNO 40-69, ... EMPNO 70 -the max value

- EMPNO 15 and EMPNO 31 are based on DEPTNO 0-9 and DEPTNO 10-19

- EMPNO 54 is based on DEPTNO 0-9

- EMPNO 73, EMPNO 82, and EMPNO 96 are based on DEPTNO 10-19 and DEPTNO 90-99
