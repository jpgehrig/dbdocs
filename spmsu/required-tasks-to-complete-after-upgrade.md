Review and complete these required tasks that are specified for your environment after you complete your upgrade.

You must complete these postupgrade tasks after you upgrade Oracle Database. You must complete these tasks both when you perform the upgrade manually, and when you upgrade by using Database Upgrade Assistant (DBUA).

- [Setting Environment Variables on Linux and Unix Systems After Manual Upgrades](setting-environment-variables-on-linux-and-unix-systems.md)
  If you performed a manual upgrade of Oracle Database, then you must ensure that the required operating system environment variables point to the directories of the new Oracle Database release.
- [Recompiling All Invalid Objects](recompiling-all-invalid-objects.md)
  Oracle recommends that you run the `utlrp.sql` script after you install, patch, or upgrade a database, to identify and recompile invalid objects.
- [Track Invalid Object Recompilation Progress](track-invalid-object-recompilation-progress.md)
  Use these SQL queries to track the progress of `utlrp.sql` script recompilation of invalid objects.
- [Running OPatch Commands After Upgrading Oracle Database](running-opatch-commands-after-upgrading-oracle-database.md)
  After you upgrade Oracle Database, you must run OPatch commands from the new Oracle home.
- [Setting oratab and Scripts to Point to the New Oracle Location After Upgrading Oracle Database](setting-oratab-and-scripts-to-point-to-new-oracle-location.md)
  You must set scripts to point to the new Oracle home location.
- [Check PL/SQL Packages and Dependent Procedures](check-pl-sql-packages-and-dependent-procedures.md)
  It is possible that packages that you installed in the earlier release Oracle Database are not available in the new release, which cam affect applications.
- [Upgrading Tables Dependent on Oracle-Maintained Types](upgrading-tables-dependent-on-oracle-maintained-types.md)
  Starting with Oracle Database 12c Release 2 (12.2) and later releases, you must manually upgrade user tables that depend on Oracle-Maintained types.
- [Enabling the New Extended Data Type Capability](enabling-the-new-extended-data-type-capability.md)
  Enabling a system to take advantage of the new extended data types requires specific upgrade actions.
- [Adjusting Minimum and Maximum for Parallel Execution Servers](adjusting-min-and-max-for-parallel-execution-servers.md)
  Depending on your environment, you can reduce the default setting of the PARALLEL_MIN_SERVERS parameter.
- [About Recovery Catalog Upgrade After Upgrading Oracle Database](about-recovery-catalog-upgrade-after-upgrading-oracle-db.md)
  If you use a version of the recovery catalog schema that is older than that required by the RMAN client, then you must upgrade it.
- [Upgrading the Time Zone File Version After Upgrading Oracle Database](upgrading-time-zone-file-version-after-upgrading-oracle-db.md)
  If the Pre-Upgrade Information Tool instructs you to upgrade the time zone files after completing the database upgrade, then use the `DBMS_DST` PL/SQL package to upgrade the time zone file.
- [Upgrading Statistics Tables Created by the DBMS_STATS Package After Upgrading Oracle Database](upgrading-statistics-tables-created-by-dbms-stats-package.md)
  If you created statistics tables using the `DBMS_STATS.CREATE_STAT_TABLE` procedure, then upgrade these tables by running `DBMS_STATS.UPGRADE_STAT_TABLE`.
- [Upgrading Externally Authenticated SSL Users After Upgrading Oracle Database](upgrading-externally-authenticated-ssl-users.md)
  If you are upgrading from Oracle9i Release 2 (9.2) or Oracle Database 10g Release 1 (10.1), and you are using externally authenticated SSL users, then you must run the SSL external users conversion (`extusrupgrade`) script to upgrade those users.
- [Configuring the FTP and HTTP Ports and HTTP Authentication for Oracle XML DB](configuring-ftp-and-http-ports-andhttp-authentication.md)
  Oracle Database Configuration Assistant (DBCA) does not configure ports for Oracle XML DB on Oracle Database 12c and later release upgrades use digest authentication.
- [Install Oracle Text Supplied Knowledge Bases After Upgrading Oracle Database](install-oracle-text-supplied-knowledge-bases.md)
  After an Oracle Database upgrade, all user extensions to the Oracle Text supplied knowledge bases must be regenerated.
- [Update Oracle Application Express Configuration After Upgrading Oracle Database](update-oracle-application-express-configuration.md)
  Oracle Application Express affects upgrade procedures, depending on the Oracle Application Express release and your database installation type.
- [Configure Access Control Lists (ACLs) to External Network Services](configure-acls-to-external-network-services.md)
  Oracle Database 12c and later releases include fine-grained access control to the `UTL_TCP`, `UTL_SMTP`, `UTL_MAIL`, `UTL_HTTP`, or `UTL_INADDR` packages.
- [Check for the SQLNET.ALLOWED_LOGON_VERSION Parameter Behavior](check-for-sqlnet-allowed-logon-version-parameter-behavior.md)
  Connections to Oracle Database from clients earlier than release 10g fail with the error `ORA-28040: No matching authentication protocol`.

**Parent topic:** [Post-Upgrade Tasks for Oracle Database](post-upgrde-tasks.md)
