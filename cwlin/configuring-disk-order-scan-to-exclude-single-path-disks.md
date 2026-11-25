## Configuring Disk Order Scan to Exclude Single Path Disks

To configure ASMLIB to exclude particular single path disks, complete the following procedure.

1.  Using a text editor, open the ASMLIB configuration file `/etc/sysconfig/oracleasm`.
2.  Edit the ORACLEASM_SCANEXCLUDE variable to provide the prefix path of the single path disks.
    For example, if you want to exclude the single path disks `/dev sdb` and `/dev/sdc`, then provide a prefix path similar to the following:

        ORACLEASM_SCANEXCLUDE="sdb sdc"
3.  Save the file.

When you have completed this procedure, then when ASMLIB scans disks, it scans all disks except for the disks with the `sdb` and `sdc` prefixes, so that it ignores `/dev/sdb` and `/dev/sdc`. It does not ignore other SCSI disks, nor multipath disks. If you have a multipath disk (for example, `/dev/multipatha`), which accesses both `/dev/sdb` and `/dev/sdc`, but you have configured ASMLIB to ignore `sdb` and `sdc`, then ASMLIB ignores these disks and instead marks only the multipath disk as an Oracle ASM disk.

**Parent topic:** [Configuring Oracle ASMLIB for Multipath Disks](configuring-oracle-asmlib-for-multipath-disks.md)
