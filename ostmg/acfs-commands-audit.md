This topic provides a summary of the commands for Oracle ACFS auditing.

Table 16-44 lists the Oracle ACFS auditing commands with brief descriptions. For an overview of Oracle ACFS auditing, refer to [Oracle ACFS Auditing](understand-acfs-admin.md).

For information about running Oracle ACFS `acfsutil` commands, refer to [About Using Oracle ACFS Command-Line Tools](steps-manage-acfs.md).

**Note:**

Starting with Oracle ACFS 19c (19.5), Oracle ACFS Security (Vault) and ACFS Auditing are deprecated. Deprecating certain clustering features with limited adoption enables Oracle to focus on improving core scaling, availability, and manageability across all features and functionality. Oracle ACFS Security (Vault) and Oracle ACFS Auditing are deprecated, and can be desupported in a future release.

Table 16-44 Summary of commands for Oracle ACFS auditing

| Command                | Description                                                           |
|:-----------------------|:----------------------------------------------------------------------|
| acfsutil audit archive | Forces an archival of the audit trail.                                |
| acfsutil audit disable | Disables auditing for Oracle ACFS encryption or security.             |
| acfsutil audit enable  | Enables auditing for Oracle ACFS encryption or security.              |
| acfsutil audit info    | Displays auditing information.                                        |
| acfsutil audit init    | Initializes auditing on an Oracle ACFS environment.                   |
| acfsutil audit purge   | Purges the audit trail for a specified file system.                   |
| acfsutil audit read    | Marks the audit trail to indicate that the audit trail has been read. |

### acfsutil audit archive

#### Purpose

Forces an archival of the audit trail for the current host on the specified Oracle ACFS file system.

#### Syntax and Description

    acfsutil audit archive -h
    acfsutil audit archive -m mount_point

`acfsutil` `audit` `archive` `-h` displays help text and exits.

Table 16-45 contains the options available with the `acfsutil` `audit` `archive` command.

Table 16-45 Options for the acfsutil audit archive command

| Option             | Description                                               |
|:-------------------|:----------------------------------------------------------|
| `-m` `mount_point` | Specifies the directory where the file system is mounted. |

You can use the `acfsutil` `audit` `archive` command to safely back up or remove audit data without the possibility of losing intermediate audit messages.

Only an audit manager can run this command.

#### Examples

The following example shows the use of the `acfsutil` `audit` `archive` command.

Example 16-40 Using the acfsutil audit archive command

    $ /sbin/acfsutil audit archive -m /acfsmounts/acfs1

### acfsutil audit disable

#### Purpose

Disables auditing for either Oracle ACFS encryption or security on a specified file system.

#### Syntax and Description

    acfsutil audit disable -h
    acfsutil audit disable -m mount_point -s {encr |sec}

`acfsutil` `audit` `disable` `-h` displays help text and exits.

Table 16-46 contains the options available with the `acfsutil` `audit` `disable` command.

Table 16-46 Options for the acfsutil audit disable command

| Option                 | Description                                                       |
|:-----------------------|:------------------------------------------------------------------|
| `-m` `mount_point`     | Specifies the directory where the file system is mounted.         |
| `-s` {`encr` \| `sec`} | Specifies whether to disable auditing for encryption or security. |

Only an audit manager can run this command.

#### Examples

The following example shows the use of the `acfsutil` `audit` `disable` command.

Example 16-41 Using the acfsutil audit disable command

    $ /sbin/acfsutil audit disable -m /acfsmounts/acfs1 -s encr

### acfsutil audit enable

#### Purpose

Enables auditing for either Oracle ACFS encryption or security on a specified file system.

#### Syntax and Description

    acfsutil audit enable -h
    acfsutil audit enable -m mount_point -s {encr |sec}

`acfsutil` `audit` `enable` `-h` displays help text and exits.

Table 16-47 contains the options available with the `acfsutil` `audit` `enable` command.

Table 16-47 Options for the acfsutil audit enable command

| Option                 | Description                                                      |
|:-----------------------|:-----------------------------------------------------------------|
| `-m` `mount_point`     | Specifies the directory where the file system is mounted.        |
| `-s` {`encr` \| `sec`} | Specifies whether to enable auditing for encryption or security. |

The `acfsutil` `audit` `enable` command may also create the `mount_point``/.Security/audit` directory, which is a location for audit source files. The audit directory is created when auditing first is enabled for a file system, as a result of either the `acfsutil` `encr` `set`, `acfsutil` `sec` `prepare`, or a`cfsutil` `audit` `enable` command.

Only an audit manager can run this command.

#### Examples

The following example shows the use of the `acfsutil` `audit` `enable` command.

Example 16-42 Using the acfsutil audit enable command

    $ /sbin/acfsutil audit enable -m /acfsmounts/acfs1 -s encr

