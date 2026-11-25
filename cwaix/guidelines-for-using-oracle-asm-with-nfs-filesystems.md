Configuration guidelines for Automatic Storage Management (Oracle ASM) on NFS file systems.

**Note:**

The ACFS storage option on IBM AIX is deprecated in Oracle Database 19c.

You can create Oracle ASM disk groups on NFS (Network File System) or block devices on a supported Network Attached Storage (NAS) device. Understand the following guidelines for configuring Oracle ASM disk groups on NFS:

**Note:**

All storage products must be supported by both your server and storage vendors.

### Guidelines for Deploying Oracle ASM Disk Groups Without Quorum Disks

- To use an NFS file system, it must be on a supported NAS device. Log in to My Oracle Support at the following URL, and click Certifications to find the most current information about supported NAS devices:

  <https://support.oracle.com/>

- NFS file systems must be mounted and available over NFS mounts before you start installation. Refer to your vendor documentation to complete NFS configuration and mounting.

- Direct NFS requires hard mounts. Hard mounting NFS filers prevents corruption which could occur if the client connection were to time out. If an NFS filer hangs on an I/O operation to a mirrored file, then the database and Oracle ASM cannot failover to the surviving mirror copy. Therefore, Oracle recommends that you use external redundancy when you deploy Oracle ASM disk groups on NFS storage.

- Oracle ASM Filter Driver and Oracle ACFS and Oracle ADVM are not supported with NFS. These features are incompatible because of the nature of the operating system interface for NFS-based storage.

  **Note:**

  Oracle ACFS does not support NFS disks in an Oracle ASM disk group, but you can use NFS disks with Oracle ACFS using Oracle ACFS NAS Maximum Availability eXtensions (Oracle ACFS NAS MAX).

- The performance of Oracle software and databases stored on Oracle ASM disk groups on NFS depends on the performance of the network connection between the Oracle server and the NAS device. Oracle recommends that you connect the server to the NAS device using a private dedicated network connection, which should be Gigabit Ethernet or better.

- You can configure Oracle ASM on NFS when you deploy an Oracle Standalone Cluster configuration.

- You can specify separate NFS locations for Oracle ASM disk groups for Oracle Clusterware files and the Grid Infrastructure Management Repository (GIMR).

- The user account with which you perform the installation (`oracle` or `grid`) must have write permissions to create the files in the path that you specify.

- When you choose Oracle ASM on NFS, you cannot use Oracle Automatic Storage Management Cluster File System (Oracle ACFS) for storage. This cluster configuration cannot be used as a Oracle Fleet Patching and Provisioning Server.

### Guidelines for Deploying Oracle ASM Disk Groups With Quorum Disks

- SAN-attached storage or iSCSI-attached devices are the preferred ways to connect to quorum disks. If your standard deployment requires NFS to be used as storage, then use soft mounts for NFS-based Oracle ASM quorum disks and hard mounts for other Oracle ASM disks.

- You can use Direct NFS (dNFS) for storage of Oracle Database data files. dNFS does not support soft mounts, so you cannot use dNFS for quorum failure groups. Alternatively, use kernel-based NFS with a soft mount for NFS storage residing in a quorum failure group.

- The quorum failure group feature in Oracle ASM enables use of NFS storage in an Oracle ASM disk group without requiring a hard mount for NFS storage in the quorum failure group. This capability is useful for Oracle Extended Clusters where a third site is required for establishing quorum.

**Related Topics**

- [Creating Files on a NAS Device for Use with Oracle Automatic Storage Management](creating-files-on-a-nas-device-for-use-with-oracle-automatic-storage-management.md)

**Parent topic:** [Supported Storage Options for Oracle Database and Oracle Grid Infrastructure](supported-storage-options-for-oracle-database-and-oracle-grid-infrastructure.md)
