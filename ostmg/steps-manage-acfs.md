This topic provides an overview of the basic steps when managing Oracle ACFS file systems using command-line utilities.

The examples in this section show operating system commands that are run in a Linux environment system. ASMCMD commands manage the Oracle ADVM volumes, but you can also use SQL\*PLus and Oracle ASM Configuration Assistant (ASMCA) to manage volumes.

This section contains these topics:

- About Using Oracle ACFS Command-Line Tools

- Creating an Oracle ACFS File System

- Accessing an Oracle ACFS File System on a Different Node in the Cluster

- Managing Oracle ACFS Snapshots

- Securing Oracle ACFS File Systems

- Encrypting Oracle ACFS File Systems

- Tagging Oracle ACFS File Systems

- Replicating Oracle ACFS File Systems

- Deregistering, Dismounting, and Disabling Volumes and Oracle ACFS File Systems

- Removing an Oracle ACFS File System and a Volume

### About Using Oracle ACFS Command-Line Tools

This topic provides an overview of the use of Oracle ACFS `acfsutil` commands.

The discussions include:

- Privileges to Run Oracle ACFS acfsutil Commands

- Displaying Help for Oracle ACFS acfsutil Commands

- Running Oracle ACFS acfsutil Commands on Windows

- Displaying Oracle ACFS Version Information

- Managing Trace File Space for acfsutil Commands

#### Privileges to Run Oracle ACFS acfsutil Commands

To run many Oracle ACFS `acfsutil` commands, you must be a system administrator or an Oracle ASM administrator user that has been enabled to run the commands. These privileges are described as follows:

On Non-Windows systems:

- For system administrator privileges, you must be the `root` user.

- For Oracle ASM administrator user privileges, you must belong to the `OSASM` group and the `oinstall` group (for the `OINSTALL` privilege ).

On Windows systems:

- For system administrator privileges, you must belong to the `Administrators` group.

- For Oracle ASM administrator user privileges, you must belong to the `ORA_ASMADMIN` group and the `ORA_CRS_USERS` group.

#### Displaying Help for Oracle ACFS acfsutil Commands

You can display help and usage text for Oracle ACFS `acfsutil` commands with the `h` option. When you include a command or a subcommand with the command, the help and usage display is specific to the command and subcommand entered.

The following example illustrates several different ways to display help and usage text, from the most general to more specific. This example shows the `—h` format to display help on a non-Windows platform. On Windows, use `/h` in place of `—h`.

Example 16-1 Displaying help for Oracle ACFS acfsutil commands

    $ /sbin/acfsutil -h

    $ /sbin/acfsutil -h compress
    $ /sbin/acfsutil compress -h

    $ /sbin/acfsutil -h repl info
    $ /sbin/acfsutil repl info -h

    $ /sbin/acfsutil -h sec admin info
    $ /sbin/acfsutil sec admin info -h

#### Running Oracle ACFS acfsutil Commands on Windows

When the options are specified with Oracle ACFS `acfsutil` commands on a Windows platform, use `/` in place of `-` with the option. For example, you can display help for `acfsutil` commands on a Linux platform with `acfsutil` `-h`. On a Windows platform, use `acfsutil` `/h`.

A mount point on a Windows operating system can be a just the drive letter (`M:`) or a directory including the drive letter (`M:\my_mount_point`).

When an `acfsutil` command on Windows targets the root of the file system that is mounted on a drive letter, include the backslash and a period (`\.`) with the drive letter (`P:\.`) to avoid the possibility of triggering a Windows path substitution to the last accessed path on the specified drive. For example:

    C:\oracle> acfsutil info fs P:\.

#### Displaying Oracle ACFS Version Information

You can run `acfsutil` `version` to display the Oracle ACFS version. For example:

    $ /sbin/acfsutil version
    acfsutil version: 12.2.0.0.3

For more information about displaying Oracle ACFS version details, refer to [acfsutil version](acfs-commands-utilities.md).

#### Managing Trace Files for acfsutil Commands

The Automatic Diagnostic Repository (ADR) generates a separate internal file for each `acfsutil` command invocation to trace the operation of the command. The space consumed by these trace files can increase significantly, and some features, such as snapshot-based replication, may generate a significant number of trace files.

To limit the number of trace files and the space consumed by them, you can set policy attributes with the Automatic Diagnostic Repository Command Interpreter (ADRCI) utility to purge trace files after a specified retention period. ADRCI considers trace files to be short-lived files and the retention period is controlled by the setting of the `SHORTP_POLICY` attribute. You can view the current retention period for these trace files with the ADRCI `show` `control` command.

By default, the short-lived files are retained for `720` hours (30 days). The value in hours specifies the number of hours after creation when a given file is eligible for purging. To limit the number of these files and the space consumed by them, you can update the number of hours set for the `SHORTP_POLICY` retention period, such as `240` hours (10 days).

The following steps summarize how to update the retention period for short-lived trace files. These steps should be performed on each node where features like replication will be active.

- Start the Automatic Diagnostic Repository Command Interpreter (ADRCI) utility.

  `$ adrci`

- Display the ADR home directory paths (ADR homes):

  `ADRCI> show homes`

- If more than one home is shown, then set the appropriate home for the trace files you want to administer:

  `ADRCI> set homepath ``my_specified_homepath`

- Display the current configuration values.

  `ADRCI> show control`

- Update a specific ADRCI configuration value. For example, set `SHORTP_POLICY` to `240` hours (10 days).

  In the displayed `show control` output, check the value of the `SHORTP_POLICY` attribute, which is the retention period in hours for short-lived files. If necessary, set a new retention period for short-lived trace files with the following:

  `ADRCI> set control (SHORTP_POLICY=240)`

If you want to start an immediate purge of the trace files in the current ADR home path, you can use the following command:

`ADRCI> purge -type TRACE -age ``number_of_minutes`

The value number_of_minutes controls which files are purged based on the age of the files. Files older than the specified number of minutes are targeted for the purge operation. Note that automated purges of files in ADR occur on a fixed schedule that is not affected by changes in retention period. In other words, changing the retention period changes how soon after creation files are eligible to be purged, but does not change when a purge occurs. To force a purge, you must request it manually.

**See Also:**

- [About Privileges for Oracle ASM](authenticate-access-asm-instance.md) for information about user privileges for Oracle ASM

- [Oracle Database Utilities](../sutil/oracle-adr-command-interpreter-adrci.md) for information about the Automatic Diagnostic Repository Command Interpreter (ADRCI) utility

### Creating an Oracle ACFS File System

