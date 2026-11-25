This release includes Oracle Scheduler (the Scheduler), which provides enterprise scheduling functionality.

This release includes Oracle Scheduler (the Scheduler), which provides enterprise scheduling functionality. External jobs performed by the user are started using the `OracleJobScheduler``SID` service. This service is disabled by default. To use the external jobs functionality, the administrator must set the user name and password for the user account under which this service must run and enable the service.

ORADIM creates the Oracle Database service, Oracle VSS Writer service, and Oracle Scheduler service to run under the Oracle Home User account. If this account is a Windows Local User or a Windows Domain User Account, then ORADIM prompts for the password for that account and accepts the same through `stdin`. It is possible to specify both the Oracle Home User and its password using the `-RUNAS osusr[/ospass] `option to `oradim`. If the given `osusr` is different from the Oracle Home User, then Oracle Home User is used instead of `osusr` along with the given `ospass`. Restricting execution of external jobs to a low-privileged user prevents unauthorized database users from gaining operating system-level privileges, but it also places restrictions on the kinds of jobs that can be run. Jobs requiring a higher level of operating system privileges cannot be run by this mechanism.

Enabling and starting the `OracleJobScheduler``SID` service is required only for compatibility with Oracle Database 10g Release 1 and Release 2, for local external jobs that do not use credentials. This service is not required if all local external jobs use credentials. For improved security, Oracle recommends that all local external jobs use credentials.

**See Also:**

[Oracle Database Administrator's Guide](../admin/scheduling-jobs-with-oracle-scheduler.md)

**Parent topic:** [Postinstallation Configuration Tasks on Windows](postinstallation-configuration-tasks-on-windows.md)
