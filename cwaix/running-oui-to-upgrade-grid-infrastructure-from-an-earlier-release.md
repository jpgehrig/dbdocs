Complete this procedure to upgrade Oracle Grid Infrastructure (Oracle Clusterware and Oracle Automatic Storage Management) from an earlier release.

At any time during the upgrade, if you have a question about what you are being asked to do, or what input you are required to provide during upgrade, click the Help button on the installer page.

You should have your network information, storage information, and operating system users and groups available to you before you start upgrade, and you should be prepared to run root scripts.

1.  As `grid` user, download the Oracle Grid Infrastructure image files and extract the files to the Grid home.
    For example:

        mkdir -p /u01/app/19.0.0/grid
        chown grid:oinstall /u01/app/19.0.0/grid
        cd /u01/app/19.0.0/grid
        unzip -q download_location/grid_home.zip

    `download_location/grid_home.zip` is the path of the downloaded Oracle Grid Infrastructure image file.

    **Note:**

    - You must extract the image software into the directory where you want your Grid home to be located.

    - Download and copy the Oracle Grid Infrastructure image files to the local node only. During upgrade, the software is copied and installed on all other nodes in the cluster.
2.  Start the Oracle Grid Infrastructure wizard by running the following command:
         /u01/app/19.0.0/grid/gridSetup.sh
3.  Select the following configuration option:
    - Upgrade Oracle Grid Infrastructure: Select this option to upgrade Oracle Grid Infrastructure (Oracle Clusterware and Oracle ASM).

    **Note:**

    Oracle Clusterware must always be the later release, so you cannot upgrade Oracle ASM to a release that is more recent than Oracle Clusterware.
4.  On the Node Selection page, select all nodes.
5.  Select installation options as prompted. Oracle recommends that you configure `root` script automation, so that the `rootupgrade.sh` script can be run automatically during the upgrade.
6.  Run `root` scripts, either automatically or manually:
    - Running root scripts automatically:

      If you have configured `root` script automation, then use the pause between batches to relocate services from the nodes running the previous release to the new release.

    - Running root scripts manually

      If you have not configured `root` script automation, then when prompted, run the `rootupgrade.sh` script on each node in the cluster that you want to upgrade.

    If you run `root` scripts manually, then run the script on the local node first. The script shuts down the earlier release installation, replaces it with the new Oracle Clusterware release, and starts the new Oracle Clusterware installation. After the script completes successfully, you can run the script in parallel on all nodes except for one, which you select as the last node. When the script is run successfully on all the nodes except the last node, run the script on the last node.
7.  Because the Oracle Grid Infrastructure home is in a different location than the former Oracle Clusterware and Oracle ASM homes, update any scripts or applications that use utilities, libraries, or other files that reside in the Oracle Clusterware and Oracle ASM homes.
8.  Update the Oracle Enterprise Manager target parameters as described in the topic Updating Oracle Enterprise Manager Cloud Control Target Parameters.

**Note:**

- After upgrading to Oracle Grid Infrastructure 19c, remove the `ADR_BASE=/u01/app/grid` entry from `$ORACLE_HOME/network/admin/sqlnet.ora` file, if you use Oracle ASM for database storage.

- At the end of the upgrade, if you set the Oracle Cluster Registry (OCR) backup location manually to the earlier release Oracle Clusterware home (CRS home), then you must change the OCR backup location to the new Oracle Grid Infrastructure home (Grid home). If you did not set the OCR backup location manually, then the backup location is changed for you during the upgrade.

- Because upgrades of Oracle Clusterware are out-of-place upgrades, the previous release Oracle Clusterware home cannot be the location of the current release OCR backups. Backups in the old Oracle Clusterware home can be deleted.

- If the cluster being upgraded has a single disk group that stores the OCR, OCR backup, Oracle ASM password, Oracle ASM password file backup, and the Grid Infrastructure Management Repository (GIMR), then Oracle recommends that you create a separate disk group or use another existing disk group and store the OCR backup, the GIMR and Oracle ASM password file backup in that disk group.

**Related Topics**

- [Oracle Clusterware Administration and Deployment Guide](../cwadd/oracle-cluster-registry-utility-reference.md)

**Parent topic:** [Performing Rolling Upgrade of Oracle Grid Infrastructure](performing-rolling-upgrade-of-oracle-grid-infrastructure.md)
