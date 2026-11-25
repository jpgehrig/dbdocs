## Default Share Configuration Requirement

The prerequisite checks during Oracle Database installation require that the system drive on your computer has default share configured on it.

Use the `net use` command to verify, for example:

    C:\> net use \\hostname\c$
    The command completed successfully

Ensure that the current user, the user in the Administrator group, has all the privileges on the default share.

**Parent topic:** [Windows Certification and Web Browser Support](windows-certification-and-web-browser-support.md)
