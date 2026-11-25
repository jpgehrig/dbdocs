Learn about Cluster Verification Utility (CVU), and how to use it to prepare for installations, patching, or other system changes.

When you modify your cluster, Oracle recommends that you use Cluster Verification Utility (CVU) to perform system checks. Using CVU ensures that you have completed the required system configuration and preinstallation steps, so that your Oracle Grid Infrastructure or Oracle Real Application Clusters (Oracle RAC) installation, update, or patch operation, completes successfully.

Oracle Universal Installer is fully integrated with CVU, automating many CVU prerequisite checks. Oracle Universal Installer runs all prerequisite checks and associated fixup scripts when you run the installer.

**See Also:**

- [Oracle Real Application Clusters Administration and Deployment Guide](../racad/server-control-utility-reference.md) for information about using the Server Control utility (SRVCTL) to manage CVU

- [Oracle Grid Infrastructure Installation Guide](../install-and-upgrade.md) and [Oracle Real Application Clusters Installation Guide](../install-and-upgrade.md) for information about how to manually install CVU

**Note:**

Check for and download updated versions of CVU on Oracle Technology Network at the following URL:

[`http://www.oracle.com/technetwork/index.html`](http://www.oracle.com/technetwork/index.html)

This appendix describes CVU under the following topics:

- About Cluster Verification Utility

  - Overview of CVU

  - CVU Operational Notes

  - Special CVU Topics

- Cluster Verification Utility Command Reference

- Troubleshooting and Diagnostic Output for CVU

### About Cluster Verification Utility

This section includes topics which relate to using CVU.

- Overview of CVU

- CVU Operational Notes

- Special CVU Topics

#### Overview of CVU

CVU can verify the primary cluster components during an operational phase or stage.

A component can be basic, such as free disk space, or it can be complex, such as checking Oracle Clusterware integrity. For example, CVU can verify multiple Oracle Clusterware subcomponents across Oracle Clusterware layers. Additionally, CVU can check disk space, memory, processes, and other important cluster components. A stage could be, for example, database installation, for which CVU can verify whether your system meets the criteria for an Oracle Real Application Clusters (Oracle RAC) installation. Other stages include the initial hardware setup and the establishing of system requirements through the fully operational cluster setup.

Table A-1 lists verifications you can perform using CVU.

Table A-1 Performing Various CVU Verifications

| Verification to Perform                                   | CVU Commands to Use                                                                                                                                                                                                                                                                                                                                                                             |
|:----------------------------------------------------------|:------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| System requirements verification                          | `cluvfy comp sys`                                                                                                                                                                                                                                                                                                                                                                               |
| Oracle Cluster File System verification                   | `cluvfy stage cfs`                                                                                                                                                                                                                                                                                                                                                                              |
| Storage verifications                                     | • `cluvfy comp freespace`<br>• `cluvfy comp space`<br>• `cluvfy comp ssa`<br>• `cluvfy stage acfscfg`                                                                                                                                                                                                                                                                                           |
| Network verification                                      | `cluvfy stage hwos`                                                                                                                                                                                                                                                                                                                                                                             |
| Connectivity verifications                                | • `cluvfy comp nodecon`<br>• `cluvfy comp nodereach`                                                                                                                                                                                                                                                                                                                                            |
| Cluster Time Synchronization Services verification        | `cluvfy comp clocksync`                                                                                                                                                                                                                                                                                                                                                                         |
| User and Permissions verification                         | `cluvfy comp admprv`                                                                                                                                                                                                                                                                                                                                                                            |
| Node comparison and verification                          | `cluvfy comp peer`                                                                                                                                                                                                                                                                                                                                                                              |
| Installation verification                                 | • `cluvfy stage appcluster`<br>• `cluvfy stage hwos`<br>• `cluvfy stage dbcfg`<br>• `cluvfy stage -pre dbinst`<br>• `cluvfy stage crsinst`<br>• `cluvfy stage hacfg`<br>• `cluvfy stage nodeadd`                                                                                                                                                                                                |
| Deletion verification                                     | `cluvfy stage nodedel`                                                                                                                                                                                                                                                                                                                                                                          |
| Oracle Clusterware and Oracle ASM Component verifications | • `cluvfy comp acfs`<br>• `cluvfy comp asm`<br>• `cluvfy comp clumgr`<br>• `cluvfy comp crs`<br>• `cluvfy comp dhcp`<br>• `cluvfy comp dns`<br>• `cluvfy comp gns`<br>• `cluvfy comp gpnp`<br>• `cluvfy comp ha`<br>• `cluvfy comp nodeapp`<br>• `cluvfy comp ocr`<br>• `cluvfy comp ohasd`<br>• `cluvfy comp olr`<br>• `cluvfy comp scan`<br>• `cluvfy comp software`<br>• `cluvfy comp vdisk` |

#### CVU Operational Notes

This section includes the following topics:

- CVU Installation Requirements

- CVU Usage Information

- CVU Configuration File

- Privileges and Security

- Using CVU Help

- Deprecated and Desupported CLUVFY Commands

##### CVU Installation Requirements

CVU installation requirements are:

- At least 30 MB free space for the CVU software on the node from which you run CVU

- A work directory with at least 25 MB free space on each node. The default location of the work directory is `/tmp` on Linux and UNIX systems, and the value specified in the `TEMP` environment variable on Windows systems. You can specify a different location by setting the `CV_DESTLOC` environment variable.

  When using CVU, the utility attempts to copy any needed information to the CVU work directory. It checks for the existence of the work directory on each node. If it does not find one, then it attempts to create one. Make sure that the CVU work directory either exists on all nodes in your cluster or proper permissions are established on each node for the user running CVU to create that directory.

##### CVU Usage Information

CVU includes two scripts: `runcluvfy.sh` (`runcluvfy.bat` on Windows), which you use before installing Oracle software.

`cluvfy` (`cluvfy.bat` on Windows) are located in the `Grid_home` directory and `Grid_home``/bin`, respectively. The `runcluvfy.sh` script contains temporary variable definitions which enable it to run before you install Oracle Grid Infrastructure or Oracle Database. After you install Oracle Grid Infrastructure, use the `cluvfy` command to check prerequisites and perform other system readiness checks.

**Note:**

Oracle Universal Installer runs `cluvfy` to check all prerequisites during Oracle software installation.

Before installing Oracle software, run `runcluvfy.sh` from the directory where you want your Grid home to be located, as follows:

    cd /u01/app/19.0.0/grid
    ./runcluvfy.sh options

In the preceding example, the `options` variable represents CVU command options that you select. For example:

    $ ./runcluvfy.sh comp nodereach -n node1,node2 -verbose

CVU commands may include the following report options:

- `-json`: Displays the report output in a JSON format. If the `-json` option is not specified, then the detailed report is displayed as text to the standard output.

- `–html`: Displays the CVU report output in HTML format. If the `-html` option is not specified, then the detailed report is displayed as text to the standard output.

- `-verbose`: Displays explanations about all CVU checks, both failed and passed, in the detailed summary section of the output.

- `–file ``file_location`: Depending on the format specified, save the output with the `.htm`, `.json`, or `.txt` file extension to the specific location.

When you enter a CVU command, it provides a summary of the test. During preinstallation, Oracle recommends that you obtain detailed output by using the `-verbose` argument with the CVU command. The `-verbose` argument produces detailed output of individual checks. Where applicable, it shows results for each node in a tabular layout.

Run the CVU command-line tool using the `cluvfy` command. Using `cluvfy` does not adversely affect your cluster environment or your installed software. You can run `cluvfy` commands at any time, even before the Oracle Clusterware installation. In fact, CVU is designed to assist you as soon as your hardware and operating system are operational. If you run a command that requires Oracle Clusterware on a node, then CVU reports an error if Oracle Clusterware is not yet installed on that node.

The node list that you use with CVU commands should be a comma-delimited list of host names without a domain. CVU ignores domains while processing node lists. If a CVU command entry has duplicate node entries after removing domain information, then CVU eliminates the duplicate node entries.

For network connectivity verification, CVU discovers all of the available network interfaces if you do not specify an interface on the CVU command line. For storage accessibility verification, CVU discovers shared storage for all of the supported storage types if you do not specify a particular storage identification on the command line. CVU also discovers the Oracle Clusterware home if one is available.

**See Also:**

Privileges and Security for usage security information

##### CVU Output

CVU output consists of five distinct sections, including:

- Header: A single line containing information about what checks the stage or component is performing.

- Configuration: CVU evaluates whether the operation can be performed on all nodes. If the nodes you specify are either down or do not satisfy the necessary prerequisite conditions (such as no SSH setup), then error messages about these nodes are displayed here. This section may not always be included in the output. When the check being performed can be run on all nodes involved in the operation, then this section will not display in the output.

- Progress Message: CVU displays progress messages in this section as it cycles through various checks, which helps you determine if CVU hangs.

- Detailed Summary: By default, CVU only displays failed tasks or subtasks in this section. If you choose the `-verbose` option, then CVU displays detailed information for all tasks and subtasks.

- Executive Summary: Finally, CVU displays a concise summary of the entire checking process, similar to the following examples:

      $ cluvfy stage -pre crsinst -n sales65
      CVU operation performed: stage -pre crsinst
      Date: May 5, 2023 6:40:41 AM
      CVU version: 23.1.0.0.0 (050323x8664)
      CVU home: /scratch/oracle/crshome
      User: grid
      Operating system: Linux5.4.17-2136.302.7.2.1.el8uek.x86_64

      $ cluvfy comp baseline -collect all -allnodes
      Collection report for this execution is saved in file "/scratch/oracle/base/crsdata/@global/cvu/baseline/users/cvubaseline_04272022190027.zip".
      CVU operation performed: baseline
      Date: May 5, 2023 8:20:31 AM
      CVU version: 23.1.0.0.0 (050323x8664)
      Clusterware version: 23.0.0.0.0
      CVU home: /scratch/oracle/crshome
      Grid home: /u01/app/23.0.0/grid
      User: grid
      Operating system: Linux5.4.17-2136.302.7.2.1.el8uek.x86_64

##### CVU Configuration File

You can use the CVU configuration file to define specific inputs for the execution of CVU. The path for the configuration file is `Grid_home``/cv/admin/cvu_config` (or `Staging_area``\clusterware\stage\cvu\cv\admin` on Windows platforms). You can modify this file using a text editor. The inputs to CVU are defined in the form of key entries. You must follow these rules when modifying the CVU configuration file:

- Key entries have the syntax `name=value`

- Each key entry and the value assigned to the key only defines one property

- Lines beginning with the number sign (`#`) are comment lines and are ignored

- Lines that do not follow the syntax `name=value` are ignored

The following is the list of keys supported by CVU:

- `CV_NODE_ALL`: If set, it specifies the list of nodes that should be picked up when Oracle Clusterware is not installed. By default, this entry is commented out.

- `CV_ORACLE_RELEASE`: If set, it specifies the specific Oracle release (`10.1`, `10.2`, `11.1`, `11.2`, `12.1`, or `12.2`) for which the verifications have to be performed. If set, you do not have to use the `-r ``release` option wherever it is applicable. The default value is `12.2`.

- `CV_RAW_CHECK_ENABLED`: If set to `TRUE`, it enables the check for accessibility of shared disks on Linux and UNIX systems. This shared disk accessibility check requires that you install the `cvuqdisk` RPM Package Manager (rpm) on all of the nodes. By default, this key is set to `TRUE` and shared disk check is enabled.

- `CV_ASSUME_DISTID`: This property is used in cases where CVU cannot detect or support a particular platform or a distribution. Oracle does not recommend that you change this property as this might render CVU non-functional.

- `CV_XCHK_FOR_SSH_ENABLED`: If set to `TRUE`, it enables the X-Windows check for verifying user equivalence with `ssh`. By default, this entry is commented out and X-Windows check is disabled.

- `ORACLE_SRVM_REMOTECOPY`: If set, it specifies the location for the `scp` or `rcp` command to override the CVU default value. By default, this entry is commented out and CVU uses `/usr/bin/scp` and `/usr/sbin/rcp`.

- `ORACLE_SRVM_REMOTESHELL`: If set, it specifies the location for `ssh` command to override the CVU default value. By default, this entry is commented out and the tool uses `/usr/sbin/ssh`.

- `CV_ASSUME_CL_VERSION`: By default, the command line parser uses `crs activeversion` for the display of command line syntax usage and syntax validation. Use this property to pass a version other than `crs activeversion` for command line syntax display and validation. By default, this entry is commented out.

If CVU does not find a key entry defined in the configuration file, then CVU searches for the environment variable that matches the name of the key. If the environment variable is set, then CVU uses its value, otherwise CVU uses a default value for that entity.

##### Privileges and Security

Because of a lack of user equivalence for the `root` user, most CVU commands cannot be run as `root` to perform any remote node operations, except for the following:

- `cluvfy comp dhcp`

- `cluvfy comp dns`

However, using privilege delegation, you can specify the `-method` parameter and choose one of two methods (`sudo` or `root`) to enable the checks and run the fixup scripts that require root privileges to be performed on remote nodes. You will be prompted for a password but the password is used dynamically while the CVU commands run, rather than being stored on a storage device.

Specifying the `-method` parameter is advantageous in the context of fixup scripts. If you choose privilege delegation, then all the fixup scripts can be run at one time from the local node. If you do not choose privilege delegation, then you must log onto each relevant node as `root` and run the fixup script.

##### Using CVU Help

The `cluvfy` commands have context sensitive help that shows their usage based on the command-line arguments that you enter. For example, if you enter `cluvfy`, then CVU displays high-level generic usage text describing the stage and component syntax. The following is a list of context help commands:

- `cluvfy -help`: CVU displays detailed CVU command information.

- `cluvfy -version`: CVU displays the version of Oracle Clusterware.

- `cluvfy comp -list`: CVU displays a list of components that can be checked, and brief descriptions of how the utility checks each component.

- `cluvfy comp -help`: CVU displays detailed syntax for each of the valid component checks.

- `cluvfy stage -list`: CVU displays a list of valid stages.

- `cluvfy stage -help`: CVU displays detailed syntax for each of the valid stage checks.

You can also use the `-help` option with any CVU command. For example, `cluvfy stage -pre nodeadd -help` returns detailed information for that particular command.

If you enter an invalid CVU command, then CVU shows the correct usage for that command. For example, if you type `cluvfy stage -pre dbinst`, then CVU shows the correct syntax for the precheck commands for the `dbinst` stage. Enter the `cluvfy -help` command to see detailed CVU command information.

##### Deprecated and Desupported CLUVFY Commands

The following table includes deprecated and desupported CLUVFY commands:

Table A-2 Deprecated and Desupported Cluvfy Commands

| Command           | Deprecated                           | Desupported |
|:------------------|:-------------------------------------|:------------|
| `cluvfy comp cfs` | Oracle Database 12c release 1 (12.1) | No          |

#### Special CVU Topics

This section includes the following topics:

- Generating Fixup Scripts

- Using CVU to Determine if Installation Prerequisites are Complete

- Using CVU with Oracle Database 10g Release 1 or 2

- Entry and Exit Criteria

- Verbose Mode and UNKNOWN Output

- CVU Node List Shortcuts

##### Generating Fixup Scripts

You can use the `-fixup` flag with certain CVU commands to generate [fixup script](glossary.md)s before installation. Oracle Universal Installer can also generate fixup scripts during installation. The installer then prompts you to run the script as `root` in a separate terminal session. If you generate a fixup script from the command line, then you can run it as `root` after it is generated. When you run the script, it raises kernel values to required minimums, if necessary, and completes other operating system configuration.

Alternatively, you can specify the `-method` parameter with certain CVU commands to enable privilege delegation and enable you to run fixup scripts as `root` on remote nodes from the local node.

**See Also:**

"Privileges and Security"

##### Using CVU to Determine if Installation Prerequisites are Complete

You can use CVU to determine which system prerequisites for installation are completed.

Use this option if you are installing Oracle Database software on a system with a pre-existing Oracle software installation. In using this option, note the following:

- You must run CVU as the user account you plan to use to run the installation. You cannot run CVU as `root`, and running CVU as another user other than the user who is performing the installation does not ensure the accuracy of user and group configuration for installation or other configuration checks.

- Before you can complete a clusterwide status check, SSH must be configured for all cluster nodes. You can use the installer to complete SSH configuration, or you can complete SSH configuration yourself between all nodes in the cluster. You can also use CVU to generate a fixup script to configure SSH connectivity.

- CVU can assist you by finding preinstallation steps that must be completed, but it cannot perform preinstallation tasks.

Use the following syntax to determine what preinstallation steps are completed, and what preinstallation steps you must perform; running the command with the `-fixup` flag generates a fixup script to complete kernel configuration tasks as needed:

    $ ./runcluvfy.sh stage -pre crsinst -fixup -n node_list

In the preceding syntax example, replace the `node_list` variable with the names of the nodes in your cluster, separated by commas. On Windows, you must enclose the comma-delimited node list in double quotation marks (`""`).

For example, for a cluster with mountpoint `/mnt/dvdrom/`, and with nodes `node1`, `node2`, and `node3`, enter the following command:

    $ cd /mnt/dvdrom/
    $ ./runcluvfy.sh stage -pre crsinst -fixup -n node1,node2,node3

Review the CVU report, and complete additional steps as needed.

**See Also:**

Your platform-specific installation guide for more information about installing your product

##### Using CVU with Oracle Database 10g Release 1 or 2

You can use CVU included on the Oracle Database 12c media to check system requirements for Oracle Database 10g release 1 (10.1) and later installations. To use CVU to check Oracle Clusterware installations, append the command `-r ``release_code` flag to the standard CVU system check commands.

For example, to perform a verification check before installing Oracle Clusterware version 10. 2 on a system where the media mountpoint is `/mnt/dvdrom` and the cluster nodes are `node1`, `node2`, and `node3`, enter the following command:

    $ cd /mnt/dvdrom
    $ ./runcluvfy.sh stage -pre crsinst -n node1,node2,node3 -r 10.2

**Note:**

If you do not specify a release version to check, then CVU checks for 12c release 1 (12.1) requirements.

##### Entry and Exit Criteria

When verifying stages, CVU uses entry and exit criteria. Each stage has entry criteria that define a specific set of verification tasks to be performed before initiating that stage.

This check prevents you from beginning a stage, such as installing Oracle Clusterware, unless you meet the Oracle Clusterware prerequisites for that stage.

The exit criteria for a stage define another set of verification tasks that you must perform after the completion of the stage. Post-checks ensure that the activities for that stage have been completed. Post-checks identify stage-specific problems before they propagate to subsequent stages.

##### Verbose Mode and UNKNOWN Output

By default CVU reports in nonverbose mode by only reporting the summary of a test, you can obtain detailed output by using the `-verbose` argument.

The `-verbose` argument produces detailed output of individual checks and where applicable shows results for each node in a tabular layout.

If a `cluvfy` command responds with `UNKNOWN` for a particular node, then this is because CVU cannot determine whether a check passed or failed. The cause could be a loss of reachability or the failure of user equivalence to that node. The cause could also be any system problem that was occurring on that node when CVU was performing a check.

The following is a list of possible causes for an `UNKNOWN` response:

- The node is down

- Executables that CVU requires are missing in `Grid_home``/bin` or the `Oracle home` directory

- The user account that ran CVU does not have privileges to run common operating system executables on the node

- The node is missing an operating system patch or a required package

- The node has exceeded the maximum number of processes or maximum number of open files, or there is a problem with IPC segments, such as shared memory or semaphores

##### CVU Node List Shortcuts

To obtain the CVU node list, there are several options you can use with the `cluvfy` command.

To provide CVU a list of all of the nodes of a cluster, enter `-n all`. CVU attempts to obtain the node list in the following order:

1.  If vendor clusterware is available, then CVU selects all of the configured nodes from the vendor clusterware using the `lsnodes` utility.

    **Note:**

    Starting with Oracle Database 19c, the integration of vendor clusterware with Oracle Clusterware is deprecated, and can be desupported in a future release. For this reason, Oracle recommends that you align your next software or hardware upgrade to transition off of vendor cluster solutions.

2.  If Oracle Clusterware is installed, then CVU selects all of the configured nodes from Oracle Clusterware using the `olsnodes` utility.

3.  If neither the vendor clusterware nor Oracle Clusterware is installed, then CVU searches for a value for the `CV_NODE_ALL` key in the configuration file.

4.  If vendor clusterware and Oracle Clusterware are not installed and no key named `CV_NODE_ALL` exists in the configuration file, then CVU searches for a value for the `CV_NODE_ALL` environmental variable. If you have not set this variable, then CVU reports an error.

To provide a partial node list, you can set an environmental variable and use it in the CVU command. For example, on Linux or Unix systems you can enter:

    setenv MYNODES node1,node3,node5
    cluvfy comp nodecon -n $MYNODES [-verbose]

### Cluster Verification Utility Command Reference

This section lists and describes CVU commands.

#### cluvfy comp acfs

Checks the integrity of Oracle Automatic Storage Management Cluster File System (Oracle ACFS) on the nodes in a cluster.

##### Syntax

    cluvfy comp acfs [-n node_list | -allnodes] [-f file_system] [-save [-savedir directory_path]] [-verbose]

##### Parameters

Table A-3 cluvfy comp acfs Command Parameters

| Parameter                             | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                              |
|:--------------------------------------|:-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `-n ``node_list`` | -allnodes`        | The comma-delimited list of non domain-qualified node names on which to conduct the verification, or all nodes in a cluster.<br>If you do not specify this option, then CVU checks only the local node.                                                                                                                                                                                                                                                                                  |
| `-f ``file_system`                    | The name of the file system to check.                                                                                                                                                                                                                                                                                                                                                                                                                                                    |
| `-save [-savedir ``directory_path``]` | Use the `-save` or `-save -savedir` flags to save validation reports (`cvuchecdkreport_timestamp.txt` and `cvucheckreport_timestamp.htm`), where `timestamp` is the time and date of the validation report.<br>If you use the `-save` flag by itself, then CVU saves the reports in the `CVU_home/cv/report` directory, where `CVU_home` is the location of the CVU binaries.<br>If you use the `-save -savedir` flags, then specify a directory where you want CVU to save the reports. |
| `-verbose`                            | CVU prints detailed output.                                                                                                                                                                                                                                                                                                                                                                                                                                                              |

#### cluvfy comp admprv

Checks the required administrative privileges for the operation specified by `-o` parameter on all the nodes that you specify in the node list, or all nodes in a cluster.

##### Syntax

On Linux and UNIX platforms:

    cluvfy comp admprv [-n node_list | -allnodes] {-o user_equiv [-sshonly] [-fixup] | -o crs_inst
      [-asmgrp asmadmin_group] [-asmdbagrp asmdba_group] [-asmopergrp asmoper_group] [-orainv orainventory_group]
      [-fixup] [-fixupnoexec] [-method sudo -user user_name [-location directory_path] | -method root]
      | -o db_inst [-osdba osdba_group] [-osoper osoper_group] [-fixup] [-fixupnoexec]
      [-method sudo -user user_name [-location dir_path] | -method root] | -o db_config -d oracle_home
      [-fixup] [-fixupnoexec] [-method sudo -user user_name [-location directory_path] | -method root]}
      [-verbose] [-json] [-html] [-save [-savedir directory_path]]

On Windows platforms:

    cluvfy comp admprv [-n node_list | -allnodes] {-o user_equiv [-fixup] | -o crs_inst [-orainv orainventory_group]
      [-fixup] [-fixupnoexec] | -o db_inst [-fixup] [-fixupnoexec] | -o db_config -d oracle_home [-fixup] [-fixupnoexec]}
      [-verbose] [-json] [-html] [-savedir directory_path]]

