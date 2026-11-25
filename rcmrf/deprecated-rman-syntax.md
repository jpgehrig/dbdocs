## C Deprecated RMAN Syntax

This appendix describes Recovery Manager syntax that is deprecated and describes preferred syntax if any exists.

Deprecated RMAN syntax continues to be supported in subsequent releases for backward compatibility. For example, the `SET AUXNAME` command replaced the `SET CLONENAME` command in Oracle8i, and the `CONFIGURE AUXNAME` command replaced the `SET AUXNAME` command in Oracle9i. However, you can continue to run both `SET CLONENAME` and `SET AUXNAME` in all subsequent RMAN releases.

Table C-1 Deprecated RMAN Syntax

| Deprecated in Release | Deprecated Syntax                                                          | Preferred Current Syntax                                                                     |
|:----------------------|:---------------------------------------------------------------------------|:---------------------------------------------------------------------------------------------|
| 19c                   | `ADVISE FAILURE`                                                           | n/a                                                                                          |
| 19c                   | [`CHANGE`](CHANGE.md) `FAILURE`                                            | n/a                                                                                          |
| 19c                   | [`LIST`](LIST.md) `FAILURE`                                                | n/a                                                                                          |
| 19c                   | [`RECOVER`](RECOVER.md) `... SNAPSHOT TIME`                                | `RECOVER` `... UNTIL TIME`                                                                   |
| 19c                   | `REPAIR FAILURE`                                                           | n/a                                                                                          |
| 12.1                  | `ALTER DATABASE`                                                           | n/a                                                                                          |
| 11.2.0                | [CONFIGURE](CONFIGURE.md) or [SET](SET.md) `COMPRESSION ALGORITHM 'ZLIB'`  | [CONFIGURE](CONFIGURE.md) or [SET](SET.md) `COMPRESSION ALGORITHM 'MEDIUM'`                  |
| 11.2.0                | [CONFIGURE](CONFIGURE.md) or [SET](SET.md) `COMPRESSION ALGORITHM 'BZIP2'` | [CONFIGURE](CONFIGURE.md) or [SET](SET.md) `COMPRESSION ALGORITHM 'BASIC'`                   |
| 11.2.0                | `V$FLASH_RECOVERY_AREA_USAGE`                                              | `V$RECOVERY_AREA_USAGE`                                                                      |
| 11.1.0                | [`CONVERT`](CONVERT.md) `ON TARGET PLATFORM`                               | [`CONVERT`](CONVERT.md) `ON DESTINATION PLATFORM`                                            |
| 11.1.0                | `UNTIL RESTORE POINT`                                                      | `TO RESTORE POINT`                                                                           |
| 11.1.0                | [`BACKUP`](BACKUP.md) `... AS STANDBY`                                     | n/a                                                                                          |
| 11.1.0                | `... KEEP [LOGS | NOLOGS]`                                                 | `... KEEP`                                                                                   |
| 11.1.0                | `BLOCKRECOVER`                                                             | [`RECOVER`](RECOVER.md)                                                                      |
| 10.0.1                | [`BACKUP`](BACKUP.md) `... INCREMENTAL LEVEL` `[2,3,4]`                    | Levels other than `0` and `1` are deprecated.                                                |
| 10.0.1                | [`BACKUP`](BACKUP.md) `... PARMS`                                          | [`CONFIGURE`](CONFIGURE.md)` CHANNEL ... PARMS`                                              |
| 10.0.1                | `COPY`                                                                     | [`BACKUP`](BACKUP.md) `AS COPY`                                                              |
| 10.0.1                | [`CREATE CATALOG`](CREATE-CATALOG.md) `TABLESPACE`                         | [`CREATE CATALOG`](CREATE-CATALOG.md)                                                        |
| 10.0.1                | [`LIST`](LIST.md) `... BY BACKUP [SUMMARY]`                                | n/a                                                                                          |
| 10.0.1                | [`LIST`](LIST.md) `... VERBOSE`                                            | n/a                                                                                          |
| 10.0.1                | [`RESTORE`](RESTORE.md)` ... PARMS`                                        | [`CONFIGURE`](CONFIGURE.md) `CHANNEL ... PARMS`                                              |
| 10.0.1                | [`SEND`](SEND.md) `... PARMS`                                              | [`CONFIGURE`](CONFIGURE.md) `CHANNEL ... PARMS`                                              |
| 9.2                   | `REPLICATE`                                                                | [`RESTORE`](RESTORE.md) `CONTROLFILE FROM ...`                                               |
| 9.2                   | [`SET`](SET.md) `AUTOLOCATE`                                               | Enabled by default                                                                           |
| 9.0.1                 | `ALLOCATE CHANNEL FOR DELETE`                                              | n/a                                                                                          |
| 9.0.1                 | [`ALLOCATE CHANNEL`](ALLOCATE-CHANNEL.md)` ... TYPE`                       | [`CONFIGURE`](CONFIGURE.md) `CHANNEL ... DEVICE TYPE`                                        |
| 9.0.1                 | [`ALLOCATE CHANNEL`](ALLOCATE-CHANNEL.md) `... KBYTES`                     | [`CONFIGURE`](CONFIGURE.md) `CHANNEL ... MAXPIECESIZE`                                       |
| 9.0.1                 | [`ALLOCATE CHANNEL`](ALLOCATE-CHANNEL.md) `... READRATE`                   | [`CONFIGURE`](CONFIGURE.md) `CHANNEL ... RATE`                                               |
| 9.0.1                 | `... ARCHIVELOG ... LOGSEQ`                                                | `... ARCHIVELOG ... SEQUENCE`                                                                |
| 9.0.1                 | [`BACKUP`](BACKUP.md) `... SETSIZE`                                        | [`BACKUP`](BACKUP.md) `...` `MAXSETSIZE`                                                     |
| 9.0.1                 | [`CHANGE`](CHANGE.md) `... CROSSCHECK`                                     | [`CROSSCHECK`](CROSSCHECK.md)                                                                |
| 9.0.1                 | [`CHANGE`](CHANGE.md) `... DELETE`                                         | [`DELETE`](DELETE.md)                                                                        |
| 9.0.1                 | [`REPORT`](REPORT.md) `... AT LOGSEQ`                                      | `REPORT ... AT SEQUENCE`                                                                     |
| 9.0.1                 | [`SET`](SET.md) `AUXNAME`                                                  | [`CONFIGURE`](CONFIGURE.md) `AUXNAME`                                                        |
| 9.0.1                 | [`SET`](SET.md) `DUPLEX`                                                   | [`SET`](SET.md) `BACKUP COPIES`<br>[`CONFIGURE`](CONFIGURE.md) `BACKUP COPIES`               |
| 9.0.1                 | [`SET`](SET.md) `LIMIT CHANNEL ...`                                        | [`ALLOCATE CHANNEL`](ALLOCATE-CHANNEL.md) `...`<br>[`CONFIGURE`](CONFIGURE.md) `CHANNEL ...` |
| 9.0.1                 | [`SET`](SET.md) `SNAPSHOT`                                                 | [`CONFIGURE`](CONFIGURE.md) `SNAPSHOT`                                                       |
| 9.0.1                 | `UNTIL LOGSEQ` (see [`untilClause`](untilClause.md))                       | `UNTIL SEQUENCE` (see [`untilClause`](untilClause.md))                                       |
| 8.1.7                 | [`CONFIGURE`](CONFIGURE.md) `COMPATIBLE`                                   | n/a                                                                                          |
| 8.1.5                 | [`ALLOCATE CHANNEL`](ALLOCATE-CHANNEL.md) `CLONE`                          | [`CONFIGURE`](CONFIGURE.md) `AUXILIARY CHANNEL`                                              |
| 8.1.5                 | [`CHANGE`](CHANGE.md) `... VALIDATE`                                       | [`CROSSCHECK`](CROSSCHECK.md)                                                                |
| 8.1.5                 | `CLONE` (see [`RMAN`](RMAN.md))                                            | `AUXILIARY` (see [`RMAN`](RMAN.md))                                                          |
| 8.1.5                 | [`CONFIGURE`](CONFIGURE.md) `CLONE`                                        | [`CONFIGURE`](CONFIGURE.md) `AUXILIARY`                                                      |
| 8.1.5                 | `MSGLOG` (see [`RMAN`](RMAN.md))                                           | `LOG` (see [`RMAN`](RMAN.md))                                                                |
| 8.1.5                 | `RCVCAT` (see [`RMAN`](RMAN.md))                                           | `CATALOG` (see [`RMAN`](RMAN.md))                                                            |