You can create an Oracle ACFS file system using the steps in this topic.

To create and verify a file system, perform the following steps:

1.  Create an Oracle ADVM volume in a mounted disk group with the ASMCMD `volcreate` command.

    The compatibility parameters `COMPATIBLE.ASM` and `COMPATIBLE.ADVM` must be set to `11.2` or higher for the disk group to contain an Oracle ADVM volume. To use Oracle ACFS encryption, replication, security, or tagging, the disk group on which the volume is created for the file system must have compatibility attributes for `ASM` and `ADVM` set to `11.2.0.2` or higher.

    Start ASMCMD connected to the Oracle ASM instance. You must be a user in the OSASM operating system group.

    When configuring Oracle ADVM volume devices within a disk group, Oracle recommends assigning the Oracle Grid Infrastructure user and Oracle ASM administrator roles to users who have root privileges.

    To create a volume:

        ASMCMD [+] > volcreate -G data -s 10G volume1

    When creating an Oracle ADVM volume, a volume device name is created that includes a unique Oracle ADVM persistent disk group number. The volume device file functions in the same manner as any other disk or logical volume to mount file systems or for applications to use directly.

    The format of the volume name is platform-specific.

2.  Determine the device name of the volume that was created.

    You can determine the volume device name with the ASMCMD `volinfo` command or from the `VOLUME_DEVICE` column in the `V$ASM_VOLUME` view.

    For example:

        ASMCMD [+] > volinfo -G data volume1
        Diskgroup Name: DATA

                 Volume Name: VOLUME1
                 Volume Device: /dev/asm/volume1-123
                 State: ENABLED
             ...

        SQL> SELECT volume_name, volume_device FROM V$ASM_VOLUME
             WHERE volume_name ='VOLUME1';

        VOLUME_NAME        VOLUME_DEVICE
        -----------------  --------------------------------------
        VOLUME1            /dev/asm/volume1-123

3.  Create a file system with the Oracle ACFS `mkfs` command.

    Create a file system using an existing volume device.

    For example:

        $ /sbin/mkfs -t acfs /dev/asm/volume1-123
        mkfs.acfs: version                   = 19.0.0.0.0
        mkfs.acfs: on-disk version           = 46.0
        mkfs.acfs: volume                    = /dev/asm/volume1-123
        mkfs.acfs: volume size               = 10737418240  (   10.00 GB )
        mkfs.acfs: Format complete.

    The `root` privilege is not required to run `mkfs`. The ownership of the volume device file dictates who can run this command.

4.  Register the file system.

    In an Oracle Grid Infrastructure Clusterware configuration, you can run the `srvctl` `add` `filesystem` command to register and automount a file system. For example:

        # srvctl add filesystem -device /dev/asm/volume1-123 -path /acfsmounts/acfs1
               -user user1,user2,user3 -mtowner sysowner -mtgroup sysgrp -mtperm 755

    You can also register a file system with the `acfsutil` `registry` command. For example:

        $ /sbin/acfsutil registry -a /dev/asm/volume1-123 /acfsmounts/acfs1

    After registering an Oracle ACFS file system in the cluster mount registry, the file system is mounted automatically on each cluster member listed in the registry entry during the next registry check action. This automatic process runs every 30 seconds and eliminates the requirement to manually mount the file system on each member of the cluster. Registering an Oracle ACFS file system also causes the file system to be mounted automatically whenever Oracle Clusterware or the system is restarted.

    **Note:**

    - The `srvctl` `add` `filesystem` command is required when an Oracle Database home is installed on an Oracle ACFS file system. In this case, the file system should not be explicitly added to the registry with the Oracle ACFS registration command (`acfsutil` `registry`).
    - Oracle ACFS registration is not supported in an Oracle Restart (standalone) configuration, which is a single-instance (non-clustered) environment.
    - The `root` or `asmadmin` privileges are required to modify the registry. The Windows `Administrator` privilege is equivalent to the `root` privilege on Linux.

5.  Mount or start the file system.

    If you have previously registered the file system, then start the file system with SRVCTL. For example:

        $ srvctl start filesystem -device /dev/asm/volume1-123

    If you have not previously registered the file system, then mount the file system with the Oracle ACFS `mount` command. For example:

        # /bin/mount -t acfs /dev/asm/volume1-123 /acfsmounts/acf1

    After an unregistered file system has been mounted, ensure that the permissions are set to allow access to the file system for the appropriate users. For example:

        # chown -R oracle:dba /acfsmounts/acfs1

    The `root` privilege is required to run the `mount` command and the Windows `Administrator` privilege is required to run the `acfsmountvol` command.

6.  Create a test file in the file system.

    The user that creates the test file should be a user that is intended to access the file system. This test ensures that the appropriate user can write to the file system.

    For example:

        $ echo "Oracle ACFS File System" > /acfsmounts/acfs1/myfile

7.  List the contents of the test file that was created in the file system.

    For example:

        $ cat /acfsmounts/acfs1/myfile
        Oracle ACFS File System

**See Also:**

- [Disk Group Compatibility Attributes](diskgroup-compatibility.md) for information about disk group compatibility settings.
- [About Privileges for Oracle ASM](authenticate-access-asm-instance.md) for information about operating system groups and privileges
- [mkfs](acfs-commands-linux.md) (Linux environments) or [acfsformat](acfs-commands-windows.md) (Windows) for information about commands to create an Oracle ACFS file system
- [Managing Oracle ADVM with ASMCMD](manage-advm-asmcmd.md) for information about the `volcreate` command and the `volinfo` command
- [acfsutil registry](acfs-commands-utilities.md) for information about the `acfsutil` `registry` command to register an Oracle ACFS file system
- [About the Oracle ACFS Mount Registry](understand-acfs-concepts.md) for about information registering an Oracle ACFS file system
- [mount](acfs-commands-linux.md) (Linux environments) or [acfsmountvol](acfs-commands-windows.md) (Windows) for information about commands to mount an Oracle ACFS file system
- [Oracle Database Reference](../refrn/V-ASM_VOLUME.md) for information about the `V$ASM_VOLUME` view
- [Oracle Clusterware Administration and Deployment Guide](../cwadd/server-control-command-reference.md) for information about Server Control Utility (SRVCTL) commands

### Accessing an Oracle ACFS File System on a Different Node in the Cluster

If the node is part of a cluster, perform the following steps on node 2 to view the test file you created on node 1.

**Note:**

If the file system has been registered with the Oracle ACFS mount registry, you can skip steps 1 to 3.

