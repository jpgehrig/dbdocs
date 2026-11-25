## Cleaning Up After a Failed Installation

If an installation fails, then you must remove the Oracle home directory and remove all files that Oracle Universal Installer (OUI) created during the attempted installation.

1.  Run OUI to deinstall Oracle RAC.
2.  Manually remove the directory that was used as the Oracle home directory during the installation.
3.  Remove the following Windows Registry keys created by OUI during the previous installation attempt:
        HKEY_LOCAL_MACHINE\SOFTWARE\ODBC\ODBCINST.INI
        HKEY_LOCAL_MACHINE\SOFTWARE\ORACLE\KEY_ORACLE_HOME_NAME

After you have completed these steps, you can start the installation again.

**See Also:**

“Removing Oracle Real Application Clusters Software” in this guide for more information about removing Oracle RAC software.

**Parent topic:** [Removing Oracle RAC Software](removing-oracle-rac-software.md)
