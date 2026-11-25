## Task 5 - Create Oracle GoldenGate Deployment Directories

The Oracle GoldenGate Service Manager and deployment were already created on the primary system, but certain directories and symbolic links need to be configured on the standby system nodes. These directories and symbolic links were created on the primary system, as detailed in [Cloud: Oracle GoldenGate Microservices Architecture on Oracle Exadata Database Service Configuration Best Practices](ogg-microservices-cloud1.md).

1.  As the `oracle` OS user on the primary system, determine the datastore directory:

        [opc@exapri-node1 ~]$ sudo su - oracle
        [oracle@exapri-node1 ~]$ grep RepoDatastorePath /mnt/dbfs/goldengate
         /deployments/<instance_name>/var/log/pmsrvr.log|uniq
        "RepoDatastorePath": "",
               "RepoDatastorePath": "/u02/app/oracle/goldengate/datastores/<instance_name>",

2.  As the `oracle` OS user on the standby system, create the directory on all database nodes:

        [oracle@exastb-node1 ~]$ /usr/local/bin/dcli -l oracle -g ~/dbs_group mkdir
         -p /u02/app/oracle/goldengate/datastores/<gg_deployment_name>

    Create the Oracle GoldenGate deployment temp directory local storage to match the symbolic link created on the primary system.

3.  As the `oracle` OS user on the primary system, determine the datastore directory:

        [oracle@exapri-node1 ~]$ ls -l
         /mnt/dbfs/goldengate/deployments/<instance_name>/var |grep temp
        lrwxrwxrwx  1 oracle oinstall 49 Oct  3 10:20 temp ->
         /u02/app/oracle/goldengate/deployments/<instance_name>/temp

4.  As the `oracle` OS user on the standby system, create the same directory on the standby database nodes:

        [oracle@exastb-node1 ~]$ /usr/local/bin/dcli -l oracle -g ~/dbs_group mkdir
         -p /u02/app/oracle/goldengate/deployments/<instance_name>/temp
