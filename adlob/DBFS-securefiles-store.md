## 21  DBFS SecureFiles Store

There are certain procedures for setting up and using a DBFS SecureFiles Store.

Topics:

- Setting Up a SecureFiles Store

- Using a DBFS SecureFiles Store File System

- About DBFS SecureFiles Store Package\_ DBMS_DBFS_SFS

<!-- -->

- Setting Up a SecureFiles Store
  There are several aspects to setting up a SecureFiles Store.
- Using a DBFS SecureFiles Store File System
  The DBFS Content API provides methods to populate a SecureFiles Store file system and otherwise manage it.
- About DBFS SecureFiles Store Package, DBMS_DBFS_SFS
  The DBFS SecureFiles Store package (`DBMS_DBFS_SFS`) is a store provider for `DBMS_DBFS_CONTENT` that supports SecureFiles LOB storage for DBFS content.
- Database File System (DBFS)— POSIX File Locking

**Parent topic:** [Database File System (DBFS)](database-file-system.md)

### 21.1 Setting Up a SecureFiles Store

There are several aspects to setting up a SecureFiles Store.

This section shows how to set up a SecureFiles Store.

Topics:

- About Managing Permissions

- Creating or Setting Permissions

- Creating a SecureFiles File System Store

- Accessing Tables that Hold SecureFiles System Store Data

- Initializing SecureFiles Store File Systems

- Comparison of SecureFiles LOBs to BasicFiles LOBs

<!-- -->

- About Managing Permissions
  You must use a regular database user for all operational access to the Content API and stores.
- Creating or Setting Permissions
  You must grant the `DBFS_ROLE` role to any user that needs to use the DBFS content API.
- Creating a SecureFiles File System Store
  You must create the SecureFiles file system stores that the DBFS Content API accesses.
- Accessing Tables that Hold SecureFiles System Store Data
  You should never directly access tables that hold data for a SecureFiles Store file systems, even through the `DBMS_DBFS_SFS` package methods.
- Initializing SecureFiles Store File Systems
  You can truncate and re-initialize tables associated with an SecureFiles Store.
- Comparison of SecureFiles LOBs to BasicFiles LOBs
  SecureFiles LOBs are only available in Oracle Database 11g Release 1 and higher. They are not available in earlier releases.

**Parent topic:** DBFS SecureFiles Store

#### 21.1.1 About Managing Permissions

You must use a regular database user for all operational access to the Content API and stores.

Do not use `SYS` or `SYSTEM` users or `SYSDBA` or `SYSOPER` system privileges. For better security and separation of duty, only allow specific trusted users the ability to manage DBFS Content API operations.

You must grant each user the `DBFS_ROLE` role. Otherwise, the user is not authorized to use the DBFS Content API. A user with suitable administrative privileges (or `SYSDBA`) can grant the role to additional users as needed.

Because of the way roles, access control, and definer and invoker rights interact in the database, it may be necessary to explicitly grant various permissions (typically execute permissions) on DBFS Content API types (SQL types with the `DBMS_DBFS_CONTENT_` `xxx` prefix) and packages (typically only `DBMS_DBFS_CONTENT` and `DBMS_DBFS_SFS`) to users who might otherwise have the `DBFS_ROLE` role.

These explicit, direct grants are normal and to be expected, and can be provided as needed and on demand.

**Parent topic:** Setting Up a SecureFiles Store

#### 21.1.2 Creating or Setting Permissions

You must grant the `DBFS_ROLE` role to any user that needs to use the DBFS content API.

1.  Create or determine DBFS Content API target users.
    This example uses this user and password: `sfs_demo/``password`

    At minimum, this database user must have the `CREATE SESSION`, `CREATE RESOURCE`, and `CREATE VIEW` privileges.
2.  Grant the `DBFS_ROLE` role to the user.
        CONNECT / as sysdba
        GRANT dbfs_role TO sfs_demo;

This sets up the DBFS Content API for any database user who has the `DBFS_ROLE` role.

**Parent topic:** Setting Up a SecureFiles Store

#### 21.1.3 Creating a SecureFiles File System Store

You must create the SecureFiles file system stores that the DBFS Content API accesses.

