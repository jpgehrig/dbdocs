## Oracle ASM Upgrade Notifications

Understand Oracle ASM upgrade options and restrictions.

- You can upgrade Oracle Automatic Storage Management (Oracle ASM) 11g release 2 (11.2) and later without shutting down an Oracle RAC database by performing a rolling upgrade either of individual nodes, or of a set of nodes in the cluster. However, if you have a standalone database on a cluster that uses Oracle ASM, then you must shut down the standalone database before upgrading.

- The location of the Oracle ASM home changed in Oracle Grid Infrastructure 11g release 2 (11.2) so that Oracle ASM is installed with Oracle Clusterware in the Oracle Grid Infrastructure home (Grid home).

- Two nodes of different releases cannot run in the cluster. When upgrading from Oracle Grid Infrastructure 11g release 2 (11.2) or Oracle Grid Infrastructure 12c release 1 (12.1) to a later release, if there is an outage during the rolling upgrade, then when you restart the upgrade, ensure that you start the earlier release of Oracle Grid Infrastructure and bring the Oracle ASM cluster back in the rolling migration mode.

**Parent topic:** [Reviewing Operating System and Software Upgrade Best Practices](reviewing-operating-system-and-software-upgrade-best-practices.md)