1.  Enable the volume that was previously created and enabled on node 1.

    Start ASMCMD connected to the Oracle ASM instance. You must be a user in the OSASM operating system group.

    For example:

        ASMCMD [+] > volenable -G data volume1

2.  View information about the volume that you created on node 1.

    For example:

        ASMCMD [+] > volinfo -G data volume1

3.  Mount the file system using the Oracle ACFS `mount` command.

    For example:

        # /bin/mount -t acfs /dev/asm/volume1-123 /acfsmounts/acfs1

    The `root` privilege is required run the `mount` command and the Windows `Administrator` privilege is required to run the `acfsmountvol` command.

    After the file system has been mounted, ensure that the permissions are set to allow access for the appropriate users.

4.  List the contents of the test file you previously created on the file system.

    For example:

        $ cat /acfsmounts/acfs1/myfile
        Oracle ACFS File System

    The contents should match the file created previously on node 1.

**See Also:**

- [About Privileges for Oracle ASM](authenticate-access-asm-instance.md) for information about operating system groups and privileges.

- [Managing Oracle ADVM with ASMCMD](manage-advm-asmcmd.md)for information about the `volenable` command

- [Managing Oracle ADVM with ASMCMD](manage-advm-asmcmd.md)for information about the `volinfo` command

- [mount](acfs-commands-linux.md) (Linux environments) or [acfsmountvol](acfs-commands-windows.md) (Windows) for information about commands to mount Oracle ACFS file systems

### Managing Oracle ACFS Snapshots

To create and verify a snapshot on node 1:

1.  Create snapshot of the new file system created on node 1.
    For example:

        $ /sbin/acfsutil snap create mysnapshot_20090725 /acfsmounts/acfs1

    See "[acfsutil snap create](acfs-commands-snapshots.md)".
2.  Update the test file in the file system so that it is different than the snapshot.
    For example:

        $ echo "Modifying a file in Oracle ACFS File System" > /acfsmounts/acfs1/myfile
3.  List the contents of the test file and the snapshot view of the test file.
    For example:

        $ cat /acfsmounts/acfs1/myfile

        $ cat /acfsmounts/acfs1/.ACFS/snaps/mysnapshot_20090725/myfile

    The contents of the test file and snapshot should be different. If node 1 is in a cluster, then you can perform the same list operation on node 2.

### Securing Oracle ACFS File Systems

The basic operations to manage security for an Oracle ACFS file system on Linux are discussed in this topic.

The scenario in this topic shows how to use Oracle ACFS security to ensure that only the maintenance user can access medical history files during the maintenance period. Oracle ACFS encryption is also enabled on the same file system.

In this scenario, the disk group on which the volume is created for the file system has compatibility attributes for `ASM` and `ADVM` set to `11.2.0.3` or higher.

For the examples in this section, various operating system users, operating system groups, and directories must exist.

The basic steps to manage security are:

1.  Initialize security for Oracle ACFS.

    Run the `acfsutil` `sec` `init` command to configure storage for security credentials and identify an operating system user as the first security administrator and the operating system security group. The security administrator must belong to the operating system group. This command must be run before any other security command and requires root or Windows `Administrator` privileges to run.

    The `acfsutil` `sec` `init` command is only run once to set up Oracle ACFS security for each cluster and can be run from any node in the cluster. Other security commands can also be run from any node in a cluster. Security administrators are common for all Oracle ACFS file systems in a cluster.

    For example, the following command initializes security for a cluster and creates the first security administrator (`medHistAdmin1`).

        # /sbin/acfsutil sec init -u medHistAdmin1 -g medHistAdminGrp

    The `medHistAdmin1` security administrator must belong to the `medHistAdminGrp` operating system group. That group is identified as the security group for the security administrators.

    When the root user or Windows `Administrator` user runs the command, the user assigns a security password to the security administrator. Security administrators can change their password with the `acfsutil` `sec` `admin` `password` command.

    All `acfsutil` `sec` commands (other than `acfsutil` `sec` `init`) must be run by an Oracle ACFS security administrator and the administrator is prompted for the security administrator's password when each command is run.

    **Note:**

    When prompting for the security administrator's password, the following text displays: `Realm` `management` `password`

    The password required is the Oracle ACFS security administrator's password, not the operating system password of the user.

    Security administrators are allowed to browse all directories in an Oracle ACFS file system whether they have the underlying operating system permissions and whether any realm checks allow it. This functionality enables a security administrator to check the location of the files when securing them with Oracle ACFS security realms. However, a security administrator cannot view the contents of individual files without the appropriate operating system and security realm permissions.

2.  Add additional security administrators as necessary.

    The first security administrator can add additional security administrators to administer Oracle ACFS security with the `acfsutil` `sec` `admin` `add` command.

    For example, add a new security administrator `medHistAdmin2`.

        $ /sbin/acfsutil sec admin add medHistAdmin2

    The `medHistAdmin2` user must belong to the operating system group (`medHistAdminGrp`) identified as the security administrator group with the `acfsutil` `sec` `init` command.

    The `medHistAdmin2` security administrator should change the assigned temporary security password with the `acfsutil` `sec` `admin` `password` command. The `medHistAdmin2` administrator can add new security administrators.

3.  Prepare an Oracle ACFS file system for security.

    Run the `acfsutil` `sec` `prepare` on an Oracle ACFS file system before adding any security realms.

    For example, prepare the Oracle ACFS file system mounted on `/acfsmounts/acfs1` for Oracle ACFS security.

        $ /sbin/acfsutil sec prepare -m /acfsmounts/acfs1

    By default, security is enabled for a file system after running this command. You can explicitly disable or enable security with the `acfsutil` `sec` `disable` or `acfsutil` `sec` `enable` commands.

    This command automatically creates several security realms, such as the `SYSTEM_BackupOperators` security realm. Administrators can add users to the `SYSTEM_BackupOperators` realm which gives those users permissions to make backups of realm-secured files in the Oracle ACFS file system.

4.  Provide encryption for this file system.

    Encrypting the file system is optional, but is enabled in this scenario.

    1.  First, run the `acfsutil` `encr` `init` command to initialize encryption and create the storage necessary for the encryption keys. This command must be run one time for each cluster on which encryption is set up.

        For example, the following command initializes encryption for a cluster.

            # /sbin/acfsutil encr init

        This command must be run before any other encryption command and requires root or administrator privileges to run.

    2.  Next, run the `acfsutil` `encr` `set` command to set encryption for the Oracle ACFS file system.

        For example, the following command sets encryption for the file system mounted on the `/acfsmounts/acfs1` directory.

            # /sbin/acfsutil encr set -m /acfsmounts/acfs1/

        The `acfsutil` `encr` `set` command transparently generates a volume encryption key which is stored in the key store that was previously configured with the `acfsutil` `encr` `init` command. This command requires root or administrator privileges to run.

