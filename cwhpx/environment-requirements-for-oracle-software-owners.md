You must make the following changes to configure Oracle software owner environments:

- Set the installation software owner user (`grid`, `oracle`) default file mode creation mask (umask) to 022 in the shell startup file. Setting the mask to 022 ensures that the user performing the software installation creates files with 644 permissions.

- Set ulimit settings for file descriptors and processes for the installation software owner (`grid`, `oracle`).

- Set the DISPLAY environment variable in preparation for running an Oracle Universal Installer (OUI) installation.

**Caution:**

If you have existing Oracle installations that you installed with the user ID that is your Oracle Grid Infrastructure software owner, then unset all Oracle environment variable settings for that user.

**Parent topic:** [Configuring Grid Infrastructure Software Owner User Environments](configuring-grid-infrastructure-software-owner-user-environments.md)
