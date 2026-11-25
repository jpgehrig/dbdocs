If the Oracle software owner user (`oracle` ) does not exist, or if you require a new Oracle software owner user, then create it as described in this section.

The following example shows how to create the user `oracle` with the user ID 54321; with the primary group `oinstall`; and with secondary group `dba`.

    # /usr/sbin/useradd -u 54321 -g oinstall -G dba, oracle

You must note the user ID number for installation users, because you need it during preinstallation.

For Oracle Grid Infrastructure Installations, user IDs and group IDs must be identical on all candidate nodes.

**Parent topic:** [Creating Operating System Oracle Installation User Accounts](creating-operating-system-oracle-installation-user-accounts.md)
