This chapter describes the tasks that you must complete before you install Oracle Instant Client. It includes the following information:

- Logging In to the System as root

- Checking the Hardware Requirements

- Checking the Software Requirements

### Logging In to the System as root

Before you install the Oracle software, you must complete several tasks as the `root` user. To log in as the `root` user, complete the following procedure:

- If you are installing the software from an X Window System workstation or X terminal, then:

1.  Start a local terminal session (`xterm`).

2.  If you are not installing the software on the local system, then enter the following command to enable the remote host to display X applications on the local X server:

        $ xhost fully_qualified_remote_host_name

    For example,

        $ xhost somehost.us.example.com

3.  If you are not installing the software on the local system, then use the `ssh`, `rlogin`, or `telnet` command to connect to the system where you want to install the software:

        $ telnet fully_qualified_remote_host_name

4.  If you are not logged in as the `root` user, then enter the following command to switch user to `root`:

        $ su - root
        password:
        #

**Note:**

Unless you intend to complete a silent-mode installation, you must install the software from an X Window System workstation, an X terminal, or a PC or other system with X server software installed.

- If you are installing the software from a PC or other system with X server software installed, then:

1.  Start the X server software.
2.  Configure the security settings of the X server software to permit remote hosts to display X applications on the local system.
3.  Connect to the remote system where you want to install the software and start a terminal session on that system, for example, an X terminal (`xterm`).
4.  If you are not logged in as the `root` user on the remote system, then enter the following command to switch user to `root`:
        $ su - root
        password:
        #

**Note:**

If necessary, refer to your X server documentation for more information about completing this procedure. Depending on the X server software that you are using, you may need to complete the tasks in a different order.

### Checking the Hardware Requirements

The system must meet the following minimum hardware requirements for Oracle Database Client:

- Memory Requirements

- System Architecture

- Disk Space Requirements

- Display Requirements

- Recommended Hardware Requirement for SQL Developer

#### Memory Requirements

The following are the memory requirements for Oracle Database Client:

- 256 MB of RAM.

  To determine the physical RAM size, enter the following command:

      # grep MemTotal /proc/meminfo

  If the size of the physical RAM is less than the required size, then you must install more memory before continuing.

- The following table describes the relationship between installed RAM and the configured swap space recommendation:

  **Note:**

  On Linux on POWER Systems, the HugePages feature allocates non-swappable memory for large page tables using memory-mapped files. If you enable HugePages, then you should deduct the memory allocated to HugePages from the available RAM before calculating swap space.

  | Available RAM             | Swap Space Required        |
  |:--------------------------|:---------------------------|
  | Up to 256 MB              | 3 times the size of RAM    |
  | Between 257 MB and 512 MB | 2 times the size of RAM    |
  | Between 513 MB and 726 MB | 1.5 times the size of RAM  |
  | More than 726 MB          | 0.75 times the size of RAM |

To determine the size of the configured swap space, enter the following command:

    # grep SwapTotal /proc/meminfo

If necessary, see the operating system documentation for information about how to configure additional swap space.

To determine the available RAM and swap space, enter the following command:

    # free

**Note:**

- Oracle recommends that you take multiple values for the available RAM and swap space before finalizing on a value. This is because the available RAM and swap space keep changing depending on the user interactions with the computer.

- Contact the operating system vendor for swap space allocation guidance for your server. The vendor guidelines supersede the swap space requirements listed in this guide.

#### System Architecture

To determine whether the system architecture can run the software, enter the following command:

    # uname -m

**Note:**

This command displays the processor type. Verify that the processor architecture matches the Oracle software release to install. If you do not see the expected output, then you cannot install the software on this system.

#### Disk Space Requirements

The following are the disk space requirements for Oracle Database Client:

- The minimum disk space requirement for a client install in the `/tmp `directory is 120 MB. The minimum disk space requirement in the `/tmp `directory depends on the installation type you have selected. The following table lists the minimum disk space requirements for the `/tmp `directory in each type of installation.

  To determine the amount of disk space available, enter the following command:

      # df -k /tmp

  If there is less than 120 MB of free space available in the `/tmp `directory, then complete one of the following steps:

  - Delete unnecessary files from the `/tmp` directory to meet the space requirement.

  - Set the `TMP` and `TMPDIR` environment variables when setting the `oracle` user's environment.

  - Extend the file system that contains the `/tmp `directory. If necessary, contact the system administrator for information about extending file systems.

