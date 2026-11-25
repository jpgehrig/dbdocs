## B Completing Preinstallation Tasks Manually

You can complete the preinstallation configuration tasks manually.

Oracle recommends that you use Oracle Universal Installer and Cluster Verification Utility fixup scripts to complete minimal configuration settings. If you cannot use fixup scripts, then complete minimum system settings manually.

- [Configuring SSH Manually on All Cluster Nodes](configuring-ssh-manually-on-all-cluster-nodes.md)
  Passwordless SSH configuration is a mandatory installation requirement. SSH is used during installation to configure cluster member nodes, and SSH is used after installation by configuration assistants, Oracle Enterprise Manager, Opatch, and other features.
- [Configuring Storage Device Path Persistence Manually](configuring-storage-device-path-persistence-manually.md)
  You can maintain storage file path persistence by creating a rules file.
- [Configuring Kernel Parameters for Linux](configuring-kernel-parameters-for-linux.md)
  These topics explain how to configure kernel parameters manually for Linux if you cannot complete them using the fixup scripts.
- [Configuring Default Thread Limits Value for SUSE Linux](configuring-defaulttasksmax-for-suse.md)
  If you are on SUSE Linux Enterprise Server 12 SP2 or later, or SUSE Linux Enterprise Server 15 or later, then set the DefaultTasksMax parameter value to `65535`.
