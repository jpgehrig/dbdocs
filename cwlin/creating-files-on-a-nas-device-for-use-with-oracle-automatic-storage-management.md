## Creating Files on a NAS Device for Use with Oracle Automatic Storage Management

If you have a certified NAS storage device, then you can create zero-padded files in an NFS mounted directory and use those files as disk devices in an Oracle ASM disk group.

Ensure that you specify the ASM discovery path for Oracle ASM disks.

During installation of Oracle Grid Infrastructure, Oracle Universal Installer (OUI) can create files in the NFS mounted directory you specify. The following procedure explains how to manually create files in an NFS mounted directory to use as disk devices in an Oracle ASM disk group:

1.  If necessary, create an exported directory for the disk group files on the NAS device.
2.  Switch user to `root`.
3.  Create a mount point directory on the local system.
    For example:

        # mkdir -p /mnt/oracleasm
4.  To ensure that the NFS file system is mounted when the system restarts, add an entry for the file system in the mount file `/etc/fstab`.
5.  Enter a command similar to the following to mount the NFS on the local system:
        # mount /mnt/oracleasm
6.  Choose a name for the disk group to create, and create a directory for the files on the NFS file system, using the disk group name as the directory name.
    For example, if you want to set up a disk group for a sales database:
        # mkdir /mnt/oracleasm/sales1
7.  Use commands similar to the following to create the required number of zero-padded files in this directory:
        # dd if=/dev/zero
        of=/mnt/oracleasm/sales1/disk1 bs=1024k
        count=1000

    This example creates 1 GB files on the NFS file system. You must create one, two, or three files respectively to create an external, normal, or high redundancy disk group.

    **Note:**

    Creating multiple zero-padded files on the same NAS device does not guard against NAS failure. Instead, create one file for each NAS device and mirror them using the Oracle ASM technology.
8.  Enter commands similar to the following to change the owner, group, and permissions on the directory and files that you created:
        # chown -R grid:asmadmin /mnt/oracleasm
        # chmod -R 660 /mnt/oracleasm

    In this example, the installation owner is `grid` and the OSASM group is `asmadmin`.
9.  During Oracle Database installations, edit the Oracle ASM disk discovery string to specify a regular expression that matches the file names you created.
    For example:

        /mnt/oracleasm/sales1/

**Related Topics**

- [My Oracle Support Note 359515.1](https://support.oracle.com/rs?type=doc&id=359515.1)

**Parent topic:** [Configuring Storage for Oracle Automatic Storage Management](configuring-storage-for-oracle-automatic-storage-management.md)
