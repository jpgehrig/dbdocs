## 1.181 LOG_ARCHIVE_DEST\_n

The `LOG_ARCHIVE_DEST_``n` initialization parameter defines up to 31 (where `n` = 1, 2, 3, ... 31) destinations, each of which must specify either the `LOCATION` or the `SERVICE` attribute to specify where to archive the redo data.

| Property            | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                        |
|:--------------------|:---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Parameter type      | String                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             |
| Syntax              | `LOG_ARCHIVE_DEST_[1 | 2 | 3 | 4 | 5 | 6 | 7 | 8 | 9 | 10 | 11 | 12 | 13 | 14 | 15 | 16 | 17 | 18 | 19 | 20 | 21 | 22 | 23 | 24 | 25 | 26 | 27 | 28 | 29 | 30 | 31] =`<br>` { null_string |`<br>` { LOCATION=path_name | SERVICE=service_name }`<br>` [ MANDATORY ]`<br>` [ REOPEN[=seconds] ]`<br>` [ DELAY[=minutes] ]`<br>` [ ENCRYPTION=ENABLED|DISABLED ]`<br>` [ GROUP=group ]`<br>` [ NOREGISTER ]`<br>` [ PRIORITY=priority ]`<br>` [ TEMPLATE=template ]`<br>` [ ALTERNATE=destination ]`<br>` [ MAX_FAILURE=count ]`<br>` [ SYNC | ASYNC ]`<br>` [ AFFIRM | NOAFFIRM ]`<br>` [ NET_TIMEOUT=seconds ]`<br>` [ VALID_FOR=(redo_log_type,database_role) ]`<br>` [ DB_UNIQUE_NAME ]`<br>` [ COMPRESSION={ENABLE|DISABLE|ZLIB|LZO} ]`<br>` }` |
| Default value       | There is no default value.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         |
| Modifiable          | `ALTER SESSION`, `ALTER SYSTEM`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    |
| Modifiable in a PDB | No                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 |
| Basic               | Yes                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                |

All other attributes except the `LOCATION` or `SERVICE` attributes are optional. Note that whether you are specifying the `LOCATION` attribute or the `SERVICE` attribute, it must be the first attribute supplied in the list of attributes.

If you choose not to enter any attributes, then you can specify a NULL string by entering the following:

    LOG_ARCHIVE_DEST_n=' ';

You set the attributes for the `LOG_ARCHIVE_DEST_``n` initialization parameter to control different aspects of how redo transport services transfer redo data from a production or primary database destination to another (standby) database destination. You can query the `V$ARCHIVE_DEST` view to see the current attribute settings for each destination (`n`).

**Note:**

Some of the attributes for this parameter are deprecated, but are being retained for backward compatibility. See "Deprecated Attributes for LOG_ARCHIVE_DEST_n".

For every `LOG_ARCHIVE_DEST_n` initialization parameter that you define, you must specify a corresponding `LOG_ARCHIVE_DEST_STATE_n` parameter. The `LOG_ARCHIVE_DEST_STATE_n` (where `n` is an integer from 1 to 31) initialization parameter specifies whether the corresponding destination is currently enabled or disabled.

**See Also:**

"[LOG_ARCHIVE_DEST_STATE_n](LOG_ARCHIVE_DEST_STATE_n.md)"

Destinations `LOG_ARCHIVE_DEST_11` through `LOG_ARCHIVE_DEST_31` do not support the `SYNC`, `ARCH`, `LOCATION`, `MANDATORY`, or `ALTERNATE` attributes, and cannot be specified as the target of the `ALTERNATE` attribute.

`LOG_ARCHIVE_DEST_11` through `LOG_ARCHIVE_DEST_31` can only be used when the `COMPATIBLE` initialization parameter is set to `11.2.0` or higher.

### Values

**See Also:**

[Oracle Data Guard Concepts and Administration](../sbydb/LOG_ARCHIVE_DEST_n-parameter-attributes.md) for detailed descriptions of all the values listed in this section

- [`AFFIRM` and `NOAFFIRM`](../sbydb/LOG_ARCHIVE_DEST_n-parameter-attributes.md)

  Control whether a redo transport destination acknowledges received redo data before or after writing it to the standby redo log. The default is `NOAFFIRM`.

