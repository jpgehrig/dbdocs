## Checking OCFS2 Version Manually

Use the following command to check your OCFS2 version manually.

Ensure that `ocfs2console` and `ocfs2-tools` are at least version 1.2.7, and that the other OCFS2 components correspond to the pattern `ocfs2-``kernel_version``-1.2.7` or greater. If you want to install Oracle RAC on a shared home, then the OCFS2 version must be 1.4.1 or greater.

    modinfo ocfs2
    rpm -qa |grep ocfs2

For information about OCFS2, refer to the following website:

<http://oss.oracle.com/projects/ocfs2/>

**Parent topic:** [Configuring Storage for Oracle Grid Infrastructure](configuring-storage-for-oracle-grid-infrastructure-for-a-cluster.md)
