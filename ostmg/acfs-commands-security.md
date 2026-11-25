This topic provides a summary of the commands for Oracle ACFS security.

Table 16-52 lists the Oracle ACFS security commands with brief descriptions. For an overview of Oracle ACFS security, refer to [Oracle ACFS Security](understand-acfs-admin.md).

For more information about running Oracle ACFS `acfsutil` commands, refer to [About Using Oracle ACFS Command-Line Tools](steps-manage-acfs.md).

**Note:**

Starting with Oracle ACFS 19c (19.5), Oracle ACFS Security (Vault) and ACFS Auditing are deprecated. Deprecating certain clustering features with limited adoption enables Oracle to focus on improving core scaling, availability, and manageability across all features and functionality. Oracle ACFS Security (Vault) and Oracle ACFS Auditing are deprecated, and can be desupported in a future release.

Table 16-52 Summary of commands for Oracle ACFS security

| Command                          | Description                                                                         |
|:---------------------------------|:------------------------------------------------------------------------------------|
| acfsutil sec admin add           | Adds a security administrator.                                                      |
| acfsutil sec admin info          | Lists the Oracle ACFS security administrators.                                      |
| acfsutil sec admin password      | Changes the password of a security administrator.                                   |
| acfsutil sec admin remove        | Removes a security administrator.                                                   |
| acfsutil sec batch               | Runs a batch file.                                                                  |
| acfsutil sec disable             | Disables Oracle ACFS security.                                                      |
| acfsutil sec enable              | Enables Oracle ACFS security.                                                       |
| acfsutil sec info                | Displays Oracle ACFS file system security information.                              |
| acfsutil sec info file           | Lists the security realms that a specified file or directory belongs to.            |
| acfsutil sec init                | Initializes Oracle ACFS file system security.                                       |
| acfsutil sec load                | Loads Oracle ACFS file system security metadata.                                    |
| acfsutil sec prepare             | Prepares an Oracle ACFS file system for security.                                   |
| acfsutil sec realm add           | Adds objects to an Oracle ACFS file system security realm.                          |
| acfsutil sec realm audit disable | Disables auditing of command rules for files in an Oracle ACFS security realm.      |
| acfsutil sec realm audit enable  | Enables auditing of command rules for files in an Oracle ACFS security realm.       |
| acfsutil sec realm audit info    | Displays the realm auditing information for a specified Oracle ACFS security realm. |
| acfsutil sec realm clone         | Clones an Oracle ACFS file system security realm.                                   |
| acfsutil sec realm create        | Creates an Oracle ACFS file system security realm.                                  |
| acfsutil sec realm delete        | Removes objects from an Oracle ACFS file system security realm.                     |
| acfsutil sec realm destroy       | Removes an Oracle ACFS file system security realm.                                  |
| acfsutil sec rule clone          | Clones an Oracle ACFS file system security rule.                                    |
| acfsutil sec rule create         | Creates an Oracle ACFS file system security rule.                                   |
| acfsutil sec rule destroy        | Removes an Oracle ACFS file system security rule.                                   |
| acfsutil sec rule edit           | Updates an Oracle ACFS file system security rule.                                   |
| acfsutil sec ruleset clone       | Clones an Oracle ACFS file system security rule set.                                |
| acfsutil sec ruleset create      | Creates an Oracle ACFS file system security rule set.                               |
| acfsutil sec ruleset destroy     | Removes an Oracle ACFS file system rule set.                                        |
| acfsutil sec ruleset edit        | Updates an Oracle ACFS file system rule set.                                        |
| acfsutil sec save                | Saves Oracle ACFS file system security metadata.                                    |

### acfsutil sec admin add

#### Purpose

Adds a new security administrator for an Oracle ACFS file system.

#### Syntax and Description

    acfsutil sec admin add -h
    acfsutil sec admin add admin

`acfsutil` `sec` `admin` `add` `-h` displays help text and exits.

Table 16-53 contains the options available with the `acfsutil` `sec` `admin` `add` command.

Table 16-53 Options for the acfsutil sec admin add command

