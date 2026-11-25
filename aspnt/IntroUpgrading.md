Administrators who wish to upgrade an older instance of Oracle Providers for ASP.NET to a newer version must upgrade both the Oracle Client and database schema. Oracle does not support using one Oracle Providers for ASP.NET client version, say 11.2, with another Oracle Providers for ASP.NET database schema version, say 12.1. The database version itself does not need to be upgraded, only the ASP.NET provider schema does. Both the schema and client providers must be the same version.

The following list discusses upgrading the client and database schema:

- Oracle Client Upgrade:

  When installing the latest Oracle Providers for ASP.NET version, the `machine.config` file is no longer automatically updated by default so that Web applications are directed to use the recently installed version. If there are applications that use the newly installed Oracle ASP.NET providers, then administrators must update the appropriate .NET configuration file.

- Database Schema Upgrade:

  Administrators need to execute the new version's Oracle Providers for ASP.NET SQL scripts on the same schema where the older Oracle Providers for ASP.NET schema exists. The scripts are designed to upgrade older schemas or create the schema if none exists. The scripts preserve existing Oracle Providers for ASP.NET data such that no data is lost.

If the database server itself is being upgraded, then administrators can use standard Oracle upgrade procedures with Oracle Providers for ASP.NET data. Data is preserved when performing the upgrade. Encrypted data remains encrypted and usable after the upgrade.

### Coexistence of Multiple Oracle Providers for ASP.NET Versions

If there are multiple ASP.NET applications using a single Web server or a single Oracle Database, then it is not necessary for all of them to use the same Oracle Providers for ASP.NET version. For example, some of the applications may use Oracle Providers for ASP.NET 12.1, and other applications may use the 11.2 version. Individual `web.config` files are used to determine as to which Oracle Providers for ASP.NET version to use for each application.

Each Oracle Providers for ASP.NET version must have a database schema specific to its version. For example, all Oracle Providers for ASP.NET 11.2 applications must be able to access at least one schema built using the 11.2 SQL scripts. These 11.2 provider applications can all share one schema, but they cannot use an 12.1 schema. When using multiple Oracle Providers for ASP.NET versions to access the same database, administrators can create separate schemas for each Oracle Providers for ASP.NET version.
