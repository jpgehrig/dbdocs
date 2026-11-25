## Configuring HugePages on Linux

HugePages is a feature integrated into the Linux kernel. For Oracle Database, using HugePages reduces the operating system maintenance of page states and increases Translation Lookaside Buffer (TLB) hit ratio.

**Note:**

HugePages support is available in kernels built with the `CONFIG_HUGETLBFS` and `CONFIG_HUGETLB_PAGE` configuration options.

Oracle recommends that you reserve a minimum of 30 percent of the total memory for standard pages and not more than 70 percent of the total memory for HugePages.

Ensure that you have created the Oracle Database software owner (oracle) user accounts and all its groups. For more information see, [Automatically Configuring Oracle Linux with Oracle Database Preinstallation RPM](automatically-configuring-oracle-linux-with-oracle-preinstallation-rpm.md) or [Creating an Oracle Software Owner User](creating-an-oracle-software-owner-user.md).

### Enabling Using HugePages

Perform these steps to enable HugePages on Linux:

1.  Check if the kernel supports HugePages:

        $ grep Huge /proc/meminfo

2.  Edit the memlock setting in the `/etc/security/limits.conf` file.

    Specify the memlock setting in KB. Set the maximum locked memory limit to at least 90 percent of the current RAM when you enable HugePages memory and at least to 3145728 KB (3 GB) if you disable HugePages. For example, if you have 64 GB RAM, then add the following entries to increase the maximum locked-in-memory address space:

        oracle   soft   memlock    60397977
        oracle   hard   memlock    60397977

    You can also set the memlock value higher than your SGA requirements.

    **Note:**

    On Exadata systems, specify the memlock setting as `unlimited`.

3.  Log in as the `oracle` user again and run the `ulimit -l `command to verify the new memlock setting:

        $ ulimit -l
        60397977

4.  Run the following command to display the value of the Hugepagesize variable:

        $ grep Hugepagesize /proc/meminfo

5.  Determine the `gid` or `oracle` user group ID value:

        # id oracle

    The output is similar to the following:

        uid=54321(oracle) gid=54321(oinstall) groups=54321(oinstall),54322(dba),
        54323(oper),54324(backupdba),54325(dgdba),54326(kmdba),54327(asmdba),54330(racdba)

    Note the value of `gid`.

6.  Set the vm.hugetlb_shm_group kernel parameter value to the `gid` value:

        # sysctl -w vm.hugetlb_shm_group=gid

    where `gid` is the `oracle` user group ID. For example, value of `gid`=54321.

    To ensure that this value is available even after the system restarts, add the following entry to the `/etc/sysctl.d/99-hugetlb-shm-group.conf` file that contains this setting.

    vm.hugetlb_shm_group=gid

### Configuring the Capacity for HugePages

To configure the required number of HugePages for your databases, perform this step after you complete the Oracle Database installation and create your databases.

1.  Complete the following procedure to create a script that computes recommended values for HugePages configuration for the current shared memory segments:

    1.  Create a text file `hugepages_settings.sh`

        See [My Oracle Support note 401749.1](https://support.oracle.com/epmos/faces/DocContentDisplay?id=401749.1) to create the `hugepages_settings.sh` script.

    2.  Change the permission of the `hugepages_settings.sh` file:

            $ chmod +x hugepages_settings.sh

2.  Run the `hugepages_settings.sh` script to compute values for the HugePages configuration.

        $ ./hugepages_settings.sh

    **Note:**

    Before you run this script, ensure that all the databases that use hugepages run.

3.  Set the following kernel parameter, where `value` is the HugePages value that you determined in Step 2:

        # sysctl -w vm.nr_hugepages=value

4.  To ensure that HugePages is allocated after the system restarts, add the following entry to the `/etc/sysctl.d/99-nr_hugepages.conf` file, where `value` is the HugePages value that you determined in Step 2:

        vm.nr_hugepages=value

    **Note:**

    If you cannot set your HugePages allocation using `nr_hugepages`, then your available memory may be fragmented. Restart your server for the Hugepages allocation to take effect.

5.  Run the following command to check the available HugePages:

        $ grep Huge /proc/meminfo

6.  Restart the instances.

7.  Run the following command to check the available HugePages (1 or 2 pages free):

        $ grep Huge /proc/meminfo

**Parent topic:** [Guidelines for Linux Operating System Installation](guidelines-for-linux-operating-system-installation.md)
