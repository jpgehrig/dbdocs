## Creating Directories for Oracle Database Files

You can store Oracle Database and recovery files on a separate file system from the configuration files.

Perform this procedure to place the Oracle Database or recovery files on a separate file system from the Oracle base directory:

1.  Use the following command to determine the free disk space on each mounted file system:
        # df -h
2.  Identify the file systems to use, from the display:
    | Option         | Description                                                                                                                                                                   |
    |:---------------|:------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | Database Files | Select one of the following:<br>• A single file system with at least 1.5 GB of free disk space<br>• Two or more file systems with at least 3.5 GB of free disk space in total |
    | Recovery Files | Choose a file system with at least 2 GB of free disk space                                                                                                                    |

    If you are using the same file system for multiple file types, then add the disk space requirements for each type to determine the total disk space requirement.
3.  Note the names of the mount point directories for the file systems that you identified.
4.  If the user performing installation has permissions to create directories on the disks where you plan to install Oracle Database, then Oracle DBCA creates the Oracle Database file directory, and the Recovery file directory. If the user performing installation does not have write access, then you must create these directories manually.
    For example, given the user `oracle` and Oracle Inventory Group `oinstall`, and using the paths` /u03/oradata/wrk_area` for Oracle Database files, and `/u01/oradata/rcv_area` for the recovery area, these commands create the recommended subdirectories in each of the mount point directories and set the appropriate owner, group, and permissions on them:

    - Database file directory:

          # mkdir -p /u01/oradata/
          # chown oracle:oinstall /u01/oradata/
          # chmod 775 /u01/oradata

      The default location for the database file directory is `$ORACLE_BASE/oradata`.

    - Recovery file directory (fast recovery area):

          # mkdir -p /u01/oradata/rcv_area
          # chown oracle:oinstall /u01/oradata/rcv_area
          # chmod 775 /u01/oradata/rcv_area

      The default fast recovery area is `$ORACLE_BASE/fast_recovery_area`.

      Oracle recommends that you keep the fast recovery area on a separate physical disk than that of the database file directory. This method enables you to use the fast recovery area to retrieve data if the disk containing oradata is unusable for any reason.

**Parent topic:** [Configuring Storage for Oracle Grid Infrastructure for a Standalone Server](configuring-storage-for-oracle-grid-infrastructure-for-a-standalone-server.md)
