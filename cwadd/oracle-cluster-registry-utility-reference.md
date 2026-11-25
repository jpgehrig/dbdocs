This appendix describes the syntax of the Oracle Cluster Registry (OCR) configuration utility, OCRCONFIG, and troubleshooting OCR, which includes descriptions and usage information for OCRCHECK and OCRDUMP.

This appendix contains the following topics:

- About OCRCONFIG

- OCRCONFIG Command Reference

- Troubleshooting Oracle Cluster Registry and Diagnostic Output

### About OCRCONFIG

Use the `ocrconfig` command to manage OCR. Using this utility you can import, export, add, delete, restore, overwrite, backup, repair, replace, move, upgrade, or downgrade OCR.

#### Usage Information

- The OCRCONFIG executable is located in the `Grid_home/bin` directory

- The `ocrconfig` command syntax is as follows:

      ocrconfig -option

#### Using Utility Help

To display the help output for the OCRCONFIG utility:

    ocrconfig -help

#### Privileges and Security

To use the OCRCONFIG utility you must be logged into the operating system as a user with administrative privileges.

#### Log Files

The OCRCONFIG utility creates a log file in `ORACLE_BASE``/diag/crs/``host_name``/crs` .

To change the amount of logging, edit the path in the `ORACLE_BASE``/crsdata/``host_name``/crsdiag/ocrconfig.ini` file.

### OCRCONFIG Command Reference

This section describes the following OCRCONFIG commands:

- `ocrconfig -add`

- `ocrconfig -backuploc`

- `ocrconfig -copy`

- `ocrconfig -delete`

- `ocrconfig -downgrade`

- `ocrconfig -export`

- `ocrconfig -import`

- `ocrconfig -manualbackup`

- `ocrconfig -overwrite`

- `ocrconfig -repair`

- `ocrconfig -replace`

- `ocrconfig -restore`

- `ocrconfig -showbackup`

- `ocrconfig -showbackuploc`

- `ocrconfig -upgrade`

#### ocrconfig -add

Adds an OCR location to an Oracle Automatic Storage Management (Oracle ASM) disk group.

##### Syntax

    ocrconfig -add +diskgroup_name

##### Usage Notes

- OCR locations that you add must exist, have sufficient permissions, and must be mounted before you can add them.

- You must run this command as `root`.

