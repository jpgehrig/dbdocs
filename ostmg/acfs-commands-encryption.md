This topic provides a summary of the commands for Oracle ACFS encryption.

Table 16-81 lists the Oracle ACFS encryption commands with brief descriptions. For an overview of Oracle ACFS encryption, refer to [Oracle ACFS Encryption](understand-acfs-admin.md).

For information about running Oracle ACFS `acfsutil` commands, refer to [About Using Oracle ACFS Command-Line Tools](steps-manage-acfs.md).

Table 16-81 Summary of commands for Oracle ACFS encryption

| Command                   | Description                                                             |
|:--------------------------|:------------------------------------------------------------------------|
| acfsutil encr info        | Displays encryption-related information about Oracle ACFS file systems. |
| acfsutil encr init        | Creates storage for encryption keys.                                    |
| acfsutil encr off         | Disables encryption for an Oracle ACFS file system.                     |
| acfsutil encr on          | Encrypts an Oracle ACFS file system.                                    |
| acfsutil encr rekey       | Generates a new key and re-encrypts an Oracle ACFS file system.         |
| acfsutil encr set         | Sets or changes encryption parameters for an Oracle ACFS file system.   |
| acfsutil keystore migrate | Migrates the encryption keystore.                                       |

### acfsutil encr info

#### Purpose

Displays encryption-related information about Oracle ACFS file systems, directories, or files.

#### Syntax and Description

    acfsutil encr info -h
    acfsutil encr info -m mount_point [[-r] path [path …]]

`acfsutil` `encr` `info` `-h` displays help text and exits.

Table 16-82 contains the options available with the `acfsutil` `encr` `info` command.

Table 16-82 Options for the acfsutil encr info command

| Option             | Description                                                                               |
|:-------------------|:------------------------------------------------------------------------------------------|
| `-m` `mount_point` | Specifies the directory where the file system is mounted.                                 |
| `-r`               | Specifies recursive action under an existing directory folder identified by `path`.       |
| `path`             | Specifies the absolute or relative path of a directory. Multiple path values are allowed. |

If `-m` is specified without a `path`, the encryption status, algorithm, and key length are displayed for the file system level.

If `-r` is specified with a `path`, the encryption status, algorithm, and key length are displayed for all objects under the directory specified by `path`.

The `acfsutil` `encr` `info` command displays encryption status and parameters for files in a snapshot if the files are specified with the `path` option.

This command fails when it is run on realm-secured objects.

Any user can run this command to display encryption information about a file system, directory, or file.

If the `acfsutil` `encr` `info` command is run as a system administrator, then the output displays the types of keystore used. The types are single-sign-on wallet in the OCR (SSO), password-protected wallet in the OCR (PKS), and Oracle Key Vault as the key store (OKV).

#### Examples

The following are examples of the use of `acfsutil` `encr` `info`.

Example 16-78 Using the acfsutil encr info command

    # /sbin/acfsutil encr info -m /acfsmounts/acfs1

    # /sbin/acfsutil encr info -m /acfsmounts/acfs1
                               -r /acfsmounts/acfs1/myfiles

### acfsutil encr init

#### Purpose

Creates storage for encryption keys.

#### Syntax and Description

    acfsutil encr init -h
    acfsutil encr init [-p ]

`acfsutil` `encr` `init` `-h` displays help text and exits.

Table 16-83 contains the options available with the `acfsutil` `encr` `init` command.

Table 16-83 Options for the acfsutil encr init command

| Option | Description                                         |
|:-------|:----------------------------------------------------|
| `-p`   | Creates PKCS (password-protected) storage for keys. |

The `acfsutil` `encr` `init` command must be run before any other encryption `acfsutil` commands can be run. This command must be run once for each cluster on which Oracle ACFS encryption is run.

If you plan to use Oracle Key Vault as the key store, then you still must run `acfsutil` `encr` `init` first.

**See Also:**

