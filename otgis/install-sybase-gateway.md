This section provides information about the hardware and software requirements and the installation procedure for Oracle Database Gateway for Sybase.

To install the gateway, follow these steps:

1.  Ensure that the system meets all of the hardware and software requirements specified in System Requirements for Oracle Database Gateway for Sybase

2.  Run the Oracle Universal Installer.

    See Step Through the Oracle Universal Installer for more information about running the Oracle Universal Installer

    Oracle Universal Installer is a menu-driven utility that guides you through the installation of the gateway by prompting you with action items. The action items and the sequence in which they appear depend on your platform.

    See Table 2-3 for a description of the installation procedure of Oracle Database Gateway for Sybase

### 2.1 System Requirements for Oracle Database Gateway for Sybase

The following topics provide information about the hardware and software requirements for the gateway:

- Hardware Requirements

- Software Requirements

Refer to the [Oracle Database Installation Guide](../install-and-upgrade.md) and to the certification matrix on My Oracle Support for the most up-to-date list of certified hardware platforms and operating system version requirements to operate the gateway for your system. The My Oracle Support Web site can be found at:

<https://support.oracle.com>

#### 2.1.1 Hardware Requirements

Table 2-1 lists the minimum hardware requirements for Oracle Database Gateway for Sybase.

Table 2-1 Hardware Requirements for Oracle Database Gateway for Sybase

| Hardware Items       | Required for IBM AIX on POWER Systems (64-Bit) | Required for Linux x86 64 bit | Required for Oracle Solaris on SPARC (64-Bit)  | Required for Oracle Solaris on x86-64 (64-Bit) | Required for HP-UX Itanium        |
|:---------------------|:-----------------------------------------------|:------------------------------|:-----------------------------------------------|:-----------------------------------------------|:----------------------------------|
| Temporary Disk Space | 400 MB                                         | 400 MB                        | 400 MB                                         | 400 MB                                         | 400 MB                            |
| Disk Space           | 1.5 GB                                         | 750 MB                        | 750 MB                                         | 750 MB                                         | 1.5 GB                            |
| Physical Memory\*    | 512 MB                                         | 512 MB                        | 512 MB                                         | 512 MB                                         | 512 MB                            |
| Swap Space           | 1 GB                                           | 1 GB                          | 1 GB                                           | 1 GB                                           | 1 GB                              |
| Processor            | IBM RS/6000 AIX-Based System Processor         | x86_64                        | Sun Solaris Operating System (SPARC) Processor | x86_64                                         | HP Itanium processor for hp-ux 11 |

\* The minimum swap space is 1 GB (or twice the size of RAM). On systems with 2 GB or more of RAM, the swap space can be between one and two times the size of RAM. On AIX systems with 1 GB or more of memory, do not increase the swap space more than 2 GB.

#### 2.1.2 Checking the Hardware Requirements

To ensure that the system meets the minimum requirements, follow these steps:

1.  To determine the physical RAM size, enter one of the following commands:
    | Operating System                  | Command                                        |
    |:----------------------------------|:-----------------------------------------------|
    | IBM AIX on POWER Systems (64-Bit) | `# /usr/sbin/lsattr -E -l sys0 -a realmem`     |
    | Linux x86 64 bit                  | `# grep MemTotal /proc/meminfo`                |
    | Oracle Solaris on SPARC (64-Bit)  | `# /usr/sbin/prtconf | grep "Memory size"`     |
    | Oracle Solaris on x86-64 (64-Bit) | `# /usr/sbin/prtconf | grep "Memory size"`     |
    | HP-UX Itanium                     | `# /usr/contrib/bin/machinfo | grep -i Memory` |

    If the size of the physical RAM installed in the system is less than the required size, you must install more memory before continuing.
2.  To determine the size of the configured swap space, enter one of the following commands:
    | Operating System                  | Command                          |
    |:----------------------------------|:---------------------------------|
    | IBM AIX on POWER Systems (64-Bit) | `# /usr/sbin/lsps -a`            |
    | Linux x86 64 bit                  | `# grep SwapTotal /proc/meminfo` |
    | Oracle Solaris on SPARC (64-Bit)  | `# /usr/sbin/swap -s`            |
    | Oracle Solaris on x86-64 (64-Bit) | `# /usr/sbin/swap -s`            |
    | HP-UX Itanium                     | `# /usr/sbin/swapinfo -a`        |

    If necessary, see your operating system documentation for information about how to configure additional swap space.
3.  To determine the amount of disk space available in the `/tmp `directory enter the following commands:
    | Operating System                  | Command        |
    |:----------------------------------|:---------------|
    | IBM AIX on POWER Systems (64-Bit) | `# df -k /tmp` |
    | Linux x86 64 bit                  | `# df -k /tmp` |
    | Oracle Solaris on SPARC (64-Bit)  | `# df -k /tmp` |
    | Oracle Solaris on x86-64 (64-Bit) | `# df -k /tmp` |
    | HP-UX Itanium                     | `# bdf /tmp`   |
4.  To determine the amount of disk space available on the system enter the following commands:
    | Operating System                  | Command   |
    |:----------------------------------|:----------|
    | IBM AIX on POWER Systems (64-Bit) | `# df -k` |
    | Linux x86 64 bit                  | `# df -k` |
    | Oracle Solaris on SPARC (64-Bit)  | `# df -k` |
    | Oracle Solaris on x86-64 (64-Bit) | `# df -k` |
    | HP-UX Itanium                     | `# bdf`   |

