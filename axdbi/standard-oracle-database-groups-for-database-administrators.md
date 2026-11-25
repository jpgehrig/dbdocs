Oracle Database has two standard administration groups: OSDBA, which is required, and OSOPER, which is optional.

- The OSDBA group (typically, `dba`)

  You must create this group the first time you install Oracle Database software on the system. This group identifies operating system user accounts that have database administrative privileges (the `SYSDBA` privilege).

  If you do not create separate OSDBA, OSOPER, and OSASM groups for the Oracle ASM instance, then operating system user accounts that have the `SYSOPER` and `SYSASM` privileges must be members of this group. The name used for this group in Oracle code examples is `dba`. If you do not designate a separate group as the OSASM group, then the OSDBA group you define is also by default the OSASM group.

- The OSOPER group for Oracle Database (typically, `oper`)

  OSOPER grants the OPERATOR privilege to start up and shut down the database (the `SYSOPER` privilege). By default, members of the OSDBA group have all privileges granted by the `SYSOPER` privilege.

**Parent topic:** [Oracle Installations with Standard and Job Role Separation Groups and Users](oracle-installations-with-standard-and-job-role-separation-groups-and-users.md)
