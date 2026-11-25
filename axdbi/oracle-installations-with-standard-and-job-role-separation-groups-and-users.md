A job role separation configuration of Oracle Database and Oracle ASM is a configuration with groups and users to provide separate groups for operating system authentication.

Review the following sections to understand more about a Job Role Separation deployment:

- [About Oracle Installations with Job Role Separation](about-oracle-installations-with-job-role-separation.md)
  Job role separation requires that you create different operating system groups for each set of system privileges that you grant through operating system authorization.
- [Standard Oracle Database Groups for Database Administrators](standard-oracle-database-groups-for-database-administrators.md)
  Oracle Database has two standard administration groups: OSDBA, which is required, and OSOPER, which is optional.
- [Extended Oracle Database Groups for Job Role Separation](extended-oracle-database-groups-for-job-role-separation.md)
  Oracle Database provides an extended set of database groups to grant task-specific system privileges for database administration.
- [Creating an ASMSNMP User](creating-an-asmsnmp-user.md)
  The `ASMSNMP` user is an Oracle ASM user with privileges to monitor Oracle ASM instances. You are prompted to provide a password for this user during installation.
- [Oracle Automatic Storage Management Groups for Job Role Separation](oracle-automatic-storage-management-groups-for-job-role-separation.md)
  Oracle Grid Infrastructure operating system groups provide their members task-specific system privileges to access and to administer Oracle Automatic Storage Management.

**Parent topic:** [Configuring Users, Groups and Environments for Oracle Grid Infrastructure and Oracle Database](configuring-users-groups-and-environments-for-oracle-grid-infrastructure-and-oracle-database.md)
