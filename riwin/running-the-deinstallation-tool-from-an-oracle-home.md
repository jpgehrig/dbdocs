## Running the deinstall Command From an Oracle Home

You can run the `deinstall` command from an Oracle home.

1.  The default method for running the `deinstall` command is from the `deinstall` directory in the Oracle home as the Oracle Installation user:
    `C:\> %ORACLE_HOME%\deinstall\deinstall.bat`
2.  Provide information about your servers as prompted or accept the defaults.

The `deinstall` command stops Oracle software, and removes Oracle software and configuration files on the operating system.

Example 7-1 Running `deinstall.bat` From Within the Oracle Home

The most common method of running the `deinstall` command is to use the version installed in the Oracle home being removed. The `deinstall` command determines the software configuration for the local Oracle home, and then provides default values at each prompt. You can either accept the default value, or override it with a different value. If the software in the Oracle home is not running (for example, after an unsuccessful installation), then the `deinstall` command cannot determine the configuration, and you must provide all the configuration details either interactively or in a response file. To use the `deinstall` command located in the current Oracle home directory, issue the following commands while logged in as a member of the Administrators group:

    C:\> C:\app\oracle\product\19.0.0\dbhome_1\deinstall\deinstall.bat

Provide additional information as prompted.

**Note:**

When using the `deinstall` command from a location other than within the Oracle home being removed, you must specify the `-home` option on the command line.

**Parent topic:** [Using the Deinstallation Tool to Remove Oracle RAC](using-the-deinstallation-tool-to-remove-oracle-rac.md)
