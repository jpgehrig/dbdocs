## Performing Rolling Upgrade of Oracle Grid Infrastructure

Review this information to perform rolling upgrade of Oracle Grid Infrastructure.

- [Upgrading Oracle Grid Infrastructure from an Earlier Release](running-oui-to-upgrade-grid-infrastructure-from-an-earlier-release.md)
  Complete this procedure to upgrade Oracle Grid Infrastructure (Oracle Clusterware and Oracle Automatic Storage Management) from an earlier release.
- [Completing an Oracle Clusterware Upgrade when Nodes Become Unreachable](completing-an-oracle-clusterware-upgrade-when-nodes-become-unreachable.md)
  If some nodes become unreachable in the middle of an upgrade, then you cannot complete the upgrade, because the upgrade script (`rootupgrade.sh`) did not run on the unreachable nodes. Because the upgrade is incomplete, Oracle Clusterware remains in the previous release.
- [Joining Inaccessible Nodes After Forcing an Upgrade](joining-inaccessible-nodes-after-forcing-an-upgrade.md)
  Use this procedure to join inaccessible nodes after a force cluster upgrade.
- [Changing the First Node for Install and Upgrade](changing-the-first-node-for-install-and-upgrade.md)
  If the first node becomes inaccessible, you can force another node to be the first node for installation or upgrade.

**Parent topic:** [Upgrading Oracle Grid Infrastructure](upgrading-oracle-grid-infrastructure.md)
