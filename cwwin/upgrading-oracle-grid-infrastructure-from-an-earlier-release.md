## Upgrading Oracle Grid Infrastructure from an Earlier Release

Complete this procedure to upgrade Oracle Grid Infrastructure (Oracle Clusterware and Oracle Automatic Storage Management) from an earlier release.

If you previously attempted to upgrade to a higher release of Oracle Grid Infrastructure, and that Grid home still exists, then instead of running the installer, run the `config.bat` script in the `Grid_home``\crs\config` directory of the higher version Grid home. Select the Upgrade option to upgrade the existing Grid home to the later release.

1.  As the Grid installation user, download the Oracle Grid Infrastructure image files and extract the files to the Grid home.
    For example:

        mkdir C:\app\19.0.0\grid
        cd C:\app\19.0.0\grid
        unzip -q download_location\grid_home.zip

    where `download_location``\grid_home.zip` is the path of the downloaded Oracle Grid Infrastructure image file.

    **Note:**

    - You must extract the image software into the directory where you want your Grid home to be located.

    - Download and copy the Oracle Grid Infrastructure image files to the local node only. During upgrade, the software is copied and installed on all other nodes in the cluster.
2.  If there are non-clustered, or single-instance, Oracle databases that use Oracle ASM running on any of the nodes in the cluster, they must be shut down before you start the upgrade.
    Listeners associated with those databases do not have to be shut down.
    **Note:**

    Oracle recommends that you leave Oracle Real Application Clusters (Oracle RAC) instances running during the Oracle Clusterware upgrade. During the upgrade process, the database instances on the node being upgraded are stopped and started automatically during the upgrade process.
3.  Start the Oracle Grid Infrastructure wizard in the new Grid home by running the following command:
        Grid_home\gridSetup.bat
4.  Select the option Upgrade Oracle Grid Infrastructure.
    This option upgrades Oracle Grid Infrastructure (Oracle Clusterware and Oracle ASM).
5.  On the node selection page, select all nodes.
6.  Select installation options as prompted.
7.  Confirm your selections, and then the upgrade scripts are run automatically.
8.  Because the Oracle Grid Infrastructure home is in a different location than the former Oracle Clusterware and Oracle ASM homes, update any scripts or applications that use utilities or other files that reside in the Oracle Clusterware and Oracle ASM homes.
    **Note:**

    - Starting from Oracle Grid Infrastructure 12c release 2 (12.2), the OCR and OCR backup must be located in an Oracle ASM disk group. During the upgrade, regardless of where the OCR backup location was in the previous release, the OCR backup location is changed to an Oracle ASM disk group.

    - The backups in the old Oracle Clusterware home can be deleted after the upgrade because upgrades of Oracle Clusterware are out-of-place upgrades, and after the upgrade to Oracle Grid Infrastructure 19c the OCR and OCR backup must be located in an Oracle ASM disk group.

    - If the cluster being upgraded has a single disk group that stores the OCR, OCR backup, Oracle ASM password, Oracle ASM password file backup, and the Grid Infrastructure Management Repository (GIMR), then Oracle recommends that you create a separate disk group or use another existing disk group and store the OCR backup, the GIMR and Oracle ASM password file backup in that disk group.

**Related Topics**

- [Oracle Clusterware Administration and Deployment Guide](../cwadd/oracle-cluster-registry-utility-reference.md)

**Parent topic:** [Performing Rolling Upgrades of Oracle Grid Infrastructure](performing-rolling-upgrades-of-oracle-grid-infrastructure.md)
