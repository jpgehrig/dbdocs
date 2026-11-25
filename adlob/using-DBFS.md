## 25  Using DBFS

The DBFS File System implementation includes creating and accessing the file system and managing it.

Topics:

- DBFS Installation

- Creating a DBFS File System

- DBFS File System Access

- DBFS Administration

- Shrinking and Reorganizing DBFS Filesystems

<!-- -->

- DBFS Installation
  DBFS is a part of the Oracle database installation and is installed under `ORACLE_HOME`.
- Creating a DBFS File System
  A DBFS File system can be partitioned or non-partitioned. It may require users to have certain privileges.
- DBFS File System Access
  You access a DBFS file system by means of prerequisites, access interfaces, the DBFS security model, and XML DB server protocols.
- DBFS Administration
- Shrinking and Reorganizing DBFS Filesystems

**Parent topic:** [Database File System (DBFS)](database-file-system.md)

### 25.1 DBFS Installation

DBFS is a part of the Oracle database installation and is installed under `ORACLE_HOME`.

`$ORACLE_HOME/rdbms/admin` contains these DBFS utility scripts:

- Content API (CAPI)

- SecureFiles Store (SFS)

`$ORACLE_HOME/bin` contains:

- `dbfs_client` executable

`$ORACLE_HOME/rdbms/admin` contains:

- SQL (`.plb` extension) scripts for the content store

**Parent topic:** Using DBFS

### 25.2 Creating a DBFS File System

A DBFS File system can be partitioned or non-partitioned. It may require users to have certain privileges.

Topics:

- Privileges Required to Create a DBFS File System

- Advantages of Non-Partitioned Versus Partitioned DBFS File Systems

- Creating a Non-Partitioned File System

- Creating a Partitioned File System

- Dropping a File System

<!-- -->

- Privileges Required to Create a DBFS File System
  Database users must have a minimum set of privileges to create a file system.
- Advantages of Non-Partitioned Versus Partitioned DBFS File Systems
  You can create either non-partitioned or partitioned file systems. Partitioning is the best performing and most scalable way to create a file system in DBFS and is the default.
- Creating a Non-Partitioned File System
  You can create a file system by running `DBFS_CREATE_FILESYSTEM.SQL` while logged in as a user with DBFS administrator privileges.
- Creating a Partitioned File System
  Files in DBFS are hash partitioned. Partitioning creates multiple physical segments in the database, and files are distributed randomly in these partitions.
- Dropping a File System
  You can drop a file system by running `DBFS_DROP_FILESYSTEM.SQL`.

**Parent topic:** Using DBFS

#### 25.2.1 Privileges Required to Create a DBFS File System

Database users must have a minimum set of privileges to create a file system.

Users must have these privileges:

- `GRANT CONNECT`

- `CREATE SESSION`

- `RESOURCE`, `CREATE TABLE`

- `CREATE PROCEDURE`

- `DBFS_ROLE`

**Parent topic:** Creating a DBFS File System

#### 25.2.2 Advantages of Non-Partitioned Versus Partitioned DBFS File Systems

You can create either non-partitioned or partitioned file systems. Partitioning is the best performing and most scalable way to create a file system in DBFS and is the default.

Space cannot be shared between partitions, so it is possible for one partition to run out of space even when other partitions have space. This is usually not an issue if the file system size is big compared to the size of the individual files. However, if file sizes are a big percentage of the file system size, it may result in the `ENOSPC` error even if the file system is not full.

Another implication of partitioning is that a rename operation can require rewriting the file, which can be expensive if the file is big.

**Parent topic:** Creating a DBFS File System

#### 25.2.3 Creating a Non-Partitioned File System

You can create a file system by running `DBFS_CREATE_FILESYSTEM.SQL` while logged in as a user with DBFS administrator privileges.

These steps enable you to create a file system.

1.  Log in to the database instance:
        $ sqlplus dbfs_user/@db_server
2.  Enter the following command:
        @$ORACLE_HOME/rdbms/admin/dbfs_create_filesystem.sql tablespace_name
             file_system_name

For example, to create a file system called `staging_area` in an existing tablespace `dbfs_tbspc`:

    $ sqlplus dbfs_user/db_server
       @$ORACLE_HOME/rdbms/admin/dbfs_create_filesystem.sql
       dbfs_tbspc staging_area

**Parent topic:** Creating a DBFS File System

#### 25.2.4 Creating a Partitioned File System

Files in DBFS are hash partitioned. Partitioning creates multiple physical segments in the database, and files are distributed randomly in these partitions.

You can create a partitioned file system by running `DBFS_CREATE_FILESYSTEM``_ADVANCED`.`SQL` while logged in as a user with DBFS administrator privileges.

While creating a partitioned file system, you can specify any one of the following values as the hash key.

- `partition` and `partition-by-itemname`: uses the item name as the partition key. The item name is the last component in the path name. Use this option to partition files based on the last component in the file path. For example, if `/directory1/subdirectory2/filename.txt` is the entire path, then `filename.txt` is the last component in the path and `filename.txt` is used as the partition key. If you use the `partition` option, then the file system is partitioned using the item name as the partition key.
- `partition-by-guid`: uses the globally unique identifier (GUID) assigned to the file by DBFS as the partition key. DBFS assigns a GUID to each file. Use this option to partition the files based on the internally-generated GUID.
- `partition-by-path`: uses the entire path of the file as the partition key. For example, if the file is `/directory1/subdirectory2/filename.txt`, then the entire `/directory1/subdirectory2/filename.txt` is considered as the partition key.

1.  Log in to the database instance:
        $ sqlplus dbfs_user/@db_server
2.  Enter one of the following commands to create the file system based on your requirement. The tablespace in which the file system is created should be an ASSM tablespace to support Securefile store.
    - Syntax

          @$ORACLE_HOME/rdbms/admin/dbfs_create_filesystem_advanced.sql tablespace_name
                 file_system_name nocompress nodeduplicate noencrypt <partition | partition-by-itemname | partition-by-guid | partition-by-path>

      For example, to create a partitioned file system called `staging_area` in an existing ASSM tablespace `dbfs_tbspc`:

          $ sqlplus dbfs_user/@db_server
                 @$ORACLE_HOME/rdbms/admin/dbfs_create_filesystem_advanced.sql dbfs_tbspc
                 staging_area nocompress nodeduplicate noencrypt partition

**Parent topic:** Creating a DBFS File System

#### 25.2.5 Dropping a File System

You can drop a file system by running `DBFS_DROP_FILESYSTEM.SQL`.

1.  Log in to the database instance:
        $ sqlplus dbfs_user/@db_server
2.  Enter the following command:
        @$ORACLE_HOME/rdbms/admin/dbfs_drop_filesystem.sql file_system_name

**Parent topic:** Creating a DBFS File System

### 25.3 DBFS File System Access

You access a DBFS file system by means of prerequisites, access interfaces, the DBFS security model, and XML DB server protocols.

Topics:

- DBFS Client Prerequisites

- DBFS Client Command-Line Interface Operations

