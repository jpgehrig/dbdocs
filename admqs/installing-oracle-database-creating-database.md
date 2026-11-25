This chapter describes how to install Oracle Database software and create a single instance Oracle Database.

If you are using an earlier release of Oracle Database and want to install a later release of the Oracle Database software, then you can upgrade your existing Oracle Database and use it with the new release of the database software. See "[Upgrading a Database](managing-oracle-database-software.md)".

This chapter contains the following sections:

- Overview of Installing Oracle Database Software and Creating a Database

- Installing Oracle Database Software

- Creating and Managing a Database with DBCA

- Manually Installing the Database Sample Schemas Post-Installation

- Installation: Oracle By Example Series

**Note:**

This chapter provides an overview of how to install Oracle Database software and create a single instance Oracle Database. This chapter is not a complete installation guide for Oracle Database.

For more detailed information about installing Oracle Database software, see [Oracle Database Installation Guide](../install-and-upgrade.md) for your platform.

### 2.1 Overview of Installing Oracle Database Software and Creating a Database

To install your Oracle Database software, use Oracle Universal Installer (OUI). OUI is a graphical user interface utility that enables you to install new Oracle Database software. Online Help is available to guide you through the installation process.

During the installation process, you are given the opportunity to create a database. If you choose to do so, then OUI automatically starts Oracle Database Configuration Assistant (DBCA) to guide you through the process of creating and configuring a database.

Before you start the installation process, see the following sections for information about prerequisites and installation choices:

- Checking Oracle Database Installation Prerequisites

- Deciding on Oracle Database Installation Choices

If you do not create a database during installation, then you must run DBCA at some point after installation to create a database.

**Note:**

After you create a database, either during installation or as a standalone operation, you do not have to create another. Rather than requiring that you create multiple databases to accommodate different applications, you can separate data into different schemas within a single Oracle Database. See "[About User Accounts](administering-user-accounts-and-security.md)" for more information about schemas.

Starting with Oracle Database 12c, it is also possible to create a multitenant container database (CDB) that can support zero, one, or many user-created pluggable databases (PDBs). All Oracle databases created before Oracle Database 12c are non-CDBs. This manual describes the OUI and DBCA options for creating CDBs and PDBs, and subsequent chapters provide information on managing CDBs and PDBs.

**See Also:**

