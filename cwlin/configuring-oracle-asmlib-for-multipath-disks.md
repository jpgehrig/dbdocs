## Configuring Oracle ASMLIB for Multipath Disks

Additional configuration is required to use the Oracle Automatic Storage Management library Driver (ASMLIB) with third party vendor multipath disks.

- [About Using Oracle ASM with Multipath Disks](about-using-oracle-asm-with-multipath-disks.md)
  Oracle ASM requires that each disk is uniquely identified. If the same disk appears under multiple paths, then it causes errors.
- [About Disk Scan Ordering](disk-scan-ordering.md)
  The ORACLEASM_SCANORDER variable specifies disks to be scanned first.
- [Configuring Disk Scan Ordering to Select Multipath Disks](configuring-disk-scan-ordering-to-select-multipath-disks.md)
  To configure ASMLIB to select multipath disks first, complete the following procedure.
- [Configuring Disk Order Scan to Exclude Single Path Disks](configuring-disk-order-scan-to-exclude-single-path-disks.md)
  To configure ASMLIB to exclude particular single path disks, complete the following procedure.

**See Also:**

My Oracle Support site for updates to supported storage options:

<https://support.oracle.com/>

**Parent topic:** [Configuring Storage Device Path Persistence Using Oracle ASMLIB](configuring-storage-device-path-persistence-using-oracle-asmlib.md)
