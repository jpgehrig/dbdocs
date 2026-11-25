## Installing with Minimum Memory Requirements

Installations of Oracle Database on computers with RAM and virtual memory lesser than the minimum required have the following limitations:

- Computers cannot run Oracle Database Upgrade Assistant, Oracle Database Configuration Assistant, or Oracle Net Services Configuration Assistant during an Oracle Universal Installer installation session.

- Depending on how many applications run on the computer, you must further increase the paging file size or reduce the size of the System Global Area (SGA) if you run out of virtual memory. If temporary files and the paging file are both stored on the same physical drive, the space requirements for one can limit the size of the other. If your system has limited free space, first install the Oracle Database software. After the installation is finished, create a database with Oracle Database Configuration Assistant.

**Note:**

Do not install the database on computer systems that barely meet the minimum memory and virtual memory requirements of 1 GB.

You can install only the database software by selecting the Install Database Software only option provided on the Select Installation Option screen.

After installation, run the appropriate configuration assistant for your needs:

- To create a new database, run Oracle Database Configuration Assistant. From the Start menu, select All Programs, then Oracle - HOMENAME, then Configuration and Migration Tools, then Database Configuration Assistant.

- To upgrade an existing database, run Oracle Database Upgrade Assistant. From the Start menu, select All Programs, then Oracle - HOMENAME, then Configuration and Migration Tools, then Database Upgrade Assistant.

**Parent topic:** [Preinstallation Considerations for Installing Oracle Database](preinstallation-considerations-for-installing-oracle-database.md)
