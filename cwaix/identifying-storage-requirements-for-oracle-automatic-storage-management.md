To identify the storage requirements for using Oracle ASM, you must determine the number of devices and the amount of free disk space that you require.

To complete this task, follow these steps:

1.  Plan your Oracle ASM disk groups requirement, based on the cluster configuration you want to deploy. Oracle Domain Services Clusters store Oracle Clusterware files and the Grid Infrastructure Management Repository (GIMR) on separate Oracle ASM disk groups and hence require configuration of two separate Oracle ASM disk groups, one for OCR and voting files and the other for the GIMR.
2.  Determine whether you want to use Oracle ASM for Oracle Database files, recovery files, and Oracle Database binaries. Oracle Database files include data files, control files, redo log files, the server parameter file, and the password file.
    **Note:**

    - You do not have to use the same storage mechanism for Oracle Database files and recovery files. You can use a shared file system for one file type and Oracle ASM for the other.

    - There are two types of Oracle Clusterware files: OCR files and voting files. You can use either Oracle ASM or a shared file system to store OCR and voting files on Oracle Standalone Cluster deployments, but you must use Oracle ASM to store OCR and voting files on Oracle Domain Services cluster deployments.

    - If your database files are stored on a shared file system, then you can continue to use the same for database files, instead of moving them to Oracle ASM storage.
