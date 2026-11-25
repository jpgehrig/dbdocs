You must designate a group as the OSDBA for ASM (`asmdba`) group during installation. Members of this group are granted access privileges to Oracle Automatic Storage Management.

Create an OSDBA for ASM group using the group name `asmdba` unless a group with that name already exists:

    # /usr/sbin/groupadd -g 54327 asmdba

**Parent topic:** [Creating Operating System Privileges Groups](creating-operating-system-privileges-groups.md)
