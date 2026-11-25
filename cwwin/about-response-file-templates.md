## About Response File Templates

Oracle provides response file templates for each product and installation type and for each configuration tool.

For Oracle Database, the response file templates are located in the `database\response` directory on the installation media and in the `Oracle_home``\inventory\response` directory. For Oracle Grid Infrastructure, the response file templates are located in the `Grid_home``\install\response` directory after the software is installed.

All response file templates contain comment entries, sample formats, examples, and other useful instructions. Read the response file instructions to understand how to specify values for the response file variables, so that you can customize your installation.

The following response files are provided with this software:

Table A-2 Response Files for Oracle Database and Oracle Grid Infrastructure

| Response File      | Used For                                                                                                     |
|:-------------------|:-------------------------------------------------------------------------------------------------------------|
| `db_install.rsp`   | Silent configuration of Oracle Database software                                                             |
| `dbca.rsp`         | Silent creation and configuration of an Oracle Database using Oracle Database Configuration Assistant (DBCA) |
| `netca.rsp`        | Silent configuration of Oracle Net using NETCA                                                               |
| `grid_install.rsp` | Silent configuration of Oracle Grid Infrastructure installations                                             |

**Caution:**

When you modify a response file template and save a file for use, the response file may contain plain text passwords. Ownership of the response file must be given to the Oracle software installation owner only, and access restricted to the response file. Oracle strongly recommends that database administrators or other administrators delete or secure response files when they are not in use.

**Parent topic:** [Preparing Response Files](preparing-response-files.md)
