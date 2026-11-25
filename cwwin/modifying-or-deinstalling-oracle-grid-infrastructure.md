## 12 Modifying or Deinstalling Oracle Grid Infrastructure

You must follow a specific procedure when modifying or removing Oracle Clusterware and Oracle Automatic Storage Management (Oracle ASM) software.

- [Deciding When to Deinstall Oracle Clusterware](deciding-when-to-deinstall-oracle-clusterware.md)
  There are certain situations in which you might be required to remove Oracle software.
- [Migrating Standalone Grid Infrastructure Servers to a Cluster](migrating-standalone-grid-infrastructure-servers-to-a-cluster.md)
  If you have an Oracle Database installation using Oracle Restart (an Oracle Grid Infrastructure installation for a standalone server), you can reconfigure that server as a cluster member node, then complete the following tasks.
- [Changing the Oracle Grid Infrastructure Home Path](changing-the-oracle-grid-infrastructure-home-path.md)
  After installing Oracle Grid Infrastructure for a cluster, you might need to change the location of the Grid home.
- [Unconfiguring Oracle Clusterware Without Removing the Software](unconfiguring-oracle-clusterware-without-removing-the-software.md)
  By running `rootcrs.bat -deconfig -force` on nodes where you encounter an installation error, you can unconfigure Oracle Clusterware on those nodes, correct the cause of the error, and then run `rootcrs.bat` again to reconfigure Oracle Clusterware.
- [Removing Oracle Clusterware and Oracle ASM Software](removing-oracle-clusterware-and-oracle-asm-software.md)
  The `deinstall` command removes Oracle Clusterware and Oracle ASM from your server.

**See Also:**

Product-specific documentation for requirements and restrictions to remove an individual product
