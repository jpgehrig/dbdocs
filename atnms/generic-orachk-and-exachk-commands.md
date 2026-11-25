List of command options common to Oracle ORAchk and Oracle EXAchk.

### Syntax

    [-a]
    [-v]
    [-debug]
    [-nodaemon]
    [-f]
    [-upgrade]
    [-noupgrade]
    [-testemail all | "NOTIFICATION_EMAIL=comma-delimited list of email addresses"]
    [-sendemail “NOTIFICATION_EMAIL=comma-delimited list of email addresses"]
    [-dbserial]
    [-dbparallel [n]]
    [-dbparallelmax]

### Parameters

Table A-1 Generic Commands

| Option                                                                              | Description                                                                                                                                                       |
|:------------------------------------------------------------------------------------|:------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `-a`                                                                                | Runs all checks, including the best practice checks and the recommended patch check. If you do not specify any options, then the tools run all checks by default. |
| `-v`                                                                                | Shows the version of Oracle ORAchk and Oracle EXAchk tools.                                                                                                       |
| `-debug`                                                                            | Runs in debug mode.<br>The generated `.zip` file contains a debug log and other files useful for Oracle Support.                                                  |
| `-nodaemon`                                                                         | Does not send commands to the daemon, usage is interactive.                                                                                                       |
| `-f`                                                                                | Runs Offline. The tools perform health checks on the data already collected from the system.                                                                      |
| `-upgrade`                                                                          | Forces an upgrade of the version of the tools being run.                                                                                                          |
| `-noupgrade`                                                                        | Does not prompt for an upgrade even if a later version is available under the location specified in the `RAT_UPGRADE_LOC` environment variable.                   |
| `-testemail all | "NOTIFICATION_EMAIL=``comma-delimited list of email addresses``"` | Sends a test email to validate email configuration.                                                                                                               |
| `-sendemail “NOTIFICATION_EMAIL=``comma-delimited list of email addresses``"`       | Specify a comma-delimited list of email addresses.<br>Emails the generated HTML report on completion to the specified email addresses.                            |
| `-dbserial`                                                                         | Runs the `SQL`, `SQL_COLLECT`, and `OS` health checks in serial.                                                                                                  |
| `-dbparallel [``n``]`                                                               | Runs the `SQL`, `SQL_COLLECT`, and `OS` health checks in parallel, using n number of child processes.<br>Default is 25% of CPUs.                                  |
| `-dbparallelmax`                                                                    | Runs the `SQL`, `SQL_COLLECT`, and `OS` health checks in parallel, using the maximum number of child processes.                                                   |

**Parent topic:** [Oracle ORAchk and Oracle EXAchk Command-Line Options](orachk-and-exachk-command-line-options.md)
