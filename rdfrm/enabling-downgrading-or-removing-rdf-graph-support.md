## A Enabling, Downgrading, or Removing RDF Semantic Graph Support

You must perform certain steps before you can use any types, synonyms, or PL/SQL packages related to RDF Semantic Graph support in the current Oracle Database release.

You must run one or more scripts, and you must ensure that Spatial and Graph is installed and the Partitioning option is enabled. These requirements are explained in Enabling RDF Semantic Graph Support and its related subtopics.

This appendix also describes the steps if, after enabling RDF Semantic Graph support, you need to do any of the following:

- Downgrade the RDF Semantic Graph support to that provided with a previous Oracle Database release, as explained in Downgrading RDF Semantic Graph Support to a Previous Release.

- Remove all support for RDF Semantic Graph from the database, as explained in Removing RDF Semantic Graph Support.

<!-- -->

- Enabling RDF Semantic Graph Support
  Before you can use any types, synonyms, or PL/SQL packages related to RDF Semantic Graph support in the current Oracle Database release, you must either install the capabilities in a new Oracle Database installation or upgrade the capabilities from a previous release.
- Downgrading RDF Semantic Graph Support to a Previous Release
  You can downgrade the RDF Semantic Graph support, in conjunction with an Oracle Database downgrade to Release 12.1.
- Removing RDF Semantic Graph Support
  You can remove the RDF Semantic Graph support from the database.

### A.1 Enabling RDF Semantic Graph Support

Before you can use any types, synonyms, or PL/SQL packages related to RDF Semantic Graph support in the current Oracle Database release, you must either install the capabilities in a new Oracle Database installation or upgrade the capabilities from a previous release.

Install of RDF Semantic Graph support is included in install of Spatial and Graph. So you must ensure that Spatial and Graph is installed. In addition, Partitioning must be enabled. Restricted use of Partitioning is allowed free of charge for supporting Graph feature of Oracle Database. See [Restricted Use Licenses](../dblic/Licensing-Information.md) for more information.

- Enabling RDF Semantic Graph Support in a New Database Installation
- Upgrading RDF Semantic Graph Support from Release 11.1, 11.2, or 12.1
- Workspace Manager and Virtual Private Database Desupport

**Parent topic:** Enabling, Downgrading, or Removing RDF Semantic Graph Support

#### A.1.1 Enabling RDF Semantic Graph Support in a New Database Installation

RDF Semantic Graph is automatically enabled when Spatial and Graph Release 12.2 or later is installed. See [Manually Installing Spatial and Graph](../spatl/spatial-install-migrate-upgrade.md) if you do not have Spatial and Graph installed by default at the time of Oracle Database installation.

If RDF Semantic Graph was enabled successfully, a row with the following column values will exist in the MDSYS.RDF_PARAMETER table:

- NAMESPACE: `MDSYS`

- ATTRIBUTE: `SEM_VERSION`

- VALUE: (string starting with `12.2`)

- DESCRIPTION: `VALID`

##### Identifying Oracle Database Version

The full version of the database can be determined by querying `V$VERSION`. See [V\$VERSION](../refrn/V-VERSION.md) in Oracle Database Reference for more information.

For example:

    SQL> SELECT banner_full FROM V$VERSION;

On execution, the query may produce an output similar to:

`Oracle Database 19c Enterprise Edition Release 19.0.0.0.0 - Production Version 19.13.0.1.0`

In the preceding query output, `19.13.0.1.0` represents the full version of the database and `.13` is the release update version of Oracle Database 19c.

It is useful to know the `.x` release update version of your 19c database when using tools like SQL Developer. See [Creating an RDF Semantic Network Using SQL Developer](rdf-support-sql-developer.md) for more information.

**Parent topic:** Enabling RDF Semantic Graph Support

#### A.1.2 Upgrading RDF Semantic Graph Support from Release 11.1, 11.2, or 12.1

If you are upgrading from Oracle Database Release 11.1 or 11.2 that includes the semantic technologies support, the semantic technologies support is automatically upgraded to Release 12.1 or later when the database is upgraded.

However, you may also need to migrate RDF data if you have an existing Release 11.1 or 11.2 RDF network containing triples that include typed literal values of type xsd:float, xsd:double, xsd:boolean, or xsd:time.

