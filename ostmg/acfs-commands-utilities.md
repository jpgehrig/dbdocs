This topic provides a summary of the Oracle ACFS command-line utilities.

Table 16-122 lists the Oracle ACFS command-line utilities with brief descriptions.

For information about running Oracle ACFS `acfsutil` commands, refer to [About Using Oracle ACFS Command-Line Tools](steps-manage-acfs.md).

Table 16-122 Summary of Oracle ACFS command-line utilities

| Command                 | Description                                                                                                 |
|:------------------------|:------------------------------------------------------------------------------------------------------------|
| acfsutil accel replace  | Replaces an existing accelerator volume with a new one.                                                     |
| acfsutil compat get     | Displays the compatibility level of an Oracle ACFS file system.                                             |
| acfsutil compat set     | Changes the compatibility level of an Oracle ACFS file system.                                              |
| acfsutil defrag dir     | Defragments all the files in a specified directory.                                                         |
| acfsutil defrag file    | Defragments the specified files.                                                                            |
| acfsutil freeze         | Freezes modification activity temporarily in the file system.                                               |
| acfsutil info file      | Displays information for a file in an Oracle ACFS file system.                                              |
| acfsutil info fs        | Displays detailed Oracle ACFS file system information.                                                      |
| acfsutil info id        | Displays Oracle ACFS file system information for a specified file identifier and mount point.               |
| acfsutil info storage   | Displays space usage for the Oracle ASM, Oracle ACFS, and Oracle ADVM components in Oracle ASM disk groups. |
| acfsutil plugin disable | Disables the Oracle ACFS plug-in infrastructure.                                                            |
| acfsutil plugin enable  | Enables the Oracle ACFS plug-in infrastructure.                                                             |
| acfsutil plugin info    | Displays information about the Oracle ACFS plug-in infrastructure.                                          |
| acfsutil registry       | Adds, deletes, or displays entries in the Oracle ACFS mount registry.                                       |
| acfsutil rmfs           | Removes an Oracle ACFS file system.                                                                         |
| acfsutil scrub          | Checks for and reports any inconsistencies in the metadata or file data.                                    |
| acfsutil size           | Resizes an Oracle ACFS file system.                                                                         |
| acfsutil thaw           | Resumes activity after an acfsutil freeze command has been issued on a file system.                         |
| acfsutil version        | Displays Oracle ACFS version information.                                                                   |
| advmutil canonical      | Displays the canonical name of an Oracle ADVM volume.                                                       |
| advmutil volinfo        | Displays information about Oracle ADVM volumes.                                                             |

### acfsutil accel replace

#### Purpose

Replaces an existing accelerator volume with a new one.

#### Syntax and Description

    acfsutil accel replace -h
    acfsutil accel replace -a new_accel_volume primary_volume

`acfsutil` `accel` `replace` `-h` displays help text and exits.

The following table contains the options available with the `acfsutil` `accel` `replace` command.

Table 16-123 Options for the acfsutil accel replace command

| Option                  | Description                                                                                 |
|:------------------------|:--------------------------------------------------------------------------------------------|
| `—a ``new_accel_volume` | Specifies the name of the new accelerator volume.                                           |
| `primary_volume`        | Specifies the name of the primary volume with which the Oracle ACFS file system is mounted. |

This command allows an administrator to replace an existing accelerator volume with a new accelerator volume. The command is useful if the current accelerator volume is full and cannot be grown, or to migrate an accelerator to a faster volume.

The file system must be unmounted on all nodes to use this command. The new accelerator must be at least as large as the existing accelerator. If new accelerator volume is larger than the existing accelerator volume, then the administrator should run `acfsutil` `resize` `-d` `new_accel_volume` after the file system is remounted following the `acfsutil` `accel` `replace` operation to enable Oracle ACFS to utilize the entire space of the new accelerator volume.

You must be the `root` user or an Oracle ASM administrator user to run this command.

The following example shows the use of the `acfsutil` `accel` `replace` command.

Example 16-117 Using the acfsutil accel replace command

    $ /sbin/acfsutil accel replace -a new_accelerator_volume my_primary_volume

### acfsutil compat get

#### Purpose

Displays the Oracle ACFS compatibility level for the file system and the `COMPATIBLE.ADVM` level for the disk group.

#### Syntax and Description

    acfsutil compat get -h
    acfsutil compat get mount_point

`acfsutil` `compat` `get` `-h` displays help text and exits.

The following table contains the options available with the `acfsutil` `compat` `get` command.

Table 16-124 Options for the acfsutil compat get command

| Option        | Description                                               |
|:--------------|:----------------------------------------------------------|
| `mount_point` | Specifies the directory where the file system is mounted. |

The `acfsutil` `compat` `get` command displays the Oracle ACFS compatibility level for the file system that may have been set by the `mkfs` command or the `acfsutil` `compat` `set` command. `acfsutil` `compat` `get` also displays the `COMPATIBLE.ADVM` setting for the disk group, which is default compatibility level for the file system if not otherwise explicitly set. For information about Oracle ASM disk group compatibility attributes, see [Disk Group Compatibility](diskgroup-compatibility.md).

#### Examples

The following example shows the use of the `acfsutil` `compat` `get` command.

Example 16-118 Using the acfsutil compat get command

    $ /sbin/acfsutil compat get /acfsmounts/acfs1

### acfsutil compat set

#### Purpose

Change the compatibility level of an Oracle ACFS file system.

#### Syntax and Description

    acfsutil compat set -h
    acfsutil compat set -c release_version mount_point

`acfsutil` `compat` `set` `-h` displays help text and exits.

The following table contains the options available with the `acfsutil` `compat` `set` command.

Table 16-125 Options for the acfsutil compat set command

| Option                 | Description                                                                              |
|:-----------------------|:-----------------------------------------------------------------------------------------|
| `—c ``release_version` | Specifies the release version for the Oracle ACFS file system determined by mount_point. |
| `mount_point`          | Specifies the directory where the file system is mounted.                                |

The value specified with the `-c ``release_version` option must be greater than or equal to the value of `COMPATIBLE.ADVM` for the disk group, and must be less than or equal to the running Oracle Grid infrastructure release version. If `—c ``release_version` is not specified, the value of `COMPATIBLE.ADVM` is used. After the compatibility is set, it cannot be downgraded. The `—c ``release_version` option can be used in situations where it is not possible, or desirable, to update `COMPATIBLE.ADVM` and `COMPATIBLE.ASM` for the disk group, but you want to use an Oracle ACFS feature that requires a compatibility increase. After the Oracle ACFS compatibility is updated, it is no longer possible to mount the file system with an older Oracle Grid infrastructure release. For information about Oracle ASM disk group compatibility attributes, see "[Disk Group Compatibility](diskgroup-compatibility.md)".

The following example shows the use of the `acfsutil` `compat` `set` command.

Example 16-119 Using the acfsutil compat set command

    $ /sbin/acfsutil compat set -c 12.2 /acfsmounts/acfs1

### acfsutil defrag dir

#### Purpose

Defragments all the files in a specified directory.

#### Syntax and Description

    acfsutil defrag dir -h
    acfsutil defrag dir [-r] dir_path

`acfsutil defrag dir` `-h` displays help text and exits.

Table 16-126 contains the options available with the `acfsutil defrag dir` command.

Table 16-126 Options for the acfsutil defrag dir command

| Option     | Description                                                             |
|:-----------|:------------------------------------------------------------------------|
| `—r`       | Specifies recursive defragment operation.                               |
| `dir_path` | Specifies the directory where the files to be defragmented are located. |

The `acfsutil defrag dir` command is used to defragment files in the specified subdirectory. The `—r` option is used to recursively defragment files in the subdirectories of the specified directory.

You must have write access to the files to be defragmented.

Administrator privileges are required to use this command or you must be a member of the Oracle ASM administrator group.

#### Examples

Example 16-120 shows the use of the `acfsutil defrag dir` command.

Example 16-120 Using the acfsutil defrag dir command

    $ /sbin/acfsutil defrag dir /acfsmounts/critical_apps/01jan1015

### acfsutil defrag file

#### Purpose

Defragments the specified files.

