Oracle Universal Installer detects when the minimum requirements for an installation are not met, and creates shell scripts, called fixup scripts, to finish incomplete system configuration steps.

If Oracle Universal Installer detects an incomplete task, then it generates fixup scripts (`runfixup.sh`). You can run the fixup script and click Fix and Check Again. The fixup script modifies both persistent parameter settings and parameters in memory, so you do not have to restart the system.

The Fixup script does the following tasks:

- Sets kernel parameters, if necessary, to values required for successful installation, including:

  - Shared memory parameters.

  - Open file descriptor and UDP send/receive parameters.

- Creates and sets permissions on the Oracle Inventory (central inventory) directory.

- Creates or reconfigures primary and secondary group memberships for the installation owner, if necessary, for the Oracle Inventory directory and the operating system privileges groups.

<!-- -->

- Sets shell limits, if necessary, to required values.

**Note:**

Using fixup scripts does not ensure that all the prerequisites for installing Oracle Database are met. You must still verify that all the preinstallation requirements are met to ensure a successful installation.

Oracle Universal Installer is fully integrated with Cluster Verification Utility (CVU) automating many prerequisite checks for your Oracle Grid Infrastructure or Oracle Real Application Clusters (Oracle RAC) installation. You can also manually perform various CVU verifications by running the `cluvfy` command.

**Related Topics**

- [Completing Preinstallation Tasks Manually](completing-preinstallation-tasks-manually.md)
- [Oracle Clusterware Administration and Deployment Guide](../cwadd/cluster-verification-utility-reference.md)

**Parent topic:** [Configuring Oracle Solaris Operating System for Oracle Database](configuring-oracle-solaris-operating-systems-for-oracle-database.md)
