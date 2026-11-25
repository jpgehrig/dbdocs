After upgrading from previous releases, if you want to deinstall the previous release Oracle Grid Infrastructure home, then you must first change the permission and ownership of the previous release Grid home.

Unlock the Oracle Grid Infrastructure installation using the following procedure:

1.  Log in as `root`, and change the permission and ownership of the previous release Grid home using the following command syntax, where oldGH is the previous release Grid home, swowner is the Oracle Grid Infrastructure installation owner, and oldGHParent is the parent directory of the previous release Grid home:

        #chmod -R 755 oldGH
        #chown -R swowner oldGH
        #chown swowner oldGHParent

    For example:

        #chmod -R 755 /u01/app/18.0.0/grid
        #chown -R grid /u01/app/18.0.0/grid
        #chown grid /u01/app/18.0.0

2.  After you change the permissions and ownership of the previous release Grid home, log in as the Oracle Grid Infrastructure installation owner (`grid`, in the preceding example), and use the `deinstall` command from previous release Grid home (oldGH) `$ORACLE_HOME/deinstall` directory.

**Caution:**

You must use the `deinstall` command from the same release to remove Oracle software. Do not run the `deinstall` command from a later release to remove Oracle software from an earlier release. For example, do not run the `deinstall` command from the 19.0.0.0.0 Oracle home to remove Oracle software from an existing 18.0.0.0.0 Oracle home.

**Parent topic:** [Upgrading Oracle Grid Infrastructure](upgrading-oracle-grid-infrastructure.md)
