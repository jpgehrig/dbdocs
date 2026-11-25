Use the Microsoft `Dsacls.exe` tool to set ACLs on directory objects.

The `Dsacls.exe` command-line tool displays and changes permissions (access control entries) in the Access Control List (ACL) of objects in Active Directory. This command-line tool is included with the support tools on the CD-ROM.

Examples:

To enable an anonymous generic read on the `orcl` service, run the following command:

    dsacls "CN=orcl,CN=OracleContext,OU=Example,O=Com" /G "anonymous logon":GR

To enable a generic read on the `orcl` service for the user `smith` in the EXAMPLE domain, run the following command:

    dsacls "CN=orcl,CN=OracleContext,OU=Example,O=Com" /G example\smith:GR

To disable an anonymous generic read on the `orcl` service, run the following command:

    dsacls "CN=orcl,CN=OracleContext,OU=Example,O=Com" /R "anonymous logon"

To disable a generic read on the `orcl` service for the user `smith` in the EXAMPLE domain, run the following command:

    dsacls "CN=orcl,CN=OracleContext,OU=Example,O=com" /R example\smith

**See Also:**

[`http://support.microsoft.com/kb/281146`](https://www.oracle.com/pls/topic/lookup?ctx=en/database/oracle/oracle-database/19/ntqrf&id=dsacls_exe) for a complete description of the `Dsacls.exe` tool

**Parent topic:** [Overview of Access Control List Management for Oracle Directory Objects](overview-of-access-control-list-management-for-oracle-directory-objects.md)
