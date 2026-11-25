You must enable root access to use Oracle ACFS.

To enable root access, log in as `root`, navigate to the path Grid_home`/crs/install`, and run the script `roothas.sh —lockacfs`.

Where, Grid_home is the Oracle Grid Infrastructure home directory path.

For example:

    # cd /u01/app/oracle/product/19.0.0/grid/crs/install
    # roothas.sh -lockacfs

**Note:**

Starting with Oracle Database 12c Release 1 (12.1.0.2), the `roothas.sh` script replaces the `roothas.pl` script in the Oracle Grid Infrastructure home.

**Parent topic:** [Installing and Configuring Oracle Grid Infrastructure for a Standalone Server](installing-and-configuring-oracle-grid-infrastructure-for-a-standalone-server.md)
