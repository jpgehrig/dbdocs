As a database administrator (DBA), you are responsible for the overall operation of Oracle Database. This introductory chapter is intended to help orient you to many common DBA tasks, to the tools available to you, and to this guide.

The chapter contains the following sections:

- About This Guide

- About Oracle Database

- Common Oracle DBA Tasks

- Tools for Administering the Database

### 1.1 About This Guide

Oracle Database 2 Day DBA is a database administration quick start guide that teaches you how to perform day-to-day database administrative tasks. The goal of this guide is to help you understand the concepts behind Oracle Database, and to help you learn how to perform all common administrative tasks needed to keep the database operational. These tasks include configuring the database, managing memory and storage, managing users, managing database objects such as tables, performing basic troubleshooting, creating backups for your database, performance monitoring activities, and more.

The primary administrative interface used in this guide is Oracle Enterprise Manager Database Express (EM Express), featuring all the self-management capabilities introduced in Oracle Database.

This section includes these topics:

- What This Guide Is Not

- How to Use This Guide with Related Material

#### 1.1.1 What This Guide Is Not

Oracle Database 2 Day DBA is task-oriented. The objective is to describe why and when administrative tasks must be performed. Where appropriate, it describes the concepts necessary to understand and complete a task, assuming the reader has no prior knowledge of the database. This guide is not an exhaustive discussion of all Oracle Database concepts. For this type of information, see [Oracle Database Concepts](../cncpt/introduction-to-oracle-database.md).

Additionally, for a complete discussion of administrative tasks, see [Oracle Database Administrator’s Guide](../admin/getting-started-with-database-administration.md)

#### 1.1.2 How to Use This Guide with Related Material

This guide is part of a comprehensive set of learning materials for administering Oracle Database, which includes a learning path containing several 2 Day DBA Oracle By Example (OBE) tutorials, available on the Web.

Every chapter in Oracle Database 2 Day DBA has an associated set of 2 Day DBA tutorials. Each tutorial steps you through tasks in the chapter and includes annotated screenshots. In some cases, the tutorial provides additional information to help you complete the task.

At the end of each chapter, you can find the link to the associated OBE tutorial series. The home page for the 2 Day DBA learning path is:

[Oracle Database 2 Day DBA Learning Path](https://docs.oracle.com/pls/topic/lookup?ctx=en/database/oracle/oracle-database/19/admqs&id=twodaydba_learning_path)

### 1.2 About Oracle Database

Oracle Database is a relational database with object and Extensible Markup Language (XML) capabilities. In a relational database, all data is stored in tables that are composed of rows and columns. Oracle Database enables you to store data, update it, and efficiently retrieve it, with a high degree of performance, reliability, and scalability.

Oracle Database is composed of the following elements:

- The Oracle software that you install on your host computer

- The database, which is a collection of physical files on one or more disks

  The database contains user data, metadata, and control structures. Metadata, or data about the data, is the collection of information on disk that permits Oracle software to manage user data. An example of metadata is the data dictionary. Control structures (such as the control file and online redo log files) ensure the integrity, availability, and recoverability of user data.

- The Oracle instance, which is composed of the following:

  - The background processes, which are the operating system processes or threads that perform the work of accessing, storing, monitoring, and recovering user data, metadata, and control files associated with the database

  - The shared memory areas used by the background processes

- Server processes that perform work on behalf of connected users and applications, and the memory and temporary storage used by these processes

  Server processes parse and execute SQL statements, and retrieve and return results to the user or application.

- Oracle Net, which is a software layer that enables client applications and Oracle Database to communicate over a network, and the Oracle Net listener, which is a process that listens for connection requests from the network.

**See Also:**

- [Configuring the Network Environment](configuring-the-network-environment.md)

- [Managing the Oracle Instance](managing-the-oracle-instance.md)

- [Managing Database Storage Structures](managing-database-storage-structures.md)

- [Administering User Accounts and Security](administering-user-accounts-and-security.md)

- [Oracle Database Concepts](../cncpt/process-architecture.md) for more information about background processes

- [Oracle Database Reference](../refrn/background-processes.md) for more information about background processes

### 1.3 Common Oracle DBA Tasks

As an Oracle database administrator (DBA), you can expect to be involved in various tasks. For example:

- Installing Oracle software

- Creating Oracle databases

- Performing upgrades of the database and software to new release levels

- Starting and shutting down the database instance

- Managing the storage structures of the database

- Managing users and security

- Managing database objects, such as tables, indexes, and views

- Backing up the database and performing recovery operations when necessary

- Monitoring the state of the database and taking preventive or corrective action as required

- Monitoring and tuning database performance

- Diagnosing and reporting critical errors to Oracle Support Services

In a small to medium-sized database environment, you might be the sole person performing these tasks. In large, enterprise environments, the job is often divided among several DBAs, each of whom has a specialty, such as database security or database tuning.

**See Also:**

[Oracle Database Concepts](../cncpt/concepts-for-database-administrators.md) for more information about the duties of database administrators

### 1.4 Tools for Administering the Database

The goal of this guide is to enable you to quickly and efficiently create an Oracle database, and to provide guidance in basic database administration.

The following are some products, tools, and utilities you can use to achieve your goals as a database administrator:

- Oracle Universal Installer

  Oracle Universal Installer (OUI) is a utility that installs your Oracle software and options. It can automatically start Oracle Database Configuration Assistant to install a database.

- Oracle Database Configuration Assistant

  Oracle Database Configuration Assistant (DBCA) is a utility that creates a database from templates that are supplied by Oracle, or you can create your own. It enables you to copy a preconfigured seed database, thus saving the time and effort of generating and customizing a new database.

- Database Upgrade Assistant

  The Database Upgrade Assistant (DBUA) is a tool that guides you through the upgrade of your existing database to a new Oracle Database release.

- Net Configuration Assistant

  Net Configuration Assistant is a utility that enables you to configure listeners and naming methods, which are critical components of the Oracle Database network.

- Oracle Enterprise Manager Database Express

  The primary product for managing your database is Oracle Enterprise Manager Database Express (EM Express), a Web-based interface. After you have installed the Oracle Database software, created or upgraded a database, and configured the network, you can use EM Express to manage your database. EM Express also provides an interface for performance advisors.

  Oracle also offers separately licensed Oracle Enterprise Manager management packs, management plug-ins, and other products you can purchase to enhance the capabilities of Oracle Enterprise Manager in specific environments.

- SQL Developer

  SQL Developer provides another GUI for accessing your Oracle database. SQL Developer supports development in both the SQL and PL/SQL languages. It is available in the default installation of Oracle Database.

  With SQL Developer, you can browse database objects, run SQL statements and SQL scripts, and edit and debug PL/SQL statements. You can also run any number of provided reports, and also create and save your own.

**See Also:**

[Oracle Database Licensing Information User Manual](../dblic/Licensing-Information.md)
