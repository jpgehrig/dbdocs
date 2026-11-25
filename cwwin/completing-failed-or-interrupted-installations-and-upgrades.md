## Completing Failed or Interrupted Installations and Upgrades

If Oracle Universal Installer (OUI) exits on the node from which you started the installation or upgrade (the first node), or the node reboots before you confirm that the `gridconfig.bat` script was run on all cluster nodes, then the upgrade or installation remains incomplete.

In an incomplete installation or upgrade, configuration assistants still need to run, and the new Grid home still needs to be marked as active in the central Oracle inventory. You must complete the installation or upgrade on the affected nodes manually.

- [Completing Failed Installations and Upgrades](completing-failed-installations-and-upgrades.md)
  Understand how to join nodes to the cluster after installation or upgrade fails on some nodes.
- [Continuing Incomplete Upgrade of First Nodes](continuing-upgrade-when-upgrade-fails-on-the-first-node.md)
  When the first node cannot be upgraded, use these steps to continue the upgrade process.
- [Continuing Incomplete Upgrades on Remote Nodes](continuing-upgrade-when-upgrade-fails-on-nodes-other-than-the-first-node.md)
  For nodes other than the first node (the node on which you started the upgrade), use these steps to continue the upgrade process.
- [Continuing Incomplete Installations on First Nodes](continuing-incomplete-installations-on-first-nodes.md)
  To continue an incomplete installation, the first node must finish before the rest of the clustered nodes.
- [Continuing Incomplete Installation on Remote Nodes](continuing-installations-on-nodes-other-than-the-first-node.md)
  For nodes other than the first node (the node on which you started the installation), use these steps to continue the installation process.

**Parent topic:** [Upgrading Oracle Grid Infrastructure](upgrading-oracle-grid-infrastructure.md)
