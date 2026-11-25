You can complete the preinstallation configuration tasks manually.

Oracle recommends that you use Oracle Universal Installer and Cluster Verification Utility fixup scripts to complete minimal configuration settings. If you cannot use fixup scripts, then complete minimum system settings manually.

- [Configuring SSH Manually on All Cluster Nodes](configuring-ssh-manually-on-all-cluster-nodes.md)
  Passwordless SSH configuration is a mandatory installation requirement. SSH is used during installation to configure cluster member nodes, and SSH is used after installation by configuration assistants, Oracle Enterprise Manager, Opatch, and other features.
- [Configuring Shell Limits and System Configuration Parameters for IBM AIX](configuring-shell-limits-and-system-configuration.md)
  These topics explain how to configure shell limits and system configuration parameters manually if you cannot complete them using the fixup scripts.
- [Setting UDP and TCP Kernel Parameters Manually](setting-udp-tcp-kernel-parameters.md)
  If you do not use a Fixup script or CVU to set ephemeral ports, then use NDD to ensure that the kernel TCP/IP ephemeral port range is broad enough to provide enough ephemeral ports for the anticipated server workload.