[Oracle Key Vault Administrator's Guide](https://docs.oracle.com/pls/topic/lookup?ctx=en/database/oracle/oracle-database/19/ostmg&id=OKVAG10489) for information about Oracle Key Vault

If the `-p` option is specified, you must provide a password when prompted. The password must conform to the format that is described in "[acfsutil sec init](acfs-commands-security.md)".

If the `-p` option is not specified, a single sign-on (SSO) wallet is created.

Only a user with root or system administrator privileges can run this command.

#### Examples

The following is an example of the use of `acfsutil` `encr` `init`.

Example 16-79 Using the acfsutil encr init command

    # /sbin/acfsutil encr init

### acfsutil encr off

#### Purpose

Disables encryption for an Oracle ACFS file system, directories, or individual files.

#### Syntax and Description

    acfsutil encr off -h
    acfsutil encr off -m mount_point [[-r] path [ path ...]]

`acfsutil` `encr` `off` `-h` displays help text and exits.

Table 16-85 contains the options available with the `acfsutil` `encr` `off` command.

Table 16-84 Options for the acfsutil encr off command

| Option             | Description                                                                                   |
|:-------------------|:----------------------------------------------------------------------------------------------|
| `-m` `mount_point` | Specifies the directory where the file system is mounted.                                     |
| `-r`               | Specifies to disable encryption recursively under an existing directory identified by `path`. |
| `path`             | Specifies the absolute or relative path of a directory. Multiple path values are allowed.     |

This command cannot be run on security realm-protected files.

Only an administrator can run this command on an Oracle ACFS file system (`-m` option without a `path` specified). When the `-m` option is specified without a `path`, all the files under the mount point are decrypted.

The `path` option can specify a path to a file or directory in a read-write snapshot. If the `-r` option is specified with the command on the root directory, the command does not transverse the snapshots under the `.ACFS` directory. If a decryption operation is specified at the file system level, then the operation does not process files and directories of snapshots in the `.ACFS/snaps/` directory.

Only a user with root or system administrator privileges can run this command to disable encryption on a file system. The file owner can also run this command to disable encryption on a directory or file.

#### Examples

The following are examples of the use of `acfsutil` `encr` `off`.

Example 16-80 Using the acfsutil encr off command

    # /sbin/acfsutil encr off -m /acfsmounts/acfs1

    # /sbin/acfsutil encr off -m /acfsmounts/acfs1
                              -r /acfsmounts/acfs1/myfiles

### acfsutil encr on

#### Purpose

Encrypts an Oracle ACFS file system, directories, or individual files.

#### Syntax and Description

    acfsutil encr on -h
    acfsutil encr on -m mount_point
              [-a {AES} -k {128|192|256}] [[-r] path [path...]]

`acfsutil` `encr` `on` `-h` displays help text and exits.

Table 16-85 contains the options available with the `acfsutil` `encr` `on` command.

Table 16-85 Options for the acfsutil encr on command

| Option             | Description                                                                                                                                                      |
|:-------------------|:-----------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `-m` `mount_point` | Specifies the directory where the file system is mounted.                                                                                                        |
| `-a` `algorithm`   | Specifies the encryption algorithm type for a directory or file. Advanced Encryption Standard (AES) is the only encryption algorithm supported for this release. |
| `-k` `key_length`  | Specifies the encryption key length for a directory or file.                                                                                                     |
| `-r`               | Specifies encryption recursively under existing directory folder identified by `path`.                                                                           |
| `path`             | Specifies the absolute or relative path of a directory. Multiple path values are allowed.                                                                        |

This command cannot be run on realm-protected files.

The default values for the `-a` and `-k` are determined by the volume parameters specified when `acfsutil` `encr` `set` was run. To set the key length at the volume level, use the `acfsutil` `encr` `set` command.

Only an administrator can run this command on an Oracle ACFS file system (`-m` option without a `path` specified). When the `-m` option is specified without a `path`, all the files under the mount point are encrypted.

The `path` option can specify a path to a file or directory in a read-write snapshot. If the `-r` option is specified with the command on the root directory, the command does not transverse the snapshots under the `.ACFS` directory. If an encryption operation is specified at the file system level, then the operation does not process files and directories of snapshots in the `.ACFS/snaps/` directory.

When you run `acfsutil` `encr` `on` with the `-r` option, the command encrypts the specified directory recursively, but does not enable encryption on the file system level.

Only a user with root or system administrator privileges can run this command to enable encryption on a file system. The file owner can also run this command to enable encryption on a directory or file.

#### Examples

The following are examples of the use of `acfsutil` `encr` `on`.

Example 16-81 Using the acfsutil encr on command

    # /sbin/acfsutil encr on -m /acfsmounts/acfs1

    # /sbin/acfsutil encr on -m /acfsmounts/acfs1
                             -a AES -k 128 -r /acfsmounts/acfs1/myfiles

### acfsutil encr rekey

#### Purpose

Generates a new key and re-encrypts volume or file.

#### Syntax and Description

    acfsutil encr rekey -h
    acfsutil encr rekey -m mount_point
        {-f [-r] path [path…] |-v } [-a {AES} -k {128|192 |256}]

`acfsutil` `encr` `rekey` `-h` displays help text and exits.

Table 16-86 contains the options available with the `acfsutil` `encr` `rekey` command.

Table 16-86 Options for the acfsutil encr rekey command

| Option                   | Description                                                                                                                                                                                                                                                                                                                                                                   |
|:-------------------------|:------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `-m` `mount_point`       | Specifies the directory where the file system is mounted.                                                                                                                                                                                                                                                                                                                     |
| `-f` \[`-r`\] `path` ... | Generates a new file encryption key for the specified path and then encrypts the data with the new key.<br>If -r is specified, the rekey operation is performed recursively under `path`.<br>`path` specifies the absolute or relative path of a directory. Multiple path values are allowed.                                                                                 |
| `-v`                     | Generates a new volume encryption key (VEK) for the specified mount point and then encrypts all the file encryption keys in file system with the new key. Prompts for the wallet password because the wallet must be accessed to store the new VEK.<br>The generated key is stored in the key store that was previously configured with the `acfsutil` `encr` `init` command. |
| `-a` `algorithm`         | Specifies the algorithm. Advanced Encryption Standard (AES) is the only encryption supported for this release.                                                                                                                                                                                                                                                                |
| `-k` `key_length`        | Specifies the key length for the directory or file specified by `path`.                                                                                                                                                                                                                                                                                                       |

This command cannot be run on security realm-protected files.

The default values for the `-a` and `-k` are determined by the volume parameters specified when `acfsutil` `encr` `set` was run.

The `path` option can specify a path to a file or directory in a read-write snapshot. If the `-r` option is specified with the command on the root directory, the command does not transverse the snapshots under the `.ACFS` directory. If a rekey operation is specified at the file system level, then the operation does not process files and directories of snapshots in the `.ACFS/snaps/` directory.

If Oracle Key Vault is the key store for the file system, then the Oracle Key Vault home environmental variable (`OKV_HOME`) must be set when using the `-v` option to generate a new volume key. If the client was configured to use a password with Oracle Key Vault, then the same password must be entered when prompted.

**See Also:**

[Oracle Key Vault Administrator's Guide](https://docs.oracle.com/pls/topic/lookup?ctx=en/database/oracle/oracle-database/19/ostmg&id=OKVAG10489) for information about Oracle Key Vault

Only a user with root or system administrator privileges can run this command with the `-v` option. The file owner can also run this command with the `-f` option to rekey encryption on the directory or file.

#### Examples

The following are examples of the use of `acfsutil` `encr` `rekey`.

Example 16-82 Using the acfsutil encr rekey command

    # /sbin/acfsutil encr rekey -m /acfsmounts/acfs1 -v

    # /sbin/acfsutil encr rekey -m /acfsmounts/acfs1 -f
                                -r /acfsmounts/acfs1/myfiles

### acfsutil encr set

#### Purpose

Sets or changes encryption parameters for an Oracle ACFS file system.

#### Syntax and Description

    acfsutil encr set -h
    acfsutil encr set [ [-a {AES} -k {128|192|256}] [-e] | -u ] -m mount_point

`acfsutil` `encr` `set` `-h` displays help text and exits.

Table 16-87 contains the options available with the `acfsutil` `encr` `set` command.

Table 16-87 Options for the acfsutil encr set command

| Option                     | Description                                                                                                                                                                                                                                                                                                                                                  |
|:---------------------------|:-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `-a` `algorithm`           | Specifies the algorithm. Advanced Encryption Standard (`AES`) is the default value and the only encryption supported for this release. The algorithm must be specified if `-k` is specified.                                                                                                                                                                 |
| `-k` {`128`\|`192`\|`256`} | Specifies the key length. The key length is set at the volume level. The default is `192`. Must be specified if `-a` is specified.                                                                                                                                                                                                                           |
| `-e`                       | Specifies to use Oracle Key Vault as the key store.                                                                                                                                                                                                                                                                                                          |
| `-u`                       | Backs out encryption. Decrypts all encrypted files in the file system and reverts the file system to the state before `acfsutil` `encr` `set` was run on the file system. If security is being used, then this command can only be run after security has been backed out. To remove security, refer to "[acfsutil sec prepare](acfs-commands-security.md)". |
| `-m` `mount_point`         | Specifies the directory where the file system is mounted.                                                                                                                                                                                                                                                                                                    |

Before running the `acfsutil` `encr` `set` command, you must first run the `acfsutil` `encr` `init` command.

The `acfsutil` `encr` `set` command configures encryption parameters for a file system, transparently generates a volume encryption key, and stores that the generated key in the key store that was previously configured with the `acfsutil` `encr` `init` command.

If auditing is initialized on a cluster, this command also enables an Oracle ACFS encryption auditing source on the file system. The actions performed when enabling this audit source are the same as those done when the `acfsutil` `audit` `enable` command is run directly. For more information, refer to "[acfsutil audit enable](acfs-commands-audit.md)".

In addition `acfsutil` `encr` `set` creates the `mount_point``/.Security``/encryption/logs/` directory that contains the log file (`encr-``hostname``_fsid.log`) that collects auditing and diagnostic data.

Password requirements when storing the key are dependent on how the encryption key storage was configured. If `-p` was specified with `acfsutil` `encr` `init`, then a password is required to run this command.

Before using the `-e` option to specify Oracle Key Vault as the key store, Oracle Key Vault must be configured first. If you want to choose Oracle Key Vault as the key store for the file system, then the Oracle Key Vault home environmental variable (`OKV_HOME`) must be set when running the command with the `-e` option. If the client was configured to use a password with Oracle Key Vault, then the same password must be entered when prompted.

**See Also:**

[Oracle Key Vault Administrator's Guide](https://docs.oracle.com/pls/topic/lookup?ctx=en/database/oracle/oracle-database/19/ostmg&id=OKVAG10489) for information about configuring Oracle Key Vault

The `acfsutil` `encr` `set` `–u` command is not allowed if any snapshots exist in the file system.

Only a user with root or system administrator privileges can run the `acfsutil` `encr` `set` command.

#### Examples

The following example shows the use of `acfsutil` `encr` `set` command.

Example 16-83 Using the acfsutil encr set command

    # /sbin/acfsutil encr set -a AES -k 256 -m /acfsmounts/acfs1

### acfsutil keystore migrate

#### Purpose

Migrates the encryption keystore.

#### Syntax and Description

    acfsutil keystore migrate -h
    acfsutil keystore migrate [-p ]

`acfsutil` `keystore migrate` `-h` displays help text and exits.

Table 16-83 contains the options available with the `acfsutil` `keystore migrate` command.

Table 16-88 Options for the acfsutil keystore migrate command

| Option | Description                                                          |
|:-------|:---------------------------------------------------------------------|
| `-p`   | Converts the encryption keystore from a SSO wallet to a PKCS wallet. |

If the `-p` option is specified, `acfsutil` `keystore` `migrate` converts the SSO wallet to a PKCS wallet. If the `-p` option is not specified, `acfsutil` `keystore` `migrate` converts the PKCS wallet to a SSO wallet.

Only a user with root or system administrator privileges can run this command.

#### Examples

The following is an example of the use of `acfsutil` `keystore` `migrate`.

Example 16-84 Using the acfsutil keystore migrate command

    # /sbin/acfsutil keystore migrate
