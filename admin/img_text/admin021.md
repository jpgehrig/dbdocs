# Description of the illustration admin021.eps

This is a text description of admin021.gif. This figure compares the structure of clustered tables to the structure of nonclustered tables.

One part of the illustration shows two tables as nonclustered tables. There are two distinct tables, EMP and DEPT. The EMP table contains (among other columns) the following columns: EMPNO, ENAME, DEPTNO. The DEPT table contains the following columns: DEPTNO, DNAME, LOC.

Another part of the illustration shows the EMP table and DEPT table created as clustered tables. The cluster key is DEPTNO. The information relating to DEPTNO is stored in the cluster. EMPNO, ENAME, and the other columns in the EMP table are all stored with the department data. Effectively, all data has been stored in the same table (cluster).

End of image description.
