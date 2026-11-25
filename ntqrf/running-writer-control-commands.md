The writer control commands are applicable to all the restored components during the postrestore phase.

The format is as follows:

    OP1=CMD1, OP2=CMD2, . . .

Run the commands in the following sequence:

1.  `POST_WTRCMD=NORECOVER`
    This command instructs the writer to not perform any postrestore recovery activities defined in the default postrestore recovery operations for the restored component. Otherwise, the postrestore phase default actions are performed.
2.  `POST_RMANCMD=``cmdstr`
    This command instructs the writer to run specific RMAN commands, instead of the default operations, after the current operation.
3.  `PRE_SQLCMD=``cmdstr`
    This command instructs the writer to run specific SQL commands in `OnPrepareBackup` or `OnPreRestore` callback, before performing any other validations. The command is used to stop MRP on a standby database before VSS snapshot is created or to shut down database instance creating a cold backup of the database.
4.  `POST_SQLCMD=``cmdstr`
    This command instructs the writer to run specific SQL commands in PostSnapshot or PostRestore callback. This command is used to restart MRP on standby database after VSS snapshot is created or to restart the database instance after the cold backup of the database is performed.

**Parent topic:** [About Integrating VSS with Third-Party Requester Applications](about-integrating-vss-with-third-party-requester-applications.md)