5.  Create a security realm on the file system.

    Run the `acfsutil` `sec` `realm` `create` command to create a security realm for a file system.

    For example, create a security realm named `medHistRealm` which contains medical records files with all files encrypted in the realm.

        $ /sbin/acfsutil sec realm create medHistRealm -m /acfsmounts/acfs1/
                                                       -e on -a AES -k 128

    The `-e` option specifies that all the files in the realm are encrypted with the `AES` algorithm and the key length set to 128 bits. The file system must first be prepared for encryption with the `acfsutil` `encr` `init` and `acfsutil` `encr` `set` commands. You do not have to enter the same value for the `-k` option with `acfsutil` `sec` `realm` `create` as you have entered with the `acfsutil` `encr` `set` command.

6.  Create security rules.

    Run the `acfsutil` `sec` `rule` `create` command to create rules which determine access to the files and directories of a security realm.

    For example, create rules that can enable the `medMaintenance` user to access medical records for the time period 10 PM to 2 AM for file maintenance. Also, create rules that can deny operations during the time period 8 AM to 9 AM and deny operations to the `medBrowse` user.

        $ /sbin/acfsutil sec rule create medHistRule1a -m /acfsmounts/acfs1/
              -t time 22:00:00,02:00:00 -o ALLOW

        $ /sbin/acfsutil sec rule create medHistRule1b -m /acfsmounts/acfs1/
              -t username medMaintenance -o ALLOW

        $ /sbin/acfsutil sec rule create medHistRule1c -m /acfsmounts/acfs1/
              -t time 08:00:00,09:00:00 -o DENY

        $ /sbin/acfsutil sec rule create medHistRule1d -m /acfsmounts/acfs1/
              -t username medBrowse -o DENY

    You can edit rules with the `acfsutil` `sec` `rule` `edit` command.

7.  Create security rule sets and add rules to rule sets.

    Run the `acfsutil` `sec` `ruleset` `create` command to create rule sets to which rules can be added.

    For example, create rule sets named `medRuleSet1` and `medRuleSet2` that include rules for operations on the files and directories of the security `medHistRealm` realm.

        $ /sbin/acfsutil sec ruleset create medRuleSet1 -m /acfsmounts/acfs1/

        $ /sbin/acfsutil sec ruleset create medRuleSet2 -m /acfsmounts/acfs1/

    Add existing rules to the rule sets.

        $ /sbin/acfsutil sec ruleset edit medRuleSet1 -m /acfsmounts/acfs1/
                   -a medHistRule1a,medHistRule1b -o ALL_TRUE

        $ /sbin/acfsutil sec ruleset edit medRuleSet2 –m /acfsmounts/acfs1/
                   -a medHistRule1c,medHistRule1d -o ALL_TRUE

    The `ALL_TRUE` option is the default action, but is added here to emphasize that both rules in each rule set must be true.

8.  Add objects to a security realm.

    Run the `acfsutil` `sec` `realm` `add` command to add objects, such as command rules, rule sets, and files, to a security realm. For example, add the `medRuleSet1` and `medRuleSet2` rule sets and all the files in the `/acfsmounts/acfs1/medicalrecords` directory to the `medHistRealm`.

    When adding a rule set to a realm, the rule set is added with a command rule, such as `DELETEFILE:medRuleSet1`. Only one rule set can be included with each command rule. To display a list of the command rules, use `acfsutil` `sec` `info` with the `-c` option.

    The following `acfsutil` `sec` `realm` `add` command enables the `medMaintenance` user to delete medical records during the time period 10 PM to 2 AM, but blocks writing to files during 8 AM to 9 AM.

        $ /sbin/acfsutil sec realm add medHistRealm -m /acfsmounts/acfs1/
                -l DELETEFILE:medRuleSet1
                -f -r /acfsmounts/acfs1/medicalrecords

    This `acfsutil` `sec` `realm` `add` command prevents the `medBrowse` user from writing or deleting medical records anytime.

        $ /sbin/acfsutil sec realm add medHistRealm -m /acfsmounts/acfs1/
                -l WRITE:medRuleSet2
                -f -r /acfsmounts/acfs1/medicalrecords

    This `acfsutil` `sec` `realm` `add` command adds backup operators to the `SYSTEM_BackupOperators` security realm that was automatically created with the `acfsutil` `sec` `prepare` command.

        $ /sbin/acfsutil sec realm add SYSTEM_BackupOperators -m /acfsmounts/acfs1/
                -G sysBackupGrp

    Users that belong to the `sysBackupGrp` operating system group can now make backups of realm-secured files in the Oracle ACFS file system.

9.  Display security information.

    Run the `acfsutil` `sec` `info` command to display information for a security realm. For example, display security information for the `medHistRealm` realm.

        $ /sbin/acfsutil sec info -m /acfsmounts/acfs1/ –n medHistRealm

    To display the security realms to which a file or a directory belongs, run the `acfsutil` `sec` `info` `file` command. For example:

        $ /sbin/acfsutil sec info file -m /acfsmounts/acfs1/
                                       /acfsmounts/acfs1/medicalrecords

10. Save security metadata as a backup.

    Run the `acfsutil` `sec` `save` command to save the security metadata of a file system.

    For example, save the security metadata of the `/acfsmounts/acfs1` file system to the `acfs1_backup.xml` file.

        $ /sbin/acfsutil sec save –m /acfsmounts/acfs1
                                  –p acfs1_backup.xml

    The `acfs1_backup.xml` security metadata backup file is saved in the `/acfsmounts/acfs1/.Security/backup/` directory. The saved XML file can be loaded with the `acfsutil` `sec` `load` command.

You can run some `acfsutil` `sec` commands in a batch file with the `acfsutil` `sec` `batch` command. For example, you could create a batch file that contains a group of `acfsutil` `sec` `rule` and `acfsutil` `sec` `ruleset` commands.

Auditing and diagnostic data for Oracle ACFS security is saved to log files.

**See Also:**

- [Oracle ACFS Security](understand-acfs-admin.md) for more information about Oracle ACFS security, including security log files

- [Disk Group Compatibility](diskgroup-compatibility.md) for information about disk group compatibility

- [acfsutil sec prepare](acfs-commands-security.md) and [acfsutil sec init](acfs-commands-security.md) for information about commands to set up security

