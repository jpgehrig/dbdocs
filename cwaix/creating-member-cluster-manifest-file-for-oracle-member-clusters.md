Create a Member Cluster Manifest file to specify the Oracle Member Cluster configuration for the Grid Infrastructure Management Repository (GIMR), Grid Naming Service, Oracle ASM storage server, and Oracle Fleet Patching and Provisioning configuration.

Oracle Member Clusters use Oracle ASM storage from the Oracle Domain Services Cluster. Grid Naming Service (GNS) without zone delegation must be configured so that the GNS virtual IP address (VIP) is available for connection.

1.  (Optional) If the Oracle Member Cluster accesses direct or indirect Oracle ASM storage, then, enable access to the disk group. Connect to any Oracle ASM instance as SYSASM user and run the command:
        ALTER DISKGROUP diskgroup_name SET ATTRIBUTE 'access_control.enabled' = 'true';
2.  From the Grid home on the Oracle Domain Services Cluster, create the member cluster manifest file:
        cd Grid_home/bin
        ./crsctl create member_cluster_configuration member_cluster_name
        -file cluster_manifest_file_name -member_type database|application
        [-version member_cluster_version
        [-domain_services [asm_storage local|direct|indirect][rhp] [acfs]]

    member_cluster_name is the name of the member cluster.

    `-file` specifies the full path of the xml file to export the credentials, `-version` is the five digit Member Cluster version, for example, `19.0.0.0.0`, if it is different from the Storage Server version. The Storage Server version is used if `-version` is not specified.

    In the options for `-domain_services`, specifying `rhp` generates credentials and configuration for a Oracle Fleet Patching and Provisioning Member Cluster, and `asm_storage` generates credentials and configuration for an Oracle ASM Member Cluster. `direct` if specified, signifies direct storage access, otherwise indirect.

    This command creates a member cluster manifest file containing configuration details about Grid Infrastructure Management Repository (GIMR), Storage services, and Oracle Fleet Patching and Provisioning for the Oracle Member Cluster.
3.  GNS client data is required if the Oracle Member Cluster uses dynamic networks and the server cluster has GNS with zone delegation. Provide the GNS client data as follows:
    1.  As `root` or `grid` user, export the Grid Naming Service (GNS) client data, to the member cluster manifest file created earlier:
            srvctl export gns -clientdata manifest_file_name -role CLIENT

        The GNS configuration is appended to the member cluster manifest file.
4.  Copy the manifest file to a location on the Oracle Member Cluster, and select the file during the installation and configuration of the Oracle Member Cluster.

**Parent topic:** [Configuring Storage for Oracle Grid Infrastructure](configuring-storage-for-oracle-grid-infrastructure-for-a-cluster.md)