##### Parameters

Table A-4 cluvfy comp admprv Command Parameters

| Parameter                                                                  | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                              |
|:---------------------------------------------------------------------------|:-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `-n ``node_list`` | -allnodes`                                             | The comma-delimited list of non domain-qualified node names on which to conduct the verification, or all nodes in a cluster.<br>If you do not specify this option, then CVU checks only the local node.                                                                                                                                                                                                                                                                                  |
| `-o user_equiv [-sshonly]`                                                 | Checks user equivalence between the nodes. On Linux and UNIX platforms, you can optionally verify user equivalence using `ssh` by adding the `-sshonly` parameter.                                                                                                                                                                                                                                                                                                                       |
| `-o crs_inst [``option``]`                                                 | Checks administrative privileges for installing Oracle Clusterware. Optionally, you can specify the following:<br>• `-asmgrp`: Specify the name of the OSASM group. The default is `asmadmin`.<br>• `-asmdbagrp`: Specify the name of the ASMDBA group. The default is `asmdba`.<br>• `-orainv`: Specify the name of the Oracle Inventory group. The default is `oinstall`.                                                                                                              |
| `-o db_inst ``option``]`                                                   | Checks administrative privileges for installing an Oracle RAC database. Optionally, you can specify the following:<br>• `-osdba`: The name of the OSDBA group. The default is `dba`.<br>• `–osoper`: The name of the OSOPER group.                                                                                                                                                                                                                                                       |
| `-o db_config -d ``oracle_home`                                            | Checks administrative privileges for creating or configuring an Oracle RAC database. Specify the location of the Oracle home for the Oracle RAC database.                                                                                                                                                                                                                                                                                                                                |
| `-fixup`                                                                   | Specifies that if the verification fails, then CVU generates fixup instructions, if feasible.                                                                                                                                                                                                                                                                                                                                                                                            |
| `-fixupnoexec`                                                             | Specifies that if verification fails, then CVU generates the fixup data and displays the instructions for manual execution of the generated fixups.                                                                                                                                                                                                                                                                                                                                      |
| `-method sudo -user ``user_name`` [-location ``dir_path``] | -method root` | Specify whether the privilege delegation method is `sudo` or `root`, for root user access. If you specify `sudo`, then you must specify the user name to access all the nodes with root privileges and, optionally, provide the full file system path for the `sudo` executable.                                                                                                                                                                                                         |
| `-save [-savedir ``directory_path``]`                                      | Use the `-save` or `-save -savedir` flags to save validation reports (`cvuchecdkreport_timestamp.txt` and `cvucheckreport_timestamp.htm`), where `timestamp` is the time and date of the validation report.<br>If you use the `-save` flag by itself, then CVU saves the reports in the `CVU_home/cv/report` directory, where `CVU_home` is the location of the CVU binaries.<br>If you use the `-save -savedir` flags, then specify a directory where you want CVU to save the reports. |
| `–verbose`                                                                 | CVU prints detailed output.                                                                                                                                                                                                                                                                                                                                                                                                                                                              |

##### Usage Notes

- The operations following the `-o` parameter are mutually exclusive and you can specify only one operation at a time.

- By default, the equivalence check does not verify X-Windows configurations, such as whether you have disabled X-forwarding, whether you have the proper setting for the `DISPLAY` environment variable, and so on.

  To verify X-Windows aspects during user equivalence checks, set the `CV_XCHK_FOR_SSH_ENABLED` key to `TRUE` in the configuration file that resides in the `CV_HOME/cv/admin/cvu_config` directory before you run the `cluvfy comp admprv -o user_equiv` command.

##### Examples

You can verify that the permissions required for installing Oracle Clusterware have been configured on the nodes `racnode1` and `racnode2` by running the following command:

    $ cluvfy comp admprv -n racnode1,racnode2 -o crs_inst -verbose

You can verify that the permissions required for creating or modifying an Oracle RAC database using the `C:\app\oracle\product\19.0.0\dbhome_1` Oracle home directory, and generate a script to configure the permissions by running the following command:

    cluvfy comp admprv -n racnode1,racnode2 -o db_config -d C:\app\oracle\product\19.0.0\dbhome_1 -fixup -verbose

#### cluvfy comp asm

Checks the integrity of Oracle Automatic Storage Management (Oracle ASM) on specific nodes in the cluster.

This check ensures that the Oracle ASM instances on the specified nodes are running from the same Oracle home and that `asmlib`, if it exists, has a valid version and ownership.

##### Syntax

    cluvfy comp asm [-n node_list | -allnodes] [-verbose] [-json]
        [-html] [-save [-savedir directory_path]] [-verbose]

##### Parameters

Table A-5 cluvfy comp asm Command Parameters

| Parameter                             | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                              |
|:--------------------------------------|:-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `-n ``node_list`` | -allnodes`        | The comma-delimited list of non domain-qualified node names on which to conduct the verification, or all nodes in a cluster.<br>If you do not specify this option, then CVU checks only the local node.                                                                                                                                                                                                                                                                                  |
| `-json`                               | Use the `-json` flag to generate a detailed report in JSON format.<br>If you do not specify the `-json` flag, then CVU generates the detailed report in a text file.                                                                                                                                                                                                                                                                                                                     |
| `-html`                               | Use the `-html` flag to generate a detailed report in HTML format.<br>If you specify the `-html` flag, and a browser that CVU recognizes is available on the system, then CVU starts the browser and displays the report on the browser when the checks are complete.<br>If you do not specify the `-html` flag, then CVU generates the detailed report in a text file.                                                                                                                  |
| `-save [-savedir ``directory_path``]` | Use the `-save` or `-save -savedir` flags to save validation reports (`cvuchecdkreport_timestamp.txt` and `cvucheckreport_timestamp.htm`), where `timestamp` is the time and date of the validation report.<br>If you use the `-save` flag by itself, then CVU saves the reports in the `CVU_home/cv/report` directory, where `CVU_home` is the location of the CVU binaries.<br>If you use the `-save -savedir` flags, then specify a directory where you want CVU to save the reports. |
| `-verbose`                            | CVU prints detailed output.                                                                                                                                                                                                                                                                                                                                                                                                                                                              |

##### Examples

This command produces output similar to the following:

    $ cluvfy comp asm –n all

    Verifying ASM Integrity

    Task ASM Integrity check started...

    Starting check to see if ASM is running on all cluster nodes...

    ASM Running check passed. ASM is running on all specified nodes

    Starting Disk Groups check to see if at least one Disk Group configured...
    Disk Group Check passed. At least one Disk Group configured

    Task ASM Integrity check passed...

    Verification of ASM Integrity was successful.

#### cluvfy comp baseline

Captures system and cluster configuration information to create a baseline.

You can use this baseline for comparison with the state of the system. You can collect baselines at strategic times, such as after Oracle Clusterware installation, before and after upgrading Oracle Clusterware, or automatically as part of periodic execution of CVU running as an Oracle Clusterware resource. You can also compare several baselines.

##### Syntax

    cluvfy comp baseline -collect {all | cluster | database | asm} [-n node_list | -allnodes]
       [-d Oracle_home | -db db_unique_name] [-bestpractice | -mandatory] [-binlibfilesonly]
       [-reportname report_name] [-savedir save_dir]
       [-method sudo -user user_name [-location directory_path] | -method root]
       [-orachk_loc location] [-skip check_utilities]

    cluvfy comp baseline -compare baseline1,baseline2,... [-cross_compare] [-deviations] [-savedir save_dir]

##### Parameters

Table A-6 cluvfy comp baseline Command Parameters

| Parameter                                                          | Description                                                                                                                                                                                                                                                                                                                                                         |
|:-------------------------------------------------------------------|:--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `-collect {all | cluster | database | asm}`                        | The `-collect` parameter instructs CVU to create a baseline and save it in the `Grid_home``/cv/report/xml` directory.<br>You can collect a baseline related to Oracle Clusterware (`cluster`), the database (`database`), Oracle ASM, or all three (`all`).                                                                                                         |
| `-n ``node_list`` | -allnodes`                                     | Specify a comma-delimited list of non domain-qualified node names, or all nodes in a cluster, on which the test should be conducted.                                                                                                                                                                                                                                |
| `-d ``Oracle_home`                                                 | When collecting a database baseline, if you specify an Oracle home, then CVU collects baselines for all the databases running from the Oracle home.<br>Use the `-db` parameter to collect a baseline for a specific database.                                                                                                                                       |
| `-db ``db_unique_name`                                             | The name of the database for which you want to collect information.<br>When collecting a database baseline, if you specify the `-db` parameter, then CVU only collects the baseline for the specified database. If you do not specify `-db`, then CVU discovers all of the cluster databases configured in the system and the collects baselines for each of those. |
| `-bestpractice | -mandatory`                                       | Specify `-bestpractice` to collect a baseline for only best practice recommendations. Specify `-mandatory` to collect a baseline for only mandatory requirements.                                                                                                                                                                                                   |
| `-binlibfilesonly`                                                 | Specify `-binlibfilesonly` to collect only files in the `bin/`, `lib/`, and `jlib/` subdirectories of the software home.                                                                                                                                                                                                                                            |
| `-report ``report_name`                                            | Use this optional parameter to specify a name for the report.                                                                                                                                                                                                                                                                                                       |
| `-savedir ``save_dir`                                              | Use this optional parameter to specify a location in which CVU saves the reports. If you do not specify the `-savedir` option, then CVU saves the reports in the `Grid_home``/cv/report` directory.                                                                                                                                                                 |
| `-method sudo -user user_name [-location dir_path] | -method root` | Specify whether the privilege delegation method is `sudo` or `root`, for root user access. If you specify `sudo`, then you must specify the user name to access all the nodes with root privileges and, optionally, provide the full file system path for the `sudo` executable.                                                                                    |
| `-compare ``baseline1``,``baseline2``,...`                         | Specify `-compare` to compare baselines. If you specify only one baseline, then CVU displays the results of the collections. If you specify multiple baselines in a comma-delimited list, then CVU compares the values from the baselines against each other in an HTML document.                                                                                   |
| `-cross_compare`                                                   | Specify `-cross_compare` to compare baselines across clusters or across cluster nodes and databases.                                                                                                                                                                                                                                                                |
| `-deviations`                                                      | Optionally, you can specify this parameter to display only the deviations from best practice recommendations or mandatory requirements, or both, (depending on whether you specified the `-bestpractice` and `-mandatory` parameters).                                                                                                                              |