The `CREATEFILESYSTEM` procedure auto-commits before and after its execution (like a DDL). The method `CREATESTORE` is a wrapper around `CREATEFILESYSTEM`.

**See Also:**

[Oracle Database PL/SQL Packages and Types Reference](../arpls/index.md) for `DBMS_DBFS_SFS` syntax details

##### To create a SecureFiles File System Store:

1.  Create the necessary stores to be accessed using the DBFS Content API:
        DECLARE
          BEGIN
            DBMS_DBFS_SFS.CREATEFILESYSTEM(
              store_name => 'FS1',
              tbl_name => 'T1',
              tbl_tbs => null,
              use_bf => false
            );
            COMMIT;
          END;
        /

    where:

    - `store_name` is any arbitrary, user-unique name.

    - `tbl_name` is a valid table name, created in the current schema.

    - `tbl_tbs` is a valid tablespace name used for the store table and its dependent segments, such as indexes, LOBs, or nested tables. The default is `NULL` and specifies a tablespace of the current schema.

    - `use_bf` specifies that BasicFiles LOBs should be used, if `true`, or not used, if `false`.
2.  Register this store with the DBFS Content API as a new store managed by the SecureFiles Store provider.
        CONNECT sfs_demo
        Enter password:password
        DECLARE
          BEGIN
            DBMS_DBFS_CONTENT.REGISTERSTORE(
              store_name    => 'FS1',
              provider_name => 'anything',
              provider_package => 'dbms_dbfs_sfs'
            );
            COMMIT;
          END;
        /

    where:

    - `store_name` is SecureFiles Store `FS1`, which uses table `SFS_DEMO.T1`.

    - `provider_name` is ignored.

    - `provider_package` is `DBMS_DBFS_SFS`, for SecureFiles Store reference provider.

    This operation associates the SecureFiles Store `FS1` with the `DBMS_DBFS_SFS` provider.
3.  Mount the store at suitable a mount-point.
        CONNECT sfs_demo
        Enter password: password
        DECLARE
          BEGIN
            DBMS_DBFS_CONTENT.MOUNTSTORE(
              store_name    => 'FS1',
              store_mount   => 'mnt1'
            );
            COMMIT;
          END;
        /

    where:

    - `store_name` is SecureFiles Store `FS1`, which uses table `SFS_DEMO.T1`.

    - `store_mount` is the [mount point](glossary.md).
4.  \[Optional\] To see the results of the preceding steps, you can use the following statements.
    - To verify SecureFiles Store tables and file systems:

          SELECT * FROM TABLE(DBMS_DBFS_SFS.LISTTABLES);
          SELECT * FROM TABLE(DBMS_DBFS_SFS.LISTFILESYSTEMS);

    - To verify ContentAPI Stores and mounts:

          SELECT * FROM TABLE(DBMS_DBFS_CONTENT.LISTSTORES);
          SELECT * FROM TABLE(DBMS_DBFS_CONTENT.LISTMOUNTS);


    - To verify SecureFiles Store features:

          var fs1f number;
          exec :fs1f := dbms_dbfs_content.getFeaturesByName('FS1');
          select * from table(dbms_dbfs_content.decodeFeatures(:fs1f));

    - To verify resource and property views:

          SELECT * FROM DBFS_CONTENT;
          SELECT * FROM DBFS_CONTENT_PROPERTIES;

**Parent topic:** Setting Up a SecureFiles Store

#### 21.1.4 Accessing Tables that Hold SecureFiles System Store Data

You should never directly access tables that hold data for a SecureFiles Store file systems, even through the `DBMS_DBFS_SFS` package methods.

This is the correct way to access the file systems.

- For procedural operations: Use the DBFS Content API (`DBMS_DBFS_CONTENT` methods).

- For SQL operations: Use the resource and property views (`DBFS_CONTENT` and `DBFS_CONTENT_PROPERTIES`).

**Parent topic:** Setting Up a SecureFiles Store

#### 21.1.5 Initializing SecureFiles Store File Systems

You can truncate and re-initialize tables associated with an SecureFiles Store.

- Use the procedure `INITFS()`.

  The procedure executes like a DDL, auto-committing before and after its execution.

