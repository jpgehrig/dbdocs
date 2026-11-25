## 7.68 V\$ASM_DISKGROUP_STAT

`V$ASM_DISKGROUP_STAT` displays performance statistics in the same way that `V$ASM_DISKGROUP` does, but without performing discovery of new disk groups.

This results in a less expensive operation. However, since discovery is not performed, the output of this view does not include any data about disk groups that are new to the system.

The columns for `V$ASM_DISKGROUP_STAT` are the same as those for `V$ASM_DISKGROUP`.

**See Also:**

"[V\$ASM_DISKGROUP](V-ASM_DISKGROUP.md)"
