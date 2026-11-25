Passwordless SSH configuration is a mandatory installation requirement. SSH is used during installation to configure cluster member nodes, and SSH is used after installation by configuration assistants, Oracle Enterprise Manager, Opatch, and other features.

Automatic Passwordless SSH configuration using OUI creates RSA encryption keys on all nodes of the cluster. If you have system restrictions that require you to set up SSH manually, such as using DSA keys, then use this procedure as a guide to set up passwordless SSH. If SSH is not available, then Oracle Universal Installer (OUI) attempts to use `rcp` instead. However, these services are disabled by default on most Linux systems.

**Note:**

The supported version of SSH for Linux distributions is OpenSSH.

- [Checking Existing SSH Configuration on the System](checking-existing-ssh-configuration.md)
  To determine if SSH is running, enter the following command.
- [Configuring SSH on Cluster Nodes](configuring-ssh-on-cluster-nodes.md)
  You must configure SSH separately for each Oracle software installation owner that you intend to use for installation.
- [Enabling SSH User Equivalency on Cluster Nodes](enabling-ssh-user-equivalency-on-cluster-nodes.md)
  After you have copied the `authorized_keys` file that contains all keys to each node in the cluster, complete the following procedure.

**Parent topic:** [Completing Preinstallation Tasks Manually](completing-preinstallation-tasks-manually.md)
