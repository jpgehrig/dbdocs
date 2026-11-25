## Identifying an Oracle Software Owner User Account

You must create at least one software owner user account the first time you install Oracle software on the system. Either use an existing Oracle software user account, or create an Oracle software owner user account for your installation.

To use an existing user account, obtain the name of an existing Oracle installation owner from your system administrator. Confirm that the existing owner is a member of the Oracle Inventory group.

For example, if you know that the name of the Oracle Inventory group is `oinstall`, then an Oracle software owner should be listed as a member of `oinstall`:

    $ grep "oinstall" /etc/group
    oinstall:x:54321:grid,oracle

You can then use the ID command to verify that the Oracle installation owners you intend to use have the Oracle Inventory group as their primary group. For example:

    $ id oracle
    uid=54321(oracle) gid=54321(oinstall) groups=54321(oinstall),54322(dba),
    54323(oper),54324(backupdba),54325(dgdba),54326(kmdba),54327(asmdba),54330(racdba)

    $ id grid
    uid=54331(grid) gid=54321(oinstall) groups=54321(oinstall),
    54327(asmdba),54328(asmoper),54329(asmadmin),54330(racdba)

**Note:**

For Oracle Restart installations, to successfully install Oracle Database, ensure that the `grid` user is a member of the `racdba` group.

After you create operating system groups, create or modify Oracle user accounts in accordance with your operating system authentication planning.

**Parent topic:** [Creating Groups, Users and Paths for Oracle Grid Infrastructure](creating-users-groups-paths-for-grid-infrastructure.md)