#### Syntax and Description

    acfsutil defrag file -h
    acfsutil defrag file [-i] file_path [file_path ... ]

`acfsutil defrag file` `-h` displays help text and exits.

Table 16-127 contains the options available with the `acfsutil defrag file` command.

Table 16-127 Options for the acfsutil defrag file command

| Option      | Description                                                                              |
|:------------|:-----------------------------------------------------------------------------------------|
| `—i`        | Estimates the reduction in number of extents possible. Requires read access to the file. |
| `file_path` | Specifies the file to be defragmented.                                                   |

The `acfsutil defrag file` command defragments files. The `—i` option displays the estimated reduction in the number of extents for the files to be defragmented.

You must have write access to the files to be defragmented.

Administrator privileges are required to use this command or you must be a member of the Oracle ASM administrator group.

#### Examples

Example 16-121 shows the use of the `acfsutil defrag file` command.

Example 16-121 Using the acfsutil defrag file command

    $ /sbin/acfsutil defrag file /acfsmounts/critical_apps/testfile

### acfsutil freeze

#### Purpose

Freezes modification activity temporarily in the file system.

#### Syntax and Description

    acfsutil freeze -h
    acfsutil freeze [-f] mount_point

`acfsutil` `freeze` `-h` displays help text and exits.

The following table contains the options available with the `acfsutil` `freeze` command.

Table 16-128 Options for the acfsutil freeze command

| Option        | Description                                                                  |
|:--------------|:-----------------------------------------------------------------------------|
| `—f`          | Specifies the command to flush data to disk before freezing the file system. |
| `mount_point` | Specifies the directory where the file system is mounted.                    |

The `acfsutil` `freeze` command temporarily halts modification activity on a file system. You can use `acfsutil` `freeze` to create point-in-time images across different snapshots without stopping applications. To resume activity after the `acfsutil` `freeze` command has been issued on a file system, run the `acfsutil` `thaw` command. For information about `acfsutil` `thaw`, refer to acfsutil thaw.

Use the `acfsutil` `freeze` command with caution to prevent application timeouts and possible instance evictions. If a database or database diagnostic area is running on an Oracle ACFS file system and the file system is frozen for more than three minutes, the database instance can be terminated due to processes that are hung while waiting to update files on the file system.

Using the `acfsutil` `freeze` command on a file system where Oracle ACFS replication is active may block replication operations if the operations modify on-disk replication configuration information or if the operations are updates to a frozen standby file system. Replication operations that are likely to be affected are:

- `acfsutil` `repl` `reverse` `standby`

- `acfsutil` `repl` `sync`

- `acfsutil` `repl` `terminate` `primary`

- `acfsutil` `repl` `terminate` `standby`

#### Examples

The following example shows the use of the `acfsutil` `freeze` command.

Example 16-122 Using the acfsutil freeze command

    $ /sbin/acfsutil freeze -f /acfsmounts/acfs1

### acfsutil info file

#### Purpose

Displays information for a file in an Oracle ACFS file system.

#### Syntax and Description

    acfsutil info file -h
    acfsutil info file [ [-d] [-o acfs_extent_offset] [-m] [-u] | [-c] ] path [path ... ]

`acfsutil` `info` `file` `-h` displays help text and exits.

Table 16-129 contains the options available with the `acfsutil` `info` `file` command.

Table 16-129 Options for the acfsutil info file command

| Option                    | Description                                                                                                                                         |
|:--------------------------|:----------------------------------------------------------------------------------------------------------------------------------------------------|
| `-d`                      | Displays detailed extent information, from Oracle ACFS to the Oracle ASM devices in the disk group.                                                 |
| `-o` `acfs_extent_offset` | `acfs_extent_offset` — Filters the extent display to the Oracle ACFS file offset specified.                                                         |
| `-c`                      | Displays extent counts only.                                                                                                                        |
| `-m`                      | Displays details about file metadata extents. The `-m` option is compatible with `-d`, `-o`, and `-u`. The `-m` option is not compatible with `-c`. |
| `-u`                      | Displays extent usage information.                                                                                                                  |
| `path`                    | Specifies the full path name of a file.                                                                                                             |

The `acfsutil` `info` `file` command displays information about a file in an Oracle ACFS file system. The information includes the extent map which details the locations of the blocks comprising the file and the used versus allocated storage for a file. Tagging information is also displayed for a file.

The `—u` option adds an additional column to the standard `acfsutil info file` output indicating whether or not the extent is inherited between a snapshot parent and child. The `-c` option displays the total extent count and the number of primary and accelerator volume extent nodes, while omitting the details of each individual extent. The output from the `—c` option is useful when you want to display the number of extents, and when using an accelerator, to ensure that the metadata is situated on the accelerator volume.

You must have read access to the specified file to run `acfsutil` `info` `file`.

#### Examples

The following is an example of the use of the `acfsutil` `info` `file` command.

Example 16-123 Using the acfsutil info file command

    $ /sbin/acfsutil info file /usmmnt/.ACFS/snaps/s1/afile
      /usmmnt/.ACFS/snaps/s1/afile
        flags:        File
        inode:        18014398509482029
        owner:        root
        group:        root
        size:         13013  (  12.71 KB )
        allocated:    24576  (  24.00 KB )
        hardlinks:    1
        device index: 1
        major, minor: 202,64
        access time:  Thu Jan  7 14:13:24 2016
        modify time:  Thu Jan  7 14:13:24 2016
        change time:  Thu Jan  7 14:13:24 2016
        extents:
            -offset ----length | -dev --------offset
                  0      24576 |    1      142188544
             extent count: 1
             granularity level: -1

    $ /sbin/acfsutil info file -c /usmmnt/.ACFS/snaps/s1/afile
      /usmmnt/.ACFS/snaps/s1/afile
        flags:        File
        inode:        18014398509482029
        owner:        root
        group:        root
        size:         13013  (  12.71 KB )
        allocated:    24576  (  24.00 KB )
        hardlinks:    1
        device index: 1
        major, minor: 202,64
        access time:  Thu Jan  7 14:13:24 2016
        modify time:  Thu Jan  7 14:13:24 2016
        change time:  Thu Jan  7 14:13:24 2016
        extents:
             extent count: 1
             primary volume extent nodes:     0
             accelerator volume extent nodes: 0
             granularity level: -1

    $ /sbin/acfsutil info file -u /usmmnt/.ACFS/snaps/s1/afile
      /usmmnt/.ACFS/snaps/s1/afile
        flags:        File
        inode:        18014398509482029
        owner:        root
        group:        root
        size:         13013  (  12.71 KB )
        allocated:    24576  (  24.00 KB )
        hardlinks:    1
        device index: 1
        major, minor: 202,64
        access time:  Thu Jan  7 14:13:24 2016
        modify time:  Thu Jan  7 14:13:24 2016
        change time:  Thu Jan  7 14:13:24 2016
        extents:
            -offset ----length | -dev --------offset | inherited
                  0      24576 |    1      142188544 | Yes
             extent count: 1
             added extent count: 0
             inherited extent count: 1
             granularity level: -1

### acfsutil info fs

#### Purpose

Displays detailed Oracle ACFS file system information.

#### Syntax and Description

    acfsutil info fs -h
    acfsutil info fs [-l] [{-o option_item | -s [interval[count][-d]] | -f [-v]}]
                     [mount_point]

`acfsutil` `info` `fs` `-h` displays help text and exits.

Table 16-130 contains the options available with the `acfsutil` `info` `fs` command.

Table 16-130 Options for the acfsutil info fs command