##### Usage Notes

- You must specify either the `-collect` or `-compare` parameter.

- Items that CVU collects when running this command include:

  - Physical memory
  - Available memory
  - Swap space
  - Free space
  - Required packages
  - Recommended kernel parameters
  - `/etc/inittab` permissions
  - Domain sockets under `/var/tmp/.oracle`
  - Oracle Clusterware software file attributes
  - Network MTU size
  - OCR permissions, group, and owner (if OCR is stored on a shared file system)
  - OCR disk group (if OCR is stored on Oracle ASM
  - System requirement pluggable tasks (Zeroconf settings, `/boot` mount, Huge Pages existence, 8888 port availability, Ethernet jumbo frames)
  - Oracle Clusterware post-check pluggable tasks (`css miscount`, `reboottime`, `disktimeout`)<sup>Foot 1</sup>
  - Database best practices

##### Examples

The following examples illustrate usage for both `-collect` and `-compare` command parameters:

    $ cluvfy comp baseline -collect all -n allnodes -db orcl -bestpractice -report bl1
       -savedir /tmp

    $ cluvfy comp baseline -compare bl1,bl2

#### cluvfy comp clocksync

Checks clock synchronization across all the nodes in the node list.

**Note:**

Cluster Time Synchronization Service (CTSS) is deprecated in Oracle Database 19c. 

CVU verifies a time synchronization service is running (Oracle Cluster Time Synchronization Service (CTSS) or Network Time Protocol (NTP)), that each node is using the same reference server for clock synchronization, and that the time offset for each node is within permissible limits.

##### Syntax

    cluvfy comp clocksync [-noctss] [-n node_list | -allnodes] [-save [-savedir directory_path]] [-verbose]

##### Parameters

Table A-7 cluvfy comp clocksync Command Parameters

| Parameter                             | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                              |
|:--------------------------------------|:-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `-noctss`                             | If you specify this parameter, then CVU does not perform a check on CTSS. Instead, CVU checks the platform's native time synchronization service, such as NTP.                                                                                                                                                                                                                                                                                                                           |
| `-n ``node_list`` | -allnodes`        | The comma-delimited list of non domain-qualified node names on which to conduct the verification, or all nodes in a cluster.<br>If you do not specify this option, then CVU checks only the local node.                                                                                                                                                                                                                                                                                  |
| `-save [-savedir ``directory_path``]` | Use the `-save` or `-save -savedir` flags to save validation reports (`cvuchecdkreport_timestamp.txt` and `cvucheckreport_timestamp.htm`), where `timestamp` is the time and date of the validation report.<br>If you use the `-save` flag by itself, then CVU saves the reports in the `CVU_home/cv/report` directory, where `CVU_home` is the location of the CVU binaries.<br>If you use the `-save -savedir` flags, then specify a directory where you want CVU to save the reports. |
| `-verbose`                            | CVU prints detailed output.                                                                                                                                                                                                                                                                                                                                                                                                                                                              |

#### cluvfy comp clu

Checks the integrity of the cluster on all nodes.

##### Syntax

    cluvfy comp clu [-verbose] [-json] [-html] [-save [-savedir directory_path]]

##### Parameters

Table A-8 cluvfy comp clu Command Parameters

| Parameter                             | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                              |
|:--------------------------------------|:-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `–verbose`                            | CVU prints detailed output.                                                                                                                                                                                                                                                                                                                                                                                                                                                              |
| `-json`                               | Use the `-json` flag to generate a detailed report in JSON format.<br>If you do not specify the `-json` flag, then CVU generates the detailed report in a text file.                                                                                                                                                                                                                                                                                                                     |
| `-html`                               | Use the `-html` flag to generate a detailed report in HTML format.<br>If you specify the `-html` flag, and a browser that CVU recognizes is available on the system, then CVU starts the browser and displays the report on the browser when the checks are complete.<br>If you do not specify the `-html` flag, then CVU generates the detailed report in a text file.                                                                                                                  |
| `-save [-savedir ``directory_path``]` | Use the `-save` or `-save -savedir` flags to save validation reports (`cvuchecdkreport_timestamp.txt` and `cvucheckreport_timestamp.htm`), where `timestamp` is the time and date of the validation report.<br>If you use the `-save` flag by itself, then CVU saves the reports in the `CVU_home/cv/report` directory, where `CVU_home` is the location of the CVU binaries.<br>If you use the `-save -savedir` flags, then specify a directory where you want CVU to save the reports. |

##### Usage Notes

**Note:**

The command has been deprecated and may be desupported in a future release.

You can also choose to print detailed output.

**See Also:**

CVU Usage Information for CVU operational notes including information about report options

#### cluvfy comp clumgr

Checks the integrity of the cluster manager subcomponent, or Oracle Cluster Synchronization Services (CSS), on the nodes in the node list.

##### Syntax

    cluvfy comp clumgr [-n node_list | -allnodes] [-save [-savedir directory_path]] [-verbose]

##### Parameters

Table A-9 cluvfy comp clumgr Command Parameters

| Parameter                             | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                              |
|:--------------------------------------|:-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `-n ``node_list`` | -allnodes`        | The comma-delimited list of non domain-qualified node names on which to conduct the verification, or all nodes in a cluster.<br>If you do not specify this option, then CVU checks only the local node.                                                                                                                                                                                                                                                                                  |
| `-save [-savedir ``directory_path``]` | Use the `-save` or `-save -savedir` flags to save validation reports (`cvuchecdkreport_timestamp.txt` and `cvucheckreport_timestamp.htm`), where `timestamp` is the time and date of the validation report.<br>If you use the `-save` flag by itself, then CVU saves the reports in the `CVU_home/cv/report` directory, where `CVU_home` is the location of the CVU binaries.<br>If you use the `-save -savedir` flags, then specify a directory where you want CVU to save the reports. |
| `-verbose`                            | CVU prints detailed output.                                                                                                                                                                                                                                                                                                                                                                                                                                                              |

#### cluvfy comp containerhost

Performs system requirement checks for container host and reports issues that may prevent successful creation of containers for hosting Oracle Clusterware and Database.

##### Syntax

    cluvfy comp containerhost [-type {docker|k8|podman}] [-fixup] [-fixupnoexec] [-method sudo -user user_name
    [-location directory_path] | -method root] [-verbose] [-json] [-html] [-save [-savedir directory_path]]

##### Parameters

Table A-10 cluvfy comp containerhost Command Parameters

| Parameter                                                                  | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                              |
|:---------------------------------------------------------------------------|:-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `-type {docker|k8|podman}`                                                 | Specify type of the container manager configured on the host.                                                                                                                                                                                                                                                                                                                                                                                                                            |
| `-fixup`                                                                   | Specifies that if the verification fails, then CVU generates fixup instructions, if feasible.                                                                                                                                                                                                                                                                                                                                                                                            |
| `-fixupnoexec`                                                             | Specifies that if verification fails, then CVU generates the fixup data and displays the instructions for manual execution of the generated fixups.                                                                                                                                                                                                                                                                                                                                      |
| `-method sudo -user ``user_name`` [-location ``dir_path``] | -method root` | Specify whether the privilege delegation method is `sudo` or `root`, for root user access. If you specify `sudo`, then you must specify the user name to access all the nodes with root privileges and, optionally, provide the full file system path for the `sudo` executable.                                                                                                                                                                                                         |
| `-verbose`                                                                 | CVU prints detailed output.                                                                                                                                                                                                                                                                                                                                                                                                                                                              |
| `-json`                                                                    | Use the `-json` flag to generate a detailed report in JSON format.<br>If you do not specify the `-json` flag, then CVU generates the detailed report in a text file.                                                                                                                                                                                                                                                                                                                     |
| `-html`                                                                    | Use the `-html` flag to generate a detailed report in HTML format.<br>If you specify the `-html` flag, and a browser that CVU recognizes is available on the system, then CVU starts the browser and displays the report on the browser when the checks are complete.<br>If you do not specify the `-html` flag, then CVU generates the detailed report in a text file.                                                                                                                  |
| `-save [-savedir ``directory_path``]`                                      | Use the `-save` or `-save -savedir` flags to save validation reports (`cvuchecdkreport_timestamp.txt` and `cvucheckreport_timestamp.htm`), where `timestamp` is the time and date of the validation report.<br>If you use the `-save` flag by itself, then CVU saves the reports in the `CVU_home/cv/report` directory, where `CVU_home` is the location of the CVU binaries.<br>If you use the `-save -savedir` flags, then specify a directory where you want CVU to save the reports. |

#### cluvfy comp crs

Checks the integrity of the Cluster Ready Services (CRS) daemon on the specified nodes.

##### Syntax

    cluvfy comp crs [-n node_list | -allnodes] [-json] [-html] [-save [-savedir [-savedir directory_path]]

##### Parameters

Table A-11 cluvfy comp clumgr Command Parameters

| Parameter                             | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                              |
|:--------------------------------------|:-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `-n ``node_list`` | -allnodes`        | The comma-delimited list of non domain-qualified node names on which to conduct the verification, or all nodes in a cluster.<br>If you do not specify this option, then CVU checks only the local node.                                                                                                                                                                                                                                                                                  |
| `-json`                               | Use the `-json` flag to generate a detailed report in JSON format.<br>If you do not specify the `-json` flag, then CVU generates the detailed report in a text file.                                                                                                                                                                                                                                                                                                                     |
| `-html`                               | Use the `-html` flag to generate a detailed report in HTML format.<br>If you specify the `-html` flag, and a browser that CVU recognizes is available on the system, then CVU starts the browser and displays the report on the browser when the checks are complete.<br>If you do not specify the `-html` flag, then CVU generates the detailed report in a text file.                                                                                                                  |
| `-save [-savedir ``directory_path``]` | Use the `-save` or `-save -savedir` flags to save validation reports (`cvuchecdkreport_timestamp.txt` and `cvucheckreport_timestamp.htm`), where `timestamp` is the time and date of the validation report.<br>If you use the `-save` flag by itself, then CVU saves the reports in the `CVU_home/cv/report` directory, where `CVU_home` is the location of the CVU binaries.<br>If you use the `-save -savedir` flags, then specify a directory where you want CVU to save the reports. |

**See Also:**

CVU Usage Information for CVU operational notes including information about report options

#### cluvfy comp dhcp

Verifies that the DHCP server exists on the network, and that it can provide a required number of IP addresses.

The required number of IP addresses is calculated, as follows:

- Regardless of the size of the cluster, there must be three scan VIPs

- One node VIP for each node you specify with the `-n` option

- One application VIP for each application VIP resource you specify with the `-vipresname` option

This verification also verifies the response time for the DHCP server.

##### Syntax

    cluvfy comp dhcp -clustername cluster_name [-vipresname application_vip_resource_name]
      [-port dhcp_port] [-n node_list | -allnodes] [-method sudo -user user_name [-location directory_path] | -method root]
      [-networks network_list] [-save [-savedir directory_path]] [-verbose]

##### Parameters

Table A-12 cluvfy comp dhcp Command Parameters

| Parameter                                                                        | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      |
|:---------------------------------------------------------------------------------|:---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `-clustername ``cluster_name`                                                    | You must specify the name of the cluster of which you want to check the integrity of DHCP.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       |
| `-vipresname ``application_vip_resource_name`                                    | Optionally, you can specify a comma-delimited list of the names of the application VIP resource.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 |
| `-port ``dhcp_port`                                                              | Optionally, you can specify the port to which DHCP packages are sent. The default port is 67.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    |
| `-n ``node_list`` | -allnodes`                                                   | Optionally, you can specify a comma-delimited list of non domain-qualified node names, or all nodes in a cluster, on which to conduct the verification.<br>If you do not specify this parameter, then CVU checks only the local node.                                                                                                                                                                                                                                                                                                                                                                                            |
| `-method sudo -user ``user_name`` [-location ``directory_path``] | -method root` | Optionally, you can specify whether the privilege delegation method is `sudo` or `root`, for root user access. If you specify `sudo`, then you must specify the user name to access all the nodes with root privileges and, optionally, provide the full file system path for the `sudo` executable.                                                                                                                                                                                                                                                                                                                             |
| `-networks ``network_list`                                                       | Optionally, you can specify a list of network classifications for the cluster separated by forward slashes (`/`) that you want CVU to check, where each network is in the form of `"``if_name``"[:``subnet_id``[:``if_type``[,``if_type``...]]]`.<br>In the preceding format, you must enclose `if_name` in double quotation marks (`""`), and you can use regular expressions, such as "`.*`", as in `"eth*"`, to match interfaces like `eth1` and `eth02`. The `subnet_id` is the subnet number of the network interface. The `if_type` is a comma-separated list of interface types: `{CLUSTER_INTERCONNECT | PUBLIC | ASM}`. |
| `-save [-savedir ``directory_path``]`                                            | Use the `-save` or `-save -savedir` flags to save validation reports (`cvuchecdkreport_timestamp.txt` and `cvucheckreport_timestamp.htm`), where `timestamp` is the time and date of the validation report.<br>If you use the `-save` flag by itself, then CVU saves the reports in the `CVU_home/cv/report` directory, where `CVU_home` is the location of the CVU binaries.<br>If you use the `-save -savedir` flags, then specify a directory where you want CVU to save the reports.                                                                                                                                         |
| `-verbose`                                                                       | CVU prints detailed output.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      |

##### Usage Notes

- You must run this command as `root`.

- Do not run this check while the default network Oracle Clusterware resource, configured to use a DHCP-provided IP address, is online (because the VIPs get released and, since the cluster is online, DHCP has provided IP, so there is no need to double the load on the DHCP server).

- Run this check on the local node. This is unlike other CVU commands, which run on all nodes specified in node list. As a result, even though the local node is not included in the node list you specify with the `-n` option, the error messages get reported to the local node.

- Before running this command, ensure that the network resource is offline. Use the `srvctl stop nodeapps` command to bring the network resource offline, if necessary.

  **See Also:**

  [Oracle Real Application Clusters Administration and Deployment Guide](../racad/server-control-utility-reference.md) for more information about the `srvctl stop nodeapps` command

#### cluvfy comp dns

Verifies that the Grid Naming Service (GNS) subdomain delegation has been properly set up in the Domain Name Service (DNS) server.

##### Syntax

    cluvfy comp dns -server -domain gns_sub_domain -vipaddress gns_vip_address [-port dns_port]
      [-method sudo -user user_name [-location directory_path] | -method root] [-save [-savedir directory_path]] [-verbose]

    cluvfy comp dns -client -domain gns_sub_domain -vip gns_vip [-port dns_port]
      [-last] [-method sudo -user user_name [-location directory_path] | -method root] [-n node_list|-allnodes]
      [-save [-savedir directory_path]] [-verbose]

##### Parameters

Table A-13 cluvfy comp dns Command Parameters

| Parameter                                                                        | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                              |
|:---------------------------------------------------------------------------------|:-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `-server`                                                                        | Start a test DNS server for the GNS subdomain that listens on the domain specified by the `-domain` option.                                                                                                                                                                                                                                                                                                                                                                              |
| `-client`                                                                        | Validate connectivity to a test DNS server started on a specific address. You must specify the same information you specified when you started the DNS server.                                                                                                                                                                                                                                                                                                                           |
| `-domain ``gns_sub_domain`                                                       | Specify the name of the GNS subdomain.                                                                                                                                                                                                                                                                                                                                                                                                                                                   |
| `-vipaddress ``gns_vip_address`                                                  | Specify the GNS virtual IP address in the form `{``ip_name`` | ``ip_address``}/``net_mask``/``interface_name`. You can specify either `ip_name`, which is a name that resolves to an IP address, or `IP_address`, which is an IP address. Either name or address is followed by `net_mask`, which is the subnet mask for the IP address, and `interface_name`, which is the interface on which to start the IP address.                                                                  |
| `-vip ``gns_vip`                                                                 | Specify a GNS virtual IP address, which is either a name that resolves to an IP address or a dotted decimal numeric IP address.                                                                                                                                                                                                                                                                                                                                                          |
| `-port ``dns_port`                                                               | Specify the port on which the test DNS server listens. The default port is 53.                                                                                                                                                                                                                                                                                                                                                                                                           |
| `–last`                                                                          | Optionally, you can use this parameter to send a termination request to the test DNS server after all the validations are complete.                                                                                                                                                                                                                                                                                                                                                      |
| `-method sudo -user ``user_name`` [-location ``directory_path``] | -method root` | Optionally, you can specify whether the privilege delegation method is `sudo` or `root`, for root user access. If you specify `sudo`, then you must specify the user name to access all the nodes with root privileges and, optionally, provide the full file system path for the `sudo` executable.                                                                                                                                                                                     |
| `-n ``node_list`` | -allnodes`                                                   | The comma-delimited list of non domain-qualified node names on which to conduct the verification, or all nodes in a cluster.<br>If you do not specify this option, then CVU checks only the local node.                                                                                                                                                                                                                                                                                  |
| `-save [-savedir ``directory_path``]`                                            | Use the `-save` or `-save -savedir` flags to save validation reports (`cvuchecdkreport_timestamp.txt` and `cvucheckreport_timestamp.htm`), where `timestamp` is the time and date of the validation report.<br>If you use the `-save` flag by itself, then CVU saves the reports in the `CVU_home/cv/report` directory, where `CVU_home` is the location of the CVU binaries.<br>If you use the `-save -savedir` flags, then specify a directory where you want CVU to save the reports. |
| `-verbose`                                                                       | CVU prints detailed output.                                                                                                                                                                                                                                                                                                                                                                                                                                                              |

##### Usage Notes

- You must run this command as `root`.

- Run `cluvfy comp dns -server` on one node of the cluster.

- On the last node, specify the `-last` option to terminate the `cluvfy comp dns -server` instance.

- Run `cluvfy comp dns -client` on the specified nodes, or all nodes of the cluster, to verify DNS server setup for the cluster.

- Do not run this command while the GNS resource is online.

- Oracle does not support this command on Windows.

#### cluvfy comp freespace

Checks the free space available in the Oracle Clusterware home storage and ensure that there is at least 5% of the total space available.

For example, if the total storage is 10GB, then the check ensures that at least 500MB of it is free.

##### Syntax

    cluvfy comp freespace [-n node_list | -allnodes]

If you choose to include the `-n` option, then enter a comma-delimited list of node names, or all nodes in a cluster, on which to run the command.

#### cluvfy comp gns

Verifies the integrity of the Grid Naming Service (GNS) on the cluster.

##### Syntax

    cluvfy comp gns -precrsinst {-vip gns_vip [-domain gns_domain] | -clientdata file_name}
      [-networks network_list] [-n node_list | -allnodes] [-verbose]
      cluvfy comp gns -postcrsinst [-save [-savedir directory_path]] [-verbose]

##### Parameters

Table A-14 cluvfy comp gns Command Parameters

| Parameter                             | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      |
|:--------------------------------------|:-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `-precrsinst`                         | Use this parameter to perform checks on the GNS domain name and VIP address before Oracle Clusterware is installed.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              |
| `-vip ``gns_vip`                      | Specify the GNS virtual IP address. When you specify `-vip` and `-domain` together, CVU validates that this cluster can become a GNS server (local GNS).                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         |
| `-domain ``gns_domain`                | Optionally, you can specify the GNS subdomain name.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              |
| `-clientdata ``file_name`             | Specify the name of the file that contains the GNS credentials. CVU validates that this cluster can use the specified client data to become a client GNS cluster of another GNS server cluster (shared GNS).                                                                                                                                                                                                                                                                                                                                                                                                                                     |
| `-networks ``network_list`            | Specify a list of network classifications for the cluster, including public networks for GNS, separated by forward slashes (`/`) that you want CVU to check, where each network is in the form of `"``if_name``"[:``subnet_id``[:``if_type``[,``if_type``...]]]`.<br>In the preceding format, you must enclose `if_name` in double quotation marks (`""`), and you can use regular expressions, such as "`.*`", as in `"eth*"`, to match interfaces like `eth1` and `eth02`. The `subnet_id` is the subnet number of the network interface. The `if_type` is a comma-separated list of interface types: `{CLUSTER_INTERCONNECT | PUBLIC | ASM}`. |
| `-n ``node_list`` | -allnodes`        | The comma-delimited list of non domain-qualified node names on which to conduct the verification, or all nodes in a cluster.<br>If you do not specify this option, then CVU checks only the local node.                                                                                                                                                                                                                                                                                                                                                                                                                                          |
| `-postcrsinst`                        | Use this parameter to check the integrity of GNS on all nodes in the cluster.<br>If you use this parameter, then you can use no other parameters with the exception of `-verbose`.                                                                                                                                                                                                                                                                                                                                                                                                                                                               |
| `-save [-savedir ``directory_path``]` | Use the `-save` or `-save -savedir` flags to save validation reports (`cvuchecdkreport_timestamp.txt` and `cvucheckreport_timestamp.htm`), where `timestamp` is the time and date of the validation report.<br>If you use the `-save` flag by itself, then CVU saves the reports in the `CVU_home/cv/report` directory, where `CVU_home` is the location of the CVU binaries.<br>If you use the `-save -savedir` flags, then specify a directory where you want CVU to save the reports.                                                                                                                                                         |
| `–verbose`                            | CVU prints detailed output.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      |

#### cluvfy comp gpnp

Checks the integrity of Grid Plug and Play on a list of nodes in a cluster.

##### Syntax

    cluvfy comp gpnp [-n node_list | -allnodes] [-save [-savedir directory_path]] [-verbose]

##### Parameters

Table A-15 cluvfy comp gpnp Command Parameters

| Parameter                             | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                              |
|:--------------------------------------|:-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `-n ``node_list`` | -allnodes`        | The comma-delimited list of non domain-qualified node names on which to conduct the verification, or all nodes in a cluster.<br>If you do not specify this option, then CVU checks only the local node.                                                                                                                                                                                                                                                                                  |
| `-save [-savedir ``directory_path``]` | Use the `-save` or `-save -savedir` flags to save validation reports (`cvuchecdkreport_timestamp.txt` and `cvucheckreport_timestamp.htm`), where `timestamp` is the time and date of the validation report.<br>If you use the `-save` flag by itself, then CVU saves the reports in the `CVU_home/cv/report` directory, where `CVU_home` is the location of the CVU binaries.<br>If you use the `-save -savedir` flags, then specify a directory where you want CVU to save the reports. |
| `-verbose`                            | CVU prints detailed output.                                                                                                                                                                                                                                                                                                                                                                                                                                                              |

#### cluvfy comp ha

Checks the integrity of Oracle Restart on the local node.

##### Syntax

    cluvfy comp ha [-save [-savedir directory_path]] [-verbose]

Use the `-save` or `-save -savedir` flags to save validation reports (`cvuchecdkreport_timestamp.txt` and `cvucheckreport_timestamp.htm`), where `timestamp` is the time and date of the validation report. If you use the `-save` flag by itself, then CVU saves the reports in the `CVU_home/cv/report` directory, where `CVU_home` is the location of the CVU binaries. If you use the `-save -savedir` flags, then specify a directory where you want CVU to save the reports. If you include the `-verbose` option, then CVU prints detailed output.

#### cluvfy comp healthcheck

Checks your Oracle Clusterware and Oracle Database installations for their compliance with mandatory requirements and best practices guidelines, and to ensure that they are functioning properly.

##### Syntax

    cluvfy comp healthcheck [-collect {cluster|database|asm}] [-db db_unique_name]
       [-bestpractice|-mandatory] [-deviations] [-json] [-html] [-save [-savedir directory_path]]
       [-orachk_loc location] [-skip check_utilities]

##### Parameters

Table A-16 cluvfy comp healthcheck Command Parameters

| Parameter                                  | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                        |
|:-------------------------------------------|:---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `-collect {cluster|database|asm}`          | Use `-collect` to specify that you want to perform checks for Oracle Clusterware (`cluster`), Oracle Database (`database`), or Oracle ASM. If you do not use the `-collect` flag with the `healthcheck` option, then CVU performs checks for all three.                                                                                                                                                                                                                                            |
| `-db ``db_unique_name`                     | Use `-db` to specify checks on the specific database that you enter after the `-db` flag. If you use the `-db` flag but do not provide a database unique name, then CVU reports error.<br>CVU uses JDBC to connect to the database as the user `dbsnmp` to verify various database parameters.                                                                                                                                                                                                     |
| `[-bestpractice|-mandatory] [-deviations]` | Use the `-bestpractice` flag to specify best practice checks, and the `-mandatory` flag to specify mandatory checks. Add the `-deviations` flag to specify that you want to see only the deviations from either the best practice recommendations or the mandatory requirements. You can specify either the `-bestpractice` or `-mandatory` flag, but not both flags. If you specify neither `-bestpractice` nor `-mandatory`, then CVU displays both best practices and mandatory requirements.   |
| `-html`                                    | Use the `-html` flag to generate a detailed report in HTML format.<br>If you specify the `-html` flag, and a browser CVU recognizes is available on the system, then CVU starts the browser and displays the report on the browser when the checks are complete.<br>If you do not specify the `-html` flag, then CVU generates the detailed report in a text file.                                                                                                                                 |
| `-save [-savedir ``directory_path``]`      | Use the `-save` or `-save -savedir` flags to save validation reports (`cvuchecdkreport_``timestamp``.txt` and `cvucheckreport_``timestamp``.htm`), where `timestamp` is the time and date of the validation report.<br>If you use the `-save` flag by itself, then CVU saves the reports in the `CVU_home``/cv/report` directory, where `CVU_home` is the location of the CVU binaries.<br>If you use the `-save -savedir` flags, then specify a directory where you want CVU to save the reports. |
| `-orachk_loc ``location`                   | Specify location of the ORAchk binaries.                                                                                                                                                                                                                                                                                                                                                                                                                                                           |

#### cluvfy comp nodeapp

Checks for the existence of node applications, namely VIP, NETWORK, and ONS, on all of the specified nodes.

##### Syntax

    cluvfy comp nodeapp [-n node_list | -allnodes] [-save [-savedir directory_path]] [-verbose]

##### Parameters

Table A-17 cluvfy comp nodeapp Command Parameters

| Parameter                             | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                              |
|:--------------------------------------|:-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `-n ``node_list`` | -allnodes`        | The comma-delimited list of non domain-qualified node names on which to conduct the verification, or all nodes in a cluster.<br>If you do not specify this option, then CVU checks only the local node.                                                                                                                                                                                                                                                                                  |
| `-save [-savedir ``directory_path``]` | Use the `-save` or `-save -savedir` flags to save validation reports (`cvuchecdkreport_timestamp.txt` and `cvucheckreport_timestamp.htm`), where `timestamp` is the time and date of the validation report.<br>If you use the `-save` flag by itself, then CVU saves the reports in the `CVU_home/cv/report` directory, where `CVU_home` is the location of the CVU binaries.<br>If you use the `-save -savedir` flags, then specify a directory where you want CVU to save the reports. |
| `-verbose`                            | CVU prints detailed output.                                                                                                                                                                                                                                                                                                                                                                                                                                                              |

#### cluvfy comp nodecon

Checks the connectivity among the nodes specified in the node list. If you provide an interface list, then CVU checks the connectivity using only the specified interfaces.

##### Syntax

    cluvfy comp nodecon [-n node_list | -allnodes] [-networks network_list] [-save [-savedir directory_path]] [-verbose]

##### Parameters

Table A-18 cluvfy comp nodecon Command Parameters

| Parameter                             | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                              |
|:--------------------------------------|:-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `-n ``node_list`` | -allnodes`        | Specify a comma-delimited list of non domain-qualified node names on which to conduct the verification, or all nodes in a cluster.<br>If you do not specify this option, then CVU checks only the local node.                                                                                                                                                                                                                                                                            |
| `-networks ``network_list`            | Specify a forward slash (/)-delimited list of networks on which to conduct the verification.                                                                                                                                                                                                                                                                                                                                                                                             |
| `-save [-savedir ``directory_path``]` | Use the `-save` or `-save -savedir` flags to save validation reports (`cvuchecdkreport_timestamp.txt` and `cvucheckreport_timestamp.htm`), where `timestamp` is the time and date of the validation report.<br>If you use the `-save` flag by itself, then CVU saves the reports in the `CVU_home/cv/report` directory, where `CVU_home` is the location of the CVU binaries.<br>If you use the `-save -savedir` flags, then specify a directory where you want CVU to save the reports. |
| `–verbose`                            | CVU prints detailed output.                                                                                                                                                                                                                                                                                                                                                                                                                                                              |

##### Usage Notes

- You can run this command in verbose mode to identify the mappings between the interfaces, IP addresses, and subnets.

- On Solaris platforms, this command skips testing IP addresses that are marked as deprecated.

- Use the `nodecon` command without the `-networks` parameter and with `-n` set to `all` to use CVU to:

  - Discover all of the network interfaces that are available on the cluster nodes

  - Review the interfaces' corresponding IP addresses and subnets

  - Obtain the list of interfaces that are suitable for use as VIPs and the list of interfaces to private interconnects

  - Verify the connectivity between all of the nodes through those interfaces

##### Examples

Example A-1 Verifying the connectivity between nodes through specific network interfaces

To verify the connectivity between the nodes `node1` and `node3` through interface `eth0`:

    cluvfy comp nodecon -n node1/node3 –networks eth0 -verbose

Example A-2 Discovering all available network interfaces and verifying the connectivity between the nodes in the cluster through those network interfaces

Use the following command to discover all of the network interfaces that are available on the cluster nodes. CVU then reviews the interfaces' corresponding IP addresses and subnets. Using this information, CVU obtains a list of interfaces that are suitable for use as VIPs and a list of interfaces to private interconnects. Finally, CVU verifies the connectivity between all of the nodes in the cluster through those interfaces.

    cluvfy comp nodecon -n all -verbose

#### cluvfy comp nodereach

Determines whether a source node can communicate with other, specific nodes, or all nodes in a cluster.

##### Syntax

    cluvfy comp nodereach {-n node_list | -allnodes} [-srcnode node] [-save [-savedir directory_path]] [-verbose]

##### Parameters

Table A-19 cluvfy comp nodereach Command Parameters

| Parameter                             | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                              |
|:--------------------------------------|:-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `-n ``node_list`` | -allnodes`        | Specify a comma-delimited list of non domain-qualified node names on which to conduct the verification, or all nodes in a cluster.                                                                                                                                                                                                                                                                                                                                                       |
| `-srcnode ``node`                     | Optionally, specify the name of the source node from which CVU performs the reachability test. If you do not specify a source node, then CVU uses the node on which you run the command as the source node.                                                                                                                                                                                                                                                                              |
| `-save [-savedir ``directory_path``]` | Use the `-save` or `-save -savedir` flags to save validation reports (`cvuchecdkreport_timestamp.txt` and `cvucheckreport_timestamp.htm`), where `timestamp` is the time and date of the validation report.<br>If you use the `-save` flag by itself, then CVU saves the reports in the `CVU_home/cv/report` directory, where `CVU_home` is the location of the CVU binaries.<br>If you use the `-save -savedir` flags, then specify a directory where you want CVU to save the reports. |
| `–verbose`                            | CVU prints detailed output.                                                                                                                                                                                                                                                                                                                                                                                                                                                              |

##### Example

To verify that `node3` is reachable over the network from the local node, use the following command:

    cluvfy comp nodereach -n node3

This command produces output similar to the following:

    Verifying node reachability

    Checking node reachability...
    Node reachability check passed from node "node1"

    Verification of node reachability was successful.

#### cluvfy comp ocr

Checks the integrity of Oracle Cluster Registry (OCR) on all specified nodes.

##### Syntax

    cluvfy comp ocr [-n node_list | -allnodes] [-method sudo -user user_name [-location directory_path] | -method root]
        [-verbose] [-json] [-html] [-save [-savedir directory_path]]

##### Parameters

Table A-20 cluvfy comp ocr Command Parameters

| Parameter                                                                  | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                              |
|:---------------------------------------------------------------------------|:-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `-n ``node_list`` | -allnodes`                                             | The comma-delimited list of non domain-qualified node names on which to conduct the verification, or all nodes in a cluster.<br>If you do not specify this option, then CVU checks only the local node.                                                                                                                                                                                                                                                                                  |
| `-method {sudo -user ``user_name`` [-location ``directory_path``] | root}` | Specify whether the privilege delegation method is `sudo` or `root`, for root user access. If you specify `sudo`, then you must specify the user name to access all the nodes with root privileges and, optionally, provide the full file system path for the `sudo` executable.                                                                                                                                                                                                         |
| `-save [-savedir ``directory_path``]`                                      | Use the `-save` or `-save -savedir` flags to save validation reports (`cvuchecdkreport_timestamp.txt` and `cvucheckreport_timestamp.htm`), where `timestamp` is the time and date of the validation report.<br>If you use the `-save` flag by itself, then CVU saves the reports in the `CVU_home/cv/report` directory, where `CVU_home` is the location of the CVU binaries.<br>If you use the `-save -savedir` flags, then specify a directory where you want CVU to save the reports. |
| `–verbose`                                                                 | CVU prints detailed output.                                                                                                                                                                                                                                                                                                                                                                                                                                                              |

##### Usage Notes

This command does not verify the integrity of OCR contents. You must use the OCRCHECK utility to verify the contents of OCR.

##### Example

To verify the integrity of OCR on the local node, run the following command:

    cluvfy comp ocr

This command returns output similar to the following:

    Verifying OCR integrity

    Checking OCR integrity...

    Checking the absence of a non-clustered configurationl...
    All nodes free of non-clustered, local-only configurations

    ASM Running check passed. ASM is running on all specified nodes

    Checking OCR config file "/etc/oracle/ocr.loc"...

    OCR config file "/etc/oracle/ocr.loc" check successful

    Disk group for ocr location “+DATA" available on all the nodes

    NOTE:
    This check does not verify the integrity of the OCR contents. Execute ‘ocrcheck' as a privileged user to verify the contents of OCR.

    OCR integrity check passed

    Verification of OCR integrity was successful.

#### cluvfy comp ohasd

Checks the integrity of the Oracle High Availability Services daemon.

##### Syntax

    cluvfy comp ohasd [-n node_list  | -allnodes] [-save [-savedir directory_path]] [-verbose]

##### Parameters

Table A-21 cluvfy comp ocr Command Parameters

| Parameter                             | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                              |
|:--------------------------------------|:-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `-n ``node_list`` | -allnodes`        | The comma-delimited list of non domain-qualified node names on which to conduct the verification, or all nodes in a cluster.<br>If you do not specify this option, then CVU checks only the local node.                                                                                                                                                                                                                                                                                  |
| `-save [-savedir ``directory_path``]` | Use the `-save` or `-save -savedir` flags to save validation reports (`cvuchecdkreport_timestamp.txt` and `cvucheckreport_timestamp.htm`), where `timestamp` is the time and date of the validation report.<br>If you use the `-save` flag by itself, then CVU saves the reports in the `CVU_home/cv/report` directory, where `CVU_home` is the location of the CVU binaries.<br>If you use the `-save -savedir` flags, then specify a directory where you want CVU to save the reports. |
| `–verbose`                            | CVU prints detailed output.                                                                                                                                                                                                                                                                                                                                                                                                                                                              |

##### Example

To verify that the Oracle High Availability Services daemon is operating correctly on all nodes in the cluster, use the following command:

    cluvfy comp ohasd -n allnodes -verbose

This command returns output similar to the following:

    Verifying OHASD integrity

    Checking OHASD integrity...
    ohasd is running on node "node1"
    ohasd is running on node "node2"
    ohasd is running on node "node3"
    ohasd is running on node "node4"

    OHASD integrity check passed

    Verification of OHASD integrity was successful.

#### cluvfy comp olr

Checks the integrity of Oracle Local Registry (OLR) on the local node.

##### Syntax

    cluvfy comp olr [-n node_list | -allnodes] [-save [-savedir directory_path]] [-verbose]

##### Parameters

Table A-22 cluvfy comp ocr Command Parameters

| Parameter                             | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                              |
|:--------------------------------------|:-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `-n ``node_list`` | -allnodes`        | The comma-delimited list of non domain-qualified node names on which to conduct the verification, or all nodes in a cluster.<br>If you do not specify this option, then CVU checks only the local node.                                                                                                                                                                                                                                                                                  |
| `-save [-savedir ``directory_path``]` | Use the `-save` or `-save -savedir` flags to save validation reports (`cvuchecdkreport_timestamp.txt` and `cvucheckreport_timestamp.htm`), where `timestamp` is the time and date of the validation report.<br>If you use the `-save` flag by itself, then CVU saves the reports in the `CVU_home/cv/report` directory, where `CVU_home` is the location of the CVU binaries.<br>If you use the `-save -savedir` flags, then specify a directory where you want CVU to save the reports. |
| `–verbose`                            | CVU prints detailed output.                                                                                                                                                                                                                                                                                                                                                                                                                                                              |

##### Usage Notes

- This command does not verify the integrity of the OLR contents. You must use the `ocrcheck -local` command to verify the contents of OLR.

##### Example

To verify the integrity of the OLR on the current node, run the following command:

    cluvfy comp olr -verbose

This command returns output similar to the following:

    Verifying OLR integrity

    Checking OLR integrity...

    Checking OLR config file...

    OLR config file check successful

    Checking OLR file attributes...

    OLR file check successful

    WARNING:
    This check does not verify the integrity of the OLR contents. Execute 'ocrcheck -local' as a privileged user to verify the contents of OLR.

    OLR integrity check passed

    Verification of OLR integrity was successful.

#### cluvfy comp peer

Checks the compatibility and properties of the specified nodes against a reference node.

You can check compatibility for non-default user group names and for different releases of the Oracle software. This command compares physical attributes, such as memory and swap space, user and group values, kernel settings, and installed operating system packages.

##### Syntax

    cluvfy comp peer {-n node_list | -allnodes} [-refnode node]
       [-r {10.1 | 10.2 | 11.1 | 11.2 | 12.1 | 12.2 | 18 | 19}] [-orainv orainventory_group]
       [-osdba osdba_group] [-osoper osoper_group] [-verbose] [-json] [-html] [-save [-savedir directory_path]]

##### Parameters

Table A-23 cluvfy comp peer Command Parameters

| Parameter                                                | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                              |
|:---------------------------------------------------------|:-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `-n ``node_list`` | -allnodes`                           | Specify a comma-delimited list of non domain-qualified node names, or all nodes in a cluster, on which to conduct the verification.<br>If you do not specify this option, then CVU checks only the local node.                                                                                                                                                                                                                                                                           |
| `-refnode ``node`                                        | Optionally, specify a node that CVU uses as a reference for checking compatibility with other nodes. If you do not specify this option, then CVU reports values for all the nodes in the node list.                                                                                                                                                                                                                                                                                      |
| `-r {10.1 | 10.2 | 11.1 | 11.2 | 12.1 | 12.2 | 18 | 19}` | Optionally, specify the software release that CVU checks as required for installation of Oracle Clusterware or Oracle RAC. If you do not specify this option, then CVU assumes Oracle Clusterware 19c or Oracle Database 19c.                                                                                                                                                                                                                                                            |
| `-orainv ``orainventory_group`                           | Optionally, you can specify the name of the Oracle Inventory group. If you do not specify this option, then CVU uses `oinstall` as the inventory group.<br>Note: This parameter is not available on Windows systems.                                                                                                                                                                                                                                                                     |
| `-osdba ``osdba_group`                                   | Optionally, you can specify the name of the OSDBA group. If you do not specify this option, then CVU uses `dba` as the OSDBA group.<br>Note: This parameter is not available on Windows systems.                                                                                                                                                                                                                                                                                         |
| `-json`                                                  | Use the `-json` flag to generate a detailed report in JSON format.<br>If you do not specify the `-json` flag, then CVU generates the detailed report in a text file.                                                                                                                                                                                                                                                                                                                     |
| `-html`                                                  | Use the `-html` flag to generate a detailed report in HTML format.<br>If you specify the `-html` flag, and a browser that CVU recognizes is available on the system, then CVU starts the browser and displays the report on the browser when the checks are complete.<br>If you do not specify the `-html` flag, then CVU generates the detailed report in a text file.                                                                                                                  |
| `-save [-savedir ``directory_path``]`                    | Use the `-save` or `-save -savedir` flags to save validation reports (`cvuchecdkreport_timestamp.txt` and `cvucheckreport_timestamp.htm`), where `timestamp` is the time and date of the validation report.<br>If you use the `-save` flag by itself, then CVU saves the reports in the `CVU_home/cv/report` directory, where `CVU_home` is the location of the CVU binaries.<br>If you use the `-save -savedir` flags, then specify a directory where you want CVU to save the reports. |
| `–verbose`                                               | CVU prints detailed output.                                                                                                                                                                                                                                                                                                                                                                                                                                                              |

##### Usage Notes

Peer comparison with the `-refnode` option compares the system properties of other nodes against the reference node. If the value of the other node is not greater than the value for that of the reference node, then CVU flags that comparison as a deviation from the reference node. If a group or user exists on neither the reference node nor on the other node, then CVU reports a match to indicate that there is no deviation from the reference node. Similarly, CVU reports as mismatched a comparison with a node that has less total memory than the reference node.

##### Example

The following command lists the values of several preselected properties on different nodes:

    cluvfy comp peer -n node1,node2,node4,node7 -verbose

#### cluvfy comp scan

Checks the Single Client Access Name (SCAN) configuration.

##### Syntax

    cluvfy comp scan [-save [-savedir directory_path]] [-verbose]

##### Usage Notes

- Use the `-save` or `-save -savedir` flags to save validation reports (`cvuchecdkreport_timestamp.txt` and `cvucheckreport_timestamp.htm`), where `timestamp` is the time and date of the validation report. If you use the `-save` flag by itself, then CVU saves the reports in the `CVU_home/cv/report` directory, where `CVU_home` is the location of the CVU binaries. If you use the `-save -savedir` flags, then specify a directory where you want CVU to save the reports.

- Optionally, you can include `-verbose` to print detailed output.

##### Example

To verify that the SCAN and SCAN listeners are configured and operational on all nodes in the cluster, use the following command:

    $ cluvfy comp scan

This command returns output similar to the following:

    Verifying scan

    Checking Single Client Access Name (SCAN)...

    Checking TCP connectivity to SCAN Listeners...
    TCP connectivity to SCAN Listeners exists on all cluster nodes

    Checking name resolution setup for "node1.example.com"...

    Verification of SCAN VIP and Listener setup passed

    Verification of scan was successful.

#### cluvfy comp software

Checks the files and attributes installed with the Oracle software.

##### Syntax

    cluvfy comp software [-n node_list | -allnodes] [-d oracle_home]
      [-allfiles] [-checksum] [-json] [-html] [-save [-savedir directory_path]] [-verbose]

##### Parameters

Table A-24 cluvfy comp software Command Parameters

| Parameter                             | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                              |
|:--------------------------------------|:-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `-n ``node_list`` | -allnodes`        | Optionally, you can specify a comma-delimited list of non domain-qualified node names, or all nodes in a cluster, on which to conduct the verification. If you do not specify this option, then CVU checks only the local node.                                                                                                                                                                                                                                                          |
| `-d ``oracle_home`                    | Optionally, you can specify the directory where the Oracle Database software is installed. If you do not specify this option, then CVU verifies the files installed in the Grid home.                                                                                                                                                                                                                                                                                                    |
| `-allfiles`                           | If you specify this parameter, then CVU checks the attributes of all files of the specified Oracle home. If you do not specify this parmater, then CVU checks the attributes of the `lib`, `jlib`, and `bin` files under the specified Oracle home.                                                                                                                                                                                                                                      |
| `-json`                               | Use the `-json` flag to generate a detailed report in JSON format.<br>If you do not specify the `-json` flag, then CVU generates the detailed report in a text file.                                                                                                                                                                                                                                                                                                                     |
| `-html`                               | Use the `-html` flag to generate a detailed report in HTML format.<br>If you specify the `-html` flag, and a browser that CVU recognizes is available on the system, then CVU starts the browser and displays the report on the browser when the checks are complete.<br>If you do not specify the `-html` flag, then CVU generates the detailed report in a text file.                                                                                                                  |
| `-save [-savedir ``directory_path``]` | Use the `-save` or `-save -savedir` flags to save validation reports (`cvuchecdkreport_timestamp.txt` and `cvucheckreport_timestamp.htm`), where `timestamp` is the time and date of the validation report.<br>If you use the `-save` flag by itself, then CVU saves the reports in the `CVU_home/cv/report` directory, where `CVU_home` is the location of the CVU binaries.<br>If you use the `-save -savedir` flags, then specify a directory where you want CVU to save the reports. |
| `–verbose`                            | CVU prints detailed output.                                                                                                                                                                                                                                                                                                                                                                                                                                                              |

##### Usage Notes

Add additional information about the command here.

##### Example

To verify that the installed files for Oracle Clusterware 19c are configured correctly, use a command similar to the following:

    $ cluvfy comp software -n all -verbose

This command returns output similar to the following:

    Verifying software

    Check: Software

     1021 files verified

    Software check passed

    Verification of software was successful.

#### cluvfy comp space

Checks for free disk space at the location you specify in the `-l` parameter on all the specified nodes.

##### Syntax

    cluvfy comp space [-n node_list | -allnodes] -l storage_location -z disk_space {B | K | M | G}
    [-save [-savedir directory_path]] [-verbose]

##### Parameters

Table A-25 cluvfy comp space Command Parameters

| Parameter                             | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                              |
|:--------------------------------------|:-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `-n ``node_list`                      | Specify a comma-delimited list of non domain-qualified node names on which to conduct the verification, or all nodes in a cluster. If you do not specify this parameter, then CVU checks only the local node.                                                                                                                                                                                                                                                                            |
| `-l ``storage_location`               | Specify the directory path to the storage location you want to check.                                                                                                                                                                                                                                                                                                                                                                                                                    |
| `-z ``disk_space`` {B | K | M | G}`   | Specify the required disk space, in units of bytes (B), kilobytes (K), megabytes (M), or gigabytes (G). There should be no space between the numeric value and the byte indicator; for example, 2G. Use only whole numbers.                                                                                                                                                                                                                                                              |
| `-save [-savedir ``directory_path``]` | Use the `-save` or `-save -savedir` flags to save validation reports (`cvuchecdkreport_timestamp.txt` and `cvucheckreport_timestamp.htm`), where `timestamp` is the time and date of the validation report.<br>If you use the `-save` flag by itself, then CVU saves the reports in the `CVU_home/cv/report` directory, where `CVU_home` is the location of the CVU binaries.<br>If you use the `-save -savedir` flags, then specify a directory where you want CVU to save the reports. |
| `–verbose`                            | CVU prints detailed output.                                                                                                                                                                                                                                                                                                                                                                                                                                                              |

##### Usage Notes

The `space` component does not support block or raw devices.

**See Also:**

The Oracle Certification site on My Oracle Support for the most current information about certified storage options:

[`https://support.oracle.com`](https://support.oracle.com)

##### Example

You can verify that each node has 5 GB of free space in the `/home/dbadmin/products` directory by running the following command:

    $ cluvfy comp space -n all -l /home/dbadmin/products –z 5G -verbose

#### cluvfy comp ssa

Use the `cluvfy comp ssa` component verification command to discover and check the sharing of the specified storage locations. CVU checks sharing for nodes in the node list.

##### Syntax

    cluvfy comp ssa [-n node_list | -allnodes] [-s storage_path_list]
      [-t {gi_software | rac_software | data | ocr_vdisk}]  [-asm] [-asmdev asm_device_list]
      [-r {10.1 | 10.2 | 11.1 | 11.2 | 12.1 | 12.2 | 18.1 | 19.1}] [-save [-savedir directory_path]] [-verbose]


##### Parameters

Table A-26 cluvfy comp ssa Command Parameters

| Parameter                                                     | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                              |
|:--------------------------------------------------------------|:-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `-n ``node_list`` | -allnodes `                               | The comma-delimited list of non domain-qualified node names on which to conduct the verification or all nodes.<br>If you do not specify any of these options, then CVU checks only the local node.                                                                                                                                                                                                                                                                                       |
| `-s ``storage_path_list`                                      | A comma-delimited list of storage paths, for example, `/dev/sda,/dev/sdb`.<br>If you do not specify the `-s` option, then CVU discovers supported storage types and checks sharing for each of them.                                                                                                                                                                                                                                                                                     |
| `-t {gi_software | rac_software | data | ocr_vdisk}`          | The type of Oracle files (Oracle Grid Infrastructure binaries, Oracle RAC, or Oracle Database binaries) that will be stored on the storage device.<br>If you do not specify `-t`, then CVU discovers or checks the `data` file type.                                                                                                                                                                                                                                                     |
| `-asm`                                                        | Specify this parameter to discover all storage suitable for use by Oracle ASM.                                                                                                                                                                                                                                                                                                                                                                                                           |
| `-asmdev ``asm_device_list`                                   | A comma-delimited list of Oracle ASM devices for which you want to check sharing of storage locations. If the list contains shell metacharacters, then enclose the list in double quotation marks (`""`).                                                                                                                                                                                                                                                                                |
| `-r {10.1 | 10.2 | 11.1 | 11.2 | 12.1 | 12.2 | 18 | 19 | 20}` | Optionally, you can specify the release number of the product for which you are running the verification. If you do not specify `-r`, then CVU runs the verification for `20`.                                                                                                                                                                                                                                                                                                           |
| `-save [-savedir ``directory_path``]`                         | Use the `-save` or `-save -savedir` flags to save validation reports (`cvuchecdkreport_timestamp.txt` and `cvucheckreport_timestamp.htm`), where `timestamp` is the time and date of the validation report.<br>If you use the `-save` flag by itself, then CVU saves the reports in the `CVU_home/cv/report` directory, where `CVU_home` is the location of the CVU binaries.<br>If you use the `-save -savedir` flags, then specify a directory where you want CVU to save the reports. |
| `-verbose`                                                    | CVU prints detailed output.                                                                                                                                                                                                                                                                                                                                                                                                                                                              |

##### Usage Notes

- The current release of `cluvfy` has the following limitations on Linux regarding shared storage accessibility check.

  - Currently NAS storage and OCFS2 (version 1.2.1 or higher) are supported.

    **See Also:**

    [Oracle Grid Infrastructure Installation Guide](../install-and-upgrade.md) for more information about NAS mount options

  - When checking sharing on NAS, `cluvfy` commands require that you have write permission on the specified path. If the `cluvfy` user does not have write permission, `cluvfy` reports the path as `not` `shared`.

- To perform discovery and shared storage accessibility checks for SCSI disks on Linux systems, CVU requires the CVUQDISK package. If you attempt to use CVU and the CVUQDISK package is not installed on all of the nodes in your Oracle RAC environment, then CVU responds with an error. See "Shared Disk Discovery on Red Hat Linux" for information about how to install the CVUQDISK package.

##### Examples

To discover all of the shared storage systems available on your system:

    $ cluvfy comp ssa -allnodes -verbose

To discover all the storage suitable for use by Oracle ASM, based on the specified Oracle ASM discovery string:

    $ cluvfy comp ssa -n node1,node2 -asm -asmdev "/dev/xda*"

You can verify the accessibility of specific storage locations, such as an Oracle ASM disk group called `OCR13`, for storing data files for all the cluster nodes by running a command similar to the following:

    $ cluvfy comp ssa -allnodes -s OCR13

This command produces output similar to the following:

    Verifying shared storage acessibility

    Checking shared storage accessibility...

    "OCR13" is shared

    Shared storage check was successful on nodes "node1,node2,node3,node4"

    Verification of shared storage accessibility was successful.

#### cluvfy comp sys

Checks that the minimum system requirements are met for the specified product on all the specified nodes.

##### Syntax

    cluvfy comp sys [-n node_list | -allnodes] -p {crs | ha | database}  [-r {10.1 | 10.2 | 11.1 | 11.2 | 12.1 | 12.2 | 18 | 19}]
      [-osdba osdba_group] [-osoper osoper_group] [-orainv orainventory_group] [-fixup] [-fixupnoexec]
      [-method sudo -user user_name [-location directory_path] | -method root] [-verbose]
      [-json] [-html] [-save [-savedir directory_path]]

##### Parameters

Table A-27 cluvfy comp sys Command Parameters

| Parameter                                                                        | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                              |
|:---------------------------------------------------------------------------------|:-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `-n ``node_list`` | -flex -hub ``hub_list`                                       | Specify a comma-delimited list of non domain-qualified node names on which to conduct the verification. If you do not specify this option, then CVU checks only the local node.<br>Alternatively, you can specify a list of Hub Nodes on which to conduct the verification.                                                                                                                                                                                                              |
| `-p {crs | ha | database}`                                                       | Specifies whether CVU checks the system requirements for Oracle Clusterware, Oracle Restart (HA), or Oracle RAC.<br>Note: Oracle does not support Oracle Restart for Oracle Database 10g. If you use the `-p ha` option with `-r 10.1 | 10.2`, then CVU returns an error.                                                                                                                                                                                                                |
| `-r {10.1 | 10.2 | 11.1 | 11.2 | 12.1 | 12.2 | 18 | 19}`                         | Specifies the Oracle Database release that CVU checks as required for installation of Oracle Clusterware or Oracle RAC. If you do not specify this option, then CVU assumes Oracle Database 19c.                                                                                                                                                                                                                                                                                         |
| `-osdba ``osdba_group`                                                           | The name of the OSDBA group. If you do not specify this option, then CVU uses `dba` as the OSDBA group.                                                                                                                                                                                                                                                                                                                                                                                  |
| `-orainv ``orainventory_group`                                                   | The name of the Oracle Inventory group. If you do not specify this option, then CVU uses `oinstall` as the inventory group.                                                                                                                                                                                                                                                                                                                                                              |
| `-fixup`                                                                         | Specifies that if the verification fails, then CVU performs fixup operations, if feasible.                                                                                                                                                                                                                                                                                                                                                                                               |
| `-fixupnoexec`                                                                   | Specifies that if verification fails, then CVU generates the fixup data and displays the instructions for manual execution of the generated fixups.                                                                                                                                                                                                                                                                                                                                      |
| `-method sudo -user ``user_name`` [-location ``directory_path``] | -method root` | Specify whether the privilege delegation method is `sudo` or `root`, for root user access. If you specify `sudo`, then you must specify the user name to access all the nodes with root privileges and, optionally, provide the full file system path for the `sudo` executable.                                                                                                                                                                                                         |
| `–verbose`                                                                       | CVU prints detailed output.                                                                                                                                                                                                                                                                                                                                                                                                                                                              |
| `-json`                                                                          | Use the `-json` flag to generate a detailed report in JSON format.<br>If you do not specify the `-json` flag, then CVU generates the detailed report in a text file.                                                                                                                                                                                                                                                                                                                     |
| `-html`                                                                          | Use the `-html` flag to generate a detailed report in HTML format.<br>If you specify the `-html` flag, and a browser that CVU recognizes is available on the system, then CVU starts the browser and displays the report on the browser when the checks are complete.<br>If you do not specify the `-html` flag, then CVU generates the detailed report in a text file.                                                                                                                  |
| `-save [-savedir ``directory_path``]`                                            | Use the `-save` or `-save -savedir` flags to save validation reports (`cvuchecdkreport_timestamp.txt` and `cvucheckreport_timestamp.htm`), where `timestamp` is the time and date of the validation report.<br>If you use the `-save` flag by itself, then CVU saves the reports in the `CVU_home/cv/report` directory, where `CVU_home` is the location of the CVU binaries.<br>If you use the `-save -savedir` flags, then specify a directory where you want CVU to save the reports. |

##### Example

To verify the system requirements for installing Oracle Clusterware 19c on the cluster nodes `node1`,`node2` and `node3`, run the following command:

    cluvfy comp sys -n node1,node2,node3 -p crs -verbose

#### cluvfy comp vdisk

Checks the voting files configuration and the `udev` settings for the voting files on all the specified nodes.

**See Also:**

[Oracle Grid Infrastructure Installation and Upgrade Guide for Linux](../cwlin/index.md) for more information about `udev` settings

##### Syntax

    cluvfy comp vdisk [-n node_list | -allnodes] [-save [-savedir directory_path]] [-verbose]

##### Parameters

Table A-28 cluvfy comp vdisk Command Parameters

| Parameter                             | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                              |
|:--------------------------------------|:-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `-n ``node_list`` | -allnodes`        | The comma-delimited list of non domain-qualified node names on which to conduct the verification, or all nodes in a cluster.<br>If you do not specify this option, then CVU checks only the local node.                                                                                                                                                                                                                                                                                  |
| `-save [-savedir ``directory_path``]` | Use the `-save` or `-save -savedir` flags to save validation reports (`cvuchecdkreport_timestamp.txt` and `cvucheckreport_timestamp.htm`), where `timestamp` is the time and date of the validation report.<br>If you use the `-save` flag by itself, then CVU saves the reports in the `CVU_home/cv/report` directory, where `CVU_home` is the location of the CVU binaries.<br>If you use the `-save -savedir` flags, then specify a directory where you want CVU to save the reports. |
| `–verbose`                            | CVU prints detailed output.                                                                                                                                                                                                                                                                                                                                                                                                                                                              |

#### cluvfy comp vital

Performs vital healthchecks and reports issues that may affect the stability of Oracle Grid Infrastructure.

##### Syntax

    cluvfy comp vital [-verbose|-progress] [-json] [-html] [-save [-savedir directory_path]]

##### Parameters

Table A-29 cluvfy comp vital Command Parameters

| Parameter                             | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                              |
|:--------------------------------------|:-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `[-verbose|-progress]`                | Use the `-verbose` flag to print detailed output, or `-progress` flag to print current progress of the command.                                                                                                                                                                                                                                                                                                                                                                          |
| `-json`                               | Use the `-json` flag to generate a detailed report in JSON format.<br>If you do not specify the `-json` flag, then CVU generates the detailed report in a text file.                                                                                                                                                                                                                                                                                                                     |
| `-html`                               | Use the `-html` flag to generate a detailed report in HTML format.<br>If you specify the `-html` flag, and a browser that CVU recognizes is available on the system, then CVU starts the browser and displays the report on the browser when the checks are complete.<br>If you do not specify the `-html` flag, then CVU generates the detailed report in a text file.                                                                                                                  |
| `-save [-savedir ``directory_path``]` | Use the `-save` or `-save -savedir` flags to save validation reports (`cvuchecdkreport_timestamp.txt` and `cvucheckreport_timestamp.htm`), where `timestamp` is the time and date of the validation report.<br>If you use the `-save` flag by itself, then CVU saves the reports in the `CVU_home/cv/report` directory, where `CVU_home` is the location of the CVU binaries.<br>If you use the `-save -savedir` flags, then specify a directory where you want CVU to save the reports. |

#### cluvfy stage acfscfg

Use the `cluvfy stage -pre acfscfg` command to verify that your cluster nodes are set up correctly before configuring Oracle Automatic Storage Management Cluster File System (Oracle ACFS). Use the `cluvfy stage -post acfscfg` to check an existing cluster after you configure Oracle ACFS.

##### Syntax

    cluvfy stage -pre acfscfg {-n node_list | -allnodes} [-asmdev asm_device_list] [-afdconfig]
    [-save [-savedir directory_path]] [-verbose]

    cluvfy stage -post acfscfg {-n node_list | -allnodes} [-save [-savedir directory_path]] [-verbose]

##### Parameters

Table A-30 cluvfy stage acfscfg Command Parameters

| Parameter                             | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                              |
|:--------------------------------------|:-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `-n ``node_list`` | -allnodes`        | Specify a comma-delimited list of non domain-qualified node names, or all nodes in a cluster, on which to conduct the verification, for both before and after configuring Oracle ACFS.                                                                                                                                                                                                                                                                                                   |
| `-asmdev ``asm_device_list`           | The list of devices you plan for Oracle ASM to use. If you do not specify this option, then CVU uses an internal operating system-dependent value; for example, `/dev/raw/*` on Linux systems.                                                                                                                                                                                                                                                                                           |
| `-afdconfig`                          | Verifies Oracle ASM Filter Driver configuration prerequisites.                                                                                                                                                                                                                                                                                                                                                                                                                           |
| `-save [-savedir ``directory_path``]` | Use the `-save` or `-save -savedir` flags to save validation reports (`cvuchecdkreport_timestamp.txt` and `cvucheckreport_timestamp.htm`), where `timestamp` is the time and date of the validation report.<br>If you use the `-save` flag by itself, then CVU saves the reports in the `CVU_home/cv/report` directory, where `CVU_home` is the location of the CVU binaries.<br>If you use the `-save -savedir` flags, then specify a directory where you want CVU to save the reports. |
| `-verbose`                            | CVU prints detailed output.                                                                                                                                                                                                                                                                                                                                                                                                                                                              |

#### cluvfy stage appcluster

Performs the appropriate pre-stage and post-stage checks for Oracle Clusterware application cluster installations on the specified nodes.

##### Syntax

    cluvfy stage -pre appcluster {-n node_list | -allnodes} [-verbose]

    cluvfy stage -post appcluster {-n node_list | -allnodes} [-method sudo -user user_name
       [-location dir_path] | -method root] [-verbose]

##### Parameters

Table A-31 cluvfy stage appcluster Command Parameters

| Parameter                                                                 | Description                                                                                                                                                                                                                                                                                  |
|:--------------------------------------------------------------------------|:---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `-n ``node_list`` | -allnodes`                                            | Specify a comma-delimited list of non domain-qualified node names on which you want to run the verification. Specify `-allnodes` to run the verification on all nodes in the cluster.                                                                                                        |
| `-method sudo -user ``user_name``[-location ``dir_path``] | -method root` | Chose the privilege delegation method, either `sudo` or `root`, to be used for root user access.<br>If you choose the `sudo` method, then you must provide a user name to access all the nodes with `root` privileges, and, optionally, the full file system path for the `sudo` executable. |

#### cluvfy stage cfs

Use the `cluvfy stage -pre cfs` stage verification command to verify your cluster nodes are set up correctly before configuring OCFS2. Use the `cluvfy stage -post cfs` stage verification command to perform the appropriate checks on the specified nodes after configuring OCFS2.

**See Also:**

[Oracle Grid Infrastructure Installation and Upgrade Guide](../install-and-upgrade.md) for your platform for a list of supported shared storage types

##### Syntax

    cluvfy stage -pre cfs {-n node_list | -allnodes} -s storageID_list [-save [-savedir directory_path]] [-verbose]

    cluvfy stage -post cfs {-n node_list | -allnodes} -f file_system [-save [-savedir directory_path]] [-verbose]

##### Parameters

Table A-32 cluvfy stage cfs Command Parameters

| Parameter                             | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                              |
|:--------------------------------------|:-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `-n ``node_list`` | -allnodes`        | Specify a comma-delimited list of non domain-qualified node names on which to conduct the verification, for both before and after configuring OCFS2. Specify `-allnodes` to run the verification on all nodes in the cluster.                                                                                                                                                                                                                                                            |
| `-s ``storageID_list`                 | Specify a comma-delimited list of storage locations to check before configuring OCFS2.                                                                                                                                                                                                                                                                                                                                                                                                   |
| `-f ``file_system`                    | Specify a file system to check after configuring OCFS2.                                                                                                                                                                                                                                                                                                                                                                                                                                  |
| `-save [-savedir ``directory_path``]` | Use the `-save` or `-save -savedir` flags to save validation reports (`cvuchecdkreport_timestamp.txt` and `cvucheckreport_timestamp.htm`), where `timestamp` is the time and date of the validation report.<br>If you use the `-save` flag by itself, then CVU saves the reports in the `CVU_home/cv/report` directory, where `CVU_home` is the location of the CVU binaries.<br>If you use the `-save -savedir` flags, then specify a directory where you want CVU to save the reports. |
| `–verbose`                            | CVU prints detailed output.                                                                                                                                                                                                                                                                                                                                                                                                                                                              |

##### Example

To check that a shared device is configured correctly before setting up OCFS2, use a command similar to the following, where you replace `/dev/sdd5` with the name of the shared device on your system:

    $ cluvfy stage -pre cfs -n node1,node2,node3,node4 -s /dev/sdd5

#### cluvfy stage crsinst

Use the `cluvfy stage -pre crsinst` command with either the `-file`, `-n`, `-flex`, or `-upgrade` parameters to check the specified nodes before installing or upgrading Oracle Clusterware. Use the `cluvfy stage -post crsinst` command to check the specified nodes after installing Oracle Clusterware.

##### Syntax

    cluvfy stage -pre crsinst -responseFile file_name [-fixup] [-fixupnoexec]
      [-method sudo -user user_name [-location directory_path] | -method root] [-r {10.1|10.2|11.1|11.2|12.1|12.2|18|19}]
      [-verbose] [-json] [-html] [-save [-savedir directory_path]] [-orachk_loc location] [-skip check_utilities]

    cluvfy stage -pre crsinst -file config_file [-fixup] [-fixupnoexec]
      [-method sudo -user user_name [-location directory_path] | -method root] [-verbose] [-json] [-html] [-save [-savedir directory_path]]

    cluvfy stage -pre crsinst {-n node_list | -allnodes}
      [-r {10.1 | 10.2 | 11.1 | 11.2 | 12.1 | 12.2 | 18 | 19}] [-c ocr_location_list] [-q voting_disk_list]
      [-osdba osdba_group] [-osoper osoper_group] [-orainv orainventory_group] [-asm [-presence {local | flex}
      | -asmcredentials client_data_file] [-asmgrp asmadmin_group] [-asmdev asm_device_list] [-afdconfig]]
      [-crshome Grid_home] [-fixup] [-fixupnoexec] [-method sudo -user user_name [-location directory_path] | -method root]
      [-networks network_list] [-dhcp -clustername cluster_name [-dhcpport dhcp_port]] [-dns -vipaddress gns_vip_address
      [-domain gns_sub_domain]] [-software_only] [-verbose] [-orachk_loc location] [-skip check_utilities]
      [-json] [-html] [-save [-savedir directory_path]] [-verbose]

    cluvfy stage -pre crsinst -upgrade [-rolling] [-src_crshome src_crshome] -dest_crshome dest_crshome
      -dest_version dest_version [-fixup] [-fixupnoexec] [-method sudo -user user_name
      [-location directory_path] | -method root] [-verbose] [-json] [-html] [-save [-savedir directory_path]] [-orachk_loc location] [-skip check_utilities]

    cluvfy stage -post crsinst {-n node_list | -allnodes}
      [-method sudo -user user_name [-location directory_path] | -method root] [-verbose] [-verbose] [-json] [-html] [-save [-savedir directory_path]]

##### Parameters

Table A-33 cluvfy stage \[-pre \| -post\] crsinst Command Parameters

| Parameter                                                                  | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                              |
|:---------------------------------------------------------------------------|:-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `-responseFile`                                                            | Specify the response file, created by the Oracle Universal Installer, containing Oracle installation variables.                                                                                                                                                                                                                                                                                                                                                                          |
| `-file ``config_file`                                                      | Specify the root script configuration file containing Oracle installation variables.                                                                                                                                                                                                                                                                                                                                                                                                     |
| `-n ``node_list`` | -allnodes`                                             | Specify a comma-delimited list of non domain-qualified node names on which to conduct the verification. Specify `-allnodes` to run the verification on all nodes in the cluster.                                                                                                                                                                                                                                                                                                         |
| `-r {10.1 | 10.2 | 11.1 | 11.2 | 12.1 | 12.2 | 18 | 19}`                   | Specifies the Oracle Clusterware release that CVU checks as required for installation of Oracle Clusterware. If you do not specify this option, then CVU assumes Oracle Clusterware 19c.                                                                                                                                                                                                                                                                                                 |
| `-c ``ocr_location_list`                                                   | Specify a comma-delimited list of directory paths for OCR locations or files that CVU checks for availability to all nodes. If you do not specify this option, then the OCR locations are not checked.                                                                                                                                                                                                                                                                                   |
| `-q ``voting_disk_list`                                                    | Specify a comma-delimited list of directory paths for voting files that CVU checks for availability to all nodes. If you do not specify this option, then CVU does not check the voting file locations.                                                                                                                                                                                                                                                                                  |
| `-osdba ``osdba_group`                                                     | Specify the name of the OSDBA group. If you do not specify this option, then CVU uses `dba` as the OSDBA group.                                                                                                                                                                                                                                                                                                                                                                          |
| `-osoper ``osoper_group`                                                   | Specify the name of the OSOPER group.                                                                                                                                                                                                                                                                                                                                                                                                                                                    |
| `-orainv ``orainventory_group`                                             | Specify the name of the Oracle Inventory group. If you do not specify this option, then CVU uses `oinstall` as the inventory group.                                                                                                                                                                                                                                                                                                                                                      |
| `-asm [-presence {local | flex} | -asmcredentials ``client_data_file`      | This parameter indicates that Oracle ASM is used for storing the Oracle Clusterware files.<br>Specify the Oracle ASM presence, either `LOCAL` or `FLEX`, on this Oracle Clusterware installation. Optionally, for an Oracle ASM client, specify the path to an Oracle ASM client credential file.                                                                                                                                                                                        |
| `-asmgrp ``asmadmin_group`                                                 | Specify the name of the OSASM group. If you do not specify this parameter, then CVU uses the same group as the Oracle Inventory group.                                                                                                                                                                                                                                                                                                                                                   |
| `-asmdev ``asm_device_list`                                                | Specify a list of devices you plan for Oracle ASM to use that CVU checks for availability to all nodes.<br>If you do not specify this parameter, then CVU uses an internal operating system-dependent value.                                                                                                                                                                                                                                                                             |
| `-afdconfig`                                                               | Verifies Oracle ASM Filter Driver configuration prerequisites.                                                                                                                                                                                                                                                                                                                                                                                                                           |
| `-crshome ``Grid_home`                                                     | Specify the location of the Oracle Grid Infrastructure or Oracle Clusterware home directory. If you specify this parameter, then the supplied file system location is checked for sufficient free space for an Oracle Clusterware installation.                                                                                                                                                                                                                                          |
| `-networks ``network_list`                                                 | Checks the network parameters of a slash ("`/`")-delimited list of networks in the form of `"``if_name``" [:``subnet_id`` [:public | :cluster_interconnect]]`.<br>• You can use the asterisk (`*`) wildcard character when you specify the network interface name (`if_name`), such as `eth*`, to match interfaces.<br>• Specify a subnet number for the network interface for the `subnet_id` variable and choose the type of network interface.                                        |
| `-dhcp -clustername ``cluster_name`` [-dhcpport ``dhcp_port``]`            | Specify the name of the cluster. Optionally, you can specify the port to which the DHCP packets will be sent. The default value for this port is 67.                                                                                                                                                                                                                                                                                                                                     |
| `-dns -vipaddress ``gns_vip_address`                                       | Specify the GNS virtual IP address in the form `{``ip_name`` | ``ip_address``}/``net_mask``/``interface_name`. You can specify either `ip_name`, which is a name that resolves to an IP address, or `IP_address`, which is an IP address. Either name or address is followed by `net_mask`, which is the subnet mask for the IP address, and `interface_name`, which is the interface on which to start the IP address.                                                                  |
| `-domain ``gns_sub_domain`                                                 | Specify the name of the GNS subdomain.                                                                                                                                                                                                                                                                                                                                                                                                                                                   |
| `–upgrade`                                                                 | Specify this parameter to verify upgrade prerequisites.                                                                                                                                                                                                                                                                                                                                                                                                                                  |
| `-rolling`                                                                 | Specify this parameter to perform a rolling upgrade.                                                                                                                                                                                                                                                                                                                                                                                                                                     |
| `-src_crshome ``src_crshome`                                               | Specify the location of the source Grid home.                                                                                                                                                                                                                                                                                                                                                                                                                                            |
| `-dest_crshome ``dest_crshome`                                             | Specify the location of the destination Grid home.                                                                                                                                                                                                                                                                                                                                                                                                                                       |
| `-dest_version ``dest_version`                                             | Specify the version to which you are upgrading, including any patchset, such as `11.2.0.1.0` or `11.2.0.2.0`.                                                                                                                                                                                                                                                                                                                                                                            |
| `-fixup`                                                                   | Specifies that if the verification fails, then CVU performs fixup operations, if feasible.                                                                                                                                                                                                                                                                                                                                                                                               |
| `-fixupnoexec`                                                             | Specifies that if verification fails, then CVU generates the fixup data and displays the instructions for manual execution of the generated fixups.                                                                                                                                                                                                                                                                                                                                      |
| `-method sudo -user ``user_name`` [-location ``dir_path``] | -method root` | Specify whether the privilege delegation method is `sudo` or `root`, for root user access. If you specify `sudo`, then you must specify the user name to access all the nodes with root privileges and, optionally, provide the full file system path for the `sudo` executable.                                                                                                                                                                                                         |
| `–verbose`                                                                 | CVU prints detailed output.                                                                                                                                                                                                                                                                                                                                                                                                                                                              |
| `-json`                                                                    | Use the `-json` flag to generate a detailed report in JSON format.<br>If you do not specify the `-json` flag, then CVU generates the detailed report in a text file.                                                                                                                                                                                                                                                                                                                     |
| `-html`                                                                    | Use the `-html` flag to generate a detailed report in HTML format.<br>If you specify the `-html` flag, and a browser that CVU recognizes is available on the system, then CVU starts the browser and displays the report on the browser when the checks are complete.<br>If you do not specify the `-html` flag, then CVU generates the detailed report in a text file.                                                                                                                  |
| `-save [-savedir ``directory_path``]`                                      | Use the `-save` or `-save -savedir` flags to save validation reports (`cvuchecdkreport_timestamp.txt` and `cvucheckreport_timestamp.htm`), where `timestamp` is the time and date of the validation report.<br>If you use the `-save` flag by itself, then CVU saves the reports in the `CVU_home/cv/report` directory, where `CVU_home` is the location of the CVU binaries.<br>If you use the `-save -savedir` flags, then specify a directory where you want CVU to save the reports. |

##### Usage Notes

- To perform checks for a new installation, specify either the `-file` or `-n` parameters, and use `-upgrade` for performing checks for upgrading to another version.

- CVU performs additional checks on OCR and voting files if you specify the `-c` and `-q` options with the `-n` parameter.

#### cluvfy stage dbcfg

Checks the specified nodes before configuring an Oracle RAC database to verify whether your system meets all of the criteria for creating a database or for making a database configuration change.

##### Syntax

On Linux and UNIX platforms:

    cluvfy stage -pre dbcfg {-n node_list | -allnodes} -d Oracle_home [-fixup] [-fixupnoexec]
      [-method sudo -user user_name [-location directory_path] | root] [-verbose] [-orachk_loc location]
      [-skip check_utilities] [-json] [-html] [-save [-savedir directory_path]]

On Windows platforms:

    cluvfy stage -pre dbcfg {-n node_list | -allnodes} -d oracle_home [-fixup] [-fixupnoexec]
      [-verbose] [-json] [-html] [-save [-savedir directory_path]]

##### Parameters

Table A-34 cluvfy stage -pre dbcfg Command Parameters

| Parameter                                                                | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                              |
|:-------------------------------------------------------------------------|:-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `-n ``node_list`` | -allnodes`                                           | The comma-delimited list of nondomain qualified node names on which to conduct the verification. Specify `-allnodes` to run the verification on all nodes in the cluster.                                                                                                                                                                                                                                                                                                                |
| `-d ``Oracle_home`                                                       | The location of the Oracle home directory for the database that is being checked.                                                                                                                                                                                                                                                                                                                                                                                                        |
| `-fixup`                                                                 | Specifies that if the verification fails, then CVU performs fixup operations, if feasible.                                                                                                                                                                                                                                                                                                                                                                                               |
| `-fixupnoexec`                                                           | Specifies that if verification fails, then CVU generates the fixup data and displays the instructions for manual execution of the generated fixups.                                                                                                                                                                                                                                                                                                                                      |
| `-method sudo -user ``user_name`` [-location ``directory_path``] | root` | Specify whether the privilege delegation method is `sudo` or `root`, for root user access. If you specify `sudo`, then you must specify the user name to access all the nodes with root privileges and, optionally, provide the full file system path for the `sudo` executable.                                                                                                                                                                                                         |
| `-save [-savedir ``directory_path``]`                                    | Use the `-save` or `-save -savedir` flags to save validation reports (`cvuchecdkreport_timestamp.txt` and `cvucheckreport_timestamp.htm`), where `timestamp` is the time and date of the validation report.<br>If you use the `-save` flag by itself, then CVU saves the reports in the `CVU_home/cv/report` directory, where `CVU_home` is the location of the CVU binaries.<br>If you use the `-save -savedir` flags, then specify a directory where you want CVU to save the reports. |
| `–verbose`                                                               | CVU prints detailed output.                                                                                                                                                                                                                                                                                                                                                                                                                                                              |
| `-json`                                                                  | Use the `-json` flag to generate a detailed report in JSON format.<br>If you do not specify the `-json` flag, then CVU generates the detailed report in a text file.                                                                                                                                                                                                                                                                                                                     |
| `-html`                                                                  | Use the `-html` flag to generate a detailed report in HTML format.<br>If you specify the `-html` flag, and a browser that CVU recognizes is available on the system, then CVU starts the browser and displays the report on the browser when the checks are complete.<br>If you do not specify the `-html` flag, then CVU generates the detailed report in a text file.                                                                                                                  |
| `-save [-savedir ``directory_path``]`                                    | Use the `-save` or `-save -savedir` flags to save validation reports (`cvuchecdkreport_timestamp.txt` and `cvucheckreport_timestamp.htm`), where `timestamp` is the time and date of the validation report.<br>If you use the `-save` flag by itself, then CVU saves the reports in the `CVU_home/cv/report` directory, where `CVU_home` is the location of the CVU binaries.<br>If you use the `-save -savedir` flags, then specify a directory where you want CVU to save the reports. |

#### cluvfy stage -pre dbinst

Checks the specified nodes before installing or creating an Oracle RAC database to verify that your system meets all of the criteria for installing or creating an Oracle RAC database.

##### Syntax

On Linux and UNIX platforms:

    cluvfy stage -pre dbinst {-n node_list | -allnodes} [-r {10.1 | 10.2 | 11.1 | 11.2 | 12.1 | 12.2 | 18 | 19}]
      [-osdba osdba_group] [-osoper osoper_group] [-osbackup osbackup_group] [-osdg osdg_group]
      [-oskm oskm_group] [-d oracle_home] [-fixup] [-fixupnoexec] [-method sudo -user user_name
      [-location directory_path] | -method root] [-verbose] [-orachk_loc location] [-skip check_utilities]
      [-json] [-html][-save [-savedir directory_path]]

    cluvfy stage pre dbinst -upgrade -src_dbhome src_dbhome [-dbname dbname-list]
      -dest_dbhome dest_dbhome -dest_version dest_version [-pdbs pdbname-list]
      [-fixup] [-fixupnoexec] [-method sudo -user user_name [-location directory_path | -method root] [-verbose]
      [-orachk_loc location] [-skip check_utilities] [-json] [-html] [-save [-savedir directory_path]]

On Windows platforms:

    cluvfy stage -pre dbinst {-n node_list | -allnodes} [-r {10.1 | 10.2 | 11.1 | 11.2 | 12.1 | 12.2 | 18 | 19}]
      [-d Oracle_home] [-fixup] [-fixupnoexec] [-serviceuser user_name [-servicepasswd]]]
      [-verbose] [-json] [-html] [-save [-savedir directory_path]]

    cluvfy stage -pre dbinst -upgrade -src_dbhome src_dbhome [-dbname dbname-list
      -dest_dbhome dest_dbhome -dest_version dest_version [-fixup] [-fixupnoexec]
      [-verbose] [-json] [-html] [-save [-savedir directory_path]]

##### Parameters

Table A-35 cluvfy stage -pre dbinst Command Parameters

| Parameter                                                                        | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    |
|:---------------------------------------------------------------------------------|:-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `-n ``node_list`` | -allnodes`                                                   | Specify a comma-delimited list of non domain-qualified node names on which to conduct the verification. Specify `-allnodes` to run the verification on all nodes in the cluster.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                               |
| `-r {10.1 | 10.2 | 11.1 | 11.2 | 12.1 | 12.2 | 18 | 19}`                         | Specifies the Oracle Database release that CVU checks as required for installation of Oracle RAC. If you do not specify this option, then CVU assumes Oracle Database 19c.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                     |
| `-osdba ``osdba_group`                                                           | The name of the OSDBA group. If you do not specify this option, then CVU uses `dba` as the OSDBA group.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                        |
| `-osoper ``osoper_group`                                                         | Specify the name of the OSOPER group.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          |
| `-osbackup ``osbackup_group`                                                     | Specify the name of the OSBACKUP group.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                        |
| `-osdg ``osdg_group`                                                             | Specify the name of the OSDG group.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            |
| `-oskm ``oskm_group`                                                             | Specify the name of the OSKM group.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            |
| `-d ``oracle_home`                                                               | The location of the Oracle home directory where you are installing Oracle RAC and creating the Oracle RAC database. If you specify this parameter, then the specified location is checked for sufficient free disk space for a database installation.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          |
| `-fixup`                                                                         | Specifies that if the verification fails, then CVU performs fixup operations, if feasible.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                     |
| `-fixupnoexec`                                                                   | Specifies that if verification fails, then CVU generates the fixup data and displays the instructions for manual execution of the generated fixups.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            |
| `-upgrade`                                                                       | Specify this parameter to verify upgrade prerequisites.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                        |
| `-src_dbhome ``src_dbhome`                                                       | Specify the location of the source database home from which you are upgrading.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 |
| `-dbname ``dbname-list`                                                          | Specify a comma-delimited list of unique names of the databases you want to upgrade.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           |
| `-dest_dbhome ``dest_dbhome`                                                     | Specify the location of the destination database home to which you are upgrading.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              |
| `-dest_version ``dest_version`                                                   | Specify the version to which you are upgrading, including any patchset, such as `11.2.0.1.0` or `11.2.0.2.0`.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  |
| `-pdbs`                                                                          | Specify a comma-delimited list of unique names of the pluggable databases (PDBs) you want to upgrade.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          |
| `-method sudo -user ``user_name`` [-location ``directory_path``] | -method root` | Specify whether the privilege delegation method is `sudo` or `root`, for root user access. If you specify `sudo`, then you must specify the user name to access all the nodes with root privileges and, optionally, provide the full file system path for the `sudo` executable.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                               |
| `-serviceuser ``user_name`` [-servicepasswd]`                                    | If you specify this option, then CVU checks the following:<br>• Whether the specified user is a domain user. If the specified user is not a domain user, then CVU returns an error and does not perform any subsequent checks on the validation of the user.<br>• Note: You must specify the user name of the Oracle home user.<br>• Whether the specified user is an administrator on all nodes in the cluster. If the user is not an administrator on any node in the cluster, then the check passes. Otherwise, the check fails.<br>• If you do not specify the `-servicepwd` option, then CVU checks whether there is a password stored in the wallet on OCR for this user. If no password exists for the specified user, then CVU continues to run.<br>• If you specify the `-servicepwd` option, then CVU prompts you for the password of the specified user, even if the password exists in the wallet.<br>Note: The `-serviceuser` and `-servicepwd` parameters only apply to Windows. |
| `-save [-savedir ``directory_path``]`                                            | Use the `-save` or `-save -savedir` flags to save validation reports (`cvuchecdkreport_timestamp.txt` and `cvucheckreport_timestamp.htm`), where `timestamp` is the time and date of the validation report.<br>If you use the `-save` flag by itself, then CVU saves the reports in the `CVU_home/cv/report` directory, where `CVU_home` is the location of the CVU binaries.<br>If you use the `-save -savedir` flags, then specify a directory where you want CVU to save the reports.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       |
| `–verbose`                                                                       | CVU prints detailed output.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    |

#### cluvfy stage hacfg

Checks the local node before and after configuring Oracle Restart.

##### Syntax

    cluvfy stage -pre hacfg [-osdba osdba_group] [-osoper osoper_group] [-orainv orainventory_group]
      [-fixup] [-fixupnoexec] [-method sudo -user user_name [-location directory_path] | -method root]
      [-verbose] [-json] [-html] [-save [-savedir directory_path]]

    cluvfy stage -post hacfg [-verbose] [-json] [-html] [-save [-savedir directory_path]]

##### Parameters

Table A-36 cluvfy stage hacfg Command Parameters

| Parameter                                                                  | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                              |
|:---------------------------------------------------------------------------|:-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `-osdba ``osdba_group`                                                     | Specify the name of the OSDBA group. If you do not specify this option, then CVU uses `dba` as the OSDBA group.                                                                                                                                                                                                                                                                                                                                                                          |
| `-osoper ``osoper_group`                                                   | Specify the name of the OSOPER group.                                                                                                                                                                                                                                                                                                                                                                                                                                                    |
| `-orainv ``orainventory_group`                                             | Specify the name of the Oracle Inventory group. If you do not specify this option, then CVU uses `oinstall` as the inventory group.                                                                                                                                                                                                                                                                                                                                                      |
| `-fixup`                                                                   | Specifies that if the verification fails, then CVU performs fixup operations, if feasible.                                                                                                                                                                                                                                                                                                                                                                                               |
| `-fixupnoexec`                                                             | Specifies that if verification fails, then CVU generates the fixup data and displays the instructions for manual execution of the generated fixups.                                                                                                                                                                                                                                                                                                                                      |
| `-method sudo -user ``user_name`` [-location ``dir_path``] | -method root` | Specify whether the privilege delegation method is `sudo` or `root`, for root user access. If you specify `sudo`, then you must specify the user name to access all the nodes with root privileges and, optionally, provide the full file system path for the `sudo` executable.                                                                                                                                                                                                         |
| `-save [-savedir ``directory_path``]`                                      | Use the `-save` or `-save -savedir` flags to save validation reports (`cvuchecdkreport_timestamp.txt` and `cvucheckreport_timestamp.htm`), where `timestamp` is the time and date of the validation report.<br>If you use the `-save` flag by itself, then CVU saves the reports in the `CVU_home/cv/report` directory, where `CVU_home` is the location of the CVU binaries.<br>If you use the `-save -savedir` flags, then specify a directory where you want CVU to save the reports. |
| `-verbose`                                                                 | CVU prints detailed output.                                                                                                                                                                                                                                                                                                                                                                                                                                                              |
| `-json`                                                                    | Use the `-json` flag to generate a detailed report in JSON format.<br>If you do not specify the `-json` flag, then CVU generates the detailed report in a text file.                                                                                                                                                                                                                                                                                                                     |
| `-html`                                                                    | Use the `-html` flag to generate a detailed report in HTML format.<br>If you specify the `-html` flag, and a browser that CVU recognizes is available on the system, then CVU starts the browser and displays the report on the browser when the checks are complete.<br>If you do not specify the `-html` flag, then CVU generates the detailed report in a text file.                                                                                                                  |
| `-save [-savedir ``directory_path``]`                                      | Use the `-save` or `-save -savedir` flags to save validation reports (`cvuchecdkreport_timestamp.txt` and `cvucheckreport_timestamp.htm`), where `timestamp` is the time and date of the validation report.<br>If you use the `-save` flag by itself, then CVU saves the reports in the `CVU_home/cv/report` directory, where `CVU_home` is the location of the CVU binaries.<br>If you use the `-save -savedir` flags, then specify a directory where you want CVU to save the reports. |

#### cluvfy stage hwos

Checks network and storage on the specified nodes in the cluster. This command also checks for supported storage types and checks each one for sharing.

##### Syntax

    cluvfy stage -post hwos {-n node_list | -allnodes} [-s storageID_list] [-save [-savedir directory_path]] [-verbose]

##### Parameters

Table A-37 cluvfy stage hwos Command Parameters

| Parameter                             | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                              |
|:--------------------------------------|:-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `-n ``node_list`                      | The comma-delimited list of non domain-qualified node names on which to conduct the verification. Specify `-allnodes` to run the verification on all nodes in the cluster.                                                                                                                                                                                                                                                                                                               |
| `-s ``storageID_list`                 | Checks the comma-delimited list of storage locations for sharing of supported storage types.<br>If you do not specify the `-s` parameter, then CVU discovers supported storage types and checks sharing for each of them.                                                                                                                                                                                                                                                                |
| `-save [-savedir ``directory_path``]` | Use the `-save` or `-save -savedir` flags to save validation reports (`cvuchecdkreport_timestamp.txt` and `cvucheckreport_timestamp.htm`), where `timestamp` is the time and date of the validation report.<br>If you use the `-save` flag by itself, then CVU saves the reports in the `CVU_home/cv/report` directory, where `CVU_home` is the location of the CVU binaries.<br>If you use the `-save -savedir` flags, then specify a directory where you want CVU to save the reports. |
| `–verbose`                            | CVU prints detailed output.                                                                                                                                                                                                                                                                                                                                                                                                                                                              |

#### cluvfy stage nodeadd

Use the `cluvfy stage -pre nodeadd` command to verify the specified nodes are configured correctly before adding them to your existing cluster, and to verify the integrity of the cluster before you add the nodes. Use the `cluvfy stage -post nodeadd` command to verify that the specified nodes have been successfully added to the cluster at the network, shared storage, and clusterware levels.

The `cluvfy stage -pre nodeadd` command verifies that the system configuration, such as the operating system version, software patches, packages, and kernel parameters, for the nodes that you want to add, is compatible with the existing cluster nodes, and that the clusterware is successfully operating on the existing nodes. Run this command on any node of the existing cluster.

##### Syntax

    cluvfy stage -pre nodeadd -n node_list [-vip vip_list] [-fixup] [-fixupnoexec]
      [-method sudo -user user_name [-location directory_path] | -method root]
      [-verbose] [-json] [-html] [-save [-savedir directory_path]]

    cluvfy stage -post nodeadd -n node_list [-verbose] [-json] [-html] [-save [-savedir directory_path]]

##### Parameters

Table A-38 cluvfy stage nodeadd Command Parameters

| Parameter                                                                        | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                              |
|:---------------------------------------------------------------------------------|:-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `-n ``node_list`                                                                 | Specify a comma-delimited list of non domain-qualified node names on which to conduct the verification. These are the nodes you are adding or have added to the cluster.                                                                                                                                                                                                                                                                                                                 |
| `-vip ``vip_list`                                                                | A comma-delimited list of virtual IP addresses to be used by the new nodes.                                                                                                                                                                                                                                                                                                                                                                                                              |
| `-flex [-hub ``hub_list`` [-vip ``vip_list``]]`                                  | Specify `-flex` if you are adding a node to an Oracle Flex Cluster. Optionally, you can specify a comma-delimited list of non domain-qualified node names that you want to add to the cluster as Hub Nodes.<br>Additionally, you can specify a comma-delimited list of virtual IP addresses that will be applied to the list of Hub Nodes you specify.                                                                                                                                   |
| `-fixup`                                                                         | This optional parameter specifies that if the verification fails, then CVU performs fixup operations, if feasible.                                                                                                                                                                                                                                                                                                                                                                       |
| `-fixupnoexec`                                                                   | This optional parameter specifies that if verification fails, then CVU generates the fixup data and displays the instructions for manual execution of the generated fixups.                                                                                                                                                                                                                                                                                                              |
| `-method sudo -user ``user_name`` [-location ``directory_path``] | -method root` | Specify whether the privilege delegation method is `sudo` or `root`, for root user access. If you specify `sudo`, then you must specify the user name to access all the nodes with root privileges and, optionally, provide the full file system path for the `sudo` executable.                                                                                                                                                                                                         |
| `–verbose`                                                                       | CVU prints detailed output.                                                                                                                                                                                                                                                                                                                                                                                                                                                              |
| `-json`                                                                          | Use the `-json` flag to generate a detailed report in JSON format.<br>If you do not specify the `-json` flag, then CVU generates the detailed report in a text file.                                                                                                                                                                                                                                                                                                                     |
| `-html`                                                                          | Use the `-html` flag to generate a detailed report in HTML format.<br>If you specify the `-html` flag, and a browser that CVU recognizes is available on the system, then CVU starts the browser and displays the report on the browser when the checks are complete.<br>If you do not specify the `-html` flag, then CVU generates the detailed report in a text file.                                                                                                                  |
| `-save [-savedir ``directory_path``]`                                            | Use the `-save` or `-save -savedir` flags to save validation reports (`cvuchecdkreport_timestamp.txt` and `cvucheckreport_timestamp.htm`), where `timestamp` is the time and date of the validation report.<br>If you use the `-save` flag by itself, then CVU saves the reports in the `CVU_home/cv/report` directory, where `CVU_home` is the location of the CVU binaries.<br>If you use the `-save -savedir` flags, then specify a directory where you want CVU to save the reports. |

#### cluvfy stage nodedel

Verifies that specific nodes have been successfully deleted from a cluster. Typically, this command verifies that the node-specific interface configuration details have been removed, the nodes are no longer a part of cluster configuration, and proper Oracle ASM cleanup has been performed.

##### Syntax

    cluvfy stage -post nodedel -n node_list [-save [-savedir directory_path]] [-verbose]

##### Parameters

Table A-39 cluvfy stage nodedel Command Parameters

| Parameter                             | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                              |
|:--------------------------------------|:-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `-n ``node_list`` | -allnodes`        | Specify a comma-delimited list of non domain-qualified node names on which to conduct the verification, for both before and after configuring OCFS2. Specify `-allnodes` to run the verification on all nodes in the cluster.                                                                                                                                                                                                                                                            |
| `-save [-savedir ``directory_path``]` | Use the `-save` or `-save -savedir` flags to save validation reports (`cvuchecdkreport_timestamp.txt` and `cvucheckreport_timestamp.htm`), where `timestamp` is the time and date of the validation report.<br>If you use the `-save` flag by itself, then CVU saves the reports in the `CVU_home/cv/report` directory, where `CVU_home` is the location of the CVU binaries.<br>If you use the `-save -savedir` flags, then specify a directory where you want CVU to save the reports. |
| `–verbose`                            | CVU prints detailed output.                                                                                                                                                                                                                                                                                                                                                                                                                                                              |

**See Also:**

[Adding and Deleting Cluster Nodes](adding-and-deleting-cluster-nodes.md)

##### Usage Notes

- If the `cluvfy stage -post nodedel` check fails, then repeat the node deletion procedure.

#### cluvfy stage osupg

Performs the Oracle Grid Infrastructure prerequisites checks on all the nodes in the nodelist to ensure readiness for Linux operating system upgrade.

##### Syntax

**Note:**

This command is supported only on Linux platforms.

    cluvfy stage -pre osupg {-n node_list | -allnodes} [-checkGIdriverSupport kernel_information]
    [-verbose] [-json] [-html] [-save [-savedir directory_path]]

##### Parameters

Table A-40 cluvfy stage osupg Command Parameters

| Parameter                                    | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                              |
|:---------------------------------------------|:-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `-n ``node_list`` | -allnodes`               | The comma-delimited list of non domain-qualified node names on which to conduct the verification, or all nodes in a cluster.<br>If you do not specify this option, then CVU checks only the local node.                                                                                                                                                                                                                                                                                  |
| `-checkGIdriverSupport ``kernel_information` | Optionally, specify the operating system kernel version or an absolute path to the kernel RPM file to check for the Oracle Grid Infrastructure driver support.                                                                                                                                                                                                                                                                                                                           |
| `-verbose`                                   | CVU prints detailed output.                                                                                                                                                                                                                                                                                                                                                                                                                                                              |
| `-json`                                      | Use the `-json` flag to generate a detailed report in JSON format.<br>If you do not specify the `-json` flag, then CVU generates the detailed report in a text file.                                                                                                                                                                                                                                                                                                                     |
| `-html`                                      | Use the `-html` flag to generate a detailed report in HTML format.<br>If you specify the `-html` flag, and a browser that CVU recognizes is available on the system, then CVU starts the browser and displays the report on the browser when the checks are complete.<br>If you do not specify the `-html` flag, then CVU generates the detailed report in a text file.                                                                                                                  |
| `-save [-savedir ``directory_path``]`        | Use the `-save` or `-save -savedir` flags to save validation reports (`cvuchecdkreport_timestamp.txt` and `cvucheckreport_timestamp.htm`), where `timestamp` is the time and date of the validation report.<br>If you use the `-save` flag by itself, then CVU saves the reports in the `CVU_home/cv/report` directory, where `CVU_home` is the location of the CVU binaries.<br>If you use the `-save -savedir` flags, then specify a directory where you want CVU to save the reports. |

#### cluvfy stage patch

Performs the appropriate pre-stage checks for the patch application on all nodes. Performs post-stage check for the patch application.

##### Syntax

    cluvfy stage -pre patch [-db -dbhome oracle_home [-dbname dbname-list]] [-non_rolling]
        [-verbose] [-orachk_loc location] [-skip check_utilities]

    cluvfy stage -post patch [-db -dbhome oracle_home] [-verbose]

##### Parameters

Table A-41 cluvfy stage patch Command Parameters

| Parameter                   | Description                                                                        |
|:----------------------------|:-----------------------------------------------------------------------------------|
| `-db -dbhome ``oracle_home` | Specify the location of the database home which you are patching.                  |
| `-dbname ``dbname-list`     | Specify a comma-delimited list of unique names of the databases you want to patch. |
| `-non_rolling`              | Use the `-non_rolling` flag to apply patch in non-rolling mode.                    |
| `–verbose`                  | CVU prints detailed output.                                                        |

##### Usage Notes

By default, the pre-stage checks are performed for patching in rolling mode.

### Troubleshooting and Diagnostic Output for CVU

This section describes the following troubleshooting topics for CVU:

- Enabling Tracing

- Known Issues for the Cluster Verification Utility

#### Enabling Tracing

CVU generates trace files unless you disable tracing. You can disable tracing by setting the `SRVM_TRACE` environment variable to `false` or `FALSE`. For example, in `tcsh` an entry such as `setenv SRVM_TRACE FALSE` disables tracing.

The CVU trace files are created in the `ORACLE_BASE/crsdata/``host_name``/cvu` directory by default. Oracle Database automatically rotates the log files and the most recently created log file has the name `cvutrace.log.0`. You should remove unwanted log files or archive them to reclaim disk place if needed.

Oracle Clusterware stores log files that CVU generates when it runs periodically in the `ORACLE_BASE/crsdata/``host_name``/cvu/cvutrc` directory.

To use a non-default location for the trace files, set the `CV_TRACELOC` environment variable to the absolute path of the desired trace directory.

#### Known Issues for the Cluster Verification Utility

This section describes the following known limitations for Cluster Verification Utility (CVU):

- Database Versions Supported by Cluster Verification Utility

- Linux Shared Storage Accessibility (ssa) Check Reports Limitations

- Shared Disk Discovery on Red Hat Linux

##### Database Versions Supported by Cluster Verification Utility

The current CVU release supports only Oracle Database 10g or higher, Oracle RAC, and Oracle Clusterware; CVU is not backward compatible. CVU cannot check or verify Oracle Database products for releases before Oracle Database 10g.

##### Linux Shared Storage Accessibility (ssa) Check Reports Limitations

The current release of `cluvfy` has the following limitations on Linux regarding shared storage accessibility check.

- OCFS2 (version 1.2.1 or higher) is supported.

- For sharedness checks on NAS, `cluvfy` commands require you to have write permission on the specified path. If the user running the `cluvfy` command does not have write permission, then `cluvfy` reports the path as `not` `shared`.

##### Shared Disk Discovery on Red Hat Linux

To perform discovery and shared storage accessibility checks for SCSI disks on Red Hat Linux 5.0 (or higher) and Oracle Linux 5.0 (or higher), and SUSE Linux Enterprise Server, CVU requires the CVUQDISK package. If you attempt to use CVU and the CVUQDISK package is not installed on all of the nodes in your Oracle RAC environment, then CVU responds with an error.

Perform the following procedure to install the CVUQDISK package:

1.  Login as the `root` user.

2.  Copy the package, `cvuqdisk-1.0.9-1.rpm` (or higher version) to a local directory. You can find this rpm in the `rpm` subdirectory of the top-most directory in the Oracle Clusterware installation media. For example, you can find `cvuqdisk-1.0.9-1.rpm` in the directory `/``mountpoint``/clusterware/rpm/` where `mountpoint` is the mount point for the disk on which the directory is located.

        # cp /mount_point/clusterware/rpm/cvuqdisk-1.0.9-1.rpm /u01/oradba

3.  Set the `CVUQDISK_GRP` environment variable to the operating system group that should own the CVUQDISK package binaries. If `CVUQDISK_GRP` is not set, then, by default, the `oinstall` group is the owner's group.

        # set CVUQDISK_GRP=oinstall

4.  Determine whether previous versions of the CVUQDISK package are installed by running the command `rpm -q cvuqdisk`. If you find previous versions of the CVUQDISK package, then remove them by running the command `rpm -e cvuqdisk` `previous_version` where `previous_version` is the identifier of the previous CVUQDISK version, as shown in the following example:

        # rpm -q cvuqdisk
        cvuqdisk-1.0.2-1
        # rpm -e cvuqdisk-1.0.2-1

5.  Install the latest CVUQDISK package by running the command `rpm -iv cvuqdisk-1.0.9-1.rpm`.

        # cd /u01/oradba
        # rpm -iv cvuqdisk-1.0.9-1.rpm

------------------------------------------------------------------------



Footnote Legend

Footnote 1: Applicable only on UNIX platforms
