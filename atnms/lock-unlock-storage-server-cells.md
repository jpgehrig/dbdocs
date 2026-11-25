Beginning with version 12.1.0.2.7, use Oracle EXAchk to lock and unlock storage server cells.

On the database server, if you configure passwordless SSH equivalency for the user that launched Oracle EXAchk to the `root` user on each storage server, then Oracle EXAchk uses SSH equivalency to complete the storage server checks. Run Oracle EXAchk from the Oracle Exadata storage server, if there is no SSH connectivity from the database to the storage server.

To lock and unlock cells, use the `–unlockcells` and `–lockcells` options for Oracle Exadata, Oracle SuperCluster and Zero Data Loss Recovery Appliance.

    ./exachk -unlockcells all | -cells [comma-delimited list of cell names or cell IPs]
    ./exachk -lockcells all | -cells [comma-delimited list of cell names or cell IPs]

**Parent topic:** [Analyzing Risks and Complying with Best Practices](purpose-oracle-orachk-and-oracle-exachk.md)
