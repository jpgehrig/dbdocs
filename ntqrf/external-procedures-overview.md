External procedures are functions written in a third-generation language (C, for example) and callable from within PL/SQL or SQL as if they were a PL/SQL routine or function.

External procedures let you take advantage of strengths and capabilities of a third-generation programming language in a PL/SQL environment.

**Note:**

Oracle Database also provides a special purpose interface, the call specification, that lets you call external procedures from other languages, as long as they are callable by C.

The main advantages of external procedures are:

- Performance, because some tasks are performed more efficiently in a third-generation language than in PL/SQL, which is better suited for SQL transaction processing

- Code re-usability, because dynamic link libraries (DLLs) can be called directly from PL/SQL programs on the server or in client tools

You can use external procedures to perform specific processes:

- Solving scientific and engineering problems

- Analyzing data

- Controlling real-time devices and processes

**Note:**

Special security precautions are warranted when configuring a listener to handle external procedures.

To create and use an external procedure, perform the following steps:

1.  [Installing and Configuring Oracle Database and Oracle Net Services](installing-and-configuring-oracle-database-and-oracle-net-services.md)

2.  [Writing an External Procedure](writing-an-external-procedure.md)

3.  [Building a DLL](building-a-dll.md)

4.  [Registering an External Procedure](registering-an-external-procedure.md)

5.  [Restricting Library-Related Privileges to Trusted Users Only](restricting-library-related-privileges-to-trusted-users-only.md)

6.  [Executing an External Procedure](executing-an-external-procedure.md)

**Note:**

- You must have a C compiler and linker installed on your system to build DLLs.

- You can combine the instructions described in the fourth and fifth tasks into one SQL script that automates the task of registering and executing your external procedure. See `ORACLE_HOME``\rdbms\extproc\extern.sql` for an example of a SQL script that combines these steps.

**See Also:**

"[Modifying Configuration of External Procedures for Higher Security](making-component-based-backups-of-a-noarchivelog.md)" and [Oracle Database Net Services Administrator's Guide](../netag/enabling-advanced-features.md)

**Parent topic:** [About Building External Procedures](about-building-external-procedures.md)