| Option                                  | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    |
|:----------------------------------------|:---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `-l`                                    | Displays symbolic links for an Oracle ACFS file system specified by the mount point or displays symbolic links for all mounted Oracle ACFS file systems if a mount point is not specified.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                     |
| `-o`                                    | Displays the specific file system option item from the following list:<br>• `allvolumes [``mount_point`` | ``primary_volume_device`` | ``auxiliary_volume_device``]` — Lists all volumes that are associated with a file system.<br>• `autoresize` — 1 if automatic resize is enabled, 0 if not.<br>• `autoresizeincrement` — Lists the automatic resize increment for the file system.<br>• `autoresizemax` — Lists the automatic resize maximum.<br>• `auxvolume {``mount_point`` | ``primary_volume_device``}` — Lists the auxiliary volumes associated with the file system. Can be run against a mount point or device.<br>• `available` - Length of time the file system has been available.<br>• `compatacfs` — Lists the ACFS compatibility setting<br>• `compatadvm` — Lists the ADVM compatibility setting.<br>• `diskgroup` - Name of the disk group associated with `path`.<br>• `fetasize` - File entry table size which is the amount of storage consumed by the on disk metadata for inodes.<br>• `freespace` - Amount of free space available in the file system.<br>• `isadvm` - 1 if an Oracle ADVM volume is present, 0 if not.<br>• `isauxvolume {``volume_device``}` — 1 if a volume is an auxiliary volume or 0 if not. Must be run against a volume device.<br>• `isavailable` - 1 if the file system is available, 0 if file system is not available.<br>• `iscompression` — State of compression on the file system. 1 for enabled, 0 for disabled.<br>• `iscorrupt` - 1 if the file system is corrupt, 0 if file system is not corrupt.<br>• `isencryption` — State of encryption on the file system, 0 for disabled, 1 for enabled. |
| `-o` (continued)                        | • `ismountpoint` - 1 if `path` is the mount point, 0 if `path` is not a mount point.<br>• `isreplprimary` - 1 if primary file system, 0 if not.<br>• `isreplstandby` - 1 if standby file system, 0 if not.<br>• `issecurity` — State of security on the file system, 0 for disabled, 1 for enabled.<br>• `metablocksize` — Size of metadata blocks on the file system.<br>• `mountpoints` - Mount points associated with file systems.<br>• `primaryvolume` - Path name of the device associated with file system.<br>• `redundancy` - Type of redundancy used by the Oracle ADVM volume.<br>• `replication` - 1 if file system has been initialized for replication as the primary or standby file system, 0 if not initialized for replication.<br>• `resizeincrement` - Allocation unit size in bytes of the Oracle ADVM volume used by `path`.<br>• `stripewidth` - Stripe width for the Oracle ADVM volume used by `path`.<br>• `stripecolumns` - Stripe set columns for the Oracle ADVM volume used by `path`.<br>• `totalspace` - Size of the file system.<br>• `volumes` - Number of volumes associated with the file system.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          |
| `-s` \[`interval` \[`count`\] \[`-d]`\] | Displays file system statistics.<br>The optional `interval` parameter specifies the amount of time in seconds between each report. The first report contains statistics for the time since the file system mount. Each subsequent report contains statistics collected during the interval since the previous report.<br>The optional `count` parameter can be specified with the `interval` parameter. If the `count` parameter is specified, the value of count determines the number of reports generated at interval seconds apart.<br>If the `interval` parameter is specified without the `count` parameter, the command generates reports continuously until you break out of the command with `Ctrl+c`.<br>The optional `-d` option displays more detailed statistical information.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    |
| `-f` \[`-v`\]                           | Displays file system fragmentation. The `-v` option displays additional fragmentation information.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             |
| `mount_point`                           | Specifies the directory where the file system is mounted. Not a valid option for replication data.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             |

`acfsutil` `info` `fs` displays information and statistics about Oracle ACFS file systems. If compression, encryption, security, or replication has been initiated on a file system, additional flags and status information are displayed.

The `-o` `option_item` option displays file system information for the `option_item` specified.

The `-s` option displays the amount and rate of change currently on a file system for the node that the command is run on.

With no option specified, the command displays file system information that includes the volume device name, the size of the file system, the amount of space available on the volume device, the file system mount time on this node, the state of the file system, the user specified block size, the number of Oracle ACFS snapshots, the space consumed by snapshots in the file system, and the optional name or volume label associated with the file system. The possible file system states are displayed in the `flags` line. These states include:

- `Offline` indicates that the underlying devices are not accessible, possibly due to an Oracle ASM instance failure, disk group forced dismount, or an irrecoverable I/O error. The file system on this node can only be dismounted. All other attempts at access result in errors.

- `Available` indicates that the file system is on line and operational.

- `Corrupt` indicates that the file system should be checked and repaired at the earliest possible convenience to correct a detected inconsistency. For example, run the `fsck` command on Linux or the `acfschkdsk` command on Windows to check and repair the file system. Ensure that you run the command in repair mode to correct the problem. For more information, refer to "[fsck (offline mode)](acfs-commands-linux.md)" and "[acfschkdsk](acfs-commands-windows.md)".

When viewing space usage values with `acfsutil` `info` `fs` on Windows systems, the values may differ from sizes in Windows folders. The mechanism used by Folder Properties on Windows systems only accounts for files and should be considered an approximate value.

Any user can run `acfsutil` `info` `fs`.

#### Examples

The following are examples of the use of `acfsutil` `info` `fs`.

Example 16-124 displays information about an Oracle ACFS file system in a Linux environment.

Example 16-124 Using the acfsutil info fs command on Linux

    $ /sbin/acfsutil info fs
    /primary
        ACFS Version: 11.2.0.2.0
        flags:        MountPoint,Available,Replication
        mount time:   Mon Oct 25 12:11:03 2010
        volumes:      1
        total size:   5368709120
        total free:   4144230400
        primary volume: /dev/asm/pvol-74
            label:
            flags:                 Primary,Available,ADVM
            on-disk version:       40.0
            allocation unit:       4096
            major, minor:          252, 37889
            size:                  5368709120
            free:                  4144230400
            ADVM diskgroup         REPLDG
            ADVM resize increment: 268435456
            ADVM redundancy:       unprotected
            ADVM stripe columns:   4
            ADVM stripe width:     131072
        number of snapshots:  0
        snapshot space usage: 0
        replication status: primary

    /standby
        ACFS Version: 11.2.0.2.0
        flags:        MountPoint,Available,Replication
        mount time:   Mon Oct 25 12:11:03 2010
        volumes:      1
        total size:   5368709120
        total free:   5263945728
        primary volume: /dev/asm/svol-74
            label:
            flags:                 Primary,Available,ADVM
            on-disk version:       40.0
            allocation unit:       4096
            major, minor:          252, 37890
            size:                  5368709120
            free:                  5263945728
            ADVM diskgroup         REPLDG
            ADVM resize increment: 268435456
            ADVM redundancy:       unprotected
            ADVM stripe columns:   4
            ADVM stripe width:     131072
        number of snapshots:  0
        snapshot space usage: 0
        replication status: standby

    $ /sbin/acfsutil info fs -o mountpoints,replication
    /primary
    1
    /standby
    1

    $ /sbin/acfsutil info fs -o mountpoints,isreplprimary
    /primary
    1
    /standby
    0

    $ /sbin/acfsutil info fs -o mountpoints,isreplstandby
    /primary
    0
    /standby
    1

Example 16-125 illustrates the use of `acfsutil` `info` `fs` in a Windows environment.

Example 16-125 Using the acfsutil info fs command on Windows

    C:\oracle>acfsutil info fs /o freespace c:\oracle\acfsmounts\acfs1
    968667136

    C:\oracle>acfsutil info fs /o totalspace c:\oracle\acfsmounts\acfs1
    1073741824

    C:\oracle>acfsutil info fs /o volumes c:\oracle\acfsmounts\acfs1
    1

    C:\oracle>acfsutil info fs /o primaryvolume c:\oracle\acfsmounts\acfs1
    asm-volume1-311

    C:\oracle>acfsutil info fs /o diskgroup c:\oracle\acfsmounts\acfs1
    DATA

    C:\oracle>acfsutil info fs /o redundancy c:\oracle\acfsmounts\acfs1
    mirror

Example 16-126 illustrates the use of `acfsutil` `info` `fs` with `-s` option to display the current amount and rate of change on a file system.

Example 16-126 Using the acfsutil info fs command with the -s option

    $ /sbin/acfsutil info fs -s /acfsmounts/acfs1
        amount of change since mount:       359.22 MB
        average rate of change since mount: 3 KB

    $ /sbin/acfsutil info fs -s 60 4 /acfsmounts/acfs1
        amount of change since mount:       359.22 MB
        average rate of change since mount: 3 KB/s

        amount of change: 15.02 MB   rate of change: 256 KB/s
        amount of change: 9.46 MB   rate of change: 161 KB/s
        amount of change: 7.32 MB   rate of change: 125 KB/s
        amount of change: 6.89 MB   rate of change: 117 KB/s
    ...

### acfsutil info id

#### Purpose

Displays Oracle ACFS file system information for a specified file identifier number and mount point.

#### Syntax and Description

    acfsutil info id -h
    acfsutil info id file_identifier mount_point

`acfsutil` `info` `id` `-h` displays help text and exits.

Table 16-131 contains the options available with the `acfsutil` `info` `id` command.

Table 16-131 Options for the acfsutil info id command

| Option            | Description                                                                                                                                            |
|:------------------|:-------------------------------------------------------------------------------------------------------------------------------------------------------|
| `mount_point`     | Specifies the directory where the file system is mounted.                                                                                              |
| `file_identifier` | Specifies the Oracle ACFS file identifier number reported by the Oracle ACFS driver. The file identifier number should be specified in decimal format. |

You can use `acfsutil` `info` `id` to translate an internal numeric Oracle ACFS file identifier to a path name in the file system. This is useful when the Oracle ACFS driver reports I/O errors to the system event logger associated with a particular file in an Oracle ACFS and identifies it by its internal identifier. You must have administrator privileges or you must be a member of the Oracle ASM administrator group to run `acfsutil` `info` `id`.

#### Examples

The following is an example of `acfsutil` `info` `id`.

Example 16-127 Using the acfsutil info id command

    $ /sbin/acfsutil info id 117 /acfsmounts/acfs1

### acfsutil info storage

#### Purpose

Displays space usage for the Oracle ASM, Oracle ACFS, and Oracle ADVM components in Oracle ASM disk groups.

#### Syntax and Description

    acfsutil info storage -h
    acfsutil info storage [-u {B|MB|GB|TB}] [-l] [disk_group,...]

`acfsutil` `info` `storage` `-h` displays help text and exits.

The following table contains the options available with the `acfsutil` `info` `storage` command.

Table 16-132 Options for the acfsutil info storage command

| Option                          | Description                                                                                                                                                           |
|:--------------------------------|:----------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `-u`<br>{`B`\|`MB`\|`GB`\|`TB`} | Specifies the unit of measurement.<br>Specifies that the space usage values are in units of `B` (kilobytes), `MB` (megabytes), `GB` (gigabytes), or `TB` (terabytes). |
| `-l`                            | Displays more detailed space information for the Oracle ASM disk group, the Oracle ADVM volume, and the Oracle ACFS file system.                                      |
| `disk_group`                    | Specifies the disk group or disk groups for which space usage is displayed. If a disk group is not specified, then information for all disk groups is displayed.      |

`acfsutil` `info` `storage` provides a platform independent way to view how the space in an Oracle ASM disk group is being consumed by components of Oracle ASM, Oracle ACFS, and Oracle ADVM.

This command gathers the space information from multiple sources, including `V$ASM_DISKGROUP`, `V$ASM_FILE`, `acfsutil` `snap` `info`, and `acfsutil` `info` `fs`. Each line in the summary output displays the primary Oracle ACFS consumers of storage in a disk group.

For each disk group, all information for that disk group is grouped together. The `%` `Free` column is calculated using the `Space` and the `Usable` `Free` columns. For `NORMAL` and `HIGH` redundancy disk groups, the `Usable` `Free` column displays the unused portion of the disk group after accounting for mirroring. For `FLEX` or `EXTENDED` disk group, the `Usable` `Free` column reports the raw total free space as the redundancy is flexible and can vary.

The `Consumer` and `Path` columns are always empty on the line that displays information for the disk group. The `Consumer` column is populated on the lines for the consumers of storage in the disk group.

If a volume is enabled, then the volume name is displayed in the `Consumer` column. The `Space` column displays the current size of the volume. The `Usable` `Free` column displays the amount of free space in the file system if the volume is part of an Oracle ACFS file system or part of a mounted non-Oracle ACFS file system. The `Path` column displays the mount point if the volume is part of a mounted file system. The `Path` column displays `*ACFS`if the volume is part of an unmounted Oracle ACFS file system.

If a snapshot exists in the Oracle ACFS file system associated with the previously listed volume, then the snapshot name is displayed on the next line in the `Consumer` column. The `Space` column associated with a snapshot is always marked with an asterisk (`*`) because the space used by a snapshot in the file system has been accounted for in the volume line. The `Size` `With` `Mirroing` column associated with a snapshot represents the space currently being used by that snapshot in the file system. If a snapshot quota has been established, then the `Usable` `Free` column displays the amount of free space left before for that snapshot reaches the quota. If a snapshot quota has not been set, then this column is empty. The `Path` column for a snapshot is a full path to the root of the snapshot. If a snapshot link has been established, then the snapshot link is displayed in the `Path` column.

`root` or users who are members of the `asmadmin` group can run this command. For information about operating system group privileges, see [About Privileges for Oracle ASM](authenticate-access-asm-instance.md).

#### Examples

The following example shows the use of `acfsutil` `info` `storage` to display space usage information in both summary and long format.

Example 16-128 Using the acfsutil info storage command

    $ /sbin/acfsutil info storage -u MB
    Diskgroup      Consumer      Space     Size With Mirroring  Usable Free  %Free   Path
    DATA                       4608.00            2304.00         895.00       38%
                       VOL1    2048.00            1024.00         831.45       81%   /acfsmnt
                     052317          *               0.25                            /acfsmnt/latest
                     052217          *             131.26         893.00       87%   /acfsmnt/.ACFS/snaps/052217
    FLASH                      2048.00            1024.00         147.00       14%
                  ACCELVOL1    1024.00             512.00         260.92       50%   ACCEL for VOL1 in DATA
    TST                        2048.00            1024.00         143.00       13%
                       VOL1    1024.00             512.00         512.00      100%
    ----
    unit of measurement: MB

    $ /sbin/acfsutil info storage -l

    Diskgroup: DATA (38% free)
      total disk space:           4.50
      ASM file space:             2.05
      total free space:           2.25
      net free with mirroring:    1.12
      usable after reservation:   0.87
      redundancy type:          NORMAL

        Total space used by ASM non-volume files:
          used:                      0.00
          mirror used:               0.00

        volume: /dev/asm/vol1-447
          total:                     1.00
          free:                      0.81
          redundancy type:         mirror
          file system:             /acfsmnt
            snapshot: 052317 (/acfsmnt/latest)
              used:          0.00
              quota limit:   none
            snapshot: 052217 (/acfsmnt/.ACFS/snaps/052217)
              used:          0.13
              quota limit:   1.00

    ...

    ----
    unit of measurement: GB

### acfsutil plugin disable

#### Purpose

Disables the Oracle ACFS plug-in infrastructure for an Oracle ACFS file system.

#### Syntax and Description

    acfsutil plugin disable -h
    acfsutil plugin disable mount_point

`acfsutil` `plugin` `disable` `-h` displays help text and exits.

Table 16-133 contains the options available with the `acfsutil` `plugin` `disable` command.

Table 16-133 Options for the acfsutil plugin disable command

| Option        | Description                                               |
|:--------------|:----------------------------------------------------------|
| `mount_point` | Specifies the directory where the file system is mounted. |

`acfsutil` `plugin` `disable` disables the collection of Oracle ACFS plug-in metrics and the associated communication with a plug-in application.

Administrator privileges are required to use this command or you must be a member of the Oracle ASM administrator group.

#### Examples

Example 16-129 shows the use of the `acfsutil` `plugin` `disable` command. After monitoring has completed for the Oracle ACFS file metric data for the file system mounted on the `/humanresources`, the command in Example 16-129 disables the subsequent collection of summary data in the Oracle ACFS driver.

Example 16-129 Disabling the Oracle ACFS driver

    # /sbin/acfsutil plugin disable /humanresource

**See Also:**

- [About Using Oracle ACFS Command-Line Tools](steps-manage-acfs.md) for information about running Oracle ACFS `acfsutil` commands

- [Oracle ACFS Plugins](understand-acfs-admin.md) for an overview of Oracle ACFS plug-ins

- [Oracle ACFS Plug-in Generic Application Programming Interface](acfs-advanced-topics.md) for information about the Oracle ACFS plug-in application programming interface

### acfsutil plugin enable

#### Purpose

Enables the Oracle ACFS plug-in infrastructure for an Oracle ACFS file system.

#### Syntax and Description

    acfsutil plugin enable -h
    acfsutil plugin enable -m metrictype [-t tag, ...]
                           [-i interval[s|m]] mount_point

`acfsutil` `plugin` `enable` `-h` displays help text and exits.

Table 16-134 contains the options available with the `acfsutil` `plugin` `enable` command.

Table 16-134 Options for the acfsutil plugin enable command

| Option                       | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          |
|:-----------------------------|:---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `-t` `tag`, ...              | An optional list of tag names selecting Oracle ACFS files that you want to be monitored. The maximum number of tags is 12. The names are separated by commas. The default is to monitor all files in the Oracle ACFS file system.<br>The tag names are managed by the Oracle ACFS tagging APIs.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      |
| `-m` `metrictype`            | Selects the message payload to be transmitted from Oracle ACFS to the plug-in module with each call-out message. Oracle ACFS provides the `acfsmetric1` and `acfsmetric2` pre-defined metric types.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  |
| `-i` `interval` \[`s`\|`m`\] | Selects posting message delivery and the posting interval. The Oracle ACFS plug-in mechanism posts a metrics message during each specified message interval.<br>An interval is the maximum amount of time which can pass before metrics are posted. The application blocks in the API call to retrieve metrics until a posting occurs.<br>The interval can be specified as an integer value in `s` seconds or `m` minutes. The default is minutes. The maximum value allowed for an interval is 60 minutes or 3600 seconds.<br>If an interval is specified, then Oracle ACFS is requested to post metrics messages to the plug-in application on an interval basis.<br>If an interval is not specified, then the application polls for metrics updates from the Oracle ACFS file system. This is the default action. |
| `mount_point`                | Specifies the directory where the file system is mounted.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            |

`acfsutil` `plugin` `enable` enables an Oracle ACFS file system for application plug-in service. Oracle ACFS plug-ins are enabled for single nodes only, either a standalone host or one or more individual nodes of a Grid Cluster. After enabled for plug-ins, the Oracle ACFS file system begins collecting metric information for either the set of specified tagged files or all files in the Oracle ACFS file system, and transmits callout messages to the plug-in application based upon the selected message payload and delivery parameters. Metrics are reset after every delivery to the application (whether through polling or posting).

In general, metrics are collected from the point of view of a user application. I/O for metadata or internal Oracle ACFS activities; such as snapshot copy-on-writing, encrypting, and replicating files; are not included. Metrics are collected for user I/O to both files in the original file system and snapshot files. Memory mapping of files that results in I/O operations is recorded in the metrics. Replication related files under the `.ACFS/repl` directory are not included in the metrics.

Oracle ACFS provides the `acfsmetric1` and `acfsmetric2` pre-defined metric types.

Administrator privileges are required to use this command or you must be a member of the Oracle ASM administrator group.

#### Examples

Example 16-130 shows the use of the `acfsutil` `plugin` `enable` command to provide additional storage usage metrics to a monitoring application.

Example 16-130 Enabling the Oracle ACFS driver for storage visibility: poll model

    # /sbin/acfsutil plugin enable -m acfsmetric1 -t HRDATA /humanresource

An Oracle ACFS file system mounted on `/humanresources` is to be enabled for plug-in service and configured with the objective of providing additional storage usage metrics to a monitoring application. The message payload type is `acfsmetric1`, the files to be monitored are human resource files that have been tagged with the Oracle ACFS file tag `HRDATA`, and the message delivery type is `poll` which means that the application plug-in polls to request metric data update messages. No interval is specified with polled message delivery.

When the command in Example 16-130 completes, the Oracle ACFS file system mounted on the `/humanresources` mount point is enabled for plug-in communication and begins collecting Oracle ACFS file access metrics for files tagged with `HRDATA`. Oracle ACFS maintains metrics collecting a summary of read and write activity. Each time the associated application plug-in module polls for the metrics, Oracle ACFS sends a message with the data as defined in the `ACFS_METRIC1` structure that is a summary of the selected Oracle ACFS activity since either the Oracle ACFS driver plug-in functionality was enabled or since the last delivery of metric data.

Example 16-131 shows the use of the `acfsutil` `plugin` `enable` command to monitor movie file updates.

Example 16-131 Enabling the Oracle ACFS driver for storage visibility: post on interval model

    # /sbin/acfsutil plugin enable -m acfsmetric1 -t FILECONTENT -i 120s /moviemods

An Oracle ACFS file system mounted on `/moviemods` is enabled for plug-in service and is configured to record and deliver storage usage messages to a monitoring application. On an interval basis, the Oracle ACFS file system sends a wakeup on a driver event on which the application API call is waiting. The application then collects a summary of read and write activity on the files.

The message payload type is `acfsmetric1` and the files to be monitored are movie files that have been tagged with the `FILECONTENT` tag. The message delivery type is `post`, which means that Oracle ACFS posts messages containing the metrics to the plug-in application for the specified interval of 120 seconds.

When the command in Example 16-131 completes, the Oracle ACFS file system mounted on the `/moviemods` mount point is enabled for plug-in communication and begins collecting Oracle ACFS storage visibility metrics for files tagged with `FILECONTENT`. On each interval, Oracle ACFS posts one or more messages to the application plug-in containing the storage visibility information.

**See Also:**

- [About Using Oracle ACFS Command-Line Tools](steps-manage-acfs.md) for information about running Oracle ACFS `acfsutil` commands

- [Oracle ACFS Plugins](understand-acfs-admin.md) for an overview of Oracle ACFS plug-ins

- [Oracle ACFS Pre-defined Metric Types](acfs-advanced-topics.md) for information about the pre-defined metric types

- [Oracle ACFS Plug-in Generic Application Programming Interface](acfs-advanced-topics.md) for information about the Oracle ACFS plug-in application programming interface

- [Oracle ACFS Tagging Generic Application Programming Interface](acfs-advanced-topics.md) for information about the Oracle ACFS tagging application programming interface

### acfsutil plugin info

#### Purpose

Displays information about the Oracle ACFS plug-in infrastructure for an Oracle ACFS file system.

#### Syntax and Description

    acfsutil plugin info -h
    acfsutil plugin info mount_point

`acfsutil` `plugin` `info` `-h` displays help text and exits.

Table 16-135 contains the options available with the `acfsutil` `plugin` `info` command.

Table 16-135 Options for the acfsutil plugin info command

| Option        | Description                                               |
|:--------------|:----------------------------------------------------------|
| `mount_point` | Specifies the directory where the file system is mounted. |

`acfsutil` `plugin` `info` displays information about the state of the Oracle ACFS plug-in mechanism.

Administrator privileges are required to use this command or you must be a member of the Oracle ASM administrator group.

#### Examples

Example 16-132 shows the use of the `acfsutil` `plugin` `info` command.

Example 16-132 Displaying information about the Oracle ACFS driver

    # /sbin/acfsutil plugin info /humanresource

    Plug-in status: ENABLED
    Metric type: acfsmetric1
    Enabled tags: HRDATA
    Delivery method: Poll
    Post interval (seconds):

    # /sbin/acfsutil plugin info /moviemods

    Plug-in status: ENABLED
    Metric type: acfsmetric1
    Enabled tags: FILECONTENT
    Delivery method: Post
    Post interval (seconds): 120

**See Also:**

- [About Using Oracle ACFS Command-Line Tools](steps-manage-acfs.md) for information about running Oracle ACFS `acfsutil` commands

- [Oracle ACFS Plugins](understand-acfs-admin.md) for an overview of Oracle ACFS plug-ins

- [Oracle ACFS Plug-in Generic Application Programming Interface](acfs-advanced-topics.md) for information about the Oracle ACFS plug-in application programming interface

### acfsutil registry

#### Purpose

Adds, deletes, or displays entries in the Oracle ACFS mount registry.

#### Syntax and Description

    acfsutil registry -h
    acfsutil registry
    acfsutil registry -a [-f] [-o moptions] [-n { nodes|all } ]
               [-u user] [-t description] device mount_point
    acfsutil registry -c  {device | mount_point} [-o moptions]
               [-n { nodes|all } ] [-u user] [-t description]
    acfsutil registry -d {device | mount_point}
    acfsutil registry -l [device | mount_point]
    acfsutil registry -m deviceacfsutil registry -r

`acfsutil` `registry` `-h` displays help text and exits.

If no options are specified, the command displays all the Oracle ACFS file systems that are configured for automatic start.

Table 16-136 contains the options available with the `acfsutil` `registry` command.

Table 16-136 Options for the acfsutil registry command

| Option                             | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   |
|:-----------------------------------|:------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `-a`                               | Add the device, mount point, and associated `moptions` to the Oracle ACFS mount registry. The Oracle ADVM volume device specified must exist on the local node to add the information to the mount registry.<br>The arguments represent all the information needed to mount the file system. At Oracle ACFS startup time these file systems are automatically mounted.<br>Duplicate device entries are not allowed. Duplicate mount points are allowed but must be include the `-n` option for disjoint node-specific mounts. |
| `-c`                               | Changes an existing registry entry for the specified device or mount point.                                                                                                                                                                                                                                                                                                                                                                                                                                                   |
| `-d`                               | Deletes the specified device or mount point from the Oracle ACFS mount registry. If a mount point is specified and it is not unique in the Oracle ACFS mount registry, the command fails and you must run the command again specifying the device.                                                                                                                                                                                                                                                                            |
| `-f`                               | This option is used in combination with `-a` when the specified device might exist in the registry and the administrator wants to replace the registration.                                                                                                                                                                                                                                                                                                                                                                   |
| `-l` \[`device` \| `mount_point`\] | Without specifying a device or mount point, the `-l` option lists all the file systems currently in the registry on a single line, with fields separated by a colon (`:`). With a device specified, lists information about the device in the Oracle ACFS registry. With a mount point specified, lists information about the mount point in the Oracle ACFS registry.                                                                                                                                                        |
| `-m` `device`                      | Lists the registered mount point, if one exists, associated with the specified device. The mount point is only returned if the Oracle ACFS file system has been registered or has been previously mounted.                                                                                                                                                                                                                                                                                                                    |
| `-n` { `nodes` \| `all`}           | This option, used in combination with `-a` and `-c`, specifies an optional comma-delimited list of nodes, or the `all` keyword. This specifies which nodes should attempt to mount this device on the specified mount point. Host names should be specified. The `all` keyword is functionally equivalent to not specifying a list of nodes and indicates that the device should be mounted on all nodes. Mounting on all nodes is the default behavior.                                                                      |
| `-o` `moptions`                    | Specifies the mount options for use when mounting the file system. Valid for Linux, Solaris, and AIX. Used in combination with `-a` and `-c`. For specific `-o` `moptions`, refer to the `mount` command for each operating system. All the options for each operating system are available except the `all` option.                                                                                                                                                                                                          |
| `-r`                               | Displays all registered file systems, not just file systems with `auto_start=always`.                                                                                                                                                                                                                                                                                                                                                                                                                                         |
| `-t` `description`                 | Adds a description of the mount. Used in combination with `-a` and `-c`. For example: `-t` `"HR Exports share"`. This description can be seen later when looking at configured resources.                                                                                                                                                                                                                                                                                                                                     |
| `-u` `user`                        | Specifies a user that is allowed to mount or umount (start and stop) the file system. This option, used in combination with `-a` and `-c`, is useful for creating a registered file system that can be started or stopped by someone other than root.                                                                                                                                                                                                                                                                         |
| `mount_point`                      | Specifies the directory where the file system is mounted.                                                                                                                                                                                                                                                                                                                                                                                                                                                                     |
| `device`                           | Specifies an Oracle ACFS device file that has been formatted.                                                                                                                                                                                                                                                                                                                                                                                                                                                                 |

`acfsutil` `registry` adds, deletes, or displays a file system from the Oracle ACFS persistent mount registry. The mount registry is a global registry that is used at Oracle ACFS startup on each node to mount all file systems specified in it. `root` or `asmadmin` privileges are required to modify the registry. For information about operating system group privileges, see "[About Privileges for Oracle ASM](authenticate-access-asm-instance.md)".

Any user is allowed to display the contents of the registry. To mount all the file systems in the Oracle ACFS mount registry, use the platform specific mount command with the `all` option. This is done automatically at Oracle ACFS startup on each node.

**Note:**

Oracle ACFS registration (`acfsutil` `registry`) is not supported in an Oracle Restart (standalone) configuration, which is a single-instance (non-clustered) environment.

See "[About the Oracle ACFS Mount Registry](understand-acfs-concepts.md)".

#### Examples

The following examples show the use of `acfsutil` `registry`. The first example shows how to add the volume device file and file system mount point to the registry. The second example shows how to list the registered mount point associated with the specified volume device file. The third example shows how to delete the specified volume device file from the registry.

Example 16-133 Using the acfsutil registry command

    $ /sbin/acfsutil registry -a /dev/asm/volume1-123 /acfsmounts/acfs1

    $ /sbin/acfsutil registry -m /dev/asm/volume1-123

    $ /sbin/acfsutil registry -d /dev/asm/volume1-123

### acfsutil rmfs

#### Purpose

Removes an Oracle ACFS file system.

#### Syntax and Description

    acfsutil rmfs -h
    acfsutil rmfs device
    acfsutil rmfs device -b

`acfsutil` `rmfs` `-h` displays help text and exits.

Table 16-137 contains the options available with the `acfsutil` `rmfs` command.

Table 16-137 Options for the acfsutil rmfs command

| Option   | Description                                                   |
|:---------|:--------------------------------------------------------------|
| `device` | Specifies an Oracle ACFS device file that has been formatted. |
| `-b`     | Specifies batch mode. No user interaction is required.        |

You can use `acfsutil` `rmfs` to remove an Oracle ACFS that is dismounted. When the command is run, the superblock of the file system is disabled. `root` or `asmadmin` privileges are required to run this command. For information about operating system group privileges, see "[About Privileges for Oracle ASM](authenticate-access-asm-instance.md)".

After `acfsutil` `rmfs` runs successfully, the `MOUNTPATH` and `USAGE` columns in the `V$ASM_VOLUME` view are cleared for the device. The removed Oracle ACFS can be restored using `fsck` or `acfschkdsk`. The device can be reformatted with a new Oracle ACFS using the `mkfs` or `acfsformat` commands.

#### Examples

The following example shows the use of `acfsutil` `rmfs` to remove the specified volume device file and associated file system.

Example 16-134 Using the acfsutil rmfs command

    $ /sbin/acfsutil rmfs /dev/asm/volume1-123

### acfsutil scrub

#### Purpose

Checks for and reports any inconsistencies in the metadata or file data.

#### Syntax and Description

    acfsutil scrub [-h] [-n] [-m] [-q] [-e number] [-b ext1[,...]] [-z] [-a] [-p level]
                   [-t level] {file | directory}

`acfsutil` `-h` `scrub` displays help text and exits.

The following table contains the options available with the `acfsutil` `scrub` command.

Table 16-138 Options for the acfsutil scrub command

| Option                | Description                                                                    |
|:----------------------|:-------------------------------------------------------------------------------|
| `-n`                  | Specifies not to scrub the directory recursively.                              |
| `-m`                  | Specifies to scrub the metadata only.                                          |
| `-q`                  | Specifies quiet mode. Only report inconsistencies to STDOUT.                   |
| `-e ``number`         | Specifies the number of inconsistencies encountered before program terminates. |
| `-b ``ext1,ext2, ...` | Specifies not to scrub files with the specified extensions.                    |
| `-z`                  | Specifies not to scrub the Oracle ACFS snapshot directory.                     |
| `-a`                  | Specifies to scrub extensions skipped by default (`.dbf`, `.arc`).             |
| `-p ``level`          | Specifies I/O load level , from `0` (lowest) to `6` (highest).                 |
| `-t ``level`          | Specifies trace level verbosity, from `0` (terse) to `6` (verbose).            |
| `file`                | Specifies the full path name of a file.                                        |
| `directory`           | Specifies the full path name of a directory.                                   |

On Linux and AIX systems, the `acfsutil` `scrub` command checks the mirror consistency of Oracle ACFS directory metadata and file user data and metadata.

For paths with metadata inconsistencies, the scrubber displays the inconsistent path.

For file paths with user data inconsistencies, the scrubber provides the following information:

- Pathname

- Byte offset of inconsistency

- Byte length of inconsistency

- ADVM volume byte offset of inconsistency

You must have `root` privileges to run `acfsutil` `scrub` .

#### Examples

The following example illustrates the use of the `acfsutil` `scrub` command. The first command scrubs only the metadata of the specified file. The second command scrubs the specified directory and all nested files, except for snapshots, `txt` files, and `pdf` files. The third command scrubs the specified directory and all nested files with the power level set to `5` and trace level set to `3`.

Example 16-135 Using the Oracle ACFS acfsutil scrub command

    $ /sbin/acfsutil scrub -m /acfsmnt/textdoc1.txt

    $ /sbin/acfsutil scrub -b txt,pdf -z /acfsmnt/dir1

    $ /sbin/acfsutil scrub -p 5 -t 3 /acfsmnt/dir1

### acfsutil size

#### Purpose

Resizes an Oracle ACFS file system.

#### Syntax and Description

    acfsutil size -h
    acfsutil size {[[+|-]n[K|M|G|T|P]] [-d volume_device] [-q]} |
                  {[-a n[K|M|G|T] ] [-x n[K|M|G|T] ]} mount_point

`acfsutil` `size` `-h` displays help text and exits.

The following table contains the options available with the `acfsutil` `size` command.

Table 16-139 Options for the acfsutil size command

| Option                                     | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      |
|:-------------------------------------------|:-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| \[`+`\|`-`\]`n`<br>`K`\|`M`\|`G`\|`T`\|`P` | Specifies the new size for the Oracle ACFS file system where `n` is a valid positive whole number greater than zero. The number can be preceded by a `+` or - to indicate the amount to add or decrease. If no operand exists, the new size is the absolute size.<br>Specifies that the integer supplied for size is in the units of `K` (Kilobytes), `M` (Megabytes), `G` (Gigabytes), `T` (Terabytes), or `P` (Petabytes). If the unit indicator is specified, then it must be appended to the integer. If omitted, the default unit is bytes.                                                                                                                                                                                                 |
| `—q `                                      | Provides an estimate of how much data may need to be moved to complete the command.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              |
| `-a``n`                                    | Specifies the increment by which an automatic resize increases the file system when the amount of free space falls below the amount specified by the increment. A nonnegative numeric value must be provided, and may optionally be followed by `K` (Kilobytes), `M` (Megabytes), `G` (Gigabytes), or `T` (Terabytes) to specify a value in kilobytes, megabytes, gigabytes, or terabytes. If the unit is omitted, the default is bytes. A value of 0 disables automatic resize. The minimum allowed increment is 1G.                                                                                                                                                                                                                            |
| `-x``n`                                    | Specifies the maximum size to which a file system automatically resizes. A nonnegative numeric value must be provided, and may optionally be followed by`K` (Kilobytes), `M` (Megabytes), `G` (Gigabytes), or `T` (Terabytes) to specify a value in kilobytes, megabytes, gigabytes, or terabytes. If the unit is omitted, the default is bytes. If this value is less than the current size of the file system then no error is returned, but automatic resize does not take place until the file system is shrunk (by manual action of the system administrator) below this value. A value of 0 indicates that no maximum size is configured, so the file system may continue to automatic resize until the underlying volume is out of space. |
| `—d ``volume_device`                       | Resizes only the specified device.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                               |
| `mount_point`                              | Specifies the directory where the file system is mounted                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         |

At least one of the `+` or `—`, `—a`, or `—x` options must be specified.

The size value is rounded up based on the block size of the file system and the allocation unit of the Oracle ADVM volume device file. To determine the Oracle ADVM volume device resize increment, examine the `RESIZE_UNIT_MB` field in the `V$ASM_VOLUME` view, `Resize` `Unit` in the output of `asmcmd` `volinfo`, or `ADVM` `resize` `increment` in the output of `acfsutil` `info` `fs`.

Before issuing an `acfsutil` `size` command to grow or shrink a file system, you can issue `acfsutil` `size` `-q` to report how much data may be needed to be moved to complete the command. This estimation can be helpful in predicting how long the command may take to complete. Using the `-q` option does not cause any resizing of the file system.

There is no limit to the number of times a file system can be expanded for a disk group with the ADVM compatibility attribute set to `11.2.0.4` or higher.

For a disk group with the ADVM compatibility attribute set to less than `11.2.0.4`, there is a limit of 5 extents for the file system's internal storage bitmap. This causes any attempts to increase the file system to fail after it has been increased four or more times. However, if after increasing the file system four times or more times the file system size is decreased, then you may be able to increase the file system size again if the size of the increase is less than the size of the decrease. When the limit on a file system expansion has been reached, running `fsck` or `acfschkdsk` with the `-a` option may consolidate the internal storage bitmap, allowing future file system expansion.

`root` or users who are members of the `asmadmin` group can run this command. For information about operating system group privileges, see [About Privileges for Oracle ASM](authenticate-access-asm-instance.md).

#### Manual Resize Option

The `+` or `-` option grows or shrinks the mounted Oracle ACFS and its underlying Oracle ADVM storage to match the new size specified. This operation also resizes the underlying Oracle ADVM volume file to match the new length that is specified. However, the disk group must have enough free storage to accommodate any requested increase to the file system size.

You can use `acfsutil` `size` to extend or shrink an entire file system or only a specified device.

Reducing a file system size returns unused storage space located at the end of the file system to the disk group.

Prior to Oracle ASM release 18c, the shrinking operation would only succeed if the operation did not require existing files in the file system to be moved. For Oracle ASM release 18c, the shrink process moves files as necessary when shrinking the file system. This process of moving files can be time consuming. In addition, a subsequent command to grow the file system may also need to move data, which may be time-consuming.

**Note:**

- An attempt to extend or shrink the file system may partially succeed, resulting in the file system having a larger or smaller size than before the `acfsutil` `size` command was issued. However, because of errors or environmental changes, the new size may not be the requested size. If a grow or shrink operation fails on a node for any reason, an error message is written to the `USM` event log and the `OKS` log.

- A shrink of the accelerator volume does not cause the migration of metadata from the accelerator volume to the primary volume. The process fails if there is too much data on the accelerator.

- A shrink command moves files out of the area of the volume that is to be removed and into a different part of the volume. This moving of files could change the fragmentation of these files. It could result in their becoming more fragmented than they were prior to the file system shrink operation. It could also result in their becoming less fragmented.

#### Automatic Resize Option

The automatic resize option (`-a` option) specifies an increment by which an Oracle ACFS file system grows automatically if the amount of available free space in the file system falls below the amount specified by the increment. You can also specify the maximum size (`-x` option) allowed when using the automatic resize option. The output of the `acfsutil info fs` command displays the automatic resize increment and maximum amounts. If only the `-x` option is provided without the `-a` option (and no automatic resize increment has previously been specified) then a warning is issued if the increment is still zero. If the increment had previously been set by an earlier invocation of the command, then the command succeeds. Automatic resize requires ADVM compatibility attribute set to `12.2` or higher.

If an automatic resize fails on a node for any reason, automatic resizing on the node is temporarily disabled. An error message is written to the `USM` event log and the `OKS` log. Automatic resizing may still take place on another node; however, if the failure is due to the underlying volume being out of free space then all nodes quickly disable automatic resize. The file system does continue to periodically try to automatic resize, at increasingly longer intervals. After a resize succeeds, such as when more space is added to the underlying Oracle ASM disk group, then automatic resize becomes re-enabled on the node. Note that other nodes may remain in the error state even after one node successfully auto-resizes the file system. Automatic resize can be manually re-enabled by either re-mounting the file system or running the acfsutil size command again with the `-a` or `-x` option to update automatic resize settings. When a file system has grown to the maximum size specified with `acfsutil size -x`, automatic resize remains enabled but does not grow the file system any further until the maximum is increased.

The `-d` argument is not compatible with the `-a` and `-x` automatic resize arguments. Unless a volume device is specified with `-d`, it is assumed that the caller is specifying an amount of storage that applies to the primary volume, which represents the size of the file system. When growing a file system with an accelerator volume, the `acfsutil` `size` command determines if the accelerator size needs to be increased. If the accelerator must be larger and cannot be increased, the command fails and the primary volume remains at the same size. When shrinking a file system, only the primary volume is shrunk. If a volume device is specified with the `-d` option, then the size specified applies to either the primary volume or the accelerator volume, whichever is specified, and only that volume device is changed. The command warns the user if the resulting accelerator volume size is not large enough to accommodate the primary volume size.

When using an accelerator volume and automatic resize, the increment specified with the automatic resize `-a` argument applies to the primary volume; however, both the primary volume and the accelerator volume are monitored. Automatic resize grows the primary volume by the specified increment, or greater if needed. Automatic resize monitors and grows the accelerator volume as needed as well by smaller increments. When automatic resize needs to grow the primary volume, it first attempts to grow the accelerator if insufficient space remains on the accelerator to accommodate the new growth, and if that fails the primary volume remains at the same size.

In addition to being triggered because the free space falls below the configured automatic resize increment, an automatic resize also takes place under other conditions, such as:

- If the free space in the file system falls below 10% of the current file system size or 5 GB, whichever is smaller.

- If a copy-on-write cannot find enough contiguous space in the file system to allocate new storage for the write.

- If the defragger cannot find enough contiguous space to allocate in order to defragment 8 MB worth of extents in a file.

These conditions protect against a large file system having enough total free space so that an automatic resize appears unnecessary, but the space is so fragmented that applications cannot use it.

When a non-sparse file is resized so that it grows by more than the configured auto-resize interval, the file system automatic resizes by a multiple of the automatic resize increment so that the resize request can be satisfied.

#### Examples

The following example shows the use of `acfsutil` `size`. This example increases the primary device file of `/acfsmounts/acfs1` file system by 500 MB.

Example 16-136 Using the acfsutil size command

    $ /sbin/acfsutil size +500M /acfsmounts/acfs1

### acfsutil thaw

#### Purpose

Resumes activity after an `acfsutil` `freeze` command has been issued on a file system.

#### Syntax and Description

    acfsutil thaw -h
    acfsutil thaw mount_point

`acfsutil` `thaw` `-h` displays help text and exits.

The following table contains the options available with the `acfsutil` `thaw` command.

Table 16-140 Options for the acfsutil thaw command

| Option        | Description                                               |
|:--------------|:----------------------------------------------------------|
| `mount_point` | Specifies the directory where the file system is mounted. |

You can use the `acfsutil` `thaw` command to resume activity after the `acfsutil` `freeze` command has been issued to temporarily halt modification activity on a file system. For information about `acfsutil` `freeze`, refer to acfsutil freeze.

#### Examples

The following example shows the use of the `acfsutil` `thaw` command.

Example 16-137 Using the acfsutil thaw command

    $ /sbin/acfsutil thaw /acfsmounts/acfs1

### acfsutil version

#### Purpose

Displays Oracle ACFS version information.

#### Syntax and Description

    acfsutil version -h
    acfsutil version -v

`acfsutil` `version` `-h` displays help text and exits.

The following table contains the options available with the `acfsutil` `version` command.

Table 16-141 Options for the acfsutil version command

| Option | Description                                             |
|:-------|:--------------------------------------------------------|
| `—v`   | Displays verbose version information about Oracle ACFS. |

Administrator privileges are required to use this command or you must be a member of the Oracle ASM administrator group.

Example 16-138 Using acfsutil version

In the first example, basic information is displayed about the Oracle ACFS release version. In the second example, detailed version information is displayed about the installed Oracle ACFS components.

    $ /sbin/acfsutil version
    acfsutil version: 19.0.0.0.0

    $ /sbin/acfsutil version -v
    Kernel:
        Build version: 19.0.0.0.0
        Build full version: 19.2.0.0.0
        Build hash:    9728583571
        Bug numbers:   26947218
    Commands:
        Build version: 19.0.0.0.0
        Build full version: 19.2.0.0.0
        Build hash:    9728583571
        Bug numbers:   26947218

### advmutil canonical

#### Purpose

`advmutil` `canonical` displays the canonical name of the specified Oracle ADVM device name.

#### Syntax and Description

    advmutil -h
    advmutil canonical volume_device

`advmutil` `-h` displays help text and exits.

Table 16-142 contains the options available with the `advmutil` `canonical` command.

Table 16-142 Options for the advmutil canonical command

| Option          | Description                                                  |
|:----------------|:-------------------------------------------------------------|
| `volume_device` | Specifies a string identifying an Oracle ADVM volume device. |

There are several different formats that can identify an Oracle ADVM volume device, but a normalized, unambiguous (canonical) name should be used when the volume device name is used with other commands such as `SRVCTL`.

For example, on the Windows operating system you can use the following prefixes with a volume device name: `\\.\`, `\??\`, `\\?\`

The `advmutil` `canonical` command would return the canonical name that another utility would recognize without having to strip off extra characters. The command would most likely be used in a script.

#### Examples

The following examples show the use of `advmutil` `canonical` on a Windows operating system. For each example, the command returns the canonical name of the volume device.

Example 16-139 Using advmutil canonical

    [C:\]advmutil canonical asm-volume1-274
    asm-volume1-274

    [C:\]advmutil canonical \\.\asm-volume1-274
    asm-volume1-274

    [C:\]advmutil canonical \\?\asm-volume1-274
    asm-volume1-274

    [C:\]advmutil canonical \??\asm-volume1-274
    asm-volume1-274

### advmutil volinfo

#### Purpose

`advmutil` `volinfo` displays information about Oracle ADVM volume devices.

#### Syntax and Description

    advmutil -h
    advmutil volinfo [-l][-L] [volume_device]

`advmutil` `-h` displays help text and exits.

Table 16-143 contains the options available with the `advmutil` `volinfo` command.

Table 16-143 Options for the advmutil volinfo command

| Option          | Description                                                                                       |
|:----------------|:--------------------------------------------------------------------------------------------------|
| `volume_device` | Specifies an optional volume device name.                                                         |
| `-l`            | Separates the Oracle ADVM volume device information by field descriptions and colons on one line. |
| `-L`            | Separates the Oracle ADVM volume device information by spaces on one line.                        |

`advmutil` `volinfo` displays information about Oracle ADVM volume devices in a list format by default. The `-l` option on Linux (`/l` on Windows) formats the display into a colon-separated string with field descriptions. The `-L` option on Linux (`/L` on Windows) formats the display into a space-separated string in a format suitable for scripting.

#### Examples

The first example displays information about an Oracle ADVM volume device, using the `advmutil` `volinfo` command with the volume device name. The second example displays information about the volume device using the `-l` option. The third example displays information about the volume device using the `-L` option.

Example 16-140 Using advmutil volinfo

    $ /sbin/advmutil volinfo /dev/asm/volume1-123
    Device : /dev/asm/volume1-228
    Interface Version: 1
    Size (MB): 256
    Resize Increment (MB): 32
    Redundancy: mirror
    Stripe Columns: 4
    Stripe Width (KB): 128
    Disk Group: DATA
    Volume: VOLUME1
    Compatible.advm : 11.2.0.0.0

    $ /sbin/advmutil volinfo -l /dev/asm/volume1-228
    Device : /dev/asm/volume1-228 : Interface Version : 1 : Size (MB) : 256 :
    Resize Increment (MB) : 32 : Redundancy : mirror : Stripe Columns : 4 :
    Stripe Width (KB) : 128 : Disk Group : DATA : Volume : VOLUME1 :
    Compatible.advm : 11.2.0.0.0

    $ /sbin/advmutil volinfo -L /dev/asm/volume1-228
    /dev/asm/volume1-228  1  256 32  mirror  4  128  DATA  VOLUME1  11.2.0.0.0
