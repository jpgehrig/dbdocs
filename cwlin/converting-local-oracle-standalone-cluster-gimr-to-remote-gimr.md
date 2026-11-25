## Converting a Local Oracle Standalone Cluster Repository to a Remote Repository

Complete this procedure to convert an Oracle Standalone Cluster with a repository in the local GIMR to a remote repository in the Oracle Domain Services Cluster GIMR.

Ensure that the Oracle Domain Services Cluster version is equal to or greater than the Oracle Standalone Cluster version.

1.  As the `grid` user on the Oracle Standalone Cluster with a repository in the local GIMR, unplug the repository PDB and export the cluster property information to a file.
        $ Grid_home/bin/mgmtca unplugRepos -local
        -serverVersion remote_GIMR_server_version -clusterInfoDir local_directory

    Where local_directory is a directory to store cluster property information file, repository PDB backup, and repository PDB metadata information.

    **Note:**

    Ensure that you have sufficient free disk space in the `local_directory` to save the exported files.
2.  Copy the contents of the `-clusterInfoDir` directory from the Oracle Standalone Cluster to the Oracle Domain Services Cluster to which you want to migrate the repository.
3.  As the `grid` user on the GIMR node of the Oracle Domain Services Cluster to which you want to migrate the repository PDB, plug the repository PDB that you unplugged in Step 1 and generate the client data file.
        $ Grid_home/bin/mgmtca plugRepos -clientDataFile client_data_file_location
        -clusterInfoDir cluster.properties_file_location

    If this step fails, then you have the following two options:
    - Fix the problem reported by the command and run the command again.
    - Run the `Grid_home/bin/mgmtca plugRepos -local -clusterInfoDir ``cluster.properties_file_location` command on the Oracle Standalone Cluster to rollback.
4.  Copy the client data file, which you generated in Step 3, from the Oracle Domain Services Cluster to Oracle Standalone Cluster.
5.  As the `grid` user on the Oracle Standalone Cluster, import credentials from the client data file.
        $ Grid_home/bin/mgmtca configRepos importCred -clientDataFile client_data_file_location
6.  As the `grid` user on the Oracle Standalone Cluster, delete the local GIMR and the management listener.
        $ Grid_home/bin/dbca -deleteDatabase -sourceDB -MGMTDB -silent -skipDBExistencecheck
        $ Grid_home/bin/srvctl disable mgmtlsnr
        $ Grid_home/bin/srvctl stop mgmtlsnr
        $ Grid_home/bin/srvctl remove mgmtlsnr
7.  Restart the `ora.crf` resource on the Oracle Standalone Cluster.
        $ Grid_home/bin/crsctl stop res ora.crf -init
        $ Grid_home/bin/crsctl start res ora.crf -init

**Parent topic:** [Using Remote GIMR for Oracle Standalone Cluster](using-remote-gimr-for-oracle-standalone-cluster.md)
