If you are upgrading from Oracle9i Release 2 (9.2) or Oracle Database 10g Release 1 (10.1), and you are using externally authenticated SSL users, then you must run the SSL external users conversion (`extusrupgrade`) script to upgrade those users.

The `extusrupgrade` script has the following syntax, where `ORACLE_HOME` is the Oracle database home, `hostname` is the name of the host on which the database is running, `port_no` is the listener port number, `sid` is the system identifier for the database instance, and `db_admin` is the database administrative user with privileges to modify user accounts.

    ORACLE_HOME/rdbms/bin/extusrupgrade --dbconnectstring
    hostname:port_no:sid --dbuser db_admin --dbuserpassword
    password -a

For example:

    extusrupgrade --dbconnectstring dlsun88:1521:10gR2 --dbuser system --dbuserpassword manager -a

**Note:**

If you are upgrading from Oracle Database 10g Release 2 (10.2) or later, then you are not required to run the `extusrupgrade` script.

**See Also:**

[Oracle Database Enterprise User Security Administrator's Guide](../dbimi/ssl-external-users-conversion-script.md) for more information about the `extusrupgrade` script

**Parent topic:** [Required Tasks to Complete After Upgrading Oracle Database](required-tasks-to-complete-after-upgrade.md)