- The `diskgroup_name` variable is the name of an Oracle ASM disk group. For example:

  - `+newdg`: Ensure that the disk group exists and is mounted

    The name of the disk group must be preceded by a plus sign (`+`).

  **See Also:**

  - [Oracle Grid Infrastructure Installation and Upgrade Guide for Linux](../cwlin/configuring-storage-for-oracle-grid-infrastructure-for-a-cluster.md) for information about creating OCR locations and setting correct permissions

  - [Oracle Automatic Storage Management Administrator's Guide](../ostmg/admin-asm-diskgroups.md) for more information about Oracle ASM disk group management

##### Example

To add an OCR location to the default location in Oracle ASM, `data`:

    # ocrconfig -add +data

#### ocrconfig -backuploc

Specify an OCR backup directory location.

##### Syntax

    ocrconfig -backuploc +disk_group_name
    ocrconfig -local -backuploc dir_name

##### Usage Notes

- You must run this command as `root`.

- Use the `-local` option to specify an OLR backup directory location.

- For an OCR backup location, the `disk_group_name` variable must be an Oracle ASM disk group. For example:

  `+bkupdg`: Ensure that the Oracle ASM disk group exists and is mounted on all nodes

  An Oracle ASM disk group name must be preceded by a plus sign (+).

- For an OLR backup location, the `dir_name` variable can be a full directory path name. For example:

  - `Grid_home``/cdata/cluster3/`: Ensure that the location exists

  - `d:\cdata\cluster3`: Ensure that the location exists

  The default location for generating OLR backups on Linux or UNIX systems is `Grid_base``/crsdata/``host_name``/olr/`, where `host_name` is the name of the node on which the OLR resides that you want to back up. The Windows default location for generating OLR backups uses the same path structure.

##### Examples

To specify an OCR backup location in an Oracle ASM disk group:

    # ocrconfig -backuploc +bkupdg

To specify an OLR backup location:

    # ocrconfig -local -backuploc full_directory_path

#### ocrconfig -copy

Copies an OCR backup file from one location to another.

##### Syntax

    ocrconfig -copy source_file_name destination_file_name

##### Usage Notes

- You must run this command as `root`.

- The `source_file_name` must be a valid OCR backup file. For example:

  - `/oradbocfs/crs/BACKUP00.ocr`

  - `d:\oracle\BACKUP01.ocr`

  - `+bkupdg:/aimev1/ocrbackup/day.ocr.260.739756845`

  If you specify an Oracle ASM disk group, then ensure that the disk group exists and is mounted.

  Examples of valid `destination_file_name` values are:

  - `/oradbocfs/crs/mybkp01.ocr`

  - `d:\oracle\mybkp01.ocr`

  - `+bkupdg:mybkp01`

  Oracle ASM disk group names must be preceded by a plus sign (+).

##### Examples

To copy an OCR backup file from a file system to an Oracle ASM disk group:

    # ocrconfig -copy /oradbocfs/crs/BACKUP00.ocr +bkupdg:mybkp01.ocr

To copy an OCR backup file from an Oracle ASM disk group to a file system:

    # ocrconfig -copy +bkupdg:/aimev1/ocrbackup/day.ocr.260.739756845 /oradbocfs/crs/mybkp01.ocr

To copy an OCR backup file from one Oracle ASM disk group to another Oracle ASM disk group:

    # ocrconfig -copy +bkupdg01:/aimev1/ocrbackup/day.ocr.260.739756845 +bkupdg02:mybkp01.ocr

#### ocrconfig -delete

Removes an OCR device or file.

##### Syntax

    ocrconfig -delete +diskgroup_name

##### Usage Notes

- You must run this command as `root`.

- The `+``diskgroup_name` variable is the name of an Oracle ASM disk group. For example: `+olddg`

  The name of the disk group must be preceded by a plus sign (`+`).

##### Example

To remove an OCR location:

    # ocrconfig -delete +olddg

#### ocrconfig -downgrade

Only root scripts use this command to downgrade OCR to an earlier specified version.

##### Syntax

`ocrconfig -downgrade`

##### Usage Notes

This command has no options.

#### ocrconfig -export

Exports the contents of OCR to a target file.

##### Syntax

    ocrconfig [-local] -export file_name

##### Usage Notes

- You must run this command as `root`.

- Use the `-local` option to export the contents of OLR.

- The `file_name` variable can be a file name or the name of an Oracle ASM disk group (preceded by a plus sign (`+`)). For example:

  - `/oradbocfs/crs/data.ocr`

  - `d:\oracle\data.ocr`

  - `+bkupdg:data.ocr`

##### Example

To export the contents of OCR to a file:

    # ocrconfig -export d:\tmp\a

#### ocrconfig -import

Imports the contents of a target file into which you exported the contents of OCR back into OCR.

##### Syntax

    ocrconfig [-local] -import file_name

##### Usage Notes

- You must run this command as `root`.

- Use the `-local` option to import the contents of OLR from a file.

- The `file_name` variable can be a file name or the name of an Oracle ASM disk group (preceded by a plus sign (`+`)). For example:

  - `/oradbocfs/crs/data.ocr`
  - `d:\oracle\data.ocr`
  - `+bkupdg:/aimev1/ocrbackup/data.ocr.260.739756845`

- You must shut down Oracle Clusterware before running this command.

##### Example

To import the contents a file back into OCR:

    # ocrconfig -import d:\tmp\a

#### ocrconfig -manualbackup

Backs up OCR on demand to a specific location.

##### Prerequisites

Determine the location of the on-demand backup using `ocrconfig -backuploc`.

##### Syntax

    ocrconfig [-local] -manualbackup

##### Usage Notes

- You must run this command as `root`.

- Use the `-local` option to perform a manual backup of OLR.

#### ocrconfig -overwrite

Overwrites an OCR configuration in the OCR metadata with the current OCR configuration information that is found on the node from which you run this command.

##### Syntax

    ocrconfig -overwrite

##### Usage Notes

You must run this command as `root`.

#### ocrconfig -repair

Repairs an OCR configuration on the node from which you run this command.

Use this command to add, delete, or replace an OCR location on a node that may have been stopped while you made changes to the OCR configuration in the cluster. OCR locations that you add must exist, have sufficient permissions, and must be mounted before you can add them.

##### Prerequisites

- Oracle High Availability Services must be started to successfully complete the repair.

- The Cluster Ready Services daemon must be stopped before running `ocrconfig -repair`.

##### Syntax

    ocrconfig -repair -add +diskgroup_name | -delete +diskgroup_name | -replace
       +current_diskgroup_name -replacement +new_diskgroup_name

##### Usage Notes

- You must run this command as `root`.

- The `+``diskgroup_name` variable is the name of an Oracle ASM disk group. For example: `+newdg/mycluster/OCRFILE/registry.255.842574125`

  If you specify an Oracle ASM disk group, then the name of the disk group must be preceded by a plus sign (`+`).

  To obtain the name of an Oracle ASM disk group, run the `ocrcheck -config -details` command on a node where the OCR configuration does not need repair.

  **See Also:**

  - [Oracle Grid Infrastructure Installation and Upgrade Guide for Linux](../cwlin/configuring-storage-for-oracle-grid-infrastructure-for-a-cluster.md) for information about creating OCR locations and setting correct permissions

  - [Oracle Automatic Storage Management Administrator's Guide](../ostmg/admin-asm-diskgroups.md) for more information about Oracle ASM disk group management

  - "Using the OCRCHECK Utility" for information about the `ocrcheck -config -details` command

- You can only use one option with `ocrconfig -repair` at a time.

- Running this command only modifies the local configuration and it and only affects the current node.

##### Example

To repair an OCR configuration:

    # ocrconfig -repair -delete +olddg

#### ocrconfig -replace

Replaces an OCR location to an Oracle Automatic Storage Management (Oracle ASM) disk group.

##### Prerequisites

- OCR locations that you add must exist, have sufficient permissions, and must be mounted before you can add them.

- You must have at least two OCR devices to use this command. If you do not have at least two OCR devices, then you must run the `ocrconfig -add` command to add a new OCR device followed by the `ocrconfig -delete` command to delete the OCR device you want to replace.

##### Syntax

    ocrconfig -replace +current_diskgroup_name -replacement +new_diskgroup_name

##### Usage Notes

- You must run this command as `root`.

- The `+``diskgroup_name` variable is the name of an Oracle ASM disk group, preceded by a plus sign (`+`). For example: `+newdg`. The disk group must exist and be mounted.

  **See Also:**

  - [Oracle Grid Infrastructure Installation and Upgrade Guide for Linux](../cwlin/configuring-storage-for-oracle-grid-infrastructure-for-a-cluster.md) for information about creating OCR locations and setting correct permissions

  - [Oracle Automatic Storage Management Administrator's Guide](../ostmg/admin-asm-diskgroups.md) for more information about Oracle ASM disk group management

##### Example

To replace an OCR device or file:

    # ocrconfig -replace +olddg -replacement +newdg

#### ocrconfig -restore

Restores OCR from an automatically created OCR backup file.

##### Prerequisites

- Before running this command, ensure that the original OCR or OLR files exist. If the original file does not exist, then you must create an empty file.

  **Note:**

  You cannot use a file generated by the `ocrconfig -export` command to restore OCR. The file must be a manual or automatic backup.

- If OCR is located on an Oracle ASM disk group, then ensure that the disk group exists and is mounted.

##### Syntax

    ocrconfig [-local] -restore file_name

##### Usage Notes

- You must run this command as `root`.

- If the OCR backup file is located in an Oracle ASM disk group, then ensure that the disk group exists and is mounted.

- The name of an Oracle ASM disk group must be preceded by a plus sign (`+`).

- Use the `-local` option to restore a backup of OLR.

- Example file names are:

  - `/oradbocfs/crs/BACKUP00.ocr`

  - `d:\oracle\BACKUP01.ocr`

  - `+bkupdg:/aimev1/ocrbackup/day.ocr.260.739756845`

##### Example

To restore OCR from a file:

    # ocrconfig -restore /oradbocfs/crs/BACKUP00.ocr

#### ocrconfig -showbackup

Displays all available backups.

##### Syntax

    ocrconfig [-local] -showbackup [auto | manual]

##### Usage Notes

- Use the `-local` option to show manual OLR backup information. The `-local` flag functions only with the `manual` option.

- You can optionally specify `auto` or `manual` to display information about only automatic backups or only manual backups, respectively:

  - `auto`: Displays information about automatic backups that Oracle Clusterware created in the past 4 hours, 8 hours, 12 hours, and in the last day and week.

  - `manual`: Displays information for, at most, the last five manual backups that you invoke using the `ocrconfig -manualbackup` command.

##### Example

This command displays manual backup information for OLR, similar to the following:

    $ ocrconfig -local -showbackup manual
    cc40524 2020/05/08 15:06:57 /gridbase/crsdata/dglnx6/olr/backup_20200508_150657.olr 0

#### ocrconfig -showbackuploc

Displays the backup location of the OCR and OLR backup files.

##### Syntax

    ocrconfig [-local] -showbackuploc

##### Usage Notes

- You must run this command as `root`

- Use the `-local` option to display the OLR backup location

##### Example

This command returns output similar to the following:

    # ocrconfig -showbackuploc

    The Oracle Cluster Registry backup location is [+bkupdg]

    # ocrconfig -local -showbackuploc
    The Oracle Local Registry backup location is [/gridbase/crsdata/dglnx6/olr]

#### ocrconfig -upgrade

Upgrades OCR from a previous version.

##### Syntax

    ocrconfig -upgrade

##### Usage Notes

This command has no options.

### Troubleshooting Oracle Cluster Registry and Diagnostic Output

This section describes various methods for troubleshooting problems with OCR, and obtaining diagnostic information from the utilities used to manage OCR. You can use these utilities to troubleshoot OLR.

This section contains the following topics:

- Troubleshooting Oracle Cluster Registry

- Using the OCRCHECK Utility

- Using the OCRDUMP Utility to View Oracle Cluster Registry Content

#### Troubleshooting Oracle Cluster Registry

Table I-1 describes common OCR problems with corresponding resolution suggestions.

Table I-1 Common Oracle Cluster Registry Problems and Solutions

| Problem                                                                                                           | Solution                                                                                                                                          |
|:------------------------------------------------------------------------------------------------------------------|:--------------------------------------------------------------------------------------------------------------------------------------------------|
| Not currently using OCR mirroring and would like to enable it.                                                    | Run the `ocrconfig` command with the `-replace` option.                                                                                           |
| OCR failed and you must replace it. Error messages in Oracle Enterprise Manager or OCR log file.                  | Run the `ocrconfig` command with the `-replace` option.                                                                                           |
| OCR has a misconfiguration.                                                                                       | Run the `ocrconfig` command with the `-repair` option as described.                                                                               |
| You are experiencing a severe performance effect from OCR processing or you want to remove OCR for other reasons. | Run the `ocrconfig` command with the `-replace` option as described.                                                                              |
| OCR has failed and before you can fix it, the node must be rebooted with only one OCR.                            | Run the `ocrconfig` with the `-repair` option to remove the bad OCR location. Oracle Clusterware cannot start if it cannot find all OCRs defined. |

#### Using the OCRCHECK Utility

The OCRCHECK utility displays the version of the OCR's block format, total space available and used space, OCRID, and the OCR locations that you have configured.

OCRCHECK performs a block-by-block `checksum` operation for all of the blocks in all of the OCRs that you have configured. It also returns an individual status for each file and a result for the overall OCR integrity check.

**Note:**

Oracle supports using the `ocrcheck` command when, at a minimum, the Oracle Cluster Ready Services stack is OFFLINE on all nodes in the cluster because the command will run even if the stack is ONLINE but it can falsely indicate that the OCR is corrupt if the check happens while an update to OCR is underway.

**See Also:**

"[The Oracle Clusterware Technology Stack](introduction-to-oracle-clusterware.md)" for more information about the Oracle Cluster Ready Services stack

##### Syntax

    ocrcheck [-local] [-config | -backupfile <backup_file_name>] [-details] [-help]

You can run the `ocrcheck -help` command to display usage information about this utility.

The `-details` option displays detailed OCR configuration information, including names for Oracle ASM disk groups.

##### Examples

The following examples show sample OCRCHECK command output and command usage.

Example I-1 OCRCHECK Utility Sample Output

    # ocrcheck

    Status of Oracle Cluster Registry is as follows :
            Version                  :          4
            Total space (kbytes)     :     409568
            Used space (kbytes)      :      17012
            Available space (kbytes) :     392556
            ID                       :  467263828
            Device/File Name         : +ocrdg1
                                       Device/File integrity check succeeded
            Device/File Name         : +ocrdg2
                                       Device/File integrity check succeeded
                                       Device/File not configured
                                       Device/File not configured
                                       Device/File not configured
            Cluster registry integrity check succeeded
            Logical corruption check succeeded

**Note:**

The logical corruption check is only performed if you run the `ocrcheck` command as `root`.

Example I-2 shows using `ocrcheck -local -config` command to obtain OLR information.

**Note:**

Oracle supports using the `ocrcheck -local` command when both the Oracle Cluster Ready Services and Oracle High Availability Services stacks are OFFLINE on the local node.

**See Also:**

"[The Oracle Clusterware Technology Stack](introduction-to-oracle-clusterware.md)" for more information about the Oracle Cluster Ready Services and Oracle High Availability Services stacks

Example I-2 Using OCRCHECK to Obtain OLR Information

    $ ocrcheck -local -config

    Oracle Local Registry configuration is :
            Device/File Name         : /oraclebase/crsdata/dglnx6/olr/dglnx6_19.olr

Example I-3 shows using the `ocrcheck -config -details` command to obtain the location of OCR in an Oracle ASM disk group.

Example I-3 Using OCRCHECK to Obtain OCR Information

    $ ocrcheck -config -details

    Oracle Cluster Registry configuration is :
            Device/File Name         : +ocrvd11/mjk_1/OCRFILE/registry.255.842574113
            Device/File Name         : +ocrdv2/mjk_1/OCRFILE/registry.255.842574125

Example I-4 shows using the `ocrcheck -details` command to obtain a greater level of detail for the OCR configuration.

Example I-4 Using OCRCHECK to Obtain More OCR Information

    $ ocrcheck -details

    Status of Oracle Cluster Registry is as follows :
            Version                  :          4
            Total space (kbytes)     :     409568
            Used space (kbytes)      :      17012
            Available space (kbytes) :     392556
            ID                       :  467263828
            Device/File Name         : +OCRVD11/mycluster/OCRFILE/registry.255.842574113
                                       Device/File integrity check succeeded
            Device/File Name         : +OCRVD2/mycluster/OCRFILE/registry.255.842574125
                                       Device/File integrity check succeeded
                                       Device/File not configured
                                       Device/File not configured
                                       Device/File not configured
            Cluster registry integrity check succeeded
            Logical corruption check succeeded

Example I-5 shows using the `ocrcheck -details` command to obtain backup file information.

Example I-5 Using OCRCHECK to Obtain Backup File Information

    % ocrcheck -backupfile +bkupdg:/sbezawadhtest/OCRBACKUP/backup00.ocr.258.919047805

    Status of backup file is as follows:
    Version : 4
    Used space (kbytes) : 17012
    Device/File Name : +bkupdg:/sbezawadhtest/OCRBACKUP/backup00.ocr.258.919047805
    Device/File integrity check succeeded
    Backup file integrity check succeeded
    Logical corruption check succeeded
    Consistency check of entities managed by Cluster Ready Services succeeded.

OCRCHECK creates a log file in the `ORACLE_BASE``/diag/crs/``host_name``/crs` directory. To change the log level, edit the `ORACLE_BASE``/crsdata/``host_name``/crsdiag/ocrcheck.ini` file. The `ORACLE_BASE`, in this case, is for the Oracle Grid Infrastructure software home.

#### Using the OCRDUMP Utility to View Oracle Cluster Registry Content

The OCRDUMP utility enables you to view OCR and OLR contents by writing the content to a file or `stdout` in a readable format.

This section explains how to use the OCRDUMP utility to view OCR and Oracle Local Registry (OLR) content for troubleshooting.

You can use several options for OCRDUMP. For example, you can limit the output to a key and its descendents. You can also write the contents to an XML file that you can view using a browser. OCRDUMP writes the OCR keys as ASCII strings and values in a data type format. OCRDUMP retrieves header information based on a best effort basis.

OCRDUMP creates a log file in `ORACLE_BASE``/diag/crs/``host_name``/crs`. To change the log level, edit the `ORACLE_BASE``/crsdata/``host_name``/crsdiag/ocrlog.ini` file.

To change the logging component, edit the entry containing the `comploglvl=` entry. For example, to change the log level of the `OCRAPI` component to 3 and to change the log level of the `OCRRAW` component to 5, make the following entry in the `ocrlog.ini` file:

    comploglvl="OCRAPI:3;OCRRAW:5"

**Note:**

Make sure that you have file creation privileges in the `Grid_home` directory before using the OCRDUMP utility.

This section includes the following topics:

- OCRDUMP Utility Syntax and Options

- OCRDUMP Utility Examples

- Sample OCRDUMP Utility Output

##### OCRDUMP Utility Syntax and Options

This section describes the OCRDUMP utility command syntax and usage. Run the `ocrdump` command with the following syntax where `file_name` is the name of a target file to which you want Oracle Database to write the Oracle Cluster Registry output and where `key_name` is the name of a key from which you want Oracle Database to write Oracle Cluster Registry subtree content:

    $ ocrdump [file_name | -stdout] [-local] [-backupfile backup_file_name
    [-keyname key_name] [-xml] [-noheader]
    ]

Table I-2 describes the OCRDUMP utility options and option descriptions.

Table I-2 OCRDUMP Options and Option Descriptions

| Options               | Description                                                                                                                                                                                                                                           |
|:----------------------|:------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `file_name`           | The name of a file to which you want OCRDUMP to write output.<br>By default, OCRDUMP writes output to a predefined output file named `OCRDUMPFILE`. The `file_name` option redirects OCRDUMP output to a file that you specify.                       |
| `-stdout`             | Use this option to redirect the OCRDUMP output to the text terminal that initiated the program.<br>If you do not redirect the output, OCRDUMP writes output to a predefined output file named `OCRDUMPFILE`.                                          |
| `-local`              | Use this option to dump the contents of OLR.                                                                                                                                                                                                          |
| `-backupfile`         | Use this option to view the contents of an OCR backup file. Use the `-local` option with this option to view the contents of an OLR backup file.                                                                                                      |
| `backup_file_name`    | The name of the backup file with the content you want to view. You can query the backups using the `ocrconfig -showbackup` command. If the backup file is located in an Oracle ASM disk group, then ensure that the disk group exists and is mounted. |
| `-keyname` `key_name` | The name of an Oracle Cluster Registry key whose subtree is to be dumped.                                                                                                                                                                             |
| `-xml`                | Use this option to write the output in XML format.                                                                                                                                                                                                    |
| `-noheader`           | Does not print the time at which you ran the command and when the Oracle Cluster Registry configuration occurred.                                                                                                                                     |

##### OCRDUMP Utility Examples

The following `ocrdump` utility examples extract various types of OCR information and write it to various targets:

    ocrdump

Writes OCR content to a file called `OCRDUMPFILE` in the current directory.

    ocrdump MYFILE

Writes OCR content to a file called `MYFILE` in the current directory.

    ocrdump -stdout -keyname SYSTEM

Displays OCR content from the subtree of the key `SYSTEM` in the terminal window.

    ocrdump -stdout -xml

Displays OCR content in the terminal window in XML format.

    ocrdump -stdout -backupfile Grid_home/cdata/cluster_name/file_name

Displays the content of the in the `Grid_home``/cdata/``cluster_name`/`file_name` directory. You must run this command as `root` to be able to view all of the keys. Be sure to name the file appropriately so that it can be recognized by anyone as an OCR backup file, such as `BACKUPOO.ocr`.

##### Sample OCRDUMP Utility Output

The following OCRDUMP examples show the `KEYNAME`, `VALUE TYPE`, `VALUE`, permission set (`user`, `group`, `world`) and access rights for two sample runs of the `ocrdump` command. The following shows the output for the `SYSTEM.language` key that has a text value of `AMERICAN_AMERICA.WE8ASCII37`.

    [SYSTEM.language]
    ORATEXT : AMERICAN_AMERICA.WE8ASCII37
    SECURITY : {USER_PERMISSION : PROCR_ALL_ACCESS, GROUP_PERMISSION : PROCR_READ,
    OTHER_PERMISSION : PROCR_READ, USER_NAME : user, GROUP_NAME : group}

The following shows the output for the `SYSTEM.version` key that has integer value of `3`:

    [SYSTEM.version]
    UB4 (10) : 3
    SECURITY : {USER_PERMISSION : PROCR_ALL_ACCESS, GROUP_PERMISSION : PROCR_READ,
    OTHER_PERMISSION : PROCR_READ, USER_NAME : user, GROUP_NAME : group}
