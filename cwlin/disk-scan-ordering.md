## About Disk Scan Ordering

The ORACLEASM_SCANORDER variable specifies disks to be scanned first.

The ASMLIB configuration file is located in the path `/etc/sysconfig/oracleasm`. It contains all the startup configuration you specified with the command `/usr/sbin/oracleasm configure`. That command cannot configure scan ordering.

The configuration file contains many configuration variables. The ORACLEASM_SCANEXCLUDE variable specifies the disks that are to be ignored.

Configure values for ORACLEASM_SCANORDER using space-delimited prefix strings. A prefix string is the common string associated with a type of disk. For example, if you use the prefix string `sd`, then this string matches all SCSI devices, including `/dev/sda`, `/dev/sdb`, `/dev/sdc` and so on. Note that these are not globs. They do not use wild cards. They are simple prefixes. Also note that the path is not a part of the prefix. For example, the `/dev/ path` is not part of the prefix for SCSI disks that are in the path `/dev/sd*`.

For Oracle Linux and Red Hat Enterprise Linux, when scanning, the kernel sees the devices as `/dev/mapper/``XXX` entries. By default, the device file naming scheme udev creates the `/dev/mapper/``XXX` names for human readability. Any configuration using ORACLEASM_SCANORDER should use the `/dev/mapper/``XXX` entries.

**Parent topic:** [Configuring Oracle ASMLIB for Multipath Disks](configuring-oracle-asmlib-for-multipath-disks.md)
