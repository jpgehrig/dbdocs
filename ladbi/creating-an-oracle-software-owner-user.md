## Creating an Oracle Software Owner User

If the Oracle software owner user (`oracle` or `grid`) does not exist, or if you require a new Oracle software owner user, then create it as described in this section.

The following example shows how to create the user `oracle` with the user ID 54321; with the primary group `oinstall`; and with secondary groups `dba`, `asmdba`, `backupdba`, `dgdba`, `kmdba`, and `racdba`:

    # /usr/sbin/useradd -u 54321 -g oinstall -G dba,asmdba,backupdba,dgdba,kmdba,racdba oracle

The following example shows how to create the user `grid` with the user ID 54331; with the primary group `oinstall`; and with secondary groups `asmadmin`, `asmdba`, `backupdba`, `dgdba`, `kmdba`, and `racdba`:

    # /usr/sbin/useradd -u 54331 -g oinstall -G asmadmin,asmdba,backupdba,dgdba,kmdba,racdba grid

You must note the user ID number for installation users, because you need it during preinstallation.

**Parent topic:** [Creating Operating System Oracle Installation User Accounts](creating-operating-system-oracle-installation-user-accounts.md)
