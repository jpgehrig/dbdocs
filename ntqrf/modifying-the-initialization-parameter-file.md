Describes how to modify the initialization parameter file.

To use the starter database `orcl` as the basis for your new database:

1.  Copy `ORACLE_BASE``\admin\orcl\pfile\init.ora`.

2.  Place the copy in `ORACLE_BASE``\admin\prod\pfile\init.ora`.

3.  Modify the file by performing the following tasks:

    **Note:**

    Starting with Oracle9i Release 2 (9.2), nesting of quotation marks using the backslash (\\ escape character is no longer supported. This affects how Oracle Database interprets the parameter values in your initialization parameter file. For example, if you specified `CONTROL_FILES = "ctlfile\'1.ora"` in releases before release 9.2, the file name was interpreted as `ctlfile'1.ora`. Starting with release 9.2, the file name will be interpreted as `ctlfile\'1.ora`.

    Oracle highly recommends modifying your parameter files to remove such references and other methods of nesting quotation marks in the initialization parameter values.

    1.  If you do not have an existing database on your system, then you cannot copy an existing initialization parameter file to use as the basis for your new initialization parameter file. However, you can use the sample initialization parameter file `initsmpl.ora` provided in:

            ORACLE_HOME\admin\sample\pfile

        This is the basis for the initialization parameter file for the database `prod`.

    2.  If you use the `initsmpl.ora` file as the basis for the initialization parameter file, then the following parameters must be set to the indicated values, otherwise you cannot start database `prod`:

        `DB_NAME=prod.domain`

        The parameter `DB_NAME` indicates the database name and must match the name used in the `CREATE DATABASE` statement. Give a unique database name to each database. You can use eight characters for a database name. The name is not required to match the `SID` of the database service.

        `INSTANCE_NAME=prod.domain`

        `SERVICE_NAMES=prod.domain`

        `CONTROL_FILES = (` `"C:\app\``username``\oradata\prod\control01.ctl",` `"C:\app\``username``\oradata\prod\control02.ctl",` `"C:\app\``username``\oradata\prod\control03.ctl")`

        The parameter `CONTROL_FILES` lists the database control files. You do not have to control files on your file system at this point, because control files are created when you run the `CREATE DATABASE` statement. Ensure that you specify the complete path and the file name, including the drive letter.

        `DB_FILES=100`

        Modifying the initialization parameter `DB_FILES` is not required, but it is recommended to optimize performance. Set this parameter to the same number as the value of the `MAXDATAFILES` option of the `CREATE DATABASE` statement. The value of `100` is used for this example.

        The `DIAGNOSTIC_DEST` initialization parameter sets the location of the Automatic Diagnostic Repository (ADR), which is a directory structure stored outside of the database. The ADR is used in problem diagnostics.

        Use `DIAGNOSTIC_DEST =` `ORACLE_HOME\log` if the environment variable `ORACLE_BASE` is not set.

        Use `DIAGNOSTIC_DEST =` `ORACLE_BASE` variable if the environment variable `ORACLE_BASE` is set.

        **See Also:**

        - [Oracle Database Installation Guide for Microsoft Windows](../ntdbi/index.md) for information about ADR

        - [Oracle Database Reference](../refrn/initialization-parameters.md) for information about other initialization parameters that you can add or modify

**Related Topics**

- [Adding the CREATE DATABASE Statement in a Script](putting-the-create-database-statement-in-a-script.md)

**Parent topic:** [Overview of Database Creation Tasks on Windows Using Command-Line Tools](overview-of-database-creation-tasks-on-windows-using-command-line-tools.md)
