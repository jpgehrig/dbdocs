Oracle provides response file templates for each product and each configuration tool.

### About Response File Templates

For Oracle Database, the response file templates are located in the `$ORACLE_HOME/install/response` directory. For Oracle Grid Infrastructure, the response file templates are located in the `Grid_home``/install/response` directory.

Where, Grid_home is the Oracle Grid Infrastructure home directory path.

**Note:**

If you copied the software to a hard disk, then the response files are located in the `$ORACLE_HOME/install/response` directory.

All response file templates contain comment entries, sample formats, examples, and other useful instructions. Read the response file instructions to understand how to specify values for the response file variables, so that you can customize your installation.

The following table lists the response files provided with this software:

Table A-1 Response Files for Oracle Database and Oracle Grid Infrastructure

| Response File    | Description                                                             |
|:-----------------|:------------------------------------------------------------------------|
| `db_install.rsp` | Silent installation of Oracle Database.                                 |
| `dbca.rsp`       | Silent creation and configuration of Oracle Database using Oracle DBCA. |
| `netca.rsp`      | Silent configuration of Oracle Net using Oracle NETCA.                  |
| `gridsetup.rsp`  | Silent configuration of Oracle Grid Infrastructure installations.       |

**Caution:**

When you modify a response file template and save a file for use, the response file may contain plain text passwords. Ownership of the response file should be given to the Oracle software installation owner only, and permissions on the response file should be changed to 600. Oracle strongly recommends that database administrators or other administrators delete or secure response files when they are not in use.

To copy and modify a response file:

1.  Copy the response file from the response file directory to a directory on your system:
    For example, for Oracle Database:

        $ cp $ORACLE_HOME/install/response/db_install.rsp local_directory
2.  Open the response file in a text editor:
        $ vi /local_directory/db_install.rsp
3.  Follow the instructions in the file to edit it.
    **Note:**

    The installer or configuration assistant fails if you do not correctly configure the response file. Also, ensure that your response file name has the `.rsp` suffix.
4.  Secure the response file by changing the permissions on the file to 600:
        $ chmod 600 /local_dir/db_install.rsp

    Ensure that only the Oracle software owner user can view or modify response files or consider deleting them after the installation succeeds.

    **Note:**

    A fully-specified response file for an Oracle Database installation contains the passwords for database administrative accounts and for a user who is a member of the OSDBA group (required for automated backups).

**Parent topic:** [Preparing Response Files](preparing-response-files.md)
