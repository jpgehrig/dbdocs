## Disk Format Requirements

Oracle recommends that you install Oracle software, or binaries, on New Technology File System (NTFS) formatted drives or partitions.

Because it is difficult for OUI to estimate NTFS and file allocation table (FAT) disk sizes on Windows, the system requirements documented in this section are likely more accurate than the values reported on the OUI Summary screen.

**Note:**

Oracle Grid Infrastructure software is not supported on Network File System (NFS).

You cannot use NTFS formatted disks or partitions for Oracle Clusterware files or data files because they cannot be shared. Oracle Clusterware shared files and Oracle Database data files can be placed on unformatted basic disks or disk partitions, called raw partitions, managed by Oracle ASM.

Oracle Clusterware files and Oracle Database data files are stored on Oracle ASM, by default.

**Parent topic:** [Configuring Servers for Oracle Grid Infrastructure and Oracle RAC](configuring-servers-for-oracle-grid-infrastructure-and-oracle-rac.md)
