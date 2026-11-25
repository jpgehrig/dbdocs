You must designate a group as the OSASM group (`asmadmin`) during installation. Members of this group are granted the SYSASM system privileges to administer storage.

Create an OSASM group using the group name `asmadmin` unless a group with that name already exists:

    # groupadd -g 54329 asmadmin

The Oracle ASM instance is managed by a privileged role called SYSASM, which grants full access to Oracle ASM disk groups. Members of OSASM are granted the SYSASM role.

**Parent topic:** [Creating Operating System Privileges Groups](creating-operating-system-privileges-groups.md)