#### 2.1.3 Software Requirements

The following topics describe the minimum software requirements for Oracle Database Gateway for Sybase.

- Operating System

- Certified Configuration

##### 2.1.3.1 Operating System

Operating system versions required for Oracle Database Gateway for Sybase.

Table 2-2 lists the minimum operating system versions required for Oracle Database Gateway for Sybase. If your operating system is lower than the minimum requirements, upgrade your operating system to meet the specified levels.

Table 2-2 Operating Systems Version for Oracle Database Gateway for Sybase

| Operating System                    | Version                                                                                                                                                                                                           |
|:------------------------------------|:------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| IBM AIX on POWER Systems (64-Bit)   | AIX 5L version 5.3 TL9 or higher, AIX 6.1                                                                                                                                                                         |
| Linux x86 64 bit Red Hat            | One of the following operating system versions:<br>• Red Hat Enterprise Linux 4.0, (Update 7 or later)<br>• Red Hat Enterprise Linux 5 Update 2<br>• Red Hat Enterprise Linux 6                                   |
| Oracle Linux x86 64 bit             | One of the following operating system versions:<br>• Oracle Linux x86-64 SLES v12<br>• Oracle Linux x86-64 SLES v15<br>• Oracle Linux x86-64 Red Hat Enterprise Linux v7<br>• Oracle Linux x86-64 Oracle Linux v7 |
| Asianux Linux 64 bit                | One of the following operating system versions:<br>• Asianux Linux 2.0<br>• Asianux Linux 3.0                                                                                                                     |
| SUSE Linux Enterprise Server 64 bit | SUSE Linux Enterprise Server 10.0<br>SUSE Linux Enterprise Server 11.0                                                                                                                                            |
| Oracle Solaris on SPARC (64-Bit)    | Solaris 10, (Update 6 or later)                                                                                                                                                                                   |
| Oracle Solaris on x86-64 (64-Bit)   | • Oracle Solaris 10 U6 (5.10-2008.10)<br>• Oracle Solaris 11 11/11 X86 and higher                                                                                                                                 |
| HP-UX Itanium                       | HP-UX 11i V3 patch Bundle Sep/ 2008 (B.11.31.0809.326a) or higher                                                                                                                                                 |

##### 2.1.3.2 Certified Configuration

The gateway supports Sybase Adaptive Server. For the latest versions supported refer to the OTN Web site:

[`http://www.oracle.com/technetwork/database/gateways/index.html`](http://www.oracle.com/technetwork/database/gateways/index.html)

#### 2.1.4 Checking the Software Requirements

To ensure that the system meets the minimum requirements, follow these steps:

- To determine which version of IBM AIX on POWER Systems (64-Bit) is installed, enter the following command:

      # oslevel -r

- To determine which distribution and version of Linux x86 64 bit is installed, enter the following command:

      # cat /proc/version

- To determine which version of Oracle Solaris on SPARC (64-Bit) is installed, enter the following command:

      # uname -r

- To determine which version of Oracle Solaris on x86-64 (64-Bit) is installed, enter the following command:

      # uname -r

- To determine which version of HP-UX Itanium is installed, enter the following command:

      # uname -a

### 2.2 Step Through the Oracle Universal Installer

Use Table 2-3 as a guide to step through the Oracle Universal Installer, performing the actions described in the Response column in order to install Oracle Database Gateway for Sybase.

Table 2-3 The Oracle Universal Installer: Steps for Installing Oracle Database Gateway for Sybase

| Screen                                                   | Response                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                        |
|:---------------------------------------------------------|:----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Oracle Universal Installer: Welcome                      | Click Next.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                     |
| Oracle Universal Installer: File Locations               | The Source section of the screen is where you specify the source location that the Oracle Universal Installer must use to install the Oracle Database Gateway for Sybase. You need not edit the file specification in the Path field. The default setting for this field points to the installer file on your Oracle Database Gateway installation media.<br>The Path field in the Destination section of the File Locations screen is where you specify the destination for your installation. You need not edit the path specification in the Path field. The default setting for this field points to `ORACLE_HOME`. After you set the fields in the File Locations screen as necessary, click Next to continue. After loading the necessary information from the installation media, the Oracle Universal Installer displays the Available Products screen. |
| Oracle Universal Installer: Available Product Components | a. Select Oracle Database Gateway for Sybase 12.2.<br>b. Click Next.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            |
| Oracle Database Gateway for Sybase                       | Sybase Database Server Host Name  - Specify the host name or the IP address of the machine hosting the Sybase database server. This release supports IPv6 format.<br>Sybase Database Server Port number - Specify the port number of the Sybase database server<br>Sybase Database Name - Specify the Sybase database name<br>Click Next to continue.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           |
| Oracle Universal Installer: Summary                      | The Installation Summary screen enables you to review a tree list of options and components for this installation. Click Install to start installation.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         |
| Oracle Net Configuration Assistant: Welcome              | Click Cancel                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    |
| Oracle Net Configuration Assistant:                      | Click Yes                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       |
| Oracle Universal Installer: Configuration Tools          | Click Exit                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      |
| Exit                                                     | The final screen of the Oracle Universal Installer is the End of Installation screen. Click Exit to exit the installer.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         |
