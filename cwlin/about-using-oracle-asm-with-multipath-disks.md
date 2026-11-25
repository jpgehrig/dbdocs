## About Using Oracle ASM with Multipath Disks

Oracle ASM requires that each disk is uniquely identified. If the same disk appears under multiple paths, then it causes errors.

In a multipath disk configuration, the same disk can appear three times: the initial path to the disk, the second path to the disk, and the multipath disk access point.

For example: If you have one local disk, `/dev/sda`, and one disk attached with external storage, then your server shows two connections, or paths, to that external storage. The Linux SCSI driver shows both paths. They appear as `/dev/sdb` and `/dev/sdc`. The system may access either `/dev/sdb` or` /dev/sdc`, but the access is to the same disk.

If you enable multipathing, then you have a multipath disk (for example, `/dev/multipatha`), which can access both `/dev/sdb` and `/dev sdc`; any I/O to `multipatha` can use either the sdb or sdc path. If a system is using the `/dev/sdb` path, and that cable is unplugged, then the system shows an error. But the multipath disk will switch from the `/dev/sdb` path to the `/dev/sdc` path.

Most system software is unaware of multipath configurations. They can use any paths (`sdb`, `sdc` or `multipatha`). ASMLIB also is unaware of multipath configurations.

By default, ASMLIB recognizes the first disk path that Linux reports to it, but because it imprints an identity on that disk, it recognizes that disk only under one path. Depending on your storage driver, it may recognize the multipath disk, or it may recognize one of the single disk paths.

Instead of relying on the default, you should configure Oracle ASM to recognize the multipath disk.

**Parent topic:** [Configuring Oracle ASMLIB for Multipath Disks](configuring-oracle-asmlib-for-multipath-disks.md)
