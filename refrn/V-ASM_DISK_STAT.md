## 7.66 V\$ASM_DISK_STAT

`V$ASM_DISK_STAT` displays performance statistics in the same way that `V$ASM_DISK` does, but without performing discovery of new disks

This results in a less expensive operation. However, since discovery is not performed, the output of this view does not include any data about disks that are new to the system.

The columns for `V$ASM_DISK_STAT` are the same as those for `V$ASM_DISK`.

**See Also:**

"[V\$ASM_DISK](V-ASM_DISK.md)"
