Oracle Net Configuration Assistant enables you to configure client computers and Oracle Database to access a directory server.

When you choose directory access configuration from Oracle Net Configuration Assistant, it prompts you to specify a directory server type to use. When you select Active Directory as the directory server type, the Automatic Discovery of Directory Servers feature of Oracle Net Configuration Assistant automatically:

- Discovers the Active Directory server location

- Configures access to the Active Directory server

- Creates the Oracle context (also known as your domain)

**Note:**

Oracle Net Configuration Assistant does not configure `DIRECTORY_SERVERS` parameter in `ldap.ora`, in which case, clients automatically discover the Active Directory server for Net Naming.

If the Active Directory server already has an Oracle Context, then select the following nondefault option:

Select the directory server you want to use, and configure the directory server for Oracle usage. (Create or upgrade Oracle schema objects and Oracle Context as necessary.)

Oracle Net Configuration Assistant reports that the Oracle Context does not exist. Ignore this and choose to create the Oracle Context anyway. Directory access configuration completes without trying to re-create the existing Oracle Context.

**Note:**

Regardless of the Oracle Database Client and Oracle Database releases you are using, you must be running a Windows Server domain to take advantage of the automatic directory server discovery features of Oracle Net Configuration Assistant. Oracle Net Configuration Assistant does not automatically discover your directory server, and instead prompts you for additional information, such as the Active Directory location.

**See Also:**

[Oracle Database Net Services Administrator's Guide](../netag/part-II-config-and-admin-of-oracle-net-services.md) for configuration procedures

[Creating Oracle Schema Objects](creating-oracle-schema-objects.md)

[Overview of Requirements for Using Oracle Database with Active Directory](overview-of-requirements-for-using-oracle-database-with-active-directory.md)

[About Automatic Discovery of Directory Servers](about-automatic-discovery-of-directory-servers.md)

**Parent topic:** [Using Oracle Database with Microsoft Active Directory](using-oracle-database-with-microsoft-active-directory.md)