- To determine the amount of free disk space on the system, enter the following command:

      # df -k

  The client install requires 130 MB disk space for software files on Linux on POWER Systems.

#### Display Requirements

The minimum display requirement for Oracle Database Client is a resolution of 1024 x 768 or higher.

#### Recommended Hardware Requirement for SQL Developer

The following are the recommended CPU, Memory and Display requirements for SQL Developer:

| Resource | Recommended                                         |
|:---------|:----------------------------------------------------|
| Memory   | 1 GB RAM (recommended), 256 MB RAM (minimum)        |
| Display  | 65536 colors, set to at least 1024 X 768 resolution |

### Checking the Software Requirements

Depending on the products that you intend to install, verify that the following software is installed on the system:

| Item                                         | Requirement                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                     |
|:---------------------------------------------|:----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Operating system                             | The following operating systems (or a later version) are supported:<br>• Red Hat Enterprise Linux Server 7.1<br>• SUSE Linux Enterprise Server 12                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                               |
| Kernel version                               | The system must be running the following kernel versions (or a later version):<br>• Red Hat Enterprise Linux Server 7.1 (`3.10.0-229.ael7b.ppc64le`)<br>• SUSE Linux Enterprise Server 12 (`3.12.28-4.6.ppc64le`)                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                               |
| Red Hat Enterprise Linux Server 7.1 Packages | The following packages must be installed:<br>`binutils-2.23.52.0.1-30.ael7b.ppc64le`<br>`compat-openldap-2.3.43-5.ael7b.ppc64le`<br>`compat-libtiff3-3.9.4-11.ael7b.ppc64le`<br>`compat-libcap1-1.10-7.ael7b.ppc64le`<br>`compat-db47-4.7.25-28.ael7b.ppc64le`<br>`compat-db-headers-4.7.25-28.ael7b.noarch`<br>`libstdc++-4.8.3-9.ael7b.ppc64le`<br>`libstdc++-devel-4.8.3-9.ael7b.ppc64le`<br>`gcc-4.8.3-9.ael7b.ppc64le`<br>`gcc-c++-4.8.3-9.ael7b.ppc64le`<br>`libgcc-4.8.3-9.ael7b.ppc64le`<br>`gcc-gfortran-4.8.3-9.ael7b.ppc64le`<br>`libaio-devel-0.3.109-12.ael7b.ppc64le`<br>`libaio-0.3.109-12.ael7b.ppc64le`<br>`glibc-common-2.17-78.ael7b.ppc64le`<br>`glibc-devel-2.17-78.ael7b.ppc64le`<br>`glibc-2.17-78.ael7b.ppc64le`<br>`glibc-headers-2.17-78.ael7b.ppc64le`<br>`GNU Make 3.82 for powerpc64le-redhat-linux-gnu`<br>`sysstat-10.1.5-7.ael7b.ppc64le`<br>`java-1.8.0-openjdk for ppc64le`<br>`java-1.8.0-openjdk-headless-1.8.0 for ppc64le`<br>`IBM XL C/C++ for Linux, V13.1.2 (5725-C73, 5765-J08)`<br>`Version: 13.01.0002.0000`                                                        |
| SUSE Linux Enterprise Server 12 Packages     | The following packages must be installed:<br>`binutils-2.24-2.165.ppc64le`<br>`libstdc++-devel-4.8-6.189.ppc64le`<br>`libstdc++6-4.8.3+r212056-6.3.ppc64le`<br>`libstdc++48-devel-4.8.3+r212056-6.3.ppc64le`<br>`libgcc_s1-4.8.3+r212056-6.3.ppc64le`<br>`gcc48-info-4.8.3+r212056-6.3.noarch`<br>`gcc-info-4.8-6.189.ppc64le`<br>`gcc48-locale-4.8.3+r212056-6.3.ppc64le`<br>`gcc-locale-4.8-6.189.ppc64le`<br>`gcc-4.8-6.189.ppc64le`<br>`gcc-c++-4.8-6.189.ppc64le`<br>`gcc48-4.8.3+r212056-6.3.ppc64le`<br>`gcc48-c++-4.8.3+r212056-6.3.ppc64le`<br>`glibc-i18ndata-2.19-17.72.noarch`<br>`glibc-devel-2.19-17.72.ppc64le`<br>`glibc-info-2.19-17.72.noarch`<br>`glibc-html-2.19-17.72.noarch`<br>`glibc-locale-2.19-17.72.ppc64le`<br>`linux-glibc-devel-3.12-3.98.noarch`<br>`glibc-profile-2.19-17.72.ppc64le`<br>`glibc-2.19-17.72.ppc64le`<br>`libaio-devel-0.3.109-17.15.ppc64le`<br>`libaio1-0.3.109-17.15.ppc64le`<br>`sysstat-10.2.1-1.11.ppc64le`<br>`sysstat-isag-10.2.1-1.11.ppc64le`<br>`GNU Make 4.0`<br>`IBM XL C/C++ for Linux, V13.1.1 (5725-C73, 5765-J08)`<br>`Version: 13.01.0001.0000` |
| C/C++ Runtime Environment                    | Download the following IBM XL C/C++ Runtime Environment:<br>• V13.1.1 for SUSE Linux Enterprise Server 12 at<br>• [`http://www-01.ibm.com/support/docview.wss?uid=swg24039070`](http://www-01.ibm.com/support/docview.wss?uid=swg24039070)<br>• V13.1.2 for Red Hat Enterprise Linux Server 7.1 at<br>• [`http://www-01.ibm.com/support/docview.wss?uid=swg24040214`](http://www-01.ibm.com/support/docview.wss?uid=swg24040214)<br>If you need VAC optimization packages, then you must download and install the XL Optimization Libraries component from this link.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           |
| Compilers                                    | The version of GNU C and C++ compilers listed under Packages are supported.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                     |
| Pro\*FORTRAN                                 | The following fortran versions (or a later version) are supported:<br>• IBM XL Fortran V15.1.2<br>• GNU Fortran (GCC) 4.8.3 20140911                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            |
| Oracle JDBC- OCI Drivers                     | You can use the following JDBC - OCI drivers; however, these are not required for the installation:<br>• JDBC-OCI 1.8.0 or later on RHEL 7.1<br>• JDBC-OCI 1.8.0 or later versions on SUSE 12                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   |
| Oracle ODBC Driver                           | To use ODBC, you must also install the following additional ODBC RPMs, depending on your operating system.<br>Red Hat Enterprise Linux Server 7.1<br>`unixODBC-2.3.1-4.95.ppc64le`<br>SUSE Linux Enterprise Server 12:<br>`unixODBC-2.3.1-4.95.ppc64le`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         |

If you want to use GNU Compiler Collection (GCC) as the primary compiler, see the "[Configuring GCC as the Primary Compiler](oracle-database-client-postinstallation-tasks.md)" section for instructions on configuring the primary compiler.

The following procedure describes how to verify and ensure that the system meets these requirements:

1.  To determine which distribution and version of Linux is installed, enter the following command:
        # cat /etc/issue

    **Note:**

    Only the distributions and versions listed in the previous table are supported. Do not install the software on other versions of Linux on POWER Systems.
2.  To determine whether the required kernel is installed, enter the following command:
        # uname -r

    The following is a sample output displayed by running this command on a Red Hat Enterprise Linux Server 7.1 system:

        3.10.0-229.ael7b.ppc64le

    In this example, the output shows the kernel version (3.10.0) and errata level (ael17b) on the system.

    If the kernel version does not meet the requirement specified earlier in this section, then contact your operating system vendor for information about obtaining and installing kernel updates.
3.  To determine whether the required packages are installed, enter commands similar to the following:
        # rpm -q package_name

    If a package is not installed, then install it from your Linux distribution media or download the required package version from your Linux vendor's website.

#### Instant Client Light Requirements

In addition to the requirements described in the preceding section, if you plan to use Instant Client Light, then the applications must use the following languages and character sets:

- Language: Any language that is supported by Oracle.

- Territory: Any territory that is supported by Oracle.

- Character sets:

  - Single byte

    - `US7ASCII`

    - `WE8DEC`

    - `WE8MSWIN1252`

    - `WE8ISO8859P1`

    - `WE8EBCDIC37C` for EBCDIC platforms only

    - `WE8EBCDIC1047` for EBCDIC platforms only

  - Unicode

    - `UTF8`

    - `AL32UTF8`

    - `AL16UTF16`

      The advantage of using Instant Client Light is that it has a smaller footprint than the regular Instant Client. The shared libraries, which an application must load, are only 34 MB as opposed to the 110 MB that regular Instant Client uses. Therefore, the applications use less memory.

The language, territory, and character sets are determined by the `NLS_LANG` environment variable.

**Note:**

Ensure that you set the `NLS_LANG` environment variable to the required character set before you run Oracle Database Instant Client.