### acfsutil audit info

#### Purpose

Displays auditing information.

#### Syntax and Description

    acfsutil audit info -h
    acfsutil audit info [-m mount_point ]

`acfsutil` `audit` `info` `-h` displays help text and exits.

Table 16-48 contains the options available with the `acfsutil` `audit` `info` command.

Table 16-48 Options for the acfsutil audit info command

| Option             | Description                                                          |
|:-------------------|:---------------------------------------------------------------------|
| `-m` `mount_point` | Optionally specifies the directory where the file system is mounted. |

Only an audit manager can run this command.

#### Examples

The following example shows the use of the `acfsutil` `audit` `info` command.

Example 16-43 Using the acfsutil audit info command

    $ /sbin/acfsutil audit info -m /acfsmounts/acfs1

    Auditing information for '/acfsmounts/acfs1':
    Audit trail size: 10MB
    Archive File: READ
    Audit Sources:
    Security: ENABLED
    Encryption: ENABLED

### acfsutil audit init

#### Purpose

Initializes Oracle ACFS auditing.

#### Syntax and Description

    acfsutil audit init -h
    acfsutil audit init -M audit_manager_group -A auditor_group

`acfsutil` `audit` `init` `-h` displays help text and exits.

Table 16-49 contains the options available with the `acfsutil` `audit` `init` command.

Table 16-49 Options for the acfsutil audit init command

| Option                     | Description                                                                                                                                                                                                                                                                                                                                                        |
|:---------------------------|:-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `-M` `audit_manager_group` | Specifies the operating system (OS) group which assigns users to the Oracle ACFS audit manager role. To achieve separation of duties, you should create a new group specifically for this purpose and this group should be different from the system administrator group, Oracle ACFS security administrator OS group, and the Oracle ACFS audit auditor OS group  |
| `-A` `auditor_group`       | Specifies the operating system (OS) group which assigns users to the Oracle ACFS audit auditor role. To achieve separation of duties, you should create a new group specifically for this purpose and this group should be different from the system administrator group, Oracle ACFS security administrator OS group, and the Oracle ACFS audit manager OS group. |

The `acfsutil` `audit` `init` command must be run by the system administrator before enabling auditing for any of the audit sources on a file system. The command sets up the required roles for auditing and must be run before any type of auditing can be enabled on a file system. After running the command, auditing is enabled by default for all features which use auditing.

Because you cannot choose a different OS group for either the Oracle ACFS audit manager or auditor after initialization, you should create new OS groups for these specific purposes before initializing Oracle ACFS auditing.

Only a system administrator can run this command.

#### Examples

The following example shows the use of the `acfsutil` `audit` `init` command.

Example 16-44 Using the acfsutil audit init command

    # /sbin/acfsutil audit init -M myaudit_mgr_grp -A myauditor_grp

### acfsutil audit purge

#### Purpose

Purges the audit trail for a specified file system.

#### Syntax and Description

    acfsutil audit purge -h
    acfsutil audit purge -m mount_point [-f]

`acfsutil` `audit` `purge` `-h` displays help text and exits.

Table 16-50 contains the options available with the `acfsutil` `audit` `purge` command.

Table 16-50 Options for the acfsutil audit purge command

| Option             | Description                                                                                                                                  |
|:-------------------|:---------------------------------------------------------------------------------------------------------------------------------------------|
| `-m` `mount_point` | Specifies the directory where the file system is mounted.                                                                                    |
| `-f`               | Forces the removal of the audit trail even if the audit auditor has not marked the file as read using the `acfsutil` `audit` `read` command. |

Only an audit manager can run this command.

#### Examples

The following example shows the use of the `acfsutil` `audit` `purge` command.

Example 16-45 Using the acfsutil audit purge command

    $ /sbin/acfsutil audit purge -m /acfsmounts/acfs1 -f

### acfsutil audit read

#### Purpose

Marks the audit trail to indicates to the audit manager that the log archive file for the current node has been reviewed, backed up as necessary, and is safe to purge.

#### Syntax and Description

    acfsutil audit read -h
    acfsutil audit read -m mount_point

`acfsutil` `audit` `read` `-h` displays help text and exits.

Table 16-51 contains the options available with the `acfsutil` `audit` `read` command.

Table 16-51 Options for the acfsutil audit read command

| Option             | Description                                               |
|:-------------------|:----------------------------------------------------------|
| `-m` `mount_point` | Specifies the directory where the file system is mounted. |

Only an audit auditor can run this command.

#### Examples

The following example shows the use of the `acfsutil` `audit` `read` command.

Example 16-46 Using the acfsutil audit read command

    $ /sbin/acfsutil audit read -m /acfsmounts/acfs1
