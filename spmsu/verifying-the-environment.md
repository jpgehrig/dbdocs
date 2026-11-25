Complete the steps before you begin duplication.

1.  Ensure that the source database host is reachable from the destination host. You must be able to SSH between the two hosts.

2.  On the destination host, use the TNSPING utility to verify the listener port on the source host works fine.

    For example:
        tnsping source host:1521

3.  On the destination host, use Easy Connect to verify the connection to the source database:
        host:port/servicename

    For example:
        sqlplus system@ip-address:1521/proddb

    Ensure that the connection string does not exceed 64 characters.

4.  Copy the required `sqlpatch` files (for rollback) from the source database home to the target database.

5.  Ensure that at least one archivelog has been created on the source database; otherwise, RMAN duplication fails with an error.

6.  If the source database uses wallets, then back up the password-based wallet and copy it to the standard location on the destination host.

    For example:
        /opt/oracle/dcs/commonstore/wallets/tde/db_unique_name/

7.  Make sure the compatibility parameters in the source database are set to at least 11.2.0.4.0 for an 11.2.0.4 database and at least 12.1.0.2.0 for a 12.1.0.2 database.

**Parent topic:** [Duplicating the Primary Oracle Database](duplicating-the-oracle-database.md)
