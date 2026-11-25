## Default Share Configuration Requirement

The prerequisite checks during Oracle Database Client installation require that the system drive on your computer has default share configured on it.

Use the `net use` command to verify, for example:

    C:\> net use \\hostname\c$
    The command completed successfully

Ensure that the current user, the user in the Administrator group, has all the privileges on the default share.

**Parent topic:** [Oracle Database Client Preinstallation Tasks](oracle-database-client-preinstallation-tasks.md)
