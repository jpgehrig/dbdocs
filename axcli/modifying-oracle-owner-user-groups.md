If you have created an Oracle software installation owner account, but or it is not a member of the groups you want to designate as the OSDBA, OSOPER, or other system privileges group, then modify the group settings for that user before installation.

**Warning:**

Each Oracle software owner must be a member of the same central inventory group. Do not modify the primary group of an existing Oracle software owner account, or designate different groups as the OINSTALL group. If Oracle software owner accounts have different groups as their primary group, then you can corrupt the central inventory.

During installation, the user that is installing the software should have the OINSTALL group as its primary group, and it must be a member of the operating system groups appropriate for your installation. For example:

1.  Enter the following command:
        # smit security
2.  Choose the appropriate menu items to modify the Oracle installation owner user group.
3.  In the Primary GROUP field, specify the Oracle Inventory group. For example: `oinstall`.
4.  In the Group SET field, specify the required secondary groups. For example: `dba`.
5.  Press F10 to exit.

**Parent topic:** [Creating Operating System Oracle Installation User Accounts](creating-operating-system-oracle-installation-user-accounts.md)
