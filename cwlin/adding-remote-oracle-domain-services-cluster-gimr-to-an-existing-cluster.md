## Adding a Remote Repository to an Existing Cluster

Complete this procedure to add a remote repository to an Oracle Standalone Cluster that was initially configured without a GIMR.

1.  As the `grid` user on the Oracle Standalone Cluster to which you want to add a GIMR, get the cluster Globally Unique Identifier (GUID).
        $ Grid_home/bin/crsctl get css clusterguid
2.  As the `grid` user on the GIMR node of the Oracle Domain Services Cluster, create a repository for the Oracle Standalone Cluster and generate the client data file.
        $ Grid_home/bin/mgmtca createRepos -clientDataFile client_data_file_location -clusterName standalone_cluster_name
        -guid standalone_cluster_guid [-version standalone_cluster_version]
3.  Copy the client data file from the Oracle Domain Services Cluster to the Oracle Standalone Cluster.
4.  As the `grid` user on the Oracle Standalone Cluster, configure the remote repository.
        $ Grid_home/bin/mgmtca configRepos deploySchema -clientDataFile client_data_file_location
5.  Restart the `ora.crf` resource on the Oracle Standalone Cluster.
        $ Grid_home/bin/crsctl stop res ora.crf -init
        $ Grid_home/bin/crsctl start res ora.crf -init

**Parent topic:** [Using Remote GIMR for Oracle Standalone Cluster](using-remote-gimr-for-oracle-standalone-cluster.md)
