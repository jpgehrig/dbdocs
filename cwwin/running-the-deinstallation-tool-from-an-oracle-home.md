## Running the deinstall Command From an Oracle Home

You can run the `deinstall` command from an Oracle home.

1.  The default method for running the `deinstall` command is from the `deinstall` directory in the Oracle home as the Oracle Installation user:
    `C:\> %ORACLE_HOME%\deinstall\deinstall.bat`
2.  Provide information about your servers as prompted or accept the defaults.

The `deinstall` command stops Oracle software, and removes Oracle software and configuration files on the operating system.

Example 12-1 Running `deinstall.bat` From Within the Oracle Home

The most common method of running the `deinstall` command is to use the version installed in the Oracle home being removed. The `deinstall` command determines the software configuration for the local Oracle home, and then provides default values at each prompt. You can either accept the default value, or override it with a different value. If the software in the Oracle home is not running (for example, after an unsuccessful installation), then the `deinstall` command cannot determine the configuration, and you must provide all the configuration details either interactively or in a response file. To use the `deinstall` command located in the Oracle home directory, issue the following command, where `C:\app\19.0.0\grid` is the location of Grid home:

Use the following command while logged in as a member of the Administrators group to remove the Oracle Grid Infrastructure installation from your cluster:

    C:\> C:\app\19.0.0\grid\deinstall\deinstall.bat

Provide additional information as prompted.

**Note:**

When using the `deinstall` command from a location other than within the Oracle home being removed, you must specify the `-home` option on the command line.

**Parent topic:** [Using the deinstall Command to Remove Oracle Clusterware and Oracle ASM](using-the-deinstallation-tool-to-remove-oracle-clusterware-and-oracle-asm.md)
