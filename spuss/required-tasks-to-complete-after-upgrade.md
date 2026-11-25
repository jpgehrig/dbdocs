Review and complete these required tasks that are specified for your environment after you complete your upgrade.

You must complete these postupgrade tasks after you upgrade Oracle Database.

**Note:**

This list of required tasks is based on the assumption that you have used AutoUpgrade to perform the upgrade. AutoUpgrade completes automatically many tasks that otherwise you are required to perform manually.

- [Setting Environment Variables on Linux and Unix Systems After Manual Upgrades](setting-environment-variables-on-linux-and-unix-systems.md)
  Check that required operating system environment variables point to the directories of the new Oracle Database release.
- [Check PL/SQL Packages and Dependent Procedures](check-pl-sql-packages-and-dependent-procedures.md)
  It is possible that packages that you installed in the earlier release Oracle Database are not available in the new release, which can affect applications.
- [Upgrading Tables Dependent on Oracle-Maintained Types](upgrading-tables-dependent-on-oracle-maintained-types.md)
  Starting with Oracle Database 12c Release 2 (12.2) and later releases, you must manually upgrade user tables that depend on Oracle-Maintained types.
- [About Recovery Catalog Upgrade After Upgrading Oracle Database](about-recovery-catalog-upgrade-after-upgrading-oracle-db.md)
  If you use a version of the recovery catalog schema that is older than that required by the RMAN client, then you must upgrade it.
- [Install Oracle Text Supplied Knowledge Bases After Upgrading Oracle Database](install-oracle-text-supplied-knowledge-bases.md)
  After an Oracle Database upgrade, all user extensions to the Oracle Text supplied knowledge bases must be regenerated.
- [Update Oracle Application Express Configuration After Upgrading Oracle Database](update-oracle-application-express-configuration.md)
  Oracle Application Express affects upgrade procedures, depending on the Oracle Application Express release and your database installation type.
- [Configure Access Control Lists (ACLs) to External Network Services](configure-acls-to-external-network-services.md)
  Oracle Database 12c and later releases include fine-grained access control to the `UTL_TCP`, `UTL_SMTP`, `UTL_MAIL`, `UTL_HTTP`, or `UTL_INADDR` packages.
- [Check for the SQLNET.ALLOWED_LOGON_VERSION Parameter Behavior](check-for-sqlnet-allowed-logon-version-parameter-behavior.md)
  Connections to Oracle Database from clients earlier than release 10g fail with the error `ORA-28040: No matching authentication protocol`.

**Parent topic:** [Post-Upgrade Tasks for Oracle Database](post-upgrde-tasks.md)
