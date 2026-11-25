## Configuring Disk Scan Ordering to Select Multipath Disks

To configure ASMLIB to select multipath disks first, complete the following procedure.

1.  Using a text editor, open the ASMLIB configuration file `/etc/sysconfig/oracleasm`.
2.  Edit the ORACLEASM_SCANORDER variable to provide the prefix path of the multipath disks.
    For example, if the multipath disks use the prefix multipath (`/dev/mapper/multipatha`, `/dev/mapper/multipathb` and so on), and the multipath disks mount SCSI disks, then provide a prefix path similar to the following:

        ORACLEASM_SCANORDER="multipath sd"
3.  Save the file.

When you have completed this procedure, then when ASMLIB scans disks, it first scans all disks with the prefix string multipath, and labels these disks as Oracle ASM disks using the` /dev/mapper/multipath``X`` `value. It then scans all disks with the prefix string `sd`. However, because ASMLIB recognizes that these disks have already been labeled with the `/dev/mapper/multipath` string values, it ignores these disks. After scanning for the prefix strings `multipath` and `sd`, Oracle ASM then scans for any other disks that do not match the scan order.

In the example in step 2, the key word `multipath` is actually the alias for multipath devices configured in `/etc/multipath.conf` under the multipaths section. The default device name is in the format `/dev/mapper/mpath*` (or a similar path). For example:

    multipaths {
           multipath {
                   wwid                    3600508b4000156d700012000000b0000
                   alias                   multipath
                   ...
           }
           multipath {
                   ...
                   alias                   mympath
                   ...
           }
           ...
    }

**Parent topic:** [Configuring Oracle ASMLIB for Multipath Disks](configuring-oracle-asmlib-for-multipath-disks.md)
