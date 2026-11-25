These are the Oracle Grid Infrastructure bugs in Oracle Database 19c.

- Bug 29414664
- Bug 29053083
- Bug 21559133

**Parent topic:** [Open Bugs Affecting All Platforms](open-bugs-for-all-platforms.md)

### Bug 29414664

The Help text for command `rhpctl instantiate image` does not show the `-server` option.

#### Workaround:

When instantiating an image between two Fleet Patching and Provisioning (FPP) servers whose peer-to-peer relationship has already been established, use the command `rhpctl instantiate image` with the `-server` option specifying the remote FPP server from which to instantiate the given image.

**Parent topic:** Oracle Grid Infrastructure Known Bugs

### Bug 29053083

The Grid Naming Service (GNS) manifest file validation fails.

#### Workaround:

Do not add GNS while creating a member cluster manifest file.

**Parent topic:** Oracle Grid Infrastructure Known Bugs

### Bug 21559133

This issue affects rolling upgrades from Oracle Grid Infrastructure 12c release 1 (12.1) to Oracle Grid Infrastructure 19c of Oracle Clusterware standard Cluster with Oracle ASM. A node running Oracle Grid Infrastructure 12c release 1 (12.1) cannot join the cluster after the first node has been upgraded to Oracle Grid Infrastructure 19c. The nodes running Oracle Grid Infrastructure 12c release 1 (12.1) that are in `ONLINE` status continue to be members of the cluster.

#### Workaround:

Upgrade Oracle Grid Infrastructure from 12c release 1 (12.1) to 19c on the failed node.

**Parent topic:** Oracle Grid Infrastructure Known Bugs
