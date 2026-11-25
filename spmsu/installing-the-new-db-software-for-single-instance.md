Use this procedure overview to assist you to install the software for the new Oracle Database release for a single instance deployment.

**Note:**

You cannot upgrade a database using Database Upgrade Assistant (DBUA) when the source and target Oracle homes are owned by different users. Attempting to do so returns error `PRKH-1014`. Either ensure that the source and target databases have the same owner, or perform a manual upgrade.

To install the new Oracle Database software for this release:

1.  Follow the instructions in your Oracle operating system-specific documentation to prepare for installation of Oracle Database software.

2.  Start Oracle Universal Installer, and select a software-only installation.

    When installation of Oracle Database software has completed successfully, click Exit to close Oracle Universal Installer.

3.  Run the Pre-Upgrade Information Tool. The tool enables you to check the types of items that DBUA checks. The tool identifies issues, and can help you fix some issues that it finds.

    By default, the tool is in the location `New_release_Oracle_home``/rdbms/admin/preupgrade.jar`.

    If you use Oracle Label Security, Oracle Database Vault, or both, then select Enterprise Edition on the Select Database Edition page, click Select Options, and enable one or both components from the components list.

**Parent topic:** [Installing Oracle Software in a New Oracle Home](installing-oracle-software-in-a-new-oracle-home.md)
