## Using DBCA to Create an Oracle RAC One Node Database

If you have selected to install only the Oracle RAC software on cluster nodes, then you can use Oracle Database Configuration Assistant (DBCA) to configure Oracle RAC One Node.

After installation of Oracle Real Application Clusters (Oracle RAC) software, start Oracle Database Configuration Assistant (DBCA).

1.  From the Database Operation page, select the option Create Database.
2.  On the Creation Mode page, select Advanced Configuration.
3.  On the Deployment Type page, select Oracle RAC One Node database.
    Selecting one node deploys Oracle RAC One Node on a single node. Oracle recommends that you select all nodes in the cluster to which you want Oracle RAC One Node to be able to fail over.

    When you create an administrator-managed Oracle RAC One Node database, note that while the database is started on only one of the pool of nodes you installed the binaries, all the candidate servers are placed into the Generic server pool. If the servers are not already in Generic or Free, then this may result in stopping resources that are running on candidate servers.

When you use DBCA to create an Oracle RAC One Node database, a failover service is automatically configured.

**Parent topic:** [Creating Oracle RAC or Oracle RAC One Node Databases with Oracle DBCA](creating-oracle-rac-or-oracle-rac-one-node-databases-with-dbca.md)