- DBFS Mounting Interface (Linux and Solaris Only)

- File System Security Model

- HTTP\_ WebDAV\_ and FTP Access to DBFS

<!-- -->

- DBFS Client Prerequisites
  The DBFS File System Client, which is named `dbfs_client`, runs on each system that will access DBFS filesystems, using certain prerequisites.
- DBFS Client Command-Line Interface Operations
  The DBFS client command-line interface allows you to directly access files stored in DBFS.
- DBFS Mounting Interface (Linux and Solaris Only)
  You can mount DBFS using the `dbfs_client` in Linux and Solaris only.
- File System Security Model
- HTTP, WebDAV, and FTP Access to DBFS

**Parent topic:** Using DBFS

#### 25.3.1 DBFS Client Prerequisites

The DBFS File System Client, which is named `dbfs_client`, runs on each system that will access DBFS filesystems, using certain prerequisites.

The prerequisites for the DBFS File System Client, `dbfs_client`, are:

- The `dbfs_``client` host must have the Oracle client libraries installed.

- The `dbfs_client` can be used as a direct RDBMS client using the DBFS Command Interface on Linux, Linux.X64, Solaris, Solaris64, AIX, HPUX and Windows platforms.

- The `dbfs_client` can only be used as a mount client on Linux, Linux.X64, and Solaris 11 platforms. This requires the following:

  - `dbfs_client` host must have the `FUSE` Linux package or the Solaris `libfuse` package installed.

  - A group named `fuse` must be created, with the user name that runs the `dbfs_client` as a member.

  **See Also:**

  DBFS Mounting Interface (Linux and Solaris Only) for further details.

**Parent topic:** DBFS File System Access

#### 25.3.2 DBFS Client Command-Line Interface Operations

The DBFS client command-line interface allows you to directly access files stored in DBFS.

Topics:

- About the DBFS Client Command-Line Interface

- Creating Content Store Paths

- Creating a Directory

- Listing a Directory

- Copying Files and Directories

- Removing Files and Directories

<!-- -->

- About the DBFS Client Command-Line Interface
  The DBFS client command-line interface allows you to perform many pre-defined commands, such as copy files in and out of the DBFS filesystem from any host on the network.
- Creating Content Store Paths
  You can create a content store path by providing a path name
- Creating a Directory
  You can use the `mkdir` command to create a new directory.
- Listing a Directory
  You can use the `ls` command to list the contents of a directory.
- Copying Files and Directories
  You can use the `cp` command to copy files or directories from the source location to the destination location.
- Removing Files and Directories
  You can use the command `rm` to delete a file or directory.

**Parent topic:** DBFS File System Access

##### 25.3.2.1 About the DBFS Client Command-Line Interface

The DBFS client command-line interface allows you to perform many pre-defined commands, such as copy files in and out of the DBFS filesystem from any host on the network.

The command-line interface has slightly better performance than the DBFS client mount interface because it does not mount the file system, thus bypassing the user space file system. However, it is not transparent to applications.

The DBFS client mount interface allows DBFS to be mounted through a file system mount point thus providing transparent access to files stored in DBFS with generic file system operations.

To run DBFS commands, specify `--command` to the DBFS client.

**Parent topic:** DBFS Client Command-Line Interface Operations

##### 25.3.2.2 Creating Content Store Paths

You can create a content store path by providing a path name

All DBFS content store paths must be preceded by `dbfs:` .This is an example: `dbfs:/staging_area/file1`. All database path names specified must be absolute paths.

    dbfs_client db_user@db_server --command command [switches] [arguments]

where:

- `command` is the executable command, such as `ls`, `cp`, `mkdir`, or `rm`.

- `switches` are specific for each command.

- `arguments` are file names or directory names, and are specific for each command.

Note that `dbfs_client` returns a nonzero value in case of failure.

**Parent topic:** DBFS Client Command-Line Interface Operations

##### 25.3.2.3 Creating a Directory

You can use the `mkdir` command to create a new directory.

Use this syntax:

    dbfs_client db_user@db_server --command mkdir directory_name

where:

- `directory_name` is the name of the directory created. For example:

      $ dbfs_client ETLUser@DBConnectString --command mkdir dbfs:/staging_area/dir1

**Parent topic:** DBFS Client Command-Line Interface Operations

##### 25.3.2.4 Listing a Directory

You can use the `ls` command to list the contents of a directory.

Use this syntax:

    dbfs_client db_user@db_server --command ls [switches] target

where

- `target` is the listed directory.

- `switches` is any combination of the following:

  - `-``a` shows all files, including '`.`' and '`..`'.

  - `-``l` shows the long listing format: name of each file, the file type, permissions, and size.

  - `-``R` lists subdirectories recursively.

For example:

    $ dbfs_client ETLUser@DBConnectString --command  ls dbfs:/staging_area/dir1

or

    $ dbfs_client ETLUser@DBConnectString --command  ls -l -a -R dbfs:/staging_area/dir1

**Parent topic:** DBFS Client Command-Line Interface Operations

##### 25.3.2.5 Copying Files and Directories

You can use the `cp` command to copy files or directories from the source location to the destination location.

The `cp` command also supports recursive copy of directories.

    dbfs_client db_user@db_server --command cp [switches] source destination

where:

- `source` is the source location.

- `destination` is the destination location.

- `switches` is either `-R` or `-r`, the options to recursively copy all source contents into the destination directory.

The following example copies the contents of the local directory, `01-01-10-dump` recursively into a directory in DBFS:

    $ dbfs_client ETLUser@DBConnectString --command cp -R  01-01-10-dump dbfs:/staging_area/

The following example copies the file `hello.txt` from DBFS to a local file `Hi.txt`:

    $ dbfs_client ETLUser@DBConnectString --command cp dbfs:/staging_area/hello.txt Hi.txt

**Parent topic:** DBFS Client Command-Line Interface Operations

##### 25.3.2.6 Removing Files and Directories

You can use the command `rm` to delete a file or directory.

The command `rm` also supports recursive delete of directories.

    dbfs_client db_user@db_server --command rm [switches] target

where:

- `target` is the listed directory.

- `switches` is either `-R` or `-r`, the options to recursively delete all contents.

For example:

    $ dbfs_client ETLUser@DBConnectString --command rm  dbfs:/staging_area/srcdir/hello.txt

or

    $ dbfs_client ETLUser@DBConnectString --command rm -R  dbfs:/staging_area/dir1

**Parent topic:** DBFS Client Command-Line Interface Operations

#### 25.3.3 DBFS Mounting Interface (Linux and Solaris Only)

You can mount DBFS using the `dbfs_client` in Linux and Solaris only.

The instructions indicate the different requirements for the Linux and Solaris platforms.

Topics:

- Installing FUSE on Solaris 11 SRU7 and Later

- Mounting the DBFS Store

- Solaris-Specific Privileges

- About the Mount Command for Solaris and Linux

- Mounting a File System with a Wallet

- Mounting a File System with Password at Command Prompt

- Mounting a File System with Password Read from a File

- Unmounting a File System

