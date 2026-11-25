If the Oracle software owner user (`oracle` ) does not exist, or if you require a new Oracle software owner user, then create it as described in this section.

1.  Enter the following command:
        # smit security
2.  Choose the appropriate menu items to create the `oracle` user, specifying the following information:
    - In the Primary GROUP field, specify the Oracle Inventory group, for example `oinstall`.
    - In the Group SET field, specify the OSDBA group and if required, the OSOPER group. For example `dba`, `asmdba`, or `oper`.

    **Note:**

    The UID for the `oracle` user must be less than 65536.
3.   Press F10 to exit.
4.  Set the password of the `oracle` user:
        # passwd oracle

You must note the user ID number for installation users, because you need it during preinstallation.

**Parent topic:** [Creating Operating System Oracle Installation User Accounts](creating-operating-system-oracle-installation-user-accounts.md)
