## Zero-Downtime Upgrade

Using Fleet Patching and Provisioning, which automates and orchestrates database upgrades, you can upgrade an Oracle RAC or Oracle RAC One Node database with no disruption in service.

The zero-downtime upgrade process is resumable, restartable, and recoverable should any errors interrupt the process. You can fix the issue then re-run the command, and Fleet Patching and Provisioning continues from the error point. Oracle also provides hooks at the beginning and end of the zero-downtime upgrade process, allowing call outs to user-defined scripts, so you can customize the process.

You can use the zero-downtime upgrade process to upgrade databases that meet the following criteria:

- Database upgrade targets: Oracle RAC and Oracle RAC One Node, with the following upgrade paths:
  - 11.2.0.4 to 12.1.0.2
  - 11.2.0.4 to 12.2
  - 11.2.0.4 to 18c
  - 12.1.0.2 to 12.2
  - 12.1.0.2 to 18c
  - 12.1.0.2 to 19c
  - 12.2 to 18c
  - 12.2 to 19c
  - 18c to 19c

- Fleet Patching and Provisioning management: The source database home can either be unmanaged (not provisioned by Fleet Patching and Provisioning service) or managed (provisioned by Fleet Patching and Provisioning service)

- Database state: The source database must be in archive log mode

### Upgrading Container Databases

You can use Fleet Patching and Provisioning to upgrade CDBs but Fleet Patching and Provisioning does not support converting a non-CDB to a CDB during upgrade. To prepare for a zero-downtime upgrade, you complete configuration steps and validation checks. When you run a zero-downtime upgrade using Fleet Patching and Provisioning, you can stop the upgrade and resume it, if necessary. You can recover from any upgrade errors, and you can restart the upgrade. You also have the ability to insert calls to your own scripts during the upgrade, so you can customize your upgrade procedure.

### Zero-Downtime Upgrade Environment Prerequisites

- Server environment: Oracle Grid Infrastructure 18c with Fleet Patching and Provisioning

- Database hosts: Databases hosted on one of the following platforms:
  - Oracle Grid Infrastructure 18c Fleet Patching and Provisioning Client

  - Oracle Grid Infrastructure 18c Fleet Patching and Provisioning Server

  - Oracle Grid Infrastructure 12c (12.2.0.1) Fleet Patching and Provisioning Client

  - Oracle Grid Infrastructure 12c (12.1.0.2) target cluster

- Database-specific prerequisites for the environment: During an upgrade, Fleet Patching and Provisioning manages replication to a local data file to preserve transactions applied to the new database when it is ready. There are two possibilities for the local data file:
  - Snap clone, which is available if the database data files and redo and archive redo logs are on Oracle ACFS file systems
  - Full copy, for all other cases

- Fleet Patching and Provisioning requires either Oracle GoldenGate or Oracle Data Guard during a zero-downtime database upgrade. As part of the upgrade procedure, Fleet Patching and Provisioning configures and manages the Oracle GoldenGate deployment.

<!-- -->

- [Running a Zero-Downtime Upgrade Using Oracle GoldenGate for Replication](running-zero-downtime-upgrade-using-oracle-goldengate.md)
  Run a zero-downtime upgrade using Oracle GoldenGate for replication.
- [Running a Zero-Downtime Upgrade Using Oracle Data Guard for Replication](running-zero-downtime-upgrade-using-oracle-data-guard.md)
  Run a zero-downtime upgrade using Oracle Data Guard for replication.
- [Customizing Zero-Downtime Upgrades](customizing-zero-downtime-upgrades.md)
  You can customize zero-downtime upgrades using the user-action framework of Fleet Patching and Provisioning.

**Parent topic:** [Patching and Upgrading Oracle Database](patching-and-upgrading-oracle-database.md)
