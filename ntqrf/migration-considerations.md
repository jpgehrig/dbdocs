While upgrading an ASM disk group from Oracle Database 11g to Oracle Database 19c on Windows platforms, all the current files on the disk group are shown as being accessible to all users.

Thus, a user with `SYSASM` privileges must modify the user ownership, group membership, and permissions of the current files accordingly, so that the files are owned by their respective database users only.

**Parent topic:** [Overview of Database Migration from a 32-Bit Windows Computer](overview-of-database-migration-from-a-32-bit-windows-computer.md)
