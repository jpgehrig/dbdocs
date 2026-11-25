The Windows native authentication adapter works with Windows authentication protocols to enable access to Oracle Database.

The NTS authentication adapter no longer supports the use of NTLM to authenticate Windows domain users. Thus the NTS cannot be used to authenticate users in old Windows NT domains or domains with old Windows NT domain controllers. However, local connections and Oracle Database services running as a Windows Local User continues to be authenticated using NTLM.

If you use the Windows Local User Account as the Oracle Home User for an Oracle Database home, then Windows Native Authentication (NTS) cannot be used for authenticating Windows domain users or users from remote computers.

Client server must not specify an authentication protocol while trying to connect to Oracle Database. Instead, Oracle Database determines the protocol to use which is completely transparent to the user. The only Oracle Database requirement is to ensure that the parameter `SQLNET.AUTHENTICATION_SERVICES` in client and database server contains `nts` in the following file:

    ORACLE_HOME\network\admin\sqlnet.ora

This is the default setting for both client computer and database server after installation.

In a typical installation, Oracle Database network includes client computers and database servers, and computers on this network may use different Oracle Database software releases on different domains of Windows operating systems. This combination of different releases means that the authentication protocol being used can vary.

**Related Topics**

- [About Configuring Oracle Database to Communicate with Oracle ASM](about-configuring-oracle-database-to-communicate-with-oracle-asm.md)

**See Also:**

Your operating system documentation for more information on authentication protocol

**Parent topic:** [Authenticating Database Users with Windows](authenticating-database-users-with-windows.md)
