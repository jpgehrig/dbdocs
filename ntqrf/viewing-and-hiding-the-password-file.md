Use this procedure to make the password file visible or invisible from different locations.

The password file is not automatically hidden. It can be made invisible and visible again from two different locations:

- Using Command Prompt

- Using Windows Explorer

  **Note:**

  The password file must be visible before it can be moved, copied, or deleted.

### Using Command Prompt

1.  To see the password file, enter:

        ORACLE_HOME\database> attrib

    The password file is displayed as `PWD``sid``.ora`:

        A       ORACLE_HOME\database\oradba.exe
        A       ORACLE_HOME\database\oradim.log
        A       ORACLE_HOME\database\PWDsid.ora
        A       ORACLE_HOME\database\SPFILEsid.ora

2.  To make the password file invisible, enter:

        ORACLE_HOME\database> attrib +H PWDsid.ora

3.  To see the effect of the change, enter:

        ORACLE_HOME\database> attrib

    The password file is now hidden:

        A       ORACLE_HOME\database\oradba.exe
        A       ORACLE_HOME\database\oradim.log
        A   H   ORACLE_HOME\database\PWDsid.ora
        A       ORACLE_HOME\database\SPFILEsid.ora

4.  To make the password file visible again, enter:

        ORACLE_HOME\database> attrib -H PWDsid.ora

### Using Windows Explorer

To make the password file invisible or visible again:

1.  Go to the directory `ORACLE_HOME``\database`.

2.  Right-click PWDsid.ora.

3.  Select Properties.

    The `PWD``sid``.ora` Properties dialog box opens.

4.  In Attributes, check or clear the check box next to Hidden.

5.  Click OK.

To view or hide an invisible password file:

1.  Go to the directory `ORACLE_HOME``\database`.
2.  Select Folder Options from the Tools main menu.
3.  In the Folder Options window, select the View tab.
4.  To view an invisible password file, select Show hidden files and folders.
5.  To hide a visible password file, select Do not show hidden files and folders.
6.  Click OK.

**Parent topic:** [Creating and Populating Password Files](creating-and-populating-password-files.md)
