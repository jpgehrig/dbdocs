The AutoUpgrade Utility simplifies the task of upgrading and converting your earlier release Oracle Database to Oracle Database 19c.

- AutoUpgrade Configuration File for Non-CDB Upgrades on the Same System
  Use this example to see how you can upgrade your non-CDB Oracle Database
- AutoUpgrade with Source and Target Database Homes on Same Server (Typical)
  When your Oracle Database Source and Target Oracle homes are installed on the same physical server, use this example.

### AutoUpgrade Configuration File for Non-CDB Upgrades on the Same System

Use this example to see how you can upgrade your non-CDB Oracle Database

In this scenario, you upgrade an earlier release non-CDB database to a non-CDB Oracle Database 19c release.

The following configuration file identifies the non-CDB database `emp` as the source database. The source database is upgraded, and the upgraded Oracle Database is placed in the new Oracle home `/u01/app/oracle/product/19.1.0/dbhome_1`:

    global.autoupg_log_dir=/u01/app/oracle/cfgtoollogs/autoupgrade
    upg1.log_dir=/u01/app/oracle/cfgtoollogs/autoupgrade/employee
    upg1.sid=emp
    upg1.source_home=/u01/app/oracle/product/12.2.0/dbhome_1
    upg1.target_home=/u01/app/oracle/product/19.1.0/dbhome_1

In this example, the following local parameters are specified:

- `upg1.log_dir` (optional) specifies that the upgrade directory for this database is placed in the folder employee, under the global AutoUpgrade log directory path.
- `upg1.sid` (required) identifies the Oracle system identifier (SID) of the database that you want to upgrade is `emp`.
- `upg1.source_home` (required) specifies the source Oracle home path.
- `upg1.target_home` (required) specifies the target Oracle home path.

The upgrade job starts immediately when you run AutoUpgrade using this configuration file. By default for Oracle Database Enterprise Edition, a guaranteed restore point is automatically created. This feature protects the upgrade, and enables you to fall back to the earlier release in case of errors.

This configuration file provides you with a minimal use case example. You can choose to add additional parameters to modify the upgrade for your needs. For example, if you want to specify a future start time to run the upgrade, then you can use the local parameter `start_time`. In addition, you can modify default behavior. For example, by default, time zone settings are upgraded as part of the database upgrade. Oracle recommends that you upgrade time zone files as part of the upgrade. However, if you want to defer this upgrade to a later maintenance window, then you can add the local parameter `timezone_upg`.

**Parent topic:** Upgrading Oracle Database

### AutoUpgrade with Source and Target Database Homes on Same Server (Typical)

When your Oracle Database Source and Target Oracle homes are installed on the same physical server, use this example.

Context: Source and Target homes are on the same server.

To start the analysis, enter the following command.

    java -jar autoupgrade.jar -config config.txt -mode analyze

The command produces a report that indicates any error conditions that the command finds. Review the error conditions.

To start the deployment of the upgrade, enter the following command:

    java -jar autoupgrade.jar -config config.txt -mode deploy

**Parent topic:** Upgrading Oracle Database
