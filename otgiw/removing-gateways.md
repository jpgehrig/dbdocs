The following topics describe how to remove Oracle Database Gateway from an Oracle home directory.

- About the Deinstallation Tool

- Removing Oracle Software

### About the Deinstallation Tool

The Deinstallation Tool (`deinstall`) is available in the installation media before installation, and is available in Oracle home directories after installation. It is located in `ORACLE_HOME``\deinstall`.

The `deinstall` command stops Oracle software, and removes Oracle software and configuration files on the operating system.

The script uses the following syntax, where variable content is indicated by italics:

    deinstall -home complete path of Oracle home [-silent] [-checkonly] [-local]
    [-paramfile complete path of input parameter property file] [-params name1=value
    name2=value . . .] [-o complete path of directory for saving files] [-help | -h]

The options are:

- `-silent`

  Use this flag to run the command in noninteractive mode. This option requires a properties file that contains the configuration values for the Oracle home that is being deinstalled or deconfigured.

  To create a properties file and provide the required parameters, see the template file `deinstall.rsp.tmpl,` located in the response folder. If you prefer, instead of using the template file, you can generate a properties file by using the `-checkonly` option to have deconfig discover information from the Oracle home that you want to deinstall and deconfigure. The tool will generate the properties file, which you can then use with the `-silent` option.

- `-checkonly`

  Use this flag to check the status of the Oracle software home configuration. Running the command with the `-checkonly `flag does not remove the Oracle configuration.

- `-local`

  Use this flag on a multinode environment to deconfigure Oracle software in a cluster.

  When you run deconfig with this flag, it deconfigures and deinstalls the Oracle software on the local node (the node where deconfig is run). On remote nodes, it deconfigures Oracle software, but does not deinstall the Oracle software.

- `-paramfile` `complete path of input parameter property file`

  Use this flag to run deconfig with a parameter file in a location other than the default. When you use this flag, provide the complete path where the parameter file is located.

  The default location of the parameter file depends on the location of deconfig:

  - From the installation media or stage location: `ORACLE_HOME``\response`

  - From a unzipped archive file from OTN: `ziplocation\response`

  - After installation from the installed Oracle home: `ORACLE_HOME``\deinstall\response`

- `-params [name1=``value` `name 2=``value` `name3=``value` `. . .]`

  Use this flag with a parameter file to override one or more values that you want to change in a parameter file you have already created.

- `-o` `complete path of directory for saving files`

  Use this flag to provide a path other than the default location where the properties file is saved. The default location is \\`response\deinstall.rsp.tmpl`.

  The default location of the parameter file depends on the location of deconfig:

  - From the installation media or stage location before installation: `ORACLE_HOME\`

  - From an unzipped archive file from OTN: `\ziplocation\response\`

  - After installation from the installed Oracle home: `ORACLE_HOME``\deinstall\response`

- `-help | -h`

  Use the help option (`-help` or `-h`) to obtain additional information about the optional flags

### Removing Oracle Software

Complete the following procedure to remove Oracle software:

1.  Log in as a member of the Administrators group.

2.  Run the `deinstall` command, providing information about the Oracle System Identifier (SID), when prompted.
