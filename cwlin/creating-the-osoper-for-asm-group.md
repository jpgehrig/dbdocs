## Creating the OSOPER for ASM Group

You can choose to designate a group as the OSOPER for ASM group (`asmoper`) during installation. Members of this group are granted startup and shutdown privileges to Oracle Automatic Storage Management.

If you want to create an OSOPER for ASM group, use the group name `asmoper` unless a group with that name already exists:

    # /usr/sbin/groupadd -g 54328 asmoper

**Parent topic:** [Creating Operating System Privileges Groups](creating-operating-system-privileges-groups.md)
