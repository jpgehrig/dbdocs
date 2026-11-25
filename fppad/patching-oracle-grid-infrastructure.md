## Patching Oracle Grid Infrastructure

Fleet Patching and Provisioning provides three methods to patch Oracle Grid Infrastructure software homes: rolling, non-rolling, and in batches.

Patching Oracle Grid Infrastructure software involves moving the Grid home to a patched version of the current Grid home. When the patching operation is initiated by a Fleet Patching and Provisioning Server or Client, the patched version must be a working copy of a gold image. The working copy to which you are moving the Grid home can be at a lower patch level than the current home. This facilitates rollback if any problems occur after moving to the higher-level patched home.

You can also perform this operation using the independent automaton in an environment where no Fleet Patching and Provisioning Server is present. In this case, the source and destination homes are not working copies of gold images, but are two installed homes that you deployed with some method other than using Fleet Patching and Provisioning.

- [Patching Oracle Grid Infrastructure Using the Rolling Method](oracle-grid-infrastructure-rolling-patching.md)
  The rolling method for patching Oracle Grid Infrastructure is the default method.
- [Patching Oracle Grid Infrastructure Using the Non-Rolling Method](oracle-grid-infrastructure-non-rolling-patching.md)
  You can use the `-nonrolling` parameter with the `rhpctl move gihome` command, which restarts the Oracle Grid Infrastructure stack on all nodes in parallel.
- [Combined Oracle Grid Infrastructure and Oracle Database Patching](combined-grid-and-database-patching.md)
  When you patch an Oracle Grid Infrastructure deployment, Oracle FPP enables you to simultaneously patch the Oracle Database homes on the cluster, so you can patch both types of software homes in a single maintenance operation.
- [Zero-Downtime Oracle Grid Infrastructure Patching](zero-downtime-grid-patching.md)
  Use Fleet Patching and Provisioning to patch Oracle Grid Infrastructure without bringing down Oracle RAC database instances.

**Related Topics**

- [rhpctl add workingcopy](workingcopy-commands.md)
- [rhpctl move gihome](gihome-commands.md)

**Parent topic:** [Patching and Upgrading Oracle Grid Infrastructure](patching-and-upgrading-oracle-grid-infrastructure.md)
