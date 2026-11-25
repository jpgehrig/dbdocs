## 7.61 V\$ASM_AUDIT_LAST_ARCH_TS

In an Oracle Automatic Storage Management (Oracle ASM) instance, `V$ASM_AUDIT_LAST_ARCH_TS` displays information about the last archive timestamps set for audit trail cleanup or purges.

In a database instance, `V$ASM_AUDIT_LAST_ARCH_TS` displays no rows.

| Column            | Datatype                      | Description                                                                                                                                                                                                                                                                                                                                                                                                                 |
|:------------------|:------------------------------|:----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `AUDIT_TRAIL`     | `VARCHAR2(64)`                | Audit trail for which the last archive timestamp applies: `OS AUDIT TRAIL` and `UNIFIED AUDIT TRAIL`                                                                                                                                                                                                                                                                                                                        |
| `LAST_ARCHIVE_TS` | `TIMESTAMP(6) WITH TIME ZONE` | Timestamp of the last audit file that has been archived                                                                                                                                                                                                                                                                                                                                                                     |
| `CON_ID`          | `NUMBER`                      | The ID of the container to which the data pertains. Possible values include:<br>• `0`: This value is used for rows containing data that pertain to the entire CDB. This value is also used for rows in non-CDBs.<br>• `1`: This value is used for rows containing data that pertain to only the root<br>• n: Where n is the applicable container ID for the rows containing data<br>For this view, the value is always `0`. |

**See Also:**

[Oracle Automatic Storage Management Administrator's Guide](../ostmg/views-asm-info.md) for additional information about using views to display Oracle ASM information