- [`ALTERNATE=LOG_ARCHIVE_DEST_`n](../sbydb/LOG_ARCHIVE_DEST_n-parameter-attributes.md)

  Specifies an alternate archiving destination to be used when the original destination fails. There is no default value; if an alternate destination is not specified, then archiving does not automatically change to another destination if the original destination fails.

- [`ASYNC`](../sbydb/LOG_ARCHIVE_DEST_n-parameter-attributes.md)

  The redo data generated by a transaction need not have been received at a destination which has this attribute before that transaction can commit. This is the default behavior if neither `SYNC` nor `ASYNC` is specified.

- [`COMPRESSION`](../sbydb/LOG_ARCHIVE_DEST_n-parameter-attributes.md)

  Indicates whether network compression is enabled or disabled, or disabled, or whether the ZLIB or LZO algorithm is used. The possible values include:
  - `DISABLE`: Compression is disabled.

  - `ENABLE`: Compression is enabled. The ZLIB compression algorithm is used.

  - `ZLIB`: ZLIB compression is used.

  - `LZO`: LZO compression is used.

  The Advanced Compression option is required in order to use the `COMPRESSION` attribute.

- [`DB_UNIQUE_NAME`=name](../sbydb/LOG_ARCHIVE_DEST_n-parameter-attributes.md)

  Specifies a unique name for the database at this destination. You must specify a name; there is no default value.

- [`DELAY`\[=minutes\]](../sbydb/LOG_ARCHIVE_DEST_n-parameter-attributes.md)

  Specifies a minimum time lag between when redo data is archived on a standby site retrieving redo from a primary and when the archived redo log file is applied to the standby database or any standbys cascading from it. If you specify the DELAY attribute without a time interval, the default is 30 minutes.

