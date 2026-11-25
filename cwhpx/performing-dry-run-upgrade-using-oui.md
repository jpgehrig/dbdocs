Run the Oracle Grid Infrastructure installer in dry-run upgrade mode to determine if the system is ready for upgrade.

At any time during the dry-run upgrade, if you have a question about what you are being asked to do, or what input you are required to provide during dry-run upgrade, click the Help button on the installer page.

You should have your network information, storage information, and operating system users and groups available to you before you start dry-run upgrade.

1.  As `grid` user, download the Oracle Grid Infrastructure image file and extract the file to the Grid home.
    For example:

        $ mkdir -p /u01/app/19.0.0/grid
        $ chown grid:oinstall /u01/app/19.0.0/grid
        $ cd /u01/app/19.0.0/grid
        $ unzip -q download_location/grid_home.zip

    `download_location/grid_home.zip` is the path of the downloaded Oracle Grid Infrastructure image file.

    **Note:**

    You must extract the image file into the directory where you want your Grid home to be located.
2.  Start the Oracle Grid Infrastructure installation wizard in dry-run upgrade mode.
        $ /u01/app/19.0.0/grid/gridSetup.sh -dryRunForUpgrade
3.  Select Upgrade Oracle Grid Infrastructure option to perform dry-run upgrade for Oracle Grid Infrastructure (Oracle Clusterware and Oracle ASM).
4.  Select installation options as prompted. Oracle recommends that you configure `root` script automation, so that the `rootupgrade.sh` script can be run automatically during the dry-run upgrade.
5.  Run `root` scripts, either automatically or manually:
    - Running root scripts automatically

      If you have configured `root` script automation, then the installer will run the `rootupgrade.sh` script automatically on the local node.

    - Running root scripts manually

      If you have not configured `root` script automation, then when prompted, run the `rootupgrade.sh` script on the local node.

    If you run `root` scripts manually, then run the script only on the local node.
6.  Check the `gridSetupActions<timestamp>.log` log file for errors and fix errors reported in the log file.
7.  Exit the installer on the Finish screen.
    **Note:**

    The `gridSetup.sh -dryRunForUpgrade` command registers the new Oracle Grid Infrastructure home in the Oracle Inventory (oraInventory).
8.  Relaunch the installer from the same Grid home without any flag to start an actual upgrade.
        $ /u01/app/19.0.0/grid/gridSetup.sh

    **Note:**

    If you need to apply patches before performing the upgrade, then use the OPatch utility to apply patches on each cluster node.

**Related Topics**

- [Upgrading Oracle Grid Infrastructure from an Earlier Release](running-oui-to-upgrade-grid-infrastructure-from-an-earlier-release.md)

**Parent topic:** [Using Dry-Run Upgrade Mode to Check System Upgrade Readiness](using-dry-run-upgrade-mode-to-check-readiness-for-oracle-clusterware-upgrades.md)
