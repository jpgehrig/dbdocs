## Oracle Restart Patching and Upgrading

You can use Oracle Fleet Patching and Provisioning to patch and upgrade Oracle Restart using gold images.

You can move the `rhpclient`-less target of single-node Oracle Restart to an Oracle home that you provision from a gold image that includes any patches. Oracle Fleet Patching and Provisioning ensures the copying of the configuration files, such as listener.ora, to the new Oracle home.

You can also use Oracle Fleet Patching and Provisioning to upgrade Oracle Restart using gold images. Upgrade the Oracle Restart environment by upgrading the Oracle home on the destination Oracle home that you provision from a higher-level gold image. Oracle Fleet Patching and Provisioning updates the configuration and inventory settings.

Use the RHPCTL utility similar to the following to patch Oracle Restart:

    rhpctl move gihome -sourcewc Oracle_Restart_home_1 -destwc Oracle_Restart_home_2
    -targetnode Oracle_Restart_node {superuser credentials}

Use the RHPCTL utility similar to the following to upgrade Oracle Restart:

    rhpctl upgrade gihome -sourcewc source_Oracle_Restart_home -destwc higher_version_Oracle_Restart_home
    -targetnode Oracle_Restart_node {superuser credentials}

**Related Topics**

- [rhpctl move gihome](gihome-commands.md)
- [rhpctl upgrade gihome](gihome-commands.md)

**Parent topic:** [Patching and Upgrading Oracle Grid Infrastructure](patching-and-upgrading-oracle-grid-infrastructure.md)
