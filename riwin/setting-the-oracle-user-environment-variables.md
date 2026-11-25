## Setting the Oracle User Environment Variables

Unlike on other platforms, do not set `ORACLE_HOME` as a fixed environment variable when running Oracle Database on Windows operating systems. This is because the Oracle software determines where executable files reside at run time.

When you invoke an Oracle executable program on Windows, for example `sqlplus.exe`, the `ORACLE_HOME`, `ORACLE_BASE`, and `ORACLE_SID` variables are determined by the `PATH` environment variable and the location of the executable program (which Oracle home it resides in). To use SQL\*Plus to manage a different database or Oracle ASM instance, click the Windows Start button, select the correct Oracle Home for the instance you want to manage, and then select the SQL\*Plus utility.

You can use Oracle Universal Installer (OUI) to specify an Oracle home as the default Oracle home and update the PATH environment variable to point to that Oracle home.

**See Also:**

"[Multiple Oracle Home Directories on Windows](multiple-oracle-home-directories-on-windows.md)" for detailed instructions on how to change the default Oracle home.

**Parent topic:** [Recommended Postinstallation Tasks](recommended-postinstallation-tasks.md)
