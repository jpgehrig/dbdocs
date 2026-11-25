This chapter details the preinstallation requirements, postinstallation tasks, installation and deinstallation of Oracle Database 19c on BS2000.

- Overview of Oracle Database Installation
- Planning the Installation
- Oracle Database Preinstallation Requirements
- About Read-Only Oracle Homes in the POSIX File System
- Installing Oracle Database
- Oracle Database Postinstallation Tasks
- About Installing Multiple Oracle Databases
- About Removing Oracle Database Software

### 2.1 Overview of Oracle Database Installation

You can download Oracle Database software from Oracle Software Delivery Cloud at [`https://edelivery.oracle.com`](https://edelivery.oracle.com). The installation files are included in a Library Maintenance System (LMS) library called staging library, which is delivered in a zip file.

Download the zip file and extract it to a temporary location on a Windows or UNIX system. Then upload the staging library to the BS2000 system using File Transfer Protocol (FTP). The following sections describe the installation process for Oracle Database on the Fujitsu BS2000 Servers. The name of the staging library reflects the releases of Oracle Database or Oracle Database Patch Set, and the supported hardware architecture:

- `ora``xxxxx``.``arch``.lib`

  Where `xxxxx` is the release number and `arch` is the supported hardware architecture. For example:

  `ora19300.s390.lib`

**Note:**

`ora19300.s390.lib` is the name of the staging library for the base release of Oracle Database 19c.

### 2.2 Planning the Installation

The Oracle Database installation process consists of the following steps:

1.  Read the release notes: Refer to [Oracle Database Release Notes for Fujitsu BS2000](../dfsrn/index.md) before you start the installation.
2.  Review the licensing information: Although the installation media in the media pack contain many Oracle components, you are permitted to use only those components for which you have purchased licenses. Oracle Support Services does not provide support for components for which licenses have not been purchased.
    **See Also:**

    [Oracle Database Licensing Information User Manual](../dblic/Licensing-Information.md) for more licensing information
3.  Complete preinstallation tasks: "Oracle Database Preinstallation Requirements" describes preinstallation tasks that you must complete before installing the product.
4.  Install the software: "Installing Oracle Database" describes how to use the installation procedure for BS2000 to install Oracle Database 19c.
5.  Complete postinstallation tasks: "Oracle Database Postinstallation Tasks" describes recommended and required postinstallation tasks.
6.  Multiple software installations: "About Installing Multiple Oracle Databases" provides information about multiple installations of Oracle software.
7.  Remove Oracle Database software: "About Removing Oracle Database Software" describes how to remove Oracle Database software from your system.

### 2.3 Oracle Database Preinstallation Requirements

You must complete the following tasks before you install Oracle Database 19c for Fujitsu BS2000:

- Checking Hardware Requirements
- Checking Software Requirements
- About Checking Required Subsystems
- Checking Network Setup
- Creating Required Operating System Users and Groups
- Required Directories in POSIX
- Identifying or Creating Oracle Base Directory in POSIX

#### 2.3.1 Checking Hardware Requirements

The system must meet the following hardware requirements:

- Fujitsu BS2000 Server Lines

- Memory Requirements

- Disk Space Requirements

- Display Requirements

##### 2.3.1.1 Fujitsu BS2000 Server Lines

Oracle Database 19c for Fujitsu BS2000 is based on the /390 instruction set and supports the Fujitsu BS2000 SE Servers.

This release runs on all Fujitsu BS2000 processors, in particular on the /390-based system units of SE servers. It runs in the /390 compatibility mode on processors that are based on Intel x86 architecture. This applies for the x86-based server units of the SE servers (SU x86).

##### 2.3.1.2 Memory Requirements

Oracle Database requires at least 2 GB main memory.

The address space limit for the installation user ID should be 512 MB or higher. For the DBA user IDs, it should be at least 1024 MB.

- To determine the memory size, enter the following command:

      /SHOW-SYSTEM-INFORMATION INFORMATION=*MEMORY-SIZE

- To determine the user address space limit, log in to the desired user ID and enter the following command:

      /SHOW-USER-ATTRIBUTES

If the user address space is less than the required size, then ask your BS2000 system administrator to increase the address space limit by using the command:

    /MODIFY-USER-ATTRIBUTES USER-IDENTIFICATION=user-id,ADDRESS-SPACE-LIMIT={512|1024}

##### 2.3.1.3 Disk Space Requirements

Oracle Database 19c requires an installation in the BS2000 file system (DMS) and in the POSIX file system. Oracle recommends using a separate POSIX file system for the Oracle Database software installation.

**See Also:**

Fujitsu guide for BS2000 mainframes POSIX Basics for Users and System Administrators for more information about creating an additional POSIX file system.

When the POSIX administrator or BS2000 system administrator creates a new POSIX file system by using the POSIX installer, which can be started with the `START-POSIX-INSTALLATION` command, a new POSIX container file similar to a UNIX disk partition is allocated in the BS2000 file system. The POSIX file system is created in this container file. If the desired mount point, for example, `/u01`, is not available in the root system, then the mount point is created and the file system is mounted.

Oracle Database 19c software for Fujitsu BS2000 requires the following disk space:

- BS2000 file system:

  | Item                   | Free Disk Space     |
  |:-----------------------|:--------------------|
  | Software               | 1.300.000 PAM pages |
  | Staging library        | 1.300.000 PAM pages |
  | Recommended (in total) | 3.000.000 PAM pages |

- POSIX file system:

  | Requirement | Free Disk Space |
  |:------------|:----------------|
  | Minimum     | 4 GB            |
  | Recommended | 7 GB            |

**Note:**

The diagnostic data of the Automatic Diagnostic Repository (ADR) reside in the POSIX file system. The disk space required for the ADR depends on the number of Oracle database instances and the amount of diagnostic data. Therefore, you may need significantly more disk space in the POSIX file system than recommended.

The extracted files occupy about 1.300.000 PAM pages in the BS2000 file system. The files installed in the POSIX file system will occupy about 770 MB.

The staging library does not have to reside in your installation user ID.

##### 2.3.1.4 Display Requirements

Oracle Database supports 9750 compatible terminals. In addition, Oracle Database supports X-terminals in the POSIX environment when you log in to POSIX using `rlogin` or `ssh`.

The minimum resolution for Java based tools with a graphical user interface (GUI) shipped with Oracle Database 19c is 1024 x 768 or higher.

#### 2.3.2 Checking Software Requirements

Before installing Oracle Database, Oracle recommends that you check if your system meets the following software requirements:

- Operating System and Communication System Requirements

- POSIX Parameters

- Package Requirements

- Additional BS2000 Software Components

- Compiler and CRTE Requirements for Oracle Database Applications

- Additional Software Requirements

##### 2.3.2.1 Operating System and Communication System Requirements

Oracle Database 19c requires the following operating system and communication system versions or higher:

- BS2000 OSD/BC V10.0, BS2000 OSD/BC V11.0, and higher.

- openNet Server V3.6

  This includes BCAM V23.0 and Sockets V2.7.

- At least the correction package 1/2020 must be installed.

Oracle recommends that you regularly install the most current correction packages for your BS2000 system.

You can check the version of your BS2000 system with the following command:

`/SHOW-SYSTEM-INFORMATION INFORMATION=*BS2000-ID`

**Note:**

- The correction level of the POSIX subsystem must be A45 or higher. You can check the POSIX correction level with the following command:
      /EXECUTE-POSIX-CMD CMD='uname -v'
- You can check the version of your openNet Server software by checking the version of the software component BCAM with the following command:
      /SHOW-INSTALLATION-PATH INSTALLATION-UNIT=BCAM,LOGICAL-IDENTIFIER=*NONE
- You can also ask your BS2000 system administrator to check the BCAM version with the command:
      /BCSHOW SHOW=BCAM

##### 2.3.2.2 POSIX Parameters

Check the following POSIX parameters for the recommended values for Oracle Database 19c:

| Parameter Name | Description                          | Recommended Value |
|:---------------|:-------------------------------------|:------------------|
| `HDSTNI`       | Number of hard disk server tasks     | 4                 |
| `NPBUF`        | Number of physical I/O buffers       | 20                |
| `NPROC`        | Maximum number of processes          | 1000              |
| `NBUF`         | Number of I/O buffers                | 200               |
| `MAXUP`        | Maximum number of processes per user | 300               |
| `NOTTY`        | Maximum number of ttys               | 512               |
| `NOPTY`        | Maximum number of ptys               | 512               |
| `NOSTTY`       | Maximum number of sttys              | 1024              |
| `DBLSTATE`     | Initial state of POSIX loader        | 1                 |
| `DBLPOOL`      | Size of pool in MB for POSIX loader  | 30                |

The POSIX administrator or the BS2000 system administrator can check the values in the file `$TSOS.SYSSSI.POSIX-BC.``version`, for example, version = 100\|110. The values can also be checked by using the `usp` POSIX command :

    # usp -s nproc

The POSIX administrator or the BS2000 administrator can update the value with the following command:

    # usp -P parameter -v value

**Note:**

- If you edit the parameters in the `$TSOS.SYSSSI.POSIX-BC.``version` file, then you must restart the POSIX subsystem.

- The parameter values depend on the overall load of the BS2000 system and must be adjusted to this load. The values listed previously are minimal recommendations.

- Irrespective of the installed software component, that is, a client or a server, Oracle Database requires a running POSIX subsystem.

##### 2.3.2.3 Package Requirements

Oracle Database 19c requires the following POSIX packages with the specified versions or higher:

- POSIX-SH V10.0
- JENV V8.1 or JENV V9.0
- APACHE V2.4A
- PERL V52.4A
- BCAM V23.0

Use the BS2000 command, `SHOW-INSTALLATION-PATH` to check the correction level of the APACHE and Perl products. For example:

`/SHOW-INSTALLATION-PATH INSTALLATION-UNIT=APACHE,LOGICAL-IDENTIFIER=*NONE`

Use the following POSIX command to check the installed packages:

    $ pkginfo package-name

**Note:**

- Ensure that all the specified packages are installed before installing Oracle Database.
- If you don't have the required APACHE and PERL releases, please request a correction delivery from the Fujitsu software distribution center or contact Fujitsu support.

##### 2.3.2.4 Additional BS2000 Software Components

Oracle Database 19c requires the following additional software with the specified versions or higher:

- CRTE-BASYS V10.0B04 or CRTE-BASYS V11.0B04
- SDF V4.7
- SDF-P V2.5
- SDF-A V4.1
- EDT V17.0D
- LMS V3.5B
- openSM2 V19.0
- PTHREADS V1.4

**Note:**

- Ensure that the correction package 1/2020 or higher is installed.
- If you don't have the required release of CRTE-BASYS, then please request a correction delivery from the Fujitsu software distribution center or contact Fujitsu support.
- The subsystem `CRTEBASY` must be loaded.
- SDF-A is optional. SDF-A is only required to update the SDF user syntax file for Oracle. If SDF-A is not available, then the SDF user syntax file update for Oracle is skipped. If you do not update the SDF syntax file for Oracle, then you cannot start Oracle Database utilities with BS2000 SDF commands in UNIX-style.
- The software component `PTHREADS` is required by the replay client utility, `wrc`.

##### 2.3.2.5 Compiler and CRTE Requirements for Oracle Database Applications

If high-level languages, such as C or COBOL, are used to interface with the Oracle Database, then the following versions or higher are supported:

- COBOL85 V2.3

- COBOL2000 V1.5

- CPP V3.2

- CRTE V10.0B, V11.0B, and higher

##### 2.3.2.6 Additional Software Requirements

openUTM V6.5 or higher is required if you want to use Oracle Database in configurations with the transaction monitor openUTM.

#### 2.3.3 About Checking Required Subsystems

For a proper behavior, Oracle Database requires running subsytems. It is mandatory to create the following subsytems:

- POSIX

- SOC6

- PRNGD

- CRTEBASY

Use the following BS2000 command to check the state of the subsystems:

    SHOW-SUBSYSTEM-STATUS

For example:

    /SHOW-SUBSYSTEM-STATUS POSIX

#### 2.3.4 Checking Network Setup

Typically, the computer on which you want to install Oracle Database is connected to the network as a member of a network domain. Besides the BCAM host name, the host must have a fully qualified name (`hostname.domain`) that can be resolved by a DNS. You must perform the following important checks on a BS2000 computer:

- About Checking BCAM Timer

- About Checking LWRESD

- About Checking Loopback Address

- About Checking the Configuration Files in the POSIX File System

##### 2.3.4.1 About Checking BCAM Timer

Oracle recommends to check the BCAM connection and letter timer. Your BS2000 system administrator can display the timer values with the following command:

`/SHOW-BCAM-TIMER[TIMER=*STD]`

The value for the connection timer, also called `CONN` in the output of the STD section must be set to a minimum of 600 seconds if you use an Oracle database server. The value for the letter timer, also known as `LETT` in the STD section must be set to a large value. The value `0` in the output indicates an infinite letter time.

##### 2.3.4.2 About Checking LWRESD

Oracle recommends to use the Light Weight Resolver (LWRESD) for host name resolution operations. You require BS2000 system administrator privilege for checking and administering LWRESD. Ask your BS2000 system administrator to check if LWRESD is running, by using the following command:

`/SHOW-LWRESD-PARAMETERS`

For example, the following output shows the parameter file in use:

`RESOLV-FILE : :PVS1:$TSOS.SYSDAT.LWRESD.012.RESOLV.CONF`

This parameter file must contain valid name server IP-addresses and a domain or a search list of domain names.

##### 2.3.4.3 About Checking Loopback Address

Check if the `$TSOS.SYSDAT.BCAM.ETC.HOSTS` file contains an entry for the loopback address. For example:

`127.0.0.1 localhost loopback # local address`

##### 2.3.4.4 About Checking the Configuration Files in the POSIX File System

Check the network configuration files, `/etc/hosts `and `/etc/resolv.conf`. These files must be identical to the corresponding files in the BS2000 administrator user ID TSOS. If the files are not identical, then consult your BS2000 system administrator to synchronize the files.

#### 2.3.5 Creating Required Operating System Users and Groups

If you are installing Oracle software on your computer for the first time, then you may have to create several BS2000 user IDs, POSIX users, and groups. The BS2000 user ID for the Oracle Database 19c software is called the installation user ID. The user ID where an Oracle database is stored is called the Oracle Database Administration (DBA) user ID.

The name of the POSIX groups can be:

- `oracle`
- `dba`

On BS2000, you can use only one group for both Oracle Database installation and administration. You must assign the same group to both POSIX users, that is, the installation user and the DBA user. This is because programs running in the BS2000 program environment, such as, Oracle background and server tasks, can only be member of the primary group defined in the POSIX user attributes.

This section includes the following topics:

- About Creating the BS2000 Installation User ID
- About Creating the POSIX Group
- About Initializing the POSIX User
- About Creating Users and Groups for Oracle Databases

##### 2.3.5.1 About Creating the BS2000 Installation User ID

The BS2000 system administrator must create an user ID under which you want the Oracle Database 19c software to reside. This user ID is called the Oracle installation user ID or Oracle software owner. Throughout this guide, `ORACINST` is used as a proxy name for the real installation user ID. This user ID does not require any special BS2000 privileges:

- You must not use the BS2000 system administrator user ID TSOS as an Oracle Database installation user ID.

- The user address space limit must be set to at least 512 MB.

- During installation, all files are created with the following file attributes:

  `USER-ACC=ALL-USERS,ACCESS=READ`

- You do not need to define write access for any file after installation.

When the BS2000 system administrator creates the installation user ID with the following command, the corresponding POSIX user is also created:

    /ADD-USER ORACINST,…

The POSIX user attributes, namely, user number, group number, login directory and program, are assigned default values.

##### 2.3.5.2 About Creating the POSIX Group

For installation under POSIX, the POSIX administrator or the BS2000 system administrator must create groups in POSIX. Oracle recommends to use the group, `oracle` for the Oracle software owner, and Oracle database administrator. However, if you want to use the `dba` group for the Oracle database administrator, then you must use this group for the Oracle software owner too.

- If this is not the first Oracle Database installation under POSIX, then you can determine the group name by using the following POSIX command:

  `$ more /var/opt/oracle/oraInst.loc`

  If the `oraInst.loc` file exists, then the output of this command is similar to the following:

      inventory_loc=/u01/app/oraInventory
      inst_group=oracle

  The `inst_group` parameter shows the group name of your former Oracle Database installation. In the above example, it is `oracle`.

- To determine if this group is defined with a unique group ID, enter the following command:

  `$ grep 'oracle' /etc/group`

  If the output shows the group name and the group ID is greater than 100, then the group exists.

  If the group ID is 100, then you must change the ID to a distinct value greater than 100, for example, 104.

  If the group cannot be found in `/etc/group`, then ask your POSIX administrator or BS2000 system administrator to add the group name and a unique group number to the `/etc/group` file. The administrator must use a text editor, such as `edt` or `vi` to add a new line with the following specifications:

  `groupname``::``groupnumber``:``user-id``[,``user-id``,...]`

  The following example shows a line in the `/etc/group` file for the `oracle` group:

  `oracle::104:ORACINST,ORACDBA`

  Add further installation user IDs and all DBA user IDs to the line with the Oracle group.

##### 2.3.5.3 About Initializing the POSIX User

Before using the installation user ID as a POSIX user, the POSIX administrator or the BS2000 system administrator must initialize the POSIX user with the following command:

`/ADD-POSIX-USER USER-NAME=``installation-user-id`,`USER-NUMBER=``nnn``,GROUP-NUMBER=``oracle-group-number``,HOME-DIRECTORY=``path``[,RLOGIN-ACCOUNT=``account``]`

Consider the following requirements:

- The `USER-NAME` is the installation user ID.

- The `USER-NUMBER` must be unique and greater than 100.

- The `GROUP-NUMBER` must be the number of the Oracle installation group and greater than 100.

- The `HOME-DIRECTORY` must be a valid path. Do not use a path which resides in the `root` or `var` file system. Oracle strictly recommends to create a separate file system for the POSIX users. An example for a valid `HOME-DIRECTORY` is `/home/oracinst `where `/home` is the mount point of a POSIX file system.

- The `RLOGIN-ACCOUNT` can be specified if you allow the remote access by using `rlogin` or `ssh`.

##### 2.3.5.4 About Creating Users and Groups for Oracle Databases

An Oracle database in BS2000 resides in separate BS2000 user IDs. This user ID is called the DBA user ID and is different from the Oracle Database installation user ID. The BS2000 system administrator must ensure that the DBA user ID has the following attributes and privileges:

- Set the user’s address space limit to at least the following value:
      ADDRESS-SPACE-LIMIT=1024

- Set the following parameters for `ACCOUNT-ATTRIBUTES`:

      MAX-ALLOWED-CATEGORY=TP
      NO-CPU-LIMIT=YES
      START-IMMEDIATE=YES

  **Note:**

  You must not use the BS2000 system administrator user ID `TSOS` as an Oracle database DBA user ID under any circumstances.

Oracle recommends that the BS2000 system administrator defines a separate job class for the background and server tasks.

This job class must have the following characteristics:

    TP-ALLOWED=YES
    NO-CPU-LIMIT=YES
    JOB-TYPE=BATCH
    START=IMMEDIATELY

The POSIX user for the DBA user ID must be initialized with a unique user number and group number. The group number must be the same as used for the Oracle Database software owner.

If you create a new DBA user ID for a new Oracle database, then you must also initialize the POSIX user in the same way as described in "About Initializing the POSIX User." If you want to upgrade an existing Oracle database, then you must check if the POSIX user is initialized for the DBA user ID using the following BS2000 command:

`/SHOW-POSIX-USER-ATTRIBUTES`

If the output shows default values and the directory is `/home/gast`, then initialize the POSIX user using the following BS2000 command:

`/ADD-POSIX-USER USER-NAME=dba-user-id,USER-NUMBER=``nnn``,GROUP-NUMBER=oracle-group-number,HOME-DIRECTORY=path[,RLOGIN-ACCOUNT=account]`

You can modify the POSIX user attributes of an initialized POSIX user using the following BS2000 command:

`/MODIFY-POSIX-USER-ATTRIBUTES USER-ID=dba-user-id,USER-NUMBER=``nnn``,GROUP-NUMBER=oracle-group-number,DIRECTORY=path`

Your POSIX administrator or BS2000 system administrator must add the new DBA user ID to the group of the Oracle Database software owner in the `/etc/group` file.

The following example shows the entries for the `oracle` and `dba` groups in the `etc/group` file:

    oracle::504:ORAINST,ORADATA

**Note:**

- Ensure that the home directory does not reside in the `root` or `var` file system.

- The `USER-NUMBER` must be unique and greater than 100.

- The `GROUP-NUMBER` must be the same as the Oracle software owner.

#### 2.3.6 Required Directories in POSIX

The following sections describe the directories that you must identify or create in the POSIX file system for Oracle Database:

- About Oracle Base Directory

- About Oracle Inventory Directory

- About Oracle Home Directory

##### 2.3.6.1 About Oracle Base Directory

The Oracle base directory is a top-level directory for Oracle software installations. Oracle recommends to use only one Oracle base directory for all software installations with a path similar to the following:

/`mount_point`/`app/``oracbase`

In this example:

- `mount_point `is the mount point directory for the file system that contains the Oracle software. The examples in this guide use `/u01` for the mount point directory.

- `oracbase` is used as an example for a significant subdirectory name to show that this is the Oracle base for the software installations.

- If you want to use different Oracle base directories, then you can use the operating system user name of the Oracle software owner as the last subdirectory name.

The components` /mount_point/app` represent the operating system part of the path. Before you install Oracle Database 19c, you must create the operating system part of the path.

**Note:**

- The installation user ID and the installation group must have read, write, and execute permissions to the subdirectory `app`.

- During Oracle Database software installation, you are prompted for a valid Oracle base directory. You can accept the default value or enter a new path as specified above. The installation procedure creates the Oracle base directory as a subdirectory of the given operating system path.

Although multiple Oracle installations require separate installation user IDs in BS2000 and separate Oracle home directories, you can always use the same Oracle base directory. For example:

`/u01/app/oracbase`

**See Also:**

"Expanding a File System for the Oracle Base Directory" for more information about the POSIX file system

##### 2.3.6.2 About Oracle Inventory Directory

The Oracle Inventory directory (`oraInventory`) stores the inventory of all Oracle software installed on the system. It is required and shared by all Oracle software installations on a single computer. If you have an existing Oracle Inventory path, then the Oracle Database installation procedure uses that Oracle Inventory.

The Oracle Database installation procedure derives the path for the Oracle Inventory directory from the `/var/opt/oracle/oraInst.loc` file. If this file does not exist, then it derives the inventory path from `ORACLE_BASE` and creates the Oracle Inventory directory in the following path:

`ORACLE_BASE/../oraInventory`

For example, if `ORACLE_BASE` is set to `/u01/app/oracbase`, then the Oracle Inventory directory is created in the `/u01/app/oraInventory` path.

The Oracle Database installation procedure creates the Oracle subdirectories and sets the correct owner, group, and permissions for it. The operating system part of the path, for example, `/u01/app` must exist and you must have read, write, and execute permissions in the `app` directory.

**Note:**

- All Oracle software installations rely on the Oracle Inventory directory. Ensure that you back it up regularly.

- Do not delete this directory unless you have completely removed all Oracle software from the system.

- By default, the Oracle Inventory directory is not installed under the Oracle base directory. This is because all Oracle software installations share a common Oracle Inventory, so there is only one Oracle Inventory for all software owners.

##### 2.3.6.3 About Oracle Home Directory

The Oracle home directory is the directory where you install the software for a particular Oracle product. When you run the Oracle installation procedure, it prompts you to specify the path of this directory. You can accept the recommended path or enter a new path. The directory that you specify must be a subdirectory of the Oracle base directory. Oracle recommends that you specify a path similar to the following for the Oracle home directory:

`oracle_base_path``/product/19.3.0/dbhome_1`

The Oracle installation procedure creates the directory path that you specify. It also sets the correct owner, group, and permissions. You do not have to create the subdirectories manually.

**Note:**

During the installation, you must not specify an existing directory that has predefined permissions applied to it as the Oracle home directory. If you do, then you may experience installation failure due to file and group ownership permission errors.

#### 2.3.7 Identifying or Creating Oracle Base Directory in POSIX

Before you start the installation, you must either identify the operating system part of an existing Oracle base directory or if required, create one. This section contains information about the following topics:

- About Identifying an Existing Oracle Base Directory in POSIX

- Expanding a File System for the Oracle Base Directory

- Creating a File System for the Oracle Base Directory

**Note:**

You can create an Oracle base directory, even if other Oracle base directories exist on the system.

##### 2.3.7.1 About Identifying an Existing Oracle Base Directory in POSIX

You can identify the existing Oracle base directories as follows:

- Identifying an existing Oracle Inventory directory.

  Search for the string `'inventory_loc'` in the file `/var/opt/oracle/oraInst.loc`:

  `$ grep 'inventory_loc' /var/opt/oracle/oraInst.loc`

  If` oraInst.loc` exists, then the output is similar to the following:

  `inventory_loc=/u01/app/oraInventory`

  The Oracle Base directory resides on the same level in the directory tree as the Oracle Inventory directory.

<!-- -->

- Deriving an Oracle base directory from an existing Oracle home directory.

  Enter the following command to display the contents of the `/var/opt/oracle/oratab` file:

  `$ more /var/opt/oracle/oratab`

  If the `oratab` file exists, then it may contain lines similar to the following:
      *:/u01/app/orac1020/product/10g:N
      *:/u01/app/orac1120/product/dbhome:N

  The directory paths specified on each line identify Oracle home directories. In the preceding examples, Oracle base directories contain the user name of the Oracle software owner, `/u01/app/orac1020` and `/u01/app/orac1120` respectively. Oracle recommends to use a single base directory for all Oracle Database installations. For example:

  `/u01/app/oracbase`

Ensure that the Oracle base directory:

- Is not on the same file system as the operating system (`root `or `var`).

- Has sufficient free disk space.

To determine the free disk space on the file system where the Oracle base directory is located, enter the following command:

`$ df -k` `oracle_base_path`

**Note:**

The installation procedure looks for an Oracle base directory and prompts you to accept the suggested path or to enter a new path.

##### 2.3.7.2 Expanding a File System for the Oracle Base Directory

If you want to install Oracle Database into an existing file system with existing Oracle software installations, but the POSIX file system has insufficient space, then the POSIX administrator or the BS2000 system administrator can expand the file system with the Oracle base directory using the POSIX installer. Complete the following steps to expand the file system using the POSIX installer:

1.  Start the POSIX Installer using the following command:
    `/START-POSIX-INSTALLATION`
2.  Choose Administrate POSIX filesystems.
3.  Mark the desired file system and choose expand.
4.  Enter the number of PAM pages by which the file system should be expanded.

##### 2.3.7.3 Creating a File System for the Oracle Base Directory

If you want the Oracle base directory to reside in a new POSIX file system, then the POSIX administrator or the BS2000 system administrator must create a POSIX file system using the POSIX installer. Complete the following steps to create a POSIX file system using the POSIX installer:

1.  Start the POSIX installer using the following command:
    `/START-POSIX-INSTALLATION`
2.  Choose Administrate POSIX filesystems and then, choose append.
3.  Enter the BS2000 file name for the container of the file system.
4.  Enter the number of PAM pages of the container.

The POSIX installer allocates a new POSIX container file in the BS2000 file system and creates the POSIX file system inside this container. The POSIX installer also prompts for a mount point for the new file system. If the mount point does not exist, then it is created in the root system and the new file system is mounted. By default, the owner of the new file system is `SYSROOT`. The administrator must at least create the operating system part of the Oracle base directory and specify the correct owner, group, and permissions for it with the following specifications:

    # /mkdir -p /mount_point/app/
    # chown oracle_sw_owner:oracle_installation_group /mount_point/app/
    # chmod 775 /mount_point/app/

For example:

    # mkdir -p /u01/app/
    # chown oracinst:oracle /u01/app/
    # chmod 775 /u01/app/

### 2.4 About Read-Only Oracle Homes in the POSIX File System

Starting with Oracle Database 19c Release, you can install Oracle Database in a read-only Oracle Home in the POSIX file system.

Oracle Database installation in the BS2000 file system is a read-only installation by default. However, Oracle Database installation in the POSIX file system is a read/write installation by default.

Understand how read-only Oracle homes work before you choose to install read-only Oracle homes in the POSIX file system.

- Understanding Read-Only Oracle Homes
- About Installing a Read-Only Oracle Home in the POSIX File System
- Determining if an Oracle Home is Read-Only
- File Path and Directory Changes in Read-Only Oracle Homes

#### 2.4.1 Understanding Read-Only Oracle Homes

Learn about read-only Oracle home concepts like Oracle base home, Oracle base config, and orabasetab.

- About Read-Only Oracle Homes
- About Oracle Base Homes
- About Oracle Base Config
- About orabasetab

##### 2.4.1.1 About Read-Only Oracle Homes

In a read-only Oracle home, all the configuration data and log files reside outside of the read-only Oracle home.

This feature allows you to use the read-only Oracle home as a software image that can be distributed across multiple servers. In this case the installation user ID must be the same on the concerned servers.

**Note:**

An Oracle database continues to write the audit files to` $ORACLE_HOME/rdbms/audit` directory until you change the destination directory specified by the `AUDIT_FILE_DEST` initialization parameter.

Apart from the traditional ORACLE_BASE and ORACLE_HOME directories, the following directories contain files that used to be in ORACLE_HOME:

- ORACLE_BASE_HOME
- ORACLE_BASE_CONFIG

##### Benefits of a Read-Only Oracle Home

- Enables seamless patching and updating of Oracle databases without extended downtime.
- Simplifies patching and mass rollout as only one image needs to be updated to distribute a patch to many servers.
- Simplifies provisioning by implementing separation of installation and configuration.

##### 2.4.1.2 About Oracle Base Homes

Both, in a read-only ORACLE_HOME and read/write ORACLE_HOME, the user-specific files, instance-specific files, and log files reside in a location known as the ORACLE_BASE_HOME.

In a read/write ORACLE_HOME, the ORACLE_BASE_HOME path is the same as the ORACLE_HOME directory. However, in a read-only ORACLE_HOME, the ORACLE_BASE_HOME directory is not co-located with ORACLE_HOME but is located at `ORACLE_BASE/homes/HOME_NAME`.

Where, HOME_NAME is the internal name for ORACLE_HOME.

For example, the networking directories `network/admin`, `network/trace`, and `network/log` are located in the ORACLE_BASE_HOME directory. In a read/write ORACLE_HOME the networking directories appear to be in ORACLE_HOME because ORACLE_BASE_HOME is co-located with ORACLE_HOME, whereas in a read-only ORACLE_HOME the networking directories are located in `ORACLE_BASE/homes/HOME_NAME`.

To print the ORACLE_BASE_HOME path, run the `orabasehome` command from the `$ORACLE_HOME/bin` directory:

    $ ORACLE_HOME=/u01/app/oracbase/product/19.3.0/dbhome_1
    $ export ORACLE_HOME
    $ cd $ORACLE_HOME/bin
    $ ./orabasehome

For example:

    $ ./orabasehome
    /u01/app/oracbase/homes/OraDB19Home1

Where, `/u01/app/oracbase` is ORACLE_BASE and` OraDB19Home1` is HOME_NAME.

##### 2.4.1.3 About Oracle Base Config

Both, in a read-only ORACLE_HOME and read/write ORACLE_HOME, the configuration files reside in a location known as ORACLE_BASE_CONFIG.

In a read/write ORACLE_HOME, the ORACLE_BASE_CONFIG path is the same as the ORACLE_HOME path because it is located at \$ORACLE_HOME. However, in a read-only ORACLE_HOME, the ORACLE_BASE_CONFIG path is the same as ORACLE_BASE.

`ORACLE_BASE_CONFIG/dbs` contains the configuration files for ORACLE_HOME. Each file in the `dbs` directory contains \$ORACLE_SID in the path or filename so that the directory can be shared by many different ORACLE_SIDs.

To print the ORACLE_BASE_CONFIG path, run the `orabaseconfig` command from the `$ORACLE_HOME/bin` directory:

    $ ORACLE_HOME /u01/app/oracbase/product/19.3.0/dbhome_1
    $ export ORACLE_HOME
    $ cd $ORACLE_HOME/bin
    $ ./orabaseconfig

For example:

    $ ./orabaseconfig
    /u01/app/oracbase

Where, `/u01/app/oracbase` is ORACLE_BASE.

##### 2.4.1.4 About orabasetab

The `orabasetab` file is used to define fundamental directories based on \$ORACLE_HOME: ORACLE_BASE, ORACLE_BASE_HOME and ORACLE_BASE_CONFIG.

The `orabasetab` file resides in` ORACLE_HOME/install/orabasetab` and can be used to determine if an ORACLE_HOME is read-only or read/write. It also defines the ORACLE_BASE and the HOME_NAME of the Oracle home. HOME_NAME is the internal name for ORACLE_HOME.

The last line in the `orabasetab` file, which starts with \$ORACLE_HOME, defines the directories for \$ORACLE_HOME. The last line consists of four fields, each separated by a colon delimiter (:).

1.  The first field matches the current \$ORACLE_HOME.
2.  The second field defines the ORACLE_BASE for the current ORACLE_HOME.
3.  The third field defines the HOME_NAME which is used in constructing the ORACLE_BASE_HOME path in a read-only ORACLE_HOME.
4.  The fourth field displays `N` in a read/write ORACLE_HOME and `Y` in a read-only ORACLE_HOME.

In a read-only ORACLE_HOME, the ORACLE_BASE_HOME path is `ORACLE_BASE/homes/HOME_NAME` and ORACLE_BASE_CONFIG is the same as ORACLE_BASE.

In a read/write ORACLE_HOME, ORACLE_HOME, ORACLE_BASE_HOME and ORACLE_BASE_CONFIG are all the same.

##### Viewing an orabasetab File

1.  Log in as the Oracle installation owner user account.

2.  Go to the `$ORACLE_HOME/install` directory.

        $ cd /u01/app/oracbase/product/19.3.0/dbhome_1/install

3.  View the contents of the `orabasetab` file.

        $ cat orabasetab
        #orabasetab file is used to track Oracle Home associated with Oracle Base
        /u01/app/oracbase/product/19.3.0/dbhome_1:/u01/app/oracbase:OraDB19Home1:Y:

In this example, a `Y` in the fourth field at the end of the line indicates you have a read-only Oracle home.

#### 2.4.2 About Installing a Read-Only Oracle Home in the POSIX File System

Starting with Oracle Database 19c, the new procedure parameter `RO-ORACLE-HOME` specifies the installation type in the POSIX file system.

Set the `RO-ORACLE-HOME` parameter to `Y` if you want a read-only ORACLE_HOME installation. Set the `RO-ORACLE-HOME` parameter to `N` if you want a read/write ORACLE_HOME installation, which is the default installation type.

If you run the installation in the DIALOG mode and you have specified an ORACLE_HOME directory for installing Oracle Database in the POSIX file system, but have not specified the type of your ORACLE_HOME directory, then you will be prompted to choose the ORACLE_HOME type in the POSIX file system.

If you run the installation in the BATCH mode and you have specified an ORACLE_HOME directory for the installation in the POSIX file system, then you must specify the type of your ORACLE_HOME by setting the procedure parameter `RO-ORACLE-HOME`. If you have not set the parameter then the default value `N` is assumed and Oracle Database will be installed in a read/write ORACLE_HOME directory.

#### 2.4.3 Determining if an Oracle Home is Read-Only

Run the `orabasehome` command to determine if your Oracle home is a read/write or read-only Oracle home.

If the output of the `orabasehome` command is the same as \$ORACLE_HOME, then your Oracle home is in read/write mode. If the output displays the path ORACLE_BASE/homes/HOME_NAME, then your Oracle home is in read-only mode.

1.  Set the ORACLE_HOME environment variable:
        $ ORACLE_HOME=/u01/app/oracbase/product/19.3.0/dbhome_1
        $ export ORACLE_HOME
2.  Go to the bin directory and run the `orabasehome` command:
        $ cd $ORACLE_HOME/bin
        $ ./orabasehome
        /u01/app/oracbase/homes/OraDB19Home1

    In this example, the Oracle home is in read-only mode.

#### 2.4.4 File Path and Directory Changes in Read-Only Oracle Homes

Examples of hierarchical file mappings in a read-only Oracle home as compared to a read/write Oracle home.

This example shows an Oracle Database installation, for the user `oracinst`, with the ORACLE_HOME, ORACLE_BASE, ORACLE_BASE_HOME, and ORACLE_BASE_CONFIG locations. The database files still reside in the BS2000 file system.

This example also shows the changes in the Oracle Database software defined paths of configuration files, log files, and other directories in a read-only Oracle home when compared to a read/write Oracle home.

Table 2-1 Read-Only Oracle Home and Read/Write Oracle Home File Path Examples

| Directory          | Read-Only Oracle Home File Path                                                    | Read/Write Oracle Home File Path                                                   |
|:-------------------|:-----------------------------------------------------------------------------------|:-----------------------------------------------------------------------------------|
| ORACLE_HOME        | `/u01/app/oracbase/product/19.3.0/dbhome_1`                                        | `/u01/app/oracbase/product/19.3.0/dbhome_1`                                        |
| ORACLE_BASE        | `/u01/app/oracbase/`                                                               | `/u01/app/oracbase/`                                                               |
| ORACLE_BASE_HOME   | ORACLE_BASE/homes/HOME_NAME<br>(or)<br>`/u01/app/oracbase/homes/OraDB19Home1`      | ORACLE_HOME<br>(or)<br>`/u01/app/oracbase/product/19.3.0/dbhome_1`                 |
| ORACLE_BASE_CONFIG | ORACLE_BASE<br>(or)<br>`/u01/app/oracbase/`                                        | ORACLE_HOME<br>(or)<br>`/u01/app/oracbase/product/19.3.0/dbhome_1`                 |
| `network`          | ORACLE_BASE_HOME/network<br>(or)<br>`/u01/app/oracbase/homes/OraDB19Home1/network` | ORACLE_HOME/network<br>(or)<br>`/u01/app/oracbase/product/19.3.0/dbhome_1/network` |
| `dbs`              | ORACLE_BASE/dbs<br>(or)<br>`/u01/app/oracbase/dbs`                                 | ORACLE_HOME/dbs<br>(or)<br>`/u01/app/oracbase/product/19.3.0/dbhome_1/dbs`         |

### 2.5 Installing Oracle Database

Oracle Database 19c software is available in a zipped LMS library. Complete the following steps to install Oracle Database:

1.  Download the installation files from Oracle Software Delivery Cloud to a Windows or UNIX system that has FTP access to the BS2000 system where you want to install the software.
    [`https://edelivery.oracle.com/`](https://edelivery.oracle.com/)
2.  Unzip the zip file with a zip utility, such as WinZip, to create the staging library `ora``xxxxx``.s390.lib`.
3.  Transfer the staging library with the FTP binary into a user ID on the BS2000 system. This can either be the Oracle installation user ID or any other user ID. Before the transfer, if you are using BS2000 FTP, preallocate the file by using the FTP file command as shown in the example:
    `file ora``xxxxx``.s390.lib,fcbtype=pam,blkctrl=no,blksize=(std,2),space=1300000`

    Use the following command if you are using FTP on the platform where you had unzipped the file:

    `quote file ora``xxxxx``.s390.lib,fcbtype=pam,blkctrl=no,blksize=(std,2),space=1300000`
4.  If you have transferred the staging library to a user ID that is not equal to the Oracle installation user ID, then you must grant access to the staging library for all users. Use the following command:
    `/MODIFY-FILE-ATTRIBUTES ORA``xxxxx``.S390.LIB,USER-ACCESS=*ALL-USERS`
5.  Log in to the installation user ID.
6.  If the staging library resides in the installation user ID, then call the Oracle installation procedure as follows:
    `/CALL-PROCEDURE (ORA``xxxxx``.S390.LIB,ORAINST.PRC)`

    If you have stored the staging library in a different BS2000 user ID, then call the Oracle installation procedure as follows:

    `/CALL-PROCEDURE` (`staging_userid``.ORA``xxxxx``.S390.LIB,ORAINST.PRC),``(STAGING-UID=``staging_userid``) `

    For example:

    `/CALL-PROCEDURE ($FOO.ORA``xxxxx``.S390.LIB,ORAINST.PRC),(STAGING-UID=$FOO)`

Oracle Database installation procedure performs the following actions:

- Checks hardware and software requirements.

- Checks the available disk space for the BS2000 files and the POSIX files.

- Extracts the files from the staging library.

- Installs Oracle software in the installation user ID.

- Updates the SDF syntax files, if SDF-A is available.

- Installs Oracle Database software in the POSIX file system.

- Registers the software in the Oracle Inventory file.

The following is the complete syntax of the installation procedure:

`/CALL-PROCEDURE ([``staging_userid``.]ORA``xxxxx``.S390.LIB,ORAINST.PRC)[`,

`([CMD={INSTALL|UNINSTALL}]`

`[,INSTALLATION-TYPE={DATABASE|CLIENT}]`

`[,STAGING-UID=``{''|``staging_userid``}]`

`[,ORACLE-BASE={*PROMPT|``oracle_base_path``}]`

`[,ORACLE-HOME={*PROMPT|``oracle_home_path``}]`

`[,RO-ORACLE-HOME={*PROMPT|Y|N}]`

`[,DEBUG={Y|N}])]`

The following table lists the parameters, their corresponding values, and their description that are used during Oracle Database installation:

| Parameter           | Value                                              | Description                                                                                                                                                                           |
|:--------------------|:---------------------------------------------------|:--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `CMD`               | `INSTALL|UNINSTALL`<br>default: `INSTALL`          | Install or uninstall Oracle Database.                                                                                                                                                 |
| `INSTALLATION-TYPE` | `DATABASE|CLIENT`<br>default: `DATABASE`           | Types of installation.                                                                                                                                                                |
| `STAGING-UID`       | ' '\|user ID of staging library<br>default: `''`   | BS2000 user ID where the staging library is located.                                                                                                                                  |
| `ORACLE-BASE`       | `*PROMPT|``oracle_base_path`<br>default:` *PROMPT` | The Oracle base directory is required for installing Oracle Database 19c in the POSIX file system. The default value `*PROMPT,` indicates the prompting for an Oracle base directory. |
| `ORACLE-HOME`       | `*PROMPT|``oracle_home_path`<br>default: `*PROMPT` | The Oracle home directory is required for installing Oracle Database 19c in the POSIX file system. The default value `*PROMPT` indicates the prompting for an Oracle home directory.  |
| `RO-ORACLE-HOME`    | `*PROMPT|Y|N`<br>default:`N`                       | Installs Oracle in the POSIX file system in READ-ONLY mode.                                                                                                                           |
| `DEBUG`             | `Y|N`<br>default: `N`                              | Debug the installation procedures.                                                                                                                                                    |

Installing Oracle Database in the POSIX file system requires an `ORACLE_BASE` and `ORACLE_HOME` path. During installation you are prompted for these paths, if the installation runs in the dialog mode and if you have not specified the parameters in the procedure call. You can accept the suggested paths or enter new paths.You will also be asked if ORACLE_HOME should be installed in read-only mode or read/write mode.

The installation procedure also provides the opportunity to run the installation as a background task. In this case, you must specify the parameters `ORACLE-BASE` and `ORACLE-HOME`, otherwise the installation will be aborted if the `INSTALLATION-TYPE` is `DATABASE`. If the `INSTALLATION-TYPE` is `CLIENT` and if `ORACLE-BASE` or `ORACLE-HOME` is not specified, then the installation in the POSIX file will be skipped. If the `RO-ORACLE-HOME` parameter is not specified, then the default value `N` will be assumed. Since the installation takes about 250 CPU seconds, Oracle recommends that you set the `CPU-LIMIT` to at least 300 seconds. You can start the installation as follows:

`/ENTER-PROCEDURE (ORA``xxxxx``.S390.LIB,ORAINST.PRC),(ORACLE-BASE='/u01/app/oracbase',ORACLE-HOME='/u01/app/oracbase/product/19.0.0/dbhome_1'),LOGGING=*NO,CPU-LIMIT=300`

When you run the installation as a background task, the installation process is logged to the file `INSTALL.ORAINST.LST`.

### 2.6 Oracle Database Postinstallation Tasks

To complete the installation, the POSIX administrator or the BS2000 system administrator must run the `oracle_home_path``/root.sh `script as follows:

- In the BS2000 environment, use the following command:

      /EXECUTE-POSIX-CMD CMD='oracle_home_path/root.sh'

  For example,

      /EXECUTE-POSIX-CMD CMD='/u01/app/oracbase/product/19.3.0/dbhome_1/root.sh'

- In the POSIX environment (shell), use the following command:

      # sh oracle_home_path/root.sh

  For example:

      # sh /u01/app/oracbase/product/19.3.0/dbhome_1/root.sh

If this is the first Oracle Database installation on the BS2000 server, then the `root.sh` script completes the following actions:

- Creates the path, `/var/opt/oracle`

- Creates the file, `/var/opt/oracle/oraInst.loc`

- Creates an empty file, `/var/opt/oracle/oratab`

### 2.7 About Installing Multiple Oracle Databases

You can install multiple Oracle databases, based on different releases of Oracle software. In this case, different releases of the software must be installed under different installation user IDs and different Oracle home directories.

### 2.8 About Removing Oracle Database Software

To remove Oracle Database software from your computer, log in to the Oracle installation user ID and use the installation procedure as follows:

`/CALL-PROCEDURE INSTALL.P.ORAINST,(CMD=UNINSTALL)`

This procedure completes the following actions:

- Removes the Oracle Database software from the POSIX file system.

- Updates the Oracle inventory.

- Removes the Oracle Database software from the BS2000 file system.

**Note:**

Only the files installed by the Oracle installation procedure, namely, `ORAINST.PRC` are removed from the system. Files created by a user or by an Oracle instance are retained in the Oracle home directory and the installation user ID.