To check if you need to migrate RDF data, connect to the database as a user with DBA privileges and query the MDSYS.RDF_PARAMETER table, as follows:

    SELECT namespace, attribute, value FROM mdsys.rdf_parameter
      WHERE namespace='MDSYS'
      AND attribute IN ('FLOAT_DOUBLE_DECIMAL',
                        'XSD_TIME', 'XSD_BOOLEAN',
                        'DATA_CONVERSION_CHECK');

If the FLOAT_DOUBLE_DECIMAL, XSD_TIME, or XSD_BOOLEAN attributes have the string value `INVALID` or if the DATA_CONVERSION_CHECK attribute has the string value `FAILED_UNABLE_TO_LOCK_APPLICATION_TABLES`, `FAILED_INSUFFICIENT_WORKSPACE_PRIVILEGES`, or `FAILED_OLS_POLICIES_ARE_ENABLED`, you need to migrate RDF data.

However, if the FLOAT_DOUBLE_DECIMAL, XSD_TIME, and XSD_BOOLEAN attributes do not exist or have the string value `VALID` and if the DATA_CONVERSION_CHECK attribute does not exist, you do not need to migrate RDF data. However, if your semantic network may have any empty RDF literals, see Handling of Empty RDF Literals; and if you choose to migrate existing empty literals to the new format, follow the steps in this section.

To migrate RDF data, follow these steps:

1.  Connect to the database as the SYSTEM (not SYS .. AS SYSDBA) user or another non-SYS user with the DBA role, and enter: `SET CURRENT_SCHEMA=MDSYS`

2.  Ensure that the user MDSYS has the following privileges:

    - INSERT privilege on all application tables in the semantic network

    - ALTER ANY INDEX privilege (optional: only necessary if Semantic Indexing for Documents is being used)

    - ACCESS privilege for any workspace in which version-enabled application tables have been modified (optional: only necessary if Workspace Manager is being used for RDF data)

3.  Ensure that any OLS policies for RDF data are temporarily disabled (optional: only necessary if OLS for RDF Data is being used). OLS policies can be re-enabled after running convert_old_rdf_data.

4.  Start SQL\*Plus. If you want to migrate the RDF data without converting existing empty literals to the new format (see Handling of Empty RDF Literals), enter the following statement:

        EXECUTE sdo_rdf_internal.convert_old_rdf_data;

    If you want to migrate the RDF data and also convert existing empty literals to the new format, call `convert_old_rdf_data` with the `flags` parameter set to `'CONVERT_ORARDF_NULL'`. In addition, you can use an optional `tablespace_name` parameter to specify the tablespace to use when creating intermediate tables during data migration. For example, the following statement migrates old semantic data, converts existing `"orardf:null "` values to "", and uses the MY_TBS tablespace for any intermediate tables:

        EXECUTE sdo_rdf_internal.convert_old_rdf_data(
          flags=>'CONVERT_ORARDF_NULL',
          tablespace_name=>'MY_TBS');

    The `sdo_rdf_internal.convert_old_rdf_data` procedure may take a significant amount of time to run if the semantic network contains many triples that are using (or affected by use of) xsd:float, xsd:double, xsd:time, or xsd:boolean typed literals.

5.  Connect to the database as the SYS user with SYSDBA privileges (SYS AS SYSDBA, and enter the SYS account password when prompted). Then enter the following statement:

    - Linux: `@$ORACLE_HOME/md/admin/semrelod.sql`

    - Windows: `@%ORACLE_HOME%\md\admin\semrelod.sql`

**Note:**

You may encounter the ORA-00904 (invalid identifier) error when executing a SEM_MATCH query if the `sdo_rdf_internal.convert_old_rdf_data` procedure and the `semrelod.sql` script were not run after the upgrade to Release 12.1 or later.

- Required Data Migration After Upgrade
- Handling of Empty RDF Literals

**Parent topic:** Enabling RDF Semantic Graph Support

##### A.1.2.1 Required Data Migration After Upgrade

After the database upgrade completes, if you have existing RDF data from a previous release, you must migrate the RDF data. If you do not perform the data migration, you will encounter the following error when running SEM_MATCH queries:

    ORA-20000:  RDF_VALUE$ Table needs data migration with SEM_APIS.MIGRATE_DATA_TO_CURRENT

