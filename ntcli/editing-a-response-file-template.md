## Editing a Response File Template

Oracle provides response file templates for each product and the installation type, and for each configuration tool. These files are located in the `ORACLE_BASE\ORACLE_HOME``\assistants` directory, and the `database\response` directory on the Oracle Database installation media.

**Note:**

If you copied the software to a hard disk, the response files are located in the `stage_area``\database\response` directory.

All response file templates contain comment entries, sample formats, examples, and other useful instructions. Read the response file instructions to understand how to specify values for the response file variables, so that you can customize your installation.

The following table lists the available sample response files:

Table B-2 Response Files

| Response File Name   | Description                                               |
|:---------------------|:----------------------------------------------------------|
| `client_install.rsp` | Oracle Database Client installation                       |
| `netca.rsp`          | Silent installation of Oracle Net Configuration Assistant |

**Caution:**

When you modify a response file template and save a file for use, the response file may contain plain text passwords. Ownership of the response file must be given to the Oracle software installation owner only. Oracle strongly recommends that database administrators or other administrators delete or secure response files when they are not in use.

To copy and modify a response file:

1.  Copy the appropriate response files from the `client\response` directory on the Oracle Database media to your hard drive.
2.  Modify the response files with a text file editor.
3.  Run the response file by following the instructions in the “Running Oracle Universal Installer Using the Response file” section.

**Related Topics**

- [Running Oracle Universal Installer Using the Response File](running-oracle-universal-installe-using-the-response-file.md)

**Parent topic:** [Preparing a Response File](preparing-a-response-file.md)
