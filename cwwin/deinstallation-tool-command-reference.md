## deinstall Command Reference

You can run the `deinstall` command to remove Oracle software. You can run this command from an Oracle home directory after installation.

### Purpose

`deinstall` stops Oracle software, and removes Oracle software and configuration files on the operating system for a specific Oracle home.

### File Path

`%ORACLE_HOME%\deinstall`

### Prerequisites

Before you run the `deinstall` command for Oracle Grid Infrastructure installations:

- Dismount Oracle Automatic Storage Management Cluster File System (Oracle ACFS) and disable Oracle Automatic Storage Management Dynamic Volume Manager (Oracle ADVM).

- If Grid Naming Service (GNS) is in use, then notify your DNS administrator to delete the subdomain entry from the DNS.

### Syntax When Using the deinstall.bat Program

    deinstall.bat
                        [-silent] [-checkonly] [-paramfile complete path on input parameter properties file]
                        [-checkonly]
                        [-local]
                        [-paramfile complete path of input parameter properties file]
                        [-params name1=value [name2=value . . .]]
                        [-o complete path of directory for saving files]
                        [-tmpdir complete path of temporary directory to use]
                        [-logdir complete path of log directory to use]
                        [-skipLocalHomeDeletion]
                        [-skipRemoteHomeDeletion]
                        [-help]

### Options

Table 12-1 Options for the Deinstallation Tool

| Command Option                                                              | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                        |
|:----------------------------------------------------------------------------|:---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `home ``complete path of Oracle home`                                       | Specify this option to indicate the home path of the Oracle home to check or deinstall. To deinstall Oracle software using the `deinstall.bat` command located within the Oracle home being removed, provide a response file in a location outside the Oracle home, and do not use the `-home` option.<br>If you run `deinstall.bat` from the `%ORACLE_HOME%\deinstall` path, then the `-home` option is not required because the command knows from which home it is being run.                                                                                                                                                                   |
| `silent`                                                                    | Specify this option to run the `deinstall` in noninteractive mode. This option requires one of the following:<br>• A working system that it can access to determine the installation and configuration information; the `-silent` option does not work with failed installations.<br>• A response file that contains the configuration values for the Oracle home that is being deinstalled or deconfigured.                                                                                                                                                                                                                                       |
| `checkonly`                                                                 | Specify this option to check the status of the Oracle software home configuration. Running the `deinstall` command with the `-checkonly` option does not remove the Oracle configuration. This option generates a response file that you can use with the `deinstall.bat` command.<br>When you use the `-checkonly` option to generate a response file, you are prompted to provide information about your system. You can accept the default value the `deinstall` command has obtained from your Oracle installation, indicated inside brackets (`[]`), or you can provide different values. To accept the defaults, press Enter at each prompt. |
| `local`                                                                     | Specify this option on a multinode environment to deconfigure Oracle software in a cluster.<br>When you run `deinstall.bat` with this option, it deconfigures and deinstalls the Oracle software only on the local node (the node on which you run `deinstall.bat`) for non-shared Oracle home directories. The `deinstall` command does not deinstall or deconfigure Oracle software on remote nodes.                                                                                                                                                                                                                                             |
| `paramfile ``complete path of input parameter properties file`              | (Optional) You can specify this option to run `deinstall.bat` with a response file in a location other than the default. When you use this option, provide the complete path where the response file is located. If you run the `deinstall.bat` command from the Oracle home that you plan to deinstall, then you do not need to specify the `-paramfile` option.<br>The default location of the response file is `%ORACLE_HOME%\deinstall\response`.                                                                                                                                                                                              |
| `params`` ``name1``=``value``[ ``name2``=``value`` ``name3``=``value``...]` | Use this option with a response file to override one or more values in a response file that you created.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           |
| `o`` complete path of directory for saving response files`                  | Use this option to provide a path other than the default location where the response file (`deinstall.rsp.tmpl`) is saved.<br>The default location of the response file is `%ORACLE_HOME%\deinstall\response`.                                                                                                                                                                                                                                                                                                                                                                                                                                     |
| `tmpdir`` complete path of temporary directory to use`                      | Specifies a non-default location where the `deinstall` command writes the temporary files for the deinstallation.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  |
| `logdir`` complete path of log directory to use`                            | Specifies a non-default location where the `deinstall` command writes the log files for the deinstallation.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                        |
| `skipLocalHomeDeletion`                                                     | Specify this option in Oracle Grid Infrastructure installations on a multinode environment to deconfigure a local Grid home without deleting the Grid home.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                        |
| `skipRemoteHomeDeletion`                                                    | Specify this option in Oracle Grid Infrastructure installations on a multinode environment to deconfigure a remote Grid home without deleting the Grid home.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       |
| `help`                                                                      | Use the `-help` option to obtain additional information about the command option flags.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            |

### Location of Log Files for the Deinstallation Tool

If you use the `deinstall.bat` command located in an Oracle home, then the `deinstall` writes log files in the `C:\Program Files\Oracle\Inventory\logs` directory.

If you are using the `deinstall.bat` command to remove the last Oracle home installed on the server, then the log files are written to the current user’s home directory. For example, if you are logged in as the domain user `RACDBA\dba1`, then the log files are stored in the directory `C:\Users\dba1.RACDBA\logs`.

**Parent topic:** [Removing Oracle Clusterware and Oracle ASM Software](removing-oracle-clusterware-and-oracle-asm-software.md)
