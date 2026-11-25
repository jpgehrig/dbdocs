## Installing OCFS2

You can use Oracle Cluster File System 2 (OCFS2) with Oracle Grid Infrastructure. However, you are not required to use OCFS2.

OCFS2 is a POSIX-compliant general purpose shared disk cluster file system for Linux. OCFS2 is supported for this release only with Oracle Linux.

An OCFS2 installation consists of two parts, the kernel module and the tools module.

The supported version of the OCFS2 kernel module depends on the version of Unbreakable Enterprise Kernel available with Oracle Linux. Run the following command to install the latest version of the OCFS2 kernel module:

`# yum install kernel-uek ocfs2`

OCFS2 Release 1.8.6–9 is the supported version of OCFS2 tools module for this release. After you install the OCFS2 kernel module, run the following command, to install the OCFS2 tools module:

`# yum install ocfs2–tools-1.8.6–9`

**Note:**

- Each cluster node should run the same version of OCFS2 modules and a compatible version of Unbreakable Enterprise Kernel.
- OCFS2 is not supported on Linux for Arm (aarch64).

<https://oss.oracle.com/projects/ocfs2/>

**Parent topic:** [Additional Drivers and Software Packages for Linux](additional-drivers-and-software-packages-for-linux.md)