The following example uses file system `FS1` and table `SFS_DEMO`.`T1`, which is associated with the SecureFiles Store `store_name`.

    CONNECT sfs_demo;
    Enter password: password
    EXEC DBMS_DBFS_SFS.INITFS(store_name => 'FS1');

**Parent topic:** Setting Up a SecureFiles Store

#### 21.1.6 Comparison of SecureFiles LOBs to BasicFiles LOBs

SecureFiles LOBs are only available in Oracle Database 11g Release 1 and higher. They are not available in earlier releases.

You must use BasicFiles LOB storage for LOB storage in tablespaces that are not managed with Automatic Segment Space Management (ASSM).

Compatibility must be at least 11.1.0.0 to use SecureFiles LOBs.

Additionally, you need to specify the following in `DBMS_DBFS_SFS.CREATEFILESYSTEM:`

- To use SecureFiles LOBs (the default), specify `use_bf => false.`

- To use BasicFiles LOBs, specify `use_bf => true`.

**Parent topic:** Setting Up a SecureFiles Store

### 21.2 Using a DBFS SecureFiles Store File System

The DBFS Content API provides methods to populate a SecureFiles Store file system and otherwise manage it.

Topics:

- DBFS Content API Working Example

- Dropping SecureFiles Store File Systems

<!-- -->

- DBFS Content API Working Example
  You can create new file and directory elements to populate a SecureFiles Store file system.
- Dropping SecureFiles Store File Systems
  You can use the `unmountStore` method to drop SecureFiles Store file systems.

**Parent topic:** DBFS SecureFiles Store

#### 21.2.1 DBFS Content API Working Example

You can create new file and directory elements to populate a SecureFiles Store file system.

If you have executed the steps in "Setting Up a SecureFiles Store", set the DBFS Content API permissions, created at least one SecureFiles Store reference file system, and mounted it under the mount point `/mnt1`, then you can create a new file and directory elements as demonstrated in Example 21-1.

Example 21-1 Working with DBFS Content API

    CONNECT tjones
    Enter password: password

    DECLARE
       ret integer;
       b   blob;
       str varchar2(1000)  := '' || chr(10) ||

    '#include <stdio.h>' || chr(10) ||
    '' || chr(10) ||
    'int main(int argc, char** argv)' || chr(10) ||
    '{' || chr(10) ||
    '    (void) printf("hello world\n");' || chr(10) ||
    '    RETURN 0;' || chr(10) ||
    '}' || chr(10) ||
    '';

        BEGIN
            ret := dbms_fuse.fs_mkdir('/mnt1/FS1');
            ret := dbms_fuse.fs_creat('/mnt1/FS1/hello.c', content => b);
            dbms_lob.writeappend(b, length(str), utl_raw.cast_to_raw(str));
            COMMIT;
        END;
        /
        SHOW ERRORS;

        -- verify newly created directory and file
        SELECT pathname, pathtype, length(filedata),
            utl_raw.cast_to_varchar2(filedata)
            FROM dbfs_content
                WHERE pathname LIKE '/mnt1/FS1%'
                ORDER BY pathname;

The file system can be populated and accessed from PL/SQL with `DBMS_DBFS_CONTENT`. The file system can be accessed read-only from SQL using the `dbfs_content` and `dbfs_content_properties` views.

The file system can also be populated and accessed using regular file system APIs and UNIX utilities when mounted using FUSE, or by the standalone `dbfs_client` tool (in environments where `FUSE` is either unavailable or not set up).

**Parent topic:** Using a DBFS SecureFiles Store File System

#### 21.2.2 Dropping SecureFiles Store File Systems

You can use the `unmountStore` method to drop SecureFiles Store file systems.

This method removes all stores referring to the file system from the metadata tables, and drops the underlying file system table. The procedure executes like a DDL, auto-committing before and after its execution.

1.  Unmount the store.
        CONNECT sfs_demo
        Enter password: password
        DECLARE
          BEGIN
            DBMS_DBFS_CONTENT.UNMOUNTSTORE(
              store_name    => 'FS1',
              store_mount   => 'mntl';
            );
            COMMIT;
        END;
        /

    where:

    - `store_name` is SecureFiles Store `FS1`, which uses table `SFS_DEMO.T1`.

    - `store_mount` is the mount point.
