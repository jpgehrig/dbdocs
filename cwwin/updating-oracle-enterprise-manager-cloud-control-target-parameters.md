## Updating Oracle Enterprise Manager Cloud Control Target Parameters

After upgrading Oracle Grid Infrastructure, upgrade the Enterprise Manager Cloud Control target.

Because Oracle Grid Infrastructure 19c is an out-of-place upgrade of the Oracle Clusterware home in a new location (the Oracle Grid Infrastructure for a cluster home, or Grid home), the path for the `CRS_HOME` parameter in some parameter files must be changed. If you do not change the parameter, then you encounter errors such as "cluster target broken" on Oracle Enterprise Manager Cloud Control.

To resolve the issue, update the Enterprise Manager Cloud Control target, and then update the Enterprise Manager Agent Base Directory on each cluster member node running an agent.

- [Updating the Enterprise Manager Cloud Control Target After Upgrades](updating-the-enterprise-manager-cloud-control-target-after-upgrades.md)
  After upgrading Oracle Grid Infrastructure, update the Enterprise Manager Target with the new Grid home path.
- [Updating the Enterprise Manager Agent Base Directory After Upgrades](updating-the-enterprise-manager-agent-base-directory-after-upgrades.md)
  After upgrading Oracle Grid Infrastructure, update the Enterprise Manager Agent Base Directory on each cluster member node running an agent.
- [Registering Resources with Oracle Enterprise Manager After Upgrades](registering-resources-with-enterprise-manager-after-upgrades.md)
  After upgrading Oracle Grid Infrastructure, add the new resource targets to Oracle Enterprise Manager Cloud Control.

**Parent topic:** [Upgrading Oracle Grid Infrastructure](upgrading-oracle-grid-infrastructure.md)
