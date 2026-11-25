## Oracle ACFS and Oracle ADVM Support on Linux x86–64

Oracle ACFS and Oracle ADVM are supported on Oracle Linux, Red Hat Enterprise Linux, and SUSE Linux Enterprise Server.

Table 7-2 Platforms That Support Oracle ACFS and Oracle ADVM

| Platform / Operating System     | Kernel                                                                                                       |
|:--------------------------------|:-------------------------------------------------------------------------------------------------------------|
| Oracle Linux 9                  | Starting with Oracle Database 19c (19.21), all Oracle Linux 9.2 and later compatible kernels                 |
| Oracle Linux 8                  | All Oracle Linux 8 compatible kernels                                                                        |
| Oracle Linux 7                  | All Oracle Linux 7 compatible kernels, except Unbreakable Enterprise Kernel 6 (UEK 6) and later UEK kernels. |
| Red Hat Enterprise Linux 9      | Starting with Oracle Database 19c (19.21), all Red Hat Enterprise Linux 9.2 and later compatible kernels     |
| Red Hat Enterprise Linux 8      | All Red Hat Enterprise Linux 8 compatible kernels                                                            |
| Red Hat Enterprise Linux 7      | All Red Hat Enterprise Linux 7 compatible kernels                                                            |
| SUSE Linux Enterprise Server 12 | All SUSE Linux Enterprise Server 12 compatible kernels                                                       |
| SUSE Linux Enterprise Server 15 | All SUSE Linux Enterprise Server 15 compatible kernels                                                       |
| Linux Containers                | Not supported                                                                                                |

**Note:**

If you use Security Enhanced Linux (SELinux) in enforcing mode with Oracle ACFS, then ensure that you mount the Oracle ACFS file systems with an SELinux default context. Refer to your Linux vendor documentation for information about the context mount option.

**Important:**

You must apply patches to some of the Linux kernel versions for successful Oracle Grid Infrastructure installation. Refer to the following notes for more information:

- My Oracle Support Note 1369107.1 for more information and a complete list of platforms and releases that support Oracle ACFS and Oracle ADVM:

  <https://support.oracle.com/rs?type=doc&id=1369107.1>

- Patch Set Updates for Oracle Products (My Oracle Support Note 854428.1) for current release and support information:

  <https://support.oracle.com/rs?type=doc&id=854428.1>

**Parent topic:** [Oracle ACFS and Oracle ADVM](oracle-acfs-and-oracle-advm.md)