- Mounting DBFS Through fstab Utility for Linux

- Mounting DBFS Through the vfstab Utility for Solaris

- Restrictions on Mounted File Systems

<!-- -->

- Installing FUSE on Solaris 11 SRU7 and Later
  You can use `dbfs_client` as a mount client in Solaris 11 SRU7 and later, if you install `FUSE`
- Mounting the DBFS Store
  You can mount the DBFS store by running the `dbfs_client` program.
- Solaris-Specific Privileges
  On Solaris, the user must have the Solaris privilege `PRIV_SYS_MOUNT` to perform mount and unmount operations on DBFS filesystems.
- About the Mount Command for Solaris and Linux
  The `dbfs_client` mount command for Solaris and Linux uses specific syntax.
- Mounting a File System with a Wallet
  You can mount a file system with a wallet after configuring various environment variables.
- Mounting a File System with Password at Command Prompt
  You can mount a file system using `dbfs_client`.
- Mounting a File System with Password Read from a File
  You can mount a file system with a password read from a file.
- Unmounting a File System
  In Linux, you can run `fusermount` to unmount file systems.
- Mounting DBFS Through fstab Utility for Linux
  In Linux, you can configure `fstab` utility to use `dbfs_client` to mount a DBFS filesystem.
- Mounting DBFS Through the vfstab Utility for Solaris
- Restrictions on Mounted File Systems

**Parent topic:** DBFS File System Access

##### 25.3.3.1 Installing FUSE on Solaris 11 SRU7 and Later

You can use `dbfs_client` as a mount client in Solaris 11 SRU7 and later, if you install `FUSE`

Install `FUSE` to use `dbfs_client` as a mount client in Solaris 11 SRU7 and later.

- Run the following package as `root`.

      pkg install libfuse

**Parent topic:** DBFS Mounting Interface (Linux and Solaris Only)

##### 25.3.3.2 Mounting the DBFS Store

You can mount the DBFS store by running the `dbfs_client` program.

To run the `dbfs_client` program.

1.  Ensure that `LD_LIBRARY_PATH` has the correct path to the Oracle client libraries.
2.  Run the `dbfs_client` program.

The `dbfs_client` program does not return until the file system is unmounted.

**See Also:**

Using Oracle Wallet with DBFS Client for the most secure method of specifying the password

**Parent topic:** DBFS Mounting Interface (Linux and Solaris Only)

##### 25.3.3.3 Solaris-Specific Privileges

On Solaris, the user must have the Solaris privilege `PRIV_SYS_MOUNT` to perform mount and unmount operations on DBFS filesystems.

Give the user the Solaris privilege `PRIV_SYS_MOUNT` .

1.  Edit `/etc/user_attr`.

2.  Add or modify the user entry (assuming the user is Oracle) as follows:

        oracle::::type=normal;project=group.dba;defaultpriv=basic,priv_sys_mount;;auth s=solaris.smf.*

**Parent topic:** DBFS Mounting Interface (Linux and Solaris Only)

##### 25.3.3.4 About the Mount Command for Solaris and Linux

The `dbfs_client` mount command for Solaris and Linux uses specific syntax.

Syntax:

    dbfs_client db_user@db_server [-o option_1 -o option_2 ...] mount_point

where the mandatory parameters are:

- `db_user` is the name of the database user who owns the DBFS content store file system.

- `db_server` is a valid connect string to the Oracle Database server, such as `hrdb_host:1521/hrservice`.

- `mount_point` is the path where the Database File System is mounted. Note that all file systems owned by the database user are visible at the mount point.

The options are:

- `direct_io`: To bypass the OS page cache and provide improved performance for large files. Programs in the file system cannot be executed with this option. Oracle recommends this option when DBFS is used as an ETL staging area.

- `wallet`: To run the DBFS client in the background. The Wallet must be configured to get its credentials.

- `failover`: To fail over the DBFS client to surviving database instances without data loss. Expect some performance cost on writes, especially for small files.

- `allow_root`: To allow the root user to access the filesystem. You must set the `user_allow_other` parameter in the `/etc/fuse.conf` configuration file.

- `allow_other`: To allow other users to access the filesystem. You must set the `user_allow_other` parameter in the `/etc/fuse.conf` configuration file.

- `rw`: To mount the filesystem as read-write. This is the default setting.

- `ro`: To mount the filesystem as read-only. Files cannot be modified.

- `trace_level=``n` sets the trace level. Trace levels are:

  - `1 DEBUG`

  - `2 INFO`

  - `3 WARNING`

  - `4 ERROR`: The default tracing level. It outputs diagnostic information only when an error happens. It is recommended that this tracing level is always enabled.

  - `5 CRITICAL`

- `trace_file=STR`: Specifies the tracing log file, where `STR` can be either a `file_name` or `syslog`.

- `trace_size=``trcfile_size`: Specifies size of the trace file in MB. By default, `dbfs_client` rotates tracing output between two 10MB files. Specifying `0` for `trace_size` sets the maximum size of the trace file to unlimited.

**Parent topic:** DBFS Mounting Interface (Linux and Solaris Only)

##### 25.3.3.5 Mounting a File System with a Wallet

You can mount a file system with a wallet after configuring various environment variables.

You must first configure the `LD_LIBRARY_PATH` and `ORACLE_HOME` environment variables correctly before mounting a file system with a wallet.

1.  Login as admin user.
2.  Mount the DBFS store. (Oracle recommends that you do not perform this step as root user.)
        % dbfs_client @/dbfsdb -o wallet,rw,user,direct_io /mnt/dbfs
3.  \[Optional\] To test if the previous step was successful, as admin user, list the `dbfs` directory.
        $ ls /mnt/tdbfs

**Parent topic:** DBFS Mounting Interface (Linux and Solaris Only)

###### 25.3.3.5.1

#####

**See Also:**

Using Oracle Wallet with DBFS Client

##### 25.3.3.6 Mounting a File System with Password at Command Prompt

You can mount a file system using `dbfs_client`.

You must enter a password on the command prompt to mount a file system using `dbfs_client`.

- Run the following:

      $ dbfs_client ETLUser@DBConnectString /mnt/dbfs
        password: xxxxxxx

**Parent topic:** DBFS Mounting Interface (Linux and Solaris Only)

##### 25.3.3.7 Mounting a File System with Password Read from a File

You can mount a file system with a password read from a file.

The following example mounts a file system and frees the terminal. It reads the password from a file:

- Run the following:

      $ nohup dbfs_client ETLUser@DBConnectString /mnt/dbfs < passwordfile.f &
      $ ls -l /mnt/dbfs
      drwxrwxrwx 10 root root 0 Feb  9 17:28 staging_area

**Parent topic:** DBFS Mounting Interface (Linux and Solaris Only)

##### 25.3.3.8 Unmounting a File System

In Linux, you can run `fusermount` to unmount file systems.

To run `fusermount` in Linux, do the following:

- Run the following:

       $ fusermount -u <mount point>

In Solaris, you can run `umount` to unmount file systems.

- Run the following:

       $ umount -u <mount point>

