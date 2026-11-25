## 3 Managing Gold Images and Working Copies

You can add new gold images to your Oracle Fleet Patching and Provisioning Server, create working copies from the gold images, and provision Oracle homes.

- [Adding Gold Images to the Fleet Patching and Provisioning Server](adding-gold-images-to-oracle-fpp-server.md)
  Use RHPCTL to add gold images for later provisioning of software.
- [Provisioning Copies of Gold Images](provisioning-gold-image-copies.md)
  Use RHPCTL to provision copies of gold images to Fleet Patching and Provisioning Servers, Clients, and targets.
- [Provisioning Oracle Grid Infrastructure Homes](provisioning-oracle-grid-homes.md)
  When you create a working copy of a gold image as part of a move or upgrade operation, Fleet Patching and Provisioning configures the operating system groups in the new working copy to match those of the source software home.
- [Provisioning Oracle Database Homes](provisioning-database-homes.md)
  Use the `rhpctl add workingcopy` command to provision a working copy of a database home on a Oracle Fleet Patching and Provisioning Server, Client, or `rhpclient`-less target.
