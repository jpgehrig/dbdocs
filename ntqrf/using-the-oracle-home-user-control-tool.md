A new Windows tool, Oracle Home User Control, is a command-line tool that displays the Oracle Home User name associated with the current Oracle home and updates the password for the Windows services for the Oracle home.

The input password must match the password for the Windows User Account used as the Oracle Home User. So, first use Windows operating system tools to change the Windows password and then use this tool. This tool updates all Windows services used by Oracle to use the new password and updates it in the Oracle Cluster Registry wallet too, if one exists.

Installer also creates a shortcut Update Password for Oracle Home User which starts the tool.

The Oracle Home User Control tool accepts the new password at the tool's prompt for password entry and validates the password provided against the password of the Windows User Account. The tool terminates if password validation fails. Moreover, the user starting the `orahomeuserctl` command must have Administrator privileges. The command must be in the following format:

    orahomeuserctl list
    orahomeuserctl updpwd [-user username] [-host hostname1, hostname2, …] [-log logfilename]

For this command, note the following:

- `list:` This utility displays the Oracle Home User name associated with the Oracle home.

- `updpwd: `This utility prompts for a new password and updates the password for all Oracle Database services associated with the named Oracle Home User on the node. When `updpwd` is started on a node within an Oracle RAC installation, then the command first updates the Oracle Cluster Registry wallet with the new password, then updates all Oracle Database services associated with the user on all active nodes within a cluster. If there is no Oracle Cluster Registry Wallet, then the utility updates only all the Oracle Database services.

- `-user:` This option updates the passwords for all services owned by a specific user, or the password of the current Oracle Home User if no user is specified.

- `-host:` This option updates the passwords for all services belonging to the named Oracle Home User on the specified hosts. To update the password on a remote host, the user must be a Windows Domain User.

- `-log:` This option appends the time-stamped results of the password update action to the specified log file for every node and service name receiving the new password. The default log file name and location is `%ORACLE_HOME%\log\orahomeuserctl.log`.

**Parent topic:** [Database Tools on Windows](database-tools-on-windows.md)