**Parent topic:** DBFS Mounting Interface (Linux and Solaris Only)

##### 25.3.3.9 Mounting DBFS Through fstab Utility for Linux

In Linux, you can configure `fstab` utility to use `dbfs_client` to mount a DBFS filesystem.

To mount DBFS through `/etc/fstab`, you must use Oracle Wallet for authentication.

1.  Login as `root` user.
2.  Change the user and group of `dbfs_client` to user `root` and group `fuse`.
        # chown root.fuse $ORACLE_HOME/bin/dbfs_client
3.  Set the `setuid` bit on `dbfs_client` and restrict `execute` privileges to the user and group only.
        # chmod u+rwxs,g+rx-w,o-rwx dbfs_client
4.  Create a symbolic link to `dbfs_client` in `/sbin` as "`mount.dbfs`".
        $ ln -s $ORACLE_HOME/bin/dbfs_client /sbin/mount.dbfs
5.  Create a new Linux group called "`fuse`".
6.  Add the Linux user that is running the DBFS Client to the `fuse` group.
7.  Add the following line to `/etc/fstab`:
        /sbin/mount.dbfs#db_user@db_server mount_point fuse rw,user,noauto 0 0

    For example:

        /sbin/mount.dbfs#/@DBConnectString /mnt/dbfs fuse rw,user,noauto 0 0
8.  The Linux user can mount the DBFS file system using the standard Linux `mount` command. For example:
        $ mount /mnt/dbfs

    Note that `FUSE` does not currently support `automount`.

**Parent topic:** DBFS Mounting Interface (Linux and Solaris Only)

##### 25.3.3.10 Mounting DBFS Through the vfstab Utility for Solaris

On Solaris, file systems are commonly configured using the `vfstab` utility.

1.  Create a mount shell script `mount_dbfs.sh` to use to start `dbfs_client`. All the environment variables that are required for Oracle RDBMS must be exported. These environment variables include `TNS_ADMIN`, `ORACLE_HOME`, and `LD_LIBRARY_PATH`. For example:
        #!/bin/ksh
        export TNS_ADMIN=/export/home/oracle/dbfs/tnsadmin
        export ORACLE_HOME=/export/home/oracle/11.2.0/dbhome_1
        export DBFS_USER=dbfs_user
        export DBFS_PASSWD=/tmp/passwd.f
        export DBFS_DB_CONN=dbfs_db
        export O=$ORACLE_HOME
        export LD_LIBRARY_PATH=$O/lib:$O/rdbms/lib:/usr/lib:/lib:$LD_LIBRARY_PATH
        export NOHUP_LOG=/tmp/dbfs.nohup

        (nohup $ORACLE_HOME/bin/dbfs_client $DBFS_USER@$DBFS_DB_CONN < $DBFS_PASSWD
                 2>&1 & ) &
2.  Add an entry for DBFS to `/etc/vfstab`. Specify the `mount_dbfs.sh` script for the `device_to_mount`. Specify `uvfs` for the `FS_type`. Specify no `formount_at_boot`. Specify mount options as needed. For example:
        /usr/local/bin/mount_dbfs.sh - /mnt/dbfs uvfs - no rw,allow_other
3.  User can mount the DBFS file system using the standard Solaris mount command. For example:
        $ mount /mnt/dbfs
4.  User can unmount the DBFS file system using the standard Solaris umount command. For example:
        $ umount /mnt/dbfs

**Parent topic:** DBFS Mounting Interface (Linux and Solaris Only)

##### 25.3.3.11 Restrictions on Mounted File Systems

DBFS supports most file system operations with exceptions. Exceptions are:

- `ioctl`

- range locking (file locking is supported)

- asynchronous I/O through `libaio`

- `O_DIRECT` file opens

- hard links, pipes

- other special file modes

Memory-mapped files are supported except in shared-writable mode. For performance reasons, DBFS does not update the file access time every time file data or the file data attributes are read.

You cannot run programs from a DBFS-mounted file system if the `direct_io` option is specified.

Oracle does not support exporting DBFS file systems using NFS or Samba.

**Parent topic:** DBFS Mounting Interface (Linux and Solaris Only)

#### 25.3.4 File System Security Model

The database manages security in DBFS. It does not use the operating system security model.

- About the File System Security Model

- Enabling Shared Root Access

- About DBFS Access Among Multiple Database Users

- Establishing DBFS Access Sharing Across Multiple Database Users

<!-- -->

- About the File System Security Model
- Enabling Shared Root Access
- About DBFS Access Among Multiple Database Users
- Establishing DBFS Access Sharing Across Multiple Database Users

**Parent topic:** DBFS File System Access

##### 25.3.4.1 About the File System Security Model

DBFS operates under a security model where all file systems created by a user are private to that user, by default.

Oracle recommends maintaining this model. Because operating system users and Oracle Database users are different, it is possible to allow multiple operating system users to mount a single DBFS filesystem. These mounts may potentially have different mount options and permissions. For example, `user1` may mount a DBFS filesystem as `READ ONLY`, and `user2` may mount it as `READ WRITE`. However, Oracle Database views both users as having the same privileges because they would be accessing the filesystem as the same database user.

Access to a database file system requires a database login as a database user with privileges on the tables that underlie the file system.The database administrator grants access to a file system to database users, and different database users may have different `READ` or `UPDATE` privileges to the file system. The database administrator has access to all files stored in the DBFS file system.

On each client computer, access to a DBFS mount point is limited to the operating system user that mounts the file system. This, however, does not limit the number of users who can access the DBFS file system, because many users may separately mount the same DBFS file system.

DBFS only performs database privilege checking. Linux performs operating system file-level permission checking when a DBFS file system is mounted. DBFS does not perform this check either when using the command interface or when using the PL/SQL interface directly.

**Parent topic:** File System Security Model

##### 25.3.4.2 Enabling Shared Root Access

As an operating system user who mounts the file system, you can allow root access to the file system by specifying the `allow_root` option. This option requires that the `/etc/fuse.conf` file contain the `user_allow_other` field, as demonstrated in Example 25-1.

Example 25-1 Enabling Root Access for Other Users

    # Allow users to specify the 'allow_root' mount option.
    user_allow_other

**Parent topic:** File System Security Model

##### 25.3.4.3 About DBFS Access Among Multiple Database Users

Some circumstances may require that multiple database users access the same filesystem. For example, the database user that owns the filesystem may be a privileged user and sharing its user credentials may pose a security risk. To mitigate this, DBFS allows multiple database users to share a subset of the filesystem state.

While DBFS registrations and mounts made through the DBFS content API are private to each user, the underlying filesystem and the tables on which they rely may be shared across users. After this is done, the individual filesystems may be independently mounted and used by different database users, either through SQL/PLSQL, or through `dbfs_client` APIs.

**Parent topic:** File System Security Model

##### 25.3.4.4 Establishing DBFS Access Sharing Across Multiple Database Users

You can share DBFS across multiple database users.

