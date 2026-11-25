Complete this procedure on your Oracle Restart server to upgrade the operating system.

1.  As the `root` user, disable the automatic startup of Oracle High Availability Services, when the server reboots.
        # cd Grid_home/bin
        # ./crsctl disable has
2.  Shut down the Oracle Restart stack on the server.
        # ./crsctl stop has
3.  Verify all services are stopped before the operating system upgrade.
        # ./crsctl check has
4.  Upgrade the operating system to a version that is supported for your Oracle Restart release.
    Refer to your operating system documentation for more information about upgrading the operating system.
5.  Reboot your Oracle Restart server after the operating system upgrade is complete.
6.  As the `root` user, add the Oracle Database libraries and lock the Oracle Restart installation.
        # cd Grid_home/rdbms/install/
        # ./rootadd_rdbms.sh
        # cd Grid_home/crs/install
        # roothas.sh -lock
7.  As the `root` user, enable the automatic startup of Oracle High Availability Services, when the server reboots.
        # cd Grid_home/bin
        # ./crsctl enable has
8.  Start the Oracle Restart stack on the server.
        # ./crsctl start has
9.  Connect to an SQL\*Plus session and open the Pluggable Database (PDB).
        SQL> CONNECT / AS SYSDBA
        SQL> ALTER PLUGGABLE DATABASE pdb_name OPEN;
10. As the `grid` user, list all registered resources on your Oracle Restart server.
        $ Grid_home/bin/crsctl stat res -t

**Parent topic:** [Preparing to Upgrade Oracle Restart](preparing-to-upgrade-oracle-restart.md)
