## Checking the Available Disk Space for Oracle Home Directories

Additional shared disk space on a cluster file system is required for the Oracle Grid Infrastructure Management Repository (GIMR), Oracle Cluster Registry (OCR) and voting files used by Oracle Clusterware.

If you are installing Oracle RAC, then you must configure additional disk space for:

- The Oracle RAC software and log files

- The shared data files and, optionally, the shared Fast Recovery Area in an Oracle ASM disk group

If you use standard redundancy for Oracle Clusterware files, which is 3 Oracle Cluster Registry (OCR) files and 3 voting files, then you should have at least 2 GB of disk space available on three separate physical disks reserved for storing the Oracle Clusterware files in Oracle ASM.

**Note:**

You cannot create OCR or voting files (Oracle Clusterware files) on raw partitions. You can store Oracle Clusterware files only on Oracle ASM. Raw devices can be configured as Oracle ASM disks.

To ensure high availability of OCR or voting files on Oracle ASM, you need to have at least 2 GB of disk space for Oracle Clusterware files in three separate failure groups, with at least three physical disks. Each disk must have at least 1 GB of capacity to ensure that there is sufficient space to create Oracle Clusterware files.

If the temp space and the Grid home are on the same file system, then add together their respective requirements for the total minimum space required for that file system.

**Note:**

Oracle recommends that you choose the Oracle Grid Infrastructure Management Repository option when installing Oracle Grid Infrastructure. When you choose this option, OUI configures a Oracle Grid Infrastructure Management Repository database on one of the nodes in the cluster.

To determine the amount of available free disk space, there are two methods you can use:

1.  Using the Computer properties window:
    1.  Open the Start menu, then click Computer.
    2.  View the free disk space for each drive.
    3.  Right-click the drive on which you plan to install the Oracle software and select Properties to view additional information about the disk space for that drive.
2.  Using the Disk Management Microsoft Management Console (MMC) plug-in:
    1.  From the Start menu, select Run...
    2.  In the Run window, type in `Diskmgmt.msc` to open the Disk Management graphical user interface (GUI).
        The Disk Management GUI displays the available space on the available file systems.

**Parent topic:** [Checking Server Hardware and Memory Configuration](checking-server-hardware-and-memory-configuration.md)
