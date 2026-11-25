You must create at least one software owner user account the first time you install Oracle software on the system. Either use an existing Oracle software user account, or create an Oracle software owner user account for your installation.

To use an existing user account, obtain from you system administrator the name of an existing Oracle installation owner. Confirm that the existing owner is a member of the Oracle Inventory group.

For example if you know that the name of the Oracle Inventory group is `oinstall`, then an Oracle software owner should be listed as a member of `oinstall`.:

    $ grep "oinstall" /etc/group
    oinstall:x:54321:oracle

You can then use the ID command to verify that the Oracle installation owners you intend to use have the Oracle Inventory group as their primary group. For example:`$ id oracle`

    uid=54321(oracle) gid=54321(oinstall) groups=54321(oper),54322(dba)

After you create operating system groups, create or modify Oracle user accounts in accordance with your operating system authentication planning.

**Parent topic:** [Required Operating System Groups and Users](required-operating-system-groups-and-users.md)
