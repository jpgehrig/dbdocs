Depending on your platform, you may have to set environment variables before starting SQL\*Plus, or at least verify that they are set properly.

For example, on most platforms, you must set the environment variables `ORACLE_SID` and `ORACLE_HOME`. In addition, you must configure the `PATH` environment variable to include the `ORACLE_HOME/bin` directory. Some platforms may require additional environment variables:

- On UNIX and Linux, set environment variables by entering operating system commands.

- On Windows, Oracle Universal Installer (OUI) automatically assigns values to `ORACLE_HOME` and `ORACLE_SID` in the Windows registry.

If you did not create a database upon installation, OUI does not set `ORACLE_SID` in the registry; after you create your database at a later time, you must set the `ORACLE_SID` environment variable from a command window.

UNIX and Linux installations come with two scripts, `oraenv` and `coraenv`, that you can use to easily set environment variables. For more information, see Oracle Database Administrator's Reference for Linux and UNIX-Based Operating Systems.

For all platforms, when switching between instances with different Oracle homes, you must change the `ORACLE_HOME` environment variable. If multiple instances share the same Oracle home, then you must change only `ORACLE_SID` when switching instances.

Example 3-1 Setting Environment Variables in UNIX (C Shell)

    setenv ORACLE_SID orcl
    setenv ORACLE_HOME /u01/app/oracle/product/database_release_number/dbhome_1
    setenv LD_LIBRARY_PATH $ORACLE_HOME/lib:/usr/lib:/usr/dt/lib:/usr/openwin/lib:/usr/ccs/lib

Example 3-2 Setting Environment Variables in UNIX (Bash Shell)

    export ORACLE_SID=orcl
    export ORACLE_HOME=/u01/app/oracle/product/database_release_number/dbhome_1
    export LD_LIBRARY_PATH=$ORACLE_HOME/lib:/usr/lib:/usr/dt/lib:/usr/openwin/lib:/usr/ccs/lib

Example 3-3 Setting Environment Variables in Windows

    SET ORACLE_SID=orawin2

Example 3-3 assumes that `ORACLE_HOME` and `ORACLE_SID` are set in the registry but that you want to override the registry value of `ORACLE_SID` to connect to a different instance.

On Windows, environment variable values that you set in a command prompt window override the values in the registry.

**Parent topic:** [Connecting to the Database with SQL\*Plus](connecting-to-the-database-with-sql-plus.md)
