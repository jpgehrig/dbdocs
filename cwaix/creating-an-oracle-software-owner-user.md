If the Oracle software owner user (`oracle` or `grid`) does not exist, or if you require a new Oracle software owner user, then create it as described in this section.

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
5.  Ensure that the Oracle software owner user (`oracle` or `grid`) has the capabilities `CAP_NUMA_ATTACH`, `CAP_BYPASS_RAC_VMM`, and `CAP_PROPAGATE`.
    1.  To check existing capabilities, enter the following command as `root`; in this example, the Oracle Database installation user account is `oracle`:
            # /usr/bin/lsuser -a capabilities oracle
    2.  To add capabilities, enter a command similar to the following:
            # /usr/bin/chuser
            capabilities=CAP_NUMA_ATTACH,CAP_BYPASS_RAC_VMM,CAP_PROPAGATE oracle

You must note the user ID number for installation users, because you need it during preinstallation.

**Note:**

On IBM AIX on POWER Systems (64-bit), Oracle Database software installations using an Active Directory (AD) account is not supported.

**Parent topic:** [Creating Operating System Oracle Installation User Accounts](creating-operating-system-oracle-installation-user-accounts.md)