In the following example, user `user1` is able to modify the filesystem, and user `user2` can see these changes. Here, `user1` is the database user that creates a filesystem, and `user2` is the database user that eventually uses `dbfs_client` to mount and access the filesystem. Both `user1` and `user2` must have the `DBFS_ROLE` privilege.

1.  Connect as the user who creates the filesystem.
        sys@tank as sysdba> connect user1
        Connected.
2.  Create the filesystem `user1_FS`, register the store, and mount it as `user1_mt`.
        user1@tank> exec dbms_dbfs_sfs.createFilesystem('user1_FS');
        user1@tank> exec dbms_dbfs_content.registerStore('user1_FS', 'posix', 'DBMS_DBFS_SFS');
        user1@tank> exec dbms_dbfs_content.mountStore('user1_FS', 'user1_mnt');
        user1@tank> commit;
3.  \[Optional\] You may check that the previous step has completed successfully by viewing all mounts.
        user1@tank> select * from table(dbms_dbfs_content.listMounts);

        STORE_NAME           |   STORE_ID|PROVIDER_NAME
        ---------------------|- ---------|------------------------------------------
        PROVIDER_PKG         |PROVIDER_ID|PROVIDER_VERSION     |STORE_FEATURES
        ---------------------|-----------|---------------------|--------------------
        STORE_GUID
        ----------
        STORE_MOUNT
        ----------------------------------------------------------------------------
        CREATED
        ----------------------------------------------------------------------------
        MOUNT_PROPERTIES(PROPNAME, PROPVALUE, TYPECODE)
        ----------------------------------------------------------------------------
        user1_FS             | 1362968596|posix
        "DBMS_DBFS_SFS"      | 3350646887|0.5.0                | 12714135  141867344
        user1_mnt
        01-FEB-10 09.44.25.357858 PM
        DBMS_DBFS_CONTENT_PROPERTIES_T(
          DBMS_DBFS_CONTENT_PROPERTY_T('principal', (null), 9),
          DBMS_DBFS_CONTENT_PROPERTY_T('owner', (null), 9),
          DBMS_DBFS_CONTENT_PROPERTY_T('acl', (null), 9),
          DBMS_DBFS_CONTENT_PROPERTY_T('asof', (null), 187),
          DBMS_DBFS_CONTENT_PROPERTY_T('read_only', '0', 2))
4.  \[Optional\] Connect as the user who will use the `dbfs_client`.
        user1@tank> connect user2
        Connected.
5.  \[Optional\] Note that `user2` cannot see `user1`'s DBFS state, as he has no mounts.
        user2@tank> select * from table(dbms_dbfs_content.listMounts);
6.  While connected as `user1`, export filesystem `user1_FS` for access to any user with `DBFS_ROLE` privilege.
        user1@tank> exec dbms_dbfs_sfs.exportFilesystem('user1_FS');
        user1@tank> commit;
7.  Connect as the user who will use the `dbfs_client`.
        user1@tank> connect user2
        Connected.
8.  As `user2`, view all available tables.
        user2@tank> select * from table(dbms_dbfs_sfs.listTables);

        SCHEMA_NAME                |TABLE_NAME                 |PTABLE_NAME
        ---------------------------|---------------------------|-------------------
        VERSION#
        --------------------------------CREATED
        ---------------------------------------------------------------------------
        FORMATTED
        ---------------------------------------------------------------------------
        PROPERTIES(PROPNAME, PROPVALUE, TYPECODE)
        ---------------------------------------------------------------------------
        user1                        |SFS$_FST_11                |SFS$_FSTP_11
        0.5.0
        01-FEB-10 09.43.53.497856 PM
        01-FEB-10 09.43.53.497856 PM
        (null)
9.  As `user2`, register and mount the store, but do not re-create the `user1_FS` filesystem.
        user2@tank> exec dbms_dbfs_sfs.registerFilesystem(
           'user2_FS', 'user1', 'SFS$_FST_11');
        user2@tank> exec dbms_dbfs_content.registerStore(
           'user2_FS', 'posix', 'DBMS_DBFS_SFS');
        user2@tank> exec dbms_dbfs_content.mountStore(
           'user2_FS', 'user2_mnt');
        user2@tank> commit;
10. \[Optional\] As `user2`, you may check that the previous step has completed successfully by viewing all mounts.
        user2@tank> select * from table(dbms_dbfs_content.listMounts);

        STORE_NAME           |   STORE_ID|PROVIDER_NAME
        ---------------------|- ---------|------------------------------------------
        PROVIDER_PKG         |PROVIDER_ID|PROVIDER_VERSION     |STORE_FEATURES
        ---------------------|-----------|---------------------|--------------------
        STORE_GUID
        ----------
        STORE_MOUNT
        ----------------------------------------------------------------------------
        CREATED
        ----------------------------------------------------------------------------
        MOUNT_PROPERTIES(PROPNAME, PROPVALUE, TYPECODE)
        ----------------------------------------------------------------------------
        user2_FS             | 1362968596|posix
        "DBMS_DBFS_SFS"      | 3350646887|0.5.0                | 12714135  141867344
        user1_mnt
        01-FEB-10 09.46.16.013046 PM
        DBMS_DBFS_CONTENT_PROPERTIES_T(
          DBMS_DBFS_CONTENT_PROPERTY_T('principal', (null), 9),
          DBMS_DBFS_CONTENT_PROPERTY_T('owner', (null), 9),
          DBMS_DBFS_CONTENT_PROPERTY_T('acl', (null), 9),
          DBMS_DBFS_CONTENT_PROPERTY_T('asof', (null), 187),
          DBMS_DBFS_CONTENT_PROPERTY_T('read_only', '0', 2))
11. \[Optional\] List path names for `user2` and `user1`. Note that another mount, `user2_mnt,`for store `user2_FS,` is available for `user2`. However, the underlying filesystem data is the same for `user2` as for `user1`.
        user2@tank> select pathname from dbfs_content;

        PATHNAME
        -------------------------------------------------------------------------------
        /user2_mnt
        /user2_mnt/.sfs/tools
        /user2_mnt/.sfs/snapshots
        /user2_mnt/.sfs/content
        /user2_mnt/.sfs/attributes
        /user2_mnt/.sfs/RECYCLE
        /user2_mnt/.sfs

        user2@tank> connect user1
        Connected.

        user1@tank> select pathname from dbfs_content;

        PATHNAME
        ---------------------
        /user1_mnt
        /user1_mnt/.sfs/tools
        /user1_mnt/.sfs/snapshots
        /user1_mnt/.sfs/content
        /user1_mnt/.sfs/attributes
        /user1_mnt/.sfs/RECYCLE
        /user1_mnt/.sfs
12. In filesystem `user1_FS`, `user1` creates file `xxx`.
        user1@tank> var ret number;
        user1@tank> var data blob;
        user1@tank> exec :ret := dbms_fuse.fs_create('/user1_mnt/xxx', content => :data);
        user1@tank> select :ret from dual;
              :RET
        ----------
                 0