- [`ENCRYPTION=DISABLE|ENABLE`](../sbydb/LOG_ARCHIVE_DEST_n-parameter-attributes.md)

  Controls whether encryption of the redo stream sent to Zero Data Loss Recovery Appliance (Recovery Appliance) is enabled or disabled. The default value for the attribute is `DISABLE`.

  This attribute cannot be used with the `COMPRESSION`, `LOCATION`, or `SYNC` attributes.

  To use the `ENCRYPTION` attribute, you must set the `COMPATIBLE` initialization parameter to `11.2.0.4` or higher on the protected database.

  **See Also:**

  [Zero Data Loss Recovery Appliance Administrator's Guide](https://docs.oracle.com/pls/topic/lookup?ctx=en/database/oracle/oracle-database/19/refrn&id=AMAGD-GUID-B57EDE37-6F78-409D-B29D-4D9F942174BC) for introductory information about Recovery Appliance

- [`GROUP`=group](../sbydb/LOG_ARCHIVE_DEST_n-parameter-attributes.md)

  The `GROUP` attribute is used to specify membership in a specific collection of log archive destinations. Groups are numbered 1 through 8. The default group (`GROUP=0`) is special in that it cannot be assigned. The default group is populated with all destinations that are not explicitly assigned to a group. All groups other than the default group must consist of a set of remote destinations. No group (other than the default group) can contain local destinations.

- [`LOCATION`=local_disk_directory or `USE_DB_RECOVERY_FILE_DEST`](../sbydb/LOG_ARCHIVE_DEST_n-parameter-attributes.md)

  Specifies either a local file system destination or the directory, file system, or Automatic Storage Management disk group that will serve as the fast recovery area. You must specify this attribute for at least one destination. You can specify either a local disk directory or fast recovery area with the `LOCATION` attribute. You must include either the `LOCATION` or the `SERVICE` attribute for each destination to specify where to archive the redo data.

- [`MANDATORY`](../sbydb/LOG_ARCHIVE_DEST_n-parameter-attributes.md)

  Specifies that the transmission of redo data to the destination must succeed before the local online redo log file can be made available for reuse. If the `MANDATORY` attribute is not specified, then the destination is optional.

- [`MAX_FAILURE`](../sbydb/LOG_ARCHIVE_DEST_n-parameter-attributes.md)

  Controls the consecutive number of times redo transport services attempt to reestablish communication and transmit redo data to a failed destination before the primary database gives up on the destination. See the `MAX_FAILURE` description in [Oracle Data Guard Concepts and Administration](../sbydb/LOG_ARCHIVE_DEST_n-parameter-attributes.md) for usage notes about how this attribute is handled differently in Oracle Database 12c Release 2 (12.2.0.1) and in Oracle Database 12c Release 1 (12.1.0.2).

- [`NET_TIMEOUT`=seconds](../sbydb/LOG_ARCHIVE_DEST_n-parameter-attributes.md)

  Specifies the number of seconds the log writer process on the primary system waits for status from the SYNC (NSSn) process before terminating the network connection. The default is 30 seconds.

- [`NOREGISTER`](../sbydb/LOG_ARCHIVE_DEST_n-parameter-attributes.md)

  Indicates that the location of the archived redo log file is not to be recorded at the corresponding destination.

- [`PRIORITY`=priority](../sbydb/LOG_ARCHIVE_DEST_n-parameter-attributes.md)

  The `PRIORITY` attribute is used to specify preference within a group of log archive destinations. Priorities are numbered 1 through 8. A lower value represents a higher priority. The lowest priority (`PRIORITY=8`) is special in the sense that if that priority is active then all destinations at that priority will be made active. If any higher priority destination returns to service then that destination will be made active and all low priority destinations will be made inactive because they will be receiving redo from one of the other redo destinations, either through cascading or a Far Sync.

- [`REOPEN`\[=seconds\]](../sbydb/LOG_ARCHIVE_DEST_n-parameter-attributes.md)

  Specifies the minimum number of seconds before the archiver processes (ARCn) or the log writer process (LGWR) should try again to access a previously failed destination. The default is 300 seconds.

- [`SERVICE`=net_service_name](../sbydb/LOG_ARCHIVE_DEST_n-parameter-attributes.md)

  Specifies a valid Oracle Net service name (`SERVICE=`net_service_name) that identifies the remote Oracle database instance to which redo data will be sent. Each destination must specify either the `LOCATION` or the `SERVICE` attribute. There is no default net service name.

- [`SYNC`](../sbydb/LOG_ARCHIVE_DEST_n-parameter-attributes.md)

  The redo data generated by a transaction must have been received by every enabled destination which has this attribute before that transaction can commit.

- [`TEMPLATE`](../sbydb/LOG_ARCHIVE_DEST_n-parameter-attributes.md)=filename_template\_%t\_%s\_%r

  Specifies a path name and a file name template for archived redo log files created at a redo transport destination that contain redo data from the database where this attribute is specified. This attribute overrides the value of the `LOG_ARCHIVE_FORMAT` initialization parameter at a redo transport destination. This attribute does not have a default value.

- [`VALID_FOR=(redo_log_type, database_role)`](../sbydb/LOG_ARCHIVE_DEST_n-parameter-attributes.md)

  Identifies when redo transport services can transmit redo data to destinations based on the following factors:

  - `redo_log_type`—whether online redo log files, standby redo log files, or both are currently being archived on the database at this destination

  - `database_role`—whether the database is currently running in the primary or the standby role

### Deprecated Attributes for LOG_ARCHIVE_DEST_n

The following attributes are deprecated for the `LOG_ARCHIVE_DEST_``n` parameter. They are retained for backward compatibility only.

Table 1-3 Deprecated Attributes on the LOG_ARCHIVE_DEST_n Initialization Parameter

| Deprecated Attribute | Alternative                                                                          |
|:---------------------|:-------------------------------------------------------------------------------------|
| `ARCH`               | Specify `SYNC` or `ASYNC`. `ASYNC` is the default if neither attribute is specified. |
| `LGWR`               | Specify `SYNC` or `ASYNC`. `ASYNC` is the default if neither attribute is specified. |
| `OPTIONAL`           | Destinations are optional by default.                                                |
| `VERIFY`             | None. This attribute is only used with the deprecated `ARCH` attribute.              |

In addition, note the following changes to the `ASYNC` and `SYNC` attributes:

- The `BLOCKS` keyword on the `ASYNC` attribute is no longer needed.

  It is no longer necessary to set this keyword because Data Guard dynamically adjusts the block count up or down to an appropriate number of blocks, as necessary.

- The `PARALLEL` and `NOPARALLEL` keywords on the `SYNC` attribute are no longer needed.