Columns were added to the MDSYS.RDF_VALUE\$ table in Release 12.2 (see [Enhanced RDF ORDER BY Query Processing](rdf-semantic-graph-overview.md)). These columns must be populated after upgrading an existing RDF network. The need for migration will be noted with the following row in the MDSYS.RDF_PARAMETER table:

- NAMESPACE: `MDSYS`

- ATTRIBUTE: `RDF_VALUE$`

- VALUE: `INVALID_ORDER_COLUMNS`

- DESCRIPTION: `RDF_VALUE$ Table needs data migration with SEM_APIS.MIGRATE_DATA_TO_CURRENT`

If migration is needed, the RDF Semantic Graph installation will initially be marked as `INVALD`, which is signified with the following row in MDSYS.RDF_PARAMETER:

- NAMESPACE: `MDSYS`

- ATTRIBUTE: `SEM_VERSION`

- VALUE: (string starting with `12.2`)

- DESCRIPTION: `INVALID`

To perform data migration by populating new MDSYS.RDF_VALUE\$ columns, follow these steps:

1.  1\. Connect to the database as the SYSTEM (not SYS .. AS SYSDBA) user or as another non-SYS user with the DBA role.

2.  Run the following statement:

        EXECUTE sem_apis.migrate_data_to_current;

If data migration was successful, the INVALID_ORDER_COLUMNS row will be removed from MDSYS.RDF_PARAMETER and the SEM_VERSION row will have a DESCRIPTION value of `VALID`.

Moreover, additional data migration may be required if you are upgrading an existing Release 11.1 or 11.2 RDF network containing triples that include typed literal values of type xsd:float, xsd:double, xsd:boolean, or xsd:time.

To check if you need to perform this additional RDF data migration, connect to the database as a user with DBA privileges and query the MDSYS.RDF_PARAMETER table, as follows:

    SELECT namespace, attribute, value FROM mdsys.rdf_parameter
      WHERE namespace='MDSYS'
      AND attribute IN ('FLOAT_DOUBLE_DECIMAL',
                        'XSD_TIME', 'XSD_BOOLEAN',
                        'DATA_CONVERSION_CHECK');

If the FLOAT_DOUBLE_DECIMAL, XSD_TIME, or XSD_BOOLEAN attributes have the string value `INVALID` or if the DATA_CONVERSION_CHECK attribute has the string value `FAILED_UNABLE_TO_LOCK_APPLICATION_TABLES`, `FAILED_INSUFFICIENT_WORKSPACE_PRIVILEGES`, or `FAILED_OLS_POLICIES_ARE_ENABLED`, you need to migrate RDF data.

However, if the FLOAT_DOUBLE_DECIMAL, XSD_TIME, and XSD_BOOLEAN attributes do not exist or have the string value `VALID` and if the DATA_CONVERSION_CHECK attribute does not exist, you do not need to migrate RDF data. However, if your semantic network may have any empty RDF literals, see Handling of Empty RDF Literals; and if you choose to migrate existing empty literals to the new format, follow the steps in this section.

To migrate the RDF data, follow these steps:

1.  Connect to the database as the SYSTEM (not SYS .. AS SYSDBA) user or as another non-SYS user with the DBA role , and enter: `SET CURRENT_SCHEMA=MDSYS`

2.  Ensure that the user MDSYS has the following privileges:

    - INSERT privilege on all application tables in the semantic network

    - ALTER ANY INDEX privilege (optional: only necessary if Semantic Indexing for Documents is being used)

    - ACCESS privilege for any workspace in which version-enabled application tables have been modified (optional: only necessary if Workspace Manager is being used for RDF data)

3.  Ensure that any OLS policies for RDF data are temporarily disabled (optional: only necessary if OLS for RDF Data is being used). OLS policies can be re-enabled after running convert_old_rdf_data.