- [Oracle Multitenant Administrator's Guide](../multi/introduction-to-the-multitenant-architecture.md) for conceptual information about CDBs and PDBS

- [Oracle Multitenant Administrator's Guide](../multi/managing-a-multitenant-environment.md) for information about managing CDBs and PDBs

#### 2.1.1 Checking Oracle Database Installation Prerequisites

Before installing the software, Oracle Universal Installer (OUI) performs several automated checks to ensure that your computer fulfills the basic hardware and software requirements for an Oracle Database installation. If your computer does not meet a requirement, then an error message is displayed.

The requirements may vary depending upon the type of computer and operating system you are using, but some prerequisites include:

- There is a minimum of 1 GB of physical memory.

- Sufficient paging space is available.

- The appropriate service packs or patches for your operating system are installed.

- An appropriate file system format is being used.

**See Also:**

[Oracle Database Installation Guide](../install-and-upgrade.md) for your platform for more information about preinstallation requirements and tasks

#### 2.1.2 Deciding on Oracle Database Installation Choices

Oracle Universal Installer (OUI) guides you through an interview phase where you specify your choices for installation and database creation. The exact sequence of steps depends on your operating system. As you progress through the installation, you are presented with choices on how to configure the database.

- Install Option for Oracle Database

- Installation Class for Oracle Database

- Installation Edition for Oracle Database

- Software Installation Directories for Oracle Database

- Database File Location for Oracle Database

- Database Identifiers for Oracle Database

- About Advanced Installation for Oracle Database

##### 2.1.2.1 Install Option for Oracle Database

You can choose to create and configure a database, or to only install the database software.

You can create a preconfigured database or a custom-configured database during installation. If you choose not to create a database during installation, then you must run Database Configuration Assistant (DBCA) after installation to create a database.

**Note:**

If you choose to create and configure a database, then Oracle Universal Installer (OUI) will start DBCA at the end of the installation to configure the database.

If you choose to only install the database software using OUI, then you must manually run DBCA after the installation to create and configure the database. With this approach, more options are available for controlling database configuration.

Preconfigured databases are based on templates that Oracle provides or that you create. Each Oracle-provided template is optimized for a particular workload type. See Table 2-2 for information about the types of preconfigured databases.

If you choose to use a Desktop Class installation, then the general purpose database template is used. To create a custom database in which you configure your own database structure, see "About Advanced Installation for Oracle Database."

**Note:**

If you must create a new database, then Oracle recommends that you install a preconfigured database, which is faster and easier. You can customize the database after it has been created.

##### 2.1.2.2 Installation Class for Oracle Database

The installation classes are Desktop Class and Server Class.

- Desktop Class—This installation class is most appropriate for laptop or desktop computers. It includes a starter database and requires minimal configuration.

- Server Class—This installation class is for servers, such as you would find in a data center, or used to support enterprise-level applications. Choose this installation class if you need access to advanced configuration options.

During a Desktop Class installation, you make only basic choices. For a Server Class installation, you choose either typical installation (where you make only basic choices) or advanced installation.

During a Desktop Class or a typical installation, Oracle Database automatically installs the sample schemas.

##### 2.1.2.3 Installation Edition for Oracle Database

When you install Oracle Database during basic and advanced installations, you can choose a database edition.

For example, you can choose one of these database editions:

- Enterprise Edition—This installation type is the full-featured Oracle Database product that provides data management for enterprise-level applications. It is intended for mission-critical, high-security online transaction processing (OLTP) and data warehousing environments.

- Standard Edition 2—This installation type is designed for department or workgroup- level applications and for small and medium-sized enterprises (SMEs). It is engineered to provide core relational database management services and options. It installs an integrated set of management tools, full distribution, replication, Web features, and facilities for building business-critical applications.

##### 2.1.2.4 Software Installation Directories for Oracle Database

You must specify the directory in which the Oracle Database software is installed, or the location where the product binary files are copied from the installation media. You must choose a location that has enough disk space to contain the software and is accessible by the operating system user performing the installation.

You also specify the location of the Oracle base directory, which is used by all Oracle software products installed on the server. The first time you install Oracle software on a server, you are prompted to specify the location of the inventory directory, called `oraInventory`. This directory provides a centralized inventory of all Oracle software products installed on the server. You should use the same value for the Oracle inventory directory each time you perform an Oracle software installation on the server.

##### 2.1.2.5 Database File Location for Oracle Database

A database includes several files that store the user data, database metadata, and information required to recover from failures. As an administrator, you decide what kind of storage subsystem to use for these files.

You can select from the following options:

- File System—This default option creates database files that are managed by the file system of your operating system. You can specify the directory path where database files are to be stored. Oracle Database can create and manage the actual files.

  If you are not certain about which option to use, then select File System (the default).

- Automatic Storage Management—This option enables you to place your data files in Oracle Automatic Storage Management (Oracle ASM) disk groups. If you choose Oracle ASM, then Oracle Database automatically manages database file placement and naming. For environments with a large number of disks, this option simplifies database administration and maximizes performance. Oracle ASM performs software striping and mirroring at the file level for maximum storage flexibility, performance, and availability.

  Oracle ASM uses an Oracle ASM instance, which is distinct from the database instance, to configure and manage disk groups. A single Oracle ASM instance can provide storage for multiple databases on the same server.

  For more information, see [Oracle Automatic Storage Management Administrator's Guide](../ostmg/asm-intro.md).

**Note:**

In past releases, Oracle ASM was installed as part of the Oracle Database installation. With Oracle Database 11g Release 2 (11.2), Oracle ASM is part of an Oracle Grid Infrastructure installation.

To use Oracle ASM for storing database files, you must have installed Oracle ASM and created one or more disk groups before performing the Oracle Database installation.

##### 2.1.2.6 Database Identifiers for Oracle Database

These options include your global database name and system identifier (SID). The SID is a unique identifier that is used to distinguish this instance from other Oracle Database instances that you may create later and run concurrently on your system.

The global database name is the full name of the database that uniquely distinguishes it from any other database. The global database name is in the form `database_name.database_domain`, for example `sales.example.com`. The database name portion `sales` is a simple name you call your database. The database domain portion `example.com` specifies the database domain in which the database is located. Together, the database name and domain form the global database name.

##### 2.1.2.7 About Advanced Installation for Oracle Database

During advanced installations using the Server Class method you are prompted to make the additional choices listed in this section, and the choices for a typical installation. The installation process provides default values for every choice.

This guide describes, but does not document, these additional advanced installation choices. For more information, see [Oracle Database Installation Guide](../install-and-upgrade.md) for your platform.

- Product Languages

  You choose which language the software should use after it is installed. You can select multiple languages. The default value is English. If you choose a value other than English, it does not change the language used by the installation.

- Database Configuration Type

  You select a template to use when configuring the database. You can choose either General Purpose/Transaction Processing or Data Warehousing.

- Database Configuration Options

  You can choose how to configure the database created by the installer. You can select the memory size and management options, the character sets used to store data, the security options for database access, and whether the sample schemas should be installed.

  To complete the exercises in this guide and related course material, you must install the sample schemas. This data is also used in most examples throughout Oracle Database documentation. Oracle recommends that you install the sample schemas.

  This choice is a configuration option only during advanced installation. Sample schemas are installed by default during typical or Desktop class installations.

- Recovery Options

  During an advanced installation, you can configure backup and recovery optins for the database. If you choose this option, you must specify whether the recovery area should be stored on the local file system or in an Oracle ASM disk group.

  **Note:**

  To use Oracle ASM for recovery area storage, you must have installed Oracle ASM as part of an Oracle Grid Infrastructure installation and created one or more disk groups before performing the Oracle Database installation.

- Schema Passwords

  When you create a database, certain administrative user accounts are created automatically. You are prompted to enter the passwords for administrative accounts such as the `SYS` and `SYSTEM` accounts, which enable you to manage and administer the database. You can use the same password for each account, or specify passwords for each account individually. If you do not enter a secure password, you will receive a warning message during installation.

- Operating System Groups

  Administrative access to the database is granted by membership in certain operating system groups. You can choose the operating system group to be used for `SYSDBA` access (typically `dba`) and `SYSOPER` access (typically `oper`).

  The `SYSDBA` group identifies operating system user accounts that have database administrative privileges and can log in with `SYSDBA` access. The `SYSOPER` group is an optional group for users that should have limited database administrative privileges. See "[SYSDBA and SYSOPER System Privileges](administering-user-accounts-and-security.md)" for more information about these groups and privileges.

### 2.2 Installing Oracle Database Software

This section briefly describes the steps for a system class installation. Most steps are common to all platforms and involve running Oracle Universal Installer (OUI). Platform-specific steps are noted. For further assistance, consult the online Help or the [Oracle Database Installation Guide](../install-and-upgrade.md) for your platform.

**Note:**

The following steps describe the OUI workflow for a host computer that has no previous Oracle software installed. If your host computer has Oracle software installed, then you may see a different workflow.

#### To perform a basic installation:

1.  Log on to your computer as a member of the administrative group that is authorized to install Oracle Database software and to create and run the database.
    Refer to your operating system-specific documentation or contact your system administrator to determine whether you have the necessary privileges and permissions to install new software.
2.  Do one of the following:
    - If you are installing from distribution media, then insert the distribution media for the database into your computer.

      The Autorun feature opens the Select a Product to Install window automatically.

    - If you downloaded the installation software from the Oracle Web site, then follow the instructions on the site to run the Oracle Universal Installer. Or, see the [Oracle Database Installation Guide](../install-and-upgrade.md) for your platform.
3.  The first window that appears is the Configuration Option window. Choose the Create and configure a database single instance option. Or, you also have the option of choosing to only install the database software, but then you must create a database in an additional step after the software is installed. If you are currently using a previous version of Oracle Database, choose Upgrade an existing database. After you have chosen an option, click Next.
    The System Class window appears.
4.  Choose Server Class.
    You can choose the Server Class option to customize your installation. For example, you use this method to configure Oracle Automatic Storage Management for your database, install the Sample Schemas, or configure backup and recovery options.

    The steps for a Desktop Class installation are similar to the steps for a Server Class installation, but fewer choices are required to install the database.

    Click Next.

    The Install Type window appears.
5.  Choose Typical install and click Next.
    If you choose Advanced install, some of the installation steps are not documented in this guide. For more information about the advanced choices, see "About Advanced Installation for Oracle Database". Also see [Oracle Database Installation Guide](../install-and-upgrade.md) for your platform.
    **Note:**

    On Microsoft Windows operating systems only, the Specify Oracle Home User window appears. This window enables you to use a non-administrator, low privileged Windows User Account as the Oracle Home User. This option is recommended for database installation to ensure that Oracle services run with limited privileges. For single instance databases, you can also choose to allow the Oracle Installer to create a new Windows User Account (local user only) which will then be used as the Oracle Home User.

    If you decline this option, all the services will be installed and will run as the System user.

    See [Oracle Database Administrator’s Reference for Microsoft Windows](../ntqrf/supporting-oracle-home-user-on-windows.md) for more information about this feature.

    The Typical Installation window appears.
6.  Provide the following configuration details for the database:
    - Oracle base— The Oracle base directory helps to facilitate the organization of multiple Oracle software installations. See [Oracle Database Installation Guide](../install-and-upgrade.md) for your platform for more information about `ORACLE_BASE`.

      If you did not set the `ORACLE_BASE` environment variable before starting OUI, then the Oracle base directory is created in an `app/``username``/`directory on the first existing and writable directory from `/u01` through `/u09` for UNIX and Linux systems, or on the disk drive with the most available space for Windows systems. If `/u01` through `/u09` does not exist on the UNIX or Linux system, then the default location is `user_home_directory``/app/``username`.

      You can click Browse to find the directory you want to act as the Oracle base directory.

    - Software location—The software location is the Oracle home for your database. You must specify a new Oracle home directory for each new installation of Oracle Database software. By default, the Oracle home directory is a subdirectory of the Oracle base directory.

      You can click Browse to find the directory where you want to install the Oracle Database software.

    - Storage type—You can choose either File system or Oracle Automatic Storage Management.

    - Database file location—The database file location is the location where Oracle Database files are stored. By default, this location is `Oracle_base``/oradata`. You can click Browse to select a different location.

    - Database edition—Select either Enterprise Edition or Personal Edition (Microsoft Windows platforms only). See "Installation Edition for Oracle Database".

    - OSDBA group (Linux and UNIX platforms only)—Specify the operating system DBA group. Host computer users in this group have administrative privileges on the database. This group is typically named `dba`. Refer to [Oracle Database Installation Guide for Linux](../ladbi/index.md) or for your UNIX platform for more details.

    - Global database name—Enter the fully qualified global database name. See "Database Identifiers for Oracle Database" for more information about global database names.

    - Administrative password—Specify the initial password for administrator accounts such as the `SYS` and `SYSTEM` accounts. If the password you choose is not a secure password, a warning message will be displayed.

    - Create as Container database: Enable this option to create the database as a multitenant container database (CDB) that can support zero, one, or many user-created pluggable databases (PDBs).

      If you want Database Configuration Assistant (DBCA) to create a PDB when it creates the CDB, specify the PDB name in the Pluggable database name field.

    After you enter the required information, click Next.

    For first time installations on Linux and UNIX operating systems only, if Oracle software has not previously been installed on this server, then the Create Inventory window appears. If this is not the first installation attempt on this server, then the Perform Prerequisite Checks window appears.
7.  If the Create Inventory windows appears, specify a directory for installation files and the name of an operating system group that has write permissions for that directory.
    If this is the first time you are installing any Oracle software on this computer, then the Create Inventory Directory window appears. You must specify a local directory for the inventory, which OUI uses to keep track of all Oracle software installed on the computer. This information is used while applying patches or upgrading an existing installation, and while deinstalling Oracle software. Note that this directory is different from the Oracle home directory. The recommended value for the inventory directory is `Oracle_base``/../oraInventory`, or one level above the Oracle base directory, in the `oraInventory` subdirectory. If your Oracle base directory is `/u01/app/oracle`, then the Oracle inventory directory defaults to `/u01/app/oraInventory`.

    In this window you can also specify the operating system group that has write permissions on the inventory directory. This prevents other users from writing over the Oracle product installation files.

    After you enter a directory path and specify an operating system group, click Next to continue.

    The Perform Prerequisite Checks window appears.
8.  If any checks failed, then take corrective actions.
    OUI performs several environment checks and indicates whether the check was a success, or resulted in a warning or failure. Details of the checks are provided in the displayed window. The installation can proceed only when all checks have a status of either Succeeded or Warning. If any of the environment checks failed, then they must be resolved manually. See "Checking Oracle Database Installation Prerequisites" for more information.

    If all the prerequisite checks passed, or after you click Next, the Summary window appears.
9.  Review the installation summary, then click Install to start the installation.
    The Install Product window appears, showing the installation progress.
10. For Linux and UNIX operating systems only, you are prompted to run configuration scripts. To run root scripts automatically, select Automatically run configuration scripts. Alternatively, you can run the configuration scripts manually as the `root` user. Run the scripts and then click OK.
    When the installation is complete, the Finish window appears.
11. Make note of the information in the Finish window, then click Close to exit OUI.
    Your installation and database creation is now complete.

    You use Oracle Enterprise Manager Database Express (EM Express) to perform common database administration tasks.

    Use the URL for EM Express that is provided in the Finish window to start EM Express, specifying your database hostname instead of 'localhost.' When EM Express prompts you for your username and password, log in as a user with DBA privilege (such as SYSTEM).

    **Note:**

    By default, DBCA picks a free port from the 5500 to 5599 range to use as the EM Express port.

    If you want a particular port to be used as the EM Express port, specify that port using the `DBEXPRESS_HTTPS_PORT` operating system environment variable before starting OUI or DBCA.

    For more information on setting environment variables, see "[Configuring the Operating System Environment Variables](getting-started-with-database-administration.md)."

    **See Also:**

    - [Oracle Multitenant Administrator's Guide](../multi/introduction-to-the-multitenant-architecture.md) for conceptual information about CDBs and PDBs.

    - [Oracle Multitenant Administrator's Guide](../multi/managing-a-multitenant-environment.md) for information about managing CDBs and PDBs.

    - "[SYS and SYSTEM Users](administering-user-accounts-and-security.md)" for information about the recommended alternative to using the `SYSTEM` account for day-to-day administrative tasks.

    - "[Getting Started with Database Administration](getting-started-with-database-administration.md)" for more information about using EM Express.

### 2.3 Creating and Managing a Database with DBCA

Unless you specified that only the Oracle Database software should be installed, Oracle Universal Installer (OUI) automatically runs Database Configuration Assistant (DBCA) after software installation is complete. DBCA then creates a database using the information you provided. If you do not create a starter database and later want to create one, or to create additional databases, use DBCA.

**Note:**

With Oracle Database, you typically have a single database that hosts multiple applications. You do not need multiple databases to run different applications. Instead, you can separate the objects that support each different application into different schemas in the same database. However, there may be situations in which you want to create multiple Oracle databases on the same host computer. When you do this with DBCA, the new databases typically use the same Oracle home directory as the first database, but store database data files separately from those of the first database.

DBCA also enables you to modify a database configuration, delete a database, and more. You can perform the following DBCA tasks:

- Starting DBCA

- Creating a Database Using DBCA

- Changing the Configuration of a Database Using DBCA

- Deleting a Database Using DBCA

- Managing Templates with DBCA

- Using DBCA to Manage PDBs

Online Help is available by clicking Help. It provides information that guides you in selecting configuration options.

**Note:**

Starting with Oracle Database 19c Release Update (19.7), you can install Oracle Database Standard Edition 2 in high availability mode. Standard Edition High Availability provides cluster-based failover for single-instance Standard Edition Oracle Databases using Oracle Clusterware. For more information, see [Oracle Database Installation Guide for Linux](../ladbi/about-standard-edition-high-availability.md).

#### 2.3.1 Starting DBCA

This section describes how to start Database Configuration Assistant (DBCA).

**Note:**

If you choose to create a starter database while installing the Oracle Database software, then Oracle Universal Installer (OUI) automatically starts DBCA.

##### To start DBCA:

1.  Log on to your computer as a member of the administrative group that is authorized to install Oracle Database software and to create and run the database.
2.  Do one of the following:
    - To start DBCA on a Microsoft Windows operating system, click Start, select Programs (or All Programs), then Oracle - HOME_NAME, then Configuration and Migration Tools, and then Database Configuration Assistant.

    - To start DBCA on UNIX or Linux, or at the command-line prompt on the Windows operating system, enter the following command:

          dbca

      The `dbca` utility is typically located in the `ORACLE_HOME``/bin` directory.

#### 2.3.2 Creating a Database Using DBCA

Database Configuration Assistant (DBCA) enables you to create an Oracle database by following a step-by-step guided workflow.

##### To create a database using DBCA:

1.  Start DBCA as described in "Starting DBCA".
2.  In the Database Operation window, select Create a database and click Next to start the guided workflow for creating a database. If you then select Advanced Mode and click Next, the workflow requests your input in the following windows:

- DBCA Creation Mode Window

- DBCA Deployment Type Window

- DBCA Database Identification Window

- DBCA Storage Option Window

- DBCA Fast Recovery Option Window

- DBCA Network Configuration Window

- DBCA Database Vault Option Window

- DBCA Configuration Options Window

- DBCA Management Options Window

- DBCA User Credentials Window

- DBCA Creation Option Window

- DBCA Summary Window

- DBCA Progress Window

- DBCA Finish Window

Most of these windows provide default settings. Depending on the options you choose in DBCA, some of these windows may not be displayed.

##### 2.3.2.1 DBCA Creation Mode Window

The Database Configuration Assistant (DBCA) Creation Mode window enables you to create a database with typical configuration or with advanced configuration.

If you choose Advanced configuration, you can customize storage locations, management options, database options, and different passwords for Administrator user accounts.

If you choose Typical configuration, you make fewer choices in the options for your database, which allows you to create your database sooner.

When you select Typical configuration, you can select the following options:

- Global database name: Enter the database name in the form database_name.domain_name.

- Storage type: Choose either File System or Automatic Storage Management.

  When you choose File System, your database files are managed by the file system of your operating system.

  When you choose Automatic Storage Management, you place your data files in Oracle Automatic Storage Management (Oracle ASM) disk groups.

- Database files location: The choice you make for the Storage type option determines what you specify for the Database files location option.

  When you choose File System in the Storage type field, you specify the directory path where the database files are to be stored in the Database files location field. Oracle Database can create and manage the actual files.

  When you choose Automatic Storage Management in the Storage type field, you specify the disk group to use in the Database files location field (the disk group must already exist). With Oracle ASM, Oracle Database automatically manages database file placement and naming.

- Fast Recovery Area (FRA): Specify a backup and recovery area.

- Database character set: Choose the character set to use for the database. See "Character Sets" for more information about character sets.

- Administrative password: Enter the password to use for the database administrative passwords (such as the `SYS` and `SYSTEM` accounts).

- User "Oracle Home User" Password (on Microsoft Windows operating systems only): If during the installation you specified a non-administrator, low privileged Windows User Account (as Oracle Home User) to run the database services under, you are prompted for the password of that user account.

- Create as Container database: Enable this option to create the database as a multitenant container database (CDB) that can support zero, one, or many user-created pluggable databases (PDBs).

  If you want DBCA to create a PDB when it creates the CDB, specify the PDB name in the Pluggable database name field.

**See Also:**

- [Oracle Database Platform Guide for Microsoft Windows](../ntqrf/supporting-oracle-home-user-on-windows.md) for more information about the Oracle Home User feature

- [Oracle Multitenant Administrator's Guide](../multi/introduction-to-the-multitenant-architecture.md) for an introduction to CDBs and PDBs

- [Oracle Multitenant Administrator's Guide](../multi/managing-a-multitenant-environment.md) for information about managing CDBs and PDBs

##### 2.3.2.2 DBCA Deployment Type Window

The Database Configuration Assistant (DBCA) Deployment Type window enables you to select the type of database template to use to create the database. You can select:

- Data Warehouse

- General Purpose or Transaction Processing

- Custom Database

Oracle Enterprise Manager Database Express (EM Express) supports Oracle single instance databases, including non-CDBs, multitenant container databases (CDBs), and pluggable databases (PDBs).

You can use DBCA to create a database from templates supplied by Oracle or from templates that you create. The templates contain settings optimized for a particular type of workload.

Oracle ships templates for the following two workload types:

- General purpose or transaction processing

- Data warehouse

Select the template suited to the type of workload your database will support. If you are not sure which to choose, then select the default General Purpose or Transaction Processing template.

**Note:**

The General Purpose or Transaction template and the Data Warehouse template create a database with the `COMPATIBLE` initialization parameter set to `12.2.0.0.0`.

For more complex environments, you can select the Custom Database option. This option does not use templates and results in a more extensive interview, which means that it takes longer to create your database.

**See Also:**

- [Oracle Database Reference](../refrn/COMPATIBLE.md) for more information about the `COMPATIBLE` initialization parameter

- "Managing Templates with DBCA" for more information about using database templates

##### 2.3.2.3 DBCA Database Identification Window

In the Global database name field of the Database Configuration Assistant (DBCA) Database Identification window, enter the database name in the form database_name.domain_name.

In the SID field, enter the system identifier. The SID defaults to the database name and uniquely identifies the instance that runs the database.

If you enable the Create as Container database option, the database is created as a multitenant container database (CDB) that can support zero, one, or many user-created pluggable databases (PDBs).

If you do not want DBCA to create a PDB when it creates the CDB, enable the Create an empty Container database option.

If you want DBCA to create one or more PDBs when it creates the CDB, enable the Create a Container database with one or more PDBs option. Then enter the number of PDBs to create in the Number of PDBs field. In the PDB Name field, specify the name to use for the PDB or PDBS to be created. When you create multiple PDBs, the PDB name you specify is used as a prefix for the PDBs to be created. For example, if you ask for 3 PDBs to be created and specify SANDBOXPDB as the PDB name, then the names of the PDBs created will be SANDBOXPDB1, SANDBOXPDB2, and SANDBOXPDB3.

**See Also:**

- [Oracle Multitenant Administrator's Guide](../multi/introduction-to-the-multitenant-architecture.md) for an introduction to CDBs and PDBs

- [Oracle Multitenant Administrator's Guide](../multi/managing-a-multitenant-environment.md) for information about managing CDBs and PDBs

##### 2.3.2.4 DBCA Storage Option Window

In the Database Configuration Assistant (DBCA) Storage Option window, specify the storage option for your database.

- Use template file for database storage attributes—This option instructs DBCA to use the directory information as specified in the template.

- Use following for the database storage attributes—This option requires you to specify where the database files will be stored.

  With this option, you need to choose how the database files will be managed:

  If you choose File System, your database files are managed by the file system of your operating system.

  If you choose Automatic Storage Management (ASM), you place your data files in Oracle Automatic Storage Management (Oracle ASM) disk groups.

  If you specify the Use Oracle-Managed Files (OMF) option, Oracle Database will directly manage operating system files comprising an Oracle database. You specify the default location, called a database area, for all your files. Oracle Database thereafter automatically creates and deletes files in this location, as required. When you select this option, you delegate the complete management of database files to the database. You no longer have to specify the file names, their location, or their sizes.

##### 2.3.2.5 DBCA Fast Recovery Option Window

The DBCA Fast Recovery Option window enables you to configure a backup and recovery area for your database.

Then specify the locations for the Oracle database files. Select one of the following options:

When you create a new database, it is important to configure the database so you can recover your data if a system failure occurs. Online redo log files contain a record of changes that were made to data files. Online redo log files are stored in online redo log groups. You must have at least two online redo log groups for your database. After the online redo log files in a group have filled up, the log writer process (LGWR) switches the writing of redo records to a new online redo log group. Oracle Database can automatically save the inactive group of online redo log files to one or more offline destinations, known collectively as the archived redo log (also called the archive log). The process of turning online redo log files into archived redo log files is called archiving.

Archiving can be performed only if the database is running in `ARCHIVELOG` mode. A group of online redo log files cannot be reused by the log writer (LGWR) process until the group is archived. If the database is running in `NOARCHIVELOG` mode, then when a group becomes inactive after the LGWR process switches to a new group, the inactive group is available for immediate reuse by the LGWR process.

The `NOARCHIVELOG` mode protects a database from instance failure but not from media failure. Only the most recent changes made to the database, which are stored in the online redo log files, are available for instance recovery. To restore a database operating in `NOARCHIVELOG` mode, you can use only entire database backups taken while the database is closed. Therefore, if you operate a database in `NOARCHIVELOG` mode, then back up the entire database at regular, frequent intervals.

The archiving of online redo log files has the following advantages:

- A database backup, with online and archived redo log files, guarantees that you can recover all committed transactions if the operating system or hardware fails.

- You can recover the database using a backup that was taken while the database was open and being used, if you have a copy of the archived log files that were written while the database was being backed up.

- You can perform online tablespace backups, and use these backups to restore a tablespace following media failure.

- You can keep a standby database current with its original database by continuously applying the original archived redo log files to the standby database.

Before you can archive the online redo log files, you must determine the destination to which you want to archive. Oracle recommends that the archive log be stored in a fast recovery area because it can simplify backup and recovery operations for your database. A fast recovery area is a location in which Oracle Database can store and manage files related to backup and recovery. It is distinct from the database area, which is a location for the current database files (data files, control files, and online redo log files).

When creating your database, you can select the following options:

- Specify Fast Recovery Area—Select this option to specify a backup and recovery area and its directory location and size. You can use variables to identify standard locations.

  With this option, you also make choices for these fields:
  - Recovery files storage type—Specify the directory to use for the fast recovery area.

  - Fast Recovery Area—Specify the type of storage you would like your database to use for recovery-related files.

  - Fast Recovery Area size—Specify the size of the fast recovery area.

- Enable Archiving—Select this option to enable the archiving of database online redo log files, which can be used to recover a database. Selecting this option is the same as running the database in `ARCHIVELOG` mode.

  Oracle recommends you select Enable Archiving. Selecting this option provides better protection for your database for software or hardware failure. If you do not select this option now, then you can enable ARCHIVELOG mode later. See "[Configuring Your Database for Basic Backup and Recovery](performing-backup-and-recovery.md)".

##### 2.3.2.6 DBCA Network Configuration Window

In the Database Configuration Assistant (DBCA) Network Configuration window, the listeners in the current Oracle home are displayed. If you want to create a new listener in the current Oracle home, you can do it in the Network Configuration window.

##### 2.3.2.7 DBCA Database Vault Option Window

The Database Configuration Assistant (DBCA) Database Vault Option window enables you to configure Oracle Database Vault and Oracle Database Label Security for your database.

You can configure Oracle Database Vault and Oracle Label Security in this window, or you can click Next to continue through DBCA without configuring Oracle Database Vault and Oracle Label Security.

**See Also:**

- [Oracle Database Vault Administrator's Guide](../dvadm/introduction-to-oracle-database-vault.md) for more information about Oracle Database Vault

- [Oracle Label Security Administrator's Guide](../olsag/introduction-to-oracle-label-security.md) for more information about Oracle Label Security

##### 2.3.2.8 DBCA Configuration Options Window

The links in the Database Configuration Assistant (DBCA) Configuration Options window provide access to additional windows that enable you to further configure your database.

For example, you can use this window to configure the following for your database:

- Memory

- Sizing

- Character Sets

- Connection mode

- Sample schema

###### 2.3.2.8.1 Memory

Use the Memory tab of the Database Configuration Assistant (DBCA) Configuration Options window to control how the database manages its memory.

You can choose from the following memory management methods:

- Use Automatic Shared Memory Management

  This method enables you to allocate specific amounts of memory to the SGA and aggregate PGA. Automatic shared memory management is enabled for the SGA, and memory is allocated to the individual PGAs as needed.

  To learn more about SGA and PGA, see "[About Instance Memory Structures](managing-the-oracle-instance.md)".

- Use Manual Shared Memory Management

  This method requires you to enter specific values for each SGA component and the aggregate PGA. You determine how the SGA memory is distributed among the SGA memory components. This method is intended for experienced Oracle Database administrators.

- Use Automatic Memory Management

  This method requires you to set the Oracle systemwide usable memory in the Memory target field, and then the system automatically tunes many of the memory components of the SGA, and allocates memory to individual PGAs as needed. The system can also dynamically decrease or increase the total amount of memory allocated to the SGA or aggregate PGA, depending on processing demands. The total memory used for the database instance never exceeds the amount you specify.

  **Note:**

  If the total physical memory of your database instance is greater than 4 GB, then you cannot select the Use Automatic Memory Management option. Instead, use automatic shared memory management. Automatic shared memory management automatically distributes the available memory among the various components as required, allowing the system to maximize the use of all available SGA memory.

**See Also:**

"[Managing the Oracle Instance](managing-the-oracle-instance.md)" for more information about memory management options

###### 2.3.2.8.2 Sizing

In the Sizing tab of the Database Configuration Assistant (DBCA) Configuration Options window, you specify the smallest block size and the maximum number of operating system user processes that can simultaneously connect to the database.

- Block Size—Use this list to select the block size, or accept the default. Oracle Database data is stored in data blocks of the size specified. One data block corresponds to a specific number of bytes of physical space on disk. Selecting a block size other than the default 8 kilobytes (KB) value requires advanced knowledge and should be done only when absolutely required.

  While using predefined templates, this list is not enabled because the database will be created with the default block size of 8 KB.

- Processes—In this field, specify the maximum number of processes that can simultaneously connect to the database. Enter a number or accept the default value of 320. The default value for this parameter is appropriate for many environments. The value you select should allow for all background processes, user processes, and parallel execution processes.

###### 2.3.2.8.3 Character Sets

Use the Character sets tab of the Database Configuration Assistant (DBCA) Configuration Options window to determine how character data is stored in the database. Character sets are the encoding schemes used to display characters on your computer screen. The character set determines what languages can be represented in the database.

Oracle recommends using Unicode (AL32UTF8) as the database character set. AL32UTF8 is Oracle's name for the UTF-8 encoding of the Unicode standard. The Unicode standard is the universal character set that supports most of the currently spoken languages of the world. The use of the Unicode standard is indispensable for any multilingual technology, including database processing.

After a database is created and accumulates production data, changing the database character set is a time consuming and complex project. Therefore, it is very important to select the right character set at installation time. Even if the database does not currently store multilingual data but is expected to store multilingual data within a few years, the choice of AL32UTF8 for the database character set is usually the only good decision.

If you create a multitenant container database (CDB), consider that the character set you select determines which other databases you can later plug into the CDB. Only databases with a compatible database character set can be plugged into the CDB.

The default character set used by Oracle Universal Installer (OUI) and DBCA for the UNIX, Linux, and Microsoft Windows platforms is not AL32UTF8, but a Microsoft Windows character set known as an ANSI code page. The particular character set is selected based on the current language (locale) of the operating system session that started OUI or DBCA. If the language is American English or a Western European language, then the default character set is WE8MSWIN1252. Each Microsoft Windows ANSI Code Page can store data from only one language or a limited group of languages, such as only Western European, or only Eastern European, or only Japanese.

A Microsoft Windows character set is the default even for databases created on UNIX and Linux platforms because Microsoft Windows is the prevalent platform for client workstations. Oracle Client libraries automatically perform the necessary character set conversion between the database character set and the character sets used by non-Windows client applications.

You may also choose to use any other character set from the presented list of character sets. You can use this option to select a particular character set required by an application vendor, or choose a particular character set that is the common character set used by all clients connecting to this database.

Because AL32UTF8 is a multibyte character set, database operations on character data may be slightly slower when compared to single-byte database character sets, such as WE8MSWIN1252. Storage space requirements for text in most languages that use characters outside of the ASCII repertoire are higher in AL32UTF8 compared to legacy character sets supporting the language. Note that the increase in storage space concerns only character data and only data that is not in English. The universality and flexibility of Unicode usually outweighs these additional costs.

Choose one of the following for the database character set:

- Use Unicode (AL32UTF8)—Select this option to support multiple languages for your database users and database applications.

  **Note:**

  - AL32UTF8 is a variable-width multibyte character set. Applications connecting to a database that uses AL32UTF8 for character data processing must be correctly programmed to work with such character sets. Always verify the character set requirements of the applications that use the database. Contact the application vendor and ask for a Unicode-capable version, if your current application version does not support the Unicode standard.

  - Oracle recommends using AL32UTF8 as the database character set. AL32UTF8 is the proper implementation of the Unicode encoding UTF-8. Starting with Oracle Database 12c Release 2, AL32UTF8 is used as the default database character set while creating a database using OUI as well as DBCA.

  - Do not use UTF8 as the database character set as it is not a proper implementation of the Unicode encoding UTF-8. If the UTF8 character set is used where UTF-8 processing is expected, then data loss and security issues may occur. This is especially true for Web related data, such as XML and URL addresses.

  - AL32UTF8 and UTF8 character sets are not compatible with each other as they have different maximum character widths (four versus three bytes per character).

- Use OS character set (WE8MSWIN1252)—Select this option to select only the language currently used by the operating system for all your database users and database applications.

- Choose from the list of character sets—Select this option if you want Oracle Database to use a character set other than the default character set used by the operating system.

Choose a national character set:

- National Character Set—In this list, select a character set or accept the default. The national character set, also called `NCHAR` character set, is the character set used to store and process data of data types `NVARCHAR2`, `NCHAR`, and `NCLOB`. These data types allow storing of Unicode characters in a database that does not have a Unicode database character set. Unless installation requirements of any of your applications specify otherwise, accept the default value of AL16UTF16 as the national character set.

  **Note:**

  Although this character set is called "national," after the SQL standard (ISO/IEC 9075), it is not better suited to support globalized applications than the database character set. Because working with national character set data requires additional API calls in client applications, and because national character set data is not supported by some database components, such as Oracle Text, Oracle recommends that multilingual applications use `VARCHAR2`, `CHAR`, and `CLOB` data types and an Oracle database with the database character set AL32UTF8.

- Default language—In this list, select a default database language or accept the default. The default language determines how the database supports locale-sensitive information such as day and month abbreviations, default sorting sequence for character data, and reading direction (left to right or right to left).

- Default territory—In this list, select the name of the territory whose conventions are to be followed for day and week numbering or accept the default. The default territory also establishes the default date format, the default decimal character and group separator, and the default International Standardization Organization (ISO) and local currency symbols. For example, in the United Kingdom, the default date format is DD-MON-YYYY, where DD is the day of the month (1-31), MON is the abbreviated name of the month, and YYYY is the 4-digit year.

###### 2.3.2.8.4 Connection mode

Use the Connection mode tab of the Database Configuration Assistant (DBCA) Configuration Options window to select the database connection mode. You can run the database in either of the following connection modes:

- Dedicated server mode—This mode allows a dedicated server process for each user process. Select this option when the number of total clients is expected to be small, for example, 50 or fewer. You might also choose this option when database clients typically make persistent, long-running requests to the database. By default, the database is configured for dedicated server processes.

- Shared server mode—This mode allows several client connections to share a database-allocated pool of resources. Use this mode in configurations in which client load is expected to cause a strain on memory and other system resources. If you choose shared server mode, then you must indicate the number of server processes you want to create when a database instance is started. For more information about setting this parameter, click Help.

###### 2.3.2.8.5 Sample schema

Use the Sample schema tab of the Database Configuration Assistant (DBCA) Configuration Options window to configure the Oracle database sample schemas.

To include the sample schemas in your database, select Add sample schemas to the database.

##### 2.3.2.9 DBCA Management Options Window

Use the Database Configuration Assistant (DBCA) Management Options window to set up your database so it can be managed with Oracle Enterprise Manager. Oracle Enterprise Manager provides Web-based management tools for individual databases, and central management tools for managing your entire Oracle environment.

- To manage your database locally, select Configure Enterprise Manager (EM) database express. You can accept the assigned port for EM Express or enter a different unused port.

- If the Oracle Management Agent is installed on your host computer, then you can choose Register with Enterprise Manager (EM) cloud control and then specify the host and port for the Management Service and the EM Admin username and password.

  **See Also:**

  [Oracle Database Administrator's Guide](../admin/distributed-database-concepts.md) for more information about Oracle Enterprise Manager Cloud Control

##### 2.3.2.10 DBCA User Credentials Window

In the Database Configuration Assistant (DBCA) User Credentials window, specify the passwords for the administrative accounts such as `SYS`, `SYSTEM`, and `PDBADMIN`.

On Microsoft Windows operating systems only: If during the installation you specified a non-administrator, low privileged Windows User Account as Oracle Home User, you are prompted for the password of that user account.

##### 2.3.2.11 DBCA Creation Option Window

The Database Configuration Assistant (DBCA) Creation Option window enables you to select different options for creating the database.

For example, in the Database Configuration Assistant (DBCA) Creation Option window, select any of the following options for creating the database:

- Create database—Select this option to create your database now.

- Save as a database template—Select this option to save the database definition as a template to use at a later time.

- Generate database creation scripts—Select this option to generate a SQL database creation script that you can run at a later time.

##### 2.3.2.12 DBCA Summary Window

The Database Configuration Assistant (DBCA) Summary window displays a summary of the configuration options that you have chosen for the database. Review the summary information.

To change any of these options, click Back and return to the window where you can modify the option.

Click Finish to have DBCA begin the creation of the database with the specified configuration options.

##### 2.3.2.13 DBCA Progress Window

The Database Configuration Assistant (DBCA) Progress window displays the progress of the database creation operation.

##### 2.3.2.14 DBCA Finish Window

The DBCA Finish window appears after DBCA finishes configuring the database.

The Finish window provides information about:

- The location of the DBCA log files

- The global database name, SID, and server parameter file name for the database

- The URL to use to access Enterprise Manager to manage the database

- Managing the database accounts that were created

#### 2.3.3 Changing the Configuration of a Database Using DBCA

You can use Database Configuration Assistant (DBCA) to change the configuration of an existing database. For example, you can make configuration changes such as:

- Add database options that were not previously configured (for example, Oracle Label Security or Oracle OLAP)

- Change default security settings

- Change the server mode from dedicated to shared, or the reverse

##### To change the configuration of a database using DBCA:

1.  Start DBCA as described in "Starting DBCA".
2.  In the Database Operation window, select Configure an existing database and click Next.
3.  Follow the instructions in the DBCA guided workflow.

#### 2.3.4 Deleting a Database Using DBCA

You can use Database Configuration Assistant (DBCA) to delete a database. When DBCA deletes a database, it shuts down the database instance and then deletes all database files. On the Windows platform, it also deletes associated Windows services.

##### To delete a database using DBCA:

1.  Start DBCA as described in "Starting DBCA".
2.  In the Database Operation window, select Delete database and click Next.
3.  Select the database to delete and click Next.
4.  Follow the instructions in the DBCA guided workflow.

#### 2.3.5 Managing Templates with DBCA

Database Configuration Assistant (DBCA) templates are XML files that contain information required to create a database. Templates are used in DBCA to create new databases and duplicate existing databases. The information in templates includes database options, initialization parameters, and storage attributes (for data files, tablespaces, control files, and online redo log files).

Templates can be used just like scripts, but they are more powerful than scripts because you have the option of duplicating a database. Duplication saves time because you copy the files of an existing database, referred to as a seed database, to the correct locations.

Templates are stored in the following directory:

    ORACLE_HOME/assistants/dbca/templates

##### 2.3.5.1 Advantages of Using DBCA Templates

There are several advantages to using Database Configuration Assistant (DBCA) templates. For example:

- Time saving. If you use a template, then you do not have to define the database.

- Easy duplication. By creating a template containing your database settings, you can easily create a duplicate database without specifying parameters twice.

- Easy editing. You can quickly change database options from the template settings. Database options can be configured or modified only for a custom database or nonseed template (.dbt file). You can not modify database options for a seed template (includes data file backups).

- Easy sharing. Templates can be copied from one computer to another.

##### 2.3.5.2 Types of DBCA Templates

Database Configuration Assistant (DBCA) templates include seed templates and nonseed templates.

The characteristics of each are shown in Table 2-1.

Table 2-1 DBCA Template Types

| Type    | File Extension | Includes Data Files | Database Structure                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 |
|:--------|:---------------|:--------------------|:-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Seed    | `.dbc`         | Yes                 | This type of template contains both the structure and the physical data files of an existing database, referred to as the seed database. Your new database starts as a copy of the seed database, and requires only the following changes:<br>• Name of the database<br>• Destination of the data files<br>• Number of control files<br>• Number of online redo log groups<br>• Initialization parameters<br>Other changes can be made after database creation using custom scripts that can be invoked by DBCA, command-line SQL statements, or Oracle Enterprise Manager Database Express (EM Express).<br>The data files for the seed database are stored in compressed Recovery Manager (RMAN) backup format in a file with a .dfb extension. The seed database control file is stored in a file with .ctl extension. (This file is needed only when storing data files in Oracle Automatic Storage Management (Oracle ASM) disk groups or as Oracle Managed Files.) The .dbc file contains the location of the seed database data files and contains the source database name used to mount the control file. |
| Nonseed | `.dbt`         | No                  | This type of template is used to create a new database. It contains the characteristics of the database to be created. Nonseed templates are more flexible than their seed counterparts because all data files and online redo log files are created to your specification, and names, sizes, and other attributes can be changed as required.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                     |

##### 2.3.5.3 DBCA Templates Provided by Oracle

Oracle provides Database Configuration Assistant (DBCA) templates for data warehouses, general purpose or transaction processing databases, and for custom databases. These templates are described in Table 2-2.

Table 2-2 Oracle-Provided DBCA Templates and Their Corresponding Workloads

| Template                                  | Workload                                                                                                                                                                                                                                                                                                                      |
|:------------------------------------------|:------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Data warehouse                            | Users perform numerous, complex queries that process large volumes of data. Response time, accuracy, and availability are key issues.<br>These queries (`SELECT` statements) range from a fetch of a few records to queries that sort thousands of records from many different tables.                                        |
| General Purpose or Transaction processing | Many concurrent users perform numerous transactions that require rapid access to data. Availability, speed, concurrency, and recoverability are key issues.<br>Transactions consist of reading (`SELECT` statements), writing (`INSERT` and `UPDATE` statements), and deleting (`DELETE` statements) data in database tables. |
| Custom database                           | This template allows you maximum flexibility in defining a database because you can change any of the settings for the database being created.                                                                                                                                                                                |

##### 2.3.5.4 Creating Templates Using DBCA

Follow the instructions in this section to create your own Database Configuration Assistant (DBCA) templates.

##### To create templates:

1.  Start DBCA as described in "Starting DBCA".
2.  In the Database Operation window, select Manage templates and click Next.
3.  In the Template Management window, select Create a database template, enter values for the following fields, and click Next.
    - Template name

      The name you provide in the Template name field identifies the template when it appears on the Database Templates page when you are creating a new database.

    - Template location

      Specify a location to store the template.

    - Description

      Use the Description field to provide information about the purpose and features of databases created with the template. The description appears just below the template name when you click View Details for the template on the Deployment Type page.
4.  Follow the instructions in the DBCA guided workflow to create your template.

##### 2.3.5.5 Deleting DBCA Templates

When you delete a Database Configuration Assistant (DBCA) template, it is no longer available to create a new database or a new template.

##### To delete a template:

1.  Start DBCA as described in "Starting DBCA".
2.  In the Database Operation window, select Manage templates and click Next.
3.  In the Template Management window, select Delete a database template and click Next.
4.  Select the template to delete and click Next.
5.  Follow the instructions in the DBCA guided workflow.

#### 2.3.6 Using DBCA to Manage PDBs

When a multitenant container database (CDB) exists, you can use Database Configuration Assistant (DBCA) to perform pluggable database (PDB) operations in the CDB. For example, you can use DBCA to perform the following PDB operations in the CDB:

- Create a PDB

  This option creates a new PDB in a CDB.

  DBCA can create the new PDB:

  - From an existing PDB

  - From the CDB seed, PDB\$SEED

  - Using a PDB archive (.pdb) file for an unplugged PDB

  - Using a PDB file set for an unplugged PDB

    A PDB file set includes a PDB metadata (.xml) file and a PDB datafile backup (.dfb) file.

- Delete a PDB

  This option deletes a PDB.

- Unplug a PDB

  This option unplugs a PDB. The unplugged PDB can be plugged into the same CDB or another CDB.

  You can use DBCA to create a PDB archive (.pdb) file or a PDB file set (.xml file and .dfb file) when you unplug a PDB.

- Configure a PDB

  This option enables you to specify an Oracle Enterprise Manager Database Express (EM Express) port for the PDB, so that you can manage the PDB using EM Express. It also allows you to configure other database options for the PDB.

##### 2.3.6.1 Managing PDBs in a CDB using DBCA

You can use Database Configuration Assistant (DBCA) to create, unplug, delete, or configure a pluggable database (PDB) in an existing multitenant container database (CDB).

**Note:**

The PDB operations can be performed only in a CDB. DBCA issues an error message if you attempt to perform PDB operations in a database that is not a CDB.

##### To manage PDBs using DBCA:

1.  Start DBCA as described in "Starting DBCA".
2.  In the Database Operation window, select Manage Pluggable databases and click Next
3.  In the Manage Pluggable Databases window, select one of the PDB operations and click Next.
4.  In the Select Database window, select the CDB in which to perform the selected PDB operation and click Next.
5.  Follow the instructions in the DBCA guided workflow for the selected PDB operation.

**See Also:**

- [Oracle Multitenant Administrator's Guide](../multi/introduction-to-the-multitenant-architecture.md) for an introduction to CDBs and PDBs

- [Oracle Multitenant Administrator's Guide](../multi/managing-a-multitenant-environment.md) for information about managing CDBs and PDBs

### 2.4 Manually Installing the Database Sample Schemas Post-Installation

You may decide sometime after the initial database installation that you would like to install the database sample schemas. You can create the sample schemas manually by running SQL scripts.

**See Also:**

[Oracle Database Sample Schemas](../comsc/installing-sample-schemas.md) for more information about creating the sample schemas manually using SQL

### 2.5 Installation: Oracle By Example Series

Oracle By Example (OBE) has a series on the Oracle Database 2 Day DBA guide. This OBE series steps you through the tasks in this chapter and includes annotated screenshots.

The series consists of the following tutorials:

1.  Create Container Database - Typical Mode

2.  Create Container Database - Advanced Mode

3.  Create Non-Container Database - Typical Mode

4.  Create Non-Container Database - Advanced Mode

5.  Perform Advanced Installation for Non-Container Database

6.  Perform Basic Installation for Container Database

7.  Perform Basic Installation for Non-Container Database

The above tutorials can be accessed in two ways:

- To see a clickable list of the above tutorials, go to [Install Oracle Database Series](https://docs.oracle.com/pls/topic/lookup?ctx=en/database/oracle/oracle-database/19/admqs&id=twodaydba_obe_install).

- For seamless navigation through the tutorial series, access the following link:

  [Install Oracle Database Software and Create a Database](https://docs.oracle.com/pls/topic/lookup?ctx=en/database/oracle/oracle-database/19/admqs&id=twodaydba_lp_install)

  You can navigate across the tutorials by clicking the \> button at the bottom of the pane.