- [acfsutil sec disable](acfs-commands-security.md) and [acfsutil sec enable](acfs-commands-security.md) for information about commands to enable and disable security

- [acfsutil sec admin add](acfs-commands-security.md) and [acfsutil sec admin password](acfs-commands-security.md)for information about commands to manage security administration

- [acfsutil encr init](acfs-commands-encryption.md) and [acfsutil encr set](acfs-commands-encryption.md) for information about commands to manage encryption

- [acfsutil sec realm create](acfs-commands-security.md), [acfsutil sec realm add](acfs-commands-security.md), and [acfsutil sec realm delete](acfs-commands-security.md)for information about commands to manage security realms

- [acfsutil sec rule create](acfs-commands-security.md) and [acfsutil sec rule edit](acfs-commands-security.md) for information about commands to manage security rules

- [acfsutil sec ruleset create](acfs-commands-security.md) and [acfsutil sec ruleset edit](acfs-commands-security.md) for information about commands to manage security rule sets

- [acfsutil sec info](acfs-commands-security.md) and [acfsutil sec info file](acfs-commands-security.md) for information about commands to display security information

- [acfsutil sec save](acfs-commands-security.md) and [acfsutil sec load](acfs-commands-security.md) for information about commands to load and save security metadata

- [acfsutil sec batch](acfs-commands-security.md) for information about running `acfsutil` `sec` commands in a batch file

### Encrypting Oracle ACFS File Systems

Basic operations to manage encryption on an Oracle ACFS file system on Linux are discussed in this topic.

The examples in this section show a scenario in which the medical history files are encrypted in an Oracle ACFS file system. The steps in this section assume Oracle ACFS security is not configured for the file system; however, you can use both Oracle ACFS security and encryption on the same file system. If you decide to use both security and encryption, then both encryption and security must be initialized for the cluster containing the file system. After security is initialized on the file system, then an Oracle ACFS security administrator runs `acfsutil` `sec` commands to provide encryption for the file system.

Because the `acfsutil` `encr` `set` and `acfsutil` `encr` `rekey` `-v` commands modify the encryption key store, you should back up the Oracle Cluster Registry (OCR) after running these commands to ensure there is an OCR backup that contains all of the volume encryption keys (VEKs) for the file system.

The disk group on which the volume is created for the file system has compatibility attributes for `ASM` and `ADVM` set to `11.2.0.3` or higher.

For the examples in this section, various operating system users, operating system groups, and directories must exist.

The basic steps to manage encryption are:

1.  Initialize encryption.

    Run the `acfsutil` `encr` `init` command to initialize encryption and create the storage necessary for the encryption keys. This command must be run one time for each cluster on which encryption is set up.

    For example, the following command initializes encryption for a cluster.

        # /sbin/acfsutil encr init

    This command must be run before any other encryption command and requires root or administrator privileges to run.

2.  Set encryption parameters.

    Run the `acfsutil` `encr` `set` command to set the encryption parameters for the entire Oracle ACFS file system.

    For example, the following command sets the `AES` encryption algorithm and a file key length of `128` for a file system mounted on the `/acfsmounts/acfs1` directory.

        # /sbin/acfsutil encr set -a AES -k 128 -m /acfsmounts/acfs1/

    The `acfsutil` `encr` `set` command also transparently generates a volume encryption key which is stored in the key store that was previously configured with the `acfsutil` `encr` `init` command.

    This command requires root or administrator privileges to run.

3.  Enable encryption.

    Run the `acfsutil` `encr` `on` command to enable encryption for directories and files.

    For example, the following command enables encryption recursively on all files in the `/acfsmounts/acfs1/medicalrecords` directory.

        # /sbin/acfsutil encr on -r /acfsmounts/acfs1/medicalrecords
                                 -m /acfsmounts/acfs1/

    For users that have appropriate permissions to access files in the `/acfsmounts/acfs1/medicalrecords` directory, they can still read the decrypted files.

    This command can be run by an administrator or the file owner.

4.  Display encryption information.

    Run the `acfsutil` `encr` `info` command to display encryption information for directories and files.

        # /sbin/acfsutil encr info -m /acfsmounts/acfs1/
                                   -r /acfsmounts/acfs1/medicalrecords

    This command can be run by an administrator or the file owner.

Auditing and diagnostic data for Oracle ACFS encryption is saved to log files. .

**See Also:**

- [Oracle ACFS Encryption](understand-acfs-admin.md) for more information about Oracle ACFS encryption, including log files

- Securing Oracle ACFS File Systems for information about setting up security with encryption

- [Disk Group Compatibility](diskgroup-compatibility.md) for information about disk group compatibility

- [acfsutil encr init](acfs-commands-encryption.md) for information about initializing encryption

- [acfsutil encr set](acfs-commands-encryption.md) for information about setting encryption parameters

- [acfsutil encr on](acfs-commands-encryption.md) for information about enabling encryption

- [acfsutil encr info](acfs-commands-encryption.md) for information displaying encryption information

### Tagging Oracle ACFS File Systems

The operations to manage tagging on directories and files in an Oracle ACFS file system on Linux are discussed in this topic.

The disk group on which the volume is created for the file system has compatibility attributes for `ASM` and `ADVM` set to `11.2.0.3` or higher.

Oracle ACFS implements tagging with Extended Attributes. There are some requirements when using Extended Attributes that should be reviewed.

The steps to manage tagging are:

1.  Specify tag names for directories and files.

    Run the `acfsutil` `tag` `set` command to set tags on directories or files. You can use these tags to specify which objects are replicated.

    For example, add the `comedy` and `drama` tags to the files in the subdirectories of the `/acfsmounts/repl_data/films` directory.

        $ /sbin/acfsutil tag set -r comedy /acfsmounts/repl_data/films/comedies

        $ /sbin/acfsutil tag set -r drama /acfsmounts/repl_data/films/dramas

        $ /sbin/acfsutil tag set -r drama /acfsmounts/repl_data/films/mysteries

    In this example, the `drama` tag is purposely used twice and that tag is changed in a later step.

    You must have system administrator privileges or be the file owner to run this command.

2.  Display tagging information.

    Run the `acfsutil` `tag` `info` command to display the tag names for directories or files in Oracle ACFS file systems. Files without tags are not be displayed.

    For example, display tagging information for files in the `/acfsmounts/repl_data/films` directory.

        $ /sbin/acfsutil tag info -r /acfsmounts/repl_data/films

    Display tagging information for files with the `drama` tag in the `/acfsmounts/repl_data/films` directory.

        $ /sbin/acfsutil tag info -t drama -r /acfsmounts/repl_data/films

    You must have system administrator privileges or be the file owner to run this command.

