The identity of an Oracle ASM user can be changed from one operating system user to another operating system user.

It enables end users to change the identity of an Oracle ASM user without having to delete and re-create the user, which requires dropping all the files a user owns. This feature improves the manageability of Oracle ASM users and the files they own. The SQL Statements `ALTER, DISKGROUP, REPLACE, USER`, and a new ASMCMD command (`rpusr`) have been added to support user replacement in a disk group.

**See Also:**

[Oracle Automatic Storage Management Administrator's Guide](../ostmg/admin-asm-diskgroups.md)

**Parent topic:** [Oracle Automatic Storage Management File Access Control](oracle-automatic-storage-management-file-access-control.md)
