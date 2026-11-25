## Deinstalling Previous Release Grid Home

Use this procedure to deinstall the previous release Grid home.

For upgrades from previous releases, if you want to deinstall the previous release Grid home, then perform the following steps:

1.  Log in as the `root` user.
2.  Manually change the permissions of the previous release Grid home.
        # chmod -R 775 /u01/app/oracle/product/18.0.0/grid
        # chown -R oracle:oinstall /u01/app/oracle/product/18.0.0/grid
        # chown oracle /u01/app/oracle/product/18.0.0

    In this example:

    - `/u01/app/oracle/product/18.0.0/grid` is the previous release Oracle Grid Infrastructure for a standalone server home

    - `oracle` is the Oracle Grid Infrastructure installation owner user

    - `oinstall` is the name of the Oracle Inventory group (OINSTALL group)

    - `/u01/app/oracle/product/18.0.0` is the parent directory of the previous Grid home.
3.  Log in as the Oracle Grid Infrastructure software owner user (`oracle`) and run the `deinstall` command.

**Parent topic:** [Removing Oracle Database Software](removing-oracle-database-software.md)
