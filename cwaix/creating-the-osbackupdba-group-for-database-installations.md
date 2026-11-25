You must designate a group as the OSBACKUPDBA group during installation. Members of this group are granted the SYSBACKUP privileges to perform backup and recovery operations using RMAN or SQL Plus.

Create the OSBACKUPDBA group using the group name `backupdba`, unless a group with that name already exists:

1.   Enter the following command:
        # smit security
2.  Choose the appropriate menu items to create the `backupdba` group.
3.  Press F10 to exit.

**Note:**

On IBM AIX on POWER Systems (64-bit), the user and group name length limit parameter default value is 9 characters. Refer your operating system documentation, to increase the user and group name length limit.

**Parent topic:** [Creating Operating System Privileges Groups](creating-operating-system-privileges-groups.md)