3.  Choose the Oracle ASM redundancy level to use for the Oracle ASM disk group.
    Except when using external redundancy, Oracle ASM mirrors all Oracle Clusterware files in separate failure groups within a disk group. A quorum failure group, a special type of failure group, contains mirror copies of voting files when voting files are stored in normal or high redundancy disk groups. The disk groups that contain Oracle Clusterware files (OCR and voting files) have a higher minimum number of failure groups than other disk groups because the voting files are stored in quorum failure groups in the Oracle ASM disk group.

    A quorum failure group is a special type of failure group that is used to store the Oracle Clusterware voting files. The quorum failure group is used to ensure that a quorum of the specified failure groups are available. When Oracle ASM mounts a disk group that contains Oracle Clusterware files, the quorum failure group is used to determine if the disk group can be mounted in the event of the loss of one or more failure groups. Disks in the quorum failure group do not contain user data, therefore a quorum failure group is not considered when determining redundancy requirements in respect to storing user data.

    The redundancy levels are as follows:

    - High redundancy

      In a high redundancy disk group, Oracle ASM uses three-way mirroring to increase performance and provide the highest level of reliability. A high redundancy disk group requires a minimum of three disk devices (or three failure groups). The effective disk space in a high redundancy disk group is one-third the sum of the disk space in all of its devices.

      For Oracle Clusterware files, a high redundancy disk group requires a minimum of five disk devices and provides five voting files and one OCR (one primary and two secondary copies). For example, your deployment may consist of three regular failure groups and two quorum failure groups. Note that not all failure groups can be quorum failure groups, even though voting files need all five disks. With high redundancy, the cluster can survive the loss of two failure groups.

      While high redundancy disk groups do provide a high level of data protection, you should consider the greater cost of additional storage devices before deciding to select high redundancy disk groups.

    - Normal redundancy

      In a normal redundancy disk group, to increase performance and reliability, Oracle ASM by default uses two-way mirroring. A normal redundancy disk group requires a minimum of two disk devices (or two failure groups). The effective disk space in a normal redundancy disk group is half the sum of the disk space in all of its devices.

      For Oracle Clusterware files, a normal redundancy disk group requires a minimum of three disk devices and provides three voting files and one OCR (one primary and one secondary copy). For example, your deployment may consist of two regular failure groups and one quorum failure group. With normal redundancy, the cluster can survive the loss of one failure group.

      If you are not using a storage array providing independent protection against data loss for storage, then Oracle recommends that you select normal redundancy.

    - External redundancy

      An external redundancy disk group requires a minimum of one disk device. The effective disk space in an external redundancy disk group is the sum of the disk space in all of its devices.

      Because Oracle ASM does not mirror data in an external redundancy disk group, Oracle recommends that you use external redundancy with storage devices such as RAID, or other similar devices that provide their own data protection mechanisms.

    - Flex redundancy

      A flex redundancy disk group is a type of redundancy disk group with features such as flexible file redundancy, mirror splitting, and redundancy change. A flex disk group can consolidate files with different redundancy requirements into a single disk group. It also provides the capability for databases to change the redundancy of its files. A disk group is a collection of file groups, each associated with one database. A quota group defines the maximum storage space or quota limit of a group of databases within a disk group.

      In a flex redundancy disk group, Oracle ASM uses three-way mirroring of Oracle ASM metadata to increase performance and provide reliability. For database data, you can choose no mirroring (unprotected), two-way mirroring (mirrored), or three-way mirroring (high). A flex redundancy disk group requires a minimum of three disk devices (or three failure groups).

    - Extended redundancy

      Extended redundancy disk group has similar features as the flex redundancy disk group. Extended redundancy is available when you configure an Oracle Extended Cluster. Extended redundancy extends Oracle ASM data protection to cover failure of sites by placing enough copies of data in different failure groups of each site. A site is a collection of failure groups. For extended redundancy with three sites, for example, two data sites, and one quorum failure group, the minimum number of disks is seven (three disks each for two data sites and one quorum failure group outside the two data sites). The maximum number of supported sites for extended redundancy is three. In an extended redundancy disk group, each site maintains the user data redundancy as specified by the file group attribute. Each site can host data failure groups and quorum failure groups for a given disk group. For example, if the file group redundancy is specified as 2 or 3, each site has 2 or 3 mirrors respectively, provided there are enough failure groups to accommodate the mirrors. See About Oracle Extended Clusters for more information about selecting redundancy levels for extended clusters.

    **See Also:**

    [Oracle Automatic Storage Management Administrator's Guide](../ostmg/asm-intro.md) for more information about file groups and quota groups for flex disk groups
    **Note:**

    You can alter the redundancy level of the disk group after a disk group is created. For example, you can convert a normal or high redundancy disk group to a flex redundancy disk group. Within a flex redundancy disk group, file redundancy can change among three possible values: unprotected, mirrored, or high.
4.  Determine the total amount of disk space that you require for Oracle Clusterware files, and for the database files and recovery files.
    If an Oracle ASM instance is running on the system, then you can use an existing disk group to meet these storage requirements. If necessary, you can add disks to an existing disk group during the database installation.

    See Oracle Clusterware Storage Space Requirements to determine the minimum number of disks and the minimum disk space requirements for installing Oracle Clusterware files, and installing the starter database, where you have voting files in a separate disk group.
5.  Determine an allocation unit size.
    Every Oracle ASM disk is divided into allocation units (AU). An allocation unit is the fundamental unit of allocation within a disk group. You can select the AU Size value from 1, 2, 4, 8, 16, 32, or 64 MB, depending on the specific disk group compatibility level. For flex disk groups, the default value for AU size is set to 4 MB. For external, normal, and high redundancies, the default AU size is 1 MB.
6.  For Oracle Clusterware installations, you must also add additional disk space for the Oracle ASM metadata. You can use the following formula to calculate the disk space requirements (in MB) for OCR and voting files, and the Oracle ASM metadata:
        total = [2 * ausize * disks] + [redundancy * (ausize * (all_client_instances + nodes + disks + 32) + (64 * nodes) + clients + 543)]

    redundancy = Number of mirrors: external = 1, normal = 2, high = 3, flex = 3.

    ausize = Metadata AU size in megabytes

    all_client_instance = Sum of all database clients and ACFS proxy instances

    nodes = Number of nodes in cluster.

    clients - Number of database instances for each node.

    disks - Number of disks in disk group.
7.  Optionally, identify failure groups for the Oracle ASM disk group devices.
    If you intend to use a normal or high redundancy disk group, then you can further protect the database against hardware failure by associating a set of disk devices in a custom failure group. By default, each device is included in its failure group. However, if two disk devices in a normal redundancy disk group are attached to the same Host Bus Adapter (HBA), then the disk group becomes unavailable if the adapter fails. The HBA in this example is a single point of failure.

    For instance, to avoid failures of this type, you can use two HBA fabric paths, each with two disks, and define a failure group for the disks attached to each adapter. This configuration would enable the disk group to tolerate the failure of one HBA fabric path.

    **Note:**

    You can define custom failure groups during installation of Oracle Grid Infrastructure. You can also define failure groups after installation using the GUI tool ASMCA, the command line tool asmcmd, or SQL commands. If you define custom failure groups, then you must specify a minimum of two failure groups for normal redundancy disk groups and three failure groups for high redundancy disk groups.
8.   If you are sure that a suitable disk group does not exist on the system, then install or identify appropriate disk devices to add to a new disk group. Use the following guidelines when identifying appropriate disk devices:
    - The disk devices must be owned by the user performing Oracle Grid Infrastructure installation.
    - All the devices in an Oracle ASM disk group must be the same size and have the same performance characteristics.
    - Do not specify multiple partitions on a single physical disk as a disk group device. Oracle ASM expects each disk group device to be on a separate physical disk.
    - Although you can specify a logical volume as a device in an Oracle ASM disk group, Oracle does not recommend their use because it adds a layer of complexity that is unnecessary with Oracle ASM. Oracle recommends that if you choose to use a logical volume manager, then use the logical volume manager to represent a single logical unit number (LUN) without striping or mirroring, so that you can minimize the effect on storage performance of the additional storage layer.
9.  If you use Oracle ASM disk groups created on Network File System (NFS) for storage, then ensure that you follow recommendations described in Guidelines for Configuring Oracle ASM Disk Groups on NFS.

**Parent topic:** [Configuring Storage for Oracle Automatic Storage Management](configuring-storage-for-oracle-automatic-storage-management.md)
