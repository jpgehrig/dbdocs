You must designate a group as the OSDGDBA group during installation. Members of this group are granted the SYSDG privileges to perform Data Guard operations.

Create the OSDGDBA group using the group name `dgdba,` unless a group with that name already exists:

    # /usr/sbin/groupadd -g 54325 dgdba

**Parent topic:** [Creating Operating System Privileges Groups](creating-operating-system-privileges-groups.md)
