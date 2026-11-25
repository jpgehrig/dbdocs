## Installing and Configuring Oracle ASMLIB Software

Review this information to install and configure the Oracle Automatic Storage Management library driver software manually.

Oracle ASMLIB is included with the Oracle Linux packages, and with SUSE Linux Enterprise Server. If you are a member of the Unbreakable Linux Network, then you can install the Oracle ASMLIB RPMs by subscribing to the Oracle Linux channel, and using `yum` to retrieve the most current package for your system and kernel. For additional information, see the following URL:

<https://www.oracle.com/linux/technologies/asmlib/>

**Note:**

- You must install Oracle ASMLib v3 (`oracleasmlib-3.0.0 or later` and `oracleasm-support-3.0.0 or later`) on all Oracle Database servers with Oracle Linux 8 and later kernels.
- You must install Oracle ASMLib v2 (`oracleasmlib-2.0.17 or later` and `oracleasm-support-2.1.3 or later`) on all Oracle Database servers with Oracle Linux 7 and earlier kernels.
- You can also use `dnf` instead of `yum`. For more information, see [Comparing Yum Version with DNF](https://docs.oracle.com/en/operating-systems/oracle-linux/8/relnotes8.0/ol8.0-ComparingYumVersion3WithDNF.html)

1.  Enter the following command to determine the kernel version and architecture of the system:
        # uname -rm
2.  Depending on your operating system version, download the required Oracle Automatic Storage Management library driver packages and driver:
    - For Oracle ASMLib v3, refer <https://docs.oracle.com/en/operating-systems/oracle-linux/asmlib/>
    - For Oracle ASMLib v2, refer <https://docs.oracle.com/en/operating-systems/oracle-linux/7/asmlib/>

    **See Also:**

    My Oracle Support note 1089399.1 for information about Oracle ASMLIB support with Red Hat distributions:

    <https://support.oracle.com/rs?type=doc&id=1089399.1>
3.  Switch to the `root` user:
        $ su -
4.  Depending on your operating system, you must install the `oracleasmlib` and `oracleasm-support` packages for all Oracle ASMLIB installations.
    **Note:**

    - For Oracle Linux 9.2 UEK7, additionally also install the `libbpf` and `libbpf-devel` packages.
    - Oracle Unbreakable Enterprise Kernel includes driver module, so you do not need to install `kmod-oracleasm`.

    Method 1 (recommended): If you have subscribed to Unbreakable Linux Network (ULN), then you can install the Oracle Automatic Storage Management library driver packages using a single `yum` command.

    For Unbreakable Enterprise Kernel

        # yum install oracleasm-support
        # yum install oracleasmlib
        # yum install libbpf
        # yum install libbpf-devel

    For Red Hat Compatible Kernel

        # yum install oracleasm-support
        # yum install oracleasmlib

    Method 2: Alternatively, download the Oracle Automatic Storage Management library driver packages as described in Step 2 and run the following `rpm -ivh` commands to install the packages in sequence.

    For Unbreakable Enterprise Kernel

        # rpm -ivh oracleasm-support-version.arch.rpm
        # rpm -ivh oracleasmlib-version.arch.rpm
        # rpm -ivh libbpf-version.arch.rpm
        # rpm -ivh libbpf-devel-version.arch.rpm

    For Red Hat Compatible Kernel

        # rpm -ivh oracleasm-support-version.arch.rpm
        # rpm -ivh oracleasmlib-version.arch.rpm

    Where `version` is the version of the Oracle Automatic Storage Management library driver, `arch` is the system architecture, and `kernel` is the version of the kernel that you are using.

    For example, if you are using Oracle Linux 9 on an x86_64 system, then enter a command similar to the following:

        # rpm -ivh oracleasmlib-3.0.0-9.el9.x86_64 \
                   oracleasm-support-3.0.0-21.el9.x86_64
5.  For SUSE Linux Enterprise Server 15, install the latest `oracleasmlib` and `oracleasm-support` RPM from <https://www.oracle.com/linux/downloads/linux-asmlib-sles15-downloads.html>.
    **Note:**

    ASMLib v3 is not supported for SUSE Linux Enterprise Server.
    Install the latest `oracleasm` driver module from the refreshed SUSE Linux Enterprise Server repository. The package name is `oracleasm-kmp-default`. For example, `oracleasm-kmp-default-2.0.8_k5.14.21_150500.55.36-150500.7.3.1.x86_64`
6.  Enter the following command to run the `oracleasm` initialization script with the `configure` option:
        # /usr/sbin/oracleasm configure -i

    **Note:**

    The oracleasm command in `/usr/sbin` is the command you should use. The `/etc/init.d` path is not deprecated, but the `oracleasm` binary in that path is now used typically for internal commands.
7.  Enter the following information in response to the prompts that the script displays:
    | Prompt                                         | Suggested Response                                                                                                                                                                                                                           |
    |:-----------------------------------------------|:---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | Default user to own the driver interface:      | Standard groups and users configuration: Specify the Oracle software owner user (for example, `oracle`)<br>Job role separation groups and users configuration: Specify the Grid Infrastructure software owner (for example, `grid`)          |
    | Default group to own the driver interface:     | Standard groups and users configuration: Specify the OSDBA group for the database (for example, `dba`).<br>Job role separation groups and users configuration: Specify the OSASM group for storage administration (for example, `asmadmin`). |
    | Start Oracle ASM Library driver on boot (y/n): | Enter `y` to start the Oracle Automatic Storage Management library driver when the system starts.                                                                                                                                            |
    | Scan for Oracle ASM disks on boot (y/n)        | Enter `y` to scan for Oracle ASM disks when the system starts.                                                                                                                                                                               |

    The script completes the following tasks:

    - Creates the `/etc/sysconfig/oracleasm` configuration file

    - Mounts the ASMLIB driver file system

      **Note:**

      The Oracle ASMLIB file system is not a regular file system. It is used only by the Oracle ASM library to communicate with the Oracle ASMLIB.
8.  Enter the following command to enable the Oracle ASMLIB file system:
    `# systemctl enable oracleasm`
9.  Enter the following command to start the Oracle ASMLIB file system:
    `# systemctl start oracleasm`

**Parent topic:** [Configuring Storage Device Path Persistence Using Oracle ASMLIB](configuring-storage-device-path-persistence-using-oracle-asmlib.md)
