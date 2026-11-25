## Example of Running the Deinstallation Tool

Review the examples to help you understand how to run the deinstallation tool.

If you perform a deinstallation by running the `setup.exe` command with the `-deinstall` option from the installation media, then help is displayed unless you enter a `-home` flag and provide a path to the home directory of the Oracle software to remove from your system.

Use the optional flag `-paramfile` to provide a path to a response file.

In the following example, the `setup.exe` command is in the path `\``directory_path`, where `directory_path` is the path to the `database` directory on the installation media, and `C:\app\oracle\product\19.0.0\dbhome_1` is the path to the Oracle home which is removed:

    DRIVE_LETTER:\> cd \directory_path
    DRIVE_LETTER:\> setup.exe -deinstall -home C:\app\oracle\product\19.0.0\dbhome_1

The following example uses a response file in the software owner location `C:\Documents and Settings\oracle\:`

    DRIVE_LETTER:\> cd \directory_path
    DRIVE_LETTER:\> setup.exe -deinstall -paramfile C:\Documents and Settings\oracle\my_db_paramfile.tmpl

**Parent topic:** [Removing Oracle Database Client Software](removing-oracle-database-client-software.md)