3.  Remove and change tag names if necessary.

    Run the `acfsutil` `tag` `unset` command to remove tags on directories or files. For example, unset the `drama` tag on the files in the `mysteries` subdirectory of the `/acfsmounts/repl_data/films` directory to apply a different tag to the subdirectory.

        $ /sbin/acfsutil tag unset -r drama /acfsmounts/repl_data/films/mysteries

    Add the `mystery` tag to the files in the `mysteries` subdirectory of the `/acfsmounts/repl_data/films` directory.

        $ /sbin/acfsutil tag set -r mystery /acfsmounts/repl_data/films/mysteries

    You must have system administrator privileges or be the file owner to run these commands.

**See Also:**

- [Disk Group Compatibility](diskgroup-compatibility.md) for information about disk group compatibility

- [Oracle ACFS Tagging](understand-acfs-admin.md) for information about tagging an Oracle ACFS file system, including requirements for using Extended Attributes in tagging

- [acfsutil tag set](acfs-commands-tagging.md) for information about specifying tag names

- [acfsutil tag info](acfs-commands-tagging.md) for information about displaying tag name and details

- [acfsutil tag unset](acfs-commands-tagging.md) for information about changing and removing tag names

### Replicating Oracle ACFS File Systems

The operations to manage Oracle ACFS snapshot-based replication on an Oracle ACFS file system on Linux are discussed in this topic.

The disk groups on which volumes are created for the primary and standby file systems must have compatibility attributes for `ASM` and `ADVM` set to `12.2` or higher. To use a snapshot as a storage location, or to use replication role reversal, the compatibility attributes for Oracle ASM and Oracle ADVM must be set to `18.0` or higher.

The steps to manage replication are:

1.  Ensure that `ssh` has been configured for replication.

    - Ensure that host keys and user keys for the `ssh` command have been configured on your primary and standby clusters.

    - On Windows, ensure that Cygwin is installed and `ssh` is configured as required for replication.

2.  Ensure that the snapshots needed by replication can be created at all times. At any given point replication, may need to be able to use two concurrent snapshots of the primary location, and one snapshot of the standby location.

3.  Ensure that there is adequate network connectivity between the primary and standby sites. You should verify that the achievable network data transfer rate from primary to standby is substantially larger than the rate of change of data on the primary location.

    One way to estimate network data transfer rate is to start with an observed transfer rate, then reduce it to account for known sources of overhead. For example, you can calculate the elapsed time needed to FTP a 1 GB file from the primary location to the intended standby location, during a period when network usage is low. This provides an estimate of the maximum achievable transfer rate. This rate should be reduced to account for overheads inherent in replication transfers, as well as to allow for other demands on the network. For replication overhead, a reasonable approach is to reduce the measured rate by 20%, then by an additional 5% for each node in the primary cluster.

    To estimate the average rate of change on the primary, you can use the command `acfsutil` `info` `fs` with the `-s` option. This command should be run on each node where the file system that contains the primary location is mounted. The command displays the amount and rate of change to the file system on that node. To compute the total rate of change for the file system, the rate of changed for each node must be aggregated. A reasonable value to use for `-s` is `900`, which would yield a 15 minute sampling interval.

    With the output from `acfsutil` `info` `fs` with the `-s` option, you can determine the average rate of change, the peak rate of change, and how long the peaks last. A conservative approach to using this data is to choose the peak rate of change as the target rate that must be accommodated.

    Because replication must transfer all data changed on the primary to the standby, obviously the achievable network transfer rate must be higher, ideally significantly higher, than the target rate of change on the primary. If this is not the case, you should increase network capacity before implementing replication for this primary location and workload.

    For example, assume you have a four node primary cluster and you determine that a 1 GB file can be transferred in 30 seconds, yielding a current FTP transfer rate of 33 MB per second. An estimate of the current replication transfer rate would be approximately 20 MB per second, calculated as follows:

        33 MB/sec * (1 – 0.2 – (4 * 0.05)) = 33 * 0.6 = ~20 MB/sec

    Also, you find that the average rate of change to the primary is 8 GB per hour, with a peak rate of 25 GB per hour. Using the peak rate, you can calculate a target rate of change of approximately 7 MB per second as follows:

        (25 GB/hour * 1024) / 3600 = ~7 MB/sec

    In the scenario that was discussed in this step, you can reasonably expect the network to be able to handle the additional workload from replication.

4.  Ensure that there is adequate storage capacity on the primary and standby sites.

    Estimate the storage capacity needed for replication on the sites hosting the primary and standby locations. In the general case, the primary site must store two snapshots of the primary location on an ongoing basis and the standby site must store a single snapshot of the standby location. The space occupied by these snapshots mostly consists of user data or metadata preserved in the snapshot, that has since been modified which triggers a new copy of the data to be created.

    The space occupied by replication-related snapshots can be directly viewed using the command `acfsutil` `snap` `info`. On the primary, check for snapshots with the names starting with the string `REPL`. On the standby, look for snapshots for names starting with `SDBACKUP`.

    If you use interval-based replication, the `-i` option to `acfsutil` `repl` `init` `primary`, and if the replication operations are successfully completing within the specified interval, then the size of replication-related snapshots is related to the rate of change of the primary and the length of the interval. For example, with an average rate of change of 8 GB per hour and a two hour replication interval, you would expect that snapshot storage usage is in the range of 16 GB per snapshot.

    Snapshot size does vary with the rate of change of the primary. Another factor is that snapshot size depends in part on the number of files in the file system, as well as the rate of change. Potentially more importantly, if you use constant mode replication, the `-C` option to `acfsutil` `repl` `init` `primary`, or if replication operations are not completing successfully in the interval given with interval—based replication because the interval is too small, the size of replication-related snapshots is difficult to predict in advance. In these cases, observe the size of the snapshots being generated over time and adjust the file system size as needed with the `acfsutil` `size` command to accommodate normal storage needs in addition in the presence of the snapshots. When collecting this information, a good starting point is to accommodate space for the snapshots to contain the data that is multiple times larger than the collection period, at the average rate of change of the primary.

    While collecting this information, choose a conservative starting point for the amount of space to allow for replication snapshots. For example, you can compute the space needed to store changes to the file system over the collection period as described previously, then you can allocate several times that space for future snapshots.

