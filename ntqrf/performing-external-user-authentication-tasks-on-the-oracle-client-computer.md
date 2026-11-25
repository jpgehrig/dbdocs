Use this procedure to perform external user authentication tasks on the client computer.

Perform the following external user authentication tasks on the client computer:

1.  Ensure that parameter `SQLNET.AUTHENTICATN_SERVICES` in file `sqlnet.ora` contains `nts`.
2.  Use Oracle Net Configuration Assistant to configure a network connection from your client computer to the Windows server on which Oracle Database is installed.
3.  Start SQL\*Plus:
        C:\> sqlplus /NOLOG
4.  Connect to your Windows server:
        SQL> CONNECT /@connect_identifier

    where `connect_identifier` is the net service name for Oracle Database.

    Oracle Database searches the data dictionary for an automatic login user name corresponding to the Windows local or domain user name, verifies it, and enables connection as `xyzjones` or `xyzsales\jones`.
5.  Verify that you have connected to Oracle Database as domain user `jones` by viewing the roles assigned.
        SQL> SELECT * FROM USER_ROLE_PRIVS;

    which outputs for local user `jones`:

        USERNAME                       GRANTED_ROLE                   ADM DEF OS_
        ------------------------------ ------------------------------ --- --- ---
        XYZJONES                       DBA                            NO  YES NO
        1 row selected.

    or, for domain user `jones`:

        USERNAME                       GRANTED_ROLE                   ADM DEF OS_
        ------------------------------ ------------------------------ --- --- ---
        XYZSALES\JONES                 DBA                            NO  YES NO
        1 row selected.

    Because the Oracle Database user name is the whole name `xyzjones` or `xyzsales\jones`, each object created by `xyzjones` or `xyzsales\jones` (that is, table, view, index, and so on) is prefixed by this name. For another user to reference the table `shark` owned by `xyzjones`, for example, the user must enter:

        SQL> SELECT * FROM xyzjones.shark

    **Note:**

    Automatic authorization is supported for all Oracle Net protocols.

    **See Also:**

    [Oracle Database Net Services Administrator's Guide](../netag/managing-oracle-net-services.md)

**Related Topics**

- [Performing External User Authentication Tasks on the Oracle Database Server](performing-external-user-authentication-tasks-on-the-oracle-database-server.md)

**Parent topic:** [About Manually Creating an External Operating System User](about-manually-creating-an-external-operating-system-user.md)
