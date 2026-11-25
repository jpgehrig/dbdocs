You must designate a group as the OSRACDBA group during database installation. Members of this group are granted the SYSRAC privileges to perform day–to–day administration of Oracle databases on an Oracle RAC cluster.

Create the OSRACDBA group using the groups name `racdba` unless a group with that name already exists:

    # /usr/sbin/groupadd -g 54330 racdba

**Parent topic:** [Creating Operating System Privileges Groups](creating-operating-system-privileges-groups.md)
