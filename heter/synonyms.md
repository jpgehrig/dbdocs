You can provide complete data location transparency and network transparency by using the synonym feature of the Oracle database server.

When a synonym is defined, you do not have to know the underlying table or network protocol. A synonym can be public, which means that all Oracle users can refer to the synonym. A synonym can also be defined as private, which means every Oracle user must have a synonym defined to access the non-Oracle table.

The following statement creates a system-wide synonym for the `emp` table in the schema of user `ORACLE` in the Sybase database:

    CREATE PUBLIC SYNONYM emp FOR "ORACLE"."EMP"@SYBS;

- Example: A Distributed Query
  An example showing a distributed query.

**See Also:**

[Oracle Database Administrator's Guide](../admin/managing-views-sequences-and-synonyms.md) for information about synonyms

**Parent topic:** [Using Heterogeneous Services Agents](using-heterogeneous-services-agents.md)

### Example: A Distributed Query

An example showing a distributed query.

**Note:**

Modify these examples for your environment. Do not try to execute them as they are written.

The following statement joins data between the Oracle database server, an IBM DB2 database, and a Sybase database:

    SELECT O.CUSTNAME, P.PROJNO, E.ENAME, SUM(E.RATE*P."HOURS")
           FROM ORDERS@DB2 O, EMP@ORACLE9 E, "PROJECTS"@SYBS P
           WHERE O.PROJNO = P."PROJNO"
              AND P."EMPNO" = E.EMPNO
           GROUP BY O.CUSTNAME, P."PROJNO", E.ENAME;

Through a combination of views and synonyms, using the following SQL statements, the process of distributed queries is transparent:

    CREATE SYNONYM ORDERS FOR ORDERS@DB2;
    CREATE SYNONYM PROJECTS FOR "PROJECTS"@SYBS;
    CREATE VIEW DETAILS (CUSTNAME,PROJNO,ENAME,SPEND)
          AS
          SELECT O.CUSTNAME, P."PROJNO", E.ENAME, SUM(E.RATE*P."HOURS")
          SPEND
          FROM ORDERS O, EMP E, PROJECTS P
          WHERE O.PROJNO = P."PROJNO"
          AND P."EMPNO" = E.EMPNO
          GROUP BY O.CUSTNAME, P."PROJNO", E.ENAME;

Use the following SQL statement to retrieve information from the data stores in one statement:

    SELECT * FROM DETAILS;

The statement retrieves the following table:

    CUSTNAME         PROJNO           ENAME          SPEND
    --------         ------           -----          -----
    ABC Co.             1             Jones            400
    ABC Co.             1             Smith            180
    XYZ Inc.            2             Jones            400
    XYZ Inc.            2             Smith            180

**Parent topic:** Using Synonyms to Provide Data Location and Network Transparency
