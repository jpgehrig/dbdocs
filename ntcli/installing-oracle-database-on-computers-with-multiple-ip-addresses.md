## Installing Oracle Database on Computers with Multiple IP Addresses

Use this procedure to set the `ORACLE_HOSTNAME` environment variable.

Clients must be able to access the computer using its host name, or using aliases for its host name. To check access, ping the host name from the client computers using the short name (host name only) and the fully qualified domain name (FQDN, host name and domain name). Both must work.

1.  Display System in the Windows Control Panel.
2.  In the System Properties dialog box, click Advanced.
3.  In the Advanced tab, click Environment Variables.
4.  In the Environment Variables dialog box, under System Variables, click New.
5.  In the New System Variable dialog box, enter the following information:
    - Variable name: `ORACLE_HOSTNAME`

    - Variable value: The host name of the computer to use.
6.  Click OK, then in the Environment Variables dialog box, click OK.
7.  Click OK in the Environment Variables dialog box, then in the System Properties dialog box, click OK.

**Parent topic:** [Configuring Networks for Oracle Database](configuring-networks-for-oracle-database.md)