5.  Determine the user to be employed for replication and optionally set up tags.

    Choose or create the replication user who logs in with `ssh` to the standby cluster to apply data replicated from the primary location to the standby location. This user is defined only at the OS level and not within Oracle. The user should belong to the groups defined for Oracle AM administrator access.

    **Note:**

    The same user and group identities (including all `uids` and `gids`) must be specified for the replication user on both your primary cluster and your standby cluster.

    Optionally set tags on directories and files to replicate only selected files in an Oracle ACFS primary location. You can also add tags to files after replication has started.

6.  Configure the site hosting the standby location.

    Before replicating an Oracle ACFS a primary storage location, configure the site hosting the standby location by performing the following:

    - To use the file system as a standby location, create a new standby file system of adequate size to hold the files replicated from the primary location, as well as a single replication snapshot, and mount the file system. For example:

      `/standby/repl_data`

    - To use a snapshot of an existing file system as a standby location, create a new read-write snapshot, and ensure that the file system is of adequate size to hold the files replicated from the primary location, as well as a single replication snapshot.

    - For either kind of standby location, run the `acfsutil` `repl` `init` `standby` command on the site hosting the standby location. For example:

          # /sbin/acfsutil repl init standby -u repluser /standby/repl_data

      **Note:**

      If the `acfsutil` `repl` `init` `standby` command is interrupted for any reason, the user must re-create the file system or snapshot used for the location, re-mount the file system if needed, and re-run the command.

      This command requires the name of the replication user and the standby location. The specified user is the user under which `ssh`, invoked from the primary cluster, logs in to the standby cluster to apply changes. This user is specified with the -u option. For example: `-u ``repluser`.

      If the standby location is a file system, it is named with its mount point. For example: `/standby/repl_data`.

      If the standby location is a read-write snapshot, it is named with the snapshot name and the mount point of the containing file system, with the two separated by the `@` character. For example: `drsnap1101@/standby/repl_data`.

    The `acfsutil` `repl` `init` `standby` command requires `root` or system administrator privileges to run.

7.  After the standby location has been set up, configure the site hosting the primary location and start replication.

    Run the `acfsutil` `repl` `init` `primary` command on the site hosting the primary location. For example:

        $ /sbin/acfsutil repl init primary -i 2h -s repluser@standby12_vip -m /standby/repl_data /acfsmounts/repl_data

    This command requires the following configuration information.

    - A replication interval, given with the option -i interval for interval mode or the option -C for constant mode replication. If an interval is specified, the option value is the minimum amount of time that elapses between replication operations. At the start of each operation, replication takes a new snapshot of the primary and compares it to the previous snapshot, if any. The changes needed to update the standby to match the primary are then sent to the standby. If -C is given instead of -i interval, a new replication operation is started as soon as the previous one completes.

      For example, to set up a replication interval of two hours, specify `-i 2h`.

    - The user name and network endpoint (VIP name or address, or host name or address) to be used to connect to the site hosting the standby location, specified with the `—s` option. For example: `-s repluser@standby12_vip`

    - If the primary location is a file system, then specify the name of the mount point of the file system. For example: `/acfsmounts/repl_data`

    - If the primary storage location is a snapshot, then specify the snapshot name plus the mount point of the containing file system, the two separated by the `@` character. For example:  `drsnap1101@/acfsmounts/repl_data`

    - If the mount point, or snapshot name with the mount point, is different on the site hosting the standby location than it is on the site hosting the primary location, then specify the name of the standby location with the `-m` option. For example: `-m /standby/repl_data`

    The `acfsutil` `repl` `init` `primary` command requires `root` or system administrator privileges to run.

8.  Monitor information about replication on the location.

    The `acfsutil` `repl` `info` command displays information about the state of the replication processing on the primary or standby location.

    For example, you can run the following on the site hosting the primary location to display configuration information.

        $ /sbin/acfsutil repl info -c -v /acfsmounts/repl_data

    You must have system administrator (the user root on non-Windows systems or local `SYSTEM` on Windows) or Oracle AM administrator privileges to run this command.

9.  Manage the replication background process.

    Run the `acfsutil` `repl` `bg` command to start, stop, or retrieve information about the replication background process.

    For example, run the following command to display information about the replication process for the `/acfsmounts/repl_data` file system.

        $ /sbin/acfsutil repl bg info /acfsmounts/repl_data

    You must have system administrator or Oracle AM administrator privileges to run the `acfsutil` `repl` `bg` `info` command.

10. Pause replication momentarily if necessary.

    Run the `acfsutil` `repl` `pause` to momentarily stop replication. Run the `acfsutil` `repl` `resume` command as soon as possible to resume replication.

    For example, the following command pauses replication on the `/acfsmounts/repl_data` file system.

        $ /sbin/acfsutil repl pause /acfsmounts/repl_data

    The following command resumes replication on the `/acfsmounts/repl_data` file system.

        $ /sbin/acfsutil repl resume /acfsmounts/repl_data

    You must have system administrator or Oracle AM administrator privileges to run the `acfsutil` `repl` `pause` and `acfsutil` `repl` `resume` commands.

11. Failing over to a standby or turning a standby location into an active location.

    If the primary location is inaccessible, you can run `acfsutil` `repl` `terminate` `standby` command to turn the standby location into read-write storage. If the primary location still exists, you should terminate the primary first with the `acfsutil` `repl` `terminate` `primary` command.

    Before terminating replication with `acfsutil` `repl` `terminate` `standby` on the standby location, you can determine the point in time of the primary location that the standby location represents. This timestamp is displayed with `acfsutil` `repl` `info` `-c` as `Last` `sync` `time` `with` `primary`. If the failover action must be coordinated with Oracle Data Guard, you can use the timestamp to set back the database if needed, or perform other necessary actions that are based on the timestamp.

    The standby location may be in the process of being modified by replication. This could occur if:

    - The primary location is available and a replication operation is currently in progress.

    - The primary location is not available, but a replication operation was in progress when it became unavailable.

    To be sure of obtaining the contents of the standby location when it was last identical to a snapshot from the primary, follow one of these procedures.

    - If the primary location is available, run the `acfsutil` `repl` `terminate` `primary` command on the primary site to terminate replication. The command waits for any in-progress replication operation to complete before it returns. Then run `acfsutil` `repl` `info` `-c` to determine the point in time of the primary location represented on the standby. After you have this information, run `acfsutil` `repl` `terminate` `standby` on the standby site.

    - If the primary location is not available, you should first compare two date strings from the `acfsutil` `repl` `info` `-c` output; these are the dates from the `Receiving primary as of` line and the `Last` `sync` `time` `with` `primary` line. If these dates are identical, then the standby location contains the most recent available point-in-time image of the primary. If they are not equal, you must use the backup snapshot recorded by replication to recover the last point-in-time image captured on the standby. When both the primary location and the standby location are file systems, you can find this snapshot using the `acfsutil` `snap` `info` command. Search for a snapshot with a name of the form:

          SDBACKUP_tstamp1_REPL_0_tstamp2_0

      where `tstamp1` represents the time at which the backup snapshot was created, and `tstamp2` represents the point in time when the primary contents in this snapshot were recorded. There should be only one backup snapshot present. The date of the backup snapshot corresponds to the date in the `Last` `sync` `time` `with` `primary` line output by `acfsutil` `repl` `info` `-c`. If there is no backup snapshot available, then the contents of the primary were never successfully transferred to the standby.

      The date of the backup snapshot corresponds to the date in the `Last` `sync` `time` `with` `primary` line output by `acfsutil` `repl` `info` `-c`.

      To use the backup snapshot, you must terminate replication and ensure that the snapshot is preserved because it is deleted by default. To ensure the snapshot is preserved, add the `-k` option to the command line for `acfsutil` `repl` `terminate` `standby`. After replication has been terminated, you optionally can run the `acfsutil` `snap` `remaster` command to use the snapshot as the new contents of the standby file system.

