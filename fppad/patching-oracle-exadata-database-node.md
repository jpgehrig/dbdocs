## Updating Oracle Exadata Database Node

Update Oracle Exadata database servers to a higher Oracle Exadata software version.

1.  Create an Oracle Exadata Database node image.
    The following command creates an Oracle Exadata image. In the example, `image` specifies the name of the Oracle Exadata image that you want to add, `imagetype` specifies `EXAPATCHSOFTWARE` for Oracle Exadata software, `version` specifies the version of the Oracle Exadata software, and `path` specifies the absolute path location of the Oracle Exadata software home that you want to import.

        rhpctl import image -image image_name -imagetype EXAPATCHSOFTWARE
        -version software_version -path absolute_path

    When you import an Oracle Exadata software home with this command, the `version` parameter must be the version of the Oracle Exadata software required by the `patchmgr` on the database node. The `path` parameter should contain Oracle Exadata update zip files.
2.  Deploy the Oracle Exadata Database node image to the client cluster.
    The following command deploys an Oracle Exadata image to a client cluster. In the example, `image` specifies the name of the Oracle Exadata image that you want to deploy, `client` specifies the name of the cluster to which you want to deploy the image, and `path` specifies the absolute path location for deploying the Oracle Exadata software home on the `rhpclient`-less target or client side.

        rhpctl deploy image -image image_name
        -client client_cluster_name -path image_file_path

    The `targetnode` parameter is required if the node hosting the home is not a Oracle Fleet Patching and Provisioning Client. If the `rhpclient`-less target or client option is not specified, then the Oracle Exadata image is deployed to the Oracle Fleet Patching and Provisioning Server.
3.  Evaluate the current configuration and perform pre-upgrade checks.
    The following command evaluates the current configuration and performs pre-upgrade checks. In the example, `image` specifies the name of the Oracle Exadata image that you want to use for update, `iso_repo` specifies the image in the ISO repository, `pathmgrloc` specifies the patch manager location, `client` specifies the name of the cluster in which you want to update database nodes, and `batches` specifies a comma-delimited list of batches of nodes where each batch is a comma-delimited list of node names enclosed in parentheses and node names are enclosed in double quotation marks (`""`) in the format: `"(nA,nB,...),(...,nY,nZ)"`.

        rhpctl update exadata -dbnodes {comma_separates_list_of_nodes | [-batches "comma_separated_list_of_batches]}
        -image image_name -iso_repo iso_image_name -client client_cluster_name
        -patchmgrloc patch_mgr_loc [-patchmgrargs "-patch_manager_arguments"] -eval

    - If you do not specify the list of nodes for `-dbnodes`, then Oracle FPP automatically discovers all active database nodes in the cluster.
    - If the `client` option is not specified when issuing the command, then database node update is performed on the Oracle Fleet Patching and Provisioning Server.
4.  Create a backup of the current configuration.
        rhpctl update exadata -dbnodes {comma_separates_list_of_nodes | [-batches "comma_separated_list_of_batches]}
        -image image_name -iso_repo iso_image_name -client client_cluster_name
        -patchmgrloc patch_mgr_loc [-patchmgrargs "-patch_manager_arguments"] -backup
5.  Update Oracle Exadata Database node with the new image.
        rhpctl update exadata -dbnodes {comma_separates_list_of_nodes | [-batches "comma_separated_list_of_batches"]}
        -image image_name -iso_repo iso_image_name -client client_cluster_name
        -patchmgrloc patch_mgr_loc [-patchmgrargs "-patch_manager_arguments"]

**Parent topic:** [Updating Oracle Exadata Infrastructure](patching-oracle-exadata.md)
