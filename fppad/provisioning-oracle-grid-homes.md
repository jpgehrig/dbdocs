## Provisioning Oracle Grid Infrastructure Homes

When you create a working copy of a gold image as part of a move or upgrade operation, Fleet Patching and Provisioning configures the operating system groups in the new working copy to match those of the source software home.

Oracle Grid Infrastructure homes are distributed in the form of working copies of gold images. After a working copy has been provisioned, Oracle Fleet Patching and Provisioning can optionally configure Oracle Grid Infrastructure. This gives Oracle Fleet Patching and Provisioning the ability to create an Oracle Grid Infrastructure installation on a group of one or more nodes that initially do not have Oracle Grid Infrastructure installed.

Oracle Fleet Patching and Provisioning also has commands for managing Oracle Grid Infrastructure homes, such as switching to a patched home or upgrading to a new Oracle Grid Infrastructure version. These are both single commands that orchestrate the numerous steps involved. You can also revert to the original home. Also, Oracle Fleet Patching and Provisioning can add or delete nodes from an Oracle Grid Infrastructure configuration.

- [About Deploying Oracle Grid Infrastructure Using Oracle Fleet Patching and Provisioning](about-deploying-grid-using-oracle-fpp.md)
  You can use Oracle Fleet Patching and Provisioning to provision and maintain your Oracle Grid Infrastructure homes.
- [Provisioning Oracle Grid Infrastructure Software](provisioning-oracle-grid.md)
  Fleet Patching and Provisioning has several methods to provision and, optionally, configure Oracle Grid Infrastructure and Oracle Restart homes.

**Parent topic:** [Managing Gold Images and Working Copies](managing-gold-images-and-working-copies.md)