4.  Start SQL\*Plus. If you want to migrate the RDF data without converting existing empty literals to the new format (see Handling of Empty RDF Literals), enter the following statement:

        EXECUTE sdo_rdf_internal.convert_old_rdf_data;

    If you want to migrate the RDF data and also convert existing empty literals to the new format, call `convert_old_rdf_data` with the `flags` parameter set to `'CONVERT_ORARDF_NULL'`. In addition, you can use an optional `tablespace_name` parameter to specify the tablespace to use when creating intermediate tables during data migration. For example, the following statement migrates old semantic data, converts existing `"orardf:null "` values to "", and uses the MY_TBS tablespace for any intermediate tables:

        EXECUTE sdo_rdf_internal.convert_old_rdf_data(
          flags=>'CONVERT_ORARDF_NULL',
          tablespace_name=>'MY_TBS');

    The `sdo_rdf_internal.convert_old_rdf_data` procedure may take a significant amount of time to run if the semantic network contains many triples that are using (or affected by use of) xsd:float, xsd:double, xsd:time, or xsd:boolean typed literals.

5.  Connect to the database as the SYS user with SYSDBA privileges (SYS AS SYSDBA), and enter the SYS account password when prompted). Then enter the following statement:

    - Linux: `@$ORACLE_HOME/md/admin/semrelod.sql`

    - Windows: `@%ORACLE_HOME%\md\admin\semrelod.sql`

**Note:**

You may encounter the ORA-00904 (invalid identifier) error when executing a SEM_MATCH query if the `sdo_rdf_internal.convert_old_rdf_data` procedure and the `semrelod.sql` script were not run after the upgrade to Release 12.1 or later.

**Parent topic:** Upgrading RDF Semantic Graph Support from Release 11.1, 11.2, or 12.1

##### A.1.2.2 Handling of Empty RDF Literals

The way empty-valued RDF literals are handled was changed in Release 11.2. Before this release, the values of empty-valued literals were converted to `"orardf:null"`. In Release 11.2 and later, such values are stored without modification (that is, as ""). However, whether you migrate existing `"orardf:null"` values to "" is optional.

To check if `"orardf:null"` values exist in your semantic network, connect to the database as a user with DBA privileges and query the MDSYS.RDF_PARAMETER table, as follows:

    SELECT namespace, attribute, value FROM mdsys.rdf_parameter
      WHERE namespace='MDSYS'
      AND attribute = 'NULL_LITERAL';

If the NULL_LITERAL attribute has the value `EXISTS`, then `"orardf:null"` values are present in your semantic network.

**Parent topic:** Upgrading RDF Semantic Graph Support from Release 11.1, 11.2, or 12.1

#### A.1.3 Workspace Manager and Virtual Private Database Desupport

Effective with Oracle Database Release 12.2, the following are no longer supported:

- Workspace Manager support for RDF data

- Virtual Private Database (VPD) support for RDF data

If an existing semantic network that contains Workspace Manager (WM) or Virtual Private Database (VPD) data is upgraded, the RDF Semantic Graph installation will be marked as `INVALID`. In addition, the MDSYS.RDF_PARAMETER table will contain a row with description `Feature not supported in current version' for the unsupported component`. To correct this situation, all existing WM and VPD data should be dropped, and the WM and VPD components should be uninstalled.

To uninstall Workspace Manager support for RDF data:

1.  Connect to the database as the SYS user with SYSDBA privileges (SYS AS SYSDBA, and enter the SYS account password when prompted).

2.  Start SQL\*Plus, and enter the following statement:

    - Linux: `@$ORACLE_HOME/md/admin/sdordfwm_rm.sql`

    - Windows: `@%ORACLE_HOME%\md\admin\sdordfwm_rm.sql`

    **Note:**

    If you are in a multitenant environment, run the script with `catcon.pl`. See “Running Oracle-Supplied SQL Scripts in a CDB” in [Oracle Database Administrator’s Guide](../multi/administering-a-cdb-with-sql-plus.md).

To uninstall Virtual Private Database support for RDF data:

1.  Connect to the database as the SYSTEM user (not SYS … AS SYSDBA) or as another non-SYS user with the DBA role.

2.  Start SQL\*Plus, and enter the following statement:

        EXECUTE mdsys.sem_rdfsa_dr.uninstall_vpd;

After performing the necessary uninstall operations, reset the network validity as follows:

1.  Connect to the database as the SYS user with SYSDBA privileges (SYS AS SYSDBA, and enter the SYS account password when prompted).

2.  Start SQL\*Plus, and enter the following statement:

    - Linux: `@$ORACLE_HOME/md/admin/semvalidate.sql`

    - Windows: `@%ORACLE_HOME%\md\admin\semvalidate.sql`

    **Note:**

    If you are in a multitenant environment, run the script with `catcon.pl`. See “Running Oracle-Supplied SQL Scripts in a CDB” in [Oracle Database Administrator’s Guide](../multi/administering-a-cdb-with-sql-plus.md).

