Every time SQL\*Plus starts an Oracle Database instance, it uses a set of parameters which specify the characteristics of the instance's operation. These parameters are kept in a file, typically named `sid`.`DBS`.`INIT`.`ORA`.This topic lists unsupported parameters, and lists other parameters that you may need to change to customize the Oracle Database for the system.

This topic contains the following sections:

- Example Parameter File

- Unsupported Parameters

- Additional Notes on Initialization Parameters

**See Also:**

[Oracle Database Reference](../refrn/basic-initialization-parameters.md) for general descriptions of the parameters

### C.1 Example Parameter File

The `$ORACINST.DEMO.DBS.INIT.ORA` parameter file is created during Oracle Database installation. You can copy and edit this as a text file.

### C.2 Unsupported Parameters

The following initialization file parameters, described in the generic documentation are not supported in Oracle Database 19c for Fujitsu BS2000:

- `MAX_DUMP_FILE_SIZE`

- `OS_ROLES`

- `AUDIT_SYSLOG_LEVEL`

- `MEMORY_MAX_TARGET`

- `MEMORY_TARGET`

Specifying these parameters in the initialization file results in an Oracle Database error during startup. The workaround is to remove such lines from the file.

### C.3 Additional Notes on Initialization Parameters

This section contains additional information about the following initialization parameters:

- BACKGROUND_DUMP_DEST

- USER_DUMP_DEST

- AUDIT_FILE_DEST

- DB_BLOCK_SIZE

- DB_FILE_MULTIBLOCK_READ_COUNT

- DB_FILES

- LOCK_SGA

- SGA_MAX_SIZE

- LOG_ARCHIVE_DEST

#### C.3.1 BACKGROUND_DUMP_DEST

This parameter specifies the path name (directory or prefix), where debugging trace files for the background processes, such as, `LGWR`, `DBWn`, and so on are written during Oracle operations. Furthermore, it specifies the path name for the alert file. The default value for this parameter is the current BS2000 user ID of the Oracle background processes. You can specify a prefix for the trace and alert files in the following format:

    BACKGROUND_DUMP_DEST=BDD

You can also specify a POSIX directory for this parameter.

**Note:**

The `BACKGROUND_DUMP_DEST` parameter is deprecated in Oracle Database 12c Release 1.

This parameter is ignored by the new diagnosability infrastructure introduced in Oracle Database 11g, which places trace and core files in a location controlled by the `DIAGNOSTIC_DEST` initialization parameter.

#### C.3.2 USER_DUMP_DEST

This parameter specifies the path name (directory or prefix), where the server writes the debugging trace files on behalf of a user process. The default value for this parameter is the current BS2000 user ID of the Oracle Database processes.

You can specify a prefix for the trace files as follows:

    USER_DUMP_DEST=UDD

You can also specify a POSIX directory for this parameter.

**Note:**

The `USER_DUMP_DEST` parameter is deprecated in Oracle Database 12c .

This parameter is ignored by the new diagnosability infrastructure introduced in Oracle Database 11g, which places trace and core files in a location controlled by the `DIAGNOSTIC_DEST` initialization parameter.

#### C.3.3 AUDIT_FILE_DEST

This parameter specifies the operating system directory into which the audit trail is written when the `AUDIT_TRAIL` initialization parameter is set to `os`, `xml`, or `xml,extended`. You must specify a POSIX directory for this parameter. The first default value for this parameter is `ORACLE_BASE/admin/ORACLE_SID/adump`. The second default value, which is used if the first default value does not exist or is unusable, is `ORACLE_HOME/rdbms/audit`. Remember that regardless of whether database auditing is enabled, Oracle Database on Fujitsu BS2000 always records some database-related actions into the operating system audit file, such as, instance startup, shutdown, and connections with administrator privileges.

**Note:**

In an Oracle Database that has been migrated to unified auditing, the setting of this parameter has no effect.

#### C.3.4 DB_BLOCK_SIZE

This parameter can have one of the following values:

- 2K, 4K, 6K, 8K, 16K, 32K, if you use BS2000 2K pubset format.

- 4K, 8K, 16K, 32K, if you use BS2000 4K pubset format.

#### C.3.5 DB_FILE_MULTIBLOCK_READ_COUNT

The maximum value of this parameter is `128K/DB_BLOCK_SIZE`, which in most cases is also the recommended value. Setting this parameter beyond this limit has no effect.

#### C.3.6 DB_FILES

The maximum value for this parameter is 65533 for BS2000.

#### C.3.7 LOCK_SGA

This parameter is ignored in Oracle Database 12c for Fujitsu BS2000. Buffers in the SGA are page-fixed only during I/O operations. Otherwise, the SGA on BS2000 is pageable.

#### C.3.8 SGA_MAX_SIZE

This parameter should not be specified for Fujitsu BS2000. Because the SGA is not permanently page-fixed as it is on some other systems, there is little benefit in reserving SGA expansion space with the `SGA_MAX_SIZE` parameter. It defaults to the actual SGA size.

#### C.3.9 LOG_ARCHIVE_DEST

This parameter can indicate a pubset, such as `LOG_ARCHIVE_DEST`=`:PUB1:` to store all the archived redo logs on a special media.
