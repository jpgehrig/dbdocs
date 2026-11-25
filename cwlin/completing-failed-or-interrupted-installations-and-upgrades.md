## Completing Failed or Interrupted Installations and Upgrades

If Oracle Universal Installer (OUI) exits on the node from which you started the upgrade, or the node reboots before you confirm that the `rootupgrade.sh` script was run on all nodes, then the upgrade remains incomplete.

In an incomplete installation or upgrade, configuration assistants still need to run, and the new Grid home still needs to be marked as active in the central Oracle inventory. You must complete the installation or upgrade on the affected nodes manually.

- [Completing Failed Installations and Upgrades](completing-failed-installation-upgrade.md)
  Understand how to join nodes to the cluster after installation or upgrade fails on some nodes.
- [Continuing Incomplete Upgrade of First Node](continuing-incomplete-upgrades-of-first-nodes.md)
  Review this information to complete the upgrade, if upgrade of Oracle Grid Infrastructure fails on the first node.
- [Continuing Incomplete Upgrades on Remote Nodes](continuing-incomplete-upgrades-on-remote-nodes.md)
  Review this information to continue incomplete upgrade on remote nodes.
- [Continuing Incomplete Installation on First Node](continuing-incomplete-installations-of-first-nodes.md)
  Review this information to continue an incomplete installation of Oracle Grid Infrastructure, if installation fails on the first node.
- [Continuing Incomplete Installation on Remote Nodes](continuing-incomplete-installation-on-remote-nodes.md)
  Review this information to continue incomplete installation on remote nodes.

**Parent topic:** [Upgrading Oracle Grid Infrastructure](upgrading-oracle-grid-infrastructure.md)
