## 1.22 ASM_PREFERRED_READ_FAILURE_GROUPS

`ASM_PREFERRED_READ_FAILURE_GROUPS` specifies the failure groups that contain preferred read disks. Preferred disks are instance specific.

| Property            | Description                                                                        |
|:--------------------|:-----------------------------------------------------------------------------------|
| Parameter type      | String                                                                             |
| Syntax              | `ASM_PREFERRED_READ_FAILURE_GROUPS = ‘<diskgroup_name>.<failure_group_name>, ...’` |
| Default value       | NULL                                                                               |
| Modifiable          | `ALTER SYSTEM`                                                                     |
| Modifiable in a PDB | No                                                                                 |
| Basic               | No                                                                                 |
| Oracle RAC          | The value is different on different nodes                                          |

**Note:**

The `ASM_PREFERRED_READ_FAILURE_GROUPS` initialization parameter is deprecated in Oracle Database 12c Release 2 (12.2.0.1) and may be desupported in a future release. It is replaced by the `PREFERRED_READ.ENABLED` disk group attribute.

See [Oracle Automatic Storage Management Administrator's Guide](../ostmg/manage-diskgroup-attributes.md) for more information about the `PREFERRED_READ.ENABLED` disk group attribute.

To reset the parameter value to null, issue the following statement, which updates the server parameter file (SP file), then reboot Oracle ASM so that the change takes effect:

    alter system reset asm_preferred_read_failure_groups;

**See Also:**

[Oracle Automatic Storage Management Administrator's Guide](../ostmg/init-params-asm-instance.md) for more information about this parameter
