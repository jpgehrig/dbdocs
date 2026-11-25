## B.1 Creating the Data Dictionary

When you use the Database Configuration Assistant to create a database, Oracle automatically creates the data dictionary. Thereafter, whenever the database is in operation, Oracle updates the data dictionary in response to every DDL statement.

The data dictionary base tables are the first objects created in any Oracle database. They are created in the `SYSTEM` tablespace and must remain there. The data dictionary base tables store information about all user-defined objects in the database.

Table B-1 lists required scripts, which are run automatically when you create a database using the Database Configuration Assistant. They are described here because you might need to run them if you create a database manually. To run these scripts, you must be connected to Oracle as a user with `SYSDBA` privileges.

Table B-1 Creating the Data Dictionary Scripts

| Script Name                    | Needed For                       | Description                                                                                                                                                                                                                                                                                                   |
|:-------------------------------|:---------------------------------|:--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `catalog.sql`                  | All databases                    | Creates the data dictionary and public synonyms for many of its views<br>Grants `PUBLIC` access to the synonyms                                                                                                                                                                                               |
| `catproc.sql`                  | All databases                    | Runs all scripts required for, or used with, PL/SQL                                                                                                                                                                                                                                                           |
| `catpcat.sql`<sup>Foot 1</sup> | All databases                    | Runs the `catalog.sql` and `catproc.sql` scripts as parallel processes, which can speed up database creation<br>Note: You must run `catpcat.sql` by using the `catctl.pl` program. See [Oracle Database Administrator’s Guide](../admin/creating-and-configuring-an-oracle-database.md) for more information. |
| `catclust.sql`                 | Oracle Real Application Clusters | Creates Oracle Real Application Clusters data dictionary views                                                                                                                                                                                                                                                |

<sup>Footnote 1</sup> This script is available starting with Oracle Database 19c.

**See Also:**

- Your operating system-specific Oracle documentation for the exact names and locations of these scripts on your operating system

- [Oracle Database Administrator’s Guide](../admin/creating-and-configuring-an-oracle-database.md) for more information about creating a database

- [Oracle Real Application Clusters Administration and Deployment Guide](../racad/monitoring-performance.md) for more information about creating Oracle Real Application Cluster views
