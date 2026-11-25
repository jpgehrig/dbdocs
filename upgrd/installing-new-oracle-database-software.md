## Installing the New Oracle Database Software for Oracle RAC

Use this procedure overview to assist you to install the software for the new Oracle Database release for an Oracle RAC deployment.

**Note:**

You cannot upgrade a database using Database Upgrade Assistant (DBUA) when the source and target Oracle homes are owned by different users. Attempting to do so returns error PRKH-1014. Either ensure that the source and target databases have the same owner, or perform a manual upgrade.

If you are upgrading an Oracle RAC database, then you must perform the following steps in the order shown:

1.  Upgrade Oracle Clusterware:

    1.  Upgrade Oracle Clusterware first as described in the Oracle Grid Infrastructure installation guide for your operating system.

    2.  When prompted, open a separate terminal session, log in as `root`, and run `root.sh`.

2.  After upgrading Oracle Clusterware, follow the instructions in your Oracle operating system-specific documentation to prepare for Oracle Database software installation.

3.  Start Oracle Universal Installer, and install the software.

    When installation of Oracle Database software has completed successfully, click Exit to close Oracle Universal Installer.

4.  Run AutoUpgrade with the `preupgrade` parameter, run in `analyze` mode. AutoUpgrade can automatically fix many issues, and list other issues in the `prefixups` file it generates, which you can fix manually before the upgrade.

5.  Run AutoUpgrade in Deploy mode.

**Related Topics**

- [Oracle Clusterware Installation Guide for your platform](../install-and-upgrade.md)

**Parent topic:** [Preparing to Upgrade Oracle Database](tasks-prepare-upgrade-oracle-database.md)
