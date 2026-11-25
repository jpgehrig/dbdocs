## Options for Oracle Grid Infrastructure Upgrades

When you upgrade to Oracle Grid Infrastructure 19c, you upgrade to an Oracle Flex Cluster configuration.

Supported upgrade paths for Oracle Grid Infrastructure for this release are:

- Oracle Grid Infrastructure upgrade from 11g Release 2 (11.2.0.4) to Oracle Grid Infrastructure 19c.

- Oracle Grid Infrastructure upgrade from 12c Release 1 (12.1.0.2) to Oracle Grid Infrastructure 19c.

- Oracle Grid Infrastructure upgrade from 12c Release 2 (12.2) to Oracle Grid Infrastructure 19c.

- Oracle Grid Infrastructure upgrade from 18c release to Oracle Grid Infrastructure 19c.

Upgrade options from Oracle Grid Infrastructure 11g Release 2 (11.2.0.4), Oracle Grid Infrastructure 12c Release 1 (12.1.0.2), Oracle Grid Infrastructure 12c Release 2 (12.2), and Oracle Grid Infrastructure 18c to Oracle Grid Infrastructure 19c include the following:

- Oracle Grid Infrastructure rolling upgrade which involves upgrading individual nodes without stopping Oracle Grid Infrastructure on other nodes in the cluster

- Oracle Grid Infrastructure non-rolling upgrade by bringing the cluster down and upgrading the complete cluster

**Note:**

- When you upgrade to Oracle Grid Infrastructure 19c, you upgrade to an Oracle Standalone Cluster configuration.

- You can use either Oracle ASM or a shared file system to store OCR and voting files on Oracle Standalone Cluster deployments. If storage for OCR and voting files is other than Oracle ASM on other cluster types, then you need to migrate OCR and voting files to Oracle ASM before upgrading to Oracle Grid Infrastructure 19c.

**Parent topic:** [Upgrading Oracle Grid Infrastructure](upgrading-oracle-grid-infrastructure.md)
