# Description of the illustration lnoci021.eps

This illustration describes using `OCIBindByName()` to associate placeholders with program variables. It shows one SQL statement: `INSERT INTO emp VALUES (:empno, :ename, :job, :sal, :deptno)`. The call `OCIBindByName()` associates the placeholders in the SQL statement as follows:

For placeholder Address, :empno to &empno, :ename to ename, :job to job, :sal to &sal, and :deptno to &deptno. :empno is data type integer with length sizeof(empno), :ename is data type string with length strlen(ename)+, :job is data type string with length strlen(job)+1, :sal is data type integer with length sizeof(sal), and :depno is datatype integer with length sizeof(deptno).
