## Configuring Oracle Components

Many Oracle products and options must be configured before you use them for the first time.

Before using individual Oracle products or options, refer to the appropriate manual in the product documentation library.

**Note:**

Perform postinstallation tasks only for the components that you intend to use.

- Windows Authentication No Longer Uses NTLM by Default
  For Microsoft Windows installations with `AUTHENTICATION_SERVICES=NTS`, in this Oracle Database release, the `SQLNET.NO_NTLM` parameter setting in the `sqlnet.ora` file defaults to `TRUE`, which can cause ORA-12638 errors.
- [Configuring Oracle Messaging Gateway](configuring-oracle-messaging-gateway.md)
  Oracle Messaging Gateway, an Oracle Database Advanced Queuing feature, requires additional configuration after you install Oracle Database if you plan to use Oracle Database Advanced Queuing.
- [Configuring the OraClrAgnt Service for Oracle Database Extensions for .NET](configuring-oraclragnt-service-for-oracle-db-extensions.md)
  Oracle Database Extensions for .NET depends on a Windows service to operate properly. This service is called the OraClrAgnt service, which can be accessed through the Service Control Panel, as `Oracle``ORACLE_HOME``ClrAgent`, where `ORACLE_HOME` represents an Oracle home name.
- [Configuring Oracle Net Services](configuring-oracle-net-services.md)
  Describes how to configure Oracle Net Services.
- [Installing Oracle Text Supplied Knowledge Bases](installing-oracle-text-supplied-knowledge-bases.md)
  An Oracle Text knowledge base is a hierarchical tree of concepts used for theme indexing, ABOUT queries, and deriving themes for document services.
- [Installing the Oracle Text Filtering Component](installing-oracle-text-filtering-component.md)
  Oracle Text Filtering Technology requires the Visual C++ libraries included in the Visual C++ Redistributable Package provided by Microsoft.
- [Configuring or Reinstalling Oracle XML DB](configuring-or-reinstalling-oracle-xml-db.md)
  Oracle XML DB is a component of the Oracle Database installation.
- [Configuring PL/SQL External Procedures](configuring-plsql-external-procedures.md)
  Configuring PL/SQL depends on the network configuration files used.
- [Configuring Shared Server Support](configuring-shared-server-support.md)
  The default setup for using the Shared Server mode depends on how the software has been installed.
- [Setting Credentials for the Job System to Work with Oracle Enterprise Manager](setting-credentials-for-job-system-to-work-with-oracle-enterprise-manager.md)
  Windows systems require that you set the correct credentials for the Jobs system to work properly in Oracle Enterprise Manager.
- [Configuring Oracle Database to Communicate with Oracle Automatic Storage Management](configuring-oracle-db-to-comm-with-oracle-asm.md)
  On Windows, Oracle Database installations that use Oracle Automatic Storage Management must use Windows native authentication.
- [Installing Oracle Database Examples](installing-oracle-db-examples.md)
  If you plan to use the following products or features, then download and install the products from the Oracle Database Examples media:
- [Creating the OraMTS Service for Microsoft Transaction Server](creating-oramts-service-for-microsoft-transaction-server.md)
  Oracle Services for Microsoft Transaction Server (OraMTS) permit Oracle databases to be used as resource managers in Microsoft application coordinated transactions.

**Parent topic:** [Oracle Database Postinstallation Tasks](oracle-database-postinstallation-tasks.md)

### Windows Authentication No Longer Uses NTLM by Default

For Microsoft Windows installations with `AUTHENTICATION_SERVICES=NTS`, in this Oracle Database release, the `SQLNET.NO_NTLM` parameter setting in the `sqlnet.ora` file defaults to `TRUE`, which can cause ORA-12638 errors.

Date: August 2023

In previous releases, the default for `AUTHENTICATION_SERVICES=NTS` was `FALSE`. `SQLNET.NO_NTLM` controls whether NTLM can be used with NTS authentication. A `TRUE` setting means that NTLM cannot be used in NTS authentication. Because NTLM does not normally provide mutual authentication and is hence less secure, a `TRUE` setting for `SQLNET.NO_NTLM` makes the database and client more secure.

The `SQLNET.NO_NTLM` parameter is used on both the server and the client. If you have upgraded a Microsoft Windows installation of Oracle Database, or upgraded a client in which `SQLNET.NO_NTLM` had not been set, then its default will be `TRUE`. In that case, when you have `SQLNET.AUTHENTICATION_SERVICES=NTS` in your `sqlnet.ora`, clients can encounter the error `ORA-12638: Credential retrieval failed`.

If you prefer to use NTLM authentication for certain clients, then set this parameter as required in client-side `sqlnet.ora` files:

    SQLNET.NO_NTLM=FALSE

You must include this setting on both the server and client, and this setting should be the same on both. Ideally, you should ensure that `SQLNET.NO_NTLM` is set to `TRUE`. However, if there is an authentication failure in `extproc`, a virtual account, or a local account on Windows, set the client `SQLNET.NO_NTLM` to `FALSE`, and then retry the login. If you change `SQLNET.NO_NTLM` on the server, then you must restart the database.

**Related Topics**

- [Upgrade Your Database Now - ORA-12638 on Windows only from Oracle 19.10.0 onwards](https://mikedietrichde.com/2021/03/10/ora-12638-on-windows-only-from-oracle-19-10-0-onwards/)
- [Windows : While Connect to Database Getting ORA-12638 After Applying Jan 2021 WINDBBP 19.10.0.0.210119 On Windows 64/32 Bit Database Client (Doc ID 2757734.1)](https://support.oracle.com/rs?type=doc&id=2757734.1)

**Parent topic:** Configuring Oracle Components
