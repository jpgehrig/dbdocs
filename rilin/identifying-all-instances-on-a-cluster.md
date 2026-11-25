## Identifying All Instances On a Cluster

Review this information to identify all instances associated with the Oracle home you want to remove.

To identify all instances associated with the Oracle home you want to remove, enter the following command, where `dbname` is the name of the database:

    $ srvctl status database -d dbname

Alternately, you can check for registered instances by viewing the `oratab` file:

AIX, HP-UX, or Linux:

    $ more /etc/oratab

Oracle Solaris:

    $ more /var/opt/oracle/oratab

The output of this command contains entries similar to the following:

    +ASM1:/u01/app/19.0.0/grid:N
    CUST:/u01/app/oracle/product/19.0.0/dbhome_1:N

These entries show that the `+ASM` Oracle Automatic Storage Management instance in the Oracle Grid Infrastructure for a cluster home (`/u01/app/19.0.0/grid`) and the `CUST` Oracle database instance are associated with the Oracle home directory `/u01/app/oracle/product/19.0.0/dbhome_1`.

**Parent topic:** [Removing Oracle Database Software](removing-oracle-database-software.md)
