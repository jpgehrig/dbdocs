## Oracle ASM Upgrade Notifications

Be aware of these issues regarding Oracle ASM upgrades.

- You can upgrade Oracle Automatic Storage Management (Oracle ASM) 11g release 1 (11.1) and later without shutting down an Oracle RAC database. Perform a rolling upgrade either of individual nodes, or of a set of nodes in the cluster. However, if you have a standalone database on a cluster that uses Oracle ASM, then you must shut down the standalone database before upgrading. If you are upgrading from Oracle ASM 10g, then you must shut down the entire Oracle ASM cluster to perform the upgrade.

- The location of the Oracle ASM home changed in Oracle Grid Infrastructure 11g release 2 (11.2) so that Oracle ASM is installed with Oracle Clusterware in the Oracle Grid Infrastructure home (Grid home).

  If you have an existing Oracle ASM home from a earlier release, then you may want to consider other configuration changes to simplify or customize storage administration.

- When upgrading from Oracle Grid Infrastructure 11g release 2 (11.2) or Oracle Grid Infrastructure 12c release 1 (12.1) to a later release, if there is an outage during the rolling upgrade, then when you restart the upgrade, ensure that you start the earlier release of Oracle Grid Infrastructure. You must then bring the Oracle ASM cluster back in the rolling migration mode, because two nodes of different releases cannot run in the cluster.

- You must be an Administrator user to upgrade Oracle ASM.

**Parent topic:** [Reviewing Operating System and Software Upgrade Best Practices](reviewing-operating-system-and-software-upgrade-best-practices.md)
