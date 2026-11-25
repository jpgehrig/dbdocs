Learn how you can view Windows-specific parameter values.

To view Windows-specific parameter values, use an ASCII editor to open the initialization parameter file:

    ORACLE_HOME\admin\db_name\pfile\init.ora

To display anyparameter value whether set in the initialization parameter file or the Oracle Database kernel, enter the following command at the SQL\*Plus command prompt:

    SQL> SHOW PARAMETER parameter_name

where `parameter_name` is the name of a specific initialization parameter.

**Parent topic:** [Oracle Database Specifications for Windows](oracle-database-specifications-for-windows.md)
