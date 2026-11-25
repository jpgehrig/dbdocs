## Creating the OSDBA for ASM Group

You must designate a group as the OSDBA for ASM (`asmdba`) group during installation. Members of this group are also allowed to access the Oracle Automatic Storage Management (Oracle ASM) disk devices.

The Oracle ASM disk devices should be owned by this group.

Create an OSDBA for ASM group using the group name `asmdba` unless a group with that name already exists:

    # /usr/sbin/groupadd -g 54327 asmdba

**Parent topic:** [Creating Operating System Privileges Groups](creating-operating-system-privileges-groups.md)
