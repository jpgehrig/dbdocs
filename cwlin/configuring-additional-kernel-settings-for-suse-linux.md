## Configuring Additional Kernel Settings for SUSE Linux

Additional kernel parameter settings configuration is required on SUSE Linux Enterprise Server systems.

Perform these steps on SUSE Linux Enterprise Server systems only:

1.  Enter the following command to enable the system to read the `/etc/sysctl.conf `file when it restarts:
        # /sbin/chkconfig boot.sysctl on
2.  Enter the GID of the oinstall group as the value for the parameter /proc/sys/vm/hugetlb_shm_group.
    For example, where the oinstall group GID is `501`:

        # echo 501 > /proc/sys/vm/hugetlb_shm_group

    Use `vi `to add the following text to `/etc/sysctl.conf`, and enable the `boot.sysctl `script to run on system restart:
        vm.hugetlb_shm_group=501

    **Note:**

    Only one group can be defined as the vm.hugetlb_shm_group.

**Parent topic:** [Configuring Kernel Parameters for Linux](configuring-kernel-parameters-for-linux.md)
