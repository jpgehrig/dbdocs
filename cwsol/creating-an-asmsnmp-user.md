The `ASMSNMP` user is an Oracle ASM user with privileges to monitor Oracle ASM instances. You are prompted to provide a password for this user during installation.

In addition to the OSASM group, whose members are granted the SYSASM system privilege to administer Oracle ASM, Oracle recommends that you create a less privileged user, `ASMSNMP`, and grant that user SYSDBA privileges to monitor the Oracle ASM instance. Oracle Enterprise Manager uses the `ASMSNMP` user to monitor Oracle ASM status.

During installation, you are prompted to provide a password for the `ASMSNMP` user. You can create an operating system authenticated user, or you can create an Oracle Database user called `asmsnmp`. In either case, grant the user SYSDBA privileges.

**Parent topic:** [Oracle Installations with Standard and Job Role Separation Groups and Users](oracle-installations-with-standard-and-job-role-separation-groups-and-users.md)
