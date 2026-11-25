## Editing a Response File Template

You can copy and modify a response file template for each product and installation type and for each configuration tool.

To copy and modify a response file, perform the following steps:

1.  Copy the response file from the response file directory to a directory on your system.
        copy Oracle_home\install\response\product_timestamp.rsp local_directory
2.  Open the response file in a text editor.
3.  Follow the instructions in the file to edit it.
    **Note:**

    The installer or configuration assistant fails if you do not correctly configure the response file. Also, ensure that your response file name has the `.rsp` suffix.
4.  Secure the response file.
    Ensure that only the user that installed the Oracle software can view or modify response files. Consider deleting the modified response file after the installation succeeds.
    **Note:**

    A fully specified response file for an Oracle Grid Infrastructure installation or an Oracle Database installation can contain the passwords for:
    - Oracle Automatic Storage Management (Oracle ASM) administrative accounts

    - Database administrative accounts

    - A user who is a member of the operating system group `ORA_DBA` (required for automated backups)

**Parent topic:** [Preparing Response Files](preparing-response-files.md)
