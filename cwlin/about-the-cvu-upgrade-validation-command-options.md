## About the CVU Upgrade Validation Command Options

Review this information about running upgrade validations.

- Run Oracle Universal Installer (OUI), and allow the Cluster Verification Utility (CVU) validation built into OUI to perform system checks and generate fixup scripts.

- Run the CVU manual script `cluvfy.sh` to perform system checks and generate fixup scripts.

To use OUI to perform pre-install checks and generate fixup scripts, run the installation as you normally would. OUI starts CVU, and performs system checks as part of the installation process. Selecting OUI to perform these checks is particularly appropriate if you think you have completed preinstallation checks, and you want to confirm that your system configuration meets minimum requirements for installation.

To use the cluvfy.sh command-line script for CVU, navigate to the new Grid home where you extracted the image files for upgrade, that contains the `runcluvfy.sh` script, and run the command `runcluvfy.sh stage -pre crsinst -upgrade` to check the readiness of your Oracle Clusterware installation for upgrades. Running `runcluvfy.sh` with the `-pre crsinst -upgrade` options performs system checks to confirm if the cluster is in a correct state for upgrading from an existing clusterware installation.

The command uses the following syntax, where variable content is indicated by italics:

    runcluvfy.sh stage -pre crsinst -upgrade [-rolling]
    -src_crshome src_Gridhome ]-dest_crshome dest_Gridhome -dest_version dest_release
    [-fixup][-fixupnoexec][-method sudo -user user_name [-location dir_path][-method root][-verbose]

The options are:

- `-rolling`

  Use this option to verify readiness for rolling upgrades.

- `-src_crshome `src_Gridhome

  Use this option to indicate the location of the source Oracle Clusterware or Grid home that you are upgrading, where src_Gridhome is the path to the home that you want to upgrade.

- `-dest_crshome` dest_Gridhome

  Use this option to indicate the location of the upgrade Grid home, where dest\_ Gridhome is the path to the Grid home.

- `-dest_version` dest_release

  Use the `-dest_version` option to indicate the release number of the upgrade, including any patchset. The release number must include the five digits designating the release to the level of the platform-specific patch. For example: `19.0.0.0.0`.

- `-fixup [-method sudo -user `user_name `[-location` dir_path`][-method` root`] `

  Use the `-fixup` option to indicate that you want to generate instructions for any required steps you need to complete to ensure that your cluster is ready for an upgrade. The default location is the CVU work directory.

  The `-fixup -method` option defines the method by which `root` scripts are run. The `-method` flag requires one of the following options:

  - `sudo`: Run as a user on the sudoers list.

  - `root`: Run as the `root` user.

  If you select `sudo`, then enter the `-location` option to provide the path to Sudo on the server, and enter the `-user` option to provide the user account with Sudo privileges.

- `-fixupnoexec`

  If the option is specified, then on verification failure, the fix up data is generated and the instruction for manual execution of the generated fix ups is displayed.

- `-verbose`

  Use the `-verbose` flag to produce detailed output of individual checks.

**Parent topic:** [Using CVU to Validate Readiness for Oracle Clusterware Upgrades](using-cvu-to-validate-readiness-for-oracle-clusterware-upgrades.md)
