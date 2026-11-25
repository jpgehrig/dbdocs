## Creating the OSBACKUPDBA Group for Database Installations

You must designate a group as the OSBACKUPDBA group during installation. Members of this group are granted the SYSBACKUP privileges to perform backup and recovery operations using RMAN or SQL\*Plus.

Create the OSBACKUPDBA group using the group name `backupdba`, unless a group with that name already exists:

    # /usr/sbin/groupadd -g 54324 backupdba

**Parent topic:** [Creating Operating System Privileges Groups](creating-operating-system-privileges-groups.md)
