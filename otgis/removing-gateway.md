The following topics describe how to remove Oracle Database Gateway from an Oracle home directory.

- About the Deinstallation Tool

- Removing Oracle Software

### 17.1 About the Deinstallation Tool

The Deinstallation Tool (`deinstall`) is available in the installation media before installation, and is available in Oracle home directories after installation. It is located in the path` $ORACLE_HOME/deinstall`.

The `deinstall` command stops Oracle software, and removes Oracle software and configuration files on the operating system.

The command uses the following syntax, where variable content is indicated by italics:

    deinstall -home complete path of Oracle home [-silent] [-checkonly] [-local]
    [-paramfile complete path of input parameter property file] [-params name1=value
    name2=value . . .] [-o complete path of directory for saving files] [-help | -h]

The options are:

- `-silent`

  Use this flag to run the command in silent or response file mode. If you use the `-silent` flag, then you must use the `-paramfile` flag, and provide a parameter file that contains the configuration values for the Oracle home that you want to deinstall or deconfigure.

  You can generate a parameter file to use or modify by running `deinstall` with the `-checkonly` flag. The `deinstall` command then discovers information from the Oracle home that you want to deinstall and deconfigure. It generates the properties file, which you can then use with the `-silent` option.

  You can also modify the template file `deinstall.rsp.tmpl`, located in the response folder.

- `-checkonly`

  Use this flag to check the status of the Oracle software home configuration. Running the command with the `-checkonly` flag does not remove the Oracle configuration. The `-checkonly` flag generates a parameter file that you can use with the deinstall command.

- `-local`

  Use this flag on a multinode environment to deconfigure Oracle software in a cluster.

  When you run `deconfig` with this flag, it deconfigures and deinstalls the Oracle software on the local node (the node where deconfig is run). On remote nodes, it deconfigures Oracle software, but does not deinstall the Oracle software.

- `-paramfile` `complete path of input parameter property file`

  Use this flag to run deconfig with a parameter file in a location other than the default. When you use this flag, provide the complete path where the parameter file is located.

  The default location of the parameter file depends on the location of deconfig:

  - From the installation media or stage location: `$ORACLE_HOME/inventory/response`

  - From a unzipped archive file from OTN: `/ziplocation/response`

  - After installation from the installed Oracle home: `$ORACLE_HOME/deinstall/response`

- `-params [name1=``value` `name 2=``value` `name3=`value `. . .]`

  Use this flag with a parameter file to override one or more values that you want to change in a parameter file you have already created.

- `-o ``complete path of directory for saving response files`

  Use this flag to provide a path other than the default location where the properties file (`deinstall.rsp.tmpl`) is saved.

  The default location of the parameter file depends on the location of deconfig:

  - From the installation media or stage location before installation: `$ORACLE_HOME/`

  - From a unzipped archive file from OTN: `/ziplocation/response/`

  - After installation from the installed Oracle home: `$ORACLE_HOME/deinstall/response`

- `-help | -h`

  Use the help option (`-help` or `-h`) to obtain additional information about the command option flags.

### 17.2 Removing Oracle Software

Complete the following procedure to remove Oracle software:

1.  Log in as the installation owner.
2.  Run the `deinstall` command, providing information about your servers as prompted.
