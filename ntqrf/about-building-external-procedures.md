Describes how to create and use external procedures on Windows.

The following files are located in `ORACLE_HOME``\rdbms\extproc`:

- `extern.c`` `is the code example shown in "Writing an External Procedure"

  `make.bat` is the batch file that builds the dynamic link library

- `extern.sql` automates the instructions described in "Registering an External Procedure" and "Executing an External Procedure"

<!-- -->

- [External Procedures Overview](external-procedures-overview.md)
  External procedures are functions written in a third-generation language (C, for example) and callable from within PL/SQL or SQL as if they were a PL/SQL routine or function.
- [Installing and Configuring Oracle Database and Oracle Net Services](installing-and-configuring-oracle-database-and-oracle-net-services.md)
  Describes about the installation and configuration of Oracle Database and Oracle Net.
- [Writing an External Procedure](writing-an-external-procedure.md)
  Using a third-generation programming language, you can write functions to be built into DLLs and started by `EXTPROC`.
- [Building a DLL](building-a-dll.md)
  After writing your external procedures in a third-generation programming language, use the appropriate compiler and linker to build a DLL, making sure to export the external procedures as noted previously.
- [Registering an External Procedure](registering-an-external-procedure.md)
  Once you have built a DLL containing your external procedures, you must register your external procedures with Oracle Database.
- [Restricting Library-Related Privileges to Trusted Users Only](restricting-library-related-privileges-to-trusted-users-only.md)
  The `CREATE LIBRARY`, `CREATE ANY LIBRARY`, `ALTER ANY LIBRARY`, and `EXECUTE ANY LIBRARY` privileges, and grants of `EXECUTE ON` `library_name` convey a great deal of power to users.
- [Executing an External Procedure](executing-an-external-procedure.md)
  To run an external procedure, you must call the PL/SQL program unit (that is, the alias for the external function) that registered the external procedure.

**Parent topic:** [Developing Applications for Windows](developing-applications-for-windows.md)
