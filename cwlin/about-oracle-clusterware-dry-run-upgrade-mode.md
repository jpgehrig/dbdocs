## About Oracle Grid Infrastructure Dry-Run Upgrade Mode

Oracle Grid Infrastructure dry-run upgrade mode enables you to check system readiness for upgrade.

Starting with Oracle Grid Infrastructure 19c, the Oracle Grid Infrastructure installer enables you to perform a dry-run upgrade to check readiness of the system for upgrade. To perform Oracle Grid Infrastructure dry-run upgrade, create a new Grid home with the necessary user group permissions, extract the Oracle Grid Infrastructure 19c gold image to the new Grid home, and then start the installer with `—dryRunForUpgrade` flag.

Dry-run upgrades are not supported on Oracle Grid Infrastructure for a standalone server (Oracle Restart) configurations.

**Note:**

The installer does not perform an actual upgrade in the dry-run upgrade mode. You can relaunch the installer, without any flag, from any of the cluster nodes to upgrade Oracle Grid Infrastructure if dry-run is successful.

The installer performs the following tasks in dry-run upgrade mode:

- Validates storage and network configuration for the new release

- Checks if the system meets the software and hardware requirements for the new release

- Checks for the patch requirements and apply necessary patches before starting the upgrade

- Writes system configuration issues or errors in the `gridSetupActions<timestamp>.log` log file

The Grid infrastructure dry-run upgrade flow is similar to a regular upgrade, but the installer does not run any configuration tool.

**Related Topics**

- [Performing Dry-Run Upgrade Using Oracle Universal Installer](running-oui-in-dry-run-upgrade-mode.md)

**Parent topic:** [Using Dry-Run Upgrade Mode to Check System Upgrade Readiness](using-dry-run-upgrade-mode-to-validate-readiness-for-oracle-grid-infrastructure.md)
