For Oracle Database Client, response files are located in the `$ORACLE_HOME/response` directory.

All response file templates contain comment entries, sample formats, examples, and other useful instructions. Please read these instructions as they help you specify values for the variables listed in the response files and customize your installation.

The following table lists the response files provided with this software:

Table A-1 Response Files for Oracle Database Client

| Response File        | Description                                                                  |
|:---------------------|:-----------------------------------------------------------------------------|
| `client_install.rsp` | Silent installation of Oracle Database Client                                |
| `netca.rsp`          | Silent configuration of Oracle Net using Oracle Net Configuration Assistant. |

**Caution:**

When you modify a response file template and save a file for use, the response file may contain plain text passwords. Ownership of the response file should be given to the Oracle software installation owner only, and permissions on the response file should be changed to 600. Oracle strongly recommends that database administrators or other administrators delete or secure response files when they are not in use.

To copy and modify a response file:

1.  Copy the response file from the response file directory to a directory on your system:
        $ cp /directory_path/inventory/response/response_file.rsp local_directory

    In this example, `directory_path` is the path of the directory where you have copied the installation binaries.
2.  Open the response file in a text editor:
        $ vi /local_dir/response_file.rsp
3.  Follow the instructions in the file to edit it.
    **Note:**

    The installer or configuration assistant fails if you do not correctly configure the response file. Also, ensure that your response file name has the `.rsp` suffix.
4.  Secure the response file by changing the permissions on the file to 600:
        $ chmod 600 /local_dir/response_file.rsp

    Ensure that only the Oracle software owner user can view or modify response files or consider deleting them after the installation succeeds.

    **Note:**

    A fully-specified response file for an Oracle Database Client installation contains the passwords for database administrative accounts and for a user who is a member of the OSDBA group (required for automated backups).

**Parent topic:** [Preparing Response Files](preparing-response-files.md)