| Option  | Description                                                                                                                                                                                                                                                                                                                                              |
|:--------|:---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `admin` | Specifies a security administrator user name. The user specified must be an existing operating system user and a member of the security group specified with the `acfsutil` `sec` `init` command.<br>On Windows, a security administrator user name must be specified with a fully qualified domain user name in the form of `domain_name``\``username`. |

Security administrators are common for all Oracle ACFS file systems in a cluster. A temporary password must be provided for the new security administrator. The password must conform to the format that is described in "acfsutil sec init".

The new security administrator can change the password with the `acfsutil` `sec` `admin` `password` command. For information, refer to "acfsutil sec admin password".

Security administrators are allowed to browse all directories in an Oracle ACFS file system whether they have the underlying operating system permissions and whether any realm checks allow it. This exception enables a security administrator to check the location of the files when securing them with Oracle ACFS security realms. However, a security administrator cannot view the contents of individual files without the appropriate operating system and security realm permissions.

Only an existing security administrator can run this command.

#### Examples

The following example shows the use of the `acfsutil` `sec` `admin` `add` command.

Example 16-47 Using the acfsutil sec admin add command

    $ /sbin/acfsutil sec admin add sec_admin_three

### acfsutil sec admin info

#### Purpose

Displays a list of the Oracle ACFS security administrators.

#### Syntax and Description

    acfsutil -h sec admin info
    acfsutil sec admin info

`acfsutil` `sec` `admin` `info` `-h` displays help text and exits.

Only a security administrator can run this command.

#### Examples

The following example shows the use of the `acfsutil` `sec` `admin` `info` command.

Example 16-48 Using the acfsutil sec info password command

    $ /sbin/acfsutil sec admin info

### acfsutil sec admin password

#### Purpose

Changes the password of a security administrator for an Oracle ACFS file system.

#### Syntax and Description

    acfsutil sec admin password -h
    acfsutil sec admin password

`acfsutil` `sec` `admin` `password` `-h` displays help text and exits.

The `acfsutil` `sec` `admin` `password` command changes the security password for the administrator that is running the command. When you run this command, you are prompted to enter a new password. The password must conform to the format that is described in "acfsutil sec init".

Every time a security administrator runs an `acfsutil` `sec` command, the administrator is prompted for the security administrator's password.

Only a security administrator can run this command.

#### Examples

The following example shows the use of the `acfsutil` `sec` `admin` `password` command.

Example 16-49 Using the acfsutil sec admin password command

    $ /sbin/acfsutil sec admin password
    ACFS Security administrator password:
    New password:
    Re-enter new password:

### acfsutil sec admin remove

#### Purpose

Removes a security administrator from an Oracle ACFS file system.

#### Syntax and Description

    acfsutil sec admin remove -h
    acfsutil sec admin remove admin

`acfsutil` `sec` `admin` `remove` `-h` displays help text and exits.

Table 16-54 contains the options available with the `acfsutil` `sec` `admin` `remove` command.

Table 16-54 Options for the acfsutil sec admin remove command

| Option  | Description                                                                                                                                                                                               |
|:--------|:----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `admin` | Specifies an existing security administrator user name.<br>On Windows, the security administrator user name must be specified with a fully qualified user name in the form of `domain_name``\``username`. |

Only a security administrator can run this command.

#### Examples

The following example shows the use of the `acfsutil` `sec` `admin` `remove` command.

Example 16-50 Using the acfsutil sec admin remove command

    $ /sbin/acfsutil sec admin remove sec_admin_three

### acfsutil sec batch

#### Purpose

Runs a specified batch file.

#### Syntax and Description

    acfsutil sec batch -h
    acfsutil sec batch batch_file

`acfsutil` `sec` `batch` `-h` displays help text and exits.

Table 16-55 contains the options available with the `acfsutil` `sec` `batch` command.

Table 16-55 Options for the acfsutil sec batch command

| Option       | Description                                                                                         |
|:-------------|:----------------------------------------------------------------------------------------------------|
| `batch_file` | Specifies an existing batch file name. The batch file contains a list of `acfsutil` `sec` commands. |

The batch file can only contain security realm management commands. Interactive commands are not recommended. The `acfsutil` `sec` `admin` `add`, `acfsutil` `sec` `admin` `password`, and `acfsutil` `sec` `init` commands are not supported in the batch file. Also, other `acfsutil` commands, such as `acfsutil` `encr` commands, are not allowed in the batch file. If a command in the batch file fails, subsequent commands in the batch file are not run.

The following are examples of commands that can be in a batch file:

    acfsutil sec realm create my_realm1 -m /mnt1 -e off
    acfsutil sec realm create my_realm2 -m /mnt2 -e off

Only a security administrator can run this command. When the command is run, the administrator is prompted once for a password.

#### Examples

The following example shows the use of the `acfsutil` `sec` `batch` command.

Example 16-51 Using the acfsutil sec batch command

    $ /sbin/acfsutil sec batch my_batch_file

### acfsutil sec disable

#### Purpose

Disables Oracle ACFS security on a mount point or a realm in a mount point.

#### Syntax and Description

    acfsutil sec disable -h
    acfsutil sec disable -m mount_point [-S snap_name] [realm]

`acfsutil` `sec` `disable` `-h` displays help text and exits.

Table 16-56 contains the options available with the `acfsutil` `sec` `disable` command.

Table 16-56 Options for the acfsutil sec disable command

| Option             | Description                                                              |
|:-------------------|:-------------------------------------------------------------------------|
| `-m` `mount_point` | Specifies the directory where the file system is mounted.                |
| `-S` `snap_name`   | Disables security for the specified read-write snapshot.                 |
| `realm`            | Specifies the name of the security realm in the Oracle ACFS file system. |

The `acfsutil` `sec` `disable` `-m` `mount_point` command disables security functionality on the Oracle ACFS file system specified by the mount point option. When security is disabled on the file system, security realms do not enforce realm authorization.

The `acfsutil` `sec` `disable` `-m` `mount_point` `realm` command disables security for the realm specified in the command.

Only a security administrator can run this command.

#### Examples

The following example shows the use of the `acfsutil` `sec` `disable` command.

Example 16-52 Using the acfsutil sec disable command

    $ /sbin/acfsutil sec disable -m /acfsmounts/acfs1 my_realm

### acfsutil sec enable

#### Purpose

Enables Oracle ACFS security on a mount point or a realm in a mount point.

#### Syntax and Description

    acfsutil sec enable -h
    acfsutil sec enable -m mount_point [-S snap_name] [realm]

`acfsutil` `sec` `enable` `-h` displays help text and exits.

Table 16-57 contains the options available with the `acfsutil` `sec` `enable` command.

Table 16-57 Options for the acfsutil sec enable command

| Option             | Description                                               |
|:-------------------|:----------------------------------------------------------|
| `-m` `mount_point` | Specifies the directory where the file system is mounted. |
| `-S` `snap_name`   | Enables security for the specified read-write snapshot.   |
| `realm`            | Specifies the name of the security realm.                 |

The `acfsutil` `sec` `enable` `-m` `mount_point` command enables security functionality on the Oracle ACFS file system specified by the mount point option. When security is enabled on the file system, security realms that have been enabled enforce realm authorization. You should run this command before enabling any individual security realm.

The `acfsutil` `sec` `enable` `-m` `mount_point` `realm` command enables security for the realm specified in the command. The realm enforces authorization if security has been enabled on the file system.

Only a security administrator can run this command.

#### Examples

These example shows the use of the `acfsutil` `sec` `enable` command.

Example 16-53 Using the acfsutil sec enable command

    $ /sbin/acfsutil sec enable -m /acfsmounts/acfs1

    $ /sbin/acfsutil sec enable -m /acfsmounts/acfs1 my_realm

### acfsutil sec info

#### Purpose

Displays information about Oracle ACFS security.

#### Syntax and Description

    acfsutil sec info -h
    acfsutil sec info -m mount_point
         [{-n [realm] | -l [rule] |-s [ruleset] |-c }] [-S snap_name]

`acfsutil` `sec` `info` `-h` displays help text and exits.

Table 16-58 contains the options available with the `acfsutil` `sec` `info` command.

Table 16-58 Options for the acfsutil sec info command

| Option             | Description                                                                                                               |
|:-------------------|:--------------------------------------------------------------------------------------------------------------------------|
| `-m` `mount_point` | Specifies the directory where the file system is mounted.                                                                 |
| `-n` `realm`       | Displays information about the specified security realm. If the realm name is omitted, a list of all realms is displayed. |
| `-l` `rule`        | Displays information about the specified rule. If the rule name is omitted, a list of all rules is displayed.             |
| `-s` `ruleset`     | Displays information about the specified rule set. If the rule set name is omitted, a list of all rule sets is displayed. |
| `-c`               | Lists all the command rules.                                                                                              |
| `-S` `snap_name`   | Displays information about the realms, rules, and rule sets in the specified snapshot.                                    |

The `acfsutil` `sec` `info` command retrieves information about the list of realms, rules, and rule sets on the specified mount point. By specifying a particular realm, rule, or ruleset, you can retrieve information specific about the specified realm, rule, or ruleset. You can also display information about a specified snapshot.

If the `-m` option is specified without any other options, then the security enabled status and prepared status are displayed for the specified mount point.

To access files in the system security realms, the user should be assigned as a security administrator with the `acfsutil` `sec` `admin` `add` command. Only a security administrator can run this command.

#### Examples

The following example shows the use of the `acfsutil` `sec` `info` command.

Example 16-54 Using the acfsutil sec info command

    $ /sbin/acfsutil sec info -m /acfsmounts/acfs1 -n my_realm

### acfsutil sec info file

#### Purpose

Lists the names of the Oracle ACFS security realms that the specified file or directory belongs to.

#### Syntax and Description

    acfsutil sec info file -h
    acfsutil sec info file -m mount_point path

`acfsutil` `sec` `info` `file` `-h` displays help text and exits.

Table 16-59 contains the options available with the `acfsutil` `sec` `info` `file` command.

Table 16-59 Options for the acfsutil sec info file command

| Option             | Description                                                     |
|:-------------------|:----------------------------------------------------------------|
| `-m` `mount_point` | Specifies the directory where the file system is mounted.       |
| `path`             | Specifies the path of the file or directory in the file system. |

This command also displays the encryption status of files.

Only a security administrator can run this command.

#### Examples

The following example shows the use of the `acfsutil` `sec` `info` `file` command.

Example 16-55 Using the acfsutil sec info file command

    $ /sbin/acfsutil sec info file -m /acfsmounts/acfs1
                                      /acfsmounts/acfs1/myfiles

### acfsutil sec init

#### Purpose

Initializes Oracle ACFS security.

#### Syntax and Description

    acfsutil sec init -h
    acfsutil sec init -u admin -g admin_sec_group

`acfsutil` `sec` `init` `-h` displays help text and exits.

Table 16-60 contains the options available with the `acfsutil` `sec` `init` command.

Table 16-60 Options for the acfsutil sec init command

| Option                 | Description                                                                                                                                                                                                                                                                                                                                                             |
|:-----------------------|:------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `-u` `admin`           | Specifies the first security administrator user name. The user specified must be an existing operating system (OS) user and a member of the operating system group specified by the `-g` option.<br>On Windows, the security administrator user name must be specified with a fully qualified user name in the form of `domain_name``\``username`.                      |
| `-g` `admin_sec_group` | Specifies the name of the security group for the administrator. The group specified must be an existing operating system (OS) group.<br>On Windows, the group name must be specified with a fully qualified domain group name in the form of `domain_name``\``groupname`. If the `domain_name``\``groupname` contains a space, then enclose the string in quotes (" "). |

The `acfsutil` `sec` `init` command creates the storage necessary for security credentials and identifies an operating system user as the first security administrator. The command also identifies the operating system group that is the designated security group. All users that are security administrators must be members of the designated security group. Security administrators are common for all Oracle ACFS file systems.

If you are setting up an OS user and OS group, refer to your operating system-specific (OS) documentation for information.

The `acfsutil` `sec` `init` command is run once to set up Oracle ACFS security for each cluster and can be run from any node in the cluster. Other security commands can also be run from any node in a cluster.

Only the root user or Windows `Administrator` user can run this command. The user specifies a password for the security administrator. The security administrator password must conform to the following format:

- The maximum number of characters is 20.

- The minimum number of characters is 8.

- The password must contain at least one digit.

- The password must contain at least one letter.

The new security administrator can change the password with the `acfsutil` `sec` `admin` `password` command. For information, refer to "acfsutil sec admin password".

Security administrators are allowed to browse all directories in an Oracle ACFS file system whether they have the underlying operating system permissions and whether any realm checks allow it. This exception enables a security administrator to check the location of the files when securing them with Oracle ACFS security realms. However, a security administrator cannot view the contents of individual files without the appropriate operating system and security realm permissions.

#### Examples

The following example shows the use of the `acfsutil` `sec` `init` command.

Example 16-56 Using the acfsutil sec init command

    $ /sbin/acfsutil sec init -u grid -g asmadmin

### acfsutil sec load

#### Purpose

Loads Oracle ACFS security metadata into a file system identified by a mount point.

#### Syntax and Description

    acfsutil sec load -h
    acfsutil sec load -m mount_point -p file

`acfsutil` `sec` `load` `-h` displays help text and exits.

Table 16-61 contains the options available with the `acfsutil` `sec` `load` command.

Table 16-61 Options for the acfsutil sec load command

| Option             | Description                                                     |
|:-------------------|:----------------------------------------------------------------|
| `-m` `mount_point` | Specifies the directory where the file system is mounted.       |
| `-p` `file`        | Specifies the name of an existing saved security metadata file. |

The `acfsutil` `sec` `load` command loads the security metadata in a saved XML file into the specified Oracle ACFS file system. `acfsutil` `sec` `load` restores only user-created security policies; the command does not add files to the realms.

`acfsutil` `sec` `load` and `acfsutil` `sec` `save` can be used together to copy user-created policies from one file system to another. For example, if you have security policies on one file system that you want to replicate on other file systems, then use `acfsutil` `sec` `save` on the source file system to create an XML backup file. Next, use `acfsutil` `sec` `load` on the other destination file systems to load the saved security metadata and create the same policies. After creating the policies, you can choose to apply policies on different directories and files on that file system by adding directories and files in different realms, according to the policies you want to impose on those files.

To run the `acfsutil` `sec` `load` command, the destination mount point must have a file system that has been prepared for security and does not contain any user-created security objects.

If the file system mounted on destination mount point contains security objects, then you must run `acfsutil` `sec` `prepare` `-u` to remove all previously created security objects on the file system. After successfully running `acfsutil` `sec` `prepare` `-u`, you must run `acfsutil` `sec` `prepare` to prepare the file system for security. After successfully running `acfsutil` `sec` `prepare`, you can run `acfsutil` `sec` `load` on the file system. For information about preparing security on or removing security from a file system, refer to "acfsutil sec prepare".

The `acfsutil` `sec` `load` command does not load system security realms from the backup file. System security realms are created with the `acfsutil` `sec` `prepare` command; `acfsutil` `sec` `load` does not re-create these realms. For information about the system-created security realms, refer to "acfsutil sec prepare".

Only a security administrator can run this command.

#### Examples

The following example shows the use of the `acfsutil` `sec` `load` command.

Example 16-57 Using the acfsutil sec load command

    $ /sbin/acfsutil sec load -m /acfsmounts/acfs1 -p my_metadata_file.xml

### acfsutil sec prepare

#### Purpose

Prepares an Oracle ACFS file system for security features.

#### Syntax and Description

    acfsutil sec prepare -h
    acfsutil sec prepare [-u] -m mount_point

`acfsutil` `sec` `prepare` `-h` displays help text and exits.

Table 16-62 contains the options available with the `acfsutil` `sec` `prepare` command.

Table 16-62 Options for the acfsutil sec prepare command

| Option             | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          |
|:-------------------|:-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `-m` `mount_point` | Specifies the directory where the file system is mounted.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            |
| `-u`               | Backs out security for the specified mount point.<br>This command removes security from in the file system and reverts the file system to the state before `acfsutil` `sec` `prepare` was run on the file system.<br>This command removes all realm-secured files and directories from the realms and then destroys all Oracle ACFS security rules, rule sets and realms from the file system. However, the `.Security` directory and its contents, including log files and the security metadata backup files, are not deleted.<br>If you want to remove encryption and security is being used, then this command must be run before encryption is backed out. To back out encryption, refer to "[acfsutil encr set](acfs-commands-encryption.md)". |

The `acfsutil` `sec` `prepare` command must be run before any of the realm management commands. This command prepares the specified Oracle ACFS file system for security and by default turns security on for the file system.

When running `acfsutil` `sec` `prepare` `-u`, ensure that no other Oracle ACFS security commands are run until `acfsutil` `sec` `prepare` has completed.

If auditing is initialized on a cluster, this command also enables an Oracle ACFS security auditing source on the file system. The actions performed when enabling this audit source are the same as those done when the `acfsutil` `audit` `enable` command is run directly. For more information, refer to "[acfsutil audit enable](acfs-commands-audit.md)".

This command creates the `/``mount_point``/.Security`, `/``mount_point``/.Security/backup`, and `/``mount_point``/.Security/realm/logs` directories where `mount_point` is the option specified in the command line.

This command creates the following system security realms:

- `SYSTEM_Logs`

  This is a system-created realm to protect the Oracle ACFS security log files in the directory `.Security/realm/logs/` directory.

- `SYSTEM_Audit`

  This is a system-created realm to protect audit trail files. This realm is created if auditing has been initialized. If auditing has not been initialized, it is created when auditing is enabled for the security source through the `acfsutil` `audit` `enable` command. This realm secures the audit trail file so that the audit manager can read and write and the auditor can read the file, and no one else has access. This realm also protects the audit trail file so the audit manager cannot delete (without running the `acfsutil` `audit` `purge` command), truncate, overwrite, or chmod the file.

- `SYSTEM_SecurityMetadata`

  This is a system-created realm to protect the Oracle ACFS metadata XML file in the directory `.Security/backup/` directory.

- `SYSTEM_Antivirus`

  This is a system-created realm that allows access for the antivirus software that is running on an Oracle ACFS file system. For every realm protected file or directory, the `SYSTEM_Antivirus` realm is evaluated when authorization checks are performed to determine if the `SYSTEM_Antivirus` realm allows access to the file or directory.

  To allow the antivirus process to access realm-protected files or directories, you must add the `LocalSystem` or `SYSTEM` group to the realm with the `acfsutil` `sec` `realm` `add` command, as shown in Example 16-59. If other antivirus processes are running as `Administrator`, then the user `Administrator` must be added to the `SYSTEM_Antivirus` realm to allow access to realm protected files and directories.

  If no Antivirus products have been installed, do not add any users or groups to the `SYSTEM_Antivirus` realm. Because users or groups added to the `SYSTEM_Antivirus` realm have `READ` and `READDIR` access, limit the users or groups added to this realm. You can restrict the time window when the users or groups of this realm can access the realm protected files or directories with time-based rules. You can also have application-based rules if you can identify the process name for the antivirus installation that scans the files.

  The `SYSTEM_Antivirus` realm can only perform the following operations on a file or directory: `OPEN`, `READ`, `READDIR`, and setting time attributes. To remove or delete files or directories, you may need to disable security to clean up the infected files.

  This realm is set up only for Windows systems.

- `SYSTEM_BackupOperators`

  This is a system-created realm that enables you to authorize users that can back up realm-secured files and directories. You can add users, groups, rule sets, and command rules to this realm to provide fine-grain authorization for backing up realm-secured files and directories. A user must be added to this realm to back up realm-secured files and directories.

  Use caution when adding groups to this system realm. After you add a group to this system realm, all the users of the added group are able to override the realm protections to access files.

To access files in the system security realms, the user should be assigned as a security administrator with the `acfsutil` `sec` `admin` `add` command.

You can add users, groups, rule sets, and command rules to system-created realms with the `acfsutil` `sec` `realm` `add` command, the same as for user-created realms. However, adding files and directories to system realms is not recommended. You can use the `acfsutil` `sec` `realm` `delete` command to delete objects from the system-created realms.

System-created security realms cannot be removed by a security administrator with the `acfsutil` `sec` `admin` `destroy` command. These realms are only removed when security is backed out of a file system when executing the `acfsutil` `sec` `prepare` command with the `-u` option.

The `acfsutil` `sec` `prepare` `–u` command is not allowed if any snapshots exist in the file system.

Only a security administrator can run the `acfsutil` `sec` `prepare` command.

#### Examples

The following example shows the use of the `acfsutil` `sec` `prepare` command.

Example 16-58 Using the acfsutil sec prepare command

    $ /sbin/acfsutil sec prepare -m /acfsmounts/acfs1

### acfsutil sec realm add

#### Purpose

Adds objects to an Oracle ACFS security realm.

#### Syntax and Description

    acfsutil sec realm add -h
    acfsutil sec realm add realm -m mount_point
       {[-u user, ...] [-G os_group,...]
        [-l commandrule:ruleset,commandrule:ruleset, ...]
        [-e [-a {AES}] [-k {128|192|256}]]
        [-f [ -r] path ...]}

`acfsutil` `sec` `realm` `add` `-h` displays help text and exits.

Table 16-63 contains the options available with the `acfsutil` `sec` `realm` `add` command.

Table 16-63 Options for the acfsutil sec realm add command

| Option                       | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                |
|:-----------------------------|:-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `realm`                      | Specifies the realm name to add.                                                                                                                                                                                                                                                                                                                                                                                                                           |
| `-m` `mount_point`           | Specifies the directory where the file system is mounted.                                                                                                                                                                                                                                                                                                                                                                                                  |
| `-u` `user`                  | Specifies user names to add.                                                                                                                                                                                                                                                                                                                                                                                                                               |
| `-G` `os_group`              | Specifies the operating system groups to add.                                                                                                                                                                                                                                                                                                                                                                                                              |
| `-l` `commandrule`:`ruleset` | Specifies the filters to add. The `commandrule` switch is used to add one or more command rules to the realm with a rule set.<br>`ruleset` specifies the rule set associated with the command rule for this realm. Only one rule set can be included with each command rule.<br>For a list of command rules, refer to Table 16-64. To display a list of the command rules, use `acfsutil` `sec` `info` with the `-c` option. Refer to "acfsutil sec info". |
| `-e`                         | Enables encryption on the realm. Turning encryption on for the realm causes all files contained in the realm to be encrypted. These files remain encrypted until they are no longer part of an encrypted realm.<br>Files that are encrypted are not re-encrypted to match the new specified encryption parameters.                                                                                                                                         |
| `-a` {`AES`}                 | Specifies the encryption algorithm for the realm.                                                                                                                                                                                                                                                                                                                                                                                                          |
| `-k` { `128`\|`192`\|`256`}  | Specifies the encryption key length.                                                                                                                                                                                                                                                                                                                                                                                                                       |
| `-f` \[`-r`\] `path` `...`   | Adds files specified by `path` to the realm. `-r` specifies a recursive operation. File paths must be separated by spaces and must be placed at the end of the command.<br>If a specified file is not realm secured, the file is encrypted or decrypted to match the encryption status for the realm.                                                                                                                                                      |

The `acfsutil` `sec` `realm` `add` command adds objects to the specified realm. The objects to be added include users, groups, command rules, rule sets, and files. If the command encounters an error when adding an object, a message is displayed and the command continues processing the remaining objects.

Multiple entries can be added in a comma-delimited list when adding users, operating system groups, or command rules. Do not use spaces in the comma-delimited list. If spaces are added, then enclose the list in quotes.

If the `-e` option is specified, then encryption must have been initialized for the cluster and set on the file system. For more information, refer to "[acfsutil encr init](acfs-commands-encryption.md)" and "[acfsutil encr set](acfs-commands-encryption.md)".

If the entire mount point, which includes the `.Security` directory, is added to the realm then the security administrator operating system group should be added to the realm to maintain security logging and backing up operations.

The supported command are rules listed in Table 16-64. These command rules restrict or protect against file system operations on realm-secured files and directories.

Table 16-64 Security Realm Command Rules

| Rule         | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                |
|:-------------|:---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `ALL`        | Protects against all file system operations on files and directories.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      |
| `APPENDFILE` | Restricts against additions to the end of a file. Restrictions include writes that start within the current file size, but proceed beyond the end of the file.                                                                                                                                                                                                                                                                                                                                                                                                             |
| `CHGRP`      | Protects from changing the group ownership on a file or directory.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         |
| `CHMOD`      | Protects from changing the permissions on a file or directory.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             |
| `CHOWN`      | Protects from changing the owner information of a file or directory.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       |
| `CREATEFILE` | Protects from creation of new file in a directory.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         |
| `DELETEFILE` | Protects from deletion of a file from a directory.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         |
| `EXTEND`     | Restricts the extension operation of a file size. A file size may still be modifiable with other operations. `EXTEND` does not protect against a `truncate` followed by an `append` operation.                                                                                                                                                                                                                                                                                                                                                                             |
| `IMMUTABLE`  | Denies any changes to the files and directories in the realm except changes to extended attributes resulting from commands such as `acfsutil` `tag` and `acfsutil` `encr`.<br>Includes the following protection for a file or directory: `APPENDFILE`, `CHGRP`, `CHMOD`, `CHOWN`, `DELETEFILE`, `EXTEND`, `OVERWRITE`, `RENAME`, `RMDIR`, `TRUNCATE`, and `WRITE`.<br>`IMMUTABLE` does not deny any changes to the `atime` attribute. The `atime` attribute changes when a user accesses the file.<br>Can be set to archive the files and directories in a security realm. |
| `LINKFILE`   | Restricts the creation of hard links to files.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             |
| `MKDIR`      | Protects from the creation of new directory in a directory.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                |
| `MMAPREAD`   | Protects a file from being memory mapped for a read operation using `mmap()` on Linux or using `CreateFileMapping` followed by `MapViewOfFile()` on Windows.                                                                                                                                                                                                                                                                                                                                                                                                               |
| `MMAPWRITE`  | Protects a file from being memory mapped for a write operation. Setting `MMAPWRITE` also protects a file from mapping for read as the operating system maps a file for both read and write.                                                                                                                                                                                                                                                                                                                                                                                |
| `OPENFILE`   | Protects from the opening of a file.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       |
| `OVERWRITE`  | Prevents existing content in a file from being overwritten with a `write` operation whose start and end offsets are within the current file size.<br>If the operations on a file are `truncate` followed by `append`, `OVERWRITE` does not protect the file. To provide additional protection from both `append` and `overwrite` operations, use the `WRITE` command rule.                                                                                                                                                                                                 |
| `READDIR`    | Restricts for a directory listing, except for use by the security administrator group.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                     |
| `READ`       | Protects from reading the contents of a file. `READ` also protects against `read` operations using `mmap(2)`.                                                                                                                                                                                                                                                                                                                                                                                                                                                              |
| `RENAME`     | Protects against renaming a file or directory.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             |
| `RMDIR`      | Protects against removing a directory.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                     |
| `SYMLINK`    | Restricts the creation of symbolic links in the directories protected by a security realm. When creating symbolic links, it does not matter whether the source file is protected by a security realm.                                                                                                                                                                                                                                                                                                                                                                      |
| `TRUNCATE`   | Restricts the truncation of a file.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                        |
| `WRITE`      | Protects a file against the `write` system call. `WRITE` also protects against `append` and `overwrite` operations, plus `write` operations using `mmap(2)`.<br>A file may still be modifiable with other file operations. To protect the file from other modifications, also use the `TRUNCATE` and `DELETEFILE` command rules.                                                                                                                                                                                                                                           |

Only a security administrator can run this command.

#### Examples

Example 16-59 shows the use of the `acfsutil` `sec` `realm` `add` command. The first `acfsutil` `sec` command adds a user group to a security realm. The second and third commands add the `LocalSystem` or `SYSTEM` group to the `SYSTEM_Antivirus` realm in a Windows environment.

Example 16-59 Using the acfsutil sec realm add command

    $ /sbin/acfsutil sec realm add my_security_realm -m /acfsmounts/acfs1
         -G my_os_group

    C:\> acfsutil sec realm add SYSTEM_Antivirus /m e: /G "NT AUTHORITY\\SYSTEM"

    C:\> acfsutil sec realm add SYSTEM_Antivirus /m e: /G "SYSTEM"

### acfsutil sec realm audit disable

#### Purpose

Disables auditing of a specific command rule or all command rules for files in an Oracle ACFS security realm.

#### Syntax and Description

    acfsutil sec realm audit disable -h
    acfsutil sec realm audit disable realm -m mount_point
         [-l commandrule,commandrule,...] {-a |-v }

`acfsutil` `sec` `realm` `audit` `disable` `-h` displays help text and exits.

Table 16-65 contains the options available with the `acfsutil` `sec` `realm` `audit` `disable` command.

Table 16-65 Options for the acfsutil sec realm audit disable command

| Option             | Description                                                                                                                                                                                                                                                                                                                    |
|:-------------------|:-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `realm`            | Specifies the security realm name.                                                                                                                                                                                                                                                                                             |
| `-m` `mount_point` | Specifies the directory where the file system is mounted.                                                                                                                                                                                                                                                                      |
| `-l` `commandrule` | Specifies the command rules on which to disable auditing.<br>If this option is not specified, then the list of all command rules is the default.<br>For a list of command rules, refer to Table 16-64. To display a list of the command rules, use `acfsutil` `sec` `info` with the `-c` option. Refer to "acfsutil sec info". |
| `-a` \| `-v`       | Specifies to disable audit realm authorizations (`-a`) or disable audit realm violations (`-v`). Either `–a` or `–v` must be specified.                                                                                                                                                                                        |

Multiple entries can be added in a comma-delimited list when listing command rules. Do not use spaces in the comma-delimited list. If spaces are added, then enclose the list in quotes.

Only a security administrator can run this command. This command is authenticated using the Oracle ACFS security administrator password.

#### Examples

Example 16-60 shows the use of the `acfsutil` `sec` `realm` `audit` `disable` command. This command disables auditing on the `OPEN` (all violations) and `WRITE` (all violations) command rules.

Example 16-60 Using the acfsutil sec realm audit disable command

    $ /sbin/acfsutil sec realm audit disable mySecureRealm
        –m /acfsmounts/acfs1 –l OPEN,WRITE –v

### acfsutil sec realm audit enable

#### Purpose

Enables auditing of a specific command rule or all command rules for files in an Oracle ACFS security realm.

#### Syntax and Description

    acfsutil sec realm audit enable -h
    acfsutil sec realm audit enable realm -m mount_point
         [-l commandrule,commandrule,...]
         [-a ] [-v [ -u] ]

`acfsutil` `sec` `realm` `audit` `enable` `-h` displays help text and exits.

Table 16-66 contains the options available with the `acfsutil` `sec` `realm` `audit` `enable` command.

Table 16-66 Options for the acfsutil sec realm audit enable command

| Option             | Description                                                                                                                                                                                                                                                                                                                   |
|:-------------------|:------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `realm`            | Specifies the security realm name.                                                                                                                                                                                                                                                                                            |
| `-m` `mount_point` | Specifies the directory where the file system is mounted.                                                                                                                                                                                                                                                                     |
| `-l` `commandrule` | Specifies the command rules on which to enable auditing.<br>If this option is not specified, then the list of all command rules is the default.<br>For a list of command rules, refer to Table 16-64. To display a list of the command rules, use `acfsutil` `sec` `info` with the `-c` option. Refer to "acfsutil sec info". |
| `-a`               | Specifies to audit realm authorizations.                                                                                                                                                                                                                                                                                      |
| `-v` \[`-u`\]      | Specifies to audit realm violations. If `–u` is also specified, only realm violations by users who are members of a realm are audited.                                                                                                                                                                                        |

If the `acfsutil` `sec` `realm` `audit` `enable` command is run multiple times, then the earlier configuration is not negated and the new settings are also applied. An exception to this behavior occurs when the command is run with the `–v` option and the specified command rule has auditing set for realm violations. In this case, the behavior is updated according to whether the `–u` flag was specified. For more information, see Example 16-63.

Multiple entries can be added in a comma-delimited list when listing command rules. Do not use spaces in the comma-delimited list. If spaces are added, then enclose the list in quotes.

If neither `–a` or `–v` are specified with the `acfsutil` `sec` `realm` `audit` `enable` command, the default is `–v`. Both `–a` and `–v` can be specified.

Only a security administrator can run this command. This command is authenticated using the Oracle ACFS security administrator password.

#### Examples

Example 16-61 shows how to enable auditing of the Oracle ACFS backup operators. Because these users are allowed access to files through the `SYSTEM_Backup` realm and are granted special privileges that give them access to all files on the file system, a security administrator may want to audit their actions. After the command is executed, any time a member of the `SYSTEM_Backup` realm opens a file an audit record is written to the Oracle ACFS Security audit trail on the file system.

Example 16-61 Auditing Oracle ACFS security backup operators

    $ /sbin/acfsutil sec realm audit enable SYSTEM_Backup
        –m /acfsmounts/acfs1 –l OPEN –a

Example 16-62 shows how to use the `–u` option to audit realm violations by users who are part of the realm. In this scenario sensitive human resources information is stored in `HumanResources` security realm and the `hr` group is allowed to access this information. However, a ruleset applied to the `ALL` command rule prevents access to this data from 6 PM to 8 AM. With this command, the security administrator could discover if any human resource employees are attempting to access sensitive data outside of the allowed time period. After this command is executed, only access violations by users who are members of the `hr` group are audited.

Example 16-62 Auditing only security realm users

    $ /sbin/acfsutil sec realm audit enable HumanResources
        –m /acfsmounts/acfs1 –l ALL –v –u

Example 16-63 shows multiple runs of the `acfsutil` `sec` `realm` `audit` `enable` command. After run 1, the `OPEN` (all violations) and `WRITE` (all violations) command rules are audited. After run 2, the `OPEN` (all violations), `WRITE` (all violations), and `DELETEFILE` (authorizations) command rules are audited. After run 3, the `OPEN` (authorizations and realm user violations), `WRITE` (all violations), `DELETEFILE` (authorizations), and `TRUNCATE` (authorizations and realm user violations) command rules are audited. After run 4, all violations are audited on all command rules. In addition, authorizations are audited for `OPEN`, `DELETEFILE`, and `TRUNCATE`.

Example 16-63 Running acfsutil sec realm audit enable multiple times

    $ echo run 1
    $ /sbin/acfsutil sec realm audit enable mySecureRealm
        –m /acfsmounts/acfs1 –l OPEN,WRITE –v

    $ echo run 2
    $ /sbin/acfsutil sec realm audit enable mySecureRealm
        –m /acfsmounts/acfs1 –l DELETEFILE –a

    $ echo run 3
    $ /sbin/acfsutil sec realm audit enable mySecureRealm
        -m /acfsmounts/acfs1 –l OPEN,TRUNCATE –a –v -u

    $ echo run 4
    $ /sbin/acfsutil sec realm audit enable mySecureRealm
        –m /acfsmounts/acfs1 –v

### acfsutil sec realm audit info

#### Purpose

Displays the realm auditing information for a specified Oracle ACFS security realm.

#### Syntax and Description

    acfsutil sec realm audit info -h
    acfsutil sec realm audit info -m mount_point -n realm

`acfsutil` `sec` `realm` `audit` `info` `-h` displays help text and exits.

Table 16-66 contains the options available with the `acfsutil` `sec` `realm` `audit` `info` command.

Table 16-67 Options for the acfsutil sec realm audit info command

| Option             | Description                                               |
|:-------------------|:----------------------------------------------------------|
| `-m` `mount_point` | Specifies the directory where the file system is mounted. |
| `-n` `realm`       | Specifies the security realm name.                        |

The `acfsutil` `sec` `realm` `audit` `info` command provides information about a specified Oracle ACFS security realm.

#### Examples

Example 16-64 shows an example of the `acfsutil` `sec` `realm` `audit` `info` command.

Example 16-64 Running acfsutil sec realm audit info

    $ /sbin/acfsutil sec realm audit info –m /acfsmounts/acfs1
        -n mySecureRealm

    Command rule auditing information for realm 'mySecureRealm'
       on mount point '/acfsmounts/acfs1':

    Realm authorization            :    'READ, WRITE'
    Realm violation for all users  :    'READ, OPENFILE'
    Realm violation for realm users:    'None'

### acfsutil sec realm clone

#### Purpose

Clones an Oracle ACFS security realm.

#### Syntax and Description

    acfsutil sec realm clone -h
    acfsutil sec realm clone realm -s src_mount_point new_realm
         [-e] [-f] [-G] [-l] [-u]
    acfsutil sec realm clone realm -s src_mount_point
         [new_realm] -d destination_mount_point
         [-e] [-G] [-l] [-u]

`acfsutil` `sec` `realm` `clone` `-h` displays help text and exits.

Table 16-68 contains the options available with the `acfsutil` `sec` `realm` `clone` command.

Table 16-68 Options for the acfsutil sec realm clone command

| Option                         | Description                                                                |
|:-------------------------------|:---------------------------------------------------------------------------|
| `realm`                        | Specifies the realm name to be cloned.                                     |
| `-s` `src_mount_point`         | Specifies the directory where the source file system is mounted.           |
| `new_realm`                    | Specifies the new realm name.                                              |
| `-d` `destination_mount_point` | Specifies the directory for the destination mount point for the new realm. |
| `-e`                           | Copy encryption attributes to the new realm.                               |
| `-f`                           | Copy file objects to the new realm.                                        |
| `-G`                           | Copy operating system groups to the new realm.                             |
| `-l`                           | Copy filters to the new realm.                                             |
| `-u`                           | Copy users to the new realm.                                               |

The `acfsutil` `sec` `realm` `clone` makes a copy of the specified realm in the destination mount point. If the source and mount points are different and the new realm name is not specified, then the realm is cloned using the existing realm name in the Oracle ACFS file system specified by destination mount point. If the destination mount point is not specified, then the cloned realm is located in the source mount point and a new unique realm name must be specified.

If the `-l` option is specified and the destination mount point is different than the source mount point, then the rules and rule sets must be cloned first.

If the `-e` option is specified and the destination mount point is different than the source mount point, then encryption must be set on destination mount point. For more information, refer to "[acfsutil encr set](acfs-commands-encryption.md)".

The `-f` option can only be used if the destination mount point is the same as the source mount point.

Only a security administrator can run this command.

#### Examples

The following example shows the use of the `acfsutil` `sec` `realm` `clone` command.

Example 16-65 Using the acfsutil sec realm clone command

    $ /sbin/acfsutil sec realm clone my_security_realm -s /acfsmounts/acfs1
          my_new_security_realm -d /acfsmounts/acfs2 -G

### acfsutil sec realm create

#### Purpose

Creates an Oracle ACFS security realm.

#### Syntax and Description

    acfsutil sec realm create -h
    acfsutil sec realm create realm -m mount_point
         -e { on -a {AES}  -k {128|192|256} | off }
         [-o {enable|disable}] [-d "description"]

`acfsutil` `sec` `realm` `create` `-h` displays help text and exits.

Table 16-69 contains the options available with the `acfsutil` `sec` `realm` `create` command.

Table 16-69 Options for the acfsutil sec realm create command

| Option                      | Description                                                                                             |
|:----------------------------|:--------------------------------------------------------------------------------------------------------|
| `realm`                     | Specifies the realm name.                                                                               |
| `-m` `mount_point`          | Specifies the mount point for the file system. A mount point is specified as a path on Linux platforms. |
| `-e` {`on`\|`off`}          | Specifies encryption on or off for the realm.                                                           |
| `-a` {`AES`}                | Specifies the encryption algorithm.                                                                     |
| `-k` { `128`\|`192`\|`256`} | Specifies the encryption key length.                                                                    |
| `-o` {`enable`\|`disable`}  | Specifies where security is on or off for the realm.                                                    |
| `-d` `"``description``"`    | Specifies a realm description.                                                                          |

The `acfsutil` `sec` `create` `realm` creates a new realm in the specified Oracle ACFS file system. The new realm name must be unique in the file system identified by the mount point.

A maximum of 500 Oracle ACFS security realms can be created, including any default system realms created by the `acfsutil` `sec` `prepare` command.

The realm is enabled by default unless the `-o` `disable` option is specified.

If the `-e` `on` option is specified, then encryption must have been initialized for the cluster and set on the file system. For more information, refer to "[acfsutil encr init](acfs-commands-encryption.md)" and "[acfsutil encr set](acfs-commands-encryption.md)".

If the `-e` `off` option is specified, you cannot specify the `-a` and `-k` options.

Only a security administrator can run this command.

#### Examples

The following example shows the use of the `acfsutil` `sec` `realm` `create` command.

Example 16-66 Using the acfsutil sec realm create command

    $ /sbin/acfsutil sec realm create my_security_realm -m /acfsmounts/acfs1
         -e on -a AES -k 192 -o enable

### acfsutil sec realm delete

#### Purpose

Deletes objects from an Oracle ACFS security realm.

#### Syntax and Description

    acfsutil sec realm delete -h
    acfsutil sec realm delete realm -m mount_point
         {[-u user, ...] [-G os_group, ...]
         [-l :ruleset,commandrule:ruleset, ...]
         [-f [ -r] path, ...] ] [-e ]}

`acfsutil` `sec` `realm` `delete` `-h` displays help text and exits.

Table 16-70 contains the options available with the `acfsutil` `sec` `realm` `delete` command.

Table 16-70 Options for the acfsutil sec realm delete command

| Option                       | Description                                                                                                                                                                                                                                                                                             |
|:-----------------------------|:--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `realm`                      | Specifies the realm name.                                                                                                                                                                                                                                                                               |
| `-m` `mount_point`           | Specifies the directory where the file system is mounted.                                                                                                                                                                                                                                               |
| `-u` `user`                  | Specifies user names to delete.                                                                                                                                                                                                                                                                         |
| `-G` `os_group`              | Specifies the operating system groups to delete.                                                                                                                                                                                                                                                        |
| `-l` `commandrule`:`ruleset` | Specifies the filters to delete from the realm. To display a list of the command rules, use `acfsutil` `sec` `info` with the `-c` option. `ruleset` specifies the rule set associated with the command rule for this realm.                                                                             |
| `-f` \[`-r`\] `path` `...`   | Deletes files specified by `path` from the realm. `-r` specifies a recursive operation. File paths must be separated by spaces.<br>If this is the last realm securing the file, the file is encrypted or decrypted to match the file system level encryption state.                                     |
| `-e`                         | Disables encryption on the realm.<br>When disabling encryption, this option decrypts any files in the realm that do not belong to any other encrypted realms. If a file is part of another realm which is encrypted or if encryption is turned on for the file system, then the file remains encrypted. |

The `acfsutil` `sec` `realm` `delete` command removes objects from the specified realm. The objects to be deleted include users, groups, rule sets, and files. If the command encounters an error when deleting an object, a message is displayed and the command continues processing the remaining objects.

Multiple entries can be added in a comma-delimited list when adding users, operating system groups, or command rules. Do not use spaces in the comma-delimited list. If spaces are added, then enclose the list in quotes.

Only a security administrator can run this command.

#### Examples

The following example shows the use of the `acfsutil` `sec` `realm` `delete` command.

Example 16-67 Using the acfsutil sec realm delete command

    $ /sbin/acfsutil sec realm delete my_security_realm -m /acfsmounts/acfs1
         -f -r /acfsmounts/acfs1/myoldfiles/*.log

### acfsutil sec realm destroy

#### Purpose

Destroys an Oracle ACFS security realm.

#### Syntax and Description

    acfsutil sec realm destroy -h
    acfsutil sec realm destroy realm -m mount_point

`acfsutil` `sec` `realm` `destroy` `-h` displays help text and exits.

Table 16-71 contains the options available with the `acfsutil` `sec` `realm` `destroy` command.

Table 16-71 Options for the acfsutil sec realm destroy command

| Option             | Description                                               |
|:-------------------|:----------------------------------------------------------|
| `realm`            | Specifies the realm name.                                 |
| `-m` `mount_point` | Specifies the directory where the file system is mounted. |

The `acfsutil` `sec` `destroy` `realm` removes a security realm from the specified Oracle ACFS file system. Destroying the realm does not destroy the objects in the realm; this command simply removes the security associated with the realm from the objects.

Only a security administrator can run this command.

#### Examples

The following example shows the use of the `acfsutil` `sec` `realm` `destroy` command.

Example 16-68 Using the acfsutil sec realm destroy command

    $ /sbin/acfsutil sec realm destroy my_security_realm -m /acfsmounts/acfs1

### acfsutil sec rule clone

#### Purpose

Clones a security rule.

#### Syntax and Description

    acfsutil sec rule clone -h
    acfsutil sec rule clone rule -s src_mount_point new_rule
    acfsutil sec rule clone rule -s src_mount_point
         [new_rule] -d mount_point

`acfsutil` `sec` `rule` `clone` `-h` displays help text and exits.

Table 16-72 contains the options available with the `acfsutil` `sec` `rule` `clone` command.

Table 16-72 Options for the acfsutil sec rule clone command

| Option                 | Description                                                                                         |
|:-----------------------|:----------------------------------------------------------------------------------------------------|
| `rule`                 | Specifies the existing name of the rule. If the name contains a space, enclose in quotes (`"` `"`). |
| `-s` `src_mount_point` | Specifies the directory where the source file system is mounted.                                    |
| `-d` `mount_point`     | Specifies the directory for the destination mount point of the file system.                         |
| `new_rule`             | Specifies the new name of the rule. If the name contains a space, enclose in quotes (`"` `"`).      |

If the source and mount points are different and the new rule name is not specified, then the rule is cloned using the existing rule name in the Oracle ACFS file system specified by destination mount point. If the destination mount point is not specified, then the cloned rule is located in the source mount point and a new unique rule name must be specified.

Only a security administrator can run this command.

#### Examples

The following example shows the use of the `acfsutil` `sec` `rule` `clone` command.

Example 16-69 Using the acfsutil sec rule clone command

    $ /sbin/acfsutil sec rule clone my_security_rule -s /acfsmounts/acfs1
          my_new_security_rule -d /acfsmounts/acfs2

### acfsutil sec rule create

#### Purpose

Creates a security rule.

#### Syntax and Description

    acfsutil sec rule create -h
    acfsutil sec rule create rule -m mount_point
         -t rule_type rule_value
         [-o {ALLOW|DENY}]

`acfsutil` `sec` `rule` `create` `-h` displays help text and exits.

Table 16-73 contains the options available with the `acfsutil` `sec` `rule` `create` command.

Table 16-73 Options for the acfsutil sec rule create command

| Option                        | Description                                                                                                                                                                                                               |
|:------------------------------|:--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `rule`                        | Specifies the name of the rule. If the name contains a space, enclose in quotes (`"` `"`).                                                                                                                                |
| `-m` `mount_point`            | Specifies the directory where the file system is mounted.                                                                                                                                                                 |
| `-t` `rule_type` `rule_value` | Specifies a rule type and a rule value. The rule type can be `application`, `hostname`, `time`, or `username`. The rule value depends on the type of rule. The valid rule types and values are described in this section. |
| `-o` `option`                 | Specifies options preceded by `-o`. The option specified can be `ALLOW` or `DENY`. The default value is `DENY`.                                                                                                           |

The `acfsutil` `sec` `rule` `create` command creates a new rule in the Oracle ACFS file system specified by the mount point. The new rule can be added to a rule set and that rule set can be added to a security realm.

A maximum of 500 Oracle ACFS security rules can be created.

The rule types and associated rule values are:

- `application`

  This rule type specifies the name of an application which is allowed or denied access to the objects protected by a realm.

- `hostname`

  This rule type specifies the name of a computer from which a user accesses the objects protected by a realm. Access from a node can be allowed or denied using this rule. The `hostname` should be one of the cluster node names and not any other external nodes which could have mounted the Oracle ACFS file system as a network File System (NFS) mount.

- `time`

  This rule type specifies the time interval in the form `start_time`,`end_time`. This time interval specifies access to a realm. Access can be allowed or denied to objects protected by a realm only during certain times of the day by setting this rule in a realm. The time is based on the local time of the host.

- `username`

  This rule type specifies the name of a user to be added or deleted from a realm. You can use this option to deny access for any user that belongs to a security group that is part of a realm.

Only a security administrator can run this command.

#### Examples

The following example shows the use of the `acfsutil` `sec` `rule` `create` command.

Example 16-70 Using the acfsutil sec rule create command

    $ /sbin/acfsutil sec rule create my_security_rule -m /acfsmounts/acfs1
          -t username security_user_one -o ALLOW

### acfsutil sec rule destroy

#### Purpose

Removes a security rule.

#### Syntax and Description

    acfsutil sec rule destroy -h
    acfsutil sec rule destroy rule -m mount_point

`acfsutil` `sec` `rule` `destroy` `-h` displays help text and exits.

Table 16-74 contains the options available with the `acfsutil` `sec` `rule` `destroy` command.

Table 16-74 Options for the acfsutil sec rule destroy command

| Option             | Description                                                                                |
|:-------------------|:-------------------------------------------------------------------------------------------|
| `rule`             | Specifies the name of the rule. If the name contains a space, enclose in quotes (`"` `"`). |
| `-m` `mount_point` | Specifies the directory where the file system is mounted.                                  |

The `acfsutil` `sec` `rule` `destroy` command removes a rule from the rule sets in the Oracle ACFS file system specified by the mount point. A rule set is not destroyed if all the rules are destroyed. The empty rule set must be explicitly destroyed.

Only a security administrator can run this command.

#### Examples

The following example shows the use of the `acfsutil` `sec` `rule` `destroy` command.

Example 16-71 Using the acfsutil sec rule destroy command

    $ /sbin/acfsutil sec rule destroy my_security_rule -m /acfsmounts/acfs1

### acfsutil sec rule edit

#### Purpose

Updates a security rule.

#### Syntax and Description

    acfsutil sec rule edit -h
    acfsutil sec rule edit rule -m mount_point
         { [-t rule_type rule_value ] [-o {ALLOW|DENY}] }

`acfsutil` `sec` `rule` `edit` `-h` displays help text and exits.

Table 16-75 contains the options available with the `acfsutil` `sec` `rule` `edit` command.

Table 16-75 Options for the acfsutil sec rule edit command

| Option                        | Description                                                                                                                                                                                                                                  |
|:------------------------------|:---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `rule`                        | Specifies the name of the rule. If the name contains a space, enclose in quotes (`"` `"`).                                                                                                                                                   |
| `-m` `mount_point`            | Specifies the directory where the file system is mounted.                                                                                                                                                                                    |
| `-t` `rule_type` `rule_value` | Specifies a rule type and a rule value. The rule type can be `application`, `hostname`, `time`, or `username`. Rule value depends on the type of rule. For information on the rule type and rule value, refer to "acfsutil sec rule create". |
| `-o` `option`                 | Specifies options preceded by `-o`. The option specified can be `ALLOW` or `DENY`.                                                                                                                                                           |

The `acfsutil` `sec` `rule` `edit` updates a rule. The value that is associated with a rule can be updated, but not the rule type.

Only a security administrator can run this command.

#### Examples

The following example shows the use of the `acfsutil` `sec` `rule` `edit` command to update `my_security_rule`. The existing rule is of type `username` and that value cannot be changed.

Example 16-72 Using the acfsutil sec rule edit command

    $ /sbin/acfsutil sec rule edit my_security_rule -m /acfsmounts/acfs1
          -t username security_user_three -o ALLOW

### acfsutil sec ruleset clone

#### Purpose

Clones a security rule set.

#### Syntax and Description

    acfsutil sec ruleset clone -h
    acfsutil sec ruleset clone ruleset -s mount_point  new_ruleset
    acfsutil sec ruleset clone ruleset -s mount_point
          [new_ruleset] -d mount_point

`acfsutil` `sec` `ruleset` `clone` `-h` displays help text and exits.

Table 16-76 contains the options available with the `acfsutil` `sec` `ruleset` `clone` command.

Table 16-76 Options for the acfsutil sec ruleset clone command

| Option             | Description                                                                                             |
|:-------------------|:--------------------------------------------------------------------------------------------------------|
| `rule_set`         | Specifies the existing name of the rule set. If the name contains a space, enclose in quotes (`"` `"`). |
| `-s` `mount_point` | Specifies the directory where the source file system is mounted.                                        |
| `-d` `mount_point` | Specifies the directory for the destination mount point of the file system.                             |
| `new_rule_set`     | Specifies the new name of the rule set. If the name contains a space, enclose in quotes (`"` `"`).      |

If the source mount point is different from destination mount point, the rules in the rule set must be cloned first.

If the source and mount points are different and the new rule set name is not specified, then the rule set is cloned using the existing rule set name in the Oracle ACFS file system specified by destination mount point. If the destination mount point is not specified, then the cloned rule set is located in the source mount point and a new unique rule set name must be specified.

Only a security administrator can run this command.

#### Examples

The following example shows the use of the `acfsutil` `sec` `ruleset` `clone` command.

Example 16-73 Using the acfsutil sec ruleset clone command

    $ /sbin/acfsutil sec ruleset clone
          my_security_ruleset -s /acfsmounts/acfs1
          my_new_security_ruleset -d /acfsmounts/acfs2

### acfsutil sec ruleset create

#### Purpose

Creates a security rule set.

#### Syntax and Description

    acfsutil sec ruleset create -h
    acfsutil sec ruleset create rule_set -m mount_point
            [-o {ALL_TRUE|ANY_TRUE}]

`acfsutil` `sec` `ruleset` `create` `-h` displays help text and exits.

Table 16-77 contains the options available with the `acfsutil` `sec` `ruleset` `create` command.

Table 16-77 Options for the acfsutil sec ruleset create command

| Option             | Description                                                                                                                |
|:-------------------|:---------------------------------------------------------------------------------------------------------------------------|
| `rule_set`         | Specifies the name of the rule set. If the name contains a space, enclose in quotes (`"` `"`).                             |
| `-m` `mount_point` | Specifies the directory where the file system is mounted.                                                                  |
| `-o` `option`      | Specifies options preceded by `-o`. The option specified can be `ALL_TRUE` or `ANY_TRUE`. The default value is `ALL_TRUE`. |

The `acfsutil` `sec` `ruleset` `create` command creates a new rule set in the specified mount point.

A maximum of 500 Oracle ACFS security rule sets can be created.

Only a security administrator can run this command.

#### Examples

The following example shows the use of the `acfsutil` `sec` `ruleset` `create` command.

Example 16-74 Using the acfsutil sec ruleset create command

    $ /sbin/acfsutil sec ruleset create
           my_security_ruleset -m /acfsmounts/acfs1 -o ANY_TRUE

### acfsutil sec ruleset destroy

#### Purpose

Removes a security rule set.

#### Syntax and Description

    acfsutil sec ruleset destroy -h
    acfsutil sec ruleset destroy rule_set -m mount_point

`acfsutil` `sec` `ruleset` `destroy` `-h` displays help text and exits.

Table 16-78 contains the options available with the `acfsutil` `sec` `ruleset` `destroy` command.

Table 16-78 Options for the acfsutil sec ruleset destroy command

| Option             | Description                                                                                    |
|:-------------------|:-----------------------------------------------------------------------------------------------|
| `rule_set`         | Specifies the name of the rule set. If the name contains a space, enclose in quotes (`"` `"`). |
| `-m` `mount_point` | Specifies the directory where the file system is mounted.                                      |

The `acfsutil` `sec` `ruleset` `destroy` command removes a rule set from the Oracle ACFS file system specified by the mount point. Only a security administrator can run this command.

#### Examples

The following example shows the use of the `acfsutil` `sec` `ruleset` `destroy` command.

Example 16-75 Using the acfsutil sec ruleset destroy command

    $ /sbin/acfsutil sec ruleset destroy
           my_security_ruleset -m /acfsmounts/acfs1

### acfsutil sec ruleset edit

#### Purpose

Updates a security rule set.

#### Syntax and Description

    acfsutil sec ruleset edit -h
    acfsutil sec ruleset edit rule_set -m mount_point
        { [-a rule,...] [-d rule,...] [-o {ALL_TRUE|ANY_TRUE}]}

`acfsutil` `sec` `ruleset` `edit` `-h` displays help text and exits.

Table 16-79 contains the options available with the `acfsutil` `sec` `ruleset` `edit` command.

Table 16-79 Options for the acfsutil sec ruleset edit command

| Option             | Description                                                                                    |
|:-------------------|:-----------------------------------------------------------------------------------------------|
| `rule_set`         | Specifies the name of the rule set. If the name contains a space, enclose in quotes (`"` `"`). |
| `-m` `mount_point` | Specifies the directory where the file system is mounted.                                      |
| `-a` `rule`        | Specifies the rule to add.                                                                     |
| `-d` `rule`        | Specifies the rule to remove.                                                                  |
| `-o` `option`      | Specifies options preceded by `-o`. The option specified can be `ALL_TRUE` or `ANY_TRUE`.      |

The `acfsutil` `sec` `ruleset` `edit` command updates a rule set in the Oracle ACFS file system specified by the mount point.

Only a security administrator can run this command.

#### Examples

The following example shows the use of the `acfsutil` `sec` `ruleset` `edit` command.

Example 16-76 Using the acfsutil sec ruleset edit command

    $ /sbin/acfsutil sec ruleset edit
           my_security_ruleset -m /acfsmounts/acfs1
           -a my_new_rule -o ANY_TRUE

### acfsutil sec save

#### Purpose

Saves Oracle ACFS file system security metadata.

#### Syntax and Description

    acfsutil sec save -h
    acfsutil sec save -m mount_point -p file

`acfsutil` `sec` `save` `-h` displays help text and exits.

Table 16-80 contains the options available with the `acfsutil` `sec` `save` command.

Table 16-80 Options for the acfsutil sec save command

| Option             | Description                                                                                                                    |
|:-------------------|:-------------------------------------------------------------------------------------------------------------------------------|
| `-m` `mount_point` | Specifies the directory where the file system is mounted.                                                                      |
| `-p` `file`        | Specifies a file name to store the security metadata. The file is saved in the `/``mount_point``/.Security/backup/` directory. |

The `acfsutil` `sec` `save` command saves the security metadata for an Oracle ACFS file system to an XML file. By default, the file is saved in the `/``mount_point``/.Security/backup` directory.

This file can be backed up as a regular file by a backup application. System realms protect this file and allow only members of these realms to access this file and prevent all other users including the root user and system administrator from access. For information about the system-created security realms, refer to "acfsutil sec prepare".

Only a security administrator can run this command.

#### Examples

The following example shows the use of the `acfsutil` `sec` `save` command.

Example 16-77 Using the acfsutil sec save command

    $ /sbin/acfsutil sec save -m /acfsmounts/acfs1 -p my_metadata_file.xml
