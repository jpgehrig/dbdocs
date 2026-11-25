## File System Options for Oracle Database

If you install Oracle Database files on a file system, then Oracle Database Configuration Assistant creates the database files in a directory on a file system mounted on the computer.

Oracle recommends that the file system be separate from the file systems used by the operating system or the Oracle Database software.

The file system can be any of the following:

### Standard Oracle Database Creation Options

- A file system on a disk that is physically attached to the system.

  If you are creating a database on basic disks that are not logical volumes or RAID devices, then Oracle recommends that you follow the Optimal Flexible Architecture (OFA) recommendations and distribute the database files over many disks.

- A file system on a logical volume manager (LVM) volume or a RAID device.

  If you are using multiple disks in an LVM or RAID configuration, then Oracle recommends that you use the Stripe and Mirror Everything (S.A.M.E) methodology to increase performance and reliability. Using this methodology, you do not have to specify multiple file system mount points for the database storage.

- A network file system (NFS) mounted from a certified network-attached storage (NAS) device. You also have the option to use Direct NFS Client, which simplifies the administration of NFS configurations and also improves performance.

### Advanced Oracle Database Creation Options

- The three file system options available to standard Oracle Database installations.

- With Oracle Managed Files, you specify file system directories in which the database automatically creates, names, and manages files at the database object level.

  If you use the Oracle Managed Files feature, then you must specify only the database object name instead of file names when creating or deleting database files.

**Related Topics**

- [Oracle RAC Technologies Matrix for Linux Platforms](https://www.oracle.com/database/technologies/rac-technologies-matrix-for-linux/)
- [Oracle Database Administrator’s Guide](../admin/creating-and-configuring-an-oracle-database.md)

**Parent topic:** [Supported Storage Options for Oracle Database and Oracle Grid Infrastructure](supported-storage-options-for-oracle-database-and-oracle-grid-infrastructure.md)
