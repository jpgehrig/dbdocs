These are the Oracle Automatic Storage Management (Oracle ASM) Cluster File System (Oracle ACFS) bugs in Oracle Database 19c.

- Bug 29391849

**Parent topic:** [Open Bugs Affecting All Platforms](open-bugs-for-all-platforms.md)

### Bug 29391849

After an upgrade to either Oracle Grid 18.x or 19.x is complete, a subsequent upgrade to Oracle Grid 18.y or 19.y results in the Oracle Automatic Storage Management Cluster File System (Oracle ACFS) being offline on the first node being upgraded. This issue does not occur on a fresh installation of Oracle Grid 19c or 18c.

#### Workaround:

- To avoid this issue:
  1.  Complete the upgrade from Oracle Grid 12c Release 1 (12.1.0.2) or Oracle Grid 12c Release 2 (12.2) to Oracle Grid 18.x or 19.x.
  2.  Restart Cluster Ready Services (CRS) on each node, restarting the master node last. For example:
      1.  Run `acfsutil clusterinfo | grep -i master` .
      2.  Restart CRS on each non-master node, in any order.
      3.  Restart CRS on the master node last.
  3.  Then, upgrade from Oracle Grid 18.x or 19.x to Oracle Grid 18.y or 19.y.
- If you have completed the upgrade from Oracle Grid 12.1.0.2 or 12.2 to Oracle Grid 18.x or 19.x, and have started the upgrade to Oracle Grid 18.y or 19.y, and if you see the Oracle Automatic Storage Management Dynamic Volume Manager (Oracle ADVM) volumes offline on the node that you have upgraded, then:
  1.  Roll back that node to Oracle Grid 18.x or 19.x.
  2.  Restart CRS on each node, restarting the master node last.
      1.  Run `acfsutil clusterinfo | grep -i master` .
      2.  Restart CRS on each non master node, in any order.
      3.  Restart CRS on the master node last.
  3.  Then, upgrade from Oracle Grid 18.x or 19.x to Oracle Grid 18.y or 19.y.

**Parent topic:** Oracle ASM Cluster File System (Oracle ACFS) Known Bugs
