## Creating an Oracle Database on Direct NFS

Learn how to install and create an Oracle Database that uses Direct NFS (dNFS) for storage.

There are different configuration processes you must perform to use dNFS for your database file system. Following are the steps:

1.  Perform a Software-Only Installation of Oracle Database

    In a software-only installation, you install the Oracle Database software but do not create a database as part of the installation process. You can install only the database software by selecting the Install Database Software only option provided on the Select Installation Option screen.

2.  Use Oracle Database Configuration Assistant to Create and Configure the Database

    After the Prerequisite checks are complete, on the Summary screen, minimize the installation window. DO NOT click Finish at this point.

3.  Enable the Direct NFS option.

    Return to the DBCA window and click Finish.

4.  Map a drive letter to a CIFS share on the NFS server that represents the location of the database files.

        NET USE * \\filer\vol0\orcl

    After you complete this step, both Oracle and the Windows operating system can access the location where the database files reside. Oracle is using DNFS, but the Windows OS uses CIFS to access the same location on the NFS server.

5.  Verify that the Direct NFS is configured for the database.

    1.  Start SQL\*Plus.

    2.  Connect to the newly created database as a DBA user.

    3.  Run the following SQL command:

            SELECT * FROM v$dnfs_servers;

**Parent topic:** [Creating a Database After Installation](creating-a-database-after-installation.md)