13. \[Optional\] Write to file `xxx`, created in the previous step.
        user1@tank> var buf varchar2(100);
        user1@tank> exec :buf := 'hello world';
        user1@tank> exec dbms_lob.writeappend(:data, length(:buf), utl_raw.cast_to_raw(:buf));
        user1@tank> commit;

14. \[Optional\] Show that file `xxx` exists, and contains the appended data.
        user1@tank> select pathname, utl_raw.cast_to_varchar2(filedata)
          from dbfs_content where filedata is not null;

        PATHNAME
        -------------------------------------------------------------------------------
        UTL_RAW.CAST_TO_VARCHAR2(FILEDATA)
        -------------------------------------------------------------------------------
        /user1_mnt/xxx
        hello world
15. User `user2` sees the same file in their own DBFS-specific path name and mount prefix.
        user1@tank> connect user2
        Connected.

        user2@tank> select pathname, utl_raw.cast_to_varchar2(filedata) from
          dbfs_content where filedata is not null;

        PATHNAME
        -------------------------------------------------------------------------------
        UTL_RAW.CAST_TO_VARCHAR2(FILEDATA)
        -------------------------------------------------------------------------------
        /user2_mnt/xxx
        hello world

After the export and register pairing completes, both users behave as equals with regard to their usage of the underlying tables. The `exportFilesystem()` procedure manages the necessary grants for access to the same data, which is shared between schemas. After `user1` calls `exportFilesystem()`, filesystem access may be granted to any user with `DBFS_ROLE`. Note that a different role can be specified.

Subsequently, `user2` may create a new DBFS filesystem that shares the same underlying storage as the `user1_FS` filesystem, by invoking `dbms_dbfs_sfs.registerFilesystem()`, `dbms_dbfs_sfs.registerStore()`, and `dmbs_dbfs_sfs.mountStore()` procedure calls.

When multiple database users share a filesystem, they must ensure that all database users unregister their interest in the filesystem before the owner (here, `user1`) drops the filesystem.

Oracle does not recommend that you run the DBFS as `root`.

**Parent topic:** File System Security Model

#### 25.3.5 HTTP, WebDAV, and FTP Access to DBFS

Components that enable HTTP, WebDAV, and FTP access to DBFS over the Internet use various XML DB server protocols.

Topics:

- Internet Access to DBFS Through XDB

- Web Distributed Authoring and Versioning (WebDAV) Access

- FTP Access to DBFS

- HTTP Access to DBFS

<!-- -->

- Internet Access to DBFS Through XDB
- Web Distributed Authoring and Versioning (WebDAV) Access
- FTP Access to DBFS
- HTTP Access to DBFS

**Parent topic:** DBFS File System Access

##### 25.3.5.1 Internet Access to DBFS Through XDB

To provide database users who have DBFS authentication with a hierarchical file system-like view of registered and mounted DBFS stores, stores are displayed under the path `/dbfs`.

The `/dbfs` folder is a virtual folder because the resources in its subtree are stored in DBFS stores, not the XDB repository. XDB issues a `dbms_dbfs_content.list()` command for the root path name "`/`" (with invoker rights) and receives a list of store access points as subfolders in the `/dbfs` folder. The list is comparable to `store_mount` parameters passed to `dbms_dbfs_content.mountStore().` FTP and WebDAV users can navigate to these stores, while HTTP and HTTPS users access URLs from browsers.

Note that features implemented by the XDB repository, such as repository events, resource configurations, and ACLs, are not available for the `/dbfs` folder.

[DBFS Content API](DBFS-content-API.md) for guidelines on DBFS store creation, registration, deregistration, mount, unmount and deletion

**Parent topic:** HTTP, WebDAV, and FTP Access to DBFS

##### 25.3.5.2 Web Distributed Authoring and Versioning (WebDAV) Access

WebDAV is an IETF standard protocol that provides users with a file-system-like interface to a repository over the Internet.

WebDAV server folders are typically accessed through Web Folders on Microsoft Windows (2000/NT/XP/Vista/7, and so on). You can access a resource using its fully qualified name, for example, `/dbfs/sfs1/dir1/file1.txt`, where `sfs1` is the name of a DBFS store.

You need to set up WebDAV on Windows to access the DBFS filesystem.

**See Also:**

