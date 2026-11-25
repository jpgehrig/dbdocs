## Deinstallation Examples for Oracle Database Client

Use these examples to learn how to run deinstallation using a standalone tool (`deinstall`).

Use the optional flag `-paramfile` to provide a path to a response file.

In the following example, the `deinstall` command is in the path `C:`\\`app\oracle\product\19.0.0\client_1\deinstall`, and it uses a response file in the software owner location `C:\Documents and Settings\oracle\`:

    DRIVE_LETTER:\> cd \app\oracle\product\19.0.0\client_1\deinstall\
    DRIVE_LETTER:\> deinstall.bat -paramfile %HOMEPATH%\my_db_paramfile.tmpl

**Parent topic:** [Removing Oracle Database Client Software](removing-oracle-database-client-software.md)
