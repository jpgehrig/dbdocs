Create a standby Oracle Database on a remote host by duplicating an active Oracle Database.

- [Overview of Active Database Duplication](overview-of-active-database-duplication.md)
  Active database duplication does not require backups of the source database. It duplicates the live source database to the destination host by copying the database files over the network to the auxiliary instance. RMAN can copy the required files as image copies or backup sets.
- [Active Database Duplication Using Backup Sets](active-database-duplication-using-backup-sets.md)
  Using backup sets to perform active database duplication is also known as the pull-based method of active database duplication.