[Oracle XML DB Developer's Guide](../adxdb/repository-access-using-protocols.md)

The user authentication required to access the DBFS virtual folder is the same as for the XDB repository.

When a WebDAV client connects to a WebDAV server for the first time, the user is typically prompted for a username and password, which the client uses for all subsequent requests. From a protocol point-of-view, every request contains authentication information, which XDB uses to authenticate the user as a valid database user. If the user does not exist, the client does not get access to the DBFS store or the XDB repository. Upon successful authentication, the database user becomes the current user in the session.

XDB supports both basic authentication and digest authentication. For security reasons, it is highly recommended that HTTPS transport be used if basic authentication is enabled.

**Parent topic:** HTTP, WebDAV, and FTP Access to DBFS

##### 25.3.5.3 FTP Access to DBFS

FTP access to DBFS uses the standard FTP clients found on most Unix-based distributions. FTP is a file transfer mechanism built on client-server architecture with separate control and data connections.

FTP users are authenticated as database users. The protocol, as outlined in RFC 959, uses clear text user name and password for authentication. Therefore, FTP is not a secure protocol.

The following commands are supported for DBFS:

- `USER`: Authentication username

- `PASS`: Authentication password

- `CWD`: Change working directory

- `CDUP`: Change to Parent directory

- `QUIT`: Disconnect

- `PORT`: Specifies an address and port to which the server should connect

- `PASV`: Enter passive mode

- `TYPE`: Sets the transfer mode, such as, ASCII or Binary

- `RETR`: Transfer a copy of the file

- `STOR`: Accept the data and store the data as a file at the server site

- `RNFR`: Rename From

- `RNTO`: Rename To

- `DELE`: Delete file

- `RMD`: Remove directory

- `MKD`: Make a directory

- `PWD`: Print working directory

- `LIST`: Listing of a file or directory. Default is current directory.

- `NLST`: Returns file names in a directory

- `HELP`: Usage document

- `SYST`: Return system type

- `FEAT`: Gets the feature list implemented by the server

- `NOOP`: No operation (used for keep-alives)

- `EPRT`: Extended address (IPv6) and port to which the server should connect

- `EPSV`: Enter extended passive mode (IPv6)

**Parent topic:** HTTP, WebDAV, and FTP Access to DBFS

##### 25.3.5.4 HTTP Access to DBFS

Users have read-only access through HTTP/HTTPS protocols. Users point their browsers to a DBFS store using the XDB HTTP server with a URL such as `https://hostname:``port``/dbfs/sfs1` where `sfs1` is a DBFS store name.

**Parent topic:** HTTP, WebDAV, and FTP Access to DBFS

### 25.4 DBFS Administration

DBFS administration includes tools that perform diagnostics, manage failover, perform backup and so on.

Topics:

- Using Oracle Wallet with DBFS Client

- DBFS Diagnostics

- Preventing Data Loss During Failover Events

- Bypassing Client-Side Write Caching

- Backing up DBFS

- Small File Performance of DBFS

- Enabling Advanced SecureFiles LOB Features for DBFS

<!-- -->

- Using Oracle Wallet with DBFS Client
- DBFS Diagnostics
- Preventing Data Loss During Failover Events
  The `dbfs_client` program can failover to one of the other existing database instances if one of the database instances in an Oracle RAC cluster fails.
- Bypassing Client-Side Write Caching
- Backing up DBFS
- Small File Performance of DBFS
- Enabling Advanced SecureFiles LOB Features for DBFS

**Parent topic:** Using DBFS

#### 25.4.1 Using Oracle Wallet with DBFS Client

An Oracle Wallet allows the DBFS client to mount a DBFS store without requiring the user to enter a password.

**See Also:**

[Oracle Database Enterprise User Security Administrator's Guide](../dbimi/using-oracle-wallet-manager.md) for more information about creation and management of wallets

The "`/@`" syntax means to use the wallet, as shown in Step 7.

1.  Create a directory for the wallet. For example:
        mkdir $ORACLE_HOME/oracle/wallet
2.  Create an auto-login wallet.
        mkstore -wrl $ORACLE_HOME/oracle/wallet -create
3.  Add the wallet location in the client's `sqlnet.ora` file:
        WALLET_LOCATION = (SOURCE = (METHOD = FILE) (METHOD_DATA = (DIRECTORY =
         $ORACLE_HOME/oracle/wallet) ) )
4.  Add the following parameter in the client's `sqlnet.ora` file:
        SQLNET.WALLET_OVERRIDE = TRUE
5.  Create credentials:
        mkstore -wrl wallet_location -createCredential db_connect_string username password

    For example:

        mkstore -wrl $ORACLE_HOME/oracle/wallet -createCredential DBConnectString scott password
6.  Add the connection alias to your `tnsnames.ora` file.
7.  Use `dbfs_client` with Oracle Wallet.
    For example:

        $ dbfs_client -o wallet /@DBConnectString /mnt/dbfs

**Parent topic:** DBFS Administration

#### 25.4.2 DBFS Diagnostics

The `dbfs_client` program supports multiple levels of tracing to help diagnose problems. It can either output traces to a file or to `/var/log/messages` using the `syslog` daemon on Linux.

When you trace to a file, the `dbfs_client` program keeps two trace files on disk. `dbfs_client`, rotates the trace files automatically, and limits disk usage to 20 MB.

By default, tracing is turned off except for critical messages which are always logged to `/var/log/messages`.

If `dbfs_client` cannot connect to the Oracle Database, enable tracing using the `trace_level` and `trace_file` options. Tracing prints additional messages to log file for easier debugging.

DBFS uses Oracle Database for storing files. Sometimes Oracle server issues are propagated to `dbfs_client` as errors. If there is a `dbfs_client` error, please view the Oracle server logs to see if that is the root cause.

**Parent topic:** DBFS Administration

#### 25.4.3 Preventing Data Loss During Failover Events

The `dbfs_client` program can failover to one of the other existing database instances if one of the database instances in an Oracle RAC cluster fails.

For `dbfs_client` failover to work correctly, you must modify the Oracle database service and specify failover parameters. Run the `DBMS_SERVICE.MODIFY_SERVICE` procedure to modify the service as shown Example 25-2

Example 25-2 Enabling DBFS Client Failover Events

    exec DBMS_SERVICE.MODIFY_SERVICE(service_name => 'service_name',
                  aq_ha_notifications => true,
                  failover_method => 'BASIC',
                  failover_type => 'SELECT',
                  failover_retries => 180,
                  failover_delay => 1);

Once you have completed the prerequisite, you can prevent data loss during a failover of the DBFS connection after a failure of the back-end Oracle database instance. In this case, cached writes may be lost if the client loses the connection. However, back-end failover to other Oracle RAC instances or standby databases does not cause lost writes.

- Specify the `-o failover` mount option:

      $ dbfs_client database_user@database_server -o failover /mnt/dbfs

**Parent topic:** DBFS Administration

#### 25.4.4 Bypassing Client-Side Write Caching

The sharing and caching semantics for `dbfs_client` are similar to NFS in using the close-to-open cache consistency behavior. This allows multiple copies of `dbfs_client` to access the same shared file system. The default mode caches writes on the client and flushes them after a timeout or after the user closes the file. Also, writes to a file only appear to clients that open the file after the writer closed the file.

You can bypass client-side write caching.

- Specify `O_SYNC` when the file is opened.

  To force writes in the cache to disk call `fsync`.

**Parent topic:** DBFS Administration

#### 25.4.5 Backing up DBFS

You have two alternatives for backing up DBFS. You can back up the tables that underlie the file system at the database level or use a file system backup utility, such as Oracle Secure Backup, through a mount point.

Topics:

- DBFS Backup at the Database Level

- DBFS Backup Through a File System Utility

<!-- -->

- DBFS Backup at the Database Level
- DBFS Backup Through a File System Utility

**Parent topic:** DBFS Administration

##### 25.4.5.1 DBFS Backup at the Database Level

An advantage of backing up the tables at the database level is that the files in the file system are always consistent with the relational data in the database. A full restore and recover of the database also fully restores and recovers the file system with no data loss. During a point-in-time recovery of the database, the files are recovered to the specified time. As usual with database backup, modifications that occur during the backup do not affect the consistency of a restore. The entire restored file system is always consistent with respect to a specified time stamp.

**Parent topic:** Backing up DBFS

##### 25.4.5.2 DBFS Backup Through a File System Utility

The advantage of backing up the file system using a file system backup utility is that individual files can be restored from backup more easily. Any changes made to the restored files after the last backup are lost.

Specify the `allow_root` mount option if backups are scheduled using the Oracle Secure Backup Administrative Server.

**Parent topic:** Backing up DBFS

#### 25.4.6 Small File Performance of DBFS

Like any shared file system, the performance of DBFS for small files lags the performance of a local file system.

Each file data or metadata operation in DBFS must go through the `FUSE` user mode file system and then be forwarded across the network to the database. Therefore, each operation that is not cached on the client takes a few milliseconds to run in DBFS.

For operations that involve an input/output (IO) to disk, the time delay overhead is masked by the wait for the disk IO. Naturally, larger IOs have a lower percentage overhead than smaller IOs. The network overhead is more noticeable for operations that do not issue a disk IO.

When you compare the operations on a few small files with a local file system, the overhead is not noticeable, but operations that affect thousands of small files incur a much more noticeable overhead. For example, listing a single directory or looking at a single file produce near instantaneous response, while searching across a directory tree with many thousands of files results in a larger relative overhead.

**Parent topic:** DBFS Administration

#### 25.4.7 Enabling Advanced SecureFiles LOB Features for DBFS

DBFS offers advanced features available with SecureFiles LOBs: compression, deduplication, encryption, and partitioning.

For example, DBFS can be configured as a compressed file system with partitioning. At the time of creating a DBFS file system, you must specify the set of enabled features for the file system.

**See Also:**

[Using Oracle LOB Storage](using-oracle-LOBs-storage.md) and Creating a Partitioned File System for more information about the features of SecureFiles LOBs.

Example 25-3 Enabling Advanced Secure Files LOB Features for DBFS

    $ sqlplus @dbfs_create_filesystem_advanced tablespace_name file_system­name
      [compress-high | compress-medium | compress-low | nocompress]
      [deduplicate | nodeduplicate]
      [encrypt | noencrypt]
      [partition | non-partition]

**Parent topic:** DBFS Administration

### 25.5 Shrinking and Reorganizing DBFS Filesystems

A DBFS Filesystem uses Online Filesystem Reorganization to shrink itself, enabling the release of allocated space back to the containing tablespace.

Topics:

- About Changing DBFS Filesystems

- Advantages of Online Filesystem Reorganization

- Determining Availability of Online Filesystem Reorganization

- Invoking Online Filesystem Reorganization

<!-- -->

- About Changing DBFS Filesystems
- Advantages of Online Filesystem Reorganization
  DBFS Online Filesystem Reorganization is a powerful data movement facility with these certain advantages.
- Determining Availability of Online Filesystem Reorganization
- Invoking Online Filesystem Reorganization
  You can perform an Online Filesystem Reorganization by creating a temporary DBFS filesystem.

**Parent topic:** Using DBFS

#### 25.5.1 About Changing DBFS Filesystems

DBFS filesystems, like other database segments, grow dynamically with the addition or enlargement of files and directories. Growth occurs with the allocation of space from the tablespace that holds the DBFS filesystem to the various segments that make up the filesystem.

However, even if files and directories in the DBFS filesystem are deleted, the allocated space is not released back to the containing tablespace, but continues to exist and be available for other DBFS entities. A process called Online Filesystem Reorganization solves this problem by shrinking the DBFS Filesystem.

The DBFS Online Filesystem Reorganization utility internally uses the Oracle Database online redefinition facility, with the original filesystem and a temporary placeholder corresponding to the base and interim objects in the online redefinition model.

**See Also:**

[Oracle Database Administrator's Guide](../admin/managing-tables.md) for further information about online redefinition

**Parent topic:** Shrinking and Reorganizing DBFS Filesystems

#### 25.5.2  Advantages of Online Filesystem Reorganization

DBFS Online Filesystem Reorganization is a powerful data movement facility with these certain advantages.

These are:

- It is online: When reorganization is taking place, the filesystem remains fully available for read and write operations for all applications.

- It can reorganize the structure: The underlying physical structure and organization of the DBFS filesystem can be changed in many ways, such as:

  - A non-partitioned filesystem can be converted to a partitioned filesystem and vice-versa.

  - Special SecureFiles LOB properties can be selectively enabled or disabled in any combination, including the compression, encryption, and deduplication properties.

  - The data in the filesystem can be moved across tablespaces or within the same tablespace.

- It can reorganize multiple filesystems concurrently: Multiple different filesystems can be reorganized at the same time, if no temporary filesystems have the same name and the tablespaces have enough free space, typically, twice the space requirement for each filesystem being reorganized.

**Parent topic:** Shrinking and Reorganizing DBFS Filesystems

#### 25.5.3 Determining Availability of Online Filesystem Reorganization

DBFS for Oracle Database 12c and later supports online filesystem reorganization. Some earlier versions also support the facility. To determine if your version does, query for a specific function in the DBFS PL/SQL packages, as shown below:

- Query for a specific function in the DBFS PL/SQL packages.

<!-- -->

    $ sqlplus / as sysdba
    SELECT * FROM dba_procedures
    WHERE   owner = 'SYS'
        and object_name = 'DBMS_DBFS_SFS'
        and procedure_name = 'REORGANIZEFS';

If this query returns a single row similar to the one in this output, the DBFS installation supports Online Filesystem Reorganization. If the query does not return any rows, then the DBFS installation should either be upgraded or requires a patch for bug-10051996.


    OWNER
    ----------------------------------------------------------------------------------
    OBJECT_NAME
    ----------------------------------------------------------------------------------
    PROCEDURE_NAME
    ----------------------------------------------------------------------------------
    OBJECT_ID|SUBPROGRAM_ID|OVERLOAD                                |OBJECT_TYPE  |AGG|PIP
    ----------|-------------|-----------------------------------|-------------|---|---
    IMPLTYPEOWNER
    ----------------------------------------------------------------------------------
    IMPLTYPENAME
    ----------------------------------------------------------------------------------
    PAR|INT|DET|AUTHID
    ---|---|---|------------
    SYS
    DBMS_DBFS_SFS
    REORGANIZEFS
         11424|           52|(null)                                  |PACKAGE      |NO |NO
    (null)
    (null)
    NO |NO |NO |CURRENT_USER

**Parent topic:** Shrinking and Reorganizing DBFS Filesystems

#### 25.5.4 Invoking Online Filesystem Reorganization

You can perform an Online Filesystem Reorganization by creating a temporary DBFS filesystem.

**Note:**

Ensure that you don't create the temporary DBFS filesystem in the SYS schema. DBFS Online Filesystem Reorganization will not work if you create the temporary DBFS filesystem in the SYS schema.

1.  Create a temporary DBFS filesystem with the desired new organization and structure: including the desired target tablespace (which may be the same tablespace as the filesystem being reorganized), desired target SecureFiles LOB storage properties (compression, encryption, or deduplication), and so on.
2.  Invoke the PL/SQL procedure to reorganize the DBFS filesystem using the newly-created temporary filesystem for data movement.
3.  Once the reorganization procedure completes, drop the temporary filesystem.

The example below reorganizes DBFS filesystem `FS1` in tablespace `TS1` into a new tablespace `TS2`, using a temporary filesystem named `TMP_FS`, where all filesystems belong to database user `dbfs_user`:

    $ cd $ORACLE_HOME/rdbms/admin
    $ sqlplus dbfs_user/***

    @dbfs_create_filesystem TS2 TMP_FS
    EXEC DBMS_DBFS_SFS.REORGANIZEFS('FS1', 'TMP_FS');
    @dbfs_drop_filesystem TMP_FS
    QUIT;

where:

- `TMP_FS` can have any valid name. It is intended as a temporary placeholder and can be dropped (as shown in the example above) or retained as a fully materialized point-in-time snapshot of the original filesystem.

- `FS1` is the original filesystem and is unaffected by the attempted reorganization. It remains usable for all DBFS operations, including SQL, PL/SQL, and `dbfs_client` mounts and commandline, during the reorganization. At the end of the reorganization, FS1 has the new structure and organization used to create `TMP_FS` and vice versa (`TMP_FS` will have the structure and organization originally used for `FS1`). If the reorganization fails for any reason, DBFS attempts to clean up the internal state of `FS1`.

- `TS2` needs enough space to accommodate all active (non-deleted) files and directories in `FS1`.

- `TS1` needs at least twice the amount of space being used by `FS1` if the filesystem is moved within the same tablespace as part of a shrink.

**Parent topic:** Shrinking and Reorganizing DBFS Filesystems
