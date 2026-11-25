Oracle Database 19c enables users to change the ownership, permissions, or group membership of a file even while the file is open.

Since this release, the ASMCMD file access control commands, such as `chgrp`, `chmod`, and `chown,` can run even while the file is open. The SQL statements, such as `ALTER, DISKGROUP, MODIFY,and USERGROUP` commands have also been modified as these SQL statements provide support for these ASMCMD commands.

**See Also:**

[Oracle Automatic Storage Management Administrator's Guide](../ostmg/asm-files-directories-templates.md)

**Parent topic:** [Oracle Automatic Storage Management File Access Control](oracle-automatic-storage-management-file-access-control.md)