2.  Unregister the stores.
        CONNECT sfs_demo
        Enter password: password
        EXEC DBMS_DBFS_CONTENT.UNREGISTERSTORE(store_name => 'FS1');
        COMMIT;

    where `store_name` is SecureFiles Store `FS1`, which uses table `SFS_DEMO.T1`.
3.  Drop the file system.
        CONNECT sfs_demo/******;
        EXEC DBMS_DBFS_SFS.DROPFILESYSTEM(store_name => 'FS1');
        COMMIT;

    where `store_name` is SecureFiles Store `FS1`, which uses table `SFS_DEMO.T1`.

**Parent topic:** Using a DBFS SecureFiles Store File System

### 21.3 About DBFS SecureFiles Store Package, DBMS_DBFS_SFS

The DBFS SecureFiles Store package (`DBMS_DBFS_SFS`) is a store provider for `DBMS_DBFS_CONTENT` that supports SecureFiles LOB storage for DBFS content.

To use the `DBMS_DBFS_SFS` package, you must be granted the `DBFS_ROLE` role.

The SecureFiles Store provider is a default implementation of the DBFS Content API (and is a standard example of a store provider that conforms to the Provider SPI) that enables applications that already use LOBs as columns in their schema, to access the `BLOB` columns. This enables existing applications to easily add PL/SQL provider implementations and provide access through the DBFS Content API without changing their schemas or their business logic.

Applications can also read and write content that is stored in other (third party) stores through the standard DBFS Content API interface.

In a SecureFiles Store, the underlying user data is stored in SecureFiles LOBs and metadata such as pathnames, IDs, and properties are stored as columns in relational tables.

**See Also:**

- See [Oracle Database PL/SQL Packages and Types Reference](../arpls/DBMS_DBFS_SFS.md) for more information about the `DBMS_DBFS_SFS` package.

- [Creating Your Own DBFS Store](creating-your-own-DBFS-store.md) and [Oracle Database PL/SQL Packages and Types Reference](../arpls/DBMS_DBFS_CONTENT_SPI.md) for more information about the Provider SPI defined in `DBMS_DBFS_CONTENT_SPI`.

- [SecureFiles LOB Storage](using-oracle-LOBs-storage.md)for advanced features of SecureFiles LOBs.

**Parent topic:** DBFS SecureFiles Store

### 21.4 Database File System (DBFS)— POSIX File Locking

Starting from Oracle Database 12c Release 2(12.2), Oracle supports the Database File system `POSIX` File locking feature. The DBFS provides file locking support for:

- `POSIX` applications using `DBFS_CLIENT` (in mount mode) as a front-end interface to DBFS.

- Applications using `PL/SQL` as an interface to DBFS.

**Note:**

Oracle supports only Full-file locks in DBFS. Full-file lock implies locking the entire file from byte zero offset to the end of file.

Topics:

- About Advisory Locking

- About Mandatory Locking

- File Locking Support

- Compatibility and Migration Factors of Database Filesystem—File Locking

- Examples of Database Filesystem—File Locking

<!-- -->

- About Advisory Locking
  Advisory locking is a file locking mechanism that locks the file for a single process.
- About Mandatory Locking
  Mandatory locking is a file locking mechanism that takes support from participating processes.
- File Locking Support
  Enabling the file locking mechanism helps applications to block files for various file system operations.
- Compatibility and Migration Factors of Database Filesystem—File Locking
- Examples of Database Filesystem—File Locking
- File Locking Behavior
- Scheduling File Locks

**Parent topic:** DBFS SecureFiles Store

#### 21.4.1 About Advisory Locking

Advisory locking is a file locking mechanism that locks the file for a single process.

File locking mechanism cannot independently enforce any form of locking and requires support from the participating processes. For example, if a process `P1` has a `write` lock on file `F1`, the locking API or the operating system does not perform any action to prevent any other process `P2` from issuing a `read` or `write` system call on the file `F1`. This behavior of file locking mechanism is also applicable to other file system operations. The processes that are involved (in file locking mechanism) must follow a lock or unlock protocol provided in a suitable API form by the user-level library. File locking semantics are guaranteed to work provided, the processes incorporate the recommended usage of the locking protocol and respect the results of API calls.

**Parent topic:** Database File System (DBFS)— POSIX File Locking

#### 21.4.2 About Mandatory Locking

Mandatory locking is a file locking mechanism that takes support from participating processes.

Mandatory locking is an enforced locking scheme that does not rely on the participating processes to cooperate and/or follow the locking API. For example, if a process `P1` has taken a `write` lock on file `F1` and if a different process `P2` attempts to issue a `read`/`write` system call (or any other file system operation) on file `F1` , the request is blocked because the concerned file is exclusively locked by process `P1`.

**Parent topic:** Database File System (DBFS)— POSIX File Locking

#### 21.4.3 File Locking Support

Enabling the file locking mechanism helps applications to block files for various file system operations.

The `fcntl()`, `lockf()`, and `flock()` system calls in `UNIX` and `LINUX` provide file locking support. These system calls enable applications to use the file locking facility through `dbfs_client-FUSE` callback interface. File Locks provided by `fcntl()` are widely known as POSIX file locks and the file locks provided by `flock()` are known as BSD file locks. The semantics and behavior of POSIX and BSD file locks differ from each other. The locks placed on the same file through `fcntl()` and `flock()` are orthogonal to each other. The semantics of file locking functionality designed and implemented in DBFS is similar to POSIX file locks. In DBFS, semantics of file locks placed through `flock()` system call will be similar to POSIX file locks (such as `fcntl()`) and not BSD file locks. `lockf()` is a library call that is implemented as a wrapper over `fcntl()` system call on most of the UNIX systems, and hence, it provides POSIX file locking semantics. In DBFS, file locks placed through `fcntl()`, `flock()`, and `lockf()` system-calls provide same kind of behavior and semantics of POSIX file locks.

**Note:**

BSD file locking semantics are not supported.

**Parent topic:** Database File System (DBFS)— POSIX File Locking

#### 21.4.4 Compatibility and Migration Factors of Database Filesystem—File Locking

The Database Filesystem File Locking feature does not impact the compatibility of `DBFS` and `SFS` store provider with `RDBMS`.

`DBFS_CLIENT` is a standalone OCI Client and uses `OCI` calls and `DBMS_FUSE API`.

**Note:**

This feature will be compatible with `Ora``SDK/RSF` .

**Parent topic:** Database File System (DBFS)— POSIX File Locking

#### 21.4.5 Examples of Database Filesystem—File Locking

The following examples illustrate the advisory locking and the locking functions available on `UNIX` based systems. The following example uses two running processes — Process A and Process B.

Example 21-2 No locking

`Process A opens file:`

    file_desc = open(“/path/to/file”, O_RDONLY);
    /* Reads data into bufffers */
    read(fd, buf1, sizeof(buf));
    read(fd, buf2, sizeof(buf));
    close(file_desc);

