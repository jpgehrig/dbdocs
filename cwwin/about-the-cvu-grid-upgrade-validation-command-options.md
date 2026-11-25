## About the CVU Grid Upgrade Validation Command Options

You can use the Cluster Verification Utility (CVU) to validate your system readiness before upgrading.

You can run upgrade validations in one of two ways:

- Run the installer, and allow the CVU validation built into the installer to perform system checks

- Run the CVU manual script `cluvfy.bat` script to perform system checks

To use the installer to perform pre-install checks, run the installation as you normally would. The installer starts CVU, and performs system checks as part of the installation process. Selecting the installer to perform these checks is particularly appropriate if you think you have completed preinstallation checks, and you want to confirm that your system configuration meets minimum requirements for installation.

To use the `cluvfy.bat` command-line script for CVU, navigate to the new Grid home where you extracted the image files for upgrade, that contains the `runcluvfy.bat` script, and run the following command to check the readiness of your Oracle Clusterware installation for upgrades:

    runcluvfy.bat stage -pre crsinst -upgrade

Running `runcluvfy.bat` with the `-pre crsinst -upgrade` options performs system checks to confirm if the cluster is in a correct state for upgrading from an existing clusterware installation.

The `runcluvfy` command uses the following syntax, where variable content is indicated by italics:

    runcluvfy.bat stage -pre crsinst -upgrade [-rolling] -src_crshome src_Gridhome
     -dest_crshome dest_Gridhome -dest_version dest_release
    [-verbose]

The options are:

- `-rolling`

  Use this option to verify readiness for rolling upgrades.

- `-src_crshome ``src_Gridhome`

  Use this option to indicate the location of the source Oracle Clusterware or Grid home that you are upgrading, where src_Gridhome is the path to the home to upgrade.

- `-dest_crshome ``dest_Gridhome`

  Use this option to indicate the location of the upgrade Grid home, where dest_Gridhome is the path to the Grid home.

- `-dest_version ``dest_release`

  Use the `dest_version` option to indicate the release number of the upgrade, including any patchset. The release number must include the five digits designating the release to the level of the platform-specific patch. For example: 12.1.0.1.0.

- `-verbose`

  Use the `-verbose` option to produce detailed output of individual checks.

**Related Topics**

- [Restrictions and Guidelines for Oracle Grid Infrastructure Upgrades](restrictions-and-guidelines-for-oracle-grid-infrastructure-upgrades.md)

**Parent topic:** [Using CVU to Validate Readiness for Oracle Clusterware Upgrades](using-cvu-to-validate-readiness-for-oracle-clusterware-upgrades.md)
