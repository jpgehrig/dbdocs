## Changing the Oracle Home User Password

Oracle Home User Control is a command-line utility that allows an administrator to update the password for an Oracle Home User.

This tool updates the password for Windows services in the Oracle home. The input password must match the password for the Windows User Account used as the Oracle Home User. So, first use the Windows operating system tools to change the Windows password and then use this tool to update the Windows services in the Oracle home to use the same password.

**Note:**

You must have the Administrator privileges to run this Oracle Home User Control utility.

Syntax Overview:

The following is the command syntax:

    orahomeuserctl list | updpwd [-user username] [-host hostname1, hostname2, . . .] [-log logfilename]

where:

- `orahomeuserctl` is used to display the Oracle Home User name associated with the current Oracle home or to update the Oracle Home User password.

- `list` displays the Oracle Home User name associated with the current Oracle home.

- `updpwd` prompts for the new password and updates the password for the named Oracle Service User. The following are the options for `updpwd`:

  - `-user` `username`

    This option determines the Oracle Home User name. If this option is not present, then the user name associated with the current Oracle home is used. If the named user, be it the `username` or user of the current Oracle home, is an MSA or Windows Built-in account, then an error message is displayed and the command is terminated.

  - `-host` `hostname1`, `hostname2`,. . .

    When this option is present, the utility updates the passwords for all the services belonging to the named Oracle Home User on the specified hosts. Otherwise, the Oracle Home User Control utility updates the passwords for all the services belonging to the named Oracle Home User on a specified host with single instance installation, or updates the passwords for all services belonging to the named Oracle Home User on all the specified hosts.

    When the update completes, the utility displays the number of successful updates and any services that failed to update with the new password.

  - `-log` `logfilename`

    This option adds the password update operation results to a log file for every service name receiving the new password. By default, the log files are located in the `ORACLE_HOME``\log` directory. If `logfilename` specifies only a file name, then the log is stored in the named file in the default directory. However, if the `logfilename` contains a path, then that path is used without modification.

**Parent topic:** [Oracle Database Postinstallation Tasks](oracle-database-postinstallation-tasks.md)
