## Creating the OSKMDBA Group for Database Installations

You must designate a group as the OSKMDBA group during installation. Members of this group are granted the SYSKM privileges to perform Transparent Data Encryption keystore operations.

If you want a separate group for Transparent Data Encryption, then create the OSKMDBA group using the group name `kmdba` unless a group with that name already exists:

    # /usr/sbin/groupadd -g 54326 kmdba

**Parent topic:** [Creating Operating System Privileges Groups](creating-operating-system-privileges-groups.md)