**Note:**

When replication is in use, replication snapshots can be viewed using the `acfsutil` `snap` `info` command, just as any other snapshot can. You can use this command to get an approximate idea of the space currently occupied by replication snapshots.

**See Also:**

- [Oracle ACFS Replication](understand-acfs-admin.md) for information about replicating Oracle ACFS file systems or snapshots

- [Disk Group Compatibility](diskgroup-compatibility.md) for information about disk group compatibility

- [Configuring ssh for Use With Oracle ACFS Replication](configure-acfs-replication.md) and [Installing ssh and Cygwin on Windows](configure-acfs-replication.md) for information about configuring replication

- [acfsutil repl init](acfs-commands-replication.md) for information initiating replication

- [About Privileges for Oracle ASM](authenticate-access-asm-instance.md) for information about user privileges for Oracle AM

- [acfsutil repl bg](acfs-commands-replication.md) for more information about managing replication background operations

- [acfsutil repl pause](acfs-commands-replication.md) and [acfsutil repl resume](acfs-commands-replication.md) for more information about pausing and resuming replication operations

- [acfsutil repl info](acfs-commands-replication.md) for information about displaying replication details

- Creating an Oracle ACFS File System for information about creating a file system

- Tagging Oracle ACFS File Systems for information about the steps to tag files

### Deregistering, Dismounting, and Disabling Volumes and Oracle ACFS File Systems

This topic discusses the operations to deregister or dismount a file system and disable a volume.

#### Deregistering an Oracle ACFS File System

You can deregister an Oracle ACFS file system if you do not want the file system to be automatically mounted.

For example:

    $ /sbin/acfsutil registry -d /acfsmounts/acfs1

If you deregister a file system, then you must explicitly mount the file system after Oracle Clusterware or the system is restarted.

For more information about the registry, refer to [About the Oracle ACFS Mount Registry](understand-acfs-concepts.md). For information about `acfsutil` `registry`, refer to [acfsutil registry](acfs-commands-utilities.md).

#### Dismounting an Oracle ACFS File System

You can dismount a file system without deregistering the file system or disabling the volume on which the file system is mounted.

For example, you can dismount a file system and run `fsck` to check the file system.

    # /bin/umount /acfsmounts/acfs1

    # /sbin/fsck -a -v -y -t acfs /dev/asm/volume1-123

After you dismount a file system, you must explicitly mount the file system.

Use `umount` on Linux systems or `acfsdismount` on Windows systems. For information about the commands to dismount a file system, refer to [umount](acfs-commands-linux.md) or [acfsdismount](acfs-commands-windows.md).

Use `fsck` on Linux systems or `acfschkdsk` on Windows systems to check a file system. For information about the commands to check a file system, refer to [fsck (offline mode)](acfs-commands-linux.md) or [acfschkdsk](acfs-commands-windows.md).

#### Disabling a Volume

To disable a volume, you must first dismount the file system on which the volume is mounted.

For example:

    # /bin/umount /acfsmounts/acfs1

After a file system is dismounted, you can disable the volume and remove the volume device file.

For example:

    ASMCMD> voldisable -G data volume1

Dismounting the file system and disabling a volume does not destroy data in the file system. You can enable the volume and mount the file system to access the existing data. For information about `voldisable` and `volenable`, refer to [Managing Oracle ADVM with ASMCMD](manage-advm-asmcmd.md).

### Removing an Oracle ACFS File System and a Volume

You can remove an Oracle ACFS file system and volume with `acfsutil` and ASMCMD commands.

To permanently remove a volume and Oracle ACFS file system, perform the following steps. These steps destroy the data in the file system.

1.  Deregister the file system with `acfsutil` `registry` `-d`.

    For example:

        $ /sbin/acfsutil registry -d /acfsmounts/acfs1
        acfsutil registry: successfully removed ACFS mount point
           /acfsmounts/acfs1 from Oracle Registry

2.  Dismount the file system.

    For example:

        # /bin/umount /acfsmounts/acfs1

    You must dismount the file system on all nodes of a cluster.

    Use `umount` on Linux systems or `acfsdismount` on Windows systems.

3.  Remove the file system with `acfsutil` `rmfs`.

    If you were not planning to remove the volume in a later step, this step is necessary to remove the file system. Otherwise, the file system is removed when the volume is deleted.

    For example:

        $ /sbin/acfsutil rmfs /dev/asm/volume1-123

4.  Optionally you can disable the volume with the ASMCMD `voldisable` command.

    For example:

        ASMCMD> voldisable -G data volume1

5.  Delete the volume with the ASMCMD `voldelete` command.

    For example:

        ASMCMD> voldelete -G data volume1

**See Also:**

- [acfsutil registry](acfs-commands-utilities.md) for information about running `acfsutil` `registry`

- [umount](acfs-commands-linux.md) or [acfsdismount](acfs-commands-windows.md) for information about running the `umount` or `acfsdismount` commands

- [acfsutil rmfs](acfs-commands-utilities.md) for information about running the `acfsutil` `rmfs` command

- [Managing Oracle ADVM with ASMCMD](manage-advm-asmcmd.md) for information about running the `voldisable` command

- [Managing Oracle ADVM with ASMCMD](manage-advm-asmcmd.md) for information about running the `voldelete` command