Subjected to OS scheduling, `process B` can enter any time and issue a `write` system call affecting the integrity of file data.

Example 21-3 Advisory locking used but process B does not follow the protocol

`Process A opens file:`

    file_desc = open(“/path/to/file”, O_RDONLY);
    ret = AcquireLock(file_desc, RD_LOCK);
    if(ret)
    {
        read(fd, buf1, sizeof(buf));
        read(fd, buf2, sizeof(buf));
        ReleaseLock(file_desc);
    }
    close(file_desc);

Subjected to OS scheduling, `process B` can come in any time and still issue a `write` system call ignoring that `process A` already holds a `read` lock.

`Process B opens file:`

    file_desc1 = open(“/path/to/file”, O_WRONLY);
    write(file_desc1, buf, sizeof(buf));
    close(file_desc1);

The above code is executed and leads to inconsistent data in the file.

Example 21-4 Advisory locking used and processes are following the protocol

`Process A opens file:`

    file_desc = open(“/path/to/file”, O_RDONLY);
    ret = AcquireLock(file_desc, RD_LOCK);
    if(ret)
    {
        read(fd, buf1, sizeof(buf));
        read(fd, buf2, sizeof(buf));
        ReleaseLock(file_desc);
    }
    close(file_desc);

`Process B opens file:`

    file_desc1 = open(“/path/to/file”, O_WRONLY);
    ret = AcquireLock(file_desc1, WR_LOCK);
    /* The above call will take care of checking the existence of a lock */
    if(ret)
    {
        write(file_desc1, buf, sizeof(buf));
        ReleaseLock(file_desc1);
    } close(file_desc1);

