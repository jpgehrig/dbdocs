## Creating Required Directories

Use this procedure to create the required directories.

**Note:**

You must complete this procedure only to place the Oracle database or recovery files on a separate file system from the Oracle base directory.

To create directories for the Oracle database or recovery files on separate file systems from the Oracle base directory, follow these steps:

1.  Use Windows Explorer to determine the free disk space on the file system.
2.  From the display, identify the file systems to use:
    | File Type      | File System Requirements                                                                                                                                                      |
    |:---------------|:------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | Data files     | Select one of the following:<br>• A single file system with at least 950 MB of free disk space<br>• Two or more file systems with at least 950 MB of free disk space in total |
    | Recovery files | Choose a file system with at least 2 GB of free disk space.                                                                                                                   |

    If you are using the same file system for multiple types of files, then add the disk space requirements for each type to determine the total disk space requirement.
3.  Note the names of the directories for the file systems that you identified.

**Parent topic:** [Creating Directories for Oracle Data Files or Recovery Files](creating-directories-data-and-recovery-files.md)
