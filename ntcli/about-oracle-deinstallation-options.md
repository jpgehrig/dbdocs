## About Oracle Deinstallation Options

You can stop and remove Oracle Database software and components in an Oracle Database home with Oracle Universal Installer.

Using Oracle Universal Installer with the deinstall option, or running the deinstallation tool from the Oracle home, stops and removes Oracle software and it's components, such as database client and configuration files for a specific Oracle home.

You can remove the following software using Oracle Universal Installer or the Oracle deinstallation tool:

- Oracle Database

- Oracle Grid Infrastructure, which includes Oracle Clusterware and Oracle Automatic Storage Management (Oracle ASM)

- Oracle Real Application Clusters (Oracle RAC)

- Oracle Database Client

The deinstallation tool is integrated with the database client installation media. You can run the deinstallation tool with the` -deinstall` and `-home `options from the base directory of the Oracle Database, Oracle Database Client, or Oracle Grid Infrastructure installation media.

The deinstallation tool is also available as a separate command (`deinstall`) in Oracle home directories after installation. It is located in `ORACLE_HOME``\deinstall` directory.

The deinstallation tool uses the information you provide, plus information gathered from the software home to create a response file. You can alternatively supply a response file generated previously by the `deinstall` command using the `–checkonly` option, or by editing the response file template.

Using Oracle Universal Installer with the deinstall option, or running the deinstallation tool from the Oracle home, stops and removes Oracle software and its components, such as database and configuration files for a specific Oracle home.

If the software in the Oracle home is not running (for example, after an unsuccessful installation), then the deinstallation tool cannot determine the configuration, and you must provide all the configuration details either interactively or in a response file.

**Caution:**

When you install Oracle Database, if the central inventory contains no other registered homes besides the home that you are deconfiguring and removing, then the Deinstallation tool removes the following files and directory contents in the Oracle base directory of the Oracle Database installation owner:

- admin

- cfgtoollogs

- checkpoints

- diag

- oradata

- flash_recovery_area

Oracle strongly recommends that you configure your installations using an Optimal Flexible Architecture (OFA) configuration, and that you reserve Oracle base and Oracle home paths for exclusive use of Oracle software. If you have any user data in these locations in the Oracle base that is owned by the user account that owns the Oracle software, then the deinstallation tool deletes this data.

In addition, for Oracle Grid Infrastructure installations:

- Oracle Automatic Storage Management Cluster File System (Oracle ACFS) must be dismounted and Oracle Automatic Storage Management Dynamic Volume Manager (Oracle ADVM) must be disabled.

- If Grid Naming Service (GNS) is in use, then the entry for the subdomain needs to be deleted from DNS by your DNS administrator.

Oracle recommends that you run the deinstallation tool as the Oracle software installation owner. The default method for running the deinstallation tool is from the deinstall directory in the Oracle home as the installation owner:

    ORACLE_HOME\deinstall
    DRIVE_LETTER:\> deinstall\deinstall.bat

The command uses the following syntax, where variable content is indicated by italics:

    deinstall.bat [-silent] [-checkonly]
    [-paramfile complete path of input parameter property file] [-params name1=value name2=value . . .]
    [-o complete path of directory for saving files] [-help]
    [-tmpdir complete path of temporary directory to use]
    [-logdir complete path of log directory to use] [-help]


To run the deinstallation tool from the database installation media, use the `setup.exe` command with the `-deinstall` option, followed by the `-home` option to specify the path of the Oracle home you want to remove using the following syntax, where variable content is indicated in italics:

    setup.exe -deinstall -home complete path of Oracle home [-silent] [-checkonly] [-local]
    [-paramfile complete path of input parameter property file] [-params name1=value
    name2=value . . .] [-o complete path of directory for saving files] [-help]
    [-tmpdir complete path of temporary directory to use]
    [-logdir complete path of log directory to use] [-help]


Provide information about your servers as prompted or accept the defaults.

**Note:**

If User Account Control is enabled, then you must create a desktop shortcut to a DOS command window. Open the command window through the Run as administrator, right-click context menu, and start the deinstallation tool.

In addition, you can run the deinstallation tool from other locations, or with a response file, or select other options to run the tool.

- `-home`

  Use this flag to indicate the home path of the Oracle home to check or deinstall. To deinstall Oracle software using the `deinstall` command, located in the Oracle home you plan to deinstall, provide a response file in a location outside the Oracle home, and do not use the `-home` flag.

  If you run the deinstallation tool from the `ORACLE_HOME\deinstall` path, then the `-home` flag is not required because the tool identifies the location of the home where it is run. If you run the tool using `setup.exe -deinstall` from the installation media, then `-home` is mandatory.

- `-silent`

  Use this flag to run the deinstallation tool in a noninteractive mode. This option requires one of the following:

  - A working system that it can access to determine the installation and configuration information. The `-silent` flag does not work with failed installations.

  - A response file that contains the configuration values for the Oracle home that is being deinstalled or deconfigured.

  You can generate a response file to use or modify by running the tool with the `-checkonly` flag. The tool then discovers information from the Oracle home to deinstall and deconfigure. It generates the response file that you can then use with the `-silent` option.

  You can also modify the template file `deinstall.rsp.tmpl`, located in the `ORACLE_HOME``\deinstall\response` directory.

- `-checkonly`

  Use this flag to check the status of the Oracle software home configuration. Running the deinstallation tool with the `-checkonly` flag does not remove the Oracle configuration. The `-checkonly` flag generates a response file that you can then use with the deinstallation tool and `-silent` option.

- `-paramfile` `complete path of input parameter property file`

  Use this flag to run the deinstallation tool with a response file in a location other than the default. When you use this flag, provide the complete path where the response file is located.

  The default location of the response file depends on the location of the deinstallation tool:

  - From the installation media or stage location: `\response`

  - After installation from the installed Oracle home: `\deinstall\response`.

- `-params` \["`name1=``value`" "`name2=``value`" "`name3=``value`" . . .\]

  Use this flag with a response file to override one or more values to change it in a response file you have created.

- `-o` `complete path of directory for saving response file`

  Use this flag to provide a path other than the default location where the response file is saved. The default location is `\response\deinstall.rsp.tmpl`.

  The default location of the response file depends on the location of deinstallation tool:

  - From the installation media or stage location before installation: `\response`

  - After installation from the installed Oracle home: `ORACLE_HOME``/deinstall/response`.

- `-tmpdir` `complete path of temporary directory`

  Specifies a non-default location where Oracle Deinstallation Tool writes the temporary files for the deinstallation.

- `-logdir` `complete path of log directory`

  Specifies a non-default location where Oracle Deinstallation Tool writes the log files for the deinstallation.

- `-help`

  Use the help option (`-help` ) to obtain additional information about the command optional flags.

**Related Topics**

- [Managing User Accounts with User Account Control](managing-user-accounts-with-user-account-control.md)

**Parent topic:** [Removing Oracle Database Client Software](removing-oracle-database-client-software.md)