`Process B` follows the lock API and this API makes sure that the process does not `write` to the file without acquiring a lock.

**Parent topic:** Database File System (DBFS)— POSIX File Locking

#### 21.4.6 File Locking Behavior

The `DBFS` File Locking feature exhibits the following behaviors:

- File locks in `DBFS` are implemented with idempotent functions. If a process issues “N” `read` or `write` lock calls on the same file, only the first call will have an effect, and the subsequent “N-1” calls will be treated as redundant and returns No Operation (NOOP).

- File can be unlocked exactly once. If a process issues “N” `unlock` calls on the same file, only the first call will have an effect, and the subsequent “N-1” calls will be treated as redundant and returns NOOP.

- Lock conversion is supported only from `read` to `write`. If a process `P` holds a `read` lock on file `F` ( and `P` is the only process holding the `read` lock), then a `write` lock request by `P` on file `F` will convert the `read` lock to `exclusive`/`write` lock.

**Parent topic:** Database File System (DBFS)— POSIX File Locking

#### 21.4.7 Scheduling File Locks

DBFS File Locking feature supports lock scheduling. This facility is implemented purely on the DBFS client side. Lock request scheduling is required when client application uses blocking call semantics in their `fcntl()`, `lockf()`, and `flock()` calls.

There are two types of scheduling:

- Greedy Scheduling

- Fair Scheduling

Oracle provides the following command line option to switch the scheduling behavior.

`Mount -o lock_sched_option = ``lock_sched_option Value``;`

Table 21-1 `lock_sched_option` Value Description

| Value | Description                                              |
|:------|:---------------------------------------------------------|
| 1     | Sets the scheduling type to Greedy Scheduling. (Default) |
| 2     | Sets the scheduling type to Fair Scheduling.             |

**Note:**

Lock Request Scheduling works only on per `DBFS` Client mount basis. For example, lock requests are not scheduled across multiple mounts of the same file system.

- Greedy Scheduling
- Fair Scheduling

**Parent topic:** Database File System (DBFS)— POSIX File Locking

##### 21.4.7.1 Greedy Scheduling

In this scheduling technique, the file lock requests does not follow any guaranteed order.

**Note:**

This is the default scheduling option provided by DBFS Client.

 If a file `F` is `read` locked by process `P1`, and if processes `P2` and `P3` submit blocking `write` lock requests on file `F`, the processes `P2` and `P3` will be blocked (using a form of spin lock) and made to wait for its turn to acquire the lock. During the wait, if a process `P4` submits a `read` lock request (blocking call or a non-blocking call) on file `F`, `P4` will be granted the `read` lock even if there are two processes (`P2` and `P3`) waiting to acquire the `write` lock. Once both `P1` and `P4` release their respective `read` locks, one of `P2` and `P3` will succeed in acquiring the lock. But, the order in which processes `P2` and `P3` acquire the lock is not determined. It is possible that process `P2` would have requested first, but the process `P3`’s request might get unblocked and acquire the lock and the process `P2` must wait for `P3` to release the lock.

**Parent topic:** Scheduling File Locks

##### 21.4.7.2 Fair Scheduling

This scheduling technique is implemented using a queuing mechanism on per file basis. For example, if a file `F` is read locked by process `P1`, and processes `P2` and `P3` submit blocking write lock requests on file `F`, these two processes will be blocked (using a form of spin lock) and will wait to acquire the lock. The requests will be queued in the order received by the DBFS client. If a process `P4` submits a read lock request (blocking call or a non-blocking call) on file `F`, this request will be queued even though a read lock can be granted to this process.

DBFS Client ensures that after `P1` releases its read lock, the order in which lock requests are honored is P2-\>P3 -\> P4.

This implies that `P2` will be the first one to get the lock. Once `P2` releases its lock, `P3` will get the lock and so on.

**Parent topic:** Scheduling File Locks
