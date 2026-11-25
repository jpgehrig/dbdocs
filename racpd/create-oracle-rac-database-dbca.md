## Create the Oracle RAC Database with DBCA

To create the Oracle Real Application Clusters (Oracle RAC) database on the container, complete these steps with Database Configuration Assistant (DBCA).

The DBCA utility is typically located in the `ORACLE_HOME/bin` directory.

1.  Change directory to `$ORACLE_HOME/bin`, and enter the command `dbca`.
2.  On the Database Operation window, select Create Database, and click Next.
3.  Select Advanced Configuration, and click Next.
4.  On the Select Database Deployment Type window, Select from the Configuration Type list the database management policy that you want to use:
    - Admin-managed (the default)

      Administrator-managed deployment is based on the Oracle RAC deployment types that existed before Oracle Database 11g release 2 (11.2) and requires that you statically configure each database instance to run on a specific node in the cluster, and that you configure database services to run on specific instances belonging to a certain database using the preferred and available designation.

    - Policy-managed

      Policy-managed deployment is based on server pools, where database services run within a server pool as singleton or uniform across all of the servers in the server pool. Databases are deployed in one or more server pools and the size of the server pools determine the number of database instances in the deployment.

    When you have made your management policy selection, click Next.
5.  Select both `racnode` and `racnode2`, and click Next.
6.  On the Database Identification window, enter values for these fields:
    - Global Database Name: Enter `orclcdb.example.info`
    - SID Prefix: Enter `orclcdb`
    - Select Use Local Undo Tablespace for PDBs
    - Select Create a Container database with one or more PDBs
    - Select Number of PDBs
    - In PDB name, enter `orclpdb`

    Click Next
7.  On the Storage Option window, select the following options:
    - Database files location: Enter +`DATA/{DB_UNIQUE_NAME}`
    - Select Use Oracle-Managed Files (OMF)

    After you make your selections, click Next.
8.  On the Fast Recovery Option window, select the following:
    - Select Fast Recovery Area, and enter `+DATA`
    - Select Enable Archiving, and select the default option

    When you have made your selections, click Next.
9.  On the Data Vault Option window, select the default, and click Next.
10. On the Configuration Option window, under the Memory tab, enter the following values:
    - SGA Size: 3G
    - PGA Size: 2G

    Select the default values for the rest of the fields on the window, and click Next.

    Container available memory is considered to be the total allocated memory to the container. However, if no memory is assigned to the container, then the host memory is considered to be the available memory. Because with `cgroups`, anyone can assign more memory than the physical memory to container, CVU honors only lower or max host memory.

    The SGA and PGA values as computed by DBCA are incorrectly based the host memory. For more information, refer to My Oracle Support Doc ID 2885873.1. Allocate SGA and PGA based on the memory that you have allocated to the container. In this case, we have given 3G to the SGA, and 2G to the PGA.

    For the SGA and PGA memory capacity values, manually enter 3GB for SGA and 2GB for PGA, and then confirm Yes to the pop-up window, and continue.
11. On the Specify Management Options window, choose the default.
12. On the Specify Database User Credentials window, provide the password
13. On the Select Database Creation Option window, choose the default, and click Next.
14. The Prerequisite Checks window displays. Confirm that the prerequisites are completed without errors. It should redirect to the Install window.
15. Click Finish to begin the installation.

After the database is created, you can either connect to the database using your application, or connect with SQL\*Plus using the SCAN `racnode-scan.example.info` on port 1521.

**Parent topic:** [Install Oracle Grid Infrastructure and Oracle RAC](install-grid-infrastructure-and-rac.md)