**Parent topic:** Enabling RDF Semantic Graph Support

### A.2 Downgrading RDF Semantic Graph Support to a Previous Release

You can downgrade the RDF Semantic Graph support, in conjunction with an Oracle Database downgrade to Release 12.1.

However, downgrading is strongly discouraged, except for rare cases where it is necessary. If you downgrade to a previous release, you will not benefit from bug fixes and enhancements that have been made in intervening releases.

- Downgrading to Release 12.1 Semantic Graph Support

**Parent topic:** Enabling, Downgrading, or Removing RDF Semantic Graph Support

#### A.2.1 Downgrading to Release 12.1 Semantic Graph Support

If you need to downgrade to Oracle Database Release 12.1, the RDF semantic graph support component will be downgraded automatically when you downgrade the database. However, any RDF or OWL data that is specific to Release 12.2 (that is, Release 12.2 or later RDF/OWL persistent structures that are not supported in previous versions) must be dropped before you perform the downgrade, so that the database is compatible with Release 12.1.

To check if any Release 12.2 or later RDF data is incompatible with Release 12.1, perform the following steps:

1.  Connect to the database (Release 12.2 or later) as the SYS user with SYSDBA privileges (SYS AS SYSDBA, and enter the SYS account password when prompted).

2.  Start SQL\*Plus, and enter the following statements:

        SET SERVEROUT ON
        EXECUTE SDO_SEM_DOWNGRADE.CHECK_121_COMPATIBLE;

If any RDF data is incompatible with Release 12.1, the procedure generates an error and displays a list of the incompatible data. In this case, you must perform the following steps:

1.  Remove any Release 12.2 or later release-specific RDF or OWL data if you have not already done so, as explained earlier in this section.

2.  Perform the database downgrade.

3.  Connect to the Release 12.1 database as the SYS user with SYSDBA privileges (SYS AS SYSDBA, and enter the SYS account password when prompted).

4.  Start SQL\*Plus, and enter the following statement:

    - Linux: `@$ORACLE_HOME/md/admin/catsem.sql`

    - Windows: `@%ORACLE_HOME%\md\admin\catsem.sql`

      **Note:**

      If you are in a multitenant environment, run the script with `catcon.pl`. See “Running Oracle-Supplied SQL Scripts in a CDB” in [Oracle Database Administrator’s Guide](../multi/administering-a-cdb-with-sql-plus.md).

    If the script completes successfully, a row with the following column values is inserted into the MDSYS.RDF_PARAMETER table:

    - NAMESPACE: `MDSYS`

    - ATTRIBUTE: `SEM_VERSION`

    - VALUE: (string starting with `12.1`)

    - DESCRIPTION: `VALID`

    After the `catsem.sql` script completes successfully, Oracle semantic technologies support for Release 11.2 is enabled and ready to use, and all Release 12.1-compatible data is preserved.

**Parent topic:** Downgrading RDF Semantic Graph Support to a Previous Release

### A.3 Removing RDF Semantic Graph Support

You can remove the RDF Semantic Graph support from the database.

However, removing this support is strongly discouraged, unless you have a solid reason for doing it. After you remove this support, no applications or database users will be able to use any types, synonyms, or PL/SQL packages related to RDF Semantic Graph support.

To remove the RDF Semantic Graph support from the database, perform the following steps:

1.  Connect to the database as the SYS user with SYSDBA privileges (SYS AS SYSDBA, and enter the SYS account password when prompted).

2.  Start SQL\*Plus, and enter the following statement:

    - Linux: `@$ORACLE_HOME/md/admin/semremov.sql`

    - Windows: `@%ORACLE_HOME%\md\admin\semremov.sql`

    **Note:**

    If you are in a multitenant environment, run the script with `catcon.pl`. See “Running Oracle-Supplied SQL Scripts in a CDB” in [Oracle Database Administrator’s Guide](../multi/administering-a-cdb-with-sql-plus.md).

The `semremov.sql` script drops the semantic network and removes any RDF Semantic Graph types, tables, and PL/SQL packages.

**Parent topic:** Enabling, Downgrading, or Removing RDF Semantic Graph Support
