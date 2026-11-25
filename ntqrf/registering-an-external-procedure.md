Once you have built a DLL containing your external procedures, you must register your external procedures with Oracle Database.

Now, you can configure the `EXTPROC` process to be authenticated through a `CREDENTIAL` for better security.

Oracle Database supports two new extensions to the `CREATE LIBRARY` command. This includes a `CREDENTIAL` clause and a `DIRECTORY` object option. The `CREDENTIAL` clause defines the user the `EXTPROC` runs as while the `DIRECTORY` object option specifies the directory where the DLL can be located.

To create a PL/SQL library to map to the DLL:

1.  Set environment variable `EXTPROC_DLLS` in the `ENVS` parameter in `listener.ora`. For example:
        SID_LIST_LISTENER =
         (SID_LIST =
          (SID_DESC =
           (SID_NAME=PLSExtProc)
           (ENVS=EXTPROC_DLLS=C:\app\oracle\product\19.0.0\dbhome_1\rdbms\extproc\extern.dll)
           (ORACLE_HOME=C:\app\oracle\product\19.0.0\dbhome_1)
           (PROGRAM=extproc)
          )
         )
2.  Start SQL\*Plus:
        C:\> sqlplus
3.  Connect to the database with appropriate username and password.
4.  Create the PL/SQL library using the `CREATE LIBRARY` command:
        DBMS_CREDENTIAL.CREATE_CREDENTIAL(...);
        CREATE DIRECTORY DLL_LOC as ...;
        CREATE LIBRARY externProcedures as 'extern.dll' in DLL_LOC credential the_credential;

    where `the_credential` is the name chosen during the `DBMS_CREDENTIAL.CREATE_CREDENTIAL` invocation

        SQL> CREATE LIBRARY externProcedures AS 'C:\app\oracle\product\19.0.0\dbhome_1\rdbms\ extproc\extern.dll';

    where `externProcedures` is an alias library (essentially a schema object in the database), and

        C:\app\oracle\product\19.0.0\dbhome_1\rdbms\extproc\extern.dll

    is the path to the Windows operating system `dllextern.dll`. This example uses `C:\app\oracle\product\19.0.0` as your Oracle base and `dbhome_1` as your Oracle home.

    **Note:**

    The DBA must grant the `EXECUTE` privilege on the PL/SQL library to users who want to call the library's external procedure from PL/SQL or SQL. Separate `EXECUTE` privilege on credential and directory object extensions are required for them to function properly.
5.  Create a PL/SQL program unit specification.
    Do this by writing a PL/SQL subprogram that uses the `EXTERNAL` clause instead of declarations and a `BEGIN...END` block. The `EXTERNAL` clause is the interface between PL/SQL and the external procedure. The `EXTERNAL` clause identifies the following information about the external procedure:

    - Name

    - DLL alias

    - Programming language in which it was written

    - Calling standard (defaults to C if omitted)

    In the following example, `externProcedures` is a DLL alias. You need the `EXECUTE` privilege for this library. The external procedure to call is `find_max`. If enclosed in double quotation marks, it becomes case-sensitive. The `LANGUAGE` term specifies the language in which the external procedure was written.

        CREATE OR REPLACE FUNCTION PLS_MAX(
          x BINARY_INTEGER,
          y BINARY_INTEGER)
        RETURN BINARY_INTEGER AS EXTERNAL
          LIBRARY externProcedures
          NAME "find_max"
          LANGUAGE C
          PARAMETERS (
            x long,                  -- stores value of x
            x_INDICATOR short,       -- used to determine if x is a NULL value
            y long,                  -- stores value of y
            y_INDICATOR short,        -- used to determine if y is a NULL value
          RETURN INDICATOR short );  -- need to pass pointer to return value's
                                     -- indicator variable to determine if NULL
        -- This means that my function is defined as:
            -- long max(long x, short x_indicator,
            -- long y, short y_indicator, short * ret_indicator)

**Parent topic:** [About Building External Procedures](about-building-external-procedures.md)
